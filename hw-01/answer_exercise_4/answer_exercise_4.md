# Crear una imagen docker a partir de un Dockerfile
Esta aplicación expondrá un servicio en el puerto 8080 y se deberá hacer uso de la instrucción HEALTHCHECK para comprobar si la aplicación está ofreciendo el servicio o por si el contrario existe un problema.

# Desarrollo
Correr los siguientes comandos en el terminal dentro del directorio hw-01:

Creamos una imagen de [node:12-alpine](https://hub.docker.com/_/node) a partir de un Dockerfile, para esto debemos crear un Dockerfile.js y configurarlo:
```sh
touch answer_exercise_4/Dockerfile.js
```
##### Dockerfile.js 
```sh
FROM node:12-alpine
# Update packages inside container image
RUN apk update
# Create folder app
WORKDIR /usr/src/app
# Copy src files inside app folder
COPY ./src .
# Execute npm install process
RUN npm install
# Expose port 3000
EXPOSE 3000
# Execute npm start
CMD [ "npm","start" ]
```

##### Configuración del Healhcheck:
Crear en el root folder un archivo healthcheck.js para configurar un custom health check
```sh
touch answer_exercise_4/healthcheck.js
```
##### healthcheck.js 
```javascript
var http = require("http");
var options = {
  host: "localhost",
  port: "3000",
  timeout: 2000,
};
var request = http.request(options, (res) => {
  console.log(`STATUS: ${res.statusCode}`);
  if (res.statusCode == 200) {
    process.exit(0);
  } else {
    process.exit(1);
  }
});
request.on("error", function (err) {
  console.log("ERROR");
  process.exit(1);
});
request.end();
```
Este código verifica si nuestra aplicación se está ejecutando en el puerto 3000 usando la biblioteca http provista con Nodejs. Si el servidor devuelve un estado 200, saldrá con la salida 0; de lo contrario, saldrá 1.

### Configuración del Dockerfile
Ahora tenemos que configurar el Dockerfile.js con nuestro custom health check
```sh
FROM node:12-alpine
# Update packages inside container image
RUN apk update
# Create folder app
WORKDIR /usr/src/app
# Copy src files inside app folder
COPY ./src .
# Execute npm install process
RUN npm install
# Expose port 3000
EXPOSE 3000
# Customize the healthcheck configuration
HEALTHCHECK --interval=45s --timeout=5s --start-period=30s --retries=2 \  
    CMD node healthcheck.js
# Execute npm start
CMD [ "npm","start" ]
```
Finalmente podemos construir y correr nuestro nuevo contenedor con los siguientes comandos:
```sh
docker build -t node-healthcheck .
docker container run -d --name node-healthcheck -p 8080:3000 node-healthcheck 
```
 ![Alt text](https://github.com/marbellacovino/docker-exercises/blob/master/hw-01/images/healthcheck-1.0.png)