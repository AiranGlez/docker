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



