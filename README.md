# httpdtest
html para WorkShops OCP
esto
# Pruebas con Docker
## Levantar un contenedor con apache:
docker run httpd
## Levantar el contenedor en backgroud:
docker run -d httpd
## Redireccionar un puerto local de la maquin (TCP/8080) a un puerto del contenedor (TCP/80):
docker run -d -p 8080:80 httpd
## Cambiar el index por defecto:
docker exec -ti <<name>> bash
Luego con el siguiente comando se cambia el index por defecto:
echo "Mi pagina personalizada" >> htdocs/index.html
## Borrar el contenedor y recrear:
