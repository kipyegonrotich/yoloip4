# Get small image for node (alpine)
FROM node:18-alpine AS builder
# Define working directory 
WORKDIR /usr/src/frontend
# Copy package.json 
COPY package*.json ./
#Install dependencies
RUN npm install
# Copy code to the working directory
COPY . /usr/src/frontend


# Expose container to the correct port number 
EXPOSE 3000
# Triggers when the container starts from the image
CMD ["npm","start"]