# docker-nginx-rtmp

## Method one only docker
In order to run this container you need docker installed https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/

Run the following command: `docker run --name nginx-rtmp -d -p 8080:80 -p 1935:1935 unafraid/nginx-rtmp:latest`

## Method two docker + docker-compose
Or use docker-compose instead https://docs.docker.com/compose/install/#install-compose

Run the following command `docker compose up -d` in the directory where you downloaded docker-compose.yml from this repository
