# Docker-game
This project is based on a guessing game written in Java 
The purpose is to create a docker image and container of this game 


## PREREQUISITES: 
Need to have [Docker Desktop](https://www.docker.com/products/docker-desktop/) downloaded 

Install vim 

Install temurin for javac command 

## INSTRUCTIONS FOR SET UP 
Step #1: Clone repo
```bash 
git clone https://github.com/MaryIshchenko/docker-game
```
Step #2: Create Dockerfile and open it to edit 

```bash 
cd /path/to/docker-game
```
``` bash
touch Dockerfile
```
```bash
vim Dockerfile
```
Step #3: Add instructions to your Dockerfile - basic instructions taken from [Docker Guide](https://docs.docker.com/get-started/run-your-own-container/?uuid=35125792-A2C8-4F82-972B-45DC61E614F9)

```
# syntax=docker/dockerfile:1

FROM openjdk:8

WORKDIR /app

COPY . /app/

RUN javac Main.java

CMD ["java", "Main"]

```
Step #4: Build Docker Image
```bash 
docker build -t docker-game .
```
Step #5: Stop container on Docker Desktop 

Notice: these instructions are based on a Mac system 

Citations: Guide created based on [Docker Instructions](https://docs.docker.com/get-started/run-your-own-container/?uuid=35125792-A2C8-4F82-972B-45DC61E614F9) 


