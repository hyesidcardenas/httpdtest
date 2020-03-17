# httpdtest
html para WorkShops de OCP
# Pruebas con Docker
## Levantar un contenedor con apache:
docker run httpd
## Levantar el contenedor en backgroud:
docker run -d httpd
## Redireccionar un puerto local de la maquin (TCP/8080) a un puerto del contenedor (TCP/80):
docker run -d -p 8080:80 httpd
## Conectarse a un contenedor:
docker exec -ti container_name bash
## Cambiar el index.html por defecto
echo "Mi pagina personalizada" >> htdocs/index.html
## Borrar el contenedor y recrear:
docker stop container_name && docker rm container_name
## Recrear el contenedor
docker run -d -p 8080:80 httpd
## 
