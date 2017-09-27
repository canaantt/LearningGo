Docker Notes:
https://github.com/wsargent/docker-cheat-sheet
====
$ docker -version

Client: Command line
 Version:      17.06.1-ce
 API version:  1.30
 Go version:   go1.8.3
 Git commit:   874a737
 Built:        Thu Aug 17 22:53:38 2017
 OS/Arch:      darwin/amd64

Server: Docker engine
 Version:      17.06.1-ce
 API version:  1.30 (minimum version 1.12)
 Go version:   go1.8.3
 Git commit:   874a737
 Built:        Thu Aug 17 22:54:55 2017
 OS/Arch:      linux/amd64
 Experimental: true
===
docker COMMAND --help
$ docker container run --publish 80:80 nginx
Local 80 to container port 80 
$ docker container run // always start a *new container
$ docker container start // starts an existing container
When run docker container run, there usually would have two containers showing up

504  docker version
  506  docker container ls --help
  507  docker container run --publish 80:80 --detach --name webhost nginx
  508  docker container logs webhost
  515  docker container rm 89a // won’t work because the container is running 
  516  docker container stop 89a
  517  docker container ls -a
  518  docker container start 89a
  522  docker container logs webhost


 $ docker container run --publish 8080:80 --detach --name apache httpd
 $ docker container run -d -p 3360:3360 --name db -e MYSQL_RANDOM_ROOT_PASSWORD=yes mysql
 $ docker container logs mysql // this is where you should find password
 
 $ docker start webhost [container_name]
 $ docker stop webhost [container_name]
 $ docker container start 89a [container_id]
 $ docker container stop 89a [container_id]

===
Looking into individual container
$ docker container top // process list in one container
$ docker container inspect // details of one container config
$ docker container stats // performance stats for all containers

 docker container run -d --name mysql -e MYSQL_RANDOM_ROOT_PASSWORD=true mysql
 docker container top mysql
 docker container top nginx
 docker container inspect mysql
 docker container stats
 
docker container run -it --name proxy nginx bash

=========
Official images are preferred
name without slash
Stable
More than one tags for each image
Tags: lastest  
# of starts and pulls

=========== Persistent data ============
Defining the problem of persistent data
Key concepts with containers: immutable, ephemeral
Learning and using Data Volumes
Learning and using Bind Mounts

VOLUME needs to be removed manually

===========Docker Golang ==============

$ docker pull google/golang
$ docker run -p 8080:8080 -ti google/golang bin/bash
[inside of the docker container] 
$ cd ..
$ go get github.com/nsavageJVM/dockrunner
$ bin/dockrunner
[open another container]
$ docker exec -ti  container_id
$ ip add | grep global 
// inet 10.99.99.2/24 scope global eth0 — this is docker Daemon configuration ‘bip’ field

==========QUESTIONS==================
- [x] From a public image, how to find out the core, or operating system? linux/amd64 from docker engine, $ docker version Server OS/Arch
- [ ] 
