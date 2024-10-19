# Entrega3SXE

## Pásos seguidos durante el proceso:

>1. Descarga la imagen 'httpd' y comprueba que está en tu equipo.

Descargámos la imágen con el comando -`sudo docker pull httpd:2.4`
y con -`sudo docker images` comprobamos que está instalada

>2. Crea un contenedor con el nombre 'dam_web1'.

Para creár el contenedor utilizámos el comando 
-`sudo docker container create -i -t --name dam-web1 httpd`
y con -`sudo docker ps -a` comprobamos que este está creado


