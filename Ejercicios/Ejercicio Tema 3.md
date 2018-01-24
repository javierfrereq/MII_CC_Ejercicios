# Ejercicio 3 - Freddy Javier Frere Quintero
## Ejercicio 1
### Crear una máquina virtual Ubuntu e instalar en ella un servidor nginx para poder acceder mediante web.

Se procedió a instalar el comando:

```az group create --name CCJavier --location westeurope```

```az vm create -g CCJavier -n Ejercicio --image UbuntuLTS```

Podemos observar que se creó la máquina virtual.

![captura1](https://user-images.githubusercontent.com/32844919/35331293-0a5ebcfc-0107-11e8-9108-bc2aa2fcdd63.PNG)

Luego procederemos a conectarnos a la VM y para ello lo haremos por medio de SSH: 

```ssh javier@52.174.176.246```

Una vez conectados a la VM procederemos a instalarle los siguientes comandos: 

```sudo apt-get update```

```sudo apt-get install nginx```

La siguiente imagen detalla se instaló correctamente los comandos:

![captura2](https://user-images.githubusercontent.com/32844919/35331575-298de7fa-0108-11e8-94e0-c1d73a6c0cbd.PNG)

Procedemos a detener la VM que se creó en la nube con el siguiente comando:

```az vm stop -g CCJavier -n Ejercicio```

## Ejercicio 2
### Crear una instancia de una máquina virtual Debian y provisionarla usando alguna de las aplicaciones vistas en el tema sobre herramientas de aprovisionamiento.

Para crear una VM en Debian procederemos a escribir el siguiente comando: 

```az vm create -g CCJavier -n EjercicioDebian --image Debian```

Podemos observar que se creó la máquina virtual.

![captura3](https://user-images.githubusercontent.com/32844919/35332032-e7db65e2-0109-11e8-8361-b77c18dba9a0.PNG)

Ya una vez creada la VM procederemos a provisionar y para ello debemos agregar en los hosts de ansible la VM creada, la ruta es la siguiente: 

```/etc/ansible/hosts ```

> [project]
> 52.166.129.248 ansible_user=javier

Procederemos a provisionar la VM, la receta para aquello es la siguiente: 
```
---
- hosts: 52.166.129.248
  sudo: yes
 
 tasks:

  # Actualización del sistema
    - name: update apt cache
      apt: update_cache=yes

 # Instalación de Apache
    - name: install apache
      apt: name=apache2 state=present

 # Instalación de mysql
    - name: install mysql
      apt: name=mysql-server state=present

 # Instalación de php
    - name: install php
      apt: name=php5 state=present
```

Luego procedemos a ejecutar el siguiente comando:

```ansible-playbook provision.yml```


