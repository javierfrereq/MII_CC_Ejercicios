# Ejercicio 5 - Freddy Javier Frere Quintero
## Ejercicio 1
### Instala LXC en tu versión de Linux favorita. Normalmente la versión en desarrollo, disponible tanto en GitHub como en el sitio web está bastante más avanzada; para evitar problemas sobre todo con las herramientas que vamos a ver más adelante, conviene que te instales la última versión y si es posible una igual o mayor a la 2.0.

Se procedió a instalar el comando:

```sudo apt install lxc1```

En la imagen detalla la versión que se instalo

![captura2](https://user-images.githubusercontent.com/32844919/35044598-53904790-fb91-11e7-91cd-afb92a5f2ed9.PNG)

Luego se creó varios contenedores de la siguiente manera: 

```sudo lxc-create -t ubuntu -n una-caja```

•Comando para realizar la creación de contenedor en la Nube 

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

Se procede a modificar el archivo ```hosts``` de ```ansible``` que se encuentra en la ruta ```$ /etc/ansible/hosts``` indicando el nodo en donde se va a ejecutar la tarea que se le va a especificar de manera automática. 

``` [webserver] IP```

Se procede a crear un playbook de nombre provision.yml la cual tendrá la configuración necesaria para realizar el ejercicio.

> -hosts: all
> sudo: yes
> task:
> apt pkg={{ item }} state=installed
> with_items:
> -lxc 
> action: sudo lxc-create -n ubuntu-lxc -t ubuntu 

## Ejercicio 4
### Buscar alguna demo interesante de Docker y ejecutarla localmente, o en su defecto, ejecutar la imagen anterior y ver cómo funciona y los procesos que se llevan a cabo la primera vez que se ejecuta y las siguientes ocasiones.

Se procedió a ejecutar el comando que está en la guía de los ejercicios que el siguiente:

```sudo  sudo docker run --rm jjmerelo/docker-daleksay -f smiling-octopus Uso argumentos, ea```


En la siguiente imagen se puede observar que al ser la primera ejecución se descarga la imagen y se instala. 

![captura ejercicio 4 1](https://user-images.githubusercontent.com/32844919/35071279-7a474b0a-fbe0-11e7-9bea-500b1346834a.PNG)

En esta imagen ya está disponible la imagen solo se ejecuta el proceso

![captura ejercicio 4](https://user-images.githubusercontent.com/32844919/35071300-85b896ba-fbe0-11e7-928f-7914d83d4320.PNG)

## Ejercicio 5
### Comparar el tamaño de las imágenes de diferentes sistemas operativos base, Fedora, CentOS y Alpine, por ejemplo.
Se procede a escribir el comando ```sudo docker images``` la cual nos permitirá visualizar el tamaño que tienen las imágenes creadas, en la siguiente imagen se puede ver un ejemplo:

![captura ejercicio 5](https://user-images.githubusercontent.com/32844919/35071710-ff63c204-fbe1-11e7-9176-9641f56a5000.PNG)

## Ejercicio 6
### Crear a partir del contenedor anterior una imagen persistente con commit.

Se procede escribir el comando ```sudo docker ps -a``` la cual nos da la información del ```CONTAINER ID``` para poder realizar el commit. 
A partir del contenedor ```prueba2``` se procederá a crear una nueva imagen con el siguiente comando:

```sudo docker commit 1db2626a58ef cambiarprueba2```

En la siguiente imagen se puede observar como se lo realizo: 

![captura ejercicio 6](https://user-images.githubusercontent.com/32844919/35072208-e91fa95c-fbe3-11e7-8a6b-88d6d197a81c.PNG)

## Ejercicio 7
### Examinar la estructura de capas que se forma al crear imágenes nuevas a partir de contenedores que se hayan estado ejecutando.

Con el siguiente comando se procedió a realizar el requerimiento del Ejercicio 7:

```sudo jq '.' /var/lib/docker/image/aufs/imagedb/content/sha256/92d1ff1b6de9e6290afa3e0400395a73250800500810af18eb1d5da1b5db4ea2```

En la siguiente imagen se puede observar el resultado: 

![captura ejercicio 7](https://user-images.githubusercontent.com/32844919/35072314-52b7b8a0-fbe4-11e7-9ab8-c7ac67d4d881.PNG)

## Ejercicio 8
### Crear un volumen y usarlo, por ejemplo, para escribir la salida de un programa determinado.

Se creó el archivo bm.sh en la ruta /app luego se procedió a probarlo en 3 sistemas diferente, en la siguiente imagen se puede observar las cantidades de archivos que hay en cada sistema.

![captura ejercicio 8](https://user-images.githubusercontent.com/32844919/35072529-3e9f8fd6-fbe5-11e7-842e-551997d6dfc3.PNG)


## Ejercicio 9
### Usar un miniframework REST para crear un servicio web y introducirlo en un contenedor, y componerlo con un cliente REST que sea el que finalmente se ejecuta y sirve como “frontend”.

[Enlace](https://github.com/javierfrereq/MII_CC_Proyecto_MicroServicios/tree/master/contenedores)

## Ejercicio 10
### Reproducir los contenedores creados anteriormente usando un Dockerfile.

## Ejercicio 11
### Crear con docker-machine una máquina virtual local que permita desplegar contenedores y ejecutar en él contenedores creados con antelación.

