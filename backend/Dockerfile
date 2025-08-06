# Use official Node.js base image
FROM node:18

# Set working directory
WORKDIR /app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Copy app source
COPY . .

# Expose port (make sure this matches the one your app listens on)
EXPOSE 5000

# Start the app
CMD ["npm", "start"]
