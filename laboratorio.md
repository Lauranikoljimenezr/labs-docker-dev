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
