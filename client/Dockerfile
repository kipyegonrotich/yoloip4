# Get small image for node (alpine)
FROM node:16-alpine
# Create new directory 
RUN mkdir -p /usr/src/frontend
# Define working directory 
WORKDIR /usr/src/frontend
# Copy backend code to the working directory
COPY . /usr/src/frontend
#Install dependencies
RUN npm install
# Expose container to the correct port number 
EXPOSE 3000
# Triggers when the container starts from the image
CMD ["npm","start"]