# docker-nginx-rtmp

# Versions
- nginx: 1.12.2
- nginx-rtmp-module: 1.2.1
- nginx-fancyindex-module: 0.4.2
- pcre: 8.40
- zlib: 1.2.11
- openssl: 1.1.0g
- go-health-check: 1.1

## Method one only docker
In order to run this container you need docker installed https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/

Run the following command: `docker run --name nginx-rtmp -d -p 8080:80 -p 1935:1935 unafraid/nginx-rtmp:1.12.2-1.2.1-no-record`

## Method two docker + docker-compose
Or use docker-compose instead https://docs.docker.com/compose/install/#install-compose

docker-compose.yml
```yaml
version: "2.1"

services:
 server:
    image: unafraid/nginx-rtmp:1.12.2-1.2.1-no-record
    container_name: nginx_rtmp
    ports:
      - 8080:80
      - 1935:1935
    restart: unless-stopped
    healthcheck:
      test: ["CMD", "/usr/local/bin/go-health-check", "tcp", "server", "80"]
      interval: 10s
      timeout: 30s
      retries: 5
```
Run the following command `docker compose up -d` in the directory where you created docker-compose.yml provided above

