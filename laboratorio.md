# Labs Docker Dev 

## Pulling an image (Descargar una imagen)

```sh
 docker pull nginx

Using default tag: latest
latest: Pulling from library/nginx
efc2b5ad9eec: Pull complete 
8fe9a55eb80f: Pull complete 
045037a63be8: Pull complete 
7111b42b4bfa: Pull complete 
3dfc528a4df9: Pull complete 
9e891cdb453b: Pull complete 
0f11e17345c5: Pull complete 
Digest: sha256:6af79ae5de407283dcea8b00d5c37ace95441fd58a8b1d2aa1ed93f5511bb18c
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest

## Ejercicio 1.1: Descargar la imagen oficial de Ubuntu

```sh
docker pull ubuntu

Using default tag: latest
latest: Pulling from library/ubuntu
9c704ecd0c69: Pull complete 
Digest: sha256:2e863c44b718727c860746568e1d54afd13b2fa71b160f5cd9058fc436217b30
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest

3.9: Pulling from library/python
...
Status: Downloaded newer image for python:3.9
docker.io/library/python:3.9


## 2.1. Ejecuta un contenedor de Ubuntu en modo interactivo

 docker run -it ubuntu bash


Unable to find image 'ubuntu:latest' locally
latest: Pulling from library/ubuntu
...
root@<container_id>:/


## 2.2. Ejecuta un servidor web Apache en segundo plano, mapeando el puerto 8000 del host al puerto 80 del contenedor


docker run -d -p 8000:80 httpd


Unable to find image 'httpd:latest' locally
latest: Pulling from library/httpd
...
<container_id>


## Ejercicio 3.1: Eliminar el contenedor de Ubuntu

```sh
docker rm 8ed70b67aa5f


## Ejercicio 3.2: Eliminar todos los contenedores detenidos

```sh
docker container prune

WARNING! This will remove all stopped containers.
Are you sure you want to continue? [y/N]

## Ejercicio 1: Crear un Dockerfile simple con Ubuntu y actualizar paquetes
FROM ubuntu:latest
RUN apt-get update && apt-get upgrade -y

Comando para construir:

 docker build -t ubuntu-updated:latest .

[+] Building 9.7s (6/6) FINISHED                                                                                                                 docker:default
 => [internal] load build definition from Dockerfile                                                                                                       0.0s
 => => transferring dockerfile: 96B                                                                                                                        0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                                           0.0s
 => [internal] load .dockerignore                                                                                                                          0.1s
 => => transferring context: 2B                                                                                                                            0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest                                                                                                             0.1s
 => [2/2] RUN apt-get update && apt-get upgrade -y                                                                                                         8.4s
 => exporting to image                                                                                                                                     0.7s
 => => exporting layers                                                                                                                                    0.6s
 => => writing image sha256:2dad02e0bf7806b5b548c5cd0d273930516f417aef367c7a735b430a1a4f2857                                                               0.0s
 => => naming to docker.io/library/ubuntu-updated:latest


## Ejercicio 3: Crear un Dockerfile para instalar Nginx en Ubuntu

Comando para construir: 

docker build -t ubuntu-updated:latest .


[+] Building 13.3s (6/6) FINISHED                                                                                                                docker:default
 => [internal] load build definition from Dockerfile                                                                                                       0.0s
 => => transferring dockerfile: 137B                                                                                                                       0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                                           0.0s
 => [internal] load .dockerignore                                                                                                                          0.0s
 => => transferring context: 2B                                                                                                                            0.0s
 => CACHED [1/2] FROM docker.io/library/ubuntu:latest                                                                                                      0.0s
 => [2/2] RUN apt-get update && apt-get install -y nginx                                                                                                  12.2s
 => exporting to image                                                                                                                                     0.6s
 => => exporting layers                                                                                                                                    0.5s
 => => writing image sha256:6538f7d26fd5a0df6d20ebba08aa96125529b3b57f80b16fbb75f0b01bc70631                                                               0.0s
 => => naming to docker.io/library/ubuntu-updated:latest  


 ##Ejercicio 4: Construir y ejecutar la imagen de Nginx

 Construir:

 docker build -t my-nginx:latest .

 [+] Building 0.4s (6/6) FINISHED                                                                                                                 docker:default
 => [internal] load build definition from Dockerfile                                                                                                       0.0s
 => => transferring dockerfile: 137B                                                                                                                       0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                                           0.0s
 => [internal] load .dockerignore                                                                                                                          0.0s
 => => transferring context: 2B                                                                                                                            0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest                                                                                                             0.0s
 => CACHED [2/2] RUN apt-get update && apt-get install -y nginx                                                                                            0.0s
 => exporting to image                                                                                                                                     0.1s
 => => exporting layers                                                                                                                                    0.0s
 => => writing image sha256:6538f7d26fd5a0df6d20ebba08aa96125529b3b57f80b16fbb75f0b01bc70631                                                               0.0s
 => => naming to docker.io/library/my-nginx:latest 

 Ejecutar:

 docker run -d -p 80:80 my-nginx:latest

9ab81f82d6969477b26279c9e302e009d2bb7075ef32806b58c8c4b51445207a

##Ejercicio 5: Modificar el Dockerfile de Nginx para exponer el puerto 80

Reconstruir:

docker build -t my-nginx:latest .

[+] Building 0.5s (6/6) FINISHED                                                                                                                 docker:default
 => [internal] load build definition from Dockerfile                                                                                                       0.0s
 => => transferring dockerfile: 147B                                                                                                                       0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                                           0.0s
 => [internal] load .dockerignore                                                                                                                          0.0s
 => => transferring context: 2B                                                                                                                            0.0s
 => [1/2] FROM docker.io/library/ubuntu:latest                                                                                                             0.0s
 => CACHED [2/2] RUN apt-get update && apt-get install -y nginx                                                                                            0.0s
 => exporting to image                                                                                                                                     0.1s
 => => exporting layers                                                                                                                                    0.0s
 => => writing image sha256:c8de7f05590ce97d277e87327b63c11195cab2e1607e77684eff5de93209c9ec                                                               0.0s
 => => naming to docker.io/library/my-nginx:latest   


 