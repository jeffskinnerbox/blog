<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------





---------------



# Docker

* [How to install Docker and Hello World](https://www.youtube.com/playlist?list=PLRAV69dS1uWTJLvDP4Veld5F05rJAmOcp)


## Docker Hub


## Installing Docker


### Step 1: Installing Docker - DONE
To install Docker manually, go to the [Docker installation page][58].
There are multiple methods but I'm using the recommend method using [Docker’s repositories][60].

Source:

* [Docker explained simply](https://www.youtube.com/watch?v=_trJf3GbZXg&list=RDCMUCZNhwA1B5YqiY1nLzmM0ZRg&index=2)
* [How To Install and Use Docker on Ubuntu 20.04](https://phoenixnap.com/kb/install-docker-on-ubuntu-20-04)

```bash
# check the currently install verson of docker
docker --version

# uninstall any old version of docker (called docker, docker.io, or docker-engine)
sudo apt-get remove docker docker-engine docker.io containerd runc

# update the apt package index and install packages
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release

# add docker’s official gpg key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# set up the stable repository
 echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] \
    https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" \
    | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# install the latest version of docker engine
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io

# install a specific version of docker engine, list the available versions in the repo
$ apt-cache madison docker-ce
 docker-ce | 5:20.10.8~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:20.10.7~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:20.10.6~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:20.10.5~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:20.10.4~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:20.10.3~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:20.10.2~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:20.10.1~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:20.10.0~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:19.03.15~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:19.03.14~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:19.03.13~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:19.03.12~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:19.03.11~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:19.03.10~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:19.03.9~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages

# install a specific version using the version string from the second column
# sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io
sudo apt-get install docker-ce=5:20.10.8~3-0~ubuntu-focal docker-ce-cli=5:20.10.8~3-0~ubuntu-focal containerd.io

# check the currently install version of docker
$ docker --version
Docker version 20.10.8, build 3967b7d
```


### Step 2: Verify Docker Installation - DONE
Next we'll verify that Docker Engine is installed correctly by running the `hello-world` image.
This command downloads a test image and runs it in a container.
When the container runs, it prints a message and exits.

```bash
# verify that docker engine is installed correctly
$ sudo docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
b8dfde127a29: Pull complete
Digest: sha256:61bd3cb6014296e214ff4c6407a5a7e7092dfa8eefdbbec539e133e97f63e09f
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

To find out the status of Docker containers,
used these commands:

```bash
# list running docker containers
$ sudo docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

# list all containers, both running and stopped
$ sudo docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                      PORTS     NAMES
3536f50560bc   hello-world   "/hello"   12 minutes ago   Exited (0) 12 minutes ago             laughing_colden

# list the total file size of each container
$ sudo docker ps -a -s
CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                      PORTS     NAMES             SIZE
3536f50560bc   hello-world   "/hello"   14 minutes ago   Exited (0) 14 minutes ago             laughing_colden   0B (virtual 13.3kB)
```


### Step 3: Upgrade Docker Engine - DONE
To upgrade Docker Engine, first run `sudo apt-get update`,
then follow the installation instructions, choosing the new version you want to install:

```bash
sudo apt-get update
apt-cache madison docker-ce
sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io
```


### Step 4: Useful Docker Commands

* [What is Docker?](https://phoenixnap.com/kb/what-is-docker)
* [Docker vs. Kubernetes](https://phoenixnap.com/kb/docker-vs-kubernetes)
* [Kubernetes vs Docker Swarm: What are the Differences?](https://phoenixnap.com/blog/kubernetes-vs-docker-swarm)
* [How to List / Start / Stop Docker Containers](https://phoenixnap.com/kb/how-to-list-start-stop-docker-containers)
* [How to Use Docker Run Command with Examples](https://phoenixnap.com/kb/docker-run-command-with-examples)
* [How To Remove Docker Images, Containers, Networks & Volumes](https://phoenixnap.com/kb/remove-docker-images-containers-networks-volumes)
* [How to Set Up and Use Private Docker Registry](https://phoenixnap.com/kb/set-up-a-private-docker-registry)
* [How to Manage Docker Containers? Best Practices](https://phoenixnap.com/kb/docker-container-management)

```bash
# list installed images
sudo docker images
```


### Step 5: Uninstall Docker Engine

```bash
# uninstall the docker engine, the cli, and containerd packages
sudo apt-get purge docker-ce docker-ce-cli containerd.io

# delete all images, containers, and volumes
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd

# you must delete any edited configuration files manually
```


## Develop with Docker

* [Develop with Docker](https://docs.docker.com/develop/)
* [How to Deploy NGINX Reverse Proxy on Docker](https://phoenixnap.com/kb/docker-nginx-reverse-proxy)
* [How to Deploy and Manage MongoDB with Docker](https://phoenixnap.com/kb/docker-mongodb)
* [How to Containerize Legacy Applications](https://phoenixnap.com/kb/how-to-containerize-applications)
* [Docker Volumes: How to Create & Get Started](https://phoenixnap.com/kb/docker-volumes)
* [Docker and Running your self-hosted applications in a more secure way behind a reverse proxy.](https://www.youtube.com/watch?v=8T68pB_Fkm4)


## Install Docker Compose
[Docker Compose][62] is a tool for defining and running multi-container Docker applications.
With Compose, you use a YAML file to configure your application’s services.
Then, with a single command, you create and start all the services from your configuration.

* [Docker-compose tutorial](https://www.youtube.com/watch?v=qH4ZKfwbO8w)
* [Overview of Docker Compose](https://docs.docker.com/compose/)
* [Install Docker Compose](https://docs.docker.com/compose/install/)
* [How to Install Docker Compose on Ubuntu 20.04](https://phoenixnap.com/kb/install-docker-compose-on-ubuntu-20-04)
* [How to Install Docker and Docker Compose on Linux](https://www.cloudsavvyit.com/10623/how-to-install-docker-and-docker-compose-on-linux/)


### Step 1: Download the Latest Docker Compose Version
`docker-compose` is a separate binarya from Docker,
and it is best downloaded directly from the project’s GitHub releases.
Head to [Docker Compose’s releases page][63] and take note of the latest version number.
At the time of writing, it was `2.5.1`.

```bash
# download docker-compose binary
#sudo curl -L "https://github.com/docker/compose/releases/download/2.5.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo apt install docker-compose

# make the file executable
#sudo chmod +x /usr/local/bin/docker-compose

# check docker-compose status
docker-compose --version
```


### Step 2: Creating a Simple Docker-Compose File


### Step 3: Uninstall Docker Compose
Uninstalling Docker Compose from your Ubuntu system requires 3-step:

```bash
# delete the docker-compose if you installed binary (as done above)
sudo rm /usr/local/bin/docker-compose

# remove software package if you used apt
sudo apt remove docker-compose

# uninstall if you installed using pip
pip uninstall docker-compose
```


---------------


## Install Portainer
Adopting container orchestration platforms like Kubernetes can be hard.
[Portainer][61] is a popular Docker UI that helps you visualise your
containers, images, volumes and networks.
Portainer helps you centrally configure, manage and secure containerized environments,
regardless of where they are hosted.
It helps you take control of the Docker resources on your machine, avoiding lengthy terminal commands.

Portainer can be deployed to Docker, Docker Swarm, or Kubernetes environments
and comprised of two elements: the Portainer Server, and the Portainer Agent.
I going to deploy Portainer via Docker below.

Sources:

* [Deploying Portainer CE in Docker](https://documentation.portainer.io/v2.0/deploy/ceinstalldocker/)
* [How to Install Portainer Docker UI Manager on Ubuntu 20.04 | 18.04 | 16.04](https://docs.fuga.cloud/how-to-install-portainer-docker-ui-manager-on-ubuntu-20.04-18.04-16.04)
* [How to Install Portainer 2.0 on your Docker](https://www.letscloud.io/community/how-to-install-portainer)

* [How to Get Started With Portainer, a Web UI for Docker](https://www.cloudsavvyit.com/8911/how-to-get-started-with-portainer-a-web-ui-for-docker/)
* [Portainer Install Ubuntu tutorial - manage your docker containers](https://www.youtube.com/watch?v=ljDI5jykjE8)

* [How to Update Portainer](https://www.wundertech.net/how-to-update-portainer/)


### Step 1: Portainer Server Deployment - DONE
Use the following Docker commands to deploy the Portainer Server.

```bash
# create the volume for storing persistent data
sudo docker volume create portainer_data

# install the portainer container (ports 8000 is for agents and 9000 for web ui)
sudo docker run -d -p 8000:8000 -p 9000:9000 -p 9443:9443 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest

# check if portainer is running
sudo docker ps -a -s
```

Now using your browser, log into portainer via this URL: `localhost:9000`.


### Step 2: Manage Multiple Hosts in Portainer

* [How to manage multiple Hosts in Portainer?](https://www.youtube.com/watch?v=kKDoPohpiNk&list=RDCMUCZNhwA1B5YqiY1nLzmM0ZRg&index=4)


### Step 2: Portainer Agent Deployment
Use the following Docker commands to deploy the Portainer Agent.
Agents are installed on Docker nodes being managed remotely by Portainer.
The agent is not needed on standalone hosts,
however it does provide additional functionality if used:

```bash
# install the portainer container
sudo docker run -d -p 9001:9001 --name portainer_agent --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /var/lib/docker/volumes:/var/lib/docker/volumes portainer/agent:latest
```


# Install Some Containers

* [How to Install Nextcloud on Ubuntu, Move Data Directory, Setup Free DDNS Domain & SSL Certificate](https://www.youtube.com/watch?v=g1mYxrxdJXM&t=0s)
* [How to Install Nextcloud Hub 21 on Ubuntu 20.04 - Apache, MySQL, and PHP Configuration](https://www.youtube.com/watch?v=ZM1fL6ze4X8)
* [Fix Nextcloud Cron Job not Running on NC 21.0.3 - Nextcloud Redis Setup](https://www.youtube.com/watch?v=8JVhRtArovg)
* [How to Install Bitwarden on Ubuntu 20.04 - Self Hosting a Password Manager](https://www.youtube.com/watch?v=7bFuJCxWH6I)


### Step X: Upgrading Portainer
To [upgrade to the latest version of Portainer Server][64],
you must do it from the commandline.
Use the following commands to stop Portainer, then remove the old version,
and finally do a new install of Portainer.

```bash
# before stopping portainer, record the ip addresses of portainer-agents associated
# with this portainer instance so you can restore the connections later

# stop and remove the portainer container
sudo docker stop portainer
sudo docker rm portainer

# pull down the latest version of portainer
sudo docker pull portainer/portainer-ce:latest

# reinstall portainer
sudo docker run -d -p 8000:8000 -p 9000:9000 -p 9443:9443 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest

# check if portainer is running
sudo docker ps -a -s
```

You may want to also upgrade the Portainer Agent and this must be done separately:

```bash
# stop and remove the portainer agent container
sudo docker stop portainer-agent
sudo docker rm portainer-agent

# pull and start the updated version of the image
sudo docker pull portainer/agent:latest
sudo docker run -d -p 9001:9001 --name portainer-agent --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /var/lib/docker/volumes:/var/lib/docker/volumes portainer/agent:latest

# check if portainer is running
sudo docker ps -a -s
```

```yaml
# docker compose file for portainer agent

version: '3.8'

services:
  portainer-agent:
    image: portainer/agent:latest
    container_name: portainer-agent
    restart: unless-stopped
    ports:
      - '9001:9001'
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - /var/lib/docker/volumes:/var/lib/docker/volumes
```

>**NOTE:** Check out the video
>"[Pi-Hosted : Upgrading Portainer and Updating Containers Part 6][59]"
>for a script to do the above steps.


### Step X: Update Your Docker Container
You can update you Docker containers via the commandline,
but Portainer provides a intuitive browser UI to do the same.
Check out the videos below

* [Use Portainer to update your Docker Containers while they are running. No command line needed.](https://www.youtube.com/watch?v=Eme2TlR7Z7E)
* [How To Update Docker Container automatically with nearly zero downtime](https://www.youtube.com/watch?v=5lP_pdjcVMo)


---------------




## Install Watchtower
With [Watchtower][65] you can automate the updating of your running containerized apps.
Watchtower will pull down your new image,
gracefully shut down your existing container,
and restart it with the same options that were used when it was deployed initially.
These updates can be scheduled or done on demand.

Sources:

* [Watchtower Documentation][65]
* [How To Update Docker Container automatically with nearly zero downtime](https://www.youtube.com/watch?v=5lP_pdjcVMo)
    * [How To Update Docker Container automatically with nearly zero downtime](https://github.com/christianlempa/videos/tree/main/watchtower-tutorial)
* [Watchtower: The Docker Container That Automatically Updates Your Images](https://www.youtube.com/watch?v=DNfMuDLDq7k)
* [How to Update Docker Containers using Watchtower with Portainer](https://www.youtube.com/watch?v=mS0ylPhwQDU)


---------------


## Thoughts on Better Docker Volume Management
Volumes are a mechanism for storing data outside containers. All volumes are managed by Docker and stored in a dedicated directory on your host, usually /var/lib/docker/volumes for Linux systems.

I have been wondering if there is any kind of best practice for structuring the volumes for the containers
(more specifically, the config and data volumes).
At the moment I am using the home directory,
and just have a folder for each container, with each service's volumes.
For each docker stack or individual service, I'll also have a subdirectory and store there all volume data.
This allows for easy backups and is very organized.

I want to structured mine so that I'd be able to back up all containers easily
and also switch around containers in various compose stacks without having to change volume locations.
Something like this:

```text
/opt/docker
  /stack1
    docker-compose.yml
  /stack2
    docker-compose.yml
  /volumes
    /container1
    /container2
```

But it might make more sense to include these volumes in something like this `/home/user/data/docker/volumes`.

* [Top Tips and Use Cases for Managing Your Volumes](https://www.docker.com/blog/top-tips-and-use-cases-for-managing-your-volumes/)
* [How to move Docker's data directory from /var/lib](https://www.dzombak.com/blog/2024/01/How-to-move-Docker-s-data-directory-from-var-lib.html)



---------------



[58]:https://docs.docker.com/engine/install/
[59]:https://www.youtube.com/watch?v=q3wKqk8qVS8&list=PL846hFPMqg3jwkxcScD1xw2bKXrJVvarc&index=8
[60]:https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository
[61]:https://www.portainer.io/
[62]:https://docs.docker.com/compose/
[63]:https://github.com/docker/compose/releases
[64]:https://docs.portainer.io/v/ce-2.9/admin/upgrade/docker
[65]:https://containrrr.dev/watchtower/

