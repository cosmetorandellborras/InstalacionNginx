# Instalación y configuración del servidor web Nginx: Virtual Hosts

## Objetivos
Los objetivos de esta práctica son desplegar un servidor web Nginx desde Ubuntu y configurar dos virtual hosts que nos permitira acceder a dos sitios web diferentes alojados en el mismo servidor nginx.

## Instalación Nginx
### Paso 1
Primeramente abriremos la terminal de Ubuntu e introduciremos el siguiente comando.
~~~
sudo apt-get install nginx
~~~
![Captura1](https://github.com/cosmetorandellborras/InstalacionNginx/blob/main/Captura1.png)

### Paso 2
Una vez instalado, Nginx en Ubuntu se inicia de manera automática. Para comprobar si efectivamente se ha instalado de manera correcta, abrimos nuestro navegador web, introducimos como direccion localhost y nos tendrá que salir la pagina de confirmación de que Nginx se ha instalado y funciona de manera correcta.
![Captura2](https://github.com/cosmetorandellborras/InstalacionNginx/blob/main/Captura2.png)

## Configuración Nginx
### Paso 1
En primer lugar nos dirigimos al directorio /etc/nginx/sites-available/ con el siguiente comando.
~~~
cd /etc/nginx/sites-available/
~~~
Seguidamente copiamos el archivo default de dicho directorio y le damos preferiblemente el nombre de nuestro dominio, haremos tantas copias como diferentes dominios queramos configurar.
~~~
sudo cp default prueba1.nginx
~~~
![Captura3](https://github.com/cosmetorandellborras/InstalacionNginx/blob/main/Captura3.png)
### Paso 2
Procedemos a abrir con un editor de textos los archivos que hemos creado en el paso anterior con el siguiente comando
~~~
sudo nano prueba1.nginx
~~~
En ellos tenemos que modificar los siguientes parámetros:
1. Eliminar default_server
2. En el campo "root" modificar la ruta donde estarán nuestros archivos html
3. Modificar el nombre del servidor, con el nombre de nuestro dominio
![Captura4](https://github.com/cosmetorandellborras/InstalacionNginx/blob/main/Captura4.png)
**Este paso hay que realizarlo con todos los archivos que hemos creado en el paso anterior**
### Paso 3
Nos posicionamos en el directorio sites-enabled y lanzamos el comando "ll" para ver la informacion detallada del contenido del directorio mediante los siguientes comandos
~~~
cd ..
cd sites-enabled/
ll
~~~
![Captura6](https://github.com/cosmetorandellborras/InstalacionNginx/blob/main/Captura6.png)
### Paso 4
Hacemos un link simbólico de los archivos de sites-available en el directorio sites-enabled mediante los siguientes comandos
~~~
sudo ln -s ../sites-available/prueba1.nginx
sudo ln -s ../sites-available/prueba2.nginx
~~~
![Captura7](https://github.com/cosmetorandellborras/InstalacionNginx/blob/main/Captura7.png)
### Paso 5
Reiniciamos el servicio Nginx con los siguientes comandos
~~~
sudo service nginx restart
sudo nginx -s reload
~~~
![Captura8](https://github.com/cosmetorandellborras/InstalacionNginx/blob/main/Captura8.png)
### Paso 6
Añadimos los dominios al archivo hosts de nuestro equipo, para qu al introducir las direcciones en nuestro navegador el equipo sepa a que dirección ip tiene que conectar.
Para ello modificamos el archivo hosts que se encuentra en la ruta /etc/hosts mediante el siguiente comando.
~~~
sudo nano /etc/hosts
~~~
![Captura9](https://github.com/cosmetorandellborras/InstalacionNginx/blob/main/Captura9.png)
### Paso 7
Creamos los directorios donde irán los archivos html, debemos crear los directorios en la misma ruta indicada en el archivo de configuracion de cada dominio que hemos realizado al principio del tutorial.
Para ello, nos situamos en el directorio donde queremos crear los directorios y los creamos mediante los siguientes comandos.
~~~
cd /var/www
sudo mkdir prueba1
sudo mkdir prueba2
~~~
![Captura10](https://github.com/cosmetorandellborras/InstalacionNginx/blob/main/Captura10.png)
### Paso 8
Insertamos el archivo html de cada web en el directorio creado en el paso anterior, cada uno irá en su carpeta correspondiente.
Seguidamente renombramos el nombre del archivo html a "index.html" en caso de que no se llame así.
Esto lo haremos con los siguientes comandos.
~~~
sudo cp /home/cosmetorandell/Desktop/mini_car_game.html /var/www/prueba1/
cd prueba1
mv mini_car_game.html index.html
~~~
![Captura11](https://github.com/cosmetorandellborras/InstalacionNginx/blob/main/Captura11.png)
**Este paso hay que realizarlo con cada archivo html**
## Comprobaciones
Una vez realizado todo el apartado de configuración, procederemos a abrir nuestro navegador e introducir la dirección de cada dominio creado. Si la configuración se ha realizado de manera exitosa nos aparecerá la web que hemos configurado.

Por ejemplo, en nuestro caso se han configurado dos dominios, uno llamado prueba1.nginx y otro llamado prueba2.nginx

Si introducimos en el navegador el primer dominio nos aparecerá la primera web que hemos configurado.
![Captura12](https://github.com/cosmetorandellborras/InstalacionNginx/blob/main/Captura12.png)
Si introducimos en el navegador el segundo dominio nos aparecerá la segunda web que hemos configurado.
![Captura13](https://github.com/cosmetorandellborras/InstalacionNginx/blob/main/Captura13.png)

Como podemos comprobar, la configuración se ha realizado correctamente y se da por finalizado el tutorial.


