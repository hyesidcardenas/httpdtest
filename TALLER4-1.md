# Aplicación de permisos mediante RBAC

Crear grupos en OpenShift y agregar usuarios a estos grupos. 

Crear un proyecto y asignar privilegios de administración del proyecto al grupo. 

Asignar privilegios de lectura y escritura a diferentes grupos de usuarios.

Inicie sesión con el usuario admin0x y cree el proyecto user0X-rbac.

oc new-project user0X-rbac

## Cree los grupos grupo-dev y grupo-qa, y agregue los miembros respectivos.

Cree un grupo denominado group-dev.
```
oc adm groups new grupo-dev
``` 
Agregue el usuario developer en grupo-dev.
```
oc adm groups add-users grupo-dev developer
````
Agregue el usuario pruebas a grupo-qa.
```
oc adm groups add-users grupo-qa pruebas
````
Validar que todos los grupos creados tengan los miembros correctos.
```
oc get groups
````
## Con el usuario admin0X, asigne privilegios de escritura a grupo-dev y privilegios de lectura a grupo-qa para el proyecto user0X-rbac.

Otorgue privilegios de administración de proyecto al usuario lider0x en el proyecto user0X-rbac.
```
oc policy add-role-to-user admin lider0x
````
Inicie sesión con el usuario lider0x.
```
oc login -u lider0x
````
Agregue privilegios de escritura a grupo-dev en el proyecto user0X-rbac.
```
oc policy add-role-to-group edit grupo-dev -n user0X-rbac
````
Agregue privilegios de lectura a grupo-qa en el proyecto user0X-rbac.
```
oc policy add-role-to-group view grupo-qa -n user0X-rbac
````
Revise todos los enlaces de roles del proyecto user0X-rbac para verificar que asignen los roles a los grupos y usuarios correctos. En la siguiente salida, se omiten los enlaces de roles predeterminados asignados por OpenShift a las cuentas de servicio
```
oc get rolebindings -o wide
````
Con el usuario developer, implemente un servidor de Apache HTTP para verificar que el usuario developer tenga privilegios en el proyecto.
```
oc login -u developer
````
Implemente un servidor de Apache HTTP mediante el flujo de imágenes estándares
de OpenShift.
```
oc new-app --name httpd httpd:2.4
````
Intente otorgar privilegios de escritura al usuario pruebas. Esto debería generar errores.
```
oc policy add-role-to-user edit pruebas
````
Verifique que el usuario pruebas solo tenga privilegios de lectura en la aplicación httpd.

Inicie sesión con el usuario pruebas.
```
oc login -u pruebas
````
Intente escalar la aplicación httpd. Esto debería generar errores.
```
oc scale deployment httpd --replicas 5
````
