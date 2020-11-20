# WorkShop - Red Hat OpenShift Container Platform
Aqui se encuentra el index.html fuente de ejemplo para el despliegue de la APP en OpenShift para el WorkShop, ademas de los comandos clave para trabajar con contenedores Docker.
# Laboratorio de Contendores Docker / Podman
## Buscar y descargar una imagen de Docker Hub
https://hub.docker.com/
## Levantar un contenedor con apache:
docker run httpd
## Levantar el contenedor en backgroud:
docker run -d httpd
## Redireccionar un puerto local de la máquina (TCP/8080) a un puerto del contenedor (TCP/80):
docker run -d -p 8080:80 httpd
## Conectarse a un contenedor:
docker exec -ti container_name bash
## Cambiar el index.html por defecto
echo "Mi pagina personalizada" >> htdocs/index.html
## Borrar el contenedor y recrear:
docker stop container_name && docker rm container_name
## Recrear el contenedor
docker run -d -p 8080:80 httpd
## Utilizar almacenamiento persistente en un contenedor:
docker run -d -p 8080:80 -v /ruta/local:/ruta/containter  httpd
## Crear un archivo llamado Dockerfile con el siguiente contenido, para instalar el comando "ps" en la imagen httpd
<pre>
FROM httpd:latest  
RUN apt-get update && \  
    apt-get install procps -y && \  
    apt-get clean  
</pre>
## Construir una imagen de docker con Dockerfile
docker build .
## Nombrar una imagen
docker tag "IMAGE ID" "name":latest
