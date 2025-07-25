# Use the exact Node version required
FROM node:16

# Set working directory
WORKDIR /usr/src/frontend

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Copy source code
COPY . .

# Expose frontend port
EXPOSE 3000

ENV CI=true

# Start the frontend
CMD ["npm", "start"]
