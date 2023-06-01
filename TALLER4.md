## Creacion de usuarios Locales

cree un nuevo usuario de HTPasswd

Extraiga los datos del archivo del secreto y guardelo en la ruta /tmp


```
oc extract secret/localusers -n openshift-config > --to ~/DO280/labs/auth-provider/ --confirm

````
