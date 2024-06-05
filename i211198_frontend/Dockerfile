# Base image
FROM node:14

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the app
RUN npm run build

# Use a different base image to serve the app
FROM nginx:alpine

# Copy the build output to nginx html folder
COPY --from=0 /app/build /usr/share/nginx/html

# Expose the port the app runs on
EXPOSE 11981

# Command to run nginx
CMD ["nginx", "-g", "daemon off;"]
