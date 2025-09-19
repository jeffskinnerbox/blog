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

>**NOTE:** The procedure documented below was tested on a [GMKtec NucBox G5][08] for this project.
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

# verify firewall configuration
sudo ufw status
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
#OR
ip address | grep eth1

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

#### Step 3: Open Windows PC Firewall - DONE

We need to ensure that your Windows PC firewall (or any third-party firewall)
is configured to allow incoming and outgoing connections
for the services running in the WSL Ubuntu instance.
Since WSL Ubuntu shares the host's IP, you'll need to manage firewall rules on both the Ubuntu and the Windows side.
We addressed Ubuntu in the earlier step.
Now we need to open port 22 for SSH services within Windows.

To do this, follow the procedure give in the video ["How to add a rule or port to a Windows 11 firewall"][10].
You'll need to establish a inbound firewall rule for port 22
(I could also create an outbound rule, but I did not).
I applied the rule to, any IP address/users/services, all Profiles (Domain, Private, and Public),and **very importantly**,
set the Action to "Allow all connections" and set the rule to "Allow edge traversal".
Allowing all connections means it doesn't have to be a secure connection,
and edge traversal allows NAT'ed unsolicited inbound packets.

To test that your firewall is set properly, connect to the WSL Ubuntu instance on the Windows 11 PC
from an entirely seperate Linux box on your local network like this:

```bash
# from a separate linux box, login to the wsl ubuntu instance successfully with
ssh jeff@192.168.1.155
```

>**NOTE:** If you kill the WSL Ubuntu instance on Windows 11, you will no longer be able to SSH into Windows 11 or Ubuntu.
>SSH is being established by the Ubuntu environment and not Windows 11.

Sources:

* [How to add a rule or port to a Windows 11 firewall][10]
* Gemini Prompt: I have successfully install WLS2 and Ubuntu 24.0 on a Windows 11 PC. I have successfully established Mirrored mode networking in WSL2 so that the Ubuntu instance is can communicate with other systems on my LAN. I now want to other systems on my LAN to communicate with my WSL Ubuntu instance via ssh. How can I do this?

#### Step 4: Remote the X Application from WSL Ubuntu - DONE, NOT

**** Work in Progress **** Work in Progress **** Work in Progress **** Work in Progress ****

It appears that to remove the display of a X Window application running on WSL Ubuntu,
you must install a X Server to handle the remote requests.
It appears the integration of GWSL into the WLS install process only works when displaying on the Windows 11 display.

Sources:

* Gemini Prompt: I have Ubuntu running in WSL on Windows 11 and I can successfully SSH into the Ubuntu instance via SSH from a separate Ubuntu box on my LAN. I attempted to execute a X Window application from the separate Ubuntu box via "ssh -X" but nothing was displayed. What have I missed?
* Gemini Prompt: Why do I need to install an X server? Doesn't WLS provide this functionality via GWSL?
* Gemini Prompt: For the latest installation procedure for WSL, do I still have to manually install GWSL as an additional step?


---------------


# Multicast DNS (mDNS) - DONE

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

* Gemini Prompt: How do I make "ssh <login@hostname.local>" work for me?

Sources:

