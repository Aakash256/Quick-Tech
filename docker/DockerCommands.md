# Pulls an image from docker hub
docker pull redis

# Creates a new docker container and starts it
docker run redis

# It also pulls if image is not available
docker run postgres:9.6

# Run docker in detach mode
docker run -d redis

# Stops running Docker container
docker stop container_id

# Starts the existing docker
docker start container_id

# list running containers
docker ps

# list running and not running containers
docker ps -a

# It binds host and docker port -> -phost_port:docker_port
docker run -p6000:6379 -d redis 

# lists all the images which you have in local
docker images ()

# DEBUG

# Prints all the logs which container is logging
docker logs container_id/names

# Create a new container w
docker run -d -p6001:6379 --name redis-older redis:4.0

# Get the terminal of container
docker exec -it container_id/names /bin/bash or /bin/sh (All containers does not support bash)
exit

# Isolated Docker Network
docker network ls  
docker network create network_name


# Real World docker example
docker pull mongo  
docker pull mongo-express  
docker network create mongo-network  
docker run -p 27017:27017 -d -e MONGO_INITDB_ROOT_USERNAME=admin -e MANGO_INITDB_ROOT_PASSWORD=secret --name mongodb --net mongo-network mongo  
docker run -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSER=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=secret --net mongo-network --name mongo-express -e  ME_CONFIG_MONGODB_SERVER=mongodb mongo-express  
Create a database using mongo-express UI  

# Docker Compose
docker-compose -f mongo.yaml up  
docker-compose -f mongo.yaml down  

# Docker File (A blueprint to create docker images)
FROM node  
RUN mkdir -p /home/app  
COPY ./app /home/app  
CMD ["node","server.js"]  

# Build image from Docker File
docker build -t my-app:1.0 .  
docker run my-app:1.0  

# Remove Docker Container and Docker Image
docker rm container_id  
docker rmi image_id  

# Private Repository or Docker Registry
- Can be created on AWS (ECR - Elastic Contain Registry)
- login to docker 
- build image (Command can be found in AWS)
- Tag the image (Command can be found in AWS)
- push image to Docker (Command can be found in AWS)

# Host Volumes (-v host_path:doker_path)
docker run -d -v /home/mount/data:/data/db  
docker run -d -v /data/db (Anonomous Volumes)  
docker run -d -v name:/data/db (Named volumes) - Mostly Used  

# Docker Compose File - mongo.yaml
https://github.com/Aakash256/Quick-Tech/blob/main/docker/mongo.yaml
