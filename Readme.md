## Introduction
This is a Dockerfile project to build a container image for nginx and php-fpm 7.0 with xdebug. 
### Git repository
The genuine project can be found here: [https://github.com/ngineered/nginx-php-fpm](https://github.com/ngineered/nginx-php-fpm)
I've extended the original version with **PHP 7.0**, **xdebug** and **composer**. 

If you have any improvements please submit a pull request.
### Docker hub repository
The Docker hub build can be found here: [https://registry.hub.docker.com/u/alexastro/nginx-php-fpm/](https://registry.hub.docker.com/u/alexastro/nginx-php-fpm/)
## Versions

| Tag    | nginx  | PHP   | xdebug     | Ubuntu  |
|--------|--------|-------|------------|---------|
| latest | 1.9.12 | 7.0.4 |  2.4.0     | 14.04.4 |

## Building from source
To build from source you need to clone the git repo and run docker build:
```
git clone https://github.com/alexastro/docker-nginx-php-fpm.git
docker build -t alexastro/nginx-php-fpm:latest .
```
## Pulling from Docker Hub
Pull the image from docker hub rather than downloading the git repo. This prevents you having to build the image on every docker host:
```
docker pull alexastro/nginx-php-fpm:latest
```
## Running
To run the container:
```
sudo docker run --name nginx -p 8080:80 -d alexastro/nginx-php-fpm
```
You can then browse to ```http://<DOCKER_HOST>:8080``` to view the default install files.
### Volumes
Link your sources directory on the docker host to the container:
```
sudo docker run --name nginx -p 8080:80 -v /your_code_directory:/usr/share/nginx/html -d alexastro/nginx-php-fpm
```
### Logging
All logs should now print out in stdout/stderr and are available via the docker logs command:
```
docker logs <CONTAINER_NAME>
```
### Displaying Errors
If you want to display PHP errors on screen (in the browser) for debugging purposes use this feature:
```
-e ERRORS=1
```