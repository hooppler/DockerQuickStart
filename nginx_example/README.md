# Docker Nginx Tutorial
This is most simple example that show how to create linux nginx container and run simple web presentation.


## Content For The Docker Container
There are only few files that are prepared to be uploaded into the container:

hello_world_example:
- Dockerfile
- HelloWorld.txt
- run_script.sh
- README.md

## Dockerfile
In order to build docker image, first step is to design Dockerfile fine which should contain information about which files to copy to docker container.

\# Dockfile Hello World Example

FROM nginx:latest AS web
WORKDIR /usr/share/nginx/html
COPY . ./

## Build Image

.> docker build -t nginx:v1 .\
...\
.> docker images

REPOSITORY               TAG         IMAGE ID       CREATED          SIZE\
hello_world_html         latest      866463995ee0   25 seconds ago   91MB

## Create Container

F: .. >docker run -it --rm -d -p 8080:80 --name web nginx\
...

F: .. >docker ps\
CONTAINER ID   IMAGE              COMMAND                  CREATED          STATUS          PORTS                  NAMES\
c9f3b34d61ff   hello_world_html   "docker-entrypoint.s…"   25 seconds ago   Up 20 seconds   0.0.0.0:8080->80/tcp   vigilant_mclean

## Enter Container and Check Web Files
Web page files are placed into: 
/usr/share/nginx/html
Enter container:
.> docker exec -it c9f /bin/sh
.> cd /usr/share/nginx/html

## Open NGINX Starting Page
From browser open:
localhost:8080


