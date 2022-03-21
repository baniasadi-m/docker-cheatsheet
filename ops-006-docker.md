# Docker-cheatsheet-ops-006-docker

##### 1-  stop container by kill command.
when container stop by kill command the `SIGTERM` signal send to process
```sh
docker kill nginx
```
##### 2- install nginx on alpine container and create image from it.
Run docker containe from alpine base image 
```sh
docker run -itd --rm --name alpine alpine
```
attach to container shell 
```sh
docker exec -it alpine sh
```
update and install nginx in container
```sh
apk update
apk add nginx
```
detach from container shel and run this command
```sh
docker commit alpine mynginx:alpine
```
#### 3- puase container
The `docker pause` command suspends all processes in the specified containers. On Linux, this uses the freezer cgroup. Traditionally, when suspending a process the `SIGSTOP` signal is used, which is observable by the process being suspended. With the freezer cgroup the process is unaware, and unable to capture, that it is being suspended, and subsequently resumed.
#### 4- get and save container id
get container id by 
```sh
docker inspect myredis | jq -r .[0].Id  > myredis.cid
```

#### 5- run limited resource container
Running limited resource container from nginx image with 512MB memory and 256MB swap memory and 1.5 core cpu that just run in 0 and 2 cpu number.
```sh
docker run -d --rm --name nginx --memory="512M" --memory-swap="256M" --cpus="1.5" --cpuset-cpus=0,2  nginx
```
#### 6- Environment in containers
set environment varibles for alpine container by `-e` parameter
```sh
docker run -itd  --rm --name alpine -e CLASS=dws -e NAME=masoud alpine
```
show container envs
```sh
docker exec -it alpine env
```
#### 7- changing working dir when running container
running container and `/data` container directory mount to `/opt/data` host directory
```sh
docker run -itd  --rm --name myalpine -w /data -v /opt/data:/data alpine
```
