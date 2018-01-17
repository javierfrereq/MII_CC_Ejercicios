# Ejercicio 5 - Freddy Javier Frere Quintero
## Ejercicio 1
### Instala LXC en tu versión de Linux favorita. Normalmente la versión en desarrollo, disponible tanto en GitHub como en el sitio web está bastante más avanzada; para evitar problemas sobre todo con las herramientas que vamos a ver más adelante, conviene que te instales la última versión y si es posible una igual o mayor a la 2.0.

Se procedió a instalar el comando:
```sudo apt install lxc1```
En la imagen detalla la versión que se instalo
![captura2](https://user-images.githubusercontent.com/32844919/35044598-53904790-fb91-11e7-91cd-afb92a5f2ed9.PNG)

Luego se creó varios contenedores de la siguiente manera: 
```sudo lxc-create -t ubuntu -n una-caja```
•	Comando para realizar la creación de contenedor en la Nube 
```sudo lxc-create -t ubuntu-cloud -n nubecilla```
La siguiente imagen detalla que se crearon los contenedores correctamente:
![captura7](https://user-images.githubusercontent.com/32844919/35044882-3a20df9e-fb92-11e7-8a95-e69137fae5cf.PNG)

Procedemos a iniciar el contenedor que se creó en la nube con los siguientes comandos:
```sudo lxc-start -n nubecilla```
Procedemos a conectar mediante el siguiente comando al contenedor que se creó en la nube, lo detalla en la siguiente imagen:
```sudo lxc-console -n nubecilla```
![captura6](https://user-images.githubusercontent.com/32844919/35044810-05f62b0c-fb92-11e7-9a90-3a64aae57993.PNG)

## Ejercicio 2
### Instalar una distro tal como Alpine y conectarse a ella usando el nombre de usuario y clave que indicará en su creación
Para verificar los distritos que podemos usar, lo hacemos con el siguiente comando: 
```$ cd /usr/share/lxc/templates```
Luego escribir un ```ls``` 
La siguiente imagen lo detalla:
![captura8](https://user-images.githubusercontent.com/32844919/35045267-8a8efcbc-fb93-11e7-979d-7c3d9be9c55e.PNG)

Se procedió a crear un contenedor en la nube con el distrito de “Alpine“y con el nombre “nubeUgr“ con el siguiente comando:
```sudo lxc-create -t alpine -n nubeUgr```
Podemos observar en la siguiente imagen que el contenedor se creó de manera correcta.
![captura10](https://user-images.githubusercontent.com/32844919/35045404-091bacc4-fb94-11e7-86f7-e1cafee7aeb0.PNG)

Procedemos a conectarnos al contenedor de Alpine que se creó como lo detalla en la siguiente imagen:
![capturademoconexion](https://user-images.githubusercontent.com/32844919/35045529-6a6d8db2-fb94-11e7-9799-9ad7d1dd922e.PNG)

## Ejercicio 3
### Provisionar un contenedor LXC usando Ansible o alguna otra herramienta de configuración que ya se haya usado

