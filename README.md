# Docker_ApacheWebServer_NginxReverseProxy
## Tarea 1: Configuración de un Servidor Web Apache con Reverse Proxy Nginx usando Docker Compose
El objetivo de este ejercicio es desplegar un servidor web con Apache detrás de un proxy inverso Nginx utilizando Docker Compose. Además, el contenido HTML servido por Apache debe ser modificable de forma dinámica.
Detalles a tener en cuenta:
Usar volúmenes para configurar el servidor Nginx y para el contenido HTML del servidor Apache.

```bash
javiercruces@5CD4342D0M:~/Docker_ApacheWebServer_NginxReverseProxy$ docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' nginx_rproxy
172.18.0.2
javiercruces@5CD4342D0M:~/Docker_ApacheWebServer_NginxReverseProxy$ sudo cat /etc/hosts

172.18.0.2 web.javiercd.es
javiercruces@5CD4342D0M:~/Docker_ApacheWebServer_NginxReverseProxy$ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS     NAMES
40501f759b4d   httpd:latest   "httpd-foreground"       5 minutes ago   Up 5 minutes   80/tcp    apache_web_server
a8d7e27db6fc   nginx:latest   "/docker-entrypoint.…"   5 minutes ago   Up 5 minutes   80/tcp    nginx_rproxy
javiercruces@5CD4342D0M:~/Docker_ApacheWebServer_NginxReverseProxy$

javiercruces@5CD4342D0M:~/Docker_ApacheWebServer_NginxReverseProxy$ curl web.javiercd.es
<h1>hola soy javier cruces</h1>
```

## Tarea 2: Creación de Imágenes Personalizadas para Apache y Nginx usando Dockerfile
A partir del ejercicio anterior, en el cual desplegaste un servidor web Apache detrás de un reverse proxy Nginx usando Docker Compose, ahora vas a crear tus propias imágenes Docker personalizadas para ambos servicios usando un Dockerfile, partiendo de una imagen base de Ubuntu.
Detalles a tener en cuenta:
Instalar además de apache o nginx: ca-certificates, openjdk-17-jre-headless, git, curl
Debes asegurarte de incluir en el Dockerfile que se limpie el sistema después de instalar paquetes con apt-get.
Debes crear un usuario sin privilegios junto a su directorio de trabajo y cambiar el usuario activo en el contenedor al usuario nuevo.

```bash
javiercruces@5CD4342D0M:~/Docker_ApacheWebServer_NginxReverseProxy/ejercicio2$ docker compose down && docker compose up -d

javiercruces@5CD4342D0M:~/Docker_ApacheWebServer_NginxReverseProxy/ejercicio2$ docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddres
s}}{{end}}' nginx_proxy
172.18.0.2

javiercruces@5CD4342D0M:~/Docker_ApacheWebServer_NginxReverseProxy/ejercicio2$ echo "172.18.0.2 web.javiercd.es" | sudo tee -a /etc/hosts > /dev/null

javiercruces@5CD4342D0M:~/Docker_ApacheWebServer_NginxReverseProxy/ejercicio2$ curl web.javiercd.es
<h1>hola soy javier cruces :)</h1>
```

## Tarea 3: Instalación de Harbor y Subida de Imágenes Personalizadas
El objetivo de este ejercicio es instalar un registro Docker privado usando Harbor y luego subir las imágenes personalizadas de Apache y Nginx creadas en el ejercicio anterior.
Detalles a tener en cuenta:
Debes instalar Harbor con docker en un sistema operativo Linux o en el Subsistema de Windows para Linux (WSL).
Sigue las instrucciones de la documentación oficial de Harbor para realizar la instalación utilizando Docker.
