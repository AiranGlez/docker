# DOCKER
##
## INSTALL

https://docs.docker.com/engine/install/ubuntu/

## FIRST STEPS

`sudo docker run hello-world` #Run a test image

`sudo docker ps -a` #Check docker containers

`sudo docker inspect CONTAINERID/NAME` #Display more info about a container

`sudo docker inspect -f '{{ json .JSONSECTIONNAME }}' CONTAINERID` #'-f' option filters output based on indication

`sudo docker rename OLDNAME NEWNAME`

`sudo docker logs CONTAINERID/NAME` #Check previous container output

`sudo docker rm CONTAINERID/NAME`

`sudo docker rm $(sudo docker ps -aq)` #Removes all containers (-q option displays only container ID)

## INTERACTIVE MODE

`sudo docker run centos` #Download a centos image and builds a container

`sudo docker ps -a`

centos container --> COMMAND '/bin/bash' (root command: it will exit when this command ends)

`sudo docker run -it centos` #Runs the container on interactive mode through host terminal

`sudo docker exec -it CONTAINERID/NAME` #Runs an interactive console on active container

`sudo docker kill CONTAINERID/NAME` #Kills root process of container

## EXPOSING CONTAINERS

`sudo docker run -d --name webserver -p 8080:80 nginx` #Detach option separates terminal from main root command / -p publishes container service through indicated port (8080)

`curl http://localhost:8080` --> nginx server index

## DATA PERSISTENCE

`sudo docker run -d --name database mongo`

`sudo docker exec -it database bash`

`mongo`

`use clients`

`db.users.insert({ "name": "Airan" })`

`db.users.find()`

After we remove this container and create a new one, we can see our data has been lost with the container. To avoid this:

`sudo mkdir /home/developer/mongodata`

`sudo docker run --name database -d -v /home/developer/mongodata:/data/db mongo`

Even if we delete this container, if we run a new one with this volume it will contain all data saved from the previous container.

## DOCKER VOLUMES

On Linux: /var/lib/docker/volumes

`sudo docker volume list`

`sudo docker volume prune` #Remove all non-used volumes

`sudo docker volume create VOLUMENAME`

`sudo docker run -d --name database2 --mount src=VOLUMENAME,dst=/data/db mongo`

## DOCKER IMAGES

`sudo docker pull IMAGENAME:VERSION` #Download a specific image

https://hub.docker.com/

`sudo docker image list`

### Building our own images

Creating a Dockerfile:

`sudo nano Dockerfile`

FROM ubuntu #Base image

RUN touch /usr/src/hola-airan #Command to execute on build

`sudo docker build -t IMAGENAME:VERSION PATH`

To test this image we will need to run a container as previously indicated

`sudo docker tag IMAGENAME:VERSION USER/REPOSITORY:VERSION` #Change image tag to allow the image to be published to own repository

`sudo docker push USER/IMAGENAME:VERSION`
