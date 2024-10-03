# Usa Ubuntu como base
FROM ubuntu:latest

# Instala Nginx, ca-certificates, openjdk-17-jre-headless, git y curl
RUN apt-get update && \
    apt-get install -y nginx ca-certificates openjdk-17-jre-headless git curl && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Crea un usuario sin privilegios
RUN useradd -m javiercruces

# Cambia el usuario activo
#USER javiercruces

# Copia el archivo de configuración de Nginx
COPY ./nginx.conf /etc/nginx/conf.d/default.conf

# Expone el puerto 80
EXPOSE 80

# Comando para ejecutar Nginx
CMD ["nginx", "-g", "daemon off;"]
