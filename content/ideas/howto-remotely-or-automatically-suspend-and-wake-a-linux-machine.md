<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/danger-prototyping-in-progress.png" title="These materials are very close to being complete and fit for use.  Then again, maybe not.  Proceed with caution and remember you have been warned!" align="center" width=390px height=282px>
</div>


# READ THIS
* [Start PCs from remote (Wake on LAN, WOL) for Windows and Linux](https://www.youtube.com/watch?v=4Jf2T45tfEU)
* [Linux Server, Wakey, Wakey](https://hackaday.com/2023/04/21/linux-server-wakey-wakey/)
    * [Making a Linux home server sleep on idle and wake on demand — the simple way](https://dgross.ca/blog/linux-home-server-auto-sleep/)
* [Proxmox Backup Auto-Shutdown](https://www.apalrd.net/posts/2024/pbs_hibernate/)
    * [Wake On LAN (on Proxmox VE machine)](https://drive.google.com/file/d/1J6_nwx4Vq8mptJZknghhs8p9OPZ4NhGP/view)




When I travel, I sometimes want access to my computers on my home LAN,
but after some period time of inactivity,
my machines will go into a suspended or hibernation state.
I could disable the suspend / hibernation feature
but doing so defeats the energy savings that its intended for.
Most of the times, I would like my machine to be sleeping since
remote access to my machine is a rare need,
I can keeping the machine in a low-power state to save electricity,
and it makes my system that much more secure.
What I need is a wake-up method that I can invoke remotely, as needed.

Generally, you are able to be waked-up a machine
by a momentary press of the computers power button.
This button push isn't possible remotely,
so I need a wake-up method, through my network card attached to my LAN,
to reach my sleeping machine.
I could use Cloudflare Tunnels to provides me a safe and secure method to
access an always actively running machine from which I can
send a command to wake-up my sleeping machine.

[Wake-on-LAN (WOL)][03] is an Ethernet networking standard that allows a server
to be turned on by a network message.
You need to send 'magic packets' to WOL enabled ethernet adapters and motherboards
to switch on the called systems.
In effect, WOL enables other systems on your LAN to turn on your system over the network.
Support for WOL is required in your network card, motherboard, UEFI/BIOS boot firmware,
and operating system network configuration.

With this strategy, if I plan to access my computer remotely while away from home,
I'll have the option of waking up you machine and gain access.
I'll need an always running server from which to send the WOL magic packet.
The obvious candidate for is my LAN's router.
I can create a Docker container specifically designed to provide this service,
accessible only via Cloudflare's tunnels capabilities.

>**NOTE: Wake-on-lan (WOL) is implemented as a Layer-2 protocol,
>and as such, it is not a Linux-specific feature.
>WOL is implemented by the motherboard and/or network card, not the operating system.
>As a result, you will see many different methodologies to get get WOL working.
>The web article in the 'Sources' below gives you a broad view on the
>many things that maybe needed to get WOL working.

Sources:

* [Introduction to Wake On Lan][05]
* [What Is Wake-on-LAN, and How Do I Enable It?](https://www.howtogeek.com/70374/how-to-geek-explains-what-is-wake-on-lan-and-how-do-i-enable-it/)
* [How To Wake Up Computers Using Linux Command, Wake-on-LAN, By Sending Magic Packets](https://www.cyberciti.biz/tips/linux-send-wake-on-lan-wol-magic-packets.html)
* [Enabling Wake-On-LAN (In Ubuntu 20.10)](https://necromuralist.github.io/posts/enabling-wake-on-lan/)
* [The Ultimate Guide to Wake on LAN for Windows, MacOS, and Linux][08]
* [Detecting whether netplan is managing network config (shell)](https://askubuntu.com/questions/1033592/detecting-whether-netplan-is-managing-network-config-shell)
* [WakeOnLan][09]


-------


# How to Disable Auto-Suspend in Linux
The easiest ways to disable auto-suspend on your computer is via the GUI Settings.
In Ubuntu, and similar distributions, you just navigating to **Settings** > **Power**.
Click on **Automatic Suspend** and toggle the two setting options so that your computer
does not automatically suspend when on battery power or plugged in.

Sources:
* [How to Disable Auto-Suspend in Linux](https://www.makeuseof.com/disable-auto-suspend-in-linux/)

# How to Automatically Suspend and Wake in Linux
The [`rtcwake`][13] command can be used to automatically place Linux into sleep, hibernate, or shut down states,
and then turn it back on at a specific time.
It uses [ACPI][14] functions to control switching the computer on or off and replaces its predecessor,
the [`nvram-wakeup`][15] command, which uses BIOS functions.

For periodic implementation of suspend & wake,
you can run `rtcwake` as a `cron` job every day or even specific days of a week or month.

Sources:
* [How to Automatically Suspend and Wake a Linux Machine](https://www.baeldung.com/linux/auto-suspend-wake)

#### Step 1: Enabling Wake-on-LAN - DONE
Ubuntu has a tool that can check to see if your machine supports WOL, and can enable it.
Open up a terminal and install `ethtool` with the following command:

```bash
# install ethtool
sudo apt install ethtool

# check if you default network interface is wol enabled
# note: your ethernet device may be named something our than 'eno1'
$ sudo ethtool eno1 | grep Wake-on
	Supports Wake-on: pumbg
	Wake-on: g
```

Look for the “Supports Wake-on” section.
As long as one of the letters listed is 'g',
you can use magic packets for Wake-on-LAN
(See [here][05] for what the other letters mean).

To enable this option, use the following command:

```bash
# enable wol
sudo ethtool --change eno1 wol g
# OR
sudo ethtool -s eno1 wol g
```

WOL should be enabled now.
You can run the command `sudo ethtool eno1 | grep Wake-on` and see if it’s enabled now.
Look for the “Wake on” section and you should see a 'g' instead of a 'd' now.

>**NOTE:** It appears that I have to repeat the execution of wake-on-lan enablement
>command `sudo ethtool -s eno1 wol g` after a Linux kernel upgrade.
>I need its enablement to be permanent and I'll show that is done later.

If your machine is using Ubuntu (like me) and using [netplan][07] (not me, I'm using NetworkManager),
a better alternative to the above would be to update you netplan file
`/etc/netplan/01-network-manager-all.yaml` (**NOTE:** your file name could differ).
See [here][08] concerning what needs to be done.

#### Step 2: Test Computer with Wake-on-LAN Magic Packets - DONE
In order to wake up a remote machine machine up,
you will need a tool that can send a wake on LAN packet to the remote machine.
I prefer installing a command line tool (but GUI tools do exist),
and one such tool is [`wakeonlan`][09],
an open source utility that’s simple to use.

```bash
# install the wol commandline tool
sudo apt install wakeonlan

# get the mac address of the ethernet card
$ ip address show eno1 | grep -i link/ether
    link/ether 00:22:4d:83:c1:c8 brd ff:ff:ff:ff:ff:ff

# get the mac address of the other ethernet card
$ ip address show eth1 | grep -i link/ether
    link/ether 00:22:4d:83:c1:d7 brd ff:ff:ff:ff:ff:ff

# print print mac address of all the active network interfaces
$ sudo ip address show eth1 | grep -i link/ether | awk '{ print $2 }' ; \
    sudo ip address show eno1 | grep -i link/ether | awk '{ print $2 }'
00:22:4d:83:c1:d7
00:22:4d:83:c1:c8

# you can now wake the machine on the same network by
sudo wakeonlan 00:22:4D:83:C1:C8 00:22:4D:83:C1:D7

# if your machine is on another network and you can reach the broadcast ip
sudo wakeonlan -i 192.168.1.255 00:22:4D:83:C1:C8 00:22:4D:83:C1:D7
```

For testing, lets install some tools to suspend the machine

```bash
# install the suspend tool
sudo apt install pm-utils

# from a terminal on the machine, suspend the machine
# see https://linux.die.net/man/8/pm-suspend
sudo pm-suspend          # system state is saved in ram and enter low power mode
#OR
sudo pm-hibernate        # system state is saved to disk and fully powered off
#OR
sudo pm-suspend-hybrid   # system does everything it needs to hibernate, suspends instead of shutting down

# from another machine on the same lan, send the magic packet
sudo wakeonlan 00:22:4D:83:C1:C8 00:22:4D:83:C1:D7
```

Sources:
* [The Ultimate Guide to Wake on LAN for Windows, MacOS, and Linux][08]
* [WoL.sh](https://github.com/leestevetk/WoL.sh)
* [pm-suspend Manual Page](https://linux.die.net/man/8/pm-suspend)
* [Generating The Wake On Lan Magic Packet](https://wiki.tcl-lang.org/page/Generating+The+Wake+On+Lan+Magic+Packet)
* [Wake-on-LAN: suspend and resume machines from the network](https://a3nm.net/blog/wakeonlan.html)

#### Step 3: Make WOL Enablement Persistent Using udev Rules - DONE
Initially, enabling the WOL feature may not be enough,
but appeared to be sufficient on my machine.
The `wakeonlan` tool appeared to work reliably, even between reboots.
Then I did a Linux kernel upgrade and it stopped working.
I had to issue the `ethtool` WOL enablement command (aka `sudo ethtool -s eno1 wol g`)
to get it working again.

The fact is, there is no assurance the WOL change will persist after machine reboot or kernel upgrades.
We must find a way to enable the option automatically at boot.
There are many ways we can do this.
The web articles ["Introduction to Wake On Lan"][05],
["ArchLinux: Wake-on-LAN"][12],
and ["An introduction to Udev: The Linux subsystem for managing device events"][06]
shows how to create a [udev rule][11]
which will run the appropriate command once the network interface is detected.

>**NOTE:** The article ["The Ultimate Guide to Wake on LAN for Windows, MacOS, and Linux"][08]
>shows how to use `systemd` and `netplan` show alternative ways
>to accomplish persistance of WOL enablement.)

I want to write a general udev rule to support the `eth` and `eno` network interface naming convention.
To enable wake-on-lan using magic packets via udev rule,
create the file `/etc/udev/rules.d/81-wake-on-lan.rules` with the following conents:

```bash
# On addition of a device to the net subsystem, where the name starts with 'eno' or 'eth',
# run ethtool to set wake-on-lan to magic packet mode.
# NOTE: Ensure that the path to ethtool is correct.
ACTION=="add", SUBSYSTEM=="net", NAME=="eno*", RUN+="/usr/sbin/ethtool -s $name wol g"
ACTION=="add", SUBSYSTEM=="net", NAME=="eth*", RUN+="/usr/sbin/ethtool -s $name wol g"
```

>**NOTE:** The file name is important and must start with a number between
>81 and 99 so that it runs after `80-net-setup-link.rules` or
>`80-net-name-slot.rules` (typical file name),
>which rename interfaces with predictable names.
>Otherwise, NAME would be undefined and the rule would not run.

With this file now created, make sure its has the right access privileges
and activate the rules (`sudo reboot` if necessary) the machine to assure
the rules are in effect:

```bash
# check the permissions
$ ls -l /etc/udev/rules.d/81-wake-on-lan.rules
-rw-r--r-- 1 root root 374 Mar 30 20:21 /etc/udev/rules.d/81-wake-on-lan.rules

# reload the udev rules
sudo udevadm control --reload-rules
sudo udevadm trigger
```


-------


# Build a REST API Microservice for Wake on LAN

* [Alpine Docker Container](https://hub.docker.com/_/alpine)
* [Building Docker Image from Scratch](https://dockerlabs.collabnix.com/beginners/building-docker-image-from-scratch.html)
* [How to build Your First Alpine Docker Image and Push it to DockerHub](https://dockerlabs.collabnix.com/beginners/building-your-first-alpine-container.html)
* [How to Build Docker Image : Comprehensive Beginners Guide](https://devopscube.com/build-docker-image/)
* [How to Deploy Microservices with Docker](https://www.linode.com/docs/guides/deploying-microservices-with-docker/)
* [Getting started with Microservices and Docker](https://www.coditation.com/blog/getting-started-with-microservices-and-docker)
* [Build and Deploy a REST API Microservice with Python Flask and Docker](https://dev.to/swarnimwalavalkar/build-and-deploy-a-rest-api-microservice-with-python-flask-and-docker-5c2d)
* [BUILD MICROSERVICE ARCHITECTURE (MSA) REST API USING THE USING FLASK](https://www.topcoder.com/thrive/articles/build-microservice-architecture-msa-rest-api-using-the-using-flask)
* [Microservices in Python using Flask Framework | Dockerize and Deploy to Kubernetes with Helm](https://www.youtube.com/watch?v=SdTzwYmsgoU)


#### Step X: Create Docker Container for Wakeup Function
At this point, all that needs to be done is to send out the following command to wake the machine:

```bash
# wake the machine
sudo wakeonlan -i 192.168.1.255 00:22:4D:83:C1:C8 00:22:4D:83:C1:D7
```

I need to launch this command from some "always up, never sleeping" Linux box on my network.
I plan to do this from a Docker container on my LAN router.

```bash
# create the wake-on-lan script to be executed
cat <<EOF > wakeup.sh
# this script will wake-on-lan desktop machine
wakeonlan -i 192.168.1.255 00:22:4D:83:C1:C8 00:22:4D:83:C1:D7
EOF
```

```
FROM alpine:latest
LABEL maintainer="jeffskinnerbox@yahoo.com"
RUN apk add --no-cache wakeonlan # bash
COPY ./wakeup.sh ./wakeup.sh
RUN chmod +x ./wakeup.sh

FROM alpine:latest
LABEL maintainer="jeffskinnerbox@yahoo.com"
RUN apk add nginx
RUN mkdir -p /run/nginx
RUN touch /run/nginx/nginx.pid
RUN adduser -D -g 'www' www
RUN mkdir /www
RUN chown -R www:www /var/lib/nginx
RUN chown -R www:www /www
COPY nginx.conf /etc/nginx/nginx.conf
COPY index.html /www
RUN ["./usr/sbin/nginx"]
```


------


# Other Tools to Wake Your Machine

Sources:
* [Alexa Wake on Lan (WoL)][04]
* [Wake Up Your Computers Using Your Android Phone](https://www.howtogeek.com/94110/wake-up-your-computers-using-your-android-phone/)

# From Within the Linux Machine
Sources:

* [How to Automatically Suspend and Wake a Linux Machine](https://www.baeldung.com/linux/auto-suspend-wake)

## Using `rtcwake`
We can use the [`rtcwake`][01] command to automatically sleep, hibernate,
or shut down a computer and then turn it back on at a specific time.
It uses [Advanced Configuration and Power Interface (ACPI)][02] functions to control switching the computer on or off.

```bash
# check it rtcwake is install
which rtcwake

# if not installed, do so
sudo apt install util-linux

# use rtcwake to suspend the computer to either memory or disk and wake it back up at a specific time
# e.g. suspend our system to ram, then wake it up one minute later
$ sudo rtcwake -u -s 60 -m mem
rtcwake: wakeup from "mem" using /dev/rtc0 at Wed Nov 9 15:11:05 2022

# alternatively, we can suspend the system to disk
$ sudo rtcwake -u -s 60 -m disk
rtcwake: wakeup from "disk" using /dev/rtc0 at Wed Nov 9 15:33:35 2022

# wake up our computer at a specific time of the day
sudo rtcwake -m no -l -t "$(date -d 'today 16:20:00' '+%s')"
```

* **-u** option to assume the hardware clock is set to UTC
* **-s** option sets the wake-up time in seconds and the -m option sets the standby state
* **-l** option assumes the hardware clock is set to local time
* **-t** option sets the wakeup time to 4:20 pm today

With `cron`, we can automate the `rtcwake` command to run every day
or even specific days of a week or month.

## Using System Commands
Many Linux distros have adopted [`systemd`][10] as their system and service manager.
In systemd-managed systems, rebooting and shutting down the system are managed by `systemctl`.

```bash
# see how shutdown commands work
$ file /sbin/{halt,poweroff,reboot,shutdown}
/sbin/halt:     symbolic link to /bin/systemctl
/sbin/poweroff: symbolic link to /bin/systemctl
/sbin/reboot:   symbolic link to /bin/systemctl
/sbin/shutdown: symbolic link to /bin/systemctl

# we can specify a specific date, time, and even a message to display before shutting down
# e.g. shut down the system at 4:20 pm
$ sudo shutdown -r 16:20
Shutdown scheduled for Sun 2022-11-10 16:20:00 CEST, use 'shutdown -c' to cancel.
```

## Wake-up to Support Nightly Backups
Here is a sample shell script that will wake up my laptop (IP 192.168.2.25 and mac 48:2a:e3:5c:16:bc) from my rsnapshot Linux backup server:

```bash
#!/bin/bash
# load ssh keys from keychain
. /home/backups/.keychain/backup-ssh-key

# Try to wake up sleeping laptop at night and odd time as per cronjob
/usr/bin/wakeonlan 48:2a:e3:5c:16:bc

# Sleep for 30 seconds to that laptop comes online
/bin/sleep 30

# Verify and start backup
/sbin/ping -q -c 30 192.168.2.25 >/dev/null
if [ "$1" != "" ]
then
    # start backup
    /usr/local/bin/rsnapshot "$1"
    # push everything offsite to aws-s3 buckets and exit this session due to slow upload links
    echo '/home/backups/push-mirror-to-aws-s3' | /usr/bin/at now + 5 minute
else
    echo "Usage: $0 [hourly|daily|montly|weekly|yearly]"
    exit 1
fi
```



[01]:https://linux.die.net/man/8/rtcwake
[02]:https://de.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface
[03]:https://en.wikipedia.org/wiki/Wake-on-LAN
[04]:https://www.amazon.com/Oscar-Penelo-Wake-Lan-WoL/dp/B07PGKK416
[05]:https://linuxconfig.org/introduction-to-wake-on-lan
[06]:https://opensource.com/article/18/11/udev
[07]:https://netplan.io/
[08]:https://docs.technotim.live/posts/wake-on-lan/
[09]:https://wiki.debian.org/WakeOnLan
[10]:https://opensource.com/downloads/pragmatic-guide-systemd-linux
[11]:https://man7.org/linux/man-pages/man7/udev.7.html
[12]:https://wiki.archlinux.org/title/Wake-on-LAN
[13]:https://linux.die.net/man/8/rtcwake
[14]:https://en.wikipedia.org/wiki/ACPI
[15]:https://manpages.ubuntu.com/manpages/trusty/man8/nvram-wakeup.8.html
[16]:
[17]:
[18]:
[19]:
[20]:


