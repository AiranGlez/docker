# USING DOCKER TO BUILD APPLICATIONS

## Download app from repository

[Platzi-Docker](https://github.com/platzi/docker)

## Building app

`sudo docker build -t platziapp .`

`sudo apt-get install npm`

`sudo npm install`

`sudo npm audit fix`

`sudo docker run --rm -p 3000:3000 -v ${PWD}:/usr/src platziapp`

## Docker networking

`sudo docker network ls`

`sudo docker network create --attachable platzinet`

`sudo docker run -d --name db mongo`

`sudo docker network connect platzinet db`

`sudo docker network inspect platzinet`

`sudo docker run -d --name app -p 3000:3000 --env MONGO_URL=mongodb://db:27017/test platziapp`

`sudo docker network connect platzinet app`