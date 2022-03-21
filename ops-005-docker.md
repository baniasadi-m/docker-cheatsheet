# Docker-cheatsheet-ops-005-docker
##### 1-  Download and get informaton about mysql:8 image.
when you want to get mysql:8 image use bellow command
```sh
docker image pull mysql:8
```
showing this image builded with which version of docker for use in script 
```sh
docker image inspect mysql:8 | jq -r .[0].DockerVersion
```
or get all image information
```sh
docker image inspect mysql:8 
```
get information about port and volumes used
```sh
docker image history mysql:8 
```
##### 2- Save,Import and load images and say deffrences
Save  nginx:latest  image to file
```sh
docker image save -o nginx.tar nginx:latest
```
Load image from tar file 
```sh
docker image load -i nginx.tar
```
Import image from tar file
```sh
docker image import nginx.tar nginx:mynginx
```
Differences between import and load image from tar file:
* `load` command is used restore all layers of image  but `import` compressed all layers to one layer.
* `load` command is used for keep all history of saved image but `import` remove all histories.
* `load` command is used all events occured for the image restored but in `import` removed.
* `import` is used to increase performance in the running container.
* `import` is used to create the base image 
##### 3- Create,run and port expose for nginx container
Running container and container port 80 to host port 8081   exposed
```sh
docker run -d --name nginx -p 8081:80 nginx:latest
```
#### 4- Show running processes in container
show running processes in container
```sh
docker top nginx
```
#### 5- Usage of docker-proxy
A full explanation of the `docker-proxy` is available [@here](https://windsock.io/the-docker-proxy/).
The summary is that the proxy is used to handle connections originating from the local machine that might otherwise not pass through the iptables rules that Docker configures to handle port forwarding, or when Docker has been configured such that it does not manipulate iptables at all.

#### 6- Dangling images
When docker image has repository name and no tag name sayed dangling image and can removed by bellow command
```sh
docker images prune
```

