# Docker-game
This project is based on a guessing game written in Java 
The purpose is to create a docker image and container of this game 

## PREREQUISITES: 
Need to have [Docker Desktop](https://www.docker.com/products/docker-desktop/) downloaded 

Install vim 

## INSTRUCTIONS FOR SET UP 
Step #1: Clone repo
```bash 
git clone https://github.com/MaryIshchenko/Docker-game
```
Step #2: Create Dockerfile and open it to edit 

```bash 
cd /path/to/Docker-game

touch Dockerfile

vim Dockerfile
```
Step #3: Add instructions to your Dockerfile - basic instructions taken from [Docker Guide](https://docs.docker.com/get-started/run-your-own-container/?uuid=35125792-A2C8-4F82-972B-45DC61E614F9)

```
# syntax=docker/dockerfile:1

# Start your image with a node base image
FROM node:18-alpine

# Create an application directory
RUN mkdir -p /app

# Set the /app directory as the working directory for any command that follows
WORKDIR /app

# Copy the local app package and package-lock.json file to the container
COPY package*.json ./

# Copy local directories to the working directory of our docker image (/app)
COPY ./src ./src
COPY ./public ./public

# Install node packages, install serve, build the app, and remove dependencies at the end
RUN npm install \
    && npm install -g serve \
    && npm run build \
    && rm -fr node_modules

# Specify that the application in the container listens on port 3000
EXPOSE 3000

# Start the app using serve command
CMD [ "serve", "-s", "build" ]
```
Step #4: Build Docker Image
```bash 
docker build -t Docker-game .
```
Step #5: Run container with port number 8089

Step #6: Verify on  http://localhost:8089

Step #7: Stop container on Docker Descktop 

Notice: these instructions are based on a Mac system 

Citations: Guide created based on [Docker Instructions](https://docs.docker.com/get-started/run-your-own-container/?uuid=35125792-A2C8-4F82-972B-45DC61E614F9) 


