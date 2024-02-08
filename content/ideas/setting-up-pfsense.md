<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----


# Home Network Best Practices
## Best Practices for pfSense Firewall Rules
* [Best Practices for pfSense Firewall Rules](https://hometechhacker.com/best-practices-for-pfsense-firewall-rules/)

### Network Segmentation
| Device         | Group             |
|----------------|-------------------|
| Work PC        | Work              |
| Smart TV       | Media             |
| Speakers       | Media             |
| Door Camera    | Operational       |
| Coffee Maker   | Operational       |
| File Server    | Personal-Wired    |
| Personal PC 1  | Personal-Wired    |
| Personal PC 2  | Personal-Wired    |
| Personal PC 3  | Personal-Wired    |
| Phone          | Personal-Wireless |
| Tablet         | Personal-Wireless |
| Water Sensors  | Internet of Things|

### Network VLANs
| Network         | VLAN / Nickname | Group             | Connectivity | # of Devices |
|-----------------|-----------------|-------------------|--------------|--------------|
| 192.168.1.0/24  | 1 / Wired       | Personal-Wired    | Wired        |       4      |
| 192.168.2.0/24  | 2 / Work        | Sensitive         | Wired        |       1      |
| 192.168.3.0/24  | 3 / Wireless    | Operational+Media | Wireless     |       4      |
| 192.168.4.0/24  | 4 / Guest       | Guest             | Wireless     |       ?      |




# Configure pfSense, Virtualized on Proxmox, Hosted on Protectli Vault

For pfSense, the specific RAM requirements can vary depending on the
network size, usage, and additional services running on pfSense.
The [minimum RAM requirements for pfSense on a home network is 2GB](https://robots.net/tech/how-much-ram-for-pfsense/).

* [Configure pfsense w/Protectli](https://www.youtube.com/watch?v=a70fUC8ZHTA)
* [How to Setup a Hardware Firewall Mini PC | pfSense 2.5 Beginners Guide](https://www.youtube.com/watch?v=qu7YR7e8xJA)

* [Best Practices for pfSense Firewall Rules](https://hometechhacker.com/best-practices-for-pfsense-firewall-rules/)
* [How To Install And Configure pfSense Firewall Pt1](https://www.youtube.com/watch?v=DVTNqzt9IFo)
* [How To Install And Configure pfSense Firewall Pt2](https://www.youtube.com/watch?v=HCIkg3nbPvM&t=2s)


# Vitrualize Your Firewall
* [How to Create Firewall Rules in pfSense](https://www.wundertech.net/how-to-create-firewall-rules-in-pfsense/)
* [What is Virtualization?](https://www.sunnyvalley.io/docs/network-basics/what-is-virtualization)
* [How to Build your Own Next-Generation Firewall (NGFW) at Home?](https://www.sunnyvalley.io/docs/network-security-tutorials/how-to-build-ngfw-for-home)


* [Home Network Setup - pfSense, VLANs, VPN, HAProxy, 10G, and more](https://www.youtube.com/watch?v=_cDEdjDGP8w)
* [How to Virtualize Your Home Router / Firewall Using pfSense](https://www.youtube.com/watch?v=hdoBQNI_Ab8)
* [Using Nginx Proxy Manager with pfSense, Proxmox, and Docker](https://www.youtube.com/watch?v=6aaSjwJhOog)
* [How to Virtualize Your Home Router / Firewall Using pfSense](https://www.youtube.com/watch?v=hdoBQNI_Ab8)

* [How to Upgrade pfSense the Right Way](https://hometechhacker.com/how-to-upgrade-pfsense/)

* [Protectli: Knowledge Base](https://protectli.com/kb/)
* [Protectli: pfSense® CE on the Vault](https://protectli.com/kb/how-to-install-pfsense-ce-2-4-on-the-vault-2/)
* [pfSense Tutorials](https://techexpert.tips/pfsense/)
* [The ultimate pfSense web configurator guide](https://www.comparitech.com/blog/vpn-privacy/setup-configure-pfsense/)
* [Install pfSense 2.5.2 Firewall](https://www.vdtutorials.com/install-pfsense-2-5-2-firewall/)
* [pfSense Firewall - pfSense Administration Full Course](https://www.youtube.com/watch?v=wv1qTYR3faQ)
* [5 Tips To Help Get The Most Out of pfSense](https://hometechhacker.com/5-tips-to-help-get-the-most-out-of-pfsense/#Tip_1_Get_notified_when_someone_connects_to_your_OpenVPN_server)




## pfSense
Your average off-the-shelf router manufacturer don't have any incentives in patching software bugs,
addressing performance problems or even serious security holes.
On the other hand,
Open Source operating systems such as pfSense are regularly updated
and are known to patch security issues promptly.
pfSense started in 2004, since then it grew to be the most well known and supported router/firewall platform,
and often ranked #1 when compared to other like products.
There are thousands of tutorials, forums, blogs and youtube videos
all over the internet that will be helpful if you get stuck on something.

pfSense can be installed on most commodity hardware, including old computers and embedded systems.
pfSense is typically configured and operated though a user-friendly web interface,
making administration easy even for users with limited networking knowledge. Generally,
one never needs to use terminal or edit config files to configure the router.
Even software updates can be run from the web UI.

>**NOTE:** The name pfSense is derives from the fact that the software
>uses the [OpenBSD][16] [packet-filtering tool, PF][17].

## Major Features of pfSense
When one thinks of pfSense, you typically focus on its firewall and router features,
but it is often configured as DHCP server, DNS server, WiFi access point,
VPN server, all running on the same hardware device.
pfSense also allows for installation of third party open source packages,
such as Snort or Squid through a built in Package Manager,
making it the default choice of many network administrators.

>**NOTE:** Gartner says that Next-Generation Firewall is ...
>Deep-packet inspection firewall that move beyond port/protocol inspection
>and blocking to add application-level inspection, intrusion prevention,
>and bring intelligence from outside the firewall.

pfSense is also often positioned as a Next-Generation Firewall.
You can load it's firewall with firewall packet filtering, load balancing,
intrusion detection system (IDS), intrusion prevention system (IPS),
VPN, DNS resolver, NetFlow collector, router, logging, VPN tools like Wireguard and OpenVPN.

pfSense is flexible by design.
It can be used on a small home router as well as run the entire network of a large corporation.
Nowadays, pfSense is often replacing expensive name brands in large corporate environments, not because it's free, but because it is feature rich and mature platform.

Hosting pfSense on Proxmox is an example of [Network Functions Virtualization (NFV)][33].
NFV is a network architecture concept that leverages the IT virtualization technologies
to virtualise entire classes of network node functions into building blocks that may connect,
or chain together, to create and deliver communication services.

Sources:

* [What is a Next-Generation Firewall (NGFW)?](https://www.sunnyvalley.io/docs/network-security-tutorials/next-generation-firewall)
* [TOP 5 BEST AND FREE NGFW OF ALL TIMES](https://syncbricks.com/top-5-best-free-ngfw-firewall/)
* [How to Build your Own Next-Generation Firewall (NGFW) at Home?](https://www.sunnyvalley.io/docs/network-security-tutorials/how-to-build-ngfw-for-home)
* [What Are The Best Open Source Firewalls?](https://www.sunnyvalley.io/docs/network-security-tutorials/best-open-source-firewalls)
* [your home router SUCKS!! (use pfSense instead)](https://www.youtube.com/watch?v=lUzSsX4T4WQ)
* [2021 Firewall Review, Feature Comparison and Recommendations](https://www.youtube.com/watch?v=ZI7zt1Vf8vE)
* [2020 Getting started with pfsense 2.4 Tutorial: Network Setup, VLANs, Features & Packages](https://www.youtube.com/watch?v=fsdm5uc_LsU)
* [Using Nginx Proxy Manager with pfSense, Proxmox, and Docker](https://www.youtube.com/watch?v=6aaSjwJhOog)

# Security
* [11 Home Network Security Tips You Need To Implement Now](https://hometechhacker.com/9-home-network-security-tips/)
* [Proxmox: Potect your server with fail2ban](https://devopstales.github.io/linux/proxmox-fail2ban/)
* [Secure Your Self Hosting with Fail2Ban + Nginx Proxy Manager + CloudFlare](https://www.youtube.com/watch?v=Ha8NIAOsNvo)
* [Fail2ban Tutorial | How to Secure Your Server](https://www.youtube.com/watch?v=kgdoVeyoO2E)
* [Ubuntu Server 18.04 Administration Guide Part 10 - Securing Applications with Fail2ban](https://www.youtube.com/watch?v=sboMT8N4ffA)
* [Additional Self-Hosted Security with Authelia on NGINX Proxy Manager](https://www.youtube.com/watch?v=4UKOh3ssQSU)

### Wireguard
* [Wireguard with pfSense CE 2.5.2+](https://www.paolotagliaferri.com/wireguard-vpn-tunnel-with-pfsense-ce-2-5-2-package/)
* [Pi-Hosted: Beginners Guide to WireGuard Docker and Installing Pi-OS 64bit](https://www.youtube.com/watch?v=yB_jAumIxOg&list=PL846hFPMqg3jwkxcScD1xw2bKXrJVvarc&index=15)

#### Tailscale
Tailscale is an SaaS product that scales from individual users to entire enterprises, and it's based on the Wireguard VPN protocol.
Instead of running a single VPN server that acts as an entry and exit point for your networks, Tailscale creates a decentralized mesh network known as a tailnet. This tailnet is coordinated by a central control server, hosted by Tailscale, which is responsible for peer discovery within a tailnet (such as sharing IP addresses and public keys).

This decentralized mesh network allows your devices to effectively exist on their own private VPN, whether they're in your home or not. This means your phone, laptop, and home server can all easily connect to each other without having to run a dedicated VPN server in your home.

* [How to set up a powerful home VPN with Tailscale](https://www.xda-developers.com/how-setup-powerful-tailscale/#what-is-tailscale)



-----



https://social.dnsmadeeasy.com/blog/understanding-dns-forwarding/
* [Linux: 25 Iptables Netfilter Firewall Examples For New SysAdmins](https://www.cyberciti.biz/tips/linux-iptables-examples.html)
* [A Deep Dive into Iptables and Netfilter Architecture](https://www.digitalocean.com/community/tutorials/a-deep-dive-into-iptables-and-netfilter-architecture)


# iptables and ufw
Linux comes with a host based [firewall][90] called [`netfilter`][91]
(or sometimes called `iptables` after the tool used to manage netfilter).
`netfilter` is the framework in the Linux kernel,
which implements the rule and filters provided by the user,
through an interface available to user called `iptables`.

Ubuntu has `iptables` but also comes with an "**U**ncomplicated **F**ire**W**all" called [`ufw`][92]
and is considered the default firewall configuration tool for Ubuntu,
but default `ufw` is disabled.
Its a much simpler front end for `iptables` is [`ufw` (Uncomplicated Firewall)][94].
The article "[How To Setup a Firewall with UFW on an Ubuntu and Debian Cloud Server][95]"
gives a good introductory tutorial on how to use `ufw`.

There is also a graphical version [`gufw`][93] can be installed with `sudo apt-get install gufw`.
Developed to ease `iptables` firewall configuration,
`ufw` provides a user friendly way to create an IPv4 or IPv6 host-based firewall.

`ufw` should be installed by default on Ubuntu.
If it has been uninstalled for some reason, you can install it with `sudo apt install ufw`.

>**NOTE:** When working with firewalls,
>take care not to lock yourself out of your own server by blocking SSH traffic
>(port 22, by default).
>If you lose access due to your firewall settings,
>you may need to connect to it via the console to fix your access.
>Once you are connected via the console, you can change your firewall rules to allow SSH access.
>If your currently saved firewall rules allow SSH access, another method is to reboot your system.

Sources:
* [How to Set Up a Firewall with UFW on Ubuntu](https://www.sunnyvalley.io/docs/network-security-tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu)
* [How To Set Up a Firewall with UFW on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-20-04)
* [UFW Essentials: Common Firewall Rules and Commands](https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands)
* [How to Set Up a Firewall with UFW on Ubuntu 20.04](https://linuxize.com/post/how-to-setup-a-firewall-with-ufw-on-ubuntu-20-04/)


# Install Google Chrome
 Installing Google Chrome via the Google repository so your system will
 automatically keep Google Chrome up to date.

```bash
# do an upgrade
apt-get update && apt-get -y upgrade

# load google chrome browser
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
apt install ./google-chrome-stable_current_amd64.deb

# clean up
mv ./google-chrome-stable_current_amd64.deb /tmp

# to use google chrome via the commandline
google-chrome
```


----



# Install pfSense
Let's get pfSense running as a virtual machine using the hypervisor Proxmox Virtual Environment (VE)
on the Protectli Vault FW4B J3160 hardware.

I **will not** cover here:

* How to install Proxmox on the Protectli Vault but you can find that information ..........
* How to enable the Protectli Vaults optional ports in pfSense,
but you can find that information [here][AA].

>**NOTE:** The typical configuration is a host with at least 2 NICs
>but you can get by with a single network interface.
>Checkout this article
>[Converting single NIC mini-pc into pfSense router/firewall by using virtual LAN configuration on a managed switch][29]
>to see how this is done.

[AA]:https://protectli.com/kb/pfsense-optional-port-configuration/
[BB]:
[CC]:


* [your home router SUCKS!! (use pfSense instead)](https://www.youtube.com/watch?v=lUzSsX4T4WQ)
* [Virtualizing pfSense with Proxmox® VE](https://docs.netgate.com/pfsense/en/latest/recipes/virtualize-proxmox-ve.html)
* [How to Install pfSense Start to Finish!](https://www.youtube.com/watch?v=CmEYf1W3EqQ)
* [How to Virtualize Your Home Router / Firewall Using pfSense](https://www.youtube.com/watch?v=hdoBQNI_Ab8&t=82s)
* [pfSense® Optional Port Configuration](https://protectli.com/kb/pfsense-optional-port-configuration/)
* [pfSense®CE Configuration Recommendations](https://protectli.com/kb/pfsense-configuration-recommendations/)
* [How to Install pfSense on Proxmox](https://www.wundertech.net/how-to-install-pfsense-on-proxmox/)

## Virtualising pfSense on Proxmox

* [5 Tips To Help Get The Most Out of pfSense](https://hometechhacker.com/5-tips-to-help-get-the-most-out-of-pfsense/)
* [Installing pfsense in Proxmox](https://server.vpnwp.com/proxmox/installing-pfsense-in-proxmox/)
* [How to Virtualize Your Home Router / Firewall Using pfSense](https://www.youtube.com/watch?v=hdoBQNI_Ab8)
* [How to Setup a Hardware Firewall Mini PC | pfSense 2.5 Beginners Guide](https://www.youtube.com/watch?v=qu7YR7e8xJA)
* [Virtualizing with Proxmox® VE](https://docs.netgate.com/pfsense/en/latest/recipes/virtualize-proxmox-ve.html)
* [Installing pfSense firewall on my virtual Proxmox machine to secure my VPS](https://www.youtube.com/watch?v=yBcM70NCyfg)

* [Home Network Setup - pfSense, VLANs, VPN, HAProxy, 10G, and more](https://www.youtube.com/watch?v=_cDEdjDGP8w)
* [SSL Encryption on Your Home Server the SIMPLE WAY - Cloudflare, pfSense, HAProxy, ACME https setup](https://www.youtube.com/watch?v=cB6oKJjr4Ls)
* [Using Nginx Proxy Manager with pfSense, Proxmox, and Docker](https://www.youtube.com/watch?v=6aaSjwJhOog&t=172s)
* [you need to learn Load Balancing RIGHT NOW!! (and put one in your home network!)](https://www.youtube.com/watch?v=LlbTSfc4biw)

## Pass-through PCIe NICs with Proxmox
[PCI passthrough][31] gives virtual machines direct access to the hardware.
This enables VMs on the same system to have isolated hardware access.
This means performance is broadly identical to if you were using that hardware on bare metal.
There are a few key types of devices that are usually worth considering passing through,
such as SATA controllers, network interfaces and graphics cards.

* [LINUX Unplugged • Episode 308 The One About GPU Passthrough](https://share.fireside.fm/episode/RUkczH-V+9ZRzR3sB)
* [How to Pass-through PCIe NICs with Proxmox VE on Intel and AMD](https://www.servethehome.com/how-to-pass-through-pcie-nics-with-proxmox-ve-on-intel-and-amd/)
* [The Ultimate Beginner's Guide to GPU Passthrough (Proxmox, Windows 10)](https://www.reddit.com/r/homelab/comments/b5xpua/the_ultimate_beginners_guide_to_gpu_passthrough/)

# Bridge Mode
Bridge Mode is the perfect thing that you can get to enjoy networking over multiple devices. It disables the NAT feature and allows the router to work independently as the DHCP server.  This way, you can not only connect two routers, but the number gets unlimited.

The IP Passthrough feature allows a single PC on the LAN to have the Router's public address assigned to it.
IP Passthrough mode shares or "passes" the Internet providers assigned IP address to a single LAN client device connected to the router.

# Double NAT
If you use FIOS TV, you still need the G3100 to be doling out IPs to the set top boxes, so do NOT turn off DHCP. Yes, this means double NAT, but this is a small price to pay for working TV features. If you don't subscribe to FIOS TV, you can remove G3100 entirely from your setup.

 NAT manages the connectivity between the public Internet and your private network, and either UPnP or manual port forwarding ensures that incoming connections from the Internet (i.e. remote access requests) find their way through NAT to the appropriate private network PC or other device.
 UPnP is enabled on my FiOS router.

when NAT is being performed not just on your router but also on another device that’s connected in front of it, you’ve got double NAT. In this case, the public/private network boundary doesn’t exist on your router — it’s on the other device, which means that both the WAN and LAN sides of your router are private networks. The upshot of this is that any UPnP and/or port forwarding you enable on your router is for naught, because incoming remote access requests never make it that far — they arrive at the public IP address on the other device, where they’re promptly discarded.

* [Network Address Translation](https://www.youtube.com/watch?v=BgtORKB0lls&list=PLIFyRwBY_4bQ7tJvbLA9A0v8Fq9l-H923)
* [NAT Terminology](https://www.practicalnetworking.net/series/nat/nat-terminology/)
* [NAT Terminology Disambiguation](https://www.practicalnetworking.net/series/nat/nat-terminology-disambiguation/)

## Work Around for Double NAT
The very first thing to do is to check if you have a Double NAT situation.
To check for double NAT on your network, log into your router and look up the IP address of its WAN port. If you see an address in the 10.x.x.x or 192.168.x.x range (both of which are private) it means that the device your router’s WAN port connects to is doing NAT, and hence, you’re dealing with double NAT.

Given that you have a Double NAT, and it is disruptive,
there are a options available to correct, or circumvent, a double NAT situation.

* **Bridge Mode -** If the culprit is your ISP-supplied equipment, you may be able to access the device’s configuration interface via a browser and set it up to work in “bridge” mode. This will disable NAT on the device and essentially make it transparent on the network so your router will receive the public IP address and perform the NAT function on its own.
**NOTE:** If, on the other hand, your double NAT is being caused by a third-party piece of equipment that needs to be connected in front of your router (e.g. VoIP adapters usually require/recommend this for quality-of-service reasons), eliminating double NAT really isn’t an option.
* **Port Forwarding -** You can compensate for double NAT is to set up separate port forwarding rules on each device so that incoming traffic is shepherded through both layers of NAT. So for example, on the first NAT device (the one closest to your Internet connection) forward the port(s) you need to the IP address of your router’s WAN port. Then on your router, forward the same port(s) to the address of the device you need to reach.
* **DMZ -** If you have a lot of ports to forward, doing them individually can get a bit cumbersome, so a simpler method is to configure the first NAT device to make your router’s IP address the DMZ. This will hustle all incoming traffic through the first layer of NAT no questions asked, but when it hits your router it will be filtered or forwarded as appropriate.

* [Double Trouble: How to Deal with Double NAT on Your Network](https://www.practicallynetworked.com/fixing-double-nat/)
* [What Is Double NAT and How to Fix It on a Network](https://helpdeskgeek.com/networking/what-is-double-nat-and-how-to-fix-it-on-a-network/)
* [What Is Bridge Mode And How It Can Be Useful For Me?](https://techietide.com/what-is-bridge-mode-and-how-it-can-be-useful-for-me/)
* [What are bridge and passthrough modes?](https://www.iplocation.net/bridge-vs-passthrough)
* [FiOS G1100 Bridge](https://www.flyn.org/notes/g1100-bridge/)
* [Verizon FiOS G1100 Bridge Mode: How to Set it Up](https://internet-access-guide.com/g1100-bridge-mode/)

# when Locked Out of pfSense
What if you find yourself locked out of pfSense?
This sounds like a nightmare give that pfSense is such a critical part of home network,
but there are a number of ways to regain control.
Check out the Netgate documentation "[Troubleshooting Access when Locked Out of the Firewall][30]".



------




### Step 1: Physical Setup - DONE
To get things started,
I want to establish a temporary configuration which will enable me to experiment until
I'm confident about how to install the Protectli Vault / Proxmox / pfSense
into my home LAN as my router/firewall.
The Protectli Vault WAN port will be plugged to my current home LAN,
using my current FiOS router as my gateway to the Internet.
I will connect a TP-Link TL-SG108E switch into the Protectli Vault LAN port
to establish a network on this switch using pfSense.

This configuration will have a double NAT and has little value other than experimentation
but should not disrupt my current FiOS services or require me to mess with my current router,
and therefore avoiding breaking things.
It will also allow me to preconfigure the pfSense with a setup that I can easily rip out my
current FiOS router and replace it with the preconfigure pfSense.

pfSense will do the following functions for me:

* DHCP
* Customize Firewall
* VPN
* VLAN
* Ad Blocking
* Reverse Proxy - HA Proxy
* Custom Port Forwarding
* Custom DNS
* Certificate Authority
* Captive Portal



```
============= Router Setup =============

       Internet
         |
         |
       FiOS Router (ISP Public IP Address)
       Subnet 192.168.1.0/24
        /  \
       /    \
      /      \
     /        \
    |       Proxmox (192.168.1.202/24) within Protectli Vault
***************************************
*   |                 Public Network  *
*   |                                 *
* pfSense (192.168.1.X/24)            *
* Subnet 192.168.2.0/24               *
*     |     |                         *
*.....................................*
*     |     |        Private Network  *
*     |     |                         *
*     |   Xubuntu (192.168.2.X/24)    *
*     |                               *
***************************************
      |
    TP-Link Switch (192.168.2.X/24)


          Key
-------------------------
X  DHCP Issued IP Address
```

This design will ultimately be migrated to this configuration:
Take your time here, things can get messy really fast if you don’t take your time
and think things through as you go.
Plan it out in advance as well, walking through each step,
and considering anything that might become an issue.

from  - https://www.dlford.io/expanding-your-home-network-how-to-home-lab-part-9/
I would start by plugging the pfSense device into the modem, then your switch into the LAN port on pfSense, and everything else on the network except Proxmox into the switch. Make sure everything is working as expected before moving Proxmox over.

Your WiFi router should be plugged into either the LAN port on pfSense, or the switch that is plugged into the LAN port on pfSense, and should be put in DHCP pass through mode. If it does not have a DCHP pass through mode, just don’t use the WAN port on the WiFi router, plug the uplink cable into one of the LAN ports instead.

DHCP Passthrough mode: disables DHCP server on the router and assumes there is a DHCP server somewhere else in the network (pfSense), should also disable NAT or have that option.

Next, you may need to change the IP address and gateway for the Proxmox host to fit into the pfSense network or VLAN you created, this can be done at Host > System > Network > vmbr0, don’t forget to check the “VLAN aware” box if you’ll be using VLANs. Save the changes, and shutdown Proxmox before moving on.

If you don’t need to change the IP address of Proxmox or enable VLANs, you can just move the network cable to your switch now. Boot up Proxmox if needed and again, make sure it’s working, port forwards won’t be working yet, but you should have access to the Proxmox admin page.

Now we can go to each VM, under Hardware, and change the network device to use the main (vmbr0) interface (add your VLAN here if you’re using them as well), and shut down the pfSense VM in Proxmox. Check that the VMs are getting the expected IP addresses, and are accessible by IP address.

Finally, remove the domain overrides in your workstations hosts file, these should now be routable on the network because pfSense is managing DNS for the whole network. As for the hosts or domains that are behind a reverse proxy such as NGINX, head to Services > DNS Resolver on your physical pfSense host, and add a host override for each domain that points to the reverse proxy, and they should be accessible without any manipulation of the hosts file on your workstation.

```
============= Router Setup =============

       Internet
         |
         |
       FiOS Router (ISP Public IP Address)
       Subnet 192.168.1.0/24
        /  \
       /    \
      /      \
     /        \
    |       Proxmox (192.168.1.202/24) within Protectli Vault
***************************************
*   |                 Public Network  *
*   |                                 *
* pfSense (192.168.1.X/24)            *
* Subnet 192.168.2.0/24               *
*     |     |                         *
*.....................................*
*     |     |        Private Network  *
*     |     |                         *
*     |   Xubuntu (192.168.2.X/24)    *
*     |                               *
***************************************
      |
    TP-Link Switch (192.168.2.X/24)


          Key
-------------------------
X  DHCP Issued IP Address
```

```
============= VLAN Setup =============

* Guest - 192.168.1.1/24
    * guest devices, TV, Chromecast,
* Personal
    * desktop, cluster, all admin for network
* IoT
    IoT devices/hubs, cameras, Home Assistent, synology

```

This experimental configuration of pfSense is illustrated in the figure above.
Once Proxmox is installed on the Protectli Vault,
the high steps I used to establish this configuration where as follows:

1. Physical establish Protectli Vault(with Proxmox installed ), and TP-Link TL-SG108E switch
2. Setup Proxmox networking with pfSense facing the public network
and pfSense supporting a private network within Proxmox and on the switch
3. Install pfSense and a test VM on the private network within Proxmox
4. Configure pfSense to support a private network much like what you need to replace your FiOS router
5. To move do the FiOS router replacement, you should be able to just change the
pfSense LAN IP network from `192.168.2.0` to `192.168.1.0`.

>**NOTE:** In a typical pfSense implementation,
>you have two interfaces/NICs; one for WAN and the other for LAN.
>pfSense can work with a hardware box that has a single NIC if you
>also include a managed switch (aka switch supporting VLAN) in your network design.
>Check out this video: "[Install & Configure Pfsense Using 1 Nic & Vlans][06]".

I also want to configure the Protectli Vault / pfSense envirnment
so that it configures properly when the Vault is booted up.
Do do this, I need to control the bootup sequence of the VMs and container used.
You can do this via the **General** tab on **Create VM**.
Specifically the items in the **Advanced Box** at the bottom where you can establish auto-start settings:

* **Start at boot:** Auto-start this VM when the Proxmox host boots up
* **Start/Shutdown order:** At boot time, the lower numbered VMs will start up first,
and on shutdown/reboot the higher numbered VMs will shut down first.
Its best pratice to start these in increments of 10 so you can slip new VMs in wherever they should go later.
There is also nothing wrong with using the same number for multiple VMs,
they will just be started/shut down at the same time.
* **Startup delay:** The number of seconds to wait after booting the VM before booting the next VM.
* **Shutdown timeout:** The number of seconds to wait,
during a shutdown of the Proxmox host, for a VM to finish shutting down.
This prevents the system from hanging if a VM refuses to shut down.
You can leave it blank to use the default setting of 5 minutes.

Sources

* To setup pfSense, by inlarge, I followed the recommendations of
[NetworkChuck][01], [H2DC][02], [Dan Ford][03], and of course [NetGate][04].

* [your home router SUCKS!! (use pfSense instead)][01]
* [Virtualizing An Internal Network With pfSense In ProxMox][02]
* [How to Home Lab: Part 3 - Host an Intranet Site with pfSense and NAT][03]
* [Virtualizing with Proxmox® VE][04]

#### Step 2: Download pfSense to Proxmox on Protectli Vault - DONE
To create virtual machine contain pfSense,
you'll need to have moved an ISO image to the Proxmox file system.
You can do this via
**Datacenter** > **local** > **ISO Images** > **Upload** or **Download from URL**.
You'll find the required URL for pfSense-CE Version 2.6.0 here:
[pfSense-CE-2.6.0-RELEASE-amd64.iso][05].

#### Step 3: Setup Proxmox Networking - DONE
Now we will building the pfSense software on a virtual machine within Proxmox.
We must create two Linux Bridges on Proxmox VE, which will be used for the WAN and LAN ports.

First, select the Proxmox host (`pve-1` in my case) from the **Server View**.
Navigate to **Datacenter** > **pve-1** > **System** > **Network**.
We'll use the default bridge `vmbr0` so select its line and click **Edit**.
It needs to read:

* Name: `vmbr0`
* IPv4/CIDR: `192.168.1.202/24`
* Gateway (IPv4): `192.168.1.1`
* Bridge port: `enp1s0`
* Comment: bridge for Proxmox and anything you expose to WAN interface

>**NOTE:** Since your using the WAN port to reach the Proxmox GUI,
>most likely the Linux Bridge for `enp1s0` is already active.

For the second network, we'll create a private network,
using the **Create** button, to looking like this:

* Name: `vmbr1`
* IPv4/CIDR: <blank>
* Gateway (IPv4): <blank>
* Bridge port: `enp1s1`
* Comment: LAN virtual private network and port to hardware switch

So interface `enp1s0` is the WAN port and interface `enp2s0` is the LAN port on the Protectli Vault.
At this moment, the IP address `192.168.1.202` is the static address to reach Proxmox GUI (`192.168.1.202:8006`)
and also used to reach the Internet via the gateway at `192.168.1.1`.
Ultimately, via the powers of Proxmox virtual networking,
pfSense will use this same WAN interface to get an IP address via DHCP,
to support the WAN interface for pfSense.

Proxmox requires a reboot if the interfaces are not marked Active.
Do the reboot now just to make sure all is well.

>**NOTE:** The bridge ports `enp1s0` and `esp1s1` are internal Proxmox port numbers.
>For matching external NIC port numbers to internal OS designations,
>see "[NIC port numbering and naming][11]".

#### Step 4: Create VM for pfSense - DONE
Within the **Server View** > **pve-1**,
click **Create VM** from the top right section to display the new virtual machine wizard.
Enter the following:

* Navigate to **General** >  **Name** and enter `pfSense`.
Check **Start at boot**, **Start/Shutdown order** is 10, and **Startup delay** is 30.
* Navigate to **OS** > **ISO image** and select the pfSense image,
and **Type** is Other (pfSense's OS is FreeBSD).
* Navigate to **System** and accept all the defaults.
* Navigate to **Disk** > **Disk size (GiB)** enter 20 and check **Discard** box
(This will free up space from files deleted on the VM guest.
If unchecked the free space will be available to the VM guest but still marked
as used on the Proxmox host and storage device)
* Navigate to **CPU** > **Sockets** is 1, **Cores** should be 2, and **CPU unit** 2048.
(CPU units give each VM a priority for CPU time,
so VMs that are less critical can just use the default value of 1024,
and critical VMs should get a higher value so they get priority if there is a high demand for CPU usage.)
* Navigate to **Memory** > **Memory (MiB)** enter 512MiB
512MiB should be fine, you can always add more later if needed).
* Navigate to **Network** > **vmbr0** > **Model** > **VirtIO (paravirtualized)**.
* Navigate to **Confirm** > **Finish**.

The interface `vmbr0` will be your WAN for pfSense and now we will setup the LAN.
Navigate to **Datacenter** > **pve-1** > **pfSense** > **Hardware** >
select button **Add** > select **Network Device**.
Set **Bridge** to `vmbr1` and **Model** to VirtIO (paravirtualized).

#### Step 5: Start the VM and Install pfSense - DONE
Navigate to **Datacenter** > **pve-1** > **pfSense**.
Next click **Console** and click then **Start** button at the top menu bar.
As the install proceeds, you should select these options:

* Accept
* Install
* Continue
* Auto (USF) BIOS
* No (system modifications)
* Reboot

After rebooting the VM, you’ll be asked for the following input before bootup completes:

* Should VLANs be set up now?: n for no
* Enter the WAN interface: vtnet0
* Enter the LAN interface: vtnet1
* Do you want to proceed?: b for no

Once the configuration is completed,
it shows the WAN as having vtnet0 "v4/DHCP4: 192.168.1.12/24"
and LAN as having vtnet1: "v4/DHCP4: 192.168.1.1/24".

#### Step 6: pfSense Configuration Modification for Convenience - DONE
At this this point,
the pfSense web interface is accessible from the LAN network at
`https://192.168.1.1` which happens to be the same as my home network FiOS router,
and the pfSense router is supporting only static IP.
To avoid confusion with you FiOS network, lets change the LAN subnet to `192.168.2.0` and use DHCP.
Using the pfSense **Console**,
select option **2** > **2** >  `192.168.2.1/24` > <Enter> > <Enter> > **n** >
(**NOTE:** Don't enter `192.168.2.0/24` since your effectively entering the browser UI for pfSense and **0** is reserved.)
start address is `192.168.2.10` > end address is `192.168.2.199`.
When asked if you want to revert to HTTP enter **n**.
(**NOTE:** If you enter "yes",
the browser interface could get confused and stop working.
I saw this when using Firefox.)

Now we can do a test via the Proxmox private network you established earlier using the Xubuntu VM.
Before doing this,
it would be wise to restart the Xubuntu VM to make sure its IP is initiated via pfSense's DHCP.
The use the Xubuntu to do the following:

```bash
# ping pfsense from private network
# ping pfsense via the wan interface will get no response
ping 192.168.2.1

# pull up admin website
firefox 192.168.2.1

# check if routing is working on pfsense
# this will not work since DNS hasn't been setup on pfsense
firefox google.com
```

>**NOTE:** If you for whatever reason locked yourself out of the pfSense admin GUI,
>or need access from a IP outside your,
>you can do this via the WAN interface but you must turn off firewall rules first.
>To do this use Proxmox **Console** for pfSense, enter 8 and then `pfctl -d`
>This will turn off the firewall rules blocking access via WAN (`192.168.1.12` on your home network).
>Use `pfctl -e` to turn firewall rules back on.

#### Step X: Disable `admin` for Increased Security
The fact that that the administrative interface of pfSense is know as `admin` is a security issue.
Best to provide a new name a make it a bit harder for hackers to compromise your system.

You can setup a new administrative login via
**System** > **User Manager**.
Here you can add a new user with administrative rights,
and disable the default `admin` user login.

#### Step 7: Create Xubuntu VM for Testing - DONE
We'll want to test the install of pfSense, and to do that,
set up Xubuntu instances on the private network, aka the `vmbr1` bridge.

Within the **Server View** > **pve-1**,
click **Create VM** from the top right section to display the new virtual machine wizard.
Enter the following:

* Navigate to **General** >  **Name** and enter `xubuntu-1`.
* Navigate to **OS** > **ISO image** and select the Xubuntu image.
* Navigate to **System** > **Graphic card** > **SPICE**.
* Navigate to **Disk** > **Bus/Device** > **VirtIO Block** > **Disk size (GiB)** enter 20.
* Navigate to **CPU** > **Sockets** > **2**.
* Navigate to **CPU** > **Cores** > **2**.
* Navigate to **Memory** > **Memory (MiB)** enter 2048.
* Navigate to **Network** > **vmbr1** > **Model** > **VirtIO (paravirtualized)**.
* Navigate to **Confirm** > **Finish**.

We'll come back later to this xubuntu instance and do an package repository update
and install tools.
Can't do it at this moment since the pfSense router isn't configrued with DNS yet.

#### Step 8: Configure pfSense via Wizard - DONE
From a web browser on the Xubuntu VM,
visit `https://192.168.1.1` and you’ll get the invalid SSL Certificate page.
Choose **Advanced**, accept the risk and continue,
or proceed to the website depending on which browser you are using.
Then log into pfSense with the default credentials:
username: **admin** and password: **pfsense**.
You will be immediately dropped into a wizard and you should enter the following information:

* Step 1 of 9: You maybe prompted to change your password. Don't since you'll get another chance to do this later.
* Step 2 of 9: Set hostname to `pfSense` and domain to `jeffskinnerbox.me`
DNS servers set to `1.1.1.1` and `1.0.0.1` (i.e. Cloudflare DNS)
Uncheck the **Override DNS**.
* Step 3 of 9: Update the **Timezone** field but the **Time server hostname** is fine.
* Step 4 of 9: Uncheck **Block RFC1918 Private Network** since, in your current physical configuration,
you WAN is pulling a private IP address from you home router.
You would check this for when you replace your FiOS router with the Protectli Vault / pfSense.
* Step 5 of 9: No changes needed.
* Step 6 of 9: Change your user `admin` password.
* Step 7 of 9: Click the **Reload** button
* Step 8 of 9: No changes needed.
* Step 9 of 9: Click the **Finish** button

At this point, you should see the pfSense Status / Dashboard.
To check again if the pfSense router is doing the basic job of
giving your private network Xubuntu access to the Internet,
open an another browser tab
and see if you can hit some Internet site like you did in the previous step.

```bash
# pull up admin website
firefox 192.168.2.1

# check if routing is working on pfsense
firefox google.com
```

If you have problems connecting with pfSense via the Xubuntu VM,
try refreshing the DHPC supplied IP address on the Xubuntu VM via:

```bash
# release your current ip address
sudo dhclient -r

# get a new ip address
sudo dhclient
```

#### Step 9: Configure Xubuntu to Use SPICE - DONE
Now lets make the Xubuntu environment a little more friendly for testing.
For example, I prefer the Google Chrome browser and I would like to install it.
A few simple (but lengthy) Shell commands can do the trick, but there is a problem.
You can't cut & paste these length commands into the Proxmox [noVNC][08] Console screen
but [SPICE][09] does support cut & paste.

>**NOTE:** There is another potential work around.
>You can use [Byobu][12] and its [terminal sharing feature][13]
>([Boybu Quick Start Guide][10]).
>Never the less, SPICE is an easier fix.

SPICE is a suite of tools for interfacing with desktop-oriented Virtual Machines.
To use SPICE, you'll need the client running on your desktop computer.
To install the client on your desktop computer:

```bash
# install on your desktop computer the spice client
sudo apt-get install qemu-kvm virt-viewer
```

Just in case during the install of the xubuntu VM,
you may have not enabled SPICE but you can do it via
**Datacenter** > **pve-1** > **xubuntu** > **Hardware** > **Display** and click button **Edit**.
Select the item **SPICE** and 32 MiB.
Now restart Proxmox via **Datacenter** > **pve-1** > **Shutdown** button.

**Datacenter** > **pve-1** > mouse right button click on **xubuntu** and select **Console**.
A pop-up window will appear to download the spice configuration file `pve-spice.vv`.
Download it and do the following
(**NOTE:** This will work if your using Google Chrome or Microsoft Explore as your browser):

* Using the File Manager, change directory to `~/Downloads`
* Double click on `pve-spice.vv` and a SPICE session should appear in a pop-up window.
* You can now use SPICE to do your cut & paste tasks.

Now do the following to install Google Chrome:

```bash
# do an upgrade
sudo apt-get -y upgrade

# load google chrome browser
echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" | sudo tee --append /etc/apt/sources.list.d/google-chrome.list> /dev/null
wget -P ~/.ssh/ https://dl.google.com/linux/linux_signing_key.pub
sudo apt-key add ~/.ssh/linux_signing_key.pub
sudo apt-get -y update
sudo apt-get -y install google-chrome-stable

# to use google chrome via the commandline
google-chrome
```

Some other useful tools are:

```bash
# networking tools
sudo apt-get -y install net-tools arp-scan netdiscover
```

* [Desktop Virtualization using SPICE on Linux](https://www.youtube.com/watch?v=fhW3ddJIWTs)
* [SPICE Project](https://www.spice-space.org/)
* [Proxmox SPICE](https://pve.proxmox.com/wiki/SPICE)
* [Proxmox SPICE console](https://www.networkshinobi.com/proxmox-spice-console/)



-------



# pfSense Configuration - DONE but you need to review these youtube links
Now that we have completed the niital install of pfSense,
we have a working / foundational version of pfSense operating.
Now we'll configure it to our specific needs.

* [PfSense Advanced Configuration - VM Setup, Virtual IPs, Alias, NAT, Rules][19]
* [2020 Getting started with pfsense 2.4 Tutorial: Network Setup, VLANs, Features & Packages][20]

#### Step 1: Upgrade pfSense - DONE
You can upgrade your pfSense software from the **Status** > **Dashboard** screen.
You find the button within the "System Information" widget in the "Version" section.

* [How to Upgrade pfSense the Right Way](https://hometechhacker.com/how-to-upgrade-pfsense/)

#### Step 2: Add Widgets to Status / Dashboard - DONE
You can customize the pfSense Dashboard display by adding (and deleting) the tiled widgets.
You'll see a menu of all the widgets by clicking the red "+" on the **Availible Widgets** widget.

* Delete the widgets **Netgate Services and Support**
* Add the widgets **Interface Statistics**, **Traffic Graphs**, **Services Status**

#### Step 3: Enable Cryptographic Acceleration - DONE but Dashboard didn't update check your Proxmox VM seetings
Cryptographic acceleration is available on the Protectli Vault platform,
specifically Intel [Advanced Encryption Standard (AES) or New Instructions (AES-NI)][14].
AES-NI is a new encryption instruction set,
baked right into CPU that dramatically speeds up cryptography tasks
such as encryption/decryption for VPN or SSL
([What is AES 256, Why is AES-NI different and why should you care][15]).

pfSense lists the AES-NI as a supported option for crypto acceleration.
pfSense will use it for OpenVPN and IPsec if you tell it to.
There's a configuration setting for it.

[To enable AES-NI on the Protectli Vault][18], go to
**System** > **Advanced** > **Miscellaneous** .
Then scroll down to the "Cryptographic & Thermal Hardware" section.
Where it says "Cryptographic Hardware", select **AES-NI and BSD Crypto Device**.
The click **Save** at the bottom of the page.

Reboot Proxmox and check **Status** > **Dashboard**.
If all is well, you should see "AES-NI CPU Crypto: Yes".

While your at it,
you can enable thermal monitoring,
display thermal sensors on the dashboard,
and enable PowerD.
The webpage "[pfSense®CE Configuration Recommendations][18]"
shows you how to do this.

* [pfSense®CE Configuration Recommendations][18]
* [Cryptographic Accelerator Support](https://docs.netgate.com/pfsense/en/latest/hardware/cryptographic-accelerators.html)

#### Step 4: Disable Hardware Checksums - DONE
When pfSense is virtualized on Proxmox,
it is [strongly urged][32] to disable Hardware Checksum Offloading
when using VirtIO interfaces in Proxmox.

To disable hardware checksum offload:

* Navigate to **System** > **Advanced**, **Networking** tab
* Locate the **Networking Interfaces** section
* Check Disable hardware checksum offload
* Click **Save** at the bottom of the page.

Reboot the firewall from **Diagnostics** > **Reboot** or the console menu.

#### Step X: Update pfSense OS - DONE
You'll want to keep pfSense updated to the most current release.
You can do an upgrade from the pfSense console screen (via menu item **13**)
or via the browser interface (`192.168.2.1:80`).

**System** > **Update**




-------




# Configure WiFi Access Point For Home Network
>**NOTE:** You can also use WiFi as your WAN interface.
>See the video "[pfsense Wireless WAN Setup][21]".

* [User Guide: Omada SDN Controller](https://static.tp-link.com/upload/software/2022/202201/20220121/1910013128-Omada%20SDN%20Controller%20User%20Guide%205.0%20(windows&linux).pdf)
* [7 Settings to Configure on Your WI-FI Router Now](https://hometechhacker.com/7-settings-to-configure-on-your-wi-fi-router-now/)

#### Step X: Install Ubuntu Container on Protectli Vault / Proxmox - DONE
Requirements:
* 64-bit Ubuntu 18.04 or later
* 1MB of RAM memory
* 10GB of disk space

First, do a `pveam update` in the Proxmox **Shell** to download the latest LXC template.

We'll now create our Ubuntu container.
Click the **Datacenter** > **pve-1** > **Create CT** button.
Now fill the form with **Hostname** is `omaha-controller`,
**Password** of your choose,
**Template** is `ubuntu-20.04-standard_20.04-1_amd64.tar.gz`,
**Disk** is 8GB, **CPU** is 1, **CPU units** is 1024,
**Memory** and **Swap** is 512MB.

For the **Network** tab,
**Bridge** is the LAN network interface `vmbr1`,
select **DHCP**
and **Gateway** we leave blank.
Also leave blank **DNS** tab, check **Start ...** and hit **Confirm**

#### Step X: Install Omada Controller - DONE
* Google Chrome 37 or later
Java Runtime Environment (JRE) - `sudo apt-get install openjdk-8-jre-headless`
Install the tools jsvc and curl - `sudo apt-get install jsvc curl`
MongoDB 3.0.15–3.6.18
Install the Omada Controller `.deb` - `dpkg -i Omada_Controller_v4.2.8_linux_x64.deb`

```bash
# do an upgrade
apt-get update && apt-get -y upgrade

# load google chrome browser
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
apt install ./google-chrome-stable_current_amd64.deb

# clean up
mv ./google-chrome-stable_current_amd64.deb /tmp

# to use google chrome via the commandline
google-chrome
```

Install the prerequisites needed by the Omada Controller:

```bash
# install java runtime environment (jre)
apt-get -y install openjdk-8-jre-headless

# install needed and desirable networking tools
apt-get -y install jsvc curl gnupg
apt-get -y install net-tools arp-scan

# install mongodb database
apg-get -y install gnupg
curl -fsSL https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-4.4.list
apt-get update && apt-get -y install mongodb-org

# start mongodb
systemctl start mongod.service
systemctl status mongod
```

Now lets install the [Omada Controller][23]:

```bash
# download the omada controller package
wget https://static.tp-link.com/upload/software/2022/202201/20220120/Omada_SDN_Controller_v5.0.30_linux_x64.deb

# install omada controller
dpkg -i Omada_Controller_v4.2.8_linux_x64.deb

# clean up
mv Omada_SDN_Controller_v5.0.30_linux_x64.deb /tmp
```

You should now be able to access the Omada Controller using
`http://<Local IP Address>:8088` or
`https://<Local IP Address>:8043` and adopt your devices
as shown below:

```bash
# test if the omada controller is up
# perform test from another host on the lan
google-chrome 192.168.2.13:8088
```

Sources:

* [Download for Omada Software Controller V5](https://www.tp-link.com/us/support/download/omada-software-controller/)
* [Install TP-Link Omada SDN Controller on Ubuntu 20.04](https://patrickdomingues.com/2021/05/07/install-tp-link-omada-sdn-controller-on-ubuntu-20-04-2/)
* [How To Install MongoDB on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-ubuntu-20-04)

#### Step X: Configure Omada Controller - DONE
Now connect the EAP610 to the LAN network and power the device.
Using the Omada Setup Wizard,
make the following chooses:

* Select **Home** and then <enter>
* Select your device (in my case Device name is `B0-A7-B9-14-D3-02` and model is `EAP610(US) v1.0`)
* Turn-off the **WAN Settings Overrides**
* I configured the WiFi to **Network Name (SSID)** to `test-wifi6`, and your **Password** same as the original
* **Administrator Name** is `admin` and **Password** is your favorite password

At this point, you should be able to connect to the TP-Link EAP610 access point.
It will be in the LANs IP address space with the LANs DHCP providing IP addresses.
If you go to pfSense's **Status** > **DHCP Leases** and you'll find among the leases
the Omada Controller and/or the EAP610 access point listed.

Also, you should be able to turn off the Omada Controller until you need to do some
additional configuration work.

>**NOTE:** If this WiFi configuration involved a WiFi wireless card instead of
>an IP-based access point, there would be a different approch required.
>For a wireless card, check out this article:
"[pfSense 2.4 WIFI configuration: a helpful illustrated guide][27]"
and "[How to configure Wi-fi+Lan bridged access point in pfSense firewall router][28]".

Sources:

* [How to Connect an Access Point to pfSense](https://openschoolsolutions.org/how-to-connect-an-access-point-to-pfsense/)
* [User Guide: Omada SDN Controller](https://static.tp-link.com/upload/software/2022/202201/20220121/1910013128-Omada%20SDN%20Controller%20User%20Guide%205.0%20(windows&linux).pdf)



-----



# Configure VLANS for Home Network
VLAN configuration will take plan in multiple places,
specifically pfSense, TP-Link Switch, and on the TP-Link Access Point.

#### Step X: Establish VLANs on pfSense
* [UniFi AP with pfSense VLAN's](https://brendonmatheson.com/2020/03/14/unifi-ap-with-pfsense-vlans.html)
* [Access Points and Creating WiFi VLANs Explained Using UniFi Wireless](https://www.youtube.com/watch?v=6wcbkE3TF3c)
* [pfSense VLAN and Guest Network Setup](https://www.youtube.com/watch?v=hhPGN4UJHAM)
* [Configuring Switches with VLANs](https://docs.netgate.com/pfsense/en/latest/recipes/switch-vlan-configuration.html)

#### Step X: Establish VLANs on Omada Controller
* [Simple Setup and Use of the TP-Link Omada EAP660 HD WiFi Access Point with VLANs | AX3600](https://www.youtube.com/watch?v=lSPIydOtOj0)



-----





#### Step X; Guest Network
* [How to set Access Control to create guest SSID on Omada Controller/EAP](https://www.tp-link.com/us/support/faq/1060/)




-------



# Aliases
Create aliases for your desktop Linux box,

Alias Name     IP Address      Description
pfSense        192.168.1.1     Router / Firewall for Home Network
Desktop        192.168.1.200   Desktop Linux Box




-------




# Configure VLANs For Home Network
What is a VLAN?
It stands for virtual local area network,
you can just think of it as a separate network, only virtual and not physically seperate.
Even though you will have all your devices plugged into the same physical network,
devices on different VLANs will need to communicate through the pfSense established VLANs and their firewalls,
allowing much better control over network rules.

Maybe you don’t want your guests to have access to your VMs.
You just put the VMs on their own VLAN,
assign your VMs a DHCP static address on the VLAN network,
and create a firewall rule to allow only your IP address to
communicate with the VLAN with your VMs on it.
What about a separate VLAN for your kids (or whoever) that blocks certain
websites or blocks the internet completely outside of designated hours?
That can all be done with pfSense and VLANs.

# Configure Firewalls for WAN, LAN, and VLANs
A best practices for firewall rules configuration:

* Block all traffic by default (aka Block Any/Any Rule) and explicitly enable only specific traffic to known services.
This strategy provides good control over the traffic and reduces the possibility of a breach because of service misconfiguration.
* Where network access is allowed, access criteria should be as specific as possible.
This strategy is the principle of least privilege, and it forces control over network traffic.
Specify as many parameters as possible in the rules.
* If the service should be accessible to everyone on the Internet,
then any source IP address is the correct option.
In all other cases, you should specify the source address.
* Always specify which server or servers are accessible and which ports are to be used.
* Final rule should be a "Block Any/Any Rule" and log all execution of this rule.
This gives you record of activity which are not being caught by the other rules.

>**Note:** Firewall rules in pfSense are applied to traffic going **IN**
>to the interface they are configured on.
>They do not apply to traffic going **OUT** of that interface.
>In our use case, the WAN interface Firewall Rules apply to Internet traffic entering any of your home networks.
>The LAN interface Firewall Rules apply to only traffic entering the network called "LAN".

Rules to be established on WAN

* [Block Bogon Networks](https://docs.netgate.com/pfsense/en/latest/firewall/rule-methodology.html#block-bogon-networks)
- filtering bogons, which are bogus (fake) IP addresses of a computer network. Bogons include IP packets on the public Internet that contain addresses that are not in any range allocated or delegated by the Internet Assigned Numbers Authority (IANA) or a delegated regional Internet registry (RIR) and allowed for public Internet use. The areas of unallocated address space are called the bogon space.
* [Anti-Lockout Rule](https://docs.netgate.com/pfsense/en/latest/firewall/rule-methodology.html#anti-lockout-rule) - allows traffic from any source inside the network containing the rule, to any firewall administration protocol listening on the LAN IP address. For example, it grants access to TCP port 443 for the WebGUI, TCP port 80 for the GUI redirect, and TCP port 22 if SSH is enabled. If the WebGUI port has been changed, the configured port is the one allowed by the anti-lockout rule.
* [Block Any/Any Rule](https://www.liquidweb.com/kb/best-practices-for-firewall-rules/#:~:text=The%20main%20purpose%20of%20firewalls,all%20mechanism%20for%20capturing%20traffic.) - (aka Cleanup Rule) at 20 minute mark in [PfSense Advanced Configuration - VM Setup, Virtual IPs, Alias, NAT, Rules][19].
pfSense does have an implied Drop Any/Any Rule at the end of its rule list but I put one in so I can log the execution of this rule.

Rules to be established on LAN

*  Allow LAN to Any Rule - allow any traffic that is both from and to the LAN network. It doesn’t do anything right now, but it will save us a lot of drama down the road if we expand the network across multiple switches or something of that nature.

Rules to be established on LAN (Admin)
Rules to be established on LAN (Personal)
Rules to be established on LAN (Guest)
Rules to be established on LAN (Video)
Rules to be established on LAN (IoT)
* [pfsense and Rules For IoT Devices with mDNS](https://www.youtube.com/watch?v=HW9mUrF1ZgU)

* [Netgate Docs: Firewall](https://docs.netgate.com/pfsense/en/latest/firewall/index.html)
* [Netgate Docs: Virtual LANs (VLANs)](https://docs.netgate.com/pfsense/en/latest/vlan/index.html)
* [Configuring pfsense Firewall Rules For Home](https://www.youtube.com/watch?v=bjr0rm93uVA)
* [Creating VLANS And Firewall Rules with PFsense](https://www.youtube.com/watch?v=CDUyMpBC8bw)
* [Inexpensive Budget Switch: TP Link TL-SG108E HW Rev. 3.0 With VLANS & pfsense Review](https://www.youtube.com/watch?v=5ohLAFHnOHg)

#### Step X: Create VLAN on pfSense
Creation of a VLAN on pfSesne is easy to perfrom.

Select **Interfaces** > **Assignments** >  **VLANs** > click **+ Add** button.

* **Patrent Interface** is LAN
* **VLAN TAg** is 10,
* **VLAN Priority** is 0 or <blank>
* **Description** is "Personal devices -- not including IoT or video devices"

Now repeat this for Admin, Guest, Video, and IoT.

In the above, you have created the VLANs but you now need to enable these newly created interfaces.
Select **Interfaces** > **Assignments** > click **+ Add** button.

* [What are VLANs? -- the simplest explanation](https://www.youtube.com/watch?v=MmwF1oHOvmg)
* [VLAN vs Subnet: What Are Their Differences?](https://www.fiber-optic-transceiver-module.com/vlan-vs-subnet.html)
* [What is a VLAN??? - How to setup VLANs in your Home Network and WHY YOU NEED THEM](https://www.youtube.com/watch?v=XdqP14NclZ0&list=PLPUuhipqbOXSr-LIm5PLNojvLw3nIWNOY&index=1)

* [Creating VLANS And Firewall Rules with PFsense](https://www.youtube.com/watch?v=CDUyMpBC8bw)
* [How to Setup VLANs on pfSense 2.5](https://www.youtube.com/watch?v=EevGik0vwlM)

* [What is a VLAN??? - How to setup VLANs in your Home Network and WHY YOU NEED THEM](https://www.youtube.com/watch?v=XdqP14NclZ0&list=PLPUuhipqbOXSr-LIm5PLNojvLw3nIWNOY&index=1)
* [Home Network Setup - pfSense, VLANs, VPN, HAProxy, 10G, and more](https://www.youtube.com/watch?v=_cDEdjDGP8w&list=PLPUuhipqbOXSr-LIm5PLNojvLw3nIWNOY&index=8)
* [Converting single NIC mini-pc into pfSense router/firewall by using virtual LAN configuration on a managed switch](https://www.joe0.com/2019/11/16/converting-single-nic-mini-pc-into-pfsense-router-firewall-by-using-virtual-lan-configuration-on-a-managed-switch/)




-------




# Configure Port Forward
When you port forward, you’re allowing access to a device on your local network. It’s important to understand that this allows for people and devices outside of your local network to access a specific device inside your local network.

**Firewall** > **NAT** > **Port Forward**

* [How to Port Forward in pfSense](https://www.wundertech.net/pfsense-port-forwarding-setup-guide/)



-------



#### Step X: Turn Portectli Vault Ports into Switch
* [pfsense - turn those extra router ports into switch!](https://www.youtube.com/watch?v=bz45r_4BREw)

#### Step X: All Traffic Routed Over VPN
If using WireGaurd, it needs to be install via Package Manager
Private Internet Access (PIA) Virtual Private Network (VPN)

* [your home router SUCKS!! (use pfSense instead)][01]

#### Step X: Telegram / Slack / Pushover Notifications
**System** > **Advanced** > **Notifications**



-------



# pfSense Packages
**System** > **Package Manager**

#### Step X: Service_Watchdog
* [your home router SUCKS!! (use pfSense instead)][01]

#### Step X: Cloudflare's 1.1.1.1 for Families
Cloudflare claims its mission is to make a [more private and safe Internet experiance][26].
Cloudflare's 1.1.1.1 DNS is designed for [private][25], security, and fast DNS resolution
but not for blocking or filtering content.
Never the less, Cloudflare has recieved requests to provide a version of the product
that automatically filters out bad sites.
Cloudflare calls this DNS service [1.1.1.1 for Families][24].

1.1.1.1 for Families has two default options:
one that blocks malware and the other that blocks malware and adult content.
You choose which setting you want depending on which IP address you configure.

1. **Malware Blocking Only**
    * Primary DNS: 1.1.1.2
    * Secondary DNS: 1.0.0.2
2. **Malware and Adult Content**
    * Primary DNS: 1.1.1.3
    * Secondary DNS: 1.0.0.3

* [Cloudflare 1.1.1.1 for Families & How to use it with pfsense](https://www.youtube.com/watch?v=uNKgnycpZhg)
* [Cloudflare 1.1.1.1 for Families DNS Service Capabilities and Limitations](https://www.youtube.com/watch?v=OmbGHJMhb48)
* [Cloudflare 1.1.1.1](https://developers.cloudflare.com/1.1.1.1/)

#### Step X: pfBlockerNG and/or Snort and/or Suricata and/or Fail2Ban
* [your home router SUCKS!! (use pfSense instead)][01]
* [How To Setup Your Own IDS/IPS in PfSense With Snort](https://www.youtube.com/watch?v=OoiY5tx7Ol4)
* [Integrate Fail2Ban with pfSense](https://www.blackrosetech.com/gessel/2020/07/13/integrate-fail2ban-with-pfsense)
* [Linux security: Protect your systems with fail2ban](https://www.redhat.com/sysadmin/protect-systems-fail2ban)
* [How to Install Fail2ban in Docker](https://fedingo.com/how-to-install-fail2ban-in-docker/)
* [Install and configure Fail2ban with Docker](https://www.the-lazy-dev.com/en/install-fail2ban-with-docker/)



-------



# NAT
Network Address Translation (NAT) is the process of shuffling internet protocol traffic
from several hosts through a single gateway IP address,
just like your home router does by default.
Essentially any host behind the NAT gateway sends it’s outbound requests to the gateway,
which forwards that traffic to its destination and keeps track of which private host made the request,
when a response comes back the gateway forwards that back to the original host.

>**Note:** NAT alone is NOT security! A crafty hacker can circumvent NAT.
>[NAT Slipstreaming][22] is one example.


-------



# DHCP
Dynamic Host Configuration Protocol (DHCP), hands out IP addresses to new hosts
on a network so no manual configuration is required.
Without DHCP, you would have to manually set a unique IP address,
and the subnet mask, gateway, and DNS settings for each device on your network.

The Dynamic Host Configuration Protocol (DHCP) provides a centralized and automated method for configuring the network attributes of hosts when they connect to the network. The DHCP server assigns IP addresses to hosts, along with configuration information such as DNS servers, the domain name used for DNS searches, the default gateway, an NTP (Network Time Protocol) server, a server from which a network boot can be performed if necessary, and more. DHCP eliminates the need to configure each network host individually.

* [How I configure a DHCP server on my personal network](https://opensource.com/article/22/7/configure-dhcp-server)



-------




# Domain Name Services (DNS)
Domain Name System (DNS), is a lookup service that translates a hostname
like `google.com` for example, to an IP address.
This is usually set to your modem or router’s IP address by default (same as the gateway address),
which will in turn use the DNS servers provided by your ISP (Internet Service Provider).

dnsmasq is a lightweight, easy to configure DNS forwarder, designed to provide DNS (and optionally DHCP and TFTP) services to a small-scale network. It can serve the names of local machines which are not in the global DNS.

The DNS Forwarder allows pfSense to resolve DNS requests using hostnames obtained by the DHCP service, static DHCP mappings, or manually entered information. The DNS Forwarder can also forward all DNS requests for a particular domain to a server specified manually.

The DNS Resolver in pfSense® software utilizes unbound, which is a validating, recursive, caching DNS resolver that supports DNSSEC, DNS over TLS, and a wide variety of options. It can act in either a DNS resolver or forwarder role.

* [pfSense and DNS | Your ISP tracks EVERY SITE you visit!](https://www.youtube.com/watch?v=-uzNMospB5I)
* [What is DNS Forwarding](https://social.dnsmadeeasy.com/blog/understanding-dns-forwarding/)
* [Set up DNSSEC and DNS over TCP on pfSense](https://www.youtube.com/watch?v=Z3-E90VEIbY)
* [Boost your home network with DNS caching on the edge](https://opensource.com/article/22/3/dns-caching-edge)

## DNS Redirect
* [2020 pfSense 2.4 DNS Redirect Tutorial: Completely control DNS on your network](https://www.youtube.com/watch?v=2g0VoMrJA5c)
* [Netgate Docs: Redirecting Client DNS Requests](https://docs.netgate.com/pfsense/en/latest/recipes/dns-redirect.html)

## Setup DNS Resolver in PfSense
* [pfSense and DNS | Your ISP tracks EVERY SITE you visit!](https://www.youtube.com/watch?v=-uzNMospB5I)
* [How To Setup Your Own DNS Resolver in PfSense](https://www.youtube.com/watch?v=zgrrrwDpyZc)

## Dynamic DNS (DDNS)
old ip = 108.44.239.214
new ip = 71.171.98.206
token = jhx0pStsQlLiWDPxToazLjUUj8lSGbvQdIJ4kId5

curl -s -X GET "https://api.cloudflare.com/client/v4/user/tokens/verify" -H "Authorization: Bearer jhx0pStsQlLiWDPxToazLjUUj8lSGbvQdIJ4kId5" -H "Content-Type:application/json" | jq -C '.'

* [Clicking Save & Force Update on a Dynamic DNS entry results in a GUI timeout](https://redmine.pfsense.org/issues/12870)
* [How to automatically save and force update of a dynamic DNS on pfSense?](https://serverfault.com/questions/1092678/how-to-automatically-save-and-force-update-of-a-dynamic-dns-on-pfsense)


If you have a static external IP address,
DDNS will provide little to no value for you.
However, if you have a dynamic IP address (like most residental IP services provider give you),
DDNS will allow you to ensure you’re always connecting to your external IP address,
even where it could changing on you.
This can all be accomplished relatively easily  with pfSense.
I used the steps below to set up DDNS on pfSense and using my DNS provider, Cloudflare.

* [How to Set Up DDNS on pfSense using Cloudflare](https://www.wundertech.net/how-to-set-up-ddns-on-pfsense-using-cloudflare)
* [How to Set Up DDNS on pfSense using Cloudflare | QUICK TUTORIAL](https://www.youtube.com/watch?v=8GYs61ThGBM)
* [DDNS on a Raspberry Pi using the Cloudflare API (Dynamic DNS)](https://www.youtube.com/watch?v=rI-XxnyWFnM)

#### Step X:
Log in to Cloudflare and select **DNS** from the lefthand main menu.
You need to create an **A** type DNS record for your domain name.
Also, turn off Proxied for now and then hit **Save**.

>**NOTE:** The Proxied featured will be turned back on within a later step.

#### Step X: Get custom API Token
We now need our API Token to use as our password in pfSense, which can be accessed in the API Tokens section of Cloudflare
**Overview** > **Get your API token**

#### Step X:
**Services** > **Dynamic DNS** > ckick **Add**

#### Step X:



-------




#### Step X: SSL Encryption and Reverse Proxy Setup
I plan to exposing some websites or services to the Internet from my home network.
Do this requires SSL which can be a can be a pain to setup and get it properly working.
Using pfSense to manage SSL is a way to easily get this done in just a few steps.
It use HAProxy as a reverse proxy and ACME to manage the SSL certificates.

* [How To Setup ACME, Let's Encrypt, and HAProxy HTTPS offloading on pfsense](https://www.youtube.com/watch?v=gVOEdt-BHDY)
* [SSL Encryption on Your Home Server the SIMPLE WAY - Cloudflare, pfSense, HAProxy, ACME https setup](https://www.youtube.com/watch?v=cB6oKJjr4Ls)
* [How To Create pfsense Let's Encrypt Wildcard Certificates using HAProxy](https://www.youtube.com/watch?v=jpyUm53we-Y)
* [pfsense HA Proxy Troubleshooting](https://www.youtube.com/watch?v=fLV3kF3QIws)



-------




#### Step X: pfSense Captive Portal
Captive Portal in pfSense forces users on an interface to authenticate before granting access to the Internet.
Where possible, the firewall automatically presents a login web page in which the user must enter credentials such as a username/password, a voucher code, or a simple click-through agreement.
It is primarily used for wireless hot spots or for additional authentication before allowing access to internal networks from wireless clients.

* [How to Set Up a Captive Portal Using pfSense](https://turbofuture.com/computers/How-to-Set-Up-a-Captive-Portal-Using-pfSense)
* [Setting up a captive portal with pfsense firewall](https://geeklk.com/2019/03/09/setting-up-a-captive-portal-with-pfsense-firewall/)
* [pfsense Captive Portal](https://www.youtube.com/watch?v=hdHDCafeFdU)
* [Netgate Docs: Captive Portal](https://docs.netgate.com/pfsense/en/latest/captiveportal/index.html)
* [Authenticating OpenVPN Users with FreeRADIUS](https://docs.netgate.com/pfsense/en/latest/recipes/openvpn-ra-auth-freeradius.html)
* [Authenticated and NON Authenticated Captive Portals with pFsense 2021](https://www.youtube.com/watch?v=ALQvXRCSy8w)



-------




#### Step X: Setup VPN




-------





# Troubleshooting Access when Locked Out of the Firewall
* [Troubleshooting Access when Locked Out of the Firewall](https://docs.netgate.com/pfsense/en/latest/troubleshooting/locked-out.html)

>**NOTE:** If you for whatever reason locked yourself out of the pfSense admin GUI,
>or need access from a IP outside your,
>you can do this via the WAN interface but you must turn off firewall rules first.
>To do this use Proxmox **Console** for pfSense, enter 8 and then `pfctl -d`
>This will turn off the firewall rules blocking access via WAN (`192.168.1.12` on your home network).
>Use `pfctl -e` to turn firewall rules back on.

#### Step X: Setup a Guest Network

#### Step X: Segregated IoT Devices
Unless you have done something explicitly to limit their access (VLAN, access control lists, a separate IOT WiFi network) they are probably members of your network like any other device.

* [How I Protect My Network from IoT Device Hacking](https://hometechhacker.com/protect-network-iot-device-hacking/)
* [11 Home Network Security Tips You Need To Implement Now](https://hometechhacker.com/9-home-network-security-tips/)

#### Step X: SNORT
Snort is an Intrusion Detection System/Intrusion Prevention System (IDS/IPS) that uses sophisticated and regularly updated rules to detect and prevent attempts by hackers to penetrate your network.


#### Step X: Automatic Backup of pfSense Configurations - DONE
I would be in a world of hurt if I had to rebuild my pfSense configuration from scratch.
So configuration backups are essential
(and you should always do them before you upgrade pfSense).
pfSense allows you to use the web interface to make a backup whenever you want,
but backups work better when they are automated.
With pfSense, you have a few backup automation choices:

* Use the [AutoConfigBackup Service](https://docs.netgate.com/pfsense/en/latest/backup/autoconfigbackup.html) – This is a built-in feature of pfSense that lets you schedule and store backups on a regular basis.
You can enambe this via **Services** > **Auto Configuration Backup** > **Settings**.
* Use [wget or curl](https://docs.netgate.com/pfsense/en/latest/backup/remote-backup.html) – This method is a little more “hacky” but allows you more control over where your backups are stored.
* Write your own script using an ssh key. You can set up access to your pfSense server via an ssh key. Then a remote machine can use scp or the like to copy the config file to your preferred location at whatever interval you like. The config file is located at /cf/conf/config.xml. This is the method I primarily use. I also regularly copy over a couple of other files in the same script for good measure.

To save your Status Dashboard layout, hit the floppy disk icon at the top right corner of the Dashboard screen.

* [PfSense 2.5.2 - Configuration Backup and Restore](https://www.youtube.com/watch?v=CQ-pv8YfwqE)
* [Netgate Docs: Backup and Recovery](https://docs.netgate.com/pfsense/en/latest/backup/index.html)

#### Step X; Setup DNS and Add-Blockers
Checkout setting-up-pi-hole.md


#### Step X: OpenVPN for Secure Remote Access
OpenVPN is an Open Source VPN client and server supported by many platforms, including pfSense.
A great way for home users to use it is for secure remote access to their home networks.
In many cases, it can more securely replace your port forwarding needs.

* [How to install OpenVPN on pfSense: Ultimate Beginner Guide](https://www.ceos3c.com/pfsense/openvpn-on-pfsense/)
* [How to setup your own OpenVPN server in pfSense](https://www.bleepingcomputer.com/vpn/guides/openvpn-server-pfsense/)
* [OpenVPN Remote Access Configuration Example](https://docs.netgate.com/pfsense/en/latest/recipes/openvpn-ra.html)
* [Tutorial: pfsense OpenVPN Configuration For Remote Users 2020](https://www.youtube.com/watch?v=PgielyUFGeQ)
* [5 Best VPNs for pfSense: Configure & Secure Your Home/Office Network!](https://www.technadu.com/best-vpn-for-pfsense/342509/)

#### Step X: Configure DHCP Server
Static DHCP leases allow the computers on your network to always receive the same IP address when they connect (based on their MAC address). If you have devices on your network that are easier to use if they keep a constant IP and have a hostname associated with that IP then static DHCP leases are for you.

[pfSense DHCP Server](https://docs.netgate.com/pfsense/en/latest/services/dhcp/ipv4.html)

#### Step X: Lock down access to pfSense
One of the main reasons I chose pfSense was for its security features.
It is best to limit the number of device you normally use to access pfSense.

[Allowing Remote Access to the GUI](https://docs.netgate.com/pfsense/en/latest/recipes/remote-firewall-administration.html)

#### Step X: Virtual Private Networks
* [pfSense Documentation](https://docs.netgate.com/pfsense/en/latest/index.html)
    * [Virtual Private Networks](https://docs.netgate.com/pfsense/en/latest/vpn/index.html)

#### Step X: pfSense Router Packages
Darkstat
Sudo
Squid
Cron
Service watchdog

#### Step X: Reverse Proxy
* [Self Hosting on your Home Server - Cloudflare + Nginix Proxy Manager - Easy SSL Setup](https://www.youtube.com/watch?v=GarMdDTAZJo)

# Firewall Physical Install

# Access Control Lists (ACLs)
* [Access Control Lists (ACLs)](https://www.youtube.com/watch?v=0gGhuYOh-54&list=PLIFyRwBY_4bRkAk_BkWL3ea6lRvOn8AKs&index=1&t=3s)

# Key features of PfSense:-
* [Top 10 Best Open Source Firewall to Protect Your Enterprise Network 2022](https://cybersecuritynews.com/best-open-source-firewall/)
Features
    Disable filtering – You can completely disable the firewall filter if you want to turn your PfSense into a pure router.
    NAT (Network Address Translation)
    HA (High Availability)
    Multi-WAN (Wide Area Network)
    Load balancing
    VPN (Virtual Private Network)
    PPPoE server
    Graphic and log monitoring
    Dynamic DNS
    Captive portal
    DHCP server and DHCP Relay
    Firewall – IP/port filtering, limiting connections, layer two capable, scrubbing
    State table – by default all rules are stateful, multiple configurations available for state handling,
    Server load balancing – inbuilt LB to distribute the load between multiple backend servers
    NAT (Network address translation) – port forwarding, reflection
    HA (High-availability) – failover to secondary if primary fail
    Multi-WAN (wide area network) – use more than one internet connection.
    VPN (a virtual private network) – support IPsec and OpenVPN
    Reporting – Keep historical resources utilization information
    Monitoring – real-time monitoring
    Dynamic DNS – multiple DNS clients are included
    DHCP & Relay ready
Packages
    Security – a stunner, snort, tinc, nmap, arpwatch
    Monitoring – iftop, ntopng, softflowd, urlsnarf, darkstat, mailreport
    Networking – netio, nut, Avahi
    Routing – frr, olsrd, routed, OpenBGPD
    Services – iperf, widentd, syslog-ng, bind, acme, imspector, git, dns-server
    Traffic Shaping
    Transparent Caching
    Web Content Filter


-----


# Securing pfSense

##  Disable Pfsense Access from WAN - DONE
By default, the pfSense administrative GUI **is not** exposed on the WAN interface
and accessible to everyone.
It is generally agreed, you enhance the security of LAN network
by restricting access to pfSense's GUI, particularly the WAN interface.
This can be done via firewall rules.
So there is nothing you need to do, just use the default setting.

Also note, by default, pfSense has enable the "Anti-lockout Rule"
You can disable this rule (but generally shouldn't) by navigating to
**System** > **Advanced** > **Admin Access** and check the item **Anti-lockout** > **Save**.
This disable webConfigurator the Anti-lockout Rule.
Then do **Diagnostics** > **Reboot**,
and when it comes up, try login use the WAN IP address
(you find that on the **Status** > **Dashboard**) from outside your desktop Linux box.

>**NOTE:** Its important to test the blocking of the GUI on the WAN from outside your LAN.
>For example, use your mobile phone's browser but with the WiFi turned off.
>If you are testing from within the LAN then the router is likely detecting
>that your using its owns public IP address and isn't forwarding the traffic to your WAN interface.

```bash
# when doing nmap from within your lan, the scan shows wan ports open
# this does NOT give you a ture reading what is physically seen from the internet
$ sudo nmap <external-IP-address>
[sudo] password for jeff:
Starting Nmap 7.80 ( https://nmap.org ) at 2023-04-07 14:45 EDT
Nmap scan report for pool-108-44-239-59.clppva.fios.verizon.net (108.44.239.59)
Host is up (0.00081s latency).
Not shown: 997 filtered ports
PORT    STATE SERVICE
53/tcp  open  domain
80/tcp  open  http
443/tcp open  https

Nmap done: 1 IP address (1 host up) scanned in 5.22 seconds

# a trustworthy test is to attempt to login via a browser outside your lan
# using a cell phone, with wifi turned off, attempt a login use the <external-IP-address>
```

Sources:

* [How to disable PfSense webConfiguration on WAN](https://stackoverflow.com/questions/66929107/how-to-disable-pfsense-webconfiguration-on-wan)
* [Securely Managing Web-administered Devices](https://www.netgate.com/blog/securely-managing-web-administered-devices)
* [pfSense Docs: Strict Management](https://docs.netgate.com/pfsense/en/latest/recipes/remote-firewall-administration.html#strict-management)
* [Allowing Remote Access to the GUI](https://docs.netgate.com/pfsense/en/latest/recipes/remote-firewall-administration.html#strict-management)



--------


# Setup VLAN in pfSense
* [How to Set up a VLAN in pfSense](https://www.wundertech.net/how-to-setup-vlans-in-pfsense/)



-------


* [How to Run a Speed Test on pfSense](https://www.wundertech.net/how-to-run-a-speed-test-on-pfsense/)




[01]:https://www.youtube.com/watch?v=lUzSsX4T4WQ&t=806s
[02]:https://www.youtube.com/watch?v=V6di1EAovN8
[03]:https://www.dlford.io/pfsense-nat-how-to-home-lab-part-3/
[04]:https://docs.netgate.com/pfsense/en/latest/recipes/virtualize-proxmox-ve.html
[05]:https://www.pfsense.org/download/
[06]:https://www.youtube.com/watch?v=7WHkuG76oBc
[07]:https://www.youtube.com/watch?v=tHfAWY_jYbQ
[08]:https://novnc.com/info.html
[09]:https://www.spice-space.org/
[10]:https://help.ubuntu.com/community/Byobu
[11]:https://protectli.com/kb/nic-port-numbering-and-naming/
[12]:https://www.byobu.org/
[13]:https://www.maketecheasier.com/share-terminal-session-with-friends/
[14]:http://www.electricmonk.org.uk/2020/11/12/aes-and-aes-ni/
[15]:https://www.youtube.com/watch?v=gdxOT6L-GHo
[16]:https://www.openbsd.org/index.html
[17]:https://www.openbsd.org/faq/pf/
[18]:https://protectli.com/kb/pfsense-configuration-recommendations/
[19]:https://www.youtube.com/watch?v=Kk9PK-1bI6U
[20]:https://www.youtube.com/watch?v=fsdm5uc_LsU
[21]:https://www.youtube.com/watch?v=qRyXAFD94lI
[22]:https://thehackernews.com/2020/11/new-natfirewall-bypass-attack-lets.html
[23]:https://www.tp-link.com/us/business-networking/omada-sdn-controller/omada-software-controller/v5/
[24]:https://blog.cloudflare.com/introducing-1-1-1-1-for-families/
[25]:https://blog.cloudflare.com/announcing-the-results-of-the-1-1-1-1-public-dns-resolver-privacy-examination/
[26]:https://blog.cloudflare.com/announcing-1111/
[27]:https://teklager.se/en/knowledge-base/pfsense-24-step-step-wifi-configuration-instructions/
[28]:https://www.cyberciti.biz/faq/howto-configure-wireless-bridge-access-point-in-pfsense/
[29]:https://www.joe0.com/2019/11/16/converting-single-nic-mini-pc-into-pfsense-router-firewall-by-using-virtual-lan-configuration-on-a-managed-switch/
[30]:https://docs.netgate.com/pfsense/en/latest/troubleshooting/locked-out.html
[31]:https://pve.proxmox.com/wiki/Pci_passthrough
[32]:https://docs.netgate.com/pfsense/en/latest/recipes/virtualize-proxmox-ve.html#disable-hardware-checksums-with-proxmox-ve-virtio
[33]:https://en.wikipedia.org/wiki/Network_function_virtualization
[34]:
[35]:
[36]:
[37]:
[38]:
[39]:
[40]:
