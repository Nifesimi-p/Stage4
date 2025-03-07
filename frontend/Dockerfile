# Use Node.js 12 as the build stage
FROM node:12 AS builder

# Set working directory
WORKDIR /app

# Copy package.json and package-lock.json for dependency installation
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the frontend code
COPY . .

# Build the frontend application
RUN npm run build

# Use Nginx as the final lightweight image for serving the frontend
FROM nginx:latest

# Copy built frontend files to Nginx's default public folder
COPY --from=builder /app/dist /usr/share/nginx/html

# Expose port 80 for serving the application
EXPOSE 80

# Start Nginx when the container runs
CMD ["nginx", "-g", "daemon off;"]
