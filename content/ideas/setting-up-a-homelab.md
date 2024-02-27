<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>



-----



* [What is a HomeLab and Why Build One?](https://www.virtualizationhowto.com/2023/08/what-is-a-homelab-and-why-build-one/)
* [Docker Swarm vs Kubernetes: Home Lab Comparison](https://www.virtualizationhowto.com/2023/08/docker-swarm-vs-kubernetes-home-lab-comparison/)
* [K3s vs K8s: The Best Kubernetes Home Lab Distribution](https://www.virtualizationhowto.com/2023/07/k3s-vs-k8s-the-best-kubernetes-home-lab-distribution/)



* [Best Practices for pfSense Firewall Rules](https://hometechhacker.com/best-practices-for-pfsense-firewall-rules/)



# What is a Homelab?
I, like many, want to experiment with different computer & networking technologies.
This would include creating my own web server, NAS storage, private cloud services,
experiment with networking techniques, have a server to create virtual machines or containers,
or create a cluster to try out Kubernetes, maybe extensive set of IoT devices, etc.
Collectively this is generally called a [homelab][12], all good stuff,
but this all needs to start with a secure environment.

So one must start by getting your router + firewall setup right to protect yourself from the
Internet and the disruption that come from experimenting with new hardware, software
and crazy experiments.
The plan below starts with router + firewall to create the foundation for the secure environment.
Once establish,
layer on the additional hardware & software pieces to fill it out further.

Sources:

* [My Overkill Home Network - Complete Details 2023](https://blog.networkprofile.org/my-home-network-complete-details-2023/)
* [What is a HomeLab and How Do I Get Started?](https://www.youtube.com/watch?v=gPGf4Y8nQqM)
* [How to set up a homelab from hardware to firewall](https://opensource.com/article/19/3/home-lab)
* [Build your own router, and homelab along the way](https://fsanmartin.co/build-your-own-router-and-homelab-along-the-way/)
* [Building a homelab with Proxmox](https://www.remotelycurious.net/post/homelab/)
* [Home Network Setup - pfSense, VLANs, VPN, HAProxy, 10G, and more](https://www.youtube.com/watch?v=_cDEdjDGP8w)
* [How to Home Lab](https://www.dlford.io/tag/home-lab/)
* [Building a Homelab VM Server (2020 Edition)](https://mtlynch.io/building-a-vm-homelab/)
* [The Homelab Wiki](https://thehomelab.wiki/)
* [Which Server Rack Is Suitable For A Home Lab?](https://robots.net/tech/which-server-rack-is-suitable-for-a-home-lab/)


## Components of a Homelab
Every homelab is a different and very much reflects the
interests, needs, and budget of the person using it.
Here are the components I plan to establish.

* Foundational Components
    * Full Feature Router + Firewall
    * Virtualization Server
    * Virtual LAN (VLAN)
    * Reverse Proxy
* Add-on Components
    * Enhansed Security
    * Dashboard
* Optional Components
    * Disk Cloning and Backups
    * eMail Spam Blocker
    * Remote Access
    * Kubernetes Cluster
    * Infrastructure as Code (IaC)

## Domains
Type    Name                IP Address
A       jeffskinnerbox.me   72.86.37.26
CNAME   www                 @
CNAME   bitwarden           @

## Physical Design & Network Addressing
My vision for the physical design will be

        Desktop - 192.168.1.200 (static)
Blog                 192.168.1.200:80
Homer                192.168.1.200:8001
Portainer            192.168.1.200:9000

        Synology - 192.168.1.201 (static)
Synology NAS         192.168.1.201:5000
Portainer Agent      192.168.1.201:9001

        Protectli Vault - 192.168.1.1 (static)
                          192.168.1.202 (static)
                          192.168.1.204 (static)
pfSense              192.168.1.1:80
Proxmox              192.168.1.202:8006
docker-containers    192.168.1.204
Portainer Agent      192.168.1.204:9001
Guacamole            192.168.1.204:8194

        Argon ONE Raspberry Pi 4 - 192.168.1.203 (static)
home-assist          192.168.1.203
Home Assistant       192.168.1.203:8123
Portainer Agent      192.168.1.203:9001

        Clear Case Raspberry Pi 3 - 192.168.1.205 (static)
test-pi              192.168.1.205
Home Assistant       192.168.1.205:8123
Portainer Agent      192.168.1.205:9001

        Other Boxes
NTP Server           192.168.1.206        Raspberry Pi 2 Model B Rev 1.1
WiFi6 Access Point   192.168.1.2:80       TP-Link EAP610
WiFi Range Extender  192.168.1.3:80       TP-Link
Ethernet Switch      192.168.1.4:80       TP-Link TL-SG108E or TP-Link TL-SG116E
Philips Hue Gateway  DHCP
SmartThings Gateway  DHCP

        Cluster of Raspberry Pi 4

```
============= Target Architecture =============

  Internet
    |
    |                        Protectli Vault
*********************************************
*   |            Proxmox (192.168.1.202/24) *
*   |                                       *
*   |   WAN ISP Public IP Address           *
* pfSense                                   *
*      LAN 192.168.1.0/24                   *
*           |   |   |                       *
*           |   |   |                       *
*           |   |   |                       *
*           |   |  VM (192.168.1.X/24)      *
*           |   |                           *
*           |  Container (192.168.1.X/24)   *
*           |                               *
*********************************************
            |
  TP-Link Switch (192.168.1.X/24)
      |   |   |    |
      |   |   |    |                              Intel Box
      |   |   |  *********************************************
      |   |   |  *       |   |   |  Linux OS (192.168.1.200) *
      |   |   |  *       |   |   |                           *
      |   |   |  *       |   |   |                           *
      |   |   |  *       |   |  VM (192.168.1.X/24)          *
      |   |   |  *       |   |                               *
      |   |   |  *       |  Container (192.168.1.X/24)       *
      |   |   |  *       |                                   *
      |   |   |  *********************************************
      |   |   |
      |   |   |                          Synology DS220+
      |   |  *********************************************
      |   |  *       DiskStation Manager (192.168.1.201) *
      |   |  *********************************************
      |   |
      |   |                            Raspberry Pi 4
      |  *********************************************
      |  *            Home Assistant (192.168.1.???) *
      |  *********************************************
      |
      |                 Cluster of Raspberry Pi 4
     *********************************************
     *                 Kubernets (192.168.1.???) *
     *********************************************


          Key
-------------------------
 X   DHCP Issued IP Address
```

## Foundational Components

### Full Feature Router + Firewall
You already have a firewall built into your existing router,
so is it necessary to buy a special purpose firewall for your home network?

* [Do You Need to Get a Hardware Firewall?](https://www.youtube.com/watch?v=4k2ZMUzfiBU)
* [Do I Need a Firewall for My Home Network?](https://www.youtube.com/watch?v=oGMbnk_vMUE)

### Virtualization Server
* [Budget Proxmox Server for Homelabs](https://www.storagereview.com/review/budget-proxmox-server-for-homelabs)

### VLAN
* [What are VLANs? -- the simplest explanation](https://www.youtube.com/watch?v=MmwF1oHOvmg)
* [VLAN vs Subnet: What Are Their Differences?](https://www.fiber-optic-transceiver-module.com/vlan-vs-subnet.html)
* [Native VLAN - the DEFINITIVE illustration](https://www.youtube.com/watch?v=Fmq1E1Qr2W4)
* [Converting single NIC mini-pc into pfSense router/firewall by using virtual LAN configuration on a managed switch](https://www.joe0.com/2019/11/16/converting-single-nic-mini-pc-into-pfsense-router-firewall-by-using-virtual-lan-configuration-on-a-managed-switch/)
* [Configuring VLANs on Proxmox- An Introductory Guide](https://engineerworkshop.com/blog/configuring-vlans-on-proxmox-an-introductory-guide/)
* [Configuring VLANs with pfSense on Proxmox](https://notdodo.medium.com/a-poor-mans-proxmox-vlan-configuration-9f562fff0eef)
* [VLANs with Proxmox and pfSense](https://www.laroberto.com/vlans-with-proxmox-and-pfsense/)

### Reverse Proxy
* [Best for Homelab? Traefik vs Nginx Proxy Manager](https://www.youtube.com/watch?v=scrtJ1U4wJU)
* [How to Home Lab: Part 4 - NGINX Reverse Proxy](https://www.dlford.io/nginx-reverse-proxy-how-to-home-lab-part-4/)

## Add-on Components

## Enhansed Security
* [How to protect Linux from Hackers // My server security strategy!](https://www.youtube.com/watch?v=Bx_HkLVBz9M)
* [Self-Hosting Security Guide for your HomeLab](https://www.youtube.com/watch?v=Cs8yOmTJNYQ)
* [How to protect Linux from Hackers // My server security strategy!](https://www.youtube.com/watch?v=Bx_HkLVBz9M)
* [11 Home Network Security Tips You Need To Implement Now](https://hometechhacker.com/9-home-network-security-tips/)
* [Self-Hosting Security Guide for your HomeLab](https://www.youtube.com/watch?v=Cs8yOmTJNYQ)
* [11 Home Network Security Tips You Need To Implement Now](https://hometechhacker.com/9-home-network-security-tips/)
* [Ubuntu Server 18.04 Administration Guide Part 10 - Securing Applications with Fail2ban](https://www.youtube.com/watch?v=sboMT8N4ffA)
* [Fail2ban Tutorial | How to Secure Your Server](https://www.youtube.com/watch?v=kgdoVeyoO2E)
* [Additional Self-Hosted Security with Authelia on NGINX Proxy Manager](https://www.youtube.com/watch?v=4UKOh3ssQSU)
* [Security Onion](https://securityonionsolutions.com/)

* [Secure Your Self Hosting with Fail2Ban + Nginx Proxy Manager + CloudFlare](https://www.youtube.com/watch?v=Ha8NIAOsNvo)
* [Cloudflare Tunnel Setup Guide - Self-Hosting for EVERYONE](https://www.youtube.com/watch?v=hrwoKO7LMzk)
* [CloudFlare - FREE Additional Security For Your Home Server!](https://www.youtube.com/watch?v=m-RYTu-Qq3A)
* [How I survived a DDoS attack](https://www.youtube.com/watch?v=VPcYMgTYQs0)

#### Step X: Itrusion Protection System (IPS)
CrowdSec is a free, open-source, and collaborative Itrusion Protection System (IPS).
Analyze behaviors, respond to attacks & share signals across the community.

* [CrowdSec](https://crowdsec.net/)
* [Pi Alert - Open Source, Self Hosted, Network Device Change Notification and Intrusion Detection](https://www.youtube.com/watch?v=oKl3WFQloE4)
* [Pi-Alert - Network Device Change Notifications](https://shownotes.opensourceisawesome.com/pi-alert-network-device-change-notifications/)

#### Step X: Ad Blockine
Clheckout setting-up-pi-hole.md

#### Step X: Setting Up WireHole
WireHole is a combination of WireGuard, PiHole, and Unbound in a docker-compose project with the intent of enabling users to quickly and easily create and deploy a personally managed full or split-tunnel WireGuard VPN with ad blocking capabilities (via Pihole), and DNS caching with additional privacy options (via Unbound).

* [WireHole: WireGuard, Pi-Hole and Unbound in Docker](https://www.youtube.com/watch?v=DOJ39lyx6Js)
* [Create Your New Reality With Wirehole And Other Awesome Automation Tools](https://hackernoon.com/create-your-new-reality-with-wirehole-and-other-awesome-automation-tools-viq3tbb)

#### Step X: Setting Up VPN
* [Cloudflare Access](https://dash.teams.cloudflare.com/2dbf9ab9f674a117b229f8c02d0cd234/onboarding)
* [Cloudflare Tunnel Setup Guide - Self-Hosting for EVERYONE](https://www.youtube.com/watch?v=hrwoKO7LMzk)
* [Free Cloudflare Tunnel To Home Assistant: Full Tutorial!](https://www.youtube.com/watch?v=4svVZGRMrsM)
* [Secure Remote Access to Home Assistant with Cloudflare Proxy](https://www.youtube.com/watch?v=AfiT6KSGXHM)

* [Stop using VPNs for privacy](https://www.youtube.com/watch?v=FMScV1Mkaok)
* [How to Make Your Own VPN (And Why You Would Want to)](https://www.youtube.com/watch?v=gxpX_mubz2A)
* [Fourteen eyes surveillance alliance explained](https://www.securitymadesimple.org/cybersecurity-blog/fourteen-eyes-surveillance-explained)

* [How To Setup pfsense OpenVPN Policy Routing With Kill Switch Using A Privacy VPN](https://www.youtube.com/watch?v=ulRgecz0UsQ)
* [OpenVPN on pfSense behind ISP router](https://forums.lawrencesystems.com/t/openvpn-on-pfsense-behind-isp-router/7887)
* [How to use your Raspberry Pi as a VPN server](https://opensource.com/article/19/6/raspberry-pi-vpn-server)
* OpenVPN: [How to Make Your Own VPN (And Why You Would Want to)](https://www.youtube.com/watch?v=gxpX_mubz2A)
* [Make Your Own VPN Pt.2 – Use It Correctly! Netflix, Torrenting, Wireguard, etc.](https://www.youtube.com/watch?v=5Tls2LRKh-c)
* [Set Up Your Own VPN at Home With Raspberry Pi! (noob-friendly)](https://www.youtube.com/watch?v=rtUl7BfCNMY)

### Homelab Dashboard with Homer
Check out `$HOME/src/homer-dashboard`


## Optional Components

### Recommended pfSense Settings
* [pfSense Configuration Recommendations](https://protectli.com/kb/pfsense-configuration-recommendations/)
* [Best Practices for pfSense Firewall Rules](https://hometechhacker.com/best-practices-for-pfsense-firewall-rules/)

### Guacamole
* [access EVERYTHING from your web browser!! (Linux and Windows Desktop, SSH) // Guacamole Install](https://www.youtube.com/watch?v=gsvS2M5knOw)
* [Meet Guacamole, Your Remote Access Gateway](https://www.youtube.com/watch?v=LWdxhZyHT_8)
* [Pi-Hosted : Manually Installing Guacamole on Portainer Part 3](https://www.youtube.com/watch?v=cKAhnf8X1lo&list=PL846hFPMqg3jwkxcScD1xw2bKXrJVvarc&index=3)

### Clonezilla (Disk Cloning)
Clonezilla is a partition and disk imaging/cloning program similar to True Image® or Norton Ghost®.
It helps you to do system deployment, bare metal backup and recovery.

* [Clonezilla](https://clonezilla.org/)
* [How to save a Clonezilla full disk image to a server/NAS over SSH](https://danielrosehill.medium.com/how-to-save-a-clonezilla-full-disk-image-to-an-nas-over-ssh-771beb37f08b)
* [PXE Boot Clonezilla Live with Synology](https://grovetech.co/blog/pxe-boot-clonezilla-live-with-synology/)
* [Using rsync to sync Clonezilla backup images to NAS (Synology DS920+)](https://www.youtube.com/watch?v=VpNlnkZRwT4)
* [Clonezilla LAN backup (over SSH): Linux host to Synology NAS](https://www.youtube.com/watch?v=cfMspUjk9ms)

### Duplicati
Duplicati is a backup client that securely stores encrypted, incremental, compressed remote backups of local files on cloud storage services and remote file servers. Duplicati supports not only various online backup services like OneDrive,[1] Amazon S3, Backblaze, Rackspace Cloud Files, Tahoe LAFS, and Google Drive, but also any servers that support SSH/SFTP, WebDAV, or FTP.

* [Duplicati a Set it and Forget it backup tool for local and remote backups of your system!](https://www.youtube.com/watch?v=N1NRvg4KaDE)
* [Setup Duplicati on Synology](https://www.youtube.com/watch?v=YVUvLZpKhQ0)

### eMail Server
By running your own email server, your data is in your own hands and on your own hardware, with no oversight from shadowy corporate entities.
* [Make Your Own Raspberry Pi Email Server](https://www.makeuseof.com/make-your-own-raspberry-pi-email-server/)
* [Docker Mailserver](https://docker-mailserver.github.io/docker-mailserver/edge/)
    * [Mail Server](https://geek-cookbook.funkypenguin.co.nz/recipes/mail/)
* [12 Best Self-Hosted Email Server Platforms to Use](https://geekflare.com/self-hosted-email-server/)


### eMail Spam Blocker
* [Spamgourmet](https://www.spamgourmet.com/index.pl)

### Remote Access to Your Home Lab
* [How to Home Lab: Part 5 - Secure SSH Remote Access](https://www.dlford.io/secure-ssh-access-how-to-home-lab-part-5/)

### Kubernetes Cluster

### Infrastructure as Code (IaC)
* [How to use infrastructure as code](https://opensource.com/article/19/7/infrastructure-code)
* [Homelab-Ansible](https://github.com/TechGeek01/Homelab-Ansible)



-------



# FiOS Service
Verizon FiOS (which stands for **Fi**ber **O**ptic **S**ervice)
is a bundled Internet access, telephone, and television service
that operates over a fiber-optic communications network.

* [Verizon FiOS FAQ](http://www.dslreports.com/faq/verizonfios)

# FiOS Optical Network Terminal (ONT)
At you house, the FiOS [Optical Network Terminal (ONT)][11] splits-out & converts
the optical fiber connection to Ethernet for Internet service, twisted pair wiring for phone service,
and coaxial cable for TV service.

# What is MoCA?
MoCA stands for Multimedia over Coaxial Alliance.
[It provides a way to use coaxial cable as Ethernet cables][10].
MoCA technology uses the existing TV cable wiring (coaxial cables) in your home to transmit data.
You use MoCA adapters to extend the coverage of your WiFi signal and to communicate with your TV settop boxes.
The [latest version of MoCA is 2.0 and there is also an upgraded version 2.5][09]
which gives you 2.0Gb/s and 2.5Gb/s respectively.

The FiOS router I have has built into it a MoCA adapter.
My service provider use the MoCA connection to route control messages to my cable TV settop boxes.

* [MoCA Made Easy!](https://www.youtube.com/watch?v=dm_Znyh7uZ0)
* [Double your Home Network Speed - Motorola MOCA Adapter](https://www.youtube.com/watch?v=i9WVH-2BjDA)
* [MoCA Networking Is A Niche Solution For Coax Lovers](https://hackaday.com/2022/11/03/moca-networking-is-a-niche-solution-for-coax-lovers/)



-------



# Replacing My FiOS Router
Much of what you see here was inspired by [NetworkChuck][05],
and my end goal is to replace my Verizon FiOS wireless router
([G-1100 FiOS Quantum Gateway Router][01]) with my own router
([Protectli Vault][02] + [Proxmox][03] + [pfSense][04]),
Ethernet Switch ([TP-Link TL-SG108E switch][06]),
and my own WiFi access point ([TP-Link EAP610 (AX1800 WiFi 6)][16]).

But really, [should I build my own router][20]?
In reality, the path leading to my decision to replace my ISP provide router is much more complicated.
It all started with [LastPass][21] increasing its service price
but without any feature improvements worth noting ... for multiple years.
This pissed me off!

So I decided I'm going to host my password management tool on my home network via [Bitwarden][22].
This begs the question, is my home network sufficiently secure to host something so import to keep secure?
So to beef up security, I pursued adding a [HAProxy or Nginx reverse proxy][23] and [Authelia][28] for authentication.
I don't think my ISP provided DNS service is helping in my security so I should move to [Cloudflare][24]
and make use of [Pi-Hole][27].
Of course my ISP provided home router has no [VLAN][25] or [Next-Generation Firewall][26] capabilities
so let remove my ISP router and replace it with [pfSense][04].
All this is complicated so let add [Proxmox][03] to virtualise everything
and put it on one host properly engineered for the task like [Protectli Vault][02]
with a dashboard like [Homer][29] to help manage all these disparate things.
And since my ISP provide router has WiFi built in, I'll need a WiFi access point.
I should replace it with the next generation, WiFi 6, via a standalone access point like [TP-Link EAP610][31].
Oh by the way, if I eliminate my ISPs router,
I then become responsible for keeping my ISP provided phone & TV service working via [MoCA][30].
Needless to say, I like a challenge and new things to learn.

## Cost & Value of Router Replacement
The estimate cost of the replacement router configuration is:

| Price | Hardware / Software       |
|-------|---------------------------|
| $ 449 | Protectli Vault           |
| $   0 | Proxmox                   |
| $   0 | pfSense                   |
| $  30 | TP-Link TL-SG108E Switch  |
| $  81 | MoCA Network Adapter      |
| $ 100 | TP-Link EAP610 WiFi 6     |
|       |                           |
| $ 660 | Total Cost                |

The lease cost of my FiOS Quantum Gateway Router is about $15/month ($180/yr).
This is about a 4 year pay back period, so not a great ROI.
The real value for me is the complete control and freedom I have to configure my home network.
To understand the full potential out of this setup, consider this:

* The pfSense firewall/router will provide a much greater number of features than the FiOS router.
In fact, it can be loaded up with many of the [Next-Generation Firewall][26]
capabilities that are consider a must today for enhanced security.
* I will not dedicate the Protectli Vault to hosting pfSense alone, but instead I will run pfSense in a Proxmox VM.
This gives me the opportunity to run addition virtual machines and containers on the Protectli Vault.
* I plan to self-host website and provide other Internet accessable services on my home network.
This will require things like Nginx Proxy Manager which could could run in Proxmox on the Protectli Vault.
This is a perfect place for it for security reasons.
* The more advanced WiFi 6 access point will future proof my WiFi and provide the capacity needed for
the many IoT device I wish to support.
* pfSense and the TP-Link switch will support VLANs giving me the ability to isolate devices,
most notable the IoT device,
onto seperate virtual networks giving me additional security.

## First, Do a Proof of Concept
The first question you have to ask,
is all this possible, particularly can you not disrupt your phone & TV service?
It is very clear to me everything else will work because its all open source tools and IP networking.
I researched the topic and many of the forums gave you concern since about its viability,
but this was balanced with success stories.
After much research, I focused in on some cases which showed real success
and had a configuration that was like my home.

* [Stop Paying FIOS Rental FEE! How to install MOCA adapter & Keep your FIOS one TV cable boxes working](https://www.youtube.com/watch?v=YqXD_4f8wAA)
* [To Bridge or Not to MoCa Bridge your Verizon FIOS Router](https://www.youtube.com/watch?v=bgW4LSSp_xY)




-------




# Replace My Verizon FiOS Router
So a complicating factor is that I'm using my FiOS service to also provide me TV and IP-telephone service.
A concern is that FiOS provided wireless router is critical to the proper operation of the TV service and telephony.
The G-1100 FiOS router has connections for Ethernet connection to the WAN and the TV coax cable,
implying to me their is some interdependence.
Turns out, the TV coax and Ethernet WAN need to be coupled but this can be handle via a [MoCA 2.5 Network Adapter][07].

An additional goal of mine is to **not** put my TV and telephony service in limbo while I make this transition.
I need to plot a course of action where I can get this done in phases with an easy fallback plan if things go wrong.
A simple description of my plan is:

My goal is to replicate my current FiOS router LAN on the new router with the same
WiFi SSID & Password, port forwarding, etc. so everything should come up on the new router.

1. **Set-up New Router:** Set-up and test the new router configuration & test
(Protectli Vault + Switch + Proxmox + pfSense + WiFi access point)
as a subnet on my existing LAN.
Nothing new like VLANs or pfSense packages installed.
I'll use this setup to learn my way around Proxmox, pfSense, etc.
and make all my mistakes without messing up my home LAN.
2. **Swap Out FiOS Router Hardware:** Remove the FiOS router from the network and replace it with the new router.
Install the MoCA device, change the IP address scheme to what was used on the FiOS router,
copy over the port forwarding scheme from the FiOS router to the new router.
3. **Power Up New Router & Test:** If all goes well, all the current LAN devices
should come up on the Ethernet / WiFi networks
and should work just like they did before (after some devices being power cycles).

>**NOTE:** I did not include a [MoCA filter][13] within my setup.
>The FiOS original setup didn't include it, so it might have been built into the FiOS router,
>or maybe at the Optical Network Terminal (ONT).
>This [article][14] advices not to use a MoCA filter.
>I did not include it and I saw no problems by leaving it off.

From here I will methodically modify the pfSense and other components to establish VLANs and other services,
all the while taking care to create backups so I can fallback if I break something.

This plan was formulated after much research on the Internet.
I found the information I needed to accomplish this from these sources below.
Make sure to watch the video ["How to use your own router with Verizon FIOS Internet & TV"][15]
since its an excellent source of information.

Sources:

* [How to use your own router with Verizon FIOS Internet & TV][15]
* [Verizon FIOS Phone, Data and TV service with your own Router](https://www.youtube.com/watch?v=2q50b8KwAZ8)
* [Verizon FiOS Use Your Own Router](https://www.youtube.com/watch?v=w2Jr_0P0zwY)
* [Using your own router with Verizon FiOS](https://forums.verizon.com/t5/Fios-Internet/Using-your-own-router-with-Verizon-FiOS/td-p/851632)
* [Replace Fios Router with Your Router](https://www.arhea.net/posts/2020-01-012-fios-own-router.html)
* [pfSense and Verizon FiOS](https://www.ianmf.com/2020/02/17/pfsense-and-verizon-fios/)

## Preparation

#### Step X: Measure Internet Speed - DONE
Lets baseline the speed of my current Internet connection.
We can do this via the [speedtest.net][17] site  or
use its command line tool [`speedtest-cli`][18] for testing internet bandwidth.
Lets install `speedtest-cli`:

```bash
# https://www.speedtest.net

# install speedtest-cli
sudo apt-get -y install python3-pip
sudo -H pip3 install speedtest-cli
```

From within my Linux desktop,
lets do the speed test using `speedtest-cli`:

```bash
# https://www.speedtest.net

# internet speed test
$ date ; speedtest-cli | grep -E 'Download|Upload'
Sat May 28 10:09:32 AM EDT 2022
Download: 731.17 Mbit/s
Upload: 641.70 Mbit/s
```

Sources:
* [How to Run a Speed Test on pfSense](https://www.wundertech.net/how-to-run-a-speed-test-on-pfsense/)

#### Step X: Gather Current Router Configuration - DONE
Before starting, you need to collect information about how you home network is currently configured.
Using my browser, I navigated to my FiOS Router via `https://192.168.1.1`
I then created PDF snapshots of the multiple UI displays for firewall rules, port forwarding, etc.
Some of this configurations,
particularly those that support your TV and phone service will need to be replicated in your new setup.

We need to configure port forwarding so that our DVR service works properly.
Note: different models of STBs require different ports. Refer to the “pre-work” before getting started.

FiOS requires a TCP port to be opened for each box and a UDP port opened your DVR to enable service.

The FiOS Router listed the following informtion concerning port forwarding:

```
Device             IP-Address:Port       Applications            Ports Forwarded      Status
localhost          127.0.0.1             Verizon Fios Service    TCP Any -> 4567      Active
                   192.168.1.104:63145   tr69_000                UDP Any -> 63145     Active
                   192.168.1.107:7547    tr69_001                TCP Any -> 35000     Active
UnNamed-Client-1   192.168.1.106:7547    tr69_002                TCP Any -> 35001     Active
UnNamed-Client     192.168.1.105:7547    tr69_003                TCP Any -> 35002     Active
Living-Room-SetTop 192.168.1.108:7547    tr69_004                TCP Any -> 35003     Active
Jennies-iPad-2     192.168.1.152:63145   tr69_005                UDP Any -> 63146     Active
                   192.168.1.225:63145   tr69_006                UDP Any -> 63147     Active
```

I translated this information to mean

```
                                  WAN            LAN
Device            Protocol    External Port  Internal Port	Note / Description
Living-Room-SetTop  TCP          35003           7547    	This must be connected to the main DVR in the home.
1-SetTop            TCP          35002           7547
2-SetTop            TCP          35001           7547
3-SetTop            TCP          35000           7547
?-SetTop            UDP          63145          63145
?-SetTop            UDP          63145          63146
?-SetTop            UDP          63145          63147
```

The FiOS router has the following information concerning the status of DHCP:

```
Host Name                    IPv4 Address     Source
amazon-91ca99692             192.168.1.190    DHCP
Living-Room                  192.168.1.108    DHCP
TVA0044ALKVTMBM              192.168.1.184    DHCP
amazon-e2244b317             192.168.1.185    DHCP
Jennies-iPad-2               192.168.1.152    DHCP
Chromecast                   192.168.1.95     DHCP
UnNamed-Client               192.168.1.105    DHCP
HarmonyHub                   192.168.1.36     DHCP
Jeffrey-s-Galaxy-Note20-5G   192.168.1.84     DHCP
Philips-Hue                  192.168.1.34     DHCP
Aura-0633                    192.168.1.61     DHCP
UnNamed-Client-1             192.168.1.106    DHCP
Jeffrey-s-Galaxy-Tab-S6-Lite 192.168.1.87     DHCP
new-host-5                   192.168.1.198    DHCP
hubv2-24fd5b0000036206       192.168.1.191    DHCP
new-host-4                   192.168.1.9      DHCP
pfSense                      192.168.1.12     DHCP
new-host-3                   192.168.1.60     DHCP
new-host-2                   192.168.1.89     DHCP
desktop                      192.168.1.29     DHCP
ESP_D5E627                   192.168.1.192    DHCP
```

Actively scaning the network produces the folling results:

```bash
# actively ping device 3 times with 10 milisec delay between scans
# and then passively sniff network traffic
$ sudo netdiscover -c 3 -s 10 -L -N -r 192.168.1.0/24
[sudo] password for jeff:
 192.168.1.1     48:5d:36:2e:ee:06      1      60  Verizon
 192.168.1.198   f8:77:b8:b7:a2:26      1      60  Samsung Electronics Co.,Ltd
 192.168.1.12    02:19:d3:92:94:83      1      60  Unknown vendor
 192.168.1.9     cc:9e:a2:17:b8:d8      1      60  Amazon Technologies Inc.
 192.168.1.29    94:db:c9:51:10:ca      1      60  AzureWave Technology Inc.
 192.168.1.34    00:17:88:4a:15:15      1      60  Philips Lighting BV
 192.168.1.36    00:04:20:fb:bd:d7      1      60  Slim Devices, Inc.
 192.168.1.48    56:8e:60:fe:8c:b2      1      60  Unknown vendor
 192.168.1.60    a2:1d:5c:6e:b1:b0      1      60  Unknown vendor
 192.168.1.61    04:c2:9b:83:1a:9b      1      60  Aura Home, Inc.
 192.168.1.89    7c:78:b2:29:c8:be      1      60  Wyze Labs Inc
 192.168.1.95    f4:f5:d8:4d:34:da      1      60  Google, Inc.
 192.168.1.105   2c:58:4f:b1:0a:42      1      60  ARRIS Group, Inc.
 192.168.1.106   2c:58:4f:b0:e0:53      1      60  ARRIS Group, Inc.
 192.168.1.108   8c:61:a3:97:8e:1f      1      60  ARRIS Group, Inc.
 192.168.1.185   24:4c:e3:36:9e:ad      1      60  Amazon Technologies Inc.
 192.168.1.184   50:e0:85:42:b8:32      1      60  Intel Corporate
 192.168.1.191   24:fd:5b:03:61:dd      1      60  SmartThings, Inc.
 192.168.1.192   5c:cf:7f:d5:e6:27      1      60  Espressif Inc.
 192.168.1.196   9e:da:c4:7d:09:63      1      60  Unknown vendor
 192.168.1.190   68:54:fd:84:18:e3      1      60  Amazon Technologies Inc.
 192.168.1.201   90:09:d0:00:4e:29      1      60  Synology Incorporated
 192.168.1.202   00:e0:67:2c:66:0e      1      60  eac AUTOMATION-CONSULTING GmbH
 192.168.1.200   94:db:c9:51:10:ca      1      60  AzureWave Technology Inc.

-- Active scan completed, 24 Hosts found. Continuing to listen passively.

 0.0.0.0         90:09:d0:00:4e:29      1      60  Synology Incorporated
 0.0.0.0         56:8e:60:fe:8c:b2      1      60  Unknown vendor
 0.0.0.0         a2:1d:5c:6e:b1:b0      1      60  Unknown vendor
 169.254.18.61   a2:1d:5c:6e:b1:b0      1      60  Unknown vendor
 0.0.0.0         2c:58:4f:b1:0a:42      1      60  ARRIS Group, Inc.
 0.0.0.0         2c:58:4f:b0:e0:53      1      60  ARRIS Group, Inc.
 0.0.0.0         8c:61:a3:97:8e:1f      1      60  ARRIS Group, Inc.
 0.0.0.0         9e:da:c4:7d:09:63      1      60  Unknown vendor
 192.168.1.84    26:49:94:3d:68:d0      1      60  Unknown vendor
```

#### Step X: Change LAN IP TCP/IP Subnet - DONE
My FiOS router is creating a home IP network using the private subnet `192.168.1.0`.
When I establish my new router, I don't want to have to resent all my currently active devices.
I want the new network to have the same WiFi SSID and use the private subnet `192.168.1.0`.
Keep in mind that during the experimenting,
I set the SSID and subnet differently (in my case `test-wifi6` and `192.168.2.0`).
So now you should change these three things to be equivalent to your current FiOS router home network.

1. **Change SSID to 74LL5:**
Go into EAP610 WiFi 6 Access Point portal.
Select **Wireless** > **Edit (icon)** and change SSID to 74LL5.
2. **Change LAN Subnet to 192.168.1.0:**
Go to pfSense console UI on Proxmox.
Select **2) Set interface(s) IP address** > **2 - LAN**.
Enter the LAN address `192.168.1.1/24`.
(**NOTE:** Don't enter `192.168.1.0/24` since your effectively entering the browser UI for pfSense and **0** is reserved.)
Enable DHCP with start address of `192.168.1.10` and final address of `192.168.1.199`.
3. **Reboot pfSense:**
Now reboot pfSense to make sure changes take effect via **5) Reboot system**.

#### Step X: Release DHCP Lease - DONE
Prior to swapping out your FiOS router for the new one,
you'll need to release the DHCP lease on the FiOS router.

Here are the FiOS router selections to do the DHCP lease release.
Make the following selection on the FiOS router UI (`http://192.168.1.1/`):
Select **My Network** > **Network Connections** > **Broadband Connection** > **Settings**
Scroll down and click **Release** right of "DHCP Lease" and click **Apply**.

Disconnect the Ethernet cable of the FiOS router immediately to prevent it from re-requesting a DHCP lease.
Next you immediately plug the Ethernet cable into the WAN port of your new router and power it on.
Your new router should obtain a fresh DHCP lease and be connected immediately.

#### Step X: Move Ethernet Connections to Switch - DONE
Next, we have to perform some hardwire (aka Ethernet) re-configuration
within the test confugration
(Protectli Vault + Proxmox + pfSense + TP-Link Switch + TP-Link EAP610)
to reflect the equivalent of the FiOS Router
(G-1100 FiOS Quantum Gateway Router).
The re-configuration required are:

1. Move the WAN connection to the FiOS router to the Proxmox WAN interface.
2. Move the Proxmox Management GUI to to the pfSense LAN (aka TP-Link TL-SG108E switch).
3. Move any of your hardwired connections off the FiOS router
to the  pfSense LAN (aka TP-Link TL-SG108E switch).
This will allow your hardwared home devices obtain their IP address from the pfSense router.

#### Step X: configure Proxmox and PfSense VM so that all network requests go through PfSense
* [Management interface to internal network](https://forum.proxmox.com/threads/management-interface-to-internal-network.73862/)
* [How to configure Proxmox and PfSense VM so that all network requests go through PfSense](https://forum.proxmox.com/threads/how-to-configure-proxmox-and-pfsense-vm-so-that-all-network-requests-go-through-pfsense.64021/)
* [How to Change Primary Proxmox VE IP Address](https://www.servethehome.com/how-to-change-primary-proxmox-ve-ip-address/)
* [Netgate Docs: Virtualizing with Proxmox® VE](https://docs.netgate.com/pfsense/en/latest/recipes/virtualize-proxmox-ve.html)
* [Virtualize pfSense Router in Proxmox](https://www.youtube.com/watch?v=Gh638KnNubo)
* [How to Install PfSense on Proxmox? | Step by Step.](https://getlabsdone.com/how-to-install-pfsense-on-proxmox-step-by-step/)
* [PROXMOX with pfsense VM as home router](https://forum.proxmox.com/threads/proxmox-with-pfsense-vm-as-home-router.41735/)
* [How to Virtualize Your Home Router / Firewall Using pfSense](https://www.youtube.com/watch?v=hdoBQNI_Ab8)
* [Router (pfsense) node with 2 NIC's](https://www.reddit.com/r/Proxmox/comments/t5vmoi/router_pfsense_node_with_2_nics/)
* [Dedicate NIC for Management Console/GUI](https://forum.proxmox.com/threads/dedicate-nic-for-management-console-gui.10107/)
* [Virtualised pfSense on Proxmox with Open vSwitch](https://webworxshop.com/virtualised-pfsense-on-proxmox-with-open-vswitch/)
* [How to Access Management GUI w/pfSense??](https://www.reddit.com/r/Proxmox/comments/ad27n3/how_to_access_management_gui_wpfsense/)
* [Management interface to internal network (vmbrX)](https://www.reddit.com/r/Proxmox/comments/i2116w/management_interface_to_internal_network_vmbrx/)
    * [Proxmox + pfSense on one public IP](https://blog.kton.me/post/152460845498/proxmox-pfsense-on-one-public-ip)

* [Physical or Virtual? A Silent 4x 2.5GbE Proxmox VE pfSense and OPNsense Box](https://www.youtube.com/watch?v=IJhlqb4iGn4)

#### Step X: Measure Internet Speed
Lets do another Internet speed test using `speedtest-cli`,
but this time from desktop and Proxmox to see what we get.

```bash
# https://www.speedtest.net

# internet speed test - desktop
$ date ; speedtest-cli | grep -E 'Download|Upload'
Sun May 29 10:19:39 AM EDT 2022
Download: 162.34 Mbit/s
Upload: 419.01 Mbit/s

# internet speed test - proxmox
$ date ; speedtest-cli | grep -E 'Download|Upload'
Sun 29 May 2022 10:19:11 AM EDT
Download: 93.43 Mbit/s
Upload: 95.03 Mbit/s
```

#### Step X: Checking Ethernet Cables
For my Ethernet networking,
I'm using a mixture of cables I have collected over the years,
including Cat5, Cat5e, and Cat6.
There are many differences between CAT5 and CAT6 cables,
not least of which is performance.
When choosing which one to use,
one must first consider the amount of bandwidth the cable must support:

* CAT5 can support up to 100 Mbps at a 11 MHz bandwidth
* CAT5e can support up to 1000 Mbps at a 100 MHz bandwidth
* CAT6 can support up to 1000 Mbps (1 Gbps) at a 250 MHz bandwidth
* Cat6a, a newer version of CAT6, support up to 10 Gbps at a 500 MHz bandwidth
* Cat7 can support up to 10 Gbps at a 600 MHz bandwidth
* Cat7a can support up to 10 Gbps at a 1000 MHz bandwidth

In residential setting,
CAT5e is generally believed to be more than capable of supporting the required bandwidth.
In fact, CAT5e is likely to support speeds faster than what the Internet connection can provide.
You'll pay a [20% to 30% premium][19] for Cat6,
but it might be worth it to future proof your network.

* [Cat5 vs. Cat6 Ethernet Cables: What's Best for You?](https://www.cdw.com/content/cdw/en/articles/hardware/cat5-vs-cat6-ethernet-cables.html)
* [What are the differences between CAT5 and CAT6 cables?](https://cablesys.com/updates/differences-between-cat5-cat6-cables/)

#### Step X: Get TV Service Working
If you have FiOS TV, your new router should be able to reach the Internet.
However, you'll notice that your TV service will have some issues,
such as the guide not working, and on demand not functioning either.

These issues are because the set top boxes rely on
MoCA technology to get their Internet access.
Since the FiOS router has been disconnected, its embedded MoCA adapter is gone.
This is remedied via adding the standalone MoCA adapter.

Simply connect the Coax cable from your FiOS router to the MoCA adapter,
and then connect an Ethernet cable between MoCA adapter's Ethernet port and a LAN port on your new router.
Reboot the set top boxes after the MoCA adapter has been connected and ensure they function as intended.

#### Step X: Return FiOS Router to Verizon
Once you elect to go with your own router,
you have 30 days to return your FiOS router to Verizon,
or they will charge you a rental fee.
Make sure you return the power cord along with the router.
And get a receipt from the store confirming that your equipment has been returned.



-----



# Current Configuration
# Test Configuration
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
* Subnet 192.168.2.0/24               * ----- Proxmox Mgmt. Browser UI
*     |     |                         *          (192.168.202:8006)
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
 X   DHCP Issued IP Address
```

# Target Configuration



-----



# Setup Router
I need to migrate some of the settings on my current router to the new router using pfSense.
Typical things that need migrating from my old router are:
DHCP Reservations Range, Static IP Addresses, DNS Resolvers, Firewall Rules, Port Forwards, Dynamic DNS Settings.
I recorded this information by capturing PDFs of my old routers browser pages.

Sources:

* [How and Why I Built a Virtual Router](https://hometechhacker.com/how-why-i-built-virtual-router/)
* [Planning Your pfSense Router Install and Configuration](https://hometechhacker.com/planning-your-pfsense-router-install-and-configuration/)

## Install Proxmox on Protectli Vault
Follow the procedures in `setting-up-proxmox.md`.
* [Proxmox VE on the Vault](https://protectli.com/kb/proxmox-ve-on-the-vault/)

## Install pfSense
Follow the procedures in `setting-up-pfsense.md`.

* [your home router SUCKS!! (use pfSense instead)](https://www.youtube.com/watch?v=lUzSsX4T4WQ)
* [pfSense CE on the Vault](https://protectli.com/kb/how-to-install-pfsense-ce-2-4-on-the-vault-2/)
* [NIC port numbering and naming](https://protectli.com/kb/nic-port-numbering-and-naming/)

## Configure Switch
For my switch, I purchased the [TP-Link TL-SG108E Version 6.6][06].
Download the user guide, configuration utility, and firmware update (none at the time of my purchase)
at [TP-Link's download site][08].

* [TL-SG108E User Guide](https://static.tp-link.com/res/down/doc/TL-SG108E_V2_UG.pdf)
* [TL-SG108E Installation Guide](https://static.tp-link.com/res/down/doc/TL-SG105E_V2_IG.pdf)
* [p-link - TL-SG108E - Just cheap managed switches for me from now on!](https://www.youtube.com/watch?v=x1-7_cbov4s)
* [TL-SG108E Unboxing and BASIC Setup Tutorial (TP-Link Smart Ethernet Switch)](https://www.youtube.com/watch?v=8V3ftwdV3Jg)


## Configure Protectli Vault

#### Step X: Configuring Optional Ports
Here we will covers how to enable the Protectli Vault's optional ports in pfSense.
The Optional Ports are labeled “OPTx” on the Vault.
The LAN ports default private IP addressing scheme is `192.168.1.x`.
The Optional ports are configuration as sub-domains:
OPT1 is `192.168.1.202` and OPT2 is `192.168.3.1`.
You can enabling the OPT ports to be a DHCP server,
establish Firewall rules, and other features you would expect of a router.

* [pfSense® Optional Port Configuration](https://protectli.com/kb/pfsense-optional-port-configuration/)
* [How to Enable LAN Bridge with pfSense](https://protectli.com/kb/how-to-enable-lan-bridge-with-pfsense/)



------



# Remote Access of Homelab
* [Proxmox remote access – Here’s how to secure it](https://bobcares.com/blog/proxmox-remote-access/)



------



# NetBox
* [Installing NetBox 10 minutes! WHAAAAAT?!?](https://www.youtube.com/watch?v=uHMXZpXpDvc)
* [NetBox - Open Source Network Design and Mapping Software from homelab to network engineers](https://www.youtube.com/watch?v=sHvMyRHA7sY)
* [NetBox Documentation](https://docs.netbox.dev/en/stable/)

# HomeBox
* [HomeBox](https://hay-kot.github.io/homebox/)
* [Keep Track of Your Belongings by Self-Hosting HomeBox on Raspberry Pi](https://www.makeuseof.com/raspberry-pi-homebox-track-belongings-self-hosting/)



------



# Uptime Kuma
* [The BEST Home Server Uptime Monitoring!](https://www.youtube.com/watch?v=tIazVdhsSqQ)
* [Monitor Self-Hosted Websites and Projects on Raspberry Pi With Uptime Kuma](https://www.makeuseof.com/raspberry-pi-monitor-self-hosted-websites-projects-uptime-kuma/)



------



#### Step X: Configure pfSense

#### Step X: Wire Up The Network

#### Step X: Configure Port Forwarding



--------



[01]:https://www.verizon.com/about/sites/default/files/fios-qgr-userguide140925.pdf
[02]:https://protectli.com/vault-4-port/
[03]:https://www.proxmox.com/en/
[04]:https://www.pfsense.org/
[05]:https://www.youtube.com/watch?v=lUzSsX4T4WQ
[06]:https://www.tp-link.com/us/business-networking/easy-smart-switch/tl-sg108e/
[07]:https://www.screenbeam.com/products/ecb6250/
[08]:https://www.tp-link.com/us/support/download/tl-sg108e/v6.6/
[09]:https://us.hitrontech.com/learn/how-is-moca-2-5-different-from-moca-2-0/
[10]:https://www.youtube.com/watch?v=DH7pnjxIui8
[11]:https://www.allconnect.com/blog/what-is-an-optical-network-terminal
[12]:https://haydenjames.io/home-lab-beginners-guide-hardware/
[13]:https://us.hitrontech.com/learn/do-i-need-a-moca-filter-where-do-i-place-it/
[14]:https://www.dslreports.com/forum/r31415145-ONT-FiOS-MoCA-Filter-Question
[15]:https://www.youtube.com/watch?v=VmBEgMR-awA
[16]:https://hwp.media/articles/review_of_tp_link_eap620_hd_wi_fi_6_ax1800_access_point/
[17]:https://www.speedtest.net/
[18]:https://github.com/sivel/speedtest-cli
[19]:https://www.versatek.com/cat5e-cat6-cat6a-which-ethernet-cabling-solution-is-best-for-you
[20]:https://www.youtube.com/watch?v=Yq9NtTS90AE
[21]:https://www.lastpass.com/
[22]:https://bitwarden.com/
[23]:https://nginxproxymanager.com/
[24]:https://www.cloudflare.com/
[25]:https://www.n-able.com/blog/what-are-vlans
[26]:https://www.sunnyvalley.io/docs/network-security-tutorials/next-generation-firewall
[27]:https://pi-hole.net/
[28]:https://www.authelia.com/
[29]:https://github.com/bastienwirtz/homer
[30]:https://www.truecable.com/blogs/cable-academy/moca-vs-ethernet
[31]:https://www.tp-link.com/baltic/business-networking/omada-sdn-access-point/eap610/
[32]:
[33]:
[34]:
[35]:
[36]:
[37]:
[38]:
[39]:
[40]:
