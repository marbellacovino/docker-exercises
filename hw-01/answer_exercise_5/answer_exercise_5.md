create a healthcheck.js
touch answer_exercise_4/healthcheck.js
docker build -t node-healthcheck .
docker container run -d --name node-healthcheck -p 8080:3000 node-healthcheck 