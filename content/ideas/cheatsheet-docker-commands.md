<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----



* [Docker Series](https://earthly.dev/blog/series/docker/)
* [Docker 101](https://nerdyarticles.com/docker-101/)
* [Intro to Docker](https://hackaday.com/2018/09/05/intro-to-docker-why-and-how-to-use-containers-on-any-system/)




# Sources
* [Docker Cheat Sheet](https://www.docker.com/sites/default/files/d8/2019-09/docker-cheat-sheet.pdf)
* [The Ultimate Docker Cheat Sheet](https://dockerlabs.collabnix.com/docker/cheatsheet/)

* [Docker Commands You Should Know as a Beginner](https://dzone.com/articles/docker-commands-you-should-know-as-a-beginner)

# Docker Cheat Sheet
Typing just `docker` or `docker help` on the command line will display a list of all available commands.

## Docker Volumes
* [Understanding Docker Volumes](https://earthly.dev/blog/docker-volumes/)

## Docker Management
All commands below are called as options to the base `docker` command.
Execute `docker <command> --help` for more information on a particular command.

- `docker builder`     -- Manage builds
- `docker config`      -- Manage Docker configs
- `docker context`     -- Manage contexts
- `docker engine`      -- Manage the docker Engine
- `docker image`       -- Manage images
- `docker network`     -- Manage networks
- `docker node`        -- Manage Swarm nodes
- `docker plugin`      -- Manage plugins
- `docker registry*`   -- Manage Docker registries
- `docker secret`      -- Manage Docker secrets
- `docker service`     -- Manage services
- `docker stack`       -- Manage Docker stacks
- `docker swarm`       -- Manage swarm
- `docker system`      -- Manage Docker
- `docker trust`       -- Manage trust on Docker images
- `docker volume`      -- Manage volumes

## Build
```bash
# build an image from the Dockerfile in the current directory and tag the image
docker build -t myimage:1.0 .

# list all images that are locally stored with the docker engine
docker image ls

# delete an image from the local image store
docker image rm alpine:3.4
```

## Share
```bash
# pull an image from a registry
docker pull myimage:1.0

# retag a local image with a new image name and tag
docker tag myimage:1.0 myrepo/myimage:2.0

# push an image to a registry
docker push myrepo/myimage:2.0
```

## Run
```bash
# run a container from the Alpine version 3.9 image, name the running container “web” and expose port 5000 externally, mapped to port 80 inside the container.
docker run <container> --name web -p 5000:80 alpine:3.9

# stop a running container through SIGTERM
docker stop <container>

# stop a running container through SIGKILL
docker kill <container>

# list the networks
docker network ls

# list the running containers (add --all to include stopped containers)
docker container ls

# delete all running and stopped containers
docker container rm -f $(docker ps -aq)

# print the last 100 lines of a container’s logs
docker logs --tail 100 <container>
```

## Docker Networking
* [Docker networking is CRAZY!! (you NEED to learn it)](https://www.youtube.com/watch?v=bKFMS5C4CG0)
* [Docker Networking Tutorial // ALL Network Types explained!](https://www.youtube.com/watch?v=5grbXvV_DSk)