* [How to check IP address in Linux](https://www.youtube.com/watch?v=L2Qh131c-EI)
* [How a DNS Server (Domain Name System) works](https://www.youtube.com/watch?v=mpQZVYPuDGU)



---------------


# Access Windows 11 desktop From Ubuntu - DONE

**** Work in Progress **** Work in Progress **** Work in Progress **** Work in Progress ****

To access a Windows 11 desktop from Ubuntu 24.04,
you'll need to use the [Remote Desktop Protocol (RDP)][12].
This requires enabling Remote Desktop on Windows 11
and then connecting to it from your Ubuntu machine using a client like [Remmina][11] or [FreeRDP][13].

Sources:

* [Access Windows 11 from Linux – Step-by-Step Remote Access Tutorial!](https://www.youtube.com/watch?v=fJCbn8aM3oU)

## Prepare Windows 11 for Remote Desktop - DONE

To enable Remote Desktop on Windows 11:

1. Open the Windows **Settings** app.
2. Go to **System** > **Remote Desktop** and toggle the switch to turn it `On`.  Remote Desktop port is set to `3389`.
3. You'll need to confirm the change by clicking the **Confirm** button. This allows you to connect to and access your Windows 11 PC remotely.

To validate all is well, open a Command Prompt terminal and execute the following:

```bash
# list all ports listing, if port is 'listening' then it is open
netstat -a -o

# get the IP address of your box
ipconfig
```

Look for an entry with TCP and port 3389.
If the status is "Listening" and there's a process ID (PID), the port is open.
If you don't see an entry, the port is likely closed.

Make note of the IP address of your Windows 11 machine, you'll need it later.

## Prepare Ubuntu for Remmina Use - DONE

You simple need to install Remmina on Ubuntu.
To do this, open the Ubuntu Software Center (at top left corner of screen), search for **Remmina**, and install it via Snap.
Better yet, you can install Remmina using this method:

```bash
# install your remote desktop client gui application
sudo apt install remmina 

# install the remmina plugin for the remote desktop protocol (rdp)
sudo apt install remmina-plugin-rdp
```

With the install done, execute Remmina and set up your first connection to your Windows 11 with the steps below:

1. Open Remmina.
2. Click the **+** icon to add a new profile.
3. Select **RDP** as the protocol.
4. Enter the IP address of your Windows 11 machine in the **Server** field.
5. Enter your Microsoft username and password.
6. Set your Resolution to **Use initial window size**, Network connection type to **Auto-detect**.
7. Click **Connect**

Sources:

* [Remote Desktop from Ubuntu to Windows](https://www.youtube.com/watch?v=x6MbzH4CWXU)

## Prepare Ubuntu for FreeRDP Use - DONE

FreeRDP's `xfreerdp` is an X11 Remote Desktop Protocol (RDP) client which is part of the FreeRDP project.
An RDP server is built-in to most editions of Microsoft Windows and the `xfreerdp` command line tool will make the connection.
The basic command structure is `xfreerdp /u:<username> /p:<password> /v:<ip_address>`.

Install the FreeRDP packages required:

```bash
# install rdp on ubuntu
sudo apt install freerdp2-x11 freerdp2-wayland
```

To use the FreeRDP command line tool:

```bash
# to get some help integration

# freerdp commandline
xfreerdp /u:jeff.irland@verizon.net /p:xXt6ttYUzZRrfQ3 /v:192.168.1.155 /size:1600x900
```


---------------


# WSL Commands to Manage Linux Virtual Machines

Below are some useful `wsl` commands, that you execute in a PowerShell terminal:

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


# UFW Commands to Manage Linux

Below are some useful `ufw` commands, that you execute in a Bash terminal:

```bash
# activates the firewall, and it will start automatically when the system boots
sudo ufw enable

# disables the firewall
sudo ufw disable

# displays the current firewall status, including whether it's active and the default policies for incoming and outgoing traffic
sudo ufw status

# provides a more detailed view of the firewall status, including a list of active rules 
sudo ufw status verbose

#  sets the default policy for incoming traffic to deny (block) all connections
sudo ufw default deny incoming

# sets the default policy for outgoing traffic to allow
sudo ufw default allow outgoing

# sets the default policy for outgoing traffic to deny
sudo ufw default deny outgoing
```

Sources:

* [How to Set Up a Firewall with UFW on Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu)
* [UFW Essentials: Common Firewall Rules and Commands](https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands)



[01]:https://learn.microsoft.com/en-us/windows/wsl/about
[02]:https://opticos.github.io/gwsl/
[04]:https://www.x.org/wiki/
[05]:https://www.x.org/releases/x11r7.7/doc/xproto/x11protocol.html
[06]:https://www.youtube.com/watch?v=vh2rjs-9ntk
[07]:https://docs.ros.org/en/jazzy/index.html
[08]:https://www.gmktec.com/products/intel-alder-lake-n97-mini-pc-nucbox-g5
[09]:https://apps.microsoft.com/detail/9nl6kd1h33v3?hl=en-us&gl=us
[10]:https://www.youtube.com/watch?v=gbuvyu69qsk
[11]:https://remmina.org/
[12]:https://support.microsoft.com/en-us/windows/how-to-use-remote-desktop-5fe128d5-8fb1-7a23-3b8a-41e636865e8c
[13]:https://www.freerdp.com/



