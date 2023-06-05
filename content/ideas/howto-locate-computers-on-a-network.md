<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----



* [hpr3052 :: Locating computers on a network](http://hackerpublicradio.org/eps.php?id=3052)
* [hpr3090 :: Locating Computer on a Enterprise Network](http://hackerpublicrdio.org/eps.php?id=3090)
* [Use this script to find a Raspberry Pi on your network](https://opensource.com/article/20/6/find-raspberry-pi)

* [What is Ethernet?](https://www.youtube.com/watch?v=HLziLmaYsO0)
* [What is Ethernet/IP?](https://www.youtube.com/watch?v=mm-NHrLtRWI)

* [Is it possible to find a computer's physical location in a room?](https://serverfault.com/questions/671781/is-it-possible-to-find-a-computers-physical-location-in-a-room)

* [How To Check If A Linux System Is Physical Or Virtual Machine](https://ostechnix.com/check-linux-system-physical-virtual-machine/)
* [5 commands to check if server is physical or virtual in Linux or Unix](https://www.golinuxcloud.com/check-if-server-is-physical-or-virtual/)

Check out the file "sniff-for-wifi-devices-and-people.md"
* [Great Badge Concept: A “Geiger Counter” For WiFi Deauthentication Frames](https://hackaday.com/2020/06/20/great-badge-concept-a-geiger-counter-for-wifi-deauthentication-frames/)


# Fing & Firewalla
* [Fingbox Review - How to manage and monitor your home network devices and users](https://www.youtube.com/watch?v=lkngAqevQ9s)
* [How to install Fing on CentOS / Ubuntu / Debian Cloud Servers](https://www.layerstack.com/resources/tutorials/How-to-install-Fing-on-CentOS-Ubuntu-Debian-Cloud-Servers)
* [Fing CLI User Guide](https://www.fing.com/images/uploads/general/Fing_CLI_User_Guide_1.2.pdf)
* [Fing Support](https://help.fing.com/article-categories/fing-desktop/)

* [Firewalla](https://firewalla.com/)






Often, when firing up a new IP-enable device on my home network,
the very first thing I want to know is it IP address.
A good example is a new Raspberry Pi OS (Raspbian) install.
RPi will lists the IP Addresses assigned to it when it first starts,
but that requires a monitor to be connected and I always run headless.
So how do I SSH into the RPi?

Other times I stumble upon a IP address of a device and I want to know what it is.
I typically can't SHH or telnet into it and poke around to discover it name or function.
How to I distinguish my Alexa from my Hue light bulb, even it I know its IP address?

If you have access to your WiFi Router/DHCP server on your network,
then you could logging in and getting the IP address from it.
This manual search can be laborious, dependent on the IP table refresh time of your router,
and worst of all, your unlikely not going to see any devices on any subnets you have created.

I want to exhaustively locate all devices automatically using a script.
I want the script to tell me the IP address, Ethernet MAC address of the device,
and provide some description of the device is.

# Network Discovery
Network discovery is the process that allows computers and devices to find one another when they are on the same network.
Sometimes call topology discovery, network discovery is the initial step system administrators
take when they want to map and monitor their network infrastructure.

With network discovery, a system will send out messages over the network looking for devices that are discoverable. Having network discovery enabled makes it easy for you to share network resources between the systems you want. But, it also makes it easier for an attacker to find these resources. Because of this, you might want network discovery turned on for some systems and off for other systems.

Network discovery will locate the devices that are connected to a network by applying different discovery protocols.
These protocols will discover and collect information about:

* Virtual computers and networks
* Hardware on a network, like switches, servers, firewalls, printers, and servers
* Software on a network, like applications and operating systems
* The logical and physical relationships between network assets

# Find all the networks
```bash
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.33.0    0.0.0.0         255.255.255.0   U     0      0        0 vboxnet1
```

# nmap
To do network discovery, you need nmap.
Issue a command like: `nmap -sP 192.168.1.0/24`
and it will do a network discovery on the subnet `192.168.1.0 - 192.168.1.255`
showing you names and IP addresses of all devices on that network.

* [An NMAP Primer](https://danielmiessler.com/study/nmap/)
* [Nmap Tutorial: Common Commands](https://www.networkcomputing.com/networking/nmap-tutorial-common-commands/520799832)
* [Running a quick NMAP scan to inventory my network](https://www.redhat.com/sysadmin/quick-nmap-inventory)
* [Beginner's Guide to Nmap](http://www.linux.com/learn/tutorials/290879-beginners-guide-to-nmap)
* [Top 30 Nmap Command Examples For Sys/Network Admins](http://www.cyberciti.biz/networking/nmap-command-examples-tutorials/)
* [Nmap Cheat Sheet](https://blogs.sans.org/pen-testing/files/2013/10/NmapCheatSheetv1.0.pdf)
* [Nmap Referasnce Guide](http://www.bandwidthco.com/whitepapers/netforensics/recon/nmap/NMAP%20Reference%20Guide.pdf)
* [NMAP - A Stealth Port Scanner](http://www.csc.villanova.edu/~nadi/csc8580/S11/nmap-tutorial.pdf)
* [Nmap Tutorial: Host Discovery](https://www.networkcomputing.com/network-security/nmap-tutorial-host-discovery/1390582372)
* http://www.cyberciti.biz/networking/nmap-command-examples-tutorials/

* [`zenmap`][91] is the official GUI for Nmap It is not to replace Nmap, but to make Nmap more useful.
[91]:https://nmap.org/book/zenmap.html#zenmap-purpose

# Address Resolution Protocol (ARP)
The ARP protocol can provide a mapping between a device's permanent MAC address
and their, often temporarily, assigned IP address.

## arp-scan

```bash
# arp-scan scans your network and lists devices
sudo arp-scan -I eth0 -l
sudo arp-scan -I wlan0 -l

# dump the ARP table after pinging all hosts
sudo nmap -sP 192.168.1.0/24
sudo arp -vn
```
# Zeroconf
If all your devices support Zeroconf, you might be able to do a device discovery this way.

# Avahi
`avahi-browse -alr` provides this information for other devices in the
local network on which avahi-daemon is running.


# Finding a device IP Address
**see the same section within "cheatsheet-ip-networking-commands.md"**

* [Finding a device IP Address](http://www.cnx-software.com/2010/10/25/finding-a-device-ip-address/)
* [ Who is on my wifi?](http://forum.backbox.org/general-support/who-is-on-my-wifi/)
* [Find What Devices Are Connected to Network In Ubuntu](http://itsfoss.com/how-to-find-what-devices-are-connected-to-network-in-ubuntu/)


# Finding a Duplicate IP Address
**see the same section within "cheatsheet-ip-networking-commands.md"**

# Finding Your Raspberry Pi
**see the same section within "cheatsheet-ip-networking-commands.md"**

# Is It a Physical Or Virtual Machine
You might be wondering whether you are working on a physical or virtual machine
but you may not have physical access.
However, it is possible to check if your Linux system is physical or virtual machine using couple of Linux utilities:
[How To Check If A Linux System Is Physical Or Virtual Machine](https://ostechnix.com/check-linux-system-physical-virtual-machine/)

```bash
# facter is a command line utility to collect and display a system's information
sudo facter | grep is_virtual

# if your using ansible to reach a remote system (appears to run facter)
ansible localhost -m setup | grep is_virtual   # doesn't seem to work
```

