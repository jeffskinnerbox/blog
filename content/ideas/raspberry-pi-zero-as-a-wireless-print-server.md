<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----




* [How to make a print server with a Raspberry Pi](https://www.xda-developers.com/how-to-make-a-print-server-with-a-raspberry-pi/)





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


#### Step 1: Download OS for Raspberry PI Zero 2 W
I'm installing the [Raspberry PI OS Lite (64-bit)][01] on a 8GB SD Cards using the [Raspberry PI Imager][02]
(in my case, the version is [Raspberry Pi OS with desktop (Debian version 12 / bookworm) from March 15, 2024][03]).

```bash
# move to the working directory
cd ~/Downloads/ISO-Images/RPi-OS/

# downlaad the rpi image to be installed
wget https://downloads.raspberrypi.com/raspios_lite_arm64/images/raspios_lite_arm64-2024-03-15/2024-03-15-raspios-bookworm-arm64-lite.img.xz

# validate file is uncorrupted via check of digital signature
$ sha256sum

# uncompress to get the raspberry pi os image file
unxz
```


#### Step 3: Write Raspberry Pi Image to SD Card
Next using Linux, you have copied the Raspberry Pi OS image onto the SD card mounted to your system.
I'll be using the [Rocketek 11-in-1 4 Slots USB 3.0 Memory Card Reader][14] to create my SD Card.
Make sure to [choose a reputable SD Card][15] from [here][10], don't go cheap.

To create you SD-Card image of Raspberry Pi OS,
install and use the [Raspberry Pi Imager (`rpi-imager`)](https://www.raspberrypi.com/software/),
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
    * Set host name (`ntp-server`)
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

#### Step 4: Booting From the SD-Card
Install into your Raspberry Pi the SD Card created earlier,
connect an Ethernet cable from you LAN,
and then install power cable and/or press the power switch.

Once the RPi boots up,
you can [find your Raspberry P on your network][12] using [`netdiscover`][31].
It may take 2 to 3 minutes before you get a response from the Raspberry Pi.

```bash
# actively scan the network for all live hosts and then passively scan indefinitely
# to obtain the ip address of your raspberry pi
$ sudo netdiscover -c 3 -s 10 -L -N -r 192.168.1.0/24 | grep Raspberry
 0.0.0.0         b8:27:eb:fa:14:96      1      60  Raspberry Pi Foundation
 192.168.1.175   b8:27:eb:fa:14:96      1      60  Raspberry Pi Foundation
```

Now using the IP address (`192.168.1.175` in my case) you found for the RPi via `netdiscover`,
in the next steps we can provides the Raspberry Pi with additional SSH access keys,
enabling us to automate the update of the OS via Ansible.

#### Step 5: Query Hardware/Software Versions
To find out what version of Raspberry Pi hardware and software your are now running,
execute the following command:

```bash
# login to the raspberry pi
ssh pi@192.168.1.175

# query for version of hardware your on
cat /proc/device-tree/model
Raspberry Pi 2 Model B Rev 1.1

# what version of debian you are running
$ cat /etc/debian_version
12.1

# os release notes
$ cat /etc/os-release
PRETTY_NAME="Raspbian GNU/Linux 12 (bookworm)"
NAME="Raspbian GNU/Linux"
VERSION_ID="12"
VERSION="12 (bookworm)"
VERSION_CODENAME=bookworm
ID=raspbian
ID_LIKE=debian
HOME_URL="http://www.raspbian.org/"
SUPPORT_URL="http://www.raspbian.org/RaspbianForums"
BUG_REPORT_URL="http://www.raspbian.org/RaspbianBugs"

# what kernel version is running
$ uname -a
Linux ntp-server 6.6.20+rpt-rpi-v7 #1 SMP Raspbian 1:6.6.20-1+rpt1 (2024-03-07) armv7l GNU/Linux
```

#### Step X: Prepare Raspberry Pi for Provisioning via Ansible
**Alternative is to use the Ansible playbook `rpi-setup-ansible.yml`.**

#### Step 6A: Set a Static IP Address (for Raspberry Pi OS Bullseye) - NOT DONE!!
If you’re using your Raspberry Pi as a server
often need to access it remotely from another device,
or provission it with with tools like Ansible,
setting a [static IP address][37] for it is a very good idea.
This way you find the Raspberry Pi at the same address every time,
rather than a new address being set dynamically by [DHCP][38].

My home router is my DHCP server (`192.168.1.1`) and I have reserved the IP range 2 to 199
for dynamically allocated IP addresses.
This leaves IP range 200 to 255 for static IP addresses.
I'll use `192.168.1.206`.

You can set up a static IP-address via the terminal.
For this we need to change the `/etc/dhcpcd.conf` file.
Scroll to the bottom, and add the following text:

```bash
# create a static ip address for this device
interface eth0
metric 300
static ip_address=192.168.1.206/24
static routers=192.168.1.1
static domain_name_servers=192.168.1.1

# use wifi if ethernet isn't available
interface wlan0
metric 200
```

Now reboot your Raspberry Pi for the changes to be incorporated:

```bash
# reboot the rpi
sudo reboot

# once the rpi comes up, check if the new static ip adress is active
ssh pi@192.168.1.206
```

Source:
* [Set up a static IP-address on the Raspberry Pi](https://raspberrypi-guide.github.io/networking/set-up-static-ip-address)

### Step 6B: Set a Static IP Address & Make Secure
**Alternative is to use the Ansible playbook `rpi-static-ip.yml`.**

Just in case your using a release of Raspberry Pi OS Bookworm (or later),
networking on the Raspberry Pi was changed to use [NetworkManager][35] as the standard controller for networking,
replacing the previous [dhcpcd][36] system.
NetworkManager includes a command line tool called `nmcli`,
which can control NetworkManager and report on the network status.
I'll use `nmcli` to configure the network to use a static IP address,
instead of editing files directly.

```bash
# find the name of the network interface you want to set as static
$ sudo nmcli connection show
NAME                UUID                                  TYPE      DEVICE
Wired connection 1  8b63b5d2-c0d0-34a5-aa7c-6e45be29c86b  ethernet  eth0
lo                  326a5c71-6b00-41c5-a1d6-eaa20f53e12b  loopback  lo

# OR
$ sudo nmcli dev status
DEVICE  TYPE      STATE                   CONNECTION
eth0    ethernet  connected               Wired connection 1
lo      loopback  connected (externally)  lo
```

Now we know the name of the network connection we want to update,
we can send four commands to set the new static IP address, Gateway, and DNS server.

```bash
# set the new ip address
sudo nmcli con mod "Wired connection 1" ipv4.addresses 192.168.1.206/24

# set the new gateway address
sudo nmcli con mod "Wired connection 1" ipv4.gateway 192.168.1.1

# set the new dns server address
sudo nmcli con mod "Wired connection 1" ipv4.dns "192.168.1.1,8.8.8.8"

# change the addressing from DHCP to static
sudo nmcli con mod "Wired connection 1" ipv4.method manual
```

When you have finished updating the network settings on your Raspberry Pi,
you can restart the network connection with the following command:

```bash
# restart the network connection
sudo nmcli con down "Wired connection 1" && sudo nmcli con up "Wired connection 1"
```

If you are using SSH to connect to your Raspberry Pi,
running the above command will cause the SSH session to end if the IP address changes.
You'll need to re-login to the Raspberry Pi,
but this time using the new IP address (i.e. `192.168.1.206`).

```bash
# re-login to the raspbrry pi
ssh pi@192.168.1.206

# examine the changes to the network interface
$ sudo nmcli -p connection show
```

Source:
* [Set a static IP Address on Raspberry Pi OS Bookworm](https://www.abelectronics.co.uk/kb/article/31/set-a-static-ip-address-on-raspberry-pi-os-bookworm)
* [How to Configure Network Connection Using ‘nmcli’ Tool](https://www.tecmint.com/nmcli-configure-network-connection/)

#### Step X: Update Raspberry Pi Software Packages
**Alternative is to use the Ansible playbook `rpi-upgrade.yml`.**

Now lets do a `sudo apt full-upgrade` packages are upgrade to their latest versions
by replacing or removing the old version package.

```bash
# update the software
sudo apt update && sudo apt -y full-upgrade

# reboot the raspberry pi
sudo reboot
```

Sources:
* [How to Use “sudo apt full-upgrade” in Linux](https://linuxsimply.com/linux-basics/package-management/upgrade-package/sudo-apt-full-upgrade/)

#### Step 7: Disable GUI Desktop Environment
I'll be using my `ntp-server` system as a server,
instead of using the desktop GUI environment.
I'll be using a terminal for all work on the system,
and any GUI applications will run there graphics from my X Windows desktop environment.
This will decrease the load on the `ntp-server` system and make boot up quicker.

To do this, we can use the `raspi-config` tool like this:
* Execute the tool via `sudo raspi-config`
* Select **System Options** > **Boot / Auto Login** > **Console**
* After a brief pause, select **Finish** and reboot.

Sources
* [How could one automate the raspbian raspi-config setup?](https://raspberrypi.stackexchange.com/questions/28907/how-could-one-automate-the-raspbian-raspi-config-setup)
* [The Ultimate Guide to the Raspi-Config Tool](https://pimylifeup.com/raspi-config-tool/)

#### Step 8: Copy Ansible SSH Keys to Raspberry Pi
Ansible primarily communicates with client computers through SSH.
While it has the ability to handle password-based SSH authentication,
using SSH keys can help to keep things simple.
(Check [here][32] if you need more information concerning SSH,
how to generate keys, using keys, etc.)

>**NOTE:** The Ansible server could exist anywhere as long as they are reachable via SSH.
>On your Ansible host machine,
>your first step is to install Ansible and any extension you may want to use.
>See `using-vagrant-docker-and-ansible.md` to understand how to do this.

**Alternative is to use the Ansible playbook `rpi-upgrade.yml`.**
On my Ansible server (my Linux desktop computer),
I have created a specific SSH key for Ansible work.
That key is `~/.ssh/ansible.pub`.
I'll use one of the methods below to push that key to my Raspberry Pi.

##### Method 8A: Copying Public Key Using ssh-copy-id
The simplest method to provide the SSH keys to the client computer
is to use the `ssh-copy-id` tool.
Launching from the Ansible server, the syntax is:
`ssh-copy-id username@remote_host`.
In my case:

```bash
# from my desktop computer, copying public key using ssh-copy-id
ssh-copy-id -i ~/.ssh/ansible.pub pi@192.168.1.206
```

To test if this is successful,
login to your Ansible client via SSH: `pi@192.168.1.206`
and you should get in without being prompted for a password.

##### Method 8B: Copying Public Key Using SSH
If you do not have `ssh-copy-id` available on your computer,
but you have password-based SSH access to an account on your server,
you can upload your keys using a conventional SSH method:

```bash
# from my desktop computer, copying public key using ssh
cat ~/.ssh/ansible.pub | ssh pi@ntp-server "mkdir -p ~/.ssh && touch ~/.ssh/authorized_keys && chmod -R go= ~/.ssh && cat >> ~/.ssh/authorized_keys"
```

##### Method 8C: Copying Public Key Manually
The final method is just to do it all manually.
Assuming SSH is already established on your Ansible server,
use the `cat` command to print the contents of your
non-root user’s SSH public key file to the terminal’s output:

```bash
# copy this public ssh key
cat ~/.ssh/id_rsa.pub
```

Copy the resulting output to your clipboard,
then open a new terminal and connect to one of your Ansible hosts using SSH,
and do the following:

1. Switch to the client machine’s root user.
1. As the root user, open the `authorized_keys` within the `~/.ssh` directory:
1. In the file, paste your Ansible server user’s SSH key, then save the file.

#### Step 9: Creating Inventory File
Ansible needs to know your remote server names or IP address.
This information is stored in a file called `hosts`, or often refered to as your "inventory".
The default file is `/etc/ansible/hosts`.
You can edit this one or create a new one in your `$HOME` directory,
or better yet, place the `inventory` file in your projects directory referance it
on the command-line when running `ansible`.

```bash
# create the hosts (aka inventory) file for your raspberry pi
cat <<EOF > inventory
# Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
# Version:      0.0.1

# aka ansible hosts file

# ansible control node
#[controller]
#127.0.0.1 ansible_connection=local

# ansible managed hosts (aka nodes)
[nodes]
ntp-server ansible_ssh_host=192.168.1.206 ansible_ssh_port=22 kubernetes_role=node
#node-1 ansible_ssh_host=192.168.33.231 ansible_ssh_port=22 kubernetes_role=master
#node-2 ansible_ssh_host=192.168.33.232 ansible_ssh_port=22 kubernetes_role=node
#node-3 ansible_ssh_host=192.168.33.233 ansible_ssh_port=22 kubernetes_role=node

# ansible varables applied to [nodes]
[nodes:vars]
ansible_user='pi'
ansible_ssh_user=pi
deploy_target=pi
ansible_become=yes
ansible_become_method=sudo
ansible_python_interpreter='/usr/bin/env python3'
EOF

```

#### Step 10: Test Ansible Configuration
Ansilbe support many ad-hoc commands that can be used to manage your nodes.
You find a long list in the webpost "[How to Use Ansible: A Reference Guide][07]"
and some listed below.
Use them to test your Ansible setup so far.

```bash
# check your inventory
ansible-inventory -i inventory --list -y

# gather facts about a node
ansible ntp-server -i inventory -m setup

# connectivity test, including localhost (aka controller)
ansible all -i inventory -m ping

# install the package vim on ntp-server from your inventory
ansible ntp-server -i inventory -m apt -a "name=vim"

# you can conduct a dry run to predict how the servers would be affected by your command
ansible ntp-server -i inventory -m apt -a "name=vim" --check

# get current disk usage, including localhost (aka controller)
$ ansible all -i inventory -m shell -a "df -h"

# get current memory usage, including localhost (aka controller)
$ ansible all -i inventory -m shell -a "free -m"

# reboot all the linux hosts, but not localhost (aka controller)
$ ansible nodes -i inventory -m shell -a "sleep 1s; shutdown -r now" -b -B 60 -P 0

# shut down all the linux hosts, but not localhost (aka controller)
$ ansible nodes -i inventory -m shell -a "sleep 1s; shutdown -h now" -b -B 60 -P 0

# uptime check for individual host 'ntp-server'
ansible ntp-server -i inventory -a "uptime" -u root

# specify multiple hosts by separating them with colons
ansible ntp-server:node-2 -i inventory -a "uptime" -u root
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
[09]:
[10]:http://www.jeffgeerling.com/blogs/jeff-geerling/raspberry-pi-microsd-card
[11]:
[12]:https://www.youtube.com/watch?v=hx7DB7Iqslk
[13]:
[14]:http://www.amazon.com/gp/product/B00GVRHON2?psc=1&redirect=true&ref_=oh_aui_detailpage_o00_s01
[15]:http://www.wirelesshack.org/best-micro-sd-card-for-the-raspberry-pi-model-2.html
[16]:
[17]:https://en.wikipedia.org/wiki/Resistive_touchscreen
[18]:http://www.lcdwiki.com/3.5inch_HDMI_Display-B
[19]:http://www.lcdwiki.com/res/MPI3501/MPI3501-3.5inch-RPi-Display-User-Manual-V1.0.pdf
[20]:https://usa.banggood.com/MPI3508-3_5-inch-USB-Touch-Screen-Real-HD-1920x1080-LCD-Display-For-Raspberry-Pi-3-or-2-or-B+-or-B-or-A+-p-1216963.html
[21]:https://www.aliexpress.us/item/3256804172295020.html?spm=a2g0o.order_list.order_list_main.11.66c81802hHpPTF
[22]:https://www.aliexpress.us/item/3256805050940054.html?gatewayAdapt=glo2usa4itemAdapt
[23]:
[24]:
[25]:
[26]:
[27]:
[28]:
[29]:
[30]:https://www.linux-magazine.com/Online/Features/Using-ARP-for-Network-Recon
[31]:https://shownotes.opensourceisawesome.com/netdiscover/
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




