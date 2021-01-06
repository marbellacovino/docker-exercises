# Caso de uso 
La compañía para la que trabajáis estudia la posibilidad de incorporar a nivel interno una herramienta para la monitorización de logs. Para ello, os han encomendado la tarea de realizar una **“Proof of Concept” (PoC)**. Tras evaluar diferentes productos, habéis considerado que una buena opción es la utilización del producto **Elastic stack**, cumple con los requisitos y necesidades de la empresa.
Tras comentarlo con el CTO a última hora de la tarde, os ha solicitado que preparéis una presentación para mañana a primera hora. Dado el escaso margen para montar la demostración, la opción más ágil y rápida es utilizar una solución basada en contenedores donde levantaréis el motor de indexación [ElasticSearch](https://www.elastic.co) y la herramienta de visualización [Kibana](https://www.elastic.co/kibana).
Rellena el siguiente fichero docker-compose para que podáis hacer la demostración al CTO.
# Desarrollo

Crear una carpeta nueva y copiar el contenido del ejercicio 4
```sh
$  cd hw-01
$  mkdir answer_exercise_5
$ cp -a answer_exercise_4/ answer_exercise_5
```
Crear el fichero docker-compose.yml
```sh
$ touch answer_exercise_5/docker-compose.yml
```
Configurar el fichero docker-compose:

![Alt text](https://github.com/marbellacovino/docker-exercises/blob/master/hw-01/images/docker-compose.png)

Finalmente construimos nuestra imagen a partir del Dockerfile y con docker-compose iniciamos todos nuestros servicios...
```sh
$ cd answer_exercise_5
$ docker build -t proofofconcept .
$ docker-compose up
$ docker container ls
```
![Alt text](https://github.com/marbellacovino/docker-exercises/blob/master/hw-01/images/docker-compose1.1.png)

Para comprobar la correcta configuración deberemos acceder al portal de Kibana (http://localhost:5601):

Escoger la opción **“Try our simple data”**:

![Alt text](https://github.com/marbellacovino/docker-exercises/blob/master/hw-01/images/docker-compose1.2.png)

Seleccionar la opción **“Add data”**:

![Alt text](https://github.com/marbellacovino/docker-exercises/blob/master/hw-01/images/docker-compose1.3.png)

Y una vez se hayan cargado los datos, seleccionar **View data > Dashboard**:

Resultado:

![Alt text](https://github.com/marbellacovino/docker-exercises/blob/master/hw-01/images/docker-compose1.4.png)