# Usa la imagen base de Ubuntu
FROM ubuntu:latest

# Instala Apache, ca-certificates, openjdk-17-jre-headless, git y curl
RUN apt-get update && \
    apt-get install -y apache2 ca-certificates openjdk-17-jre-headless git curl && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Crea un usuario sin privilegios y su directorio de trabajo
RUN useradd -m -d /home/javiercruces javiercruces

# Darle los permisos correctos a los dir de apache
RUN mkdir -p /var/run/apache2 /var/lock/apache2 && \
    chown -R javiercruces:javiercruces /var/run/apache2 /var/lock/apache2 /var/www /etc/apache2

# Cambia el usuario activo al nuevo usuario sin privilegios
#USER javiercruces

# Copia los archivos HTML al contenedor y ajusta los permisos para el usuario javiercruces
COPY  ./html /var/www/html/

# Expone el puerto 80
EXPOSE 80

# Comando para ejecutar Apache en el foreground
CMD ["apache2ctl", "-D", "FOREGROUND"]
