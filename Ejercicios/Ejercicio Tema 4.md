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

**Vagrantfile**

```
Vagrant.configure("2") do |config|
    config.vm.box = "javierfrere"
    config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
end
config.vm.provision "shell",
    inline: "sudo apt-get install -y nginx && sudo service nginx restart && sudo service nginx status"
end
```

Procedemos a provisionar 
* `vagrant provision`

## Ejercicio 3
### Crear un script para provisionar de forma básica una máquina virtual para el proyecto que se esté llevando a cabo en la asignatura. 
```
Vagrant.configure("2") do |config|
	config.vm.box = "ubuntu"
	config.ssh.insert_key = false
	config.vm.provision "shell",
		inline: "sudo apt-get install -y python3-dev python3-pip git"
		inline: "sudo pip install mysql-python"
  end
end
```

## Ejercicio 4
### Configurar tu máquina virtual usando `vagrant` con el provisionador ansible.

1.- Descargamos una imagen a nuestra preferencia.
```
vagrant box add centos https://github.com/tommy-muehle/puppet-vagrant-boxes/releases/download/1.1.0/centos-7.0-x86_64.box
```

2.- Iniciamos la imagen

`vagrant init centos`

3.- Creamos el Vagrantfile con su provisionamiento con Ansible.

```
Vagrant.configure("2") do |config|
	config.vm.box = "centos"
	config.ssh.insert_key = false
	config.vm.provision "ansible" do |ansible|
		ansible.playbook = "provision.yml"
  end
end
```
![ansible](https://user-images.githubusercontent.com/32844919/35768218-9e2e8e8c-08f8-11e8-9f4c-793b163e5f16.PNG)


