# Ejercicio 2 Owncloud - Freddy Javier Frere Quintero

## 1.- Crear una máquina Virtual en Nube
Para crear la máquina virtual podemos utilizar la plataforma de Microsoft Azure 
![imagen 0](https://user-images.githubusercontent.com/32844919/32694276-887c91e0-c73c-11e7-95bc-1dc920c4fdfd.JPG)

## 2.-  Conectarse a la máquina Virtual 
Para conectarse a la máquina virtual podemos usar la aplicación “Putty”
![imagen 0 1](https://user-images.githubusercontent.com/32844919/32694285-a9a35098-c73c-11e7-8b11-b8c9615952f6.JPG)

## Ejercicio 1
### 3.- Instalar chef-solo 
Para realizar la instalación debemos escribir la siguiente línea de comandos.

```Apt-get install chef-solo ```

```curl -L https://www.opscode.com/chef/install.sh | bash```

Ya instalado podemos verificar que se ha instalado correctamente ingresando la siguiente línea de comando 

```Chef-solo --version``` 

![imagen 1](https://user-images.githubusercontent.com/32844919/32694308-095a7cd2-c73d-11e7-8eb8-93d02d22a3ac.JPG)

## Ejercicio 2
### 4.- Crear una receta para instalar nginx, tu editor favorito y algún directorio y fichero que uses de forma habitual.
Para crear una receta debemos instalar un editor de texto con el que te sientas más cómodo.
 * Instalar el nginx debemos escribir la siguiente línea de comando 

 * Creamos el directorio donde se incluirá la receta “default.rb”

```mkdir -p ~/chef/cookbooks/nginx/recipes``` 

 * Creamos la receta en el fichero “default.rb” 
``` 
package 'nginx'
package 'emacs'
directory '/home/javier/Documentos'
file "/home/javier/Documentos/LEEME" do
	owner "javier"
	group "javier"
	mode 00544
	action :create
	content "Instalación de "
end
```
 * Creamos el fichero “node.json”
```
 {
    "run_list":["recipe[nginx]"]
  }
```

 * Creamos el fichero de configuración “solo.rb”  
```
  file_cache_path "/home/javier/chef"
  cookbook_path "/home/javier/chef/cookbooks"
  json_attribs "/home/javier/chef/node.json"
``` 
 * Escribimos el comando 
``` sudo chef-sole –c chef/solo.rb```
![imagen 14](https://user-images.githubusercontent.com/32844919/32694331-739fd862-c73d-11e7-9720-1e68f3a7989a.JPG)

## Ejercicio 3 
### 5.- Escribir en YAML la siguiente estructura de datos en: 
```
JSON { uno: "dos", tres: [ 4, 5, "Seis", { siete: 8, nueve: [ 10, 11 ] } ] }
```
![json](https://user-images.githubusercontent.com/32844919/32694334-861bbdbc-c73d-11e7-9afc-178f75cae49c.JPG)
```
YAML
```
![yaml](https://user-images.githubusercontent.com/32844919/32694335-8ddff202-c73d-11e7-93f4-3b1b5ed2b0aa.JPG)
