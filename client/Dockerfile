# Stage 1: Build the React app
FROM node:16 as builder

ARG REACT_APP_BACKEND_URL
ENV REACT_APP_BACKEND_URL=$REACT_APP_BACKEND_URL

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# Create a production build
RUN npm run build

# Stage 2: Serve the app using Nginx
FROM nginx:alpine

# Copy build artifacts to Nginx's web directory
COPY --from=builder /app/build /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
