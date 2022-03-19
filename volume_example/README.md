# Docker Volume Example
This is simple example how to add external volume to an container.


## Content For The Docker Container
There are only few files that are prepared to be uploaded into the container:

volume_example/container_content:
- Dockerfile


## Dockerfile
In order to build docker image, first step is to design Dockerfile fine which should contain information about which files to copy to docker container.

\# Dockfile Hello World Example

FROM node:12-alpine AS app-base\
WORKDIR /app\
COPY . ./

## Build Image
With terminal go to directory where Dockerfile is placed.

.> docker build -t hello_world:1.0 .\
...\
.> docker images

REPOSITORY               TAG         IMAGE ID       CREATED          SIZE\
hello_world_html         latest      866463995ee0   25 seconds ago   91MB

## Create and Run Container With External Volume

.>docker run -it -d -p 8080:80 -v [path] volume_example:v1
c9f3b34d61ff85383456f2ddc01004b34ec3066b4ef48f3f9cce983dbdaba51e

Example (Windows):
For Windows path "C:\tmp" to linux container path /new_volume
.> docker run -it -d -p 8080:80 -v "/C/tmp":/new_volume volume_example:v1

.>docker ps\
CONTAINER ID   IMAGE              COMMAND                  CREATED          STATUS          PORTS                  NAMES\
c9f3b34d61ff   hello_world_html   "docker-entrypoint.s…"   25 seconds ago   Up 20 seconds   0.0.0.0:8080->80/tcp   vigilant_mclean

## Enter Command Line Shell
.> docker exec -it c9f /bin/sh

## Enter External Volume From Linux Container
/app # cd ..
/ # ls
app         etc         media       opt         run         sys         var\
bin         home        mnt         proc        sbin        tmp\
dev         lib         new_volume  root        srv         usr\

/ # cd new_volume
/ # ls
Volume content...

