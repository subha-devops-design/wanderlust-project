# Base image for Backend
FROM node:21 AS backend-builder

# Set the working directory inside the container
WORKDIR /app

# Code
COPY . .

# Packages the installed 
RUN npm i 

# test
RUN npm run test

# stage 2 
FROM node:21-slim

# setup the working directory 
WORKDIR /app

# Copy the above stage as compressed
COPY --from=backend-builder /app .

COPY .env.docker .env

#Expose the port 
EXPOSE 5000

# Command to start the backend server
CMD ["npm", "start"]
