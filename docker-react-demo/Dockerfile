# Set the base image to create the image for the React app
FROM node:20-alpine

# Create a non-root user with limited permissions
RUN addgroup -g 1001 app \
    && adduser -u 1001 -G app -s /bin/sh -D app

# Set the user to run the app
USER app

# Set the working directory to /app
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the files to the working directory
COPY . .

# Expose port 5173
EXPOSE 5173

# Command to run the app
CMD ["npm", "run", "dev"]
