# Docker Getting Started Tutorial

## Content Of The Docker


## Dockerfile
In order to build docker image, first step is to design Dockerfile fine which should contain information about which files to copy to docker container.

\# Dockfile Hello World Example

FROM node:12-alpine AS app-base\
WORKDIR /app\
COPY . ./


## Build Image

.> docker build -t hello_world_html:1.0 .\
...\
.> docker images

REPOSITORY               TAG         IMAGE ID       CREATED          SIZE\
hello_world_html         latest      866463995ee0   25 seconds ago   91MB

## Create Container

F: .. >docker run -it -d -p 8080:80 hello_world_html
c9f3b34d61ff85383456f2ddc01004b34ec3066b4ef48f3f9cce983dbdaba51e

F: .. >docker ps\
CONTAINER ID   IMAGE              COMMAND                  CREATED          STATUS          PORTS                  NAMES\
c9f3b34d61ff   hello_world_html   "docker-entrypoint.s…"   25 seconds ago   Up 20 seconds   0.0.0.0:8080->80/tcp   vigilant_mclean

## Enter Command Line Shell
.> docker exec -it c9f /bin/sh