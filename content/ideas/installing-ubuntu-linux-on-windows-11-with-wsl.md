<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
        title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------


Linux can be used on a MS Windows computer in several ways.
It can be done via virtual machine (VM) software such as VirtualBox or VMware,
or set up a dual-boot configuration,or via the [Windows Subsystem for Linux (WSL)][01]
which allows users to run Linux directly on a Windows provided virtual environment.
Some of the advantage of WSL is its integration with the MS Windows file system,
which allows users can easily share files and data between MS Windows
and Linux environments (i.e. [X Window System][04]).
With Windows 11, it supports graphical user interfaces (GUIs)
Linux X Window applications.
Also with Windows 11, there is included a built-in package manager that allows
users to easily install and manage Linux distributions within WSL. 

[Graphical Windows Subsystem for Linux (GWSL)][02] is Microsoft's Windows 10/11 [X Server][05] fully integrated with the WSL.
There are several alternative X Servers for Windows 10/11 but GWSL is free and has MS Windows support.
GWSL automates the process of running [X Window System Protocol][05] on top of WSL and over SSH.
GWSL makes it even easier to render apps from Linux without a desktop environment.
Basically, it does a lot of stuff you expect of an X Server but makes it easier!

* It lets you easily run graphical Linux apps on Windows 10/11.
* It lets you run graphical apps located on remote Linux machines.
* It provides a simple UI for launching Linux apps, managing them graphical, and creating customized Windows shortcuts for them.
* All this at the click of a button! No memorization of commands necessary. Easy!

>**NOTE:** The procedure documented below was tested on a [GMKtec Mini PC N97][08] for this project.
>This little box has the 12th Gen Intel Alder Lake N97 CPU (clocked up to 3.60GHz),
>12GB DDR5 memory, a 256GB Hard Drive, and comes pre-installed with Microsoft Windows 11 Pro.


---------------


# Install Windows Subsystem for Linux (WSL)
Before installing WSL2, make sure we have the latest update for your Windows 11 PC.
Once WSL is installed, we will install Ubuntu Linux 24.04 within WSL.
Ubuntu Linux 24.04 is need by [ROS2 Jazzy Jalisco][07]. 

