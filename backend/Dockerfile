# Get small image for node (alpine)
FROM node:18-alpine
# Create new directory 
RUN mkdir -p /usr/src/app
# Define working directory 
WORKDIR /usr/src/app
# Copy backend code to the working directory
COPY . /usr/src/app
#Install dependencies
RUN npm install
# Expose container to the correct port number 
EXPOSE 5000
# Triggers when the container starts from the image
CMD ["node","server.js"]