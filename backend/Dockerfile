# Get small image for node (alpine)
FROM node:18-alpine AS builder

# Define working directory 
WORKDIR /usr/src/app
# Copy package.json 
COPY package*.json ./
#Install dependencies
RUN npm install
# Copy backend code to the working directory
COPY . /usr/src/app

# Add muilt stage
FROM node:18-alpine
# Define working directory
WORKDIR /usr/src/app
# Copy backend code to the working directory
COPY --from=builder /usr/src/app ./

# Expose container to the correct port number 
EXPOSE 5000

# Triggers when the container starts from the image
CMD ["node","server.js"]
