<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>



When I travel, I sometimes want access to my computers on my home LAN.
Cloudflare Tunnels provides me a safe and secure method to do this
but after some period time of inactivity,
my machines will go into a suspended or hibernation state.
Generally, you are able to be waked-up the machine, but you do so from the machine's console.
This renders the Cloudflare Tunnels access method useless,
unless I somehow disable the suspend or hibernation feature on the machine.

Disabling of suspend / hibernation feature is possible
but doing so defeats the energy savings that its intended for.
Most of the times, I would like my machine to be suspended since
remote access to my machine is a rare need.
I need a wake-up method that I can invoke remotely, as needed.

In effect, WOL enables other systems on your LAN to turn on your system over the network.
Support for WOL is required in your network card, motherboard, UEFI/BIOS boot firmware,
and operating system network configuration.
The articles [here][08] and [here][09] provide some very good guidance on how to get WOL working.

Works with an IP address or Fully Qualified Domain Name and even local Domain names as long as DNS can do a lookup.


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

# From Outside the Linux Machine
[Wake-on-LAN (WOL)][03] is an Ethernet networking standard that allows a server
to be turned on by a network message.
You need to send 'magic packets' to wake-on-lan enabled ethernet adapters and motherboards
to switch on the called systems.
First step is to make sure your machines NIC (`eth0` or `eth1`) is with the motherboard
and the BIOS’s WOL function is enabled.

This is useful if you plan to access your computer remotely for any reason.
You can keeping the machine in a low-power state to save electricity.
For example, if you want to use VNC, video conferencing, etc. while away from home,
you have the option of waking up you machine and gain access.

You'll need an always running server from which to send the WOL magic packet.
The obvious candidate foe is my LAN's router.
I'll create a Docker container specifically designed to provide this service
accessible via Cloudflare's tunnels capabilities.

>**NOTE: Wake-on-lan is implemented as a Layer-2 protocol, and as such, it is not a Linux-specific issue.
>Wake-on-lan is implemented by the motherboard and network card, not the operating system.
>As a result, you will see many different methodologies to get get Wake-on-lan working.
>The web article ["The Ultimate Guide to Wake on LAN for Windows, MacOS, and Linux"][08]
>gives you a broad view on the many things that maybe needed to get wake-on-lan working.

Sources:

* [Introduction to Wake On Lan][05]
* [What Is Wake-on-LAN, and How Do I Enable It?](https://www.howtogeek.com/70374/how-to-geek-explains-what-is-wake-on-lan-and-how-do-i-enable-it/)
* [How To Wake Up Computers Using Linux Command, Wake-on-LAN, By Sending Magic Packets](https://www.cyberciti.biz/tips/linux-send-wake-on-lan-wol-magic-packets.html)
* [Enabling Wake-On-LAN (In Ubuntu 20.10)](https://necromuralist.github.io/posts/enabling-wake-on-lan/)
* [The Ultimate Guide to Wake on LAN for Windows, MacOS, and Linux][08]
* [Detecting whether netplan is managing network config (shell)](https://askubuntu.com/questions/1033592/detecting-whether-netplan-is-managing-network-config-shell)
* [WakeOnLan][09]

## Enabling WOL via `ethtool`
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
sudo ethtool -s eno1 wol g
```

If your machine is using Ubuntu (like me) and using [netplan][07] (not me, I'm using NetworkManager),
a better alternative to the above would be to update you netplan file
`/etc/netplan/01-network-manager-all.yaml` (**NOTE:** your file name could differ).
See [here][08] concerning what needs to be done.

WOL should be enabled now.
You can run the command `sudo ethtool eno1 | grep Wake-on` and see if it’s enabled now.
Look for the “Wake on” section and you should see a 'g' instead of a 'd' now.

>**NOTE:** On my machine, I also have a NIC with the name `eth1`.
>Currently, it doesn't have an Ethernet cable attached,
>but at sometime in the future, I might move my cable intentially or mistakenly.
>I perfromed the same tasks above to that NIC to cover this senario.

## Making NIC Name Persistent Using udev Rules
Enabling the WOL feature may not be enough,
but appears to be sufficient on my machine.
The fact is, there is no assurance the change will not persist a machine reboot.
The web article ["Introduction to Wake On Lan"][05] shows how to create an [udev rule][06]
which will run the appropriate command once the network interface is detected.
The article ["The Ultimate Guide to Wake on LAN for Windows, MacOS, and Linux"][08]
shows how to use `systemd` and `netplan`.

## How to Wake Your Computer with Wake-on-LAN Magic Packets
In order to wake up a remote machine machine up,
you will need a tool that can send a wake on LAN packet to the remote machine.
I usually prefer installing a command line tool (but GUI tools do exist).
One such tool is `wakeonlan`, an open source utility that’s simple to use.

```bash
# install the wol commandline tool
sudo apt install wakeonlan

# get the mac address of the ethernet card
$ ip address show eno1 | grep -i link/ether
    link/ether 00:22:4d:83:c1:c8 brd ff:ff:ff:ff:ff:ff

# get the mac address of the other ethernet card
$ ip address show eth1 | grep -i link/ether
    link/ether 00:22:4d:83:c1:d7 brd ff:ff:ff:ff:ff:ff

# get the mac address of the wifi card
$ ip address show wlx94dbc95110ca | grep -i link/ether
    link/ether 94:db:c9:51:10:ca brd ff:ff:ff:ff:ff:ff

# you can now wake machines on the same network by
sudo wakeonlan 00:22:4D:83:C1:C8 00:22:4D:83:C1:D7 94:DB:C9:51:10:CA

# if your machine is on another network and you can reach the broadcast ip
sudo wakeonlan -i 192.168.1.255 00:22:4D:83:C1:C8 00:22:4D:83:C1:D7 94:DB:C9:51:10:CA
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
sudo wakeonlan 00:22:4D:83:C1:C8 00:22:4D:83:C1:D7 94:DB:C9:51:10:CA
```

Sources:
* [The Ultimate Guide to Wake on LAN for Windows, MacOS, and Linux][08]
* [WoL.sh](https://github.com/leestevetk/WoL.sh)
* [pm-suspend Manual Page](https://linux.die.net/man/8/pm-suspend)
* [Generating The Wake On Lan Magic Packet](https://wiki.tcl-lang.org/page/Generating+The+Wake+On+Lan+Magic+Packet)
* [Wake-on-LAN: suspend and resume machines from the network](https://a3nm.net/blog/wakeonlan.html)

## Other Tools to Wake Your Machine

Sources:
* [Alexa Wake on Lan (WoL)][04]
* [Wake Up Your Computers Using Your Android Phone](https://www.howtogeek.com/94110/wake-up-your-computers-using-your-android-phone/)

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


