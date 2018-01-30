# Ejercicio 4 - Freddy Javier Frere Quintero
## Ejercicio 1
### Instalar una máquina virtual Debian usando Vagrant y conectar con ella.

Procedemos a instalar Vagrant con el siguiente comando:

```sudo apt install vagrant```

En la imagen detalla la versión que se instalo.

![captura1](https://user-images.githubusercontent.com/32844919/35360619-a7e14b00-015e-11e8-870d-ca15c0f1a7d4.PNG)


Procedemos a ingresar en la consola los siguientes comandos para proceder a instalar la maquina:

```vagrant box add debian-jessie https://github.com/holms/vagrant-jessie-box/releases/download/Jessie-v0.1/Debian-jessie-amd64-netboot.box```

![captura2](https://user-images.githubusercontent.com/32844919/35361033-1883c828-0160-11e8-8c2e-ef79e858cd4f.PNG)

Nos conectaremos por medio de **ssh** a la VM:

```vagrant ssh```


## Ejercicio 2
### Instalar una máquina virtual ArchLinux o FreeBSD para KVM, otro hipervisor libre, usando Vagrant y conectar con ella.

## Ejercicio 3
### Crear un script para provisionar de forma básica una máquina virtual para el proyecto que se esté llevando a cabo en la asignatura. 


## Ejercicio 4
### Buscar alguna demo interesante de Docker y ejecutarla localmente, o en su defecto, ejecutar la imagen anterior y ver cómo funciona y los procesos que se llevan a cabo la primera vez que se ejecuta y las siguientes ocasiones.


## Ejercicio 5
### Configurar tu máquina virtual usando `vagrant` con el provisionador ansible.

