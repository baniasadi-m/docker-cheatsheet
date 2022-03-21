# Docker-cheatsheet-ops-007-docker

##### 1- Reason of dockerfile usage
dockerfile is used to automatically create docker images.
##### 2- Differences between `docker build` and `docker commit`
* docker commit is basically taking a "snapshot" of the current state of the "running" container and save it as an image. This basically means if your "running" container are generating logs files, update packages, or making file changes, they will be saved into the image. Every-time you run docker
commit, you will create a new image.
* There will be differences in size
* The commit operation will not include any data contained in volumes mounted inside the container. 
* docker build will only create a new image if it detects changes in Dockerfile but commit create an image agian.

##### 3- Differences between `ARG` and `ENV` in Dockerfile
`ENV` command set environmet variables to use in container and `ARG` command is a variable to use for docker engine.
##### 4- Differences between `ENTRYPOINT` and `CMD` in Dockerfile
`ENTRYPOINT` is base command run when container created and when `CMD` is exists it passes as arguments for entrypoint.

##### 5- Differences between exposing and publishing ports
Just says to docker engine this application used this port(tcp/udp),but port publish is binding host port to container port ,in other words access to container port by custom host port. 

##### 6- Concept of using `FROM` in Dockerfile
`FROM` says to docker engine to build  from base image. In other words uses base image rootfs for building and dockerizing app.

##### 7- Differences between `RUN` and `ENTRYPOINT` in Dockerfile
`RUN` command execute when building image and `ENTRYPOINT` is executed when  create and run containers from image.
##### 8- Differences between `COPY` and `ADD` in Dockerfile
* `ADD` command can copy files from url to image 
* `ADD` command extract files from tar files and then copy into image but `COPY` copy the archive file into image 
##### 9- What is the meaning of using `VOLUME /data` command in Dockerfile
`VOLUME` command says to docker engine about this path has Sensitive data and need to set persistent volume when container running.

