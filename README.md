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
**Este paso hay que realizarlo con todos los archivos que hemos creado en el paso anterior**
![Captura4](https://github.com/cosmetorandellborras/InstalacionNginx/blob/main/Captura4.png)
### Paso 3
