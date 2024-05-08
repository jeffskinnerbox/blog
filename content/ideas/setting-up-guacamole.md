<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----


* [How to use Apache Guacamole to create a VNC Connection](https://www.howtoforge.com/how-to-use-apache-guacamole-to-create-a-vnc-connection/)
* [Apache Guacamole Manual](https://guacamole.apache.org/doc/gug/)





Try install Guacamole via Docker ...
* [Installing Apache Guacamole through Docker](https://www.linode.com/docs/guides/installing-apache-guacamole-through-docker/)
* [Using a Cloud Desktop on a Browser with Apache Guacamole](https://www.linode.com/docs/guides/remote-cloud-desktop-using-apache-guacamole/)
* [Set Up Apache Guacamole Remote Desktop on Ubuntu 22.04/20.04 Server](https://www.linuxbabe.com/ubuntu/apache-guacamole-remote-desktop-ubuntu-20-04)

About VNC...
* [An Overview of VNC (Virtual Network Computing)](https://www.linode.com/docs/guides/what-is-virtual-network-computing/)

Try following this for VNC ...
* [Install VNC on Ubuntu 20.04](https://www.linode.com/docs/guides/install-vnc-on-ubuntu-20-04/)
* [How to Install TightVNC to Access Remote Desktops in Linux](https://www.tecmint.com/install-tightvnc-access-remote-desktop-in-linux/)
* [How to connect to a remote computer using VNC in Linux](https://www.redhat.com/sysadmin/vnc-screen-sharing-linux)
* [How To Access Your PCs and Servers from Anywhere Using Guacamole and CloudFlare Tunnels](https://www.youtube.com/watch?v=tg1CbMEzCsc)

for Raspberry Pi ....
* [Raspberry Pi Now Has an Official Remote Desktop Client](https://www.howtogeek.com/raspberry-pi-connect-remote-access-desktop/)
* [Raspberry Pi Solves Remote Headless Connection Headaches with the Browser-Based Raspberry Pi Connect](https://www.hackster.io/news/raspberry-pi-solves-remote-headless-connection-headaches-with-the-browser-based-raspberry-pi-connect-d65ca044f423)







VNC will usually run at :1 which is a different session. To run at :0, use x11vnc. Display :0 is your currently running GUI session.

Check out [x11vnc](https://github.com/LibVNC/x11vnc) if you want connect to a real X11 display (i.e. one attached to a physical monitor, keyboard, and mouse: a Workstation or a SunRay session) from far away. Maybe you want to close down an application cleanly rather than using kill, or want to work a bit in an already running application, or would like to help a distant colleague solve a problem with their desktop, or would just like to work out on the deck for a while. This is where x11vnc is useful.
* [How to Setup x11vnc on Ubuntu 22.04](https://linuxopsys.com/topics/setup-x11vnc-on-ubuntu)

Check out your document -  /home/jeff/blogging/content/articles/howto-using-xephyr-to-create-a-new-display-in-a-window.md

# Guacamole vs AnyDesk
AnyDesk is a popular remote desktop software for Linux, Windows, BSD, macOS, and mobile platforms.
With this tool, you can remotely access other computers using AnyDesk
(you must provide a password for a secure connection)
or let someone else remotely access your system
(you have to accept the incoming connection).

* [AnyDesk](https://anydesk.com/en)
* [Install AnyDesk on Ubuntu Linux (GUI and Terminal Methods)](https://itsfoss.com/install-anydesk-ubuntu/)
* [10 Best Remote Desktop Software Tools for Linux Users ](https://www.cendio.com/blog/10-best-remote-desktop-software-tools-for-linux-users)








# Guacamole
[Guacamole][01] is a free & open source application
that allows you to access your computers from anywhere.
It can be put behind a proxy server which allows you to access your servers from anywhere in the world.
Spcifically, Guacamole is an HTML5 remote access gateway
(aka remote desktop web client letting users access their desktop infrastructure through a HTML5 web browser).
This is made possible using Windows Remote Desktop (RDP), VNC, Telnet, SSH, SFTP, or Kubernetes protocols,
just using a modern web browser (aka HTML5 web browser) and without the need for any client apps.
As long as you have access to a HTML5 web browser, you have access to your machines.
Desktops accessed need not physically exist and your desktop operating system can be hosted in the cloud.

Guacamole is built on its own stack of thoroughly [documented core APIs][02],
including basic tutorials and conceptual overviews in the [online manual][03].
These APIs allow Guacamole to be tightly integrated into other applications,
whether they be open source or proprietary.

* Install & Configure Guacamole
    * [Apache Guacamole][01]
    * [access EVERYTHING from your web browser!! (Linux and Windows Desktop, SSH) // Guacamole Install](https://www.youtube.com/watch?v=gsvS2M5knOw)
    * [Meet Guacamole, Your Remote Access Gateway](https://www.youtube.com/watch?v=LWdxhZyHT_8)
    * [Pi-Hosted : Manually Installing Guacamole on Portainer Part 3](https://www.youtube.com/watch?v=cKAhnf8X1lo&list=PL846hFPMqg3jwkxcScD1xw2bKXrJVvarc&index=3)
    * [How To Access Your PCs and Servers from Anywhere Using Guacamole and CloudFlare Tunnels](https://www.youtube.com/watch?v=tg1CbMEzCsc)
    * [Remote Access to ANY server - Guacamole WebApp Tutorial](https://www.youtube.com/watch?v=Sq-irDBauvo)
    * [access EVERYTHING from your web browser!! (Linux and Windows Desktop, SSH) // Guacamole Install](https://www.youtube.com/watch?v=gsvS2M5knOw&t=1447s)
    * [Guacamole Remote Desktop - Open Source, Self Hosted remote access to your machines in the browser!](https://www.youtube.com/watch?v=DGw6P5Lkj-U)
* CloudFlare Tunnels
    * [Remote Access: Getting Started with CloudFlare Tunnels (Domains, DNS, Tunnels)](https://www.youtube.com/watch?v=Q5dG8g4-Sx0)
    * [Using Cloudflare Tunnels For Hosting & Certificates Without Exposing Ports On Your Firewall](https://www.youtube.com/watch?v=eojWaJQvqiw&t=5s)
    * [Cloudflare Tunnel](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/)

# How To Remove Docker Images, Containers, and Volumes
* [How To Remove Docker Images, Containers, and Volumes](https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes)
* [The Docker Ecosystem: An Introduction to Common Components](https://www.digitalocean.com/community/tutorials/the-docker-ecosystem-an-introduction-to-common-components)

Docker provides a single command that will clean up any resources — images, containers, volumes, and networks — that are dangling (not tagged or associated with a container):

sudo docker system prune

To additionally remove any stopped containers and all unused images (not just dangling images), add the -a flag to the command:

sudo docker system prune -a

# Remove dangling volumes
Since the point of volumes is to exist independent from containers, when a container is removed, a volume is not automatically removed at the same time. When a volume exists and is no longer connected to any containers, it’s called a dangling volume. To locate them to confirm you want to remove them, you can use the docker volume ls command with a filter to limit the results to dangling volumes. When you’re satisfied with the list, you can remove them all with docker volume prune:

List:

sudo docker volume ls -f dangling=true

Remove:

sudo docker volume prune

# Remove a container and its volume
If you created an unnamed volume, it can be deleted at the same time as the container with the -v flag. Note that this only works with unnamed volumes. When the container is successfully removed, its ID is displayed. Note that no reference is made to the removal of the volume. If it is unnamed, it is silently removed from the system. If it is named, it silently stays present.

Remove:

sudo docker rm -v container_name



-----



#### Step 1: Install Guacamole & Start - DONE
I'm getting my Docker container for Guacamole from the DockerHub repository [abesnier/guacamole][09].
It is a self-contained Guacamole Docker container using the latest
[tomcat][05], [postgresql][06], [s6overlay][07], and, [guacamole][01].

You can launch Guacamole via `docker-compose`, `docker`, or within Portainer.
The Docker Compose file (called `guacamole-docker-compose.yml` in this git hub repository) is:

```yaml
version: "3"
services:
  guacamole:
    container_name: guacamole
    image: abesnier/guacamole:latest
    restart: unless-stopped
    ports:
      - 8194:8080
    volumes:
      - postgres:/config
volumes:
  postgres:
    driver: local
```

This Guacamole service can be loaded & started with the following:

```bash
# load via the docker-compose file
sudo docker-compose --file ./guacamole-docker-compose.yml up -d

# alternatively, you could load it via docker
sudo docker run -p 8194:8080 -v postgres:/config --name="guacamole" --restart=always abesnier/guacamole:latest
```

My preferred alternative is to deploy applications with Portainer Stacks.
A stack is a collection of one or more containers that collectively provide a complete application.
Maintaining applications updates via Stacks is simple
because you have the `docker-compose` file within Portainer.

To use Stacks, do the following:

* Enter Portainer and navigate to my `firewall-router` instance of Portainer.
* Select **Stacks** > **Add stack** > **Web editor**
* name the stack via **Name** "guacamole".
* Paste the above YAML script into the **Web editor**.
* Scroll down to the bottom and click the **Deploy the stack** button.

See ["How to Manage Docker Containers with Portainer"][04] for more information.

>**NOTE:** If Guacamole has already been installed before,
>you may need to remove the old image within the
>**Images**, **Networks**, and **Volumes**.

At this point, you could login to Guacamole and begin to configure it
via `google-chrome 192.168.1.204:8194`
(default username is `guacadmin` with password `guacadmin`)
but we will first configure Cloudflare.

#### Step 2 - Configure Cloudflare to Support Guacamole - DONE
I'm using [Cloudflare as my DNS server][10] and [Cloudflare Tunnels][11] for incresed protection of my LAN.
To configure Cloudflare to support my home LAN envirnment,
[login to Cloudflare][12],
and via the left-hand menu,
select **Zero Trust** > **Access** > **Tunnels**.

Now select **Create a tunnel** and give the tunnel a name of "guacamole",
and select **Save tunnel**.
You'll get a new token that needs to be give to Portainer's container for
Cloudflare daemon (call `cloudflare-daemon`)
and paste it into the container.

Select **Next** on Cloudflare and you need to create a subdomain for the Guacamole application.
I entered "guac" for **Subdomain**, "jeffskinnerbox.me" for **Domain**, "HTTP" for **Type**,
and "192.168.1.204:8194" for **URL**.
Now select **Save guacamole tunnel** at the bottom of the page.

Now go to Portainer and from the left-hand menu, select **Containers** > **cloudflare-daemon**.
Select near the top, **Duplicate/Edit**
Scroll down to **Command** and paste in the token and then select **Deploy the container**.
The container should be restarted with the new token.

#### Step 3: Create New Guacamole Admin login - DONE
We are now done with Cloudflare and time to move back to Guacamole.

Make sure to remove the default username and password and create a new one.
To do this, goto the menu in the top-right corner and select **Settings** >
**Users** > **New User**.

Now add you information and time zone.
Most important is to make sure to give yourself **ALL** the privileges in **Permissions** section
so your are not locked out.

Now logout and then log back in, using the new account you created.
Goto the top right-hand menu and select **Settings** > **Users** > **New User**
and select the `guacadmin` account and disable it.
Now do all your administrative work for Guacamole via this new login.

#### Step 4: Guacamole Two Factor Authentication (2FA) via Cloudflare Tunnels - DONE
Guacamole, as currently implemented above,
provides no secuirty protection other than login/password.
Given that I plan to used Guacamole outside my home LAN, this isn't very safe.
Guacamole does provide extentions to support Two Factor Authentication (2FA)
but I prefer to use Cloudflare's Access controls.
This [video][08] provide a good tutoral on using Cloudflare Access to protect your Guacamole remote gatway.

#### Step 5: Create a Guacamole Connection
Goto the top right-hand menu and select **Settings** > **Connections**.
Click the button **New Connections**.
Enter the following information
(**NOTE:** many of the fields will be defaulted and left blank):

|       Server Name           | Protocol |     Hostname    |  Port  | User | Password |      Notes      |
|:---------------------------:|:--------:|:---------------:|:------:|:----:|:--------:|:---------------:|
| desktop (jeff via shell)    |   SSH    |  192.168.1.200  |   22   | xxxx | xxxxxxxx |                 |
| pve-1 (root via shell)      |   SSH    |  192.168.1.204  |   22   | xxxx | xxxxxxxx |                 |
| desktop (jeff via VNC)      |   VNC    |  192.168.1.200  |  5900  | xxxx | xxxxxxxx |                 |
| chromebook (jeff via VNC)   |   VNC    |  192.168.1.19   |  5900  | xxxx | xxxxxxxx | not a static IP |

Now go back to menu at the top right and select **Home**.
Select you connection and you should be logged in,
**except for the VNC connection**.
In this case, the VNC client must be running on the target machine
and we'll install that next.


------


-----


-----



# Install Virtual Network Computing (VNC)
I want to remote desktop into Linux so I can take full advantage of the the desktop GUI menu system.
There are in fact [many remote desktop software packages][32] available to choose from,
but only small number seem to have any following in the Linux world,
and VNC is the de-facto remote desktop protocol for Linux.
[Virtual Network Computing (VNC)][39] uses the RFB (“remote framebuffer”) open protocol.
Because it works at the [framebuffer][32] level, it is applicable to all windowing systems and applications,
including Microsoft Windows, MacOS, and the X Window System.
VNC can be quite a lifesaver for many who are not comfortable working
from the command-line and need to manage files,
install software, and configure settings on a remote server.

Linux X Window System has its own remote desktop tool, [Xephyr][33],
which allows you to nest X server within a X server (aka "X Nesting").
Cleaver but insecure, little used, an only available on X Window systems
(my experimentation with Xephyr can be found [here][34]).
There are other posibilities for accessing desktops remotely,
such as the [Remote Desktop Protocol (RDP)][42].
This is a proprietary protocol developed by Microsoft,
which provides a user with a graphical interface to
connect to another computer over a network connection.

Because of its popularity, VNC seems like the right choose of protocol.
The [VNC client/server model][38]
moves the whole video frame from the server to the VNCViewer on the client,
which give you a true representation of the remote desktop.
Contrast this with a popular alternative to VNC, that being Windows Remote Desktop (WRD).
WRD does not transport frames, thereby reducing the bandwidth requirements (good),
but instead must create its own separate user session / rendering of the GUI experience (not so good).

There are [multiple instance of VNC implementation][37].
[RealVNC][35] appears to be [supported by Raspberry Pi Raspian OS][36],
on the other hand, [x11vnc][44] seems well tuned for X Windows,
and [TightVNC][39] comes installed within many Linux full distribution package.
But what is the [best VNC][40] ... could it be a useless question?
Just to keep it simple but functional,
I choose to [install TigerVNC on my Ubuntu][41] system.
(See how TigerVNC compare to others [here][30] and [here][31].)

In my user scenario for VNC,
my Ubuntu desktop will be running the VNC client so it can run the remote Linux desktop in one of its window.
Therefore, my remote Linux will be configured as a VNC server.
We need to make sure VNCserver software is installed already on remote and configured as needed.

In this installation, I'm using Ubuntu 22.04 with the Gnome graphical desktop environment
and the TigerVNC package, both available from the official Ubuntu repository.
The
I followed mainly the first source below:

Sources:
* VNC vs RDP
    * [VNC vs RDP: which remote desktop tool is the best?](https://www.realvnc.com/en/blog/vnc-vs-rdp-which-remote-desktop-tool-is-best/)
    * [VNC vs RDP: Similarities and Differences](https://www.parallels.com/blogs/ras/vnc-vs-rdp/)
* TigerVNC
    * [How to Install and Configure VNC on Ubuntu 22.04][14]
    * [Install VNC Server with Gnome display on Ubuntu 18.04](https://www.teknotut.com/install-vnc-server-with-gnome-display-on-ubuntu-18-04/)
    * [How to install and configure VNC on Ubuntu](https://linuxhint.com/install-configure-vnc-ubuntu/)
    * [How To Install VNC Server on Ubuntu 22.04 LTS](https://idroot.us/install-vnc-server-ubuntu-22-04/)
* TightVNC
    * [How to Install & Configure VNC Server on Ubuntu 22.04|20.04](https://bytexd.com/how-to-install-configure-vnc-server-on-ubuntu/)
    * [How to Install and Configure VNC on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04)
    * [Install and Configure VNC server on Ubuntu 22.04](https://itnixpro.com/install-and-configure-vnc-server-on-ubuntu-22-04/)
    * [Install and Configure VNC Server on Ubuntu 22.04|20.04|18.04](https://computingforgeeks.com/how-to-install-vnc-server-on-ubuntu/)

#### Step 0: Remove VNC From Your System - DONE
During my installation of VNC,
I ran into problems, particularly with TigerVNC,
and I had  to do some remove & re-install operations.
If you run into similar challenges do the following.

To remove the VNC packages and other installation steps:

```bash
# remove both tight & tiger vnc from your linux box
sudo apt remove tigervnc-standalone-server tigervnc-xorg-extension tigervnc-viewer
sudo apt remove tightvncserver xtightvncviewer
```

Remove any startup, configuration and log files under your user account:

```bash
# remove user startup file
rm -r -f ${HOME}/.vnc
```

To remove any additional `systemd` vnc file you have made:

```bash
# check what systemd vnc files have been added
$ ls /etc/systemd/system | grep vnc
vncserver@1.service
vncserver@.service

# remove the systemd vnc files
sudo rm -r /etc/systemd/system/vncserver\@.service /etc/systemd/system/vncserver\@1.service

# reload the systemd process so that it no longer attempts to reference these files
sudo systemctl daemon-reload
```

#### Step 1: Check What is Already Install - DONE
There are couple ways to [detect whether your Linux system has GUI installed][13].
These method will not, however, help to identify if GUI is running or not.

```bash
# there is any X session installed
$ ls /usr/bin/*session
/usr/bin/dbus-run-session*  /usr/bin/gnome-session-custom-session*
/usr/bin/gnome-session*     /usr/bin/pipewire-media-session*

# check if gnome desktop window manager is working
sudo systemctl status gdm

# check if vnc packages are installed
$ apt list --installed | grep -i vnc
libgtk-vnc-2.0-0/jammy-updates,now 1.3.0-1ubuntu1 amd64 [installed,automatic]
libgvnc-1.0-0/jammy-updates,now 1.3.0-1ubuntu1 amd64 [installed,automatic]
libvncclient1/jammy,now 0.9.13+dfsg-3build2 amd64 [installed,automatic]
libvncserver1/jammy,now 0.9.13+dfsg-3build2 amd64 [installed,automatic]
remmina-plugin-vnc/jammy,now 1.4.25+dfsg-1 amd64 [installed,automatic]

# check if vnc server executable installed
ls /usr/bin/vncserver

# check if vnc start up files are installed
ls ~/.vnc
```

From the above output, my Ubuntu has the GNOME Desktop Environment installed and operational.
The VNC server package appears to be loaded but not installed and not executable.

#### Step 2: Install VNC on Ubuntu - DONE
So I need to install the TigerVNC VNC client on Ubuntu,
but for completeness, I'll do both the client and server:

```bash
# make sure your package manager is up to date
sudo apt update
sudo apt upgrade -y

# install gnome desktop and start its services
sudo apt install ubuntu-gnome-desktop
sudo systemctl start gdm

# install tigervnc on ubuntu
#sudo apt install xserver-xorg-core
#sudo apt install tigervnc-standalone-server tigervnc-xorg-extension tigervnc-viewer

# install tightvnc on ubuntu
sudo apt install tightvncserver xtightvncviewer

# install this because may be needed by the ~/.vnc/xstartup file
sudo apt install dbus-x11
```

Now execute the command `vncserver` to initialize the VNC server instance and set up a password.
This operation will also start the VNC service so we can test it.
Assuming you are acting as a non-root sudo user, do **NOT** execute this command with `sudo`.

```bash
# set the vnc password used when connecting to vnc server
$ vncserver

You will require a password to access your desktops.

Password:
Verify:
Would you like to enter a view-only password (y/n)? n
A view-only password is not used

Warning: desktop:1 is taken because of /tmp/.X1-lock
Remove this file if there is no X server desktop:1

New 'X' desktop is desktop:2

Creating default startup script /home/jeff/.vnc/xstartup
Starting applications specified in /home/jeff/.vnc/xstartup
Log file is /home/jeff/.vnc/desktop:2.log
```

If you ever want to change your password or add a view-only password,
you can do so with the `vncpasswd` command.

The process above creates the necessary default configuration files
and connection information for the VNC server.
Additionally, it launches a default server instance on port 5902.
This port is called a display port, and is referred to by VNC as :2.
VNC can launch multiple instances on other display ports,
with :2 referring to port 5902, :3 referring to 5903, and so on.
You'll notice that display port :1 is locked,
since I'm operating with dual monitors in my desktop's X Windows environment.

>**NOTE:** You'll be prompted to enter a password, and also a view-only password.
>Users who log in with the view-only password will not be able to
>control the VNC instance with their mouse or keyboard
>(Useful if you want to just demonstrate something to other people using your VNC server).

Now make sure to terminate the VNC server before moving to the next step.

```bash
# terminate any active vnc server sessions
vncserver -kill :*
```

#### Step X: Preliminary Testing of VNC
Let's do some testing of the VNC tools that have been installed to make sure
they are working and to understand how they operate.

Basic X Windows stuff ...
xclock -display :0 & ... works fine
xclock -display :1 & ... works fine but shows up on the same monitor
xclock -display :2 & ... fails since there is no :2 display

Execute `lsl /tmp/.X*-lock` to see what displays have been created

#####
After you have installed a VNC Viewer, you should test that you can connect to your  on your local network. You should do this before setting up the tunnel for remote access, to check that everything is installed correctly.

vncserver :2 -geometry 800x600 -depth 24
vncserver :2 -localhost -geometry 800x600 -depth 24

vncviewer 192.168.1.200::5902
vncviewer 192.168.1.200:2
vncviewer desktop:2

#####
Applications > Accessories > Connections

#####
$ vncserver -geometry 800x600 -depth 24 :1
Warning: desktop:1 is taken because of /tmp/.X1-lock
Remove this file if there is no X server desktop:1

check the locks with `ls -l /tmp/.X*-lock`

**This appears to work...**
    vncserver -geometry 960x540 -depth 24 :2
    vncviewer localhost:2
    vncviewer -passwd /home/jeff/.vnc/passwd localhost:2
    xclock -update 1 -hands red -display :2

**How To Start VNC Session With Gnome Desktop?**
* https://askubuntu.com/questions/1285420/how-to-properly-configure-xstartup-file-for-tightvnc-with-ubuntu-20-04-lts-gnome
* https://askubuntu.com/questions/1311713/can-anyone-help-me-with-my-tigervnc-xstartup-script-for-ubuntu-18-04s-gnome-doc
* https://askubuntu.com/questions/1318351/tigervnc-config-with-ubuntu-20-04-black-screen
* https://askubuntu.com/questions/1278053/ubuntu-20-04-gray-screen-on-vnc
* https://www.how2shout.com/linux/install-vnc-server-on-ubuntu-20-04-18-04-lts-to-access-gnome/
* https://askubuntu.com/questions/694795/how-to-start-vnc-session-with-gnome-desktop

What is the $DISPLAY environment variable? - https://askubuntu.com/questions/432255/what-is-the-display-environment-variable
Is that normal that $DISPLAY environment variable value is 1? - https://stackoverflow.com/questions/71321131/is-that-normal-that-display-environment-variable-value-is-1
Why is $DISPLAY sometimes :0 and sometimes :1 - https://stackoverflow.com/questions/14394974/why-is-display-sometimes-0-and-sometimes-1

#### Step X: Setting Up a Firewall - ???
Applications can register their profiles with UFW upon installation.
These profiles allow UFW to manage these applications by name.
Lets see if TigerVNC registered with UFW:

Add comments to the firewall rules so that you know why the ports are set open:
[How do you add comments on UFW firewall rule?](https://www.cyberciti.biz/faq/howto-adding-comments-to-ufw-firewall-rule/)

```bash
# examine the list of installed ufw profiles
$ sudo ufw app list
Available applications:
  Apache
  Apache Full
  Apache Secure
  CUPS
  OpenSSH
```

So we can see that TigerVNC did **not** register.
and therefore, needed ports are likely closed.
Next, let's open the required ports.

```bash
# what is the status of the firewall
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
Apache                     ALLOW       Anywhere
52050                      ALLOW       Anywhere
52051                      ALLOW       Anywhere
3232/tcp                   ALLOW       Anywhere
22/tcp                     ALLOW       Anywhere
Apache (v6)                ALLOW       Anywhere (v6)
52050 (v6)                 ALLOW       Anywhere (v6)
52051 (v6)                 ALLOW       Anywhere (v6)
3232/tcp (v6)              ALLOW       Anywhere (v6)
22/tcp (v6)                ALLOW       Anywhere (v6)

# open only two port for vncserver - ports 5900 & 5901
sudo ufw allow 5900 8901
```

#### Step X: Edit VNC Startup Script Settings - DONE
The VNC server can be told what commands to perform when it starts up
I want to configure VNC to launch the full desktop environment when it starts.
These commands are located in a configuration file `~/.vnc/xstartup`,
sometimes called the "vncserver script".
Make a backup of the `xstartup` file (assuming one is created),
and then make modifications so it looks like this when finished:

```bash
#!/bin/sh

# This is a startup script that will be executed when the VNC Server is activated

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources

vncconfig -iconic &
dbus-launch --exit-with-session gnome-session &
```

The `xstartup` file needs to be executable,
so lets update its mode:

```bash
# make the xstartup file executable
sudo chmod +x ~/.vnc/xstartup
```

The first command say to execute a system-wide `xstratup` file, if one exists.
The second command in the file, `xrdb $HOME/.Xresources`,
tells VNC's GUI framework to read the server user's `.Xresources` file.
`.Xresources` is where a user can make changes to certain settings of the
graphical desktop, like terminal colors, cursor themes, and font rendering.

When VNC is first set up, it launches a default server instance on port 5901.
This port is called a display port, and is referred to by VNC as `:1`.
VNC can launch multiple instances on other display ports, like `:2`, `:3`, etc.
When working with VNC servers, remember that `:X` is a display port that refers to port 5900+X.

#### Step X: Test the VNC Server & Client
To run the VNC Server, you can use the following command:

```bash
# open the ports required of the vnc server

# start the vnc server
vncserver -localhost no -geometry 800x600 -depth 24

# start the vnc client and attach to the vnc server
vncviewer localhost:5901
```

The above option will create a session that allows connections from outside
with 800×600 pixel resolution and sharpness 24.
You can configure the resolution and sharpness according to your taste.

>**NOTE:** My first execution of the `vncserver`command above appeared to fail
>or had permissions problems.
>It also spit out a lengthy description of its problems with me executing it.
>I ran it again, it was silent and appeared OK.

#### Step X: Create VNC Start/Stop Script
In an effort to make the use of VNC easy,
we will create a script to start/stop the VNC server service.
Also, with this script, we can make auto-start VNC servers when the computer is turned on.
To do this, we create a file with the name `/etc/systemd/system/vncserver@.service`.
Make the modifications below so it looks like this when finished
(this code taken from ["How to Install and Configure VNC on Ubuntu 22.04"][14]):

```
[Unit]
Description=VNC Server (TigerVNC) at startup
After=syslog.target network.target

[Service]
Type=forking
User=jeff
Group=jeff
WorkingDirectory=/home/jeff

## clean any existing files in /tmp/.X11-unix environment
#ExecStartPre=/usr/bin/vncserver -kill :%i > /dev/null 2>&1 || :
#ExecStart=/usr/bin/vncserver -geometry 800x600 -depth 24 -localhost no :%i
#ExecStop=/usr/bin/vncserver -kill :%i

# clean any existing files in /tmp/.X11-unix environment
PIDFile=/home/jeff/.vnc/%H:%i.pid
ExecStartPre=-/usr/bin/vncserver -kill :%i > /dev/null 2>&1
ExecStart=/usr/bin/vncserver -depth 24 -geometry 1280x800 -localhost :%i
ExecStop=/usr/bin/vncserver -kill :%i

[Install]
WantedBy=multi-user.target
```

* [TigerVNC server not working within systemctl but works fine separately](https://superuser.com/questions/1717705/tigervnc-server-not-working-within-systemctl-but-works-fine-separately)

>**NOTE:** In the "User=" & "Group=" & "WorkingDirectory=" rows,
>make sure the user matches the user you are using.
>Change 'jeff' to what ever your user/group name is.

Now to make sure we are in a quite state killing any active sessions.
Then enable the `startup` file and auto-start VNC via the commands below.
See ["How To Use Systemctl to Manage Systemd Services and Units"][43]
for more information about the `systemctl` commands below.

```bash
# terminate any active vnc server sessions
vncserver -kill :*

# make the system aware of the new file
sudo systemctl daemon-reload

# create the vnc server service
$ sudo systemctl enable vncserver@1
Created symlink /etc/systemd/system/multi-user.target.wants/vncserver@1.service → /etc/systemd/system/vncserver@.service

# start vnc as a linux service
sudo systemctl start vncserver@1

# check the status of the vnc server service
sudo systemctl status vncserver@1

# display the unit file that systemd has loaded into its system
sudo systemctl cat vncserver@1
````

To remove any additional `systemd` vnc file you have made:

```bash
# check what systemd vnc files have been added
$ ls /etc/systemd/system | grep vnc
vncserver@1.service
vncserver@.service

# remove the systemd vnc files
sudo rm -r /etc/systemd/system/vncserver\@.service /etc/systemd/system/vncserver\@1.service

# reload the systemd process so that it no longer attempts to reference these files
sudo systemctl daemon-reload
```


-------


# VNC Security
* [Over 9,000 VNC servers exposed online without a passwor](https://www.bleepingcomputer.com/news/security/over-9-000-vnc-servers-exposed-online-without-a-password)


----



[01]:https://guacamole.apache.org/
[02]:https://guacamole.apache.org/api-documentation/
[03]:https://guacamole.apache.org/doc/gug/
[04]:https://sweetcode.io/how-to-manage-docker-containers-with-portainer/
[05]:https://tomcat.apache.org/
[06]:https://www.postgresql.org/
[07]:https://github.com/just-containers/s6-overlay
[08]:https://www.youtube.com/watch?v=DGw6P5Lkj-U&t=2060s
[09]:https://hub.docker.com/r/abesnier/guacamole
[10]:https://www.cloudflare.com/dns/
[11]:https://www.cloudflare.com/products/tunnel/
[12]:https://dash.cloudflare.com/login
[13]:https://ostechnix.com/how-to-check-if-gui-is-installed-in-linux-from-commandline/
[14]:https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04
[15]:
[16]:
[17]:
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
[30]:https://www.lifewire.com/vnc-free-software-downloads-818116
[31]:https://fixthephoto.com/best-vnc-software.html
[32]:https://en.wikipedia.org/wiki/Framebuffer
[33]:https://nims11.wordpress.com/2012/06/24/nested-x-servers-with-xephyr/
[34]:http://jeffskinnerbox.me/posts/2014/Apr/29/howto-using-xephyr-to-create-a-new-display-in-a-window/
[35]:https://www.realvnc.com/en/
[36]:https://www.raspberrypi.org/documentation/remote-access/vnc/
[37]:https://www.lifewire.com/vnc-free-software-downloads-818116
[38]:https://www.lifewire.com/vnc-virtual-network-computing-818104
[39]:https://www.tightvnc.com/
[40]:https://www.techradar.com/news/5-of-the-best-linux-remote-desktop-clients
[41]:https://tigervnc.org/
[42]:https://en.wikipedia.org/wiki/Remote_Desktop_Protocol
[43]:https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units
[44]:http://www.karlrunge.com/x11vnc/
[45]:
[46]:
[47]:

