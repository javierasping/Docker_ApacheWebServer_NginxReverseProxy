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
```
