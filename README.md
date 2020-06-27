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

`sudo docker run -d --name webserver -p 8080:80 nginx` #Detach option separates terminal from main root command / -p publishes container service trough indicated port (8080)

`curl http://localhost:8080` --> nginx server index
