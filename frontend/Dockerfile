# Base image for Backend
FROM node:21 AS backend-builder

# Set the working directory inside the container
WORKDIR /app

# Code
COPY package*.json ./

# Packages the installed 
RUN npm install 

# test
RUN npm run test

# copy the test of the application code 
COPY . . 

# stage 2 
FROM node:21-slim

# setup the working directory 
WORKDIR /app

# Copy the above stage as compressed
COPY --from=frontend-builder /app .

# copy the .env.sample file to .env.local
COPY .env.docker .env.local

#Expose the port 
EXPOSE 5173

# Command to start the backend server
CMD ["npm", "start"]
