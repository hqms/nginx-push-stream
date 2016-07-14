# Docker-nginx-push-stream
Docker image for an nginx with additional push stream module

[NGINX Version 1.11.2](http://nginx.org/download/nginx-1.11.2.tar.gz)

[nginx-push-stream-module](https://github.com/wandenberg/nginx-push-stream-module)

## Installation
This repository consists of pre-built scripts and docker ready-to-built Dockerfile

### Compiling from scratch
This docker image based on latest Alpine linux. The build processes composed up in 2 steps:
1. Compile nginx with its additional push stream module
2. Building docker image and docker container

To build from scratch just run build script from shell

```
# ./build.sh
```

The script will build image based on ```/build/Dockerfile```, create container and compile nginx with additional module on that container. The result of this process is nginx.tar.gz file.

The script then build ```Dockerfile```  and use nginx.conf as its default configuration file. 

By default, docker images name defined in line 2 and 3 in ```build.sh```
```
DOCKER_RUN_IMAGE=nginx-push-stream
DOCKER_BUILD_IMAGE=nginx-push-stream-build
```
Exposed port by default is on ```8080```

To customise compiled nginx package, edit ```/build/Dockerfile``` before running this script

## Building Image
To build docker image, simply run docker build

``` 
# docker build -t nginx-push-stream .
```

To create container based created image:
```
# docker run -d --name nginx-push-stream -p 8080:80 -t nginx-push-stream
```
