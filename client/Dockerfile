# Step 1: Build the React frontend with env var
FROM node:16 AS build

ARG REACT_APP_BACKEND_URL
ENV REACT_APP_BACKEND_URL=$REACT_APP_BACKEND_URL

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

# This is where your REACT_APP_BACKEND_URL is baked into the build
RUN npm run build

# Step 2: Serve the production build with nginx
FROM nginx:alpine

# Copy React production build to Nginx html folder
COPY --from=build /app/build /usr/share/nginx/html

# Optional: Custom nginx config for SPA routing
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
