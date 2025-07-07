# Getting small base image for node (alpine)

FROM node:14-alpine

# Executed when building the base image

# Creating a new directory for app files

RUN mkdir -p /usr/src/app

# Sets the working directory to this path

WORKDIR /usr/src/app

# Copies the backend code to the working directory

COPY . /usr/src/app

#Install dependencies

RUN npm install

# Expose container to the correct port number 

EXPOSE 5000

# Executed when creating the container from the image

CMD ["node","server.js"]