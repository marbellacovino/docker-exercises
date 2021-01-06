# Crea un contenedor con las siguientes especificaciones:
  -  Utilizar la imagen base NGINX haciendo uso de la versión 1.19.3
  -  Al acceder a la URL localhost:8080/index.html aparecerá el mensaje HOMEWORK 1
  -  Copiar el contenido de index.html
  -  Persistir el fichero index.html en un volumen llamado static_content

# Desarrollo
Correr los siguientes comandos en el terminal dentro del directorio hw-01:

Crear una carpeta para el container nginx
```sh
$  mkdir answer_exercise_3
```
Crear el index.html  con el mensaje "HOMEWORK 1" que va a sustituir al index.html predeterminado de Nginx.
```sh
$ touch answer_exercise_3/index.html
```
Editar el index.html creado con el siguiente contenido:
```html
<!DOCTYPE html>
<html>
<head>
<title>HOMEWORK 1</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>HOMEWORK 1</h1>
<p>Imagen base NGINX haciendo uso de la versión 1.19.3</p>

</body>
</html>
```

 Crear un contenedor nuevo a partir de la imagen de nginx version-1.19.3, con el nombre nginx-hw01 en el puerto 8080, y un volumen static_content con el contenido del directorio / usr/share/nginx/html del contenedor, que es donde Nginx almacena su contenido HTML predeterminado.
 ```sh
 docker container run -d --name nginx-hw01 -p 8080:80 -v static_content:/usr/share/nginx/html nginx:1.19.3
 ```
 Para revisar que nuestro contenedor se ha creado y esta corriendo...
  ```sh
 docker container ls
 ```
 ![Alt text](/hw-01/images/nginx-1.0 "Contenedores Corriendo")

 Copiar el index.html que creamos en nuestro sistema local al directorio que contiene el contenido HTML 
  ```sh
 docker cp answer_exercise_3/index.html nginx-hw01:usr/share/nginx/html/index.html
 ```
 Para verificar que todo funciona navegar a la dirección del servidor en el navegador deseado
```sh
http://localhost:8080/
```
 ![Alt text](/hw-01/images/nginx-1.1 "index")