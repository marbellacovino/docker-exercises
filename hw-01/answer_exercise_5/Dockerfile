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





