Para poder tener una buena instalación es necesario instaalr tanto utilidades como dependencias.

Utilidades

`sudo yum install -y yum-utils device-mapper-persistent-data lvm2`

Agregar el repo de docker

`sudo yum-config-manager --add-repo https://download.docker.com/linux/cen...`

Crear llave GPG para repositorio de docker

`curl -fsSL https://download.docker.com/linux/centos/gpg | sudo apt-key add -`

Instalar docker. Se puede agregar -ce -y para aceptar todas las preguntas de la instalación

`sudo yum install docker-ce -y`

Iniciar el servicio

`sudo systemctl start docker` 

Iniciarlo con el sistema 

`sudo systemctl enable docker`

Agregar usuario al grupo docker whoami 

Saber el nombre de tu usuario

`sudo usermod -aG docker nombre_de_salida_en_whoami`

Con `docker ps` se puede ver todos lo que se tiene de contenedores... o con `docker run hello_world`

Salir de la sesión `exit`

Comprobamos que nuestro Docker este correcto

`sudo docker ps -a`

Iniciar de nuevo con el usuario y probar docker 

`run hello-world`

Los archivos de docker se almacenan en la siguiente ruta, donde vamos a poder ver todos los archivos de docker 

`sudo docker info:sudo ls /var/lib/docker/ -l`

//////////////////////////

Realizar una actualización de paquetes

* Para realizar la instalación de docker se necesitan tener todas las utilidades a considerar.

sudo yum install -y yum-utils device-mapper-persistent-data lvm2

* Posteriormente se instalarán las dependencias.

sudo yum-config-manager --add-repo https://download.docker.com/linux/cen...

* Instalar docker con -ce y para aceptar todas las preguntas que haya dentro de la instalación

sudo yum install docker-ce -y

* Inicializar el servicio
  
  sudo systemctl start docker

* Iniciarlo con el sistema
  
  sudo systemctl enable docker

* Agregar usuario al grupo docker se utiliza
  
  whoami para saber el nombre de tu usuario y después
  
  sudo usermod -aG docker __nombre_de_salida_en_whoami__

* Salir de la sesión

exit

* Comprobamos que nuestro Docker este correcto

sudo docker ps -a

* Iniciar de nuevo con el usuario y probar

docker run hello-world

(podemos ver que está funcionando correctamente)

* Los archivos de docker se almacenan en la siguiente ruta, donde vamos a poder ver todos los archivos de docker

sudo docker info:sudo ls /var/lib/docker/ -l

//////////////////////

contiene las capas necesarias para crear una imágen

vi dockerfile se coloca el sistema operativo trabajando o la aplicación a instalar

```cmd 
vi dockerfile
FROM centos:7
RUN yum install mysql
CMD ["bash"]
```


