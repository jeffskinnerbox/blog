<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>



---------------



# Development Tools: Docker & Portainer

**Docker** is a popular application that simplifies the process of managing application processes in containers.
Containers let you run your applications in resource-isolated processes.
They’re similar to virtual machines, but containers are more portable,
more resource-friendly, and more dependent on the host operating system.

For applications depending on several services,
orchestrating all the containers to start up, communicate,
and shut down together can quickly become unwieldy.
**Docker Compose** is a tool that allows you to run multi-container
application environments based on definitions set in a YAML file.
It uses service definitions to build fully customizable environments
with multiple containers that can share networks and data volumes.

Adopting container orchestration platforms like Kubernetes can be hard.
**[Portainer][39]** is a popular Docker UI that helps you visualise your
containers, images, volumes and networks.
Portainer helps you centrally configure, manage and secure containerized environments,
regardless of where they are hosted.
It helps you take control of the Docker resources on your machine, avoiding lengthy terminal commands.

>**NOTE:** By default, the `docker` command can only be run the root user
>or by a user in the `docker` group, which is automatically created during Docker’s installation process.

Sources:

* [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)
* [Install the Compose plugin](https://docs.docker.com/compose/install/linux/#install-using-the-repository)
* [How to Install Portainer on Ubuntu](https://www.wundertech.net/portainer-on-ubuntu/)
* [Install Portainer CE with Docker on Linux](https://docs.portainer.io/start/install-ce/server/docker/linux)

For developing with Docker, consider these Sources:

* [Develop with Docker](https://docs.docker.com/develop/)
* [How to Deploy NGINX Reverse Proxy on Docker](https://phoenixnap.com/kb/docker-nginx-reverse-proxy)
* [How to Deploy and Manage MongoDB with Docker](https://phoenixnap.com/kb/docker-mongodb)
* [How to Containerize Legacy Applications](https://phoenixnap.com/kb/how-to-containerize-applications)
* [Docker Volumes: How to Create & Get Started](https://phoenixnap.com/kb/docker-volumes)
* [Docker and Running your self-hosted applications in a more secure way behind a reverse proxy.](https://www.youtube.com/watch?v=8T68pB_Fkm4)



## Docker Engine & Docker Compose


#### Step 1: Installing Docker

Ubuntu is my go-to Linux OS and installing on Ubuntu is fairly straight-forward.
I'll used the installation scripts below.
This involves adding a new package source,
adding the GPG key from Docker to ensure the downloads are valid,
and then install the Docker package.

While not the absolute latest Docker version,
I’ll install Docker from the Dockers official Ubuntu repository,
instead of Docker's generic repository.

```bash
# before you can install docker engine, you need to uninstall any previous installed conflicting packages
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt remove $pkg; done

# clean up any existing docker related data
rm /var/lib/docker/*

# update your existing list of ubunutu packages
sudo apt update

# install a few prerequisite packages
sudo apt install apt-transport-https ca-certificates curl gnupg software-properties-common

# add docker's official gpg key
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# add the docker repository to apt sources
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

# check to make sure you are about to install from docker repo or ubuntu repo
apt-cache policy docker-ce
```

From the above last command,
you'll see the installation will be from the Docker repository for what ever version of Ubuntu you are running.
Now lets install Docker:

```bash
# install docker packages
sudo apt install docker-ce

# check to see if docker is running
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# docker should be running, but make sure
sudo service docker start

# verify that the docker engine installation is successful running
sudo docker run hello-world
```


#### Step 2: Upgrade Docker

Docker and Docker Compose will be automatically upgraded by Ubuntu from the official Ubuntu repository for Docker.


#### Step 3: Install Docker Compose

To ensure we get the latest version,
we’ll install Docker Compose from the official Docker repository.
To do that, we’ll add a new package source,
add the GPG key from Docker to ensure the downloads are valid,
and then install the package.

```bash
# download docker compose
sudo apt update
sudo apt install docker-compose-plugin

# verify that the installation of docker compose was successful
docker compose version
```


#### Step 4: Upgrade Docker Compose

Docker Compose will be upgraded automatically by Ubuntu from the official Ubuntu repository for Docker.


## Portainer

Portainer gives users a way to manage their Docker containers,
accross multiple sites, through a web interface.
Portainer also gives you the ability to use stacks,
which is an easy way to create new containers and allows them to be created using a docker-compose format.

**NOTE:** Instructions below must be performed on Ubuntu 22.04 or greater.


#### Step 1: Install Portainer

Before you install Portainer on Ubuntu,
you must ensure that you have Docker installed on Ubuntu first.

```bash
# create the volume for storing persistent data
sudo docker volume create portainer_data

# install the portainer container (ports 8000 is for agents and 9000 for web ui)
sudo docker run -d -p 8000:8000 -p 9000:9000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest

# check if portainer is running
sudo docker ps -a -s

# log into portainer and setup your password, etc.
#google-chrome https://localhost:9443   # <-- for https access
google-chrome https://localhost:9000   # <-- for https access
```

Now using your browser, log into portainer via this URL: `localhost:9000`.


#### Step 2: Upgrading Portainer

To [upgrade to the latest version of Portainer Server][40],
you must do it from the commandline.
Use the following commands to stop Portainer, then remove the old version,
and finally do a new install of Portainer.

```bash
# stop and remove the portainer container
sudo docker stop portainer
sudo docker rm portainer

# pull down the latest version of portainer
sudo docker pull portainer/portainer-ce:latest

# reinstall portainer
sudo docker run -d -p 8000:8000 -p 9000:9000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```

You may want to also upgrade the Portainer Agent and this must be done separately:

```bash
# stop and remove the portainer agent container
sudo docker stop portainer_agent
sudo docker rm portainer_agent

# pull nd start the updated version of the image
sudo docker pull portainer/agent:latest
sudo docker run -d -p 9001:9001 --name portainer_agent --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /var/lib/docker/volumes:/var/lib/docker/volumes portainer/agent:latest
```


#### Step 3: Refresh Portainer Stacks

Using your [GitHub repository for your HomeLab Portainer Stacks][61],
redeploy your stacks to you `desktop` computer.



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
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done

# update the apt package index and install required packages
sudo apt update
sudo apt install apt-transport-https ca-certificates curl gnupg lsb-release

# add docker’s official gpg key
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# set up the stable repository
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# install the latest version of docker engine
sudo apt update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# check the currently install version of docker
$ docker --version
Docker version 27.4.1, build b9d17ea
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


### Step 4: Uninstall Docker Engine - DONE

```bash
# uninstall the docker engine, the cli, and containerd packages
sudo apt-get purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras

# delete all images, containers, volumes, or custom configuration files
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd

# delete source list and keyrings
sudo rm /etc/apt/sources.list.d/docker.list
sudo rm /etc/apt/keyrings/docker.asc
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

---------------


## Install Docker Compose

[Docker Compose][62] is a tool for defining and running multi-container Docker applications.
With Compose, you use a YAML file to configure your application’s services.
Then, with a single command, you create and start all the services from your configuration.

>**NOTE:** Docker recommends the best way to get Docker Compose is to install Docker Desktop.
>Docker Desktop includes Docker Compose along with Docker Engine and Docker CLI which are Compose prerequisites.

If you already have Docker Engine and Docker CLI installed (as done in the above steps),
you can install the Docker Compose plugin from the command line, by either
using Docker's repository or downloading and installing manually

* [Docker-compose tutorial](https://www.youtube.com/watch?v=qH4ZKfwbO8w)
* [Overview of Docker Compose](https://docs.docker.com/compose/)
* [Install Docker Compose](https://docs.docker.com/compose/install/)
* [How to Install Docker Compose on Ubuntu 20.04](https://phoenixnap.com/kb/install-docker-compose-on-ubuntu-20-04)
* [How to Install Docker and Docker Compose on Linux](https://www.cloudsavvyit.com/10623/how-to-install-docker-and-docker-compose-on-linux/)


### Step 1: Download the Docker Compose via Repository - DONE

Following the instructions given [here][63],
you can install Dockeer COmpose via the repository we just installed above:

```bash
# update the package index, and install the latest version of docker compose
sudo apt-get update
sudo apt-get install docker-compose-plugin

# check docker-compose status
docker-compose --version
```


### Step 3: Upgrade Docker Compose - DONE

To upgrade Docker Compose, first run `sudo apt-get update`,
then follow the installation instructions, choosing the new version you want to install:

```bash
sudo apt-get update
sudo apt-get install docker-compose
```


### Step 3: Uninstall Docker Compose - DONE

Uninstalling Docker Compose from your Ubuntu system requires 3-step:

```bash
# remove software package if you used apt (as done above)
sudo apt remove docker-compose

# delete the docker-compose if you installed binary
sudo rm /usr/local/bin/docker-compose

# uninstall if you installed using pip
pip uninstall docker-compose

# uninstall if you installed using snap
snap uninstall docker-compose
```


---------------


## Install Portainer (or Docker Desktop?)

While both [Docker Desktop][41] and [Portainer][39] are used to manage Docker containers,
Docker Desktop is primarily a local development tool with a user-friendly interface for managing containers on your machine,
while Portainer is a web-based platform designed to manage multiple Docker environments
and clusters from a single dashboard, making it better suited for managing containers across different hosts or in production environments;
essentially, Docker Desktop focuses on individual development,
while Portainer is for centralized container management.
Another option is [Kubernetes (aka K8s)][42]
but adopting container orchestration platforms like Kubernetes
can be hard since its engineered for enterprise networks.

I have choosen [Portainer][61] as my Docker UI that helps you visualise my
containers, images, volumes, and networks accross all my docker instances in my network.
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
# first, create the volume that Portainer Server will use to store its database
sudo docker volume create portainer_data

# install the portainer container (ports 8000 is for agents and 9000 for web ui)
sudo docker run -d -p 8000:8000 -p 9443:9443 -p 9000:9000 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest

# check if portainer is running
sudo docker ps -a -s | grep portainer
```

Now using your browser, log into portainer via this URL: `localhost:9443`.


### Step 2: Upgrading Portainer Server - And Keepig Your Data


### Step 2A: Upgrading Portainer Server - Do Backups

**Strongly recommend that you take a backup of your Portainer instance before updating.**

* [Portainer Backup](https://docs.portainer.io/2.25/admin/settings#backup-portainer)
* [Backup Docker Data and Configs](https://wiki.opensourceisawesome.com/books/backing-up-docker/page/backup-docker-data-and-configs)


### Step 2B: Upgrading Portainer Server

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
```

Now that you have stopped and removed the old version of Portainer,
**you must ensure that you have the most up to date version of the image locally**.
You can do this with a `docker pull` command:

```bash
# pull down the latest version of portainer
sudo docker pull portainer/portainer-ce:latest

# reinstall portainer
sudo docker run -d -p 8000:8000 -p 9000:9000 -p 9443:9443 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest

# check if portainer is running
sudo docker ps -a -s
```

Sources:

* [Updating on Docker Standalone](https://docs.portainer.io/2.25/start/upgrade/docker)


### Step 2C: Upgrade Portainer Agents

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


### Step 3: Portainer Agent Deployment - DONE

Use the following Docker commands to deploy the Portainer Agent.
Agents are installed on Docker nodes being managed remotely by Portainer.
The agent is not needed on standalone hosts,
however it does provide additional functionality if used:

```bash
# stop and remove the portainer agent container
sudo docker stop portainer_agent
sudo docker rm portainer_agent

# install the portainer container
sudo docker run -d -p 9001:9001 --name portainer_agent --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /var/lib/docker/volumes:/var/lib/docker/volumes portainer/agent:latest
```

Once the agent has been installed you are ready to add the environment to your Portainer Server installation.
There are [multiple way of doing this][43],
but I'm be using the [Agent method][44].

* [Install Portainer Agent on Docker Standalone][44]
* [How to manage multiple Hosts in Portainer?](https://www.youtube.com/watch?v=kKDoPohpiNk&list=RDCMUCZNhwA1B5YqiY1nLzmM0ZRg&index=4)


#### Step 4: Manage Remote Docker Containers via Desktop Portainer - DONE

We now want to connect the remote host Docker containers with my `desktop` portainer
so all my containers can be managed from a single site.
To do this, we must connect the Portainer Agent with Portainer.

To connect your Docker container Portainer Agent, you do the following on your `desktop` Portainer.

* Select **Environments** from the lefthand menu.
* Select the **Add environment** button at top left.
* Select **Dockert Standalone** and then **Start Wizard**.
* Select the **Copy command** for "Linux & Windows WSL"
* For the **Name** field, enter the name of host,
for **Environment URL** enter `<ip-address>:9001`
* Select **Connect** at the bottom left of the page.

>**NOTE:** If you get a message sating the Portainer agent is already paired,
>restart the remote host to clear the old pairing and attempt another **Connect**.

Source:

* [Installing Portainer and Portainer Agent - An update to show you an easier way to manage Docker](https://www.youtube.com/watch?v=-LPaWq1_GF0)
* [Add ALL of your Docker Hosts to ONE Portainer Dashboard Using the Portainer Edge Agent](https://www.youtube.com/watch?v=8YmQoQ7gAg8)


### Step 5: Upgrading Portainer Agent

Since you install the Portainer Agent as a Docker container,
you can maintian just like any other Docker container.
For instrctions on how to do this, see below.


---------------


## Maintaining Your Docker Container

You can update you Docker containers via the commandline,
but Portainer provides a intuitive browser UI to do the same.
Check out the videos below

* [Use Portainer to update your Docker Containers while they are running. No command line needed.](https://www.youtube.com/watch?v=Eme2TlR7Z7E)
* [How To Update Docker Container automatically with nearly zero downtime](https://www.youtube.com/watch?v=5lP_pdjcVMo)


#### Step X: Refresh Portainer Stacks

Using your [GitHub repository for your HomeLab Portainer Stacks][61],
redeploy your stacks to you `desktop` computer.



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



[39]:https://www.portainer.io/
[40]:https://docs.portainer.io/v/ce-2.9/admin/upgrade/docker
[41]:https://www.docker.com/products/docker-desktop/
[42]:https://kubernetes.io/
[43]:https://docs.portainer.io/2.25/admin/environments/add/docker
[44]:https://docs.portainer.io/2.25/admin/environments/add/docker/agent

[58]:https://docs.docker.com/engine/install/
[59]:https://www.youtube.com/watch?v=q3wKqk8qVS8&list=PL846hFPMqg3jwkxcScD1xw2bKXrJVvarc&index=8
[60]:https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository
[61]:https://www.portainer.io/
[62]:https://docs.docker.com/compose/
[63]:https://github.com/docker/compose/releases
[64]:https://docs.portainer.io/2.25/start/upgrade/docker
[65]:https://containrrr.dev/watchtower/

