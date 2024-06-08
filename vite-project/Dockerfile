# Use node:20-alpine as the base image
FROM node:20-alpine

# Create a non-root user and group to run the application
RUN addgroup -S app && adduser -S -G app app

# Set the working directory to /app
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies as root to avoid permission issues
USER root
RUN npm install

# Copy the rest of the application files to the working directory
COPY . .

# Change ownership of the application directory to the non-root user
RUN chown -R app:app .

# Switch to the non-root user
USER app

# Expose port 5173
EXPOSE 5173

# Command to run the application
CMD ["npm", "run", "dev"]
