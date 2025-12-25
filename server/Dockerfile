# Use Node.js LTS (Long Term Support) Alpine version as base image
# Alpine is a lightweight Linux distribution (~5MB vs ~900MB for regular node)
FROM node:lts-alpine

# Set the working directory inside the container to /app
# All subsequent commands will be executed from this directory
WORKDIR /app

# Copy package.json and package-lock.json (if exists) to /app
# The * allows copying package-lock.json only if it exists
# We copy these files first to leverage Docker's layer caching
COPY package*.json ./

# Install all dependencies defined in package.json
# This layer will be cached and only re-run if package.json changes
RUN npm install

# Copy all remaining files from the server directory to /app in the container
# This includes your source code (index.js, routes, models, etc.)
COPY . .

# Expose port 9000 to allow external connections to the container
# This is documentation - it doesn't actually publish the port
EXPOSE 9000

# Define the command to run when the container starts
# This will execute "npm start" which should be defined in package.json
CMD ["npm", "start"]