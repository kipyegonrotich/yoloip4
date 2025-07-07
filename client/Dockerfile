# Get small base image for node (alpine)
FROM node:16-alpine
# Executed when building the base image
# Creating a new directory for app files
RUN mkdir -p /usr/src/frontend
# Sets the working directorry to this path
WORKDIR /usr/src/frontend
# Copies the frontend code to the working directory
COPY . /usr/src/frontend
#Install dependencies
RUN npm install
# Expose container to the correct port number 
EXPOSE 3000
# Executed when creating the container from the image
CMD ["npm","start"]