Sources:
* [Install Windows Subsystem for Linux (WSL)](https://www.youtube.com/watch?v=gTf32sX9ci0)
* [Run Linux on Windows Like a Boss (WSL)][06]
* [How to Install Windows Subsystem for Linux 2 (WSL 2) on Windows 11!](https://www.youtube.com/watch?v=8BTX9mwLcfw)

#### Step 1: Check Virtualisation is Enabled - DONE
Make sure Virtualisation is enabled by going to
**Task Manager** > **Performance** and then check that **Virtualisation** is **Enabled**
([If not enable][06], you need to turn it on via the BIOS).

#### Step 2: Enable Windows Virtualisation Features - DONE
To install WSL (Windows Subsystem for Linux) on Windows 11,
you'll need to enable the necessary Windows features
and then install a Linux distribution from the Microsoft Store.

* Go to the Start Menu and search for "Turn Windows Feature On or Off"
* Select "Virtual Machine Platform" and "Windows Subsystem for Linux". Then click OK.
* Reboot your PC and then go to Search and enter "Command Prompt"

#### Step 3: Load Windows Subsystem for Linux (WSL) - DONE
Now do the following in **Command Prompt**:

```bash 
# see if wsl is Pre-installed
wsl

# install wsl 
wsl --update

# install ubuntu 24.04 linux distribution
wsl --install -d Ubuntu-24.04

# do an update of your repositories and upgrade all your applications
sudo apt update
sudo apt upgrade
```

#### Step 4: Start Ubuntu Terminal via PowerShell Window - DONE 
Now lets validate things are working.
At this point, you should be able to open a PowerShell terminal
and open a terminal for the Ubuntu instance running within WSL.
You can do this via a clicking the pull down menu next to the "+" tab.
Do this, and you should get a new tab with a "Ubuntu colored" terminal.


---------------


# Install Graphical Windows Subsystem for Linux (GWSL)
To run graphical Linux apps, you need to enable WSL
and then install the [GWSL][09] functionality. 
Since we are using Ubuntu provided by Microsoft,
GWSL will be provided in the X Window System packages when installed.

GWSL is needed for Linux graphics application but
is **not** something you need to install separately when you use Microsoft provided Linux distributions.
Never the less, you should perform a test to make sure its working.

#### Step 1: Test Ubuntu Graphical Apps - DONE
The X11 windowing system has a miscellaneous collection of apps & tools that ship with it,
such as the `xclock`, `xcalc`, `xclipboard` for cut & paste, `xev` for event testing, etc.
Let install them and launch an app to validate that WSL's Ubuntu can in fact supports graphical applications:

```bash 
# install some graphics apps 
sudo apt install x11-apps

# test some graphical applications
xeyes &
```

You should see a small window pop-up on the PC screen,
with two eyes in the window,
that will follow your mouse pointer around the screen.

Sources:
* [Run Linux GUI apps on the Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps)
* [WSL: Run Linux GUI Apps](https://www.youtube.com/watch?v=kC3eWRPzeWw)


---------------


# Install Some Networking Tools
When WSL is install,
the installation process make sure WSL can communicate with the Internet
but no provisioning is done to assure it can talk to any device on your home network.
This is good for security but this will prevent us from using it as planned,
(That is, as a ROS2 node communicating with other ROS2 nodes on the home network.) 

#### Step 1: Install OpenSSH - DONE
We'll need SSH to test the working of WSL mirrored networking that we be established later.
Let's install SSH:

```bash
# update the systems repositories
sudo apt update
sudo apt upgrade

# install openssh server
sudo apt install ssh

# enable ssh services to start on boot
sudo systemctl enable ssh

# verify ssh service status
sudo systemctl status ssh

# configure firewall
sudo apt install ufw
sudo ufw allow ssh
sudo ufw enable
```

#### Step 2: Install Some Basic Networking Tools - DONE
We'll need to identify what network interface and IP address WSL is using.
To do this, we need to install some basic Linux networking tools:

```bash 
# install networking tools
sudo apt install net-tools network-manager netdiscover
```

Here are some helpful commands that can be used to
validate / troubleshot the procedure below, if needed:

```bash 
# list all the network interfaces (aka adapters) used by wsl ubuntu
ifconfig 
# or 
nmcli

# list all ip address' used by wsl ubuntu
ip address
# or 
nmcli device show

# finding IPs and identifying devices on your network
sudo netdiscover -c 3 -s 10 -L -N -r 192.168.1.0/24
```

#### Step 3: Query the WSL Network Configure - DONE
You can find the IP address of the Ubuntu within WSL by executing within Ubuntu `ip address | grep eth0`.
So its the IP address associated with the network interface adapter `eth0`.
In my case, that IP address is `172.27.218.249/20`.

This is **different** than the Windows PC IP address,
which you can get via the PowerShell terminal using the command `ipconfig`. 
In my case, that IP address is `192.168.1.155`.

You should be able to `ping` your WSL Ubuntu from Windows PowerShell terminal via `ping 172.27.218.249`
but you cannot `ping` the WSL Ubuntu from your Windows PC or another computer on your LAN.
In effect, MS Windows is protecting you WSL Ubuntu from anything touching it
(other than Internet request originating from Ubuntu)!
We need to remove this protection scheme, at least for your home network.

Sources:
* [WSL 2 Networking](https://www.youtube.com/watch?v=yCK3easuYm4)
* [Accessing network applications with WSL](https://learn.microsoft.com/en-us/windows/wsl/networking#accessing-a-wsl-2-distribution-from-your-local-area-network-lan)

---------------


# Configure Networking for Windows Subsystem for Linux (WSL)
On machines running Windows 11 22H2 and higher you can set `networkingMode=mirrored`
in the `.wslconfig` file to enable mirrored mode networking.
Enabling this changes WSL to an entirely new networking architecture
where the network interfaces that you have on Windows are "mirrored" into Linux.
With this, you can access the Window PC network from the WLS environment.

In Mirrored mode, WSL2 mirrors the network interfaces available on your Windows host into the Linux environment.
This means your Ubuntu instance will:

* Ubuntu shares the same IP address(es) as your Windows host on your LAN.
* Your able to directly communicate with other devices on your local network without the need for port forwarding in Windows.
* Be able to connect to Windows servers using localhost (aka `127.0.0.1`)

Sources:
* [How does mirrored mode neworking work in WSL?](https://www.youtube.com/watch?v=bvW_2rXCOQw)
* [My First Experience with WSL2 (With Mirrored Network Mode)](https://joaocarlos.dev/posts/my-wsl2-experience-so-far/)
* [Exposing ports from WSL to the Network](https://medium.com/@florian.loehden/exposing-ports-from-wsl-to-the-network-cff3bb221117)
* [Kali Linux, Windows Subsystem for Linux (WSL), Mirrored Mode Networking…What’s not to love?](https://medium.com/@theseriallearner/kali-linux-windows-subsystem-for-linux-wsl-mirrored-mode-networking-whats-not-to-love-afc211c9e2f0)
* Gemini Prompt: I have successfully install WLS2 and Ubuntu 24.0 on a Windows 11 PC. How can I use Mirrored mode networking in WSL2 so that the Ubuntu instance can communicate with other systems on my LAN?

#### Step 1: Enable Mirrored Mode Networking - DONE
You need to create or edit the `.wslconfig` file in your profile directory.
**Do the following in a PowerShell terminal**:

```powershell 
# navigate to your user profile directory
cd $env:USERPROFILE

# check if a .wslconfig file exists (it should not)
dir -Force 
```

If the file doesn't exist, create it, or edit the existing one using a text editor like Notepad:

```powershell 
# edit the .wslconfig file
notepad .wslconfig
```

Add the following text to the file:

```text 
[wsl2]
# you can revert to the default NAT mode by changing to 'networkingMode=nat'
networkingMode=mirrored
```

>**NOTE:** You can revert to the default NAT mode by changing to `networkingMode=nat`.

#### Step 2: Restart Ubuntu WSL Instance, Enabling Mirroring - DONE
In the same PowerShell window, run the following command to shut down all running WSL instances:

```powershell 
# shutdown all running wsl instances
wsl --shutdown
```

Now restart your Ubuntu instance.
You can do this by open your Ubuntu 24.04 terminal.
This will start WSL with the new configuration.

Now open your Ubuntu terminal and run the following command to check the networking mode:

```bash 
# check status of networking mode, should output 'mirrored'
wslinfo --networking-mode

# check the ip address of the wsl ubuntu, should output same ip address as the Window PC (192.168.1.155/24)
ip address | grep eth0

# finding IPs and identifying devices on your network, you should see everything on your lan
sudo netdiscover -c 3 -s 10 -L -N -r 192.168.1.0/24
```

So if every thing is working as desired,
WSL should be mirrored,
the WSL Ubuntu IP address is the same as the Window PC,
and when scanned from the WSL Ubuntu you see all the devices on the LAN.

There is one remaining problem,
and that is you can't yet reach the WSL Ubuntu from any of the devices on the LAN.
This can be seen from via the `ping 192.168.1.155`.
Let fix this next.

#### Step 3: Open Windows PC Firewall 
**** Work in Progress **** Work in Progress **** Work in Progress **** Work in Progress ****

We need to ensure that your Windows PC firewall (or any third-party firewall)
is configured to allow incoming and outgoing connections
for the services running in the WSL Ubuntu instance.
Since WSL Ubuntu shares the host's IP, you'll need to manage firewall rules on the Windows side.
In our case, we need to open port 22 for SSH services.

```powershell 
# in powershell, check the status of the port used by ssh (port 22)
```

Sources:
* [How to add a rule or port to a Windows 11 firewall](https://www.youtube.com/watch?v=GBUVyu69Qsk)
* Gemini Prompt: I have successfully install WLS2 and Ubuntu 24.0 on a Windows 11 PC. I have successfully established Mirrored mode networking in WSL2 so that the Ubuntu instance is can communicate with other systems on my LAN. I now want to other systems on my LAN to communicate with my WSL Ubuntu instance via ssh. How can I do this?

---------------


# Multicast DNS (mDNS)
**** Work in Progress **** Work in Progress **** Work in Progress **** Work in Progress ****

To make our WSL discoverable on a private network via the command `ssh login@hostname.local`,
you need to ensure that your system can resolve `hostname.local`
to the correct IP address of the target machine within your local network. 
Multicast DNS (mDNS) is a protocol that allows devices on a local network to
discover each other and resolve hostname's without a dedicated DNS server.

```bash 
# install multicase dns to resolve .local
sudo apt install avahi-daemon
sudo systemctl enable avahi-daemon
sudo systemctl start avahi-daemon

# check the daemon's status
sudo systemctl status avahi-daemon
```

Sources:
* Gemini Prompt: How do I make "ssh login@hostname.local" work for me?

Sources:
* [How to check IP address in Linux](https://www.youtube.com/watch?v=L2Qh131c-EI)
* [How a DNS Server (Domain Name System) works](https://www.youtube.com/watch?v=mpQZVYPuDGU)



---------------


# WSL Ubuntu GUI Desktop 
**** Work in Progress **** Work in Progress **** Work in Progress **** Work in Progress ****

Limitations ...
You cannot do a Windows Remote Desktop Connection directly to a Linux desktop environment.
You need Windows 11 Pro to remote into Windows Home.

Remote Desktop Protocol (RDP) is designed for connecting to Windows machines, not Linux.
To access a Linux desktop remotely from Windows,
you need to use a different protocol like VNC or xrdp (X Remote Desktop Protocol). 

Windows 11 Remote Desktop Connection

## Using VNC
* [How to Install a GUI on Ubuntu Server](https://www.youtube.com/watch?v=ODhGNe0s4lI)

## Using Ubuntu GUI Within WSL
* [How To Install Ubuntu 24.04 On Windows 11 Using WSL With GUI (NEW GUIDE)](https://www.youtube.com/watch?v=iXAWNVgOUrw)
* [How to Install a Linux Desktop and GUI on Windows Subsystem for Linux - WSL in Windows](https://www.youtube.com/watch?v=EBRxSYv0ojg)

## Apache Guacamole
* [Secure Remote Access to SSH & RDP From Your Browser](https://www.youtube.com/watch?v=GX53C80c05k)

## Rustdesk
* [Rustdesk](https://rustdesk.com/)
* [Your Remote Desktop SUCKS!! Try this instead (FREE + Open Source)](https://www.youtube.com/watch?v=EXL8mMUXs88)
* [Open Source Self Hosted Teamviewer Replacement](https://www.youtube.com/watch?v=FIEcTNjFZNA)

## Connect to Window 11 From Ubuntu
[Connect to Windows 11 from Ubuntu Linux using RDP](https://www.youtube.com/watch?v=fH1QSCwl0qY)

On your Ubuntu system, do the following:

```bash
# update your software
sudo apt update

# install your remote desktop client gui application
sudo apt install remmina 

# install the remmina plugin for the remote desktop protocol (rdp)
sudo apt install remmina-plugin-rdp
```

## Connect to Ubuntu From Windows 11
* [WSL2 Ubuntu GUI](https://www.youtube.com/watch?v=IL7Jd9rjgrM)
* [How to install a desktop environment on Windows Subsystem for Linux (WSL with GUI)](https://www.youtube.com/watch?v=Ijw1Av9xrwY)


---------------


# WSL Commands to Manage Linux Virtual Machines
Below are some useful `wsl` commands, that you execute in a PowerShell terminal.

```bash 
# update wsl to the latest version
wsl --update

# what version of wsl is install
wsl --version

# list installed Linux distributions 
wsl --list --verbose

# list Linux distributions available
wsl --list --online

# install ubuntu 24.04 linux distribution
wsl --install -d Ubuntu-24.04

# execute a specific version of linux
wsl -d Ubuntu-24.04

# what is the status/version of wsl, windows, etc. 
wsl --status

# shutdown all running wsl instances
wsl --shutdown
```



[01]:https://learn.microsoft.com/en-us/windows/wsl/about
[02]:https://opticos.github.io/gwsl/
[03]:https://www.x.org/archive/X11R7.6/doc/man/man1/Xserver.1.xhtml
[04]:https://www.x.org/wiki/
[05]:https://www.x.org/releases/X11R7.7/doc/xproto/x11protocol.html
[06]:https://www.youtube.com/watch?v=vH2rJs-9ntk
[07]:https://docs.ros.org/en/jazzy/index.html
[08]:https://www.gmktec.com/products/intel-alder-lake-n97-mini-pc-nucbox-g5
[09]:https://apps.microsoft.com/detail/9nl6kd1h33v3?hl=en-US&gl=US

