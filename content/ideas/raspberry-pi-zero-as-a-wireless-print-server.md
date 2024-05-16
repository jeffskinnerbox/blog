<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----









# Pi-Hosted
Pi-Hosted is a collection of tutorials for hosting a variety of server applications using Docker and Portainer on the Raspberry Pi.
* [pi-hosted](https://www.youtube.com/playlist?list=PL846hFPMqg3jwkxcScD1xw2bKXrJVvarc)
* [pi-hosted.com](https://pi-hosted.com/)
* [GitHub: pi-hosted/pi-hosted](https://github.com/pi-hosted/pi-hosted)



# Bill of Materials (BOM)

* Printer with USB interface - in my case, it was a [HP LaserJet P2035][04]. This printer has the rarely seen USB 2.0 Type-A interface.
* Wireless print server - I used the [Raspberry PI Zero 2 W][05] where I installed the [CUPS print server software][06].
* USB Cable - this allows flexibility for the Raspberry Pi location and [this cable][08] will convert printers female USB 2.0 Type-A to a male USB 2.0 Type-B
* USB Adapter - to convert the male USB 2.0 Type-B to male USB 2.0 Micro-B
* Power the RPi - via USB power plug and male USB 2.0 Micro-B cable

Sources:
* [What Are the Different Types of USB Cables?](https://www.anker.com/blogs/cables/how-to-identify-different-types-of-usb-cables-a-brief-guide)



-------

For printing to happen,
the Raspberry Pi print server must be connected to the same LAN that the print requesting devices are connected to.
This connection can be via wired Ethernet or wireless WiFi connection,
as long as its into the same network that the Wireless Access Point or Wireless Router serves.

* [How to make a print server with a Raspberry Pi](https://www.xda-developers.com/how-to-make-a-print-server-with-a-raspberry-pi/)

#### Step 1: Download OS for Raspberry PI Zero 2 W - DONE
I'm installing the [Raspberry PI OS Lite (64-bit)][01] on a 8GB SD Cards using the [Raspberry PI Imager][02]
(in my case, the version is [Raspberry Pi OS with desktop (Debian version 12 / bookworm) from March 15, 2024][03]).

```bash
# move to the working directory
cd ~/Downloads/ISO-Images/RPi-OS/

# downlaad the rpi image to be installed
wget https://downloads.raspberrypi.com/raspios_lite_arm64/images/raspios_lite_arm64-2024-03-15/2024-03-15-raspios-bookworm-arm64-lite.img.xz

# validate file is uncorrupted via check of digital signature
$ sha256sum 2024-03-15-raspios-bookworm-arm64-lite.img
58a3ec57402c86332e67789a6b8f149aeeb4e7bb0a16c9388a66ea6e07012e45  2024-03-15-raspios-bookworm-arm64-lite.img.xz

# uncompress to get the raspberry pi os image file
unxz *.xz
```

#### Step 2: Write Raspberry Pi Image to SD Card - DONE
Next using Linux, you have copied the Raspberry Pi OS image onto the SD card mounted to your system.
I'll be using the [Rocketek 11-in-1 4 Slots USB 3.0 Memory Card Reader][13] to create my SD Card.
Make sure to [choose a reputable SD Card][09] from [here][10], don't go cheap.

To create you SD-Card image of Raspberry Pi OS,
install and use the [Raspberry Pi Imager (`rpi-imager`)][14],
as shown below:

```bash
# install the raspberry pi imager on your desktop linux
sudo apt install rpi-imager

# execute the imager
rpi-imager
```

Next, you do the following:

* For **Operating System** select your image you downloaded (i.e. **Use custom** at the bottom of the page)
* For **Storage** you select the device containing the SD card you wish to write the image
* Now select the **"Gear"** icon and do the following:
    * Set host name (`print-server`)
    * enable SSH using password authentication
    * set your username and password (`pi` and `raspberry`)
    * set your time zone (`New York`)

>**NOTE:** As of April 2022 (Bullseye version),
>[Raspberry Pi OS has removed the default 'pi' user][33] to make it
>harder for attackers to find and compromise Internet-exposed Raspberry Pi
>devices using default credentials.
>This may (not sure about this) requires you to make use of the
>[Raspberry Pi SD-Card imager][34] to get SSH access on first boot instead of
>using the trick of placing a file name `ssh` in the `/boot` directory of the Raspberry Pi.

#### Step 3: Booting From the SD-Card - DONE
Install into your Raspberry Pi the SD Card created earlier,
connect an Ethernet cable from you LAN,
and then install power cable and/or press the power switch.

Once the RPi boots up,
you can [find your Raspberry P on your network][12] using [`netdiscover`][11].
It may take 2 to 3 minutes before you get a response from the Raspberry Pi.

```bash
# actively scan the network for all live hosts and then passively scan indefinitely
# to obtain the ip address of your raspberry pi
$ sudo netdiscover -c 3 -s 10 -L -N -r 192.168.1.0/24 | grep -E 'Raspberry|Unknown vendor'
 192.168.1.204   aa:f0:69:db:c2:b2      1      60  Unknown vendor
 192.168.1.1     62:f4:76:50:c1:da      1      60  Unknown vendor
 192.168.1.120   2e:97:fd:48:e9:db      1      60  Unknown vendor
 192.168.1.122   9a:d2:7f:f5:71:80      1      60  Unknown vendor
 192.168.1.186   2c:cf:67:26:cf:40      1      60  Unknown vendor
```

Now using the IP address (`192.168.1.186` in my case) you found for the RPi via `netdiscover`,
in the next steps we can provides the Raspberry Pi with additional SSH access keys,
enabling us to automate the update of the OS via Ansible.

#### Step 5: Query Hardware/Software Versions - DONE
To find out what version of Raspberry Pi hardware and software your are now running,
execute the following command:

```bash
# login to the raspberry pi
ssh pi@192.168.1.186

# query for version of hardware your on
$ cat /proc/device-tree/model
Raspberry Pi Zero 2 W Rev 1.0

# what version of debian you are running
$ cat /etc/debian_version
12.5

# os release notes
$ cat /etc/os-release
PRETTY_NAME="Debian GNU/Linux 12 (bookworm)"
NAME="Debian GNU/Linux"
VERSION_ID="12"
VERSION="12 (bookworm)"
VERSION_CODENAME=bookworm
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support"
BUG_REPORT_URL="https://bugs.debian.org/"

# what kernel version is running
$ uname -a
Linux print-server 6.6.20+rpt-rpi-v8 #1 SMP PREEMPT Debian 1:6.6.20-1+rpt1 (2024-03-07) aarch64 GNU/Linux
```

#### Step 6: Install `sshpass` and `lookup` - DONE
We will be using Ansible Playbooks to provision the Raspberry Pi.
Ansible want to use `ssh` with the initial playbooks requesting manual entry of a password,
aka `ssh` in non-interactive mode.

[`sshpass`][15] is a utility designed for running `ssh` using the mode referred to as
"keyboard-interactive" password authentication, but in non-interactive mode.
`ssh` uses direct TTY access to make sure that the password is indeed issued by an interactive keyboard user.
`sshpass` runs `ssh` in a dedicated tty,
fooling it into thinking it is getting the password from an interactive user.

`sshpass` must be installed on the Ansible host, so do the following there:

```bash
# install noninteractive ssh password provider
sudo apt install sshpass lookup

# restart ssh or reboot to activate sshpass
sudo reboot
```

#### Step 7: Prepare Raspberry Pi for Provisioning via Ansible - DONE
Ansible primarily communicates with client computers through SSH.
While it has the ability to handle password-based SSH authentication,
using SSH keys can help to keep things simple.
(Check [here][32] if you need more information concerning SSH,
how to generate keys, using keys, etc.)

Using the Ansible playbook `rpi-setup-ansible.yml`,
you can prepare the Raspberry Pi to be provisioned via Ansible:

```bash
# provision the raspberry pi with ansible accessibility
ansible-playbook rpi-setup-ansible.yml -i 192.168.1.186, --user pi --ask-pass
```

This playbook will:
1. Establish a user login, called `ansible`, for Ansible provisioning.
2. Give user `ansible` the `sudo` access privileges.
3. Give user `ansible` a ssh key so my `desktop` computer can remotely execute Ansible playbooks via passwordless access.
4. Disable password authentication for root (for extra-security).
5. Setup UFW firewall for only ssh outside access (for extra-security).

#### Step 7: Set a Static IP Address (for Raspberry Pi OS Bookworm) - DONE
If you’re using your Raspberry Pi as a server
often need to access it remotely from another device,
or provission it with with tools like Ansible,
setting a [static IP address][37] for it is a very good idea.
This way you find the Raspberry Pi at the same address every time,
rather than a new address being set dynamically by [DHCP][38].

If your using a release of Raspberry Pi OS Bookworm (or later),
networking on the Raspberry Pi was changed to use [NetworkManager][35]
as the standard controller for networking,
replacing the previous [dhcpcd][36] system.
NetworkManager includes a command line tool called `nmcli`,
which can control NetworkManager and report on the network status.
I'll use `nmcli` to configure the network to use a static IP address,
instead of editing files directly.

My home router is my DHCP server (`192.168.1.1`) and I have reserved the IP range 2 to 199
for dynamically allocated IP addresses.
This leaves IP range 200 to 255 for static IP addresses.
I'll use `192.168.1.207`.

Using the Ansible playbook `rpi-static-ip.yml`,
you can prepare the Raspberry Pi to be provisioned via Ansible:

```bash
# find the name of the active network interface you want to set as static
$ nmcli connection show
NAME           UUID                                  TYPE      DEVICE
preconfigured  14520577-3aa7-4f59-a532-c7feac88bf4b  wifi      wlan0
lo             dbaede8b-f3c3-46cf-8c80-24518fa77d1a  loopback  lo

# make sure you are used in the correct device name within `rpi-static-ip.yml` playbook
$ grep preconfigured rpi-static-ip.yml
    network_device_name: "preconfigured"               # nmcli's device name

# provision the raspberry pi with static ip address
ansible-playbook rpi-static-ip.yml -i 192.168.1.186, --user pi --ask-pass
```

This playbook will set the static ip address, gateway, and dns server addresses.

Sources:
* For Raspberry Pi OS Bullseye or before
    * [Set up a static IP-address on the Raspberry Pi](https://raspberrypi-guide.github.io/networking/set-up-static-ip-address)
* For Raspberry Pi OS Bookworm or after
    * [How do I set up networking on Raspberry Pi OS - Bookworm](https://raspberrypi.stackexchange.com/questions/145593/how-do-i-set-up-networking-on-raspberry-pi-os-bookworm)
    * [Set a static IP Address on Raspberry Pi OS Bookworm](https://www.abelectronics.co.uk/kb/article/31/set-a-static-ip-address-on-raspberry-pi-os-bookworm)
    * [How to Configure Network Connection Using ‘nmcli’ Tool](https://www.tecmint.com/nmcli-configure-network-connection/)

#### Step 8: Update Raspberry Pi Software Packages - DONE
Now that we have Ansible fully supported on the Raspberry Pi,
I want to do a full update of the RPi.

I'm using the Ansible playbook `rpi-setup-ansible.yml`,
you can prepare the Raspberry Pi to be provisioned via Ansible:

```bash
# provision the raspberry pi with ansible accessibility
ansible-playbook rpi-setup-ansible.yml -i 192.168.1.207, --user ansible
```

This playbook will install full-upgrade, add required packages, and reboot as needed.

Sources:
* [How to Use “sudo apt full-upgrade” in Linux](https://linuxsimply.com/linux-basics/package-management/upgrade-package/sudo-apt-full-upgrade/)

#### Step 9: Install Often Used Packages - DONE
Some software packages I use very often but don't come preinstalled on Raspberry Pi OS.
I will install them now with the Ansible playbook `rpi-prerequisites.yml`:

```bash
# provision the raspberry pi with often used packages
ansible-playbook rpi-prerequisites.yml -i 192.168.1.207, --user ansible
```

#### Step 10: Install `.dotfiles` - DONE
I use the [`.dotfiles` paradigm][16] and the [`stow`][17] utility
to manage the files which express how my computer envirnment operates.
I will install them now with the Ansible playbook `rpi-prerequisites.yml`:

```bash
# provision the raspberry pi with your .dotfiles directory and establish symbolic links
ansible-playbook rpi-dotfiles.yml -i 192.168.1.207, --user ansible
```

Sources:
* [dotfiles](https://dotfiles.github.io/)
* [The Basics of Dotfiles][16]
* [How to Create a Dotfiles Folder](https://www.youtube.com/watch?v=gibqkbdVbeY)
* [Give Your Dotfiles a Home with GNU Stow](https://www.youtube.com/watch?v=CxAT1u8G7is&t=905s)
* [Using GNU Stow to Manage Symbolic Links for Your Dotfiles][17]

#### Step X: Disable GUI Desktop Environment
I'll be using my `print-server` system as a server,
instead of using the desktop GUI environment.
I'll be using a terminal and a browser for all work on the system,
and any GUI applications will run there graphics from my X Windows desktop environment.
This will decrease the load on the `print-server` system and make boot-up quicker.

To do this, we can use the `raspi-config` tool like this:
* Execute the tool via `sudo raspi-config`
* Select **System Options** > **Boot / Auto Login** > **Console**
* After a brief pause, select **Finish** and reboot.

Sources
* [How could one automate the raspbian raspi-config setup?](https://raspberrypi.stackexchange.com/questions/28907/how-could-one-automate-the-raspbian-raspi-config-setup)
* [The Ultimate Guide to the Raspi-Config Tool](https://pimylifeup.com/raspi-config-tool/)

#### Step X: Install Docker and Portainer

#### Step X: Install the CUPS
The Common UNIX Printing System (CUPS)
is a modular printing system for Unix-like computer operating systems which allows a computer to act as a print server. A computer running CUPS is a host that can accept print jobs from client computers, process them, and send them to the appropriate printer.
CUPS consists of a print spooler and scheduler, a filter system that converts the print data to a format that the printer will understand, and a backend system that sends this data to the print device.

#### Step X: Test Ansible Configuration
Ansilbe support many ad-hoc commands that can be used to manage your nodes.
You find a long list in the webpost "[How to Use Ansible: A Reference Guide][07]"
and some listed below.
Use them to test your Ansible setup so far.

```bash
# check your inventory
ansible-inventory -i inventory --list -y

# gather facts about a node
ansible print-server -i inventory -m setup

# connectivity test, including localhost (aka controller)
ansible all -i inventory -m ping

# install the package vim on print-server from your inventory
ansible print-server -i inventory -m apt -a "name=vim"

# you can conduct a dry run to predict how the servers would be affected by your command
ansible print-server -i inventory -m apt -a "name=vim" --check

# get current disk usage, including localhost (aka controller)
$ ansible all -i inventory -m shell -a "df -h"

# get current memory usage, including localhost (aka controller)
$ ansible all -i inventory -m shell -a "free -m"

# reboot all the linux hosts, but not localhost (aka controller)
$ ansible nodes -i inventory -m shell -a "sleep 1s; shutdown -r now" -b -B 60 -P 0

# shut down all the linux hosts, but not localhost (aka controller)
$ ansible nodes -i inventory -m shell -a "sleep 1s; shutdown -h now" -b -B 60 -P 0

# uptime check for individual host 'print-server'
ansible print-server -i inventory -a "uptime" -u root

# specify multiple hosts by separating them with colons
ansible print-server:node-2 -i inventory -a "uptime" -u root
```



-------



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

### Step X: Upgrading Portainer, Manually Method
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


### Step X: Upgrading Portainer, Script Method
**NOTE:** Check out the video
"[Pi-Hosted : Upgrading Portainer and Updating Containers Part 6][59]"
for a [script that does a Portainer upgrade](https://github.com/novaspirit/pi-hosted/blob/master/update_portainer.sh)

### Step X: Update Your Docker Container
You can update you Docker containers via the commandline,
but Portainer provides a intuitive browser UI to do the same.
Check out the videos below

* [Use Portainer to update your Docker Containers while they are running. No command line needed.](https://www.youtube.com/watch?v=Eme2TlR7Z7E)
* [How To Update Docker Container automatically with nearly zero downtime](https://www.youtube.com/watch?v=5lP_pdjcVMo)



--------



# Install CUPS
* [Use a Raspberry PI Zero W as a Wireless Print Server](https://community.element14.com/products/raspberry-pi/raspberrypi_projects/b/blog/posts/use-a-raspberry-pi-zero-w-as-a-wireless-print-server)
* [CUPS and Raspberry Pi AirPrinting](https://www.developer.com/mobile/cups-and-raspberry-pi-airprinting/)
* [How to Turn a Printer into a Wireless Printer with Raspberry Pi](https://www.youtube.com/watch?v=hdwqQjDjMzU)
* [Create your own Canon Printer server with Raspberry Pi](https://www.youtube.com/watch?v=3powPeY5_-k)
* [Turn your USB Printer into a Wireless Printer! 2019](https://www.youtube.com/watch?v=4g9vnk28480)
* [Turn USB Printer to WiFi Printer for $15 | Convert Any USB Printer Wireless](https://www.youtube.com/watch?v=P3XRi-CD1a0)

#### Step X: Install and Configure CUPS on Print Server
On many Linux  installations,
support for printers via CUPS is pre-configured and is an active service.
To check if CUPS is active, use the following command:

```bash
# check the operational status of cups
systemctl status cups
```


```bash
# install some prerequisite software
sudo apt install -y build-essential git autoconf libtool

# install some of your developer tools

# install cups and its libraries
sudo apt install -y cups libcups2-dev libcupsimage2-dev
```

#### Step X: Configure CUPS
Edit the file `/etc/cups/cupsd.conf` and make the following changes.

1. Scroll down until you see the `Listen` configuration directive.
Comment it out so that CUPS is available over the network.

```bash
# Only listen for connections from the local machine
# Listen localhost:631
Port 631
```

Look for the `<Location />` directive,
and add `Allow all` (or a specific list of IPs, if your local network is not secure) to allow access.

```bash
<Location />
  # Allow remote access...
  Order allow,deny
  Allow all
</Location>
```

Save the file and restart CUPS:

```bash
# restart cups
sudo /etc/init.d/cups restart
```

#### Step X: Configure Your Printer in CUPS




Now configure CUPS to allow us to access its Web Interface
and allow use access via its DNS name instead of just the IP address.
We want to access CUPS web Interface from another computer.

2. Install Drivers
git clone https://github.com/agalakhov/captdriver.git
cd captdriver
autoreconf -i
./configure
make

sudo cp src/rastertocapt /usr/lib/cups/filter/
sudo cp Canon*.ppd /usr/share/ppd/custom/

3. CUPS remote access
sudo cupsctl --remote-any
sudo usermod -a -G lpadmin <your-username>



-------



# Printer Configuration

#### Step X: Is CUPS Running Locally?
I discovered that my fresh install of Ubuntu comes with CUPS installed and active.
To see that cupsd is indeed running on the Raspberry Pi, use the command:

```bash
# check the operational status of cups
systemctl status cups

# another way to check if the cups daemon is running
ps aux | grep cupsd
```

If you find the `cupsd` daemon running, you should stop it
and assure it doesn't restart when the system is rebooted:

```bash
# stop the cupsd daemon
sudo systemctl stop cups

# disable the cupsd daemon from restarting
sudo systemctl disable cups
```

Sources:
* [How to Start, Stop and Restart Services in Linux Using systemctl Command](https://www.geeksforgeeks.org/start-stop-restart-services-using-systemctl-in-linux/#7-how-to-disable-a-system-service-in-linux)



-------



# Considerations for a Long-Running Raspberry Pi
* [Considerations for a long-running Raspberry Pi](https://www.dzombak.com/blog/2023/12/Considerations-for-a-long-running-Raspberry-Pi.html)
* [Raspberry Pi Reliability](https://www.dzombak.com/blog/series/pi-reliability.html)
* do a periodic backup



[01]:https://www.raspberrypi.com/software/operating-systems/
[02]:https://www.raspberrypi.com/software/
[03]:https://downloads.raspberrypi.com/raspios_lite_arm64/images/raspios_lite_arm64-2024-03-15/2024-03-15-raspios-bookworm-arm64-lite.img.xz
[04]:https://support.hp.com/us-en/product/details/hp-laserjet-p2035-printer-series/3662025
[05]:https://www.raspberrypi.com/products/raspberry-pi-zero-2-w/
[06]:https://ubuntu.com/server/docs/install-and-configure-a-cups-print-server
[07]:https://www.printables.com/model/694802-retro-desktop-pc-raspberry-pi-case-v2
[08]:https://www.commfront.com/products/usb-type-a-to-usb-type-b-cable?variant=13178553091
[09]: http://www.wirelesshack.org/best-micro-sd-card-for-the-raspberry-pi-model-2.html
[10]:http://www.jeffgeerling.com/blogs/jeff-geerling/raspberry-pi-microsd-card
[11]:https://shownotes.opensourceisawesome.com/netdiscover/
[12]:https://www.youtube.com/watch?v=hx7DB7Iqslk
[13]:http://www.amazon.com/gp/product/B00GVRHON2?psc=1&redirect=true&ref_=oh_aui_detailpage_o00_s01
[14]:https://www.raspberrypi.com/software/
[15]:https://www.redhat.com/sysadmin/ssh-automation-sshpass
[16]:https://www.youtube.com/watch?v=BE87kUCTBVU
[17]:https://systemcrafters.net/managing-your-dotfiles/using-gnu-stow/
[18]:
[19]:
[20]:
[21]:
[22]:
[23]:
[24]:
[25]:
[26]:
[27]:
[28]:
[29]:
[30]:
[31]:
[32]:https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-1804
[33]:https://www.bleepingcomputer.com/news/security/raspberry-pi-removes-default-user-to-hinder-brute-force-attacks/
[34]:https://www.raspberrypi.com/software/
[35]:https://forums.raspberrypi.com/viewtopic.php?t=357739
[36]:https://roy.marples.name/projects/dhcpcd
[37]:https://www.efficientip.com/what-is-dhcp-and-why-is-it-important/
[38]:https://www.avast.com/c-static-vs-dynamic-ip-addresses

[58]:https://docs.docker.com/engine/install/
[59]:https://www.youtube.com/watch?v=q3wKqk8qVS8&list=PL846hFPMqg3jwkxcScD1xw2bKXrJVvarc&index=8
[60]:https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository
[61]:https://www.portainer.io/
[62]:https://docs.docker.com/compose/
[63]:https://github.com/docker/compose/releases
[64]:https://docs.portainer.io/v/ce-2.9/admin/upgrade/docker




