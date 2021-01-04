# 3.Crea un contenedor con las siguientes especificaciones:
a. Utilizar la imagen base NGINX haciendo uso de la versión 1.19.3
b. Al acceder a la URL localhost:8080/index.html aparecerá el mensaje
HOMEWORK 1
Copiar el contenido de index.html
c. Persistir el fichero index.html en un volumen llamado static_content

Crear una carpeta para el container nginx
 mkdir answer_exercise_3

Crear el index.html  con el mensaje "HOMEWORK 1" que va a sustituir al index.html predeterminado de Nginx.
 touch answer_exercise_3/index.html

 Crear un contenedor nuevo a partir de la imagen de nginx version-1.19.3, con el nombre nginx-hw01 en el puerto 8080, y un volumen static_content con el contenido del directorio / usr/share/nginx/html del contenedor, que es donde Nginx almacena su contenido HTML predeterminado.
 docker container run -d --name nginx-hw01 -p 8080:80 -v static_content:/usr/share/nginx/html nginx:1.19.3

 Copiar el index.html que creamos en nuestro sistema local al directorio que contiene el contenido HTML 
 docker cp answer_exercise_3/index.html nginx-hw01:usr/share/nginx/html/index.html

Nota: Adjuntar una breve explicación de todos los pasos que has seguido para la consecución de los objetivos marcados en el enunciado y todos los comandos/ficheros utilizados
