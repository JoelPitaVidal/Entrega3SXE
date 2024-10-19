# Entrega3SXE

## Pásos seguidos durante el proceso:

>1. Descarga la imagen 'httpd' y comprueba que está en tu equipo.

Descargámos la imágen con el comando -`sudo docker pull httpd:2.4`
y con -`sudo docker images` comprobamos que está instalada

>2. Crea un contenedor con el nombre 'dam_web1'.

Para creár el contenedor utilizámos el comando 
-`sudo docker container create -i -t --name dam-web1 httpd`
y con -`sudo docker ps -a` comprobamos que este está creado


>3.Si quieres poder acceder desde el navegador de tu equipo,
>¿que debes hacer? Utiliza bind mount para que el directorio del apache2
>'htdocs' esté montado un directorio que tu elijas.

Instalamos ssh y lo configuramos para establecer conexión con la máquina anfitriona
con el comandoo -`sudo apt install openssh-server`

mapeamos el puerto del contenedor al puerto del equipo:
-`sudo docker run -d --name dam_web1 -p 8000:80 httpd:2.4`

Una vez echo esto, creámos un nuevo directório:
-`mkdir /home/dam2/mi_apache_host`

ejecutamos el siguiente comando para crear el contenedor con el directorio mapeado:
-`sudo docker run -d --name dam_web1 -p 8000:80 -v /home/dam2/mi_apache_host:/usr/local/apache2/htdocs httpd:2.4`

>4. Realiza un 'hola mundo' en html y comprueba que accedes desde el navegador.

Creámos un archivo .html y lo metemos en la carpéta /home/dam2/mi_apache_host, luego lo abrímos
en el navegador:-`http://10.0.9.151:8000` , la sintaxis del hola mundo es la siguiente: 

```
<html>
     <head>
         <title>Hola Mundo</title>
     </head>
     <body>
         <h1>Hola Mundo</h1>
     </body>
 </html>
```

>5. Crea otro contenedor 'dam_web2' con el mismo bind mount y a otro puerto, por ejemplo 9080.

Creámos el contenedor dam_web2 con puertos diferentes:
-`sudo docker run -d --name dam_web2 -p 9080:80 -v /home/dam2/mi_apache_host:/usr/local/apache2/htdocs httpd:2.4`
Comprobamos que funciona con -`sudo docker ps`

>6. Comprueba que los dos servidores 'sirven' la misma página, es decir, cuando consultamos en el navegador: http://localhost:9080 http://localhost:8000

Acedemos al navegador e introducimos las siguientes sentencias:
-`http://10.0.9.151:9080`
-`http://10.0.9.151:8000`
