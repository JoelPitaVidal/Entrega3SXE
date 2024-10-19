# Entrega3SXE

## Pásos seguidos durante el proceso:

>1. Descarga la imagen 'httpd' y comprueba que está en tu equipo.

Descargámos la imágen con el comando -`sudo docker pull httpd:2.4`
y con -`sudo docker images` comprobamos que está instalada

>2. Crea un contenedor con el nombre 'dam_web1'.

Para creár el contenedor utilizámos el comando 
-`sudo docker container create -i -t --name dam-web1 httpd`
y con -`sudo docker ps -a` comprobamos que este está creado


>3. 3. Si quieres poder acceder desde el navegador de tu equipo,
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
