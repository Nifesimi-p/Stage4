# Use official Node.js image as the base
FROM node:16

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json first to leverage Docker caching
COPY package*.json ./

# Install dependencies
RUN npm install --only=production

# Copy the rest of the application code
COPY . .

# Expose the application's port (if applicable)
EXPOSE 8082  

# Define the command to start the application
CMD ["node", "server.js"]
