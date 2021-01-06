FROM node:12-alpine
# Update packages inside container image
RUN apk update
# Create folder app
WORKDIR /usr/src/app
# Copy src files inside app folder
COPY ./src .
# Execute npm install process
RUN npm install
# Bundle app source
COPY . .
# Expose port 8080
EXPOSE 8080
# Customize the healthcheck configuration
HEALTHCHECK --interval=45s --timeout=14s --start-period=30s --retries=2 \  
    CMD node healthcheck.js
# Execute npm start
CMD [ "node","app.js" ]





