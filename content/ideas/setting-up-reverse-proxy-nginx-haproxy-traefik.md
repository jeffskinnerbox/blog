<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----



ehCo91x6GESrVvTtckjzbECgHUdEXO74tlnvTj8Z

**NOTE:** During setup testing, make sure:
* "Always Use HTTPS" feature of Cloudflare is "off"
* Proxied is turned off
Once tested via HTTP is solid, setup Nginx links with SSL certs.
Only then, turn on Proxied and "Always Use HTTPS"


```
Home Router
            |   Desktop                                                           |
            |            |  Docker Container |   Vagrant VM                       |
            |            |                   |               |   Docker Container |
                                                  Webserver       Nginx Proxy Mgr
  port 80  --> port 9080 -->                       port 80   -->     port 80
  port 443 --> port 9443 -->                       port 443  -->     port 443
                                                   port 81   -->     port 81                 Admin UI

                                Netdata                              Netdata

                                Portainer                            Portainer
               port 8000 -->    port 8000                                                    Edge Agent
               port 9000 -->    port 9000                                                    Admin UI
                                                   port 8000 -->     port 8000               Edge Agent
                                                   port 9000 -->     port 9000               Admin UI

                                                                     Bitwarden
                                                   port 8080 -->     port 80                 Admin UI
                                                   port 3012 -->     port 3012               websocket traffic

                                                                     Authelia


|            Cloudflare                              |             Home Router               |    VM     |
|                DNS                                 |              firewall                 | firewall  |   Nginx Proxy Mgr
  jeffskinnerbox.me         --> My Home External IP --> Port Forwards to 192.168.33.10:xxxx --> open ?? ---> Proxy Host to https://github.com
  www.jeffskinnerbox.io     --> My Home I ExternalP --> Port Forwards to 192.168.33.10:xxxx --> open ?? ---> Proxy Host to https://github.com
  netdata.jeffskinnerbox.io --> My Home I ExternalP --> Port Forwards to 192.168.33.10:xxxx --> open ?? ---> Proxy Host to https://app.netdata.cloud/spaces/jeff-irland-space/rooms/general/overview
  bitwarden.jeffskinnerbox.io --> My Home I ExternalP --> Port Forwards to 192.168.33.10:xxxx -->open ?? ---> Proxy Host to 192.168.33.10:xxxx
```



-----------



# Traefik Hub
* [Traefik Hub: How to Publish and Secure Your Containers Instantly // Traefik Labs](https://www.youtube.com/watch?v=zUiRAMjn1lo)
* [Control your home automation remotely with Raspberry Pi and Traefik Hub](https://opensource.com/article/22/9/home-automation-traefik-raspberry-pi)


# Establish Your Internet Access Environment
For proper operation of any Internet facing service,
enabling [HTTPS (Hypertext Transfer Protocol Secure)][04] is required.
Many services recommend (required in many cases) the enablement of HTTPS
via a [reverse proxy][56] that handles HTTPS connections to increase security and performance.
A reverse proxy is a server that sits in front of your web servers (or any outward facing service)
and forwards client requests to the web servers.
In layman’s terms, you only have to expose one server (using ports 80/443)
and will be able to expose as many web services as you want via the reverse proxy.
This allows us to create more services on our network and expose them to the internet
WITHOUT opening more ports for those services to be accessed remotely.

We'll examine three well established reverse proxies here:

* [Nginx Proxy Manager (NPM)][01] - most popular, light & easy to use, lacks features often desired by commercial users
* [HAProxy][02] - runner up, fills in many of the void within NPM
* [Traeflk][03] - rising star, a "modern" reverse proxy addressing orchestrated containers, not the fastest of the bunch


* [NGINX vs Traefik vs HAProxy](https://andreidascalu.medium.com/nginx-vs-traefik-vs-haproxy-cc99546f676a)
* [TWO YEARS LATER – DID TRAEFIK REPLACE NGINX AND HAPROXY?](https://arador.com/two-years-later-did-traefik-replace-nginx-and-haproxy/)
* [Best for Homelab? Traefik vs Nginx Proxy Manager](https://www.youtube.com/watch?v=scrtJ1U4wJU)

* [Proxy vs. Reverse Proxy (Explained by Example)](https://www.youtube.com/watch?v=ozhe__GdWC8)
* [How to Setup a Reverse Proxy on Home Network](https://www.youtube.com/watch?v=QcnAqN_Ihqk)
* [Nginx Proxy Manager - How-To Installation and Configuration](https://www.youtube.com/watch?v=P3imFC7GSr0&t=129s)
* [Docker and Running your self-hosted applications in a more secure way behind a reverse proxy.](https://www.youtube.com/watch?v=8T68pB_Fkm4)
* [Nginx Proxy Manager is a free, open source, GUI for the Nginx Reverse Proxy making it easy to use](https://www.youtube.com/watch?v=RBVcnxTiIL0)
* [Putting it All Together - Docker, Docker-Compose, Nginx Proxy Manager, and Domain Routing - How To](https://www.youtube.com/watch?v=cjJVmAI1Do4)



----



# Secure Web Application Gateway (SWAG)
* [Introducing SWAG - Secure Web Application Gateway](https://www.linuxserver.io/blog/2020-08-21-introducing-swag)
* [SWAG setup](https://docs.linuxserver.io/general/swag)
* [linuxserver/swag](https://github.com/linuxserver/docker-swag)



----



# Nginx Proxy Manager
[Nginx Proxy Manager][01] is the go-to tool to establish a reverse proxy.
Using Docker, I'm going to describe how to install Nginx as a proxy manager.
Alternatively, you can use a already established reverse proxy if it exists.

Why?

* [Proxy vs. Reverse Proxy (Explained by Example)](https://www.youtube.com/watch?v=ozhe__GdWC8)
* [How to Setup a Reverse Proxy on Home Network](https://www.youtube.com/watch?v=QcnAqN_Ihqk)
* [Docker and Running your self-hosted applications in a more secure way behind a reverse proxy.](https://www.youtube.com/watch?v=8T68pB_Fkm4)
* [Nginx Proxy Manager - How-To Installation and Configuration](https://www.youtube.com/watch?v=P3imFC7GSr0&t=129s)
* [Additional Self-Hosted Security with Authelia on NGINX Proxy Manager](https://www.youtube.com/watch?v=4UKOh3ssQSU)

Nginx Proxy Server
* [How To Install Nginx Proxy Manager in Docker on Ubuntu 20.04](https://smarthomepursuits.com/how-to-install-nginx-proxy-manager-in-docker/)
* [What is Nginx | easy way](https://www.youtube.com/watch?v=WuH0T9FHDZ4)
* [NGINX Linux Server | Common Configurations](https://www.youtube.com/watch?v=MP3Wm9dtHSQ)
* [Nginx Proxy Manager - How-To Installation and Configuration](https://www.youtube.com/watch?v=P3imFC7GSr0)
* [Proxy vs reverse proxy vs load balancer (2020) | Explained with real life examples](https://www.youtube.com/watch?v=MiqrArNSxSM)
* [Reverse proxy nginx letsencrypt tutorial](https://www.youtube.com/watch?v=DyXl4c2XN-o)
* [Reverse proxy with NGINX and letsencrypt tutorial](https://www.the-digital-life.com/nginx-reverse-proxy/)
* [create short local URLs for your internal self-hosted services](https://www.youtube.com/watch?v=6aaSjwJhOog)
* [Secure Your Self Hosting with Fail2Ban + Nginx Proxy Manager + CloudFlare](https://www.youtube.com/watch?v=Ha8NIAOsNvo)

## See ~/src/docker-containers/nginx-proxy-mgr


----



# HAProxy
* [How To Setup ACME, Let's Encrypt, and HAProxy HTTPS offloading on pfsense](https://www.youtube.com/watch?v=gVOEdt-BHDY)
* [HAProxy Crash Course (TLS 1.3, HTTPS, HTTP/2 and more)](https://www.youtube.com/watch?v=qYnA2DFEELw)


----



# Traefik
* [Funky Penguin's Geek Cookbook: Traefik](https://geek-cookbook.funkypenguin.co.nz/docker-swarm/traefik/)

* [How to Install and Setup Traefik with CloudFlare Using Your Own Domain](https://www.youtube.com/watch?v=b83S_N1kkJM)
* [Put Wildcard Certificates and SSL on EVERYTHING - Traefik Tutorial](https://www.youtube.com/watch?v=liV3c9m_OX8)

* [Best for Homelab? Traefik vs Nginx Proxy Manager](https://www.youtube.com/watch?v=scrtJ1U4wJU)
* [Is this the BEST Reverse Proxy for Docker? // Traefik Tutorial](https://www.youtube.com/watch?v=wLrmmh1eI94&t=707s)
* [Self-Hosting Your Homelab Services with SSL -- Let's Encrypt, MetalLB, Traefik, Rancher, Kubernetes](https://www.youtube.com/watch?v=pAM2GBCDGTo)
* [How To Use Traefik as a Reverse Proxy for Docker Containers (One Docker Host) 2021](https://www.youtube.com/watch?v=JYZDzcurX3I)

* [Traefik v2.6+ | How to Install and Why You Should (plus Authelia, Traefik Pilot)](https://www.youtube.com/watch?v=pU7JvIrthxg)
    * [Traefik v2.6+](https://docs.ibracorp.io/traefik/)

## CrowdSec
* [CrowdSec](https://www.crowdsec.net/)
* [Blocking Malicious Connections With CrowdSec and SWAG](https://www.linuxserver.io/blog/blocking-malicious-connections-with-crowdsec-and-swag)
* [Taking a look at CrowdSec: Installation & Example Scenario](https://www.youtube.com/watch?v=QK-Fkg-88rU)
* [Boosting your Linux Server Security with CrowdSec](https://www.youtube.com/watch?v=WXHQY90Ms-g)
* [Open Source & Collaborative Security with CrowdSec and Traefik - CrowdSec & Traefik Tutorial](https://www.youtube.com/watch?v=-GxUP6bNxF0)
* [CrowdSec: Open Source Collaborative Community Security](https://www.youtube.com/watch?v=2Ec-FYmK4zg)
* []()



----




Nginx Proxy Server
* [What is Nginx | easy way](https://www.youtube.com/watch?v=WuH0T9FHDZ4)
* [NGINX Linux Server | Common Configurations](https://www.youtube.com/watch?v=MP3Wm9dtHSQ)
* [Nginx Proxy Manager - How-To Installation and Configuration](https://www.youtube.com/watch?v=P3imFC7GSr0)
* [Proxy vs reverse proxy vs load balancer (2020) | Explained with real life examples](https://www.youtube.com/watch?v=MiqrArNSxSM)
* [Reverse proxy nginx letsencrypt tutorial](https://www.youtube.com/watch?v=DyXl4c2XN-o)
* [Reverse proxy with NGINX and letsencrypt tutorial](https://www.the-digital-life.com/nginx-reverse-proxy/)
* [create short local URLs for your internal self-hosted services](https://www.youtube.com/watch?v=6aaSjwJhOog)

Sources:
* [Let's Install: Nginx Proxy Manager](https://www.youtube.com/watch?v=qXSrp_Q2pRY)
* [Nginx Proxy Manager is a free, open source, GUI for the Nginx Reverse Proxy making it easy to use](https://www.youtube.com/watch?v=RBVcnxTiIL0)

Nginx Proxy Server
* [What is Nginx | easy way](https://www.youtube.com/watch?v=WuH0T9FHDZ4)
* [NGINX Linux Server | Common Configurations](https://www.youtube.com/watch?v=MP3Wm9dtHSQ)
* [Nginx Proxy Manager - How-To Installation and Configuration](https://www.youtube.com/watch?v=P3imFC7GSr0)
* [Proxy vs reverse proxy vs load balancer (2020) | Explained with real life examples](https://www.youtube.com/watch?v=MiqrArNSxSM)
* [Reverse proxy Nginx letsencrypt tutorial](https://www.youtube.com/watch?v=DyXl4c2XN-o)
* [Reverse proxy with NGINX and letsencrypt tutorial](https://www.the-digital-life.com/nginx-reverse-proxy/)
* [Docker and Running your self-hosted applications in a more secure way behind a reverse proxy.](https://www.youtube.com/watch?v=8T68pB_Fkm4)







# Nginx Access Lists
* [Nginx Proxy Manager - ACCESS LIST protection for internal services](https://www.youtube.com/watch?v=G9voYZejH48)






### Step X: Securing NGinX Proxy Manager
* [Securing NGinX Proxy Manager - follow up - securing your admin console for this Open Source Software](https://www.youtube.com/watch?v=UfCkwlPIozw)
* [How To Harden OpenSSH Client on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-harden-openssh-client-on-ubuntu-20-04)


#### Step X: Securing Your Containerized Applications with NGINX

# Securing Your Connections
* [What is DNS over TLS? Everything you need to know](https://www.thesslstore.com/blog/what-is-dns-over-tls/)
* [What is HTTP Strict Transport Security (HSTS)?](https://www.thesslstore.com/blog/what-is-hypertext-strict-transport-security-hsts/)
* [DNSSEC](https://support.dnsimple.com/articles/dnssec/)



----



----






# CloudFlare Tunnels
Using CloudFlare Tunnels allows us to create an encrypted connection between your server(s) and CloudFlare without the need to forward any ports.

* [Cloudflare: How to Set up Cloudflare Argo Tunnel FREE on Unraid - Bypass CGNAT](https://www.youtube.com/watch?v=RQ-6dActAr8)
* [Access Your Self Hosted Services WITHOUT Port Forwarding](https://www.youtube.com/watch?v=VrV0udRUi8A)
* [Cloudflare Tunnel: Creating Tunnels via GUI - Bypass CG-NAT](https://www.youtube.com/watch?v=RUJy9fjoiy4)

# Common Error: 502 Bad Gateway openresty
This error happens when the reverse proxy can’t connect to the destination host, or doesn’t get a response. Most likely, in docker setups, the containers are not on the same network, or the destination is not correct. Make sure you’re accessing the correct IP/hostname and the NGINX proxy manager can reach this target.

* [What is a 502 Bad Gateway Error (And How Can I Fix It)?](https://www.howtogeek.com/356389/what-is-a-502-bad-gateway-error-and-how-can-i-fix-it/#autotoc_anchor_7)
* [NGINX Proxy Manager – How-To Installation and Configuration](https://www.the-digital-life.com/nginx-proxy-manager/)
* [How To Fix A 502 Bad Gateway Cloudflare Error (Fast)](https://webpop.io/cloudflare/502-bad-gateway-error/#How-to-Fix-a-502-Bad-Gateway-Cloudflare-Error)

# Setting Up Your DNS on Cloudflare
* [Cloudflare: A Complete Guide, Features & Walkthrough (2021)](https://www.youtube.com/watch?v=BlhbsHrmcDc&t=739s)
* [How to Transfer a Domain from GoDaddy to Cloudflare (Use Cloudflare as Your Domain Registrar!)](https://www.youtube.com/watch?v=81LtL2ZvD38)
* [How to set up DNS records for your domain in Cloudflare account](https://www.namecheap.com/support/knowledgebase/article.aspx/9607/2210/how-to-set-up-dns-records-for-your-domain-in-cloudflare-account/)

# Installing NGINX Proxy Manager While Using CloudFlare DNS
* [Secure Your Domain with NGINX Proxy Manager and CloudFlare (Including Uptime Kuma Demonstration)](https://www.youtube.com/watch?v=rj7DZdWMK2k)

# Setting Up Let's Encript SSL Certs on Nginx Proxy Manager
* [Self Hosting on your Home Server - Cloudflare + Nginx Proxy Manager - Easy SSL Setup](https://www.youtube.com/watch?v=GarMdDTAZJo)
* [NGINX Proxy Manager – How-To Installation and Configuration](https://www.the-digital-life.com/nginx-proxy-manager/)
* [Nginx Proxy Manager - SSL Wildcard Certs for your entire domain](https://www.youtube.com/watch?v=TBGOJA27m_0)
* [Put Wildcard Certificates and SSL on EVERYTHING](https://www.youtube.com/watch?v=liV3c9m_OX8)




----



----




----



## DNS
To change your home routers DNS, go to `https://192.168.1.1/#/network/connections/1`
and select "Settings" at the bottom of the page.

* [Anatomy of a Linux DNS Lookup – Part I](https://zwischenzugs.com/2018/06/08/anatomy-of-a-linux-dns-lookup-part-i/)
* [Anatomy of a Linux DNS Lookup – Part II](https://zwischenzugs.com/2018/06/18/anatomy-of-a-linux-dns-lookup-part-ii/)
* [Anatomy of a Linux DNS Lookup – Part III](https://zwischenzugs.com/2018/07/06/anatomy-of-a-linux-dns-lookup-part-iii/)
* [Anatomy of a Linux DNS Lookup – Part IV](https://zwischenzugs.com/2018/08/06/anatomy-of-a-linux-dns-lookup-part-iv/)
* [Anatomy of a Linux DNS Lookup – Part V – Two Debug Nightmares](https://zwischenzugs.com/2018/09/13/anatomy-of-a-linux-dns-lookup-part-v-two-debug-nightmares/)

### dig
To get DNS speed and IP adderss, use:
* `dig @princess.ns.cloudflare.com google.com`
* `dig @darwin.ns.cloudflare.com hub.tutsplus.com`

### nslookup
`nslookup` examples

```bash
# find the domain name from its ip addess
$ nslookup 162.159.38.17
17.38.159.162.in-addr.arpa	name = princess.ns.cloudflare.com.

# find the ip address from the domain name
$ nslookup princess.ns.cloudflare.com
Server:		127.0.0.53
Address:	127.0.0.53#53

Non-authoritative answer:
Name:	princess.ns.cloudflare.com
Address: 162.159.38.17
Name:	princess.ns.cloudflare.com
Address: 108.162.194.17
Name:	princess.ns.cloudflare.com
Address: 172.64.34.17
Name:	princess.ns.cloudflare.com
Address: 2a06:98c1:50::ac40:2211
Name:	princess.ns.cloudflare.com
Address: 2803:f800:50::6ca2:c211
Name:	princess.ns.cloudflare.com
Address: 2606:4700:50::a29f:2611
```

Typically, most of the responses to `nslookup` queries are going to be [non-authoritative][77].
Meaning the response is from a cached copy from a third-party
and not from the primary DNS server holding the master copy.
For troubleshooting purposes, it's important to realize that a cached copy may not
contain the most up-to-date information.
To get an authoritative answer,
you will need to specify the authoritative name server as part of your request.
To do this, include the `-type=soa` switch (SOA = Start of Authority)
and `nslookup` will respond back with the name of the authoritative name server.

```bash
# get soa record so you can get an authoritative response
$ nslookup -type=soa jeffskinnerbox.me
Server:		127.0.0.53
Address:	127.0.0.53#53

Non-authoritative answer:
jeffskinnerbox.me
	origin = darwin.ns.cloudflare.com
	mail addr = dns.cloudflare.com
	serial = 2264853868
	refresh = 10000
	retry = 2400
	expire = 604800
	minimum = 3600

Authoritative answers can be found from:

# now query the authority (aka 'origin')
$ nslookup jeffskinnerbox.me darwin.ns.cloudflare.com
Server:		darwin.ns.cloudflare.com
Address:	173.245.59.151#53

Name:	jeffskinnerbox.me
Address: 104.21.61.243
Name:	jeffskinnerbox.me
Address: 172.67.217.38
Name:	jeffskinnerbox.me
Address: 2606:4700:3030::ac43:d926
Name:	jeffskinnerbox.me
Address: 2606:4700:3030::6815:3df3
```

You'll notice that the IP address of `jeffskinnerbox.me` **is not**
what you'll find in the A RECORD of `darwin.ns.cloudflare.com`.
To get the "real" A RECORD, you turn-off the [Cloudflare Proxied service][78].

```bash
# now query the authority but with cloudflare proxied turned-off
$ nslookup jeffskinnerbox.me darwin.ns.cloudflare.com
Server:		darwin.ns.cloudflare.com
Address:	172.64.33.151#53

Name:	jeffskinnerbox.me
Address: 108.44.239.214
```

Sources:
* [Find IP Address of a Domain, Server or Website](https://www.site24x7.com/find-ip-address-of-web-site.html)
* [Find DNS records for a domain name](https://www.nslookup.io/)
* [How to use Nslookup to check DNS Records](https://activedirectorypro.com/use-nslookup-check-dns-records/#tips)
* [How to use Nslookup to check DNS Records](https://activedirectorypro.com/use-nslookup-check-dns-records/)
* [How to Use Nslookup Command with Examples](https://www.meridianoutpost.com/resources/articles/command-line/nslookup.php)
* [How to Find DNS (Domain Name Server) Records on Linux Using the nslookup Command](https://www.2daygeek.com/nslookup-command-check-find-dns-records-lookup-linux/)

### Flush DNS Cashe
It’s important to sometimes [flush the DNS server cache][86].
When you type a domain name into a browser,
a DNS servers perform this a name to IP address conversion, and vice versa.
To speed up this conversion, operating systems create their own cache for
website addresses that have been called and resolved.
This means if the user returns to a recently visited website,
instead of looking up the information all over again, the browser can get the details
from the cache and return results more quickly.
The operating system isn’t the only place storing information.
Each step of the lookup process contains its own DNS cache.

You may choose to clear the DNS cache because you’ve noticed a problem,
such as a page redirecting to the wrong site.
To flush DNS cache on most Linux systems, you must first understand the DNS resolver being used,
eather `systemd-resolved` or `dnsmasq` or `bind`.
In order to know if you are dealing with one or another, you can execute the following command:
`sudo lsof -i :53 -S`.
(NOTE: As DNS runs on port 53,
we are looking for the commands associated with the service running on port 53
which is your local DNS resolver)
In my case, I'm using `systemd-resolved`.

The DNS cache is a temporary database on an operating system that stores DNS lookups.
There are times when a DNS cache can become corrupted or stale,
like when you have made changes to your DNS records.
When this happens, flush the DNS cache on your operating system.

So if your sites aren't loading properly, or some other wonky thing,
give the [DNS resolver][79] a flush and see if clear up the issue.

You can also check what DNS server you are using on Linux,
simply open up the terminal and do `nslookup` for any website.

```bash
# find your DNS resolver
$ sudo lsof -i :53 -S
COMMAND    PID            USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
systemd-r 2264 systemd-resolve   12u  IPv4  45207      0t0  UDP localhost:domain
systemd-r 2264 systemd-resolve   13u  IPv4  45208      0t0  TCP localhost:domain (LISTEN)

# DNS resolver config and status (in order to check upstream DNS servers in use)
systemd-resolve --status

# DNS server used by your computer
$ systemd-resolve --status | grep -1 'DNS Server'
    DNSSEC supported: no
  Current DNS Server: 192.168.1.1
         DNS Servers: 192.168.1.1
          DNS Domain: fios-router.home

# note the address for dns data is 127.0.0.53
$ nslookup jeffskinnerbox.me
Server:		127.0.0.53
Address:	127.0.0.53#53

Non-authoritative answer:
Name:	jeffskinnerbox.me
Address: 172.67.217.38
Name:	jeffskinnerbox.me
Address: 104.21.61.243
Name:	jeffskinnerbox.me
Address: 2606:4700:3030::6815:3df3
Name:	jeffskinnerbox.me
Address: 2606:4700:3030::ac43:d926

# is the dns resolver running
sudo systemctl is-active systemd-resolved

# how big is the dns cashe
sudo systemd-resolve --statistics

# flush the dns cashe
sudo systemd-resolve --flush-caches
```

Note the referance to "Server" and "Address".
On Linux `127.0.0.53` where the `systemd-resolved process` [listens for DNS queries][80] over [port 53][81].

Generally, you can quickly solve connection issues or seeing incorrectly displayed web pages
by using the above flush DNS command.
If doing so doesn’t resolve the problem, try to clear your web browser cache instead.
Google Chrome stores a separate DNS cache from the operating system on your computer.
Keep in mind that this cache type is different from the system level cache.
Here are the steps to do it:

Open Google Chrome and enter the following address into its address bar:
`chrome://net-internals/#dns`.
On the net internal settings page, select `Clear host cache`.

To purge Cloudflare's cache, go to `https://dash.cloudflare.com/2dbf9ab9f674a117b229f8c02d0cd234/jeffskinnerbox.me/caching/configuration`.

```bash
# flush the chrome browser cache
chrome://net-internals/#dns

# flush the dns cashe
sudo systemd-resolve --flush-caches

# flush cloudflare's cache
see ... https://dash.cloudflare.com/2dbf9ab9f674a117b229f8c02d0cd234/jeffskinnerbox.me/caching/configuration

# flush the cache within nginx proxy manager
# or
rm -rf ./nginx/cache/*     # assumes the cache is accessable as a volume

# hit the reload button on your browser
```

* [How to purge the Nginx cache](https://bluegrid.io/edu/how-to-purge-the-nginx-cache/)
* [How to purge Nginx Proxy Cache in Linux CentOS](https://www.ryadel.com/en/nginx-purge-proxy-cache-delete-invalidate-linux-centos-7/)
You can disable the caching via the Nginx Proxy Manager UI, but it appears to be broken - https://github.com/jc21/nginx-proxy-manager/issues/389

Source:
* [How to Find Out What DNS Server Am I Using?](https://techwiser.com/check-your-dns-server/)
* [How to Flush DNS Cache](https://www.hostinger.com/tutorials/how-to-flush-dns)
* [How to flush the DNS cache on Linux](https://www.techrepublic.com/article/how-to-flush-the-dns-cache-on-linux/)
* [Flush DNS: What It Is, How to Do It & Why You Should](https://blog.hubspot.com/website/flush-dns)
* [How to Flush DNS Cache in Linux](https://beebom.com/how-flush-dns-cache-linux/)

# SSL
* [How to Fix the NET::ERR_CERT_AUTHORITY_INVALID Error](https://kinsta.com/knowledgebase/neterr-cert-authority-invalid/)



Sources:
* [Service and Version Detection](https://nmap.org/book/man-version-detection.html)
* [Nmap — A Guide To The Greatest Scanning Tool Of All Time](https://www.manishmshiva.com/nmap-a-guide-to-the-greatest-scanning-tool-of-all-time/)
* [Nmap](https://wiki.onap.org/display/DW/Nmap)

#### Step X: Check if Port 80 & 443 are Blocked
In the web world, port 80 is the default port for HTTP / HTTPS protocols.
At the same time, it is very common for Internet Service Providers (ISP) to block
all inbound data to this port (not outbound data).
ISPs do this so that you can't run a website from you home network.
Just using a port other than 80 could work,
but now the users of your website must append the URL with a port number,
making the use of you website non-standard and confusing for a novice user.

You could work around your IPSs efforts to stop you by redirecting traffic
to a different inbound port using what is generally called [Port 80 Redirect][82] service,
made popular by [No-IP.com][83].
In effect, the user of your website uses the standard URL but within the DNS infrastructure
the port distination is changed from port 80 to what ever port you have openned
to replace the blocked port 80 on your home router.

Cloudflare has it own version of this Port 80 Redirect idea but they call it

* [Port 80 Redirect - What is...](https://www.youtube.com/watch?v=pgrizFmTgvE)
* [Cloudflare Page Rules - Redirect Domain Tutorial](https://www.youtube.com/watch?v=5NGJkHAHyjE)

#### Step X: Unblock and Forward Ports on Home Router
By default, Bitwarden will be served through ports 80 (http) and 443 (https) on the host machine.
Open these ports and modify your firewall
so that Bitwarden can be accessed from within and/or outside of the network.
As an option, you can choose different ports during installation.

When I first ventured into this,
there appeared to be one major issue ... Verizon FIOS, my Internet Service Provider (ISP),
blocks incoming traffic on ports 80 and 433.
Verizon, like most all ISPs, doesn’t like its customers running home web servers,
at least without buying a [static IP address][89].
Blocking ports 80 & 433 appear to be one why to discourage home web servers.

I concluded this because when initially doing my home router port forwarding setup,
I had multiple challenges and confusing responses from my setup.
I then read several web postings ([here][74], [here][75], and [here][76])
and concluded Verizon is blocking my ports.
But many web post also said that Verizon absolutely doesn't block ports 80 & 433.
So out of desperation, I web searched and experiment further (much longer than I'm willing to admit),
ultimately concluded that the real problem is the port forwarding user interface
on my Verizon provide router was a confusing mess.
The video "[How to setup the port forwarding on Verizon FIOS Router G3100][88]"
and the website "[Create Domain Records to Point to your Home Server on Cloudflare Using Nginx Progy Manager][100]"
were my salvation and allowed me to set thing up properly.

The portforwarding settings are:

1. **Select IP from menu** = enter IP address of Vagrant host
2. **Application to Forward...** = **HTTP (Web Server)**
3. press **Add +**

Repeat but use **HTTPS (Secured Web Server)** in step 2.

* [5 Best Open Port Checkers and Scanners](https://www.dnsstuff.com/open-port-checkers-scanners)
* [Network Port Checker & Scanner Tool](https://www.ipfingerprints.com/portscan.php)
* [Port Forwarding Tester](https://www.yougetsignal.com/tools/open-ports/)
* [Shield Up](https://www.grc.com/faq-shieldsup.htm)
* [PortCheckTool.com](https://www.portchecktool.com/)

```bash
# health check of web page using curl
# -s --silent        do not show progress meter or error messages
# -S --show-error    when used with -s it makes curl show an error message if it fails.
curl -sS 192.168.1.200

curl -sS http://example.org
```

Port Check
Open a terminal on your host machine and type the following command:

```bash
telnet localhost 8080
```

Unless the port 8080 is already in use by something else
you should get something like "Connection refused".

>**Vagrant's Handling of Port Collisions:**
>When using Vagrant port-forwarding, it can happen that a Vagrant box uses a port that is not available.
>It will tell you about it anyway, but if the host machine's port doesn't really matter to you,
>amend the corresponding line in the Vagrantfile this way:
>`config.vm.network :forwarded_port, guest: 8080, host: 80, auto_correct: true`
>The `auto_correct` parameter will allow Vagrant to automatically assign another port
>of the host machine in case of unavailability (and tell you about it, of course).

#### Step X: XXX
From in side my LAN,
I used `google-chrome http://192.168.33.10:8080` and it gives me the Bitwarden login page.
So Bitwarden is reachable on my LAN from behind the Nginx Proxy Manager, as you would expect.
`google-chrome http://192.168.33.10:433` gets a "400 Bad Request" page, as it should since TLS isn't operational in Bitwarden.

From in side my LAN,
I used `google-chrome http://192.168.33.10:80` and it gives me the Nginx "Congratulations!" page.
So Bitwarden is **NOT** reachable on my LAN from the front of Nginx Proxy Manager,
and says "you're trying to access a host that isn't set up yet" .... not expected!

[CanYouSeeMe.org](https://canyouseeme.org/)
is a port checking tool.
It  it can remotely verify if a port is open or closed.
It can be used to verify port forwarding
and check to see if a server is running or a firewall or ISP is blocking certain ports.

#### Step X:
#### Step X:


## Setup Domain Name and DNS

Ultimately, I had to abandoned using Namecheap as my DNS because it didn't really support Let's Encrypt,
at least in the automated way that Nginx Proxy Manager expects it to.
With some effort, [you can get Let's Encript certificates to work on Namecheap](https://www.youtube.com/watch?v=bVbGW037fYk)
but I wanted the automation the proxy manager promised.
Also, there is very much more information on the web about Cloudflare than for Namecheap.

[Cloudflare][05] is best know as a Content Delivery Network but the also offer DNS and sercurity servcies
(check "[What is Cloudflare][99]" for more on this).
Cloudflare claims to be the world’s fastest
([certainly amount the best](https://www.keycdn.com/blog/best-free-dns-hosting-providers#dns-hosting-providers-comparison))
and most reliable public DNS resolver
with advanced security with built-in DDoS mitigation and DNSSEC.

Cloudflare DOES works with yubikey & WebAuthn -  https://blog.cloudflare.com/cloudflare-now-supports-security-keys-with-web-authentication-webauthn/ and  https://blog.centminmod.com/2021/06/30/2401/how-to-setup-yubikey-5-nfc-security-key-for-cloudflare-account-logins/


#### Step X: Setup Domain Name Account on Namecheap
I have [purchased my domain name at Namecheap][72].
Most people know of [Namecheap][52] as a domain registration and management service,
but they also offer web hosting services.
In addition to domains and full web hosting packages,
Namecheap sells SSL certificates, privacy protection services, and more.
In addition to a solid [knowledge base][70], Namecheap offers 24/7 chat support.
For information, here is a [review of Namecheap][69].
To register a domain on Namecheap,
just follow the registration process document [here][73].

#### Step X: Adding Your Domain to Cloudflare
Go to [Cloudflare](https://dash.cloudflare.com/sign-up)
and create an account.
When you start your account,
you'll be given an opportunity to register any domain you wish.
Cloudflare will pull in your current DNS records for you existing DNS provider.

Next, make sure to delete you domain records from its current registration site (Namecheap).
Modify the name service records to include Cloudflare's nameservers it provide you
(In my case `darwin.ns.cloudflare.com` and `princess.ns.cloudflare.com`).

For the free service, it could take as long as 24 hours for the registration process to complete.

When you add a new DNS record, it’s automatically set to “Proxied” but can be changed to “DNS Only”.
The DNS proxied means it will be shown a Cloudflare IP, not your IP address, if you look it up. Thus all attacks at that domain will DDoS Cloudflare and not you host directly. Non proxied means all traffic goes directly to your own IP without Cloudflare being a safety net in front.


-----



----








----



# Establish Your SSL Certificates
To enable [HTTPS on your website][61],
you need to get a [Secure Sockets Layer (SSL) certificate][62] from a [Certificate Authority (CA)][63].
In order to get a certificate for your website’s domain from aCA
you have to demonstrate control over the domain.
This is typical done using the [ACME protocol][66] which typically runs on your web host.

[Let’s Encrypt][65] is a free and open CA that provides [Domain Validated (DV) certificates][67] at no charge.
[Certbot][68] is a free, open source software tool for automatically using
Let’s Encrypt certificates on manually-administrated websites to enable HTTPS.

* [certbot instructions](https://certbot.eff.org/instructions)



* [Nginx Proxy Manager - How-To Installation and Configuration](https://www.youtube.com/watch?v=P3imFC7GSr0)
* [Nginx Proxy Manager - SSL Wildcard Certs for your entire domain](https://www.youtube.com/watch?v=TBGOJA27m_0)
* [Securing Your Containerized Applications with NGINX](https://www.youtube.com/watch?v=spVQex_qj_s)
* [Securing NGinX Proxy Manager - follow up - securing your admin console for this Open Source Software](https://www.youtube.com/watch?v=UfCkwlPIozw&t=434s)
* [Nginx Proxy Manager - SSL Wildcard Certs for your entire domain](https://www.youtube.com/watch?v=TBGOJA27m_0)
* [Put Wildcard Certificates and SSL on EVERYTHING](https://www.youtube.com/watch?v=liV3c9m_OX8)
* [Nginx Proxy Manager - ACCESS LIST protection for internal services](https://www.youtube.com/watch?v=G9voYZejH48)



----




----


## Docker and Firewalls
* [Docker and Firewalls - Docker wants to punch holes in the local firewall, let's mitigate that issue](https://www.youtube.com/watch?v=bpWytcz4uMw)
* [Docker and iptables](https://docs.docker.com/network/iptables/)

# Monitor Docker Containers using Netdata
* [How to monitor Docker containers using Netdata health and performance](https://www.youtube.com/watch?v=tMRHc9r2Jw4)






[01]:https://nginxproxymanager.com/
[02]:http://www.haproxy.org/
[03]:https://traefik.io/
[04]:https://developers.google.com/search/docs/advanced/security/https
[05]:https://www.cloudflare.com/hpg/






[50]:https://github.com/dani-garcia/vaultwarden/wiki/Enabling-WebSocket-notifications
[51]:https://github.com/dani-garcia/vaultwarden/wiki/Enabling-admin-page
[52]:https://www.namecheap.com/
[53]:https://www.namecheap.com/support/knowledgebase/article.aspx/595/11/how-do-i-enable-dynamic-dns-for-a-domain/
[54]:https://www.youtube.com/watch?v=spVQex_qj_s
[55]:https://en.wikipedia.org/wiki/DMZ_(computing)
[56]:https://en.wikipedia.org/wiki/Reverse_proxy
[58]:https://www.duckdns.org/
[59]:https://wiki.debian.org/DDNS
[60]:https://hackaday.com/2020/08/25/linux-fu-your-own-dynamic-dns/
[61]:https://www.bluehost.com/resources/how-to-add-https-to-your-domain-and-install-an-ssl-certificate-to-protect-your-customers
[62]:https://www.digicert.com/what-is-an-ssl-certificate
[63]:https://www.ssl.com/faqs/what-is-a-certificate-authority/[64]:
[65]:https://letsencrypt.org/
[66]:https://www.keyfactor.com/blog/what-is-acme-protocol-and-how-does-it-work/
[67]:https://aboutssl.org/what-is-domain-validated-ssl-certificate/
[68]:https://certbot.eff.org/
[69]:https://digital.com/best-web-hosting/namecheap/
[70]:https://www.namecheap.com/support/knowledgebase/
[71]:https://support.dnsimple.com/articles/differences-a-cname-records/
[72]:https://www.youtube.com/watch?v=MoePjwotTUE
[73]:https://www.namecheap.com/support/knowledgebase/subcategory/35/registrations/
[74]:https://www.groovypost.com/howto/news/verizon-fios-blocks-inbound-port-80/
[75]:https://itstillworks.com/12579803/how-to-block-xbox-live-on-a-netgear-router
[76]:https://forums.verizon.com/t5/Fios-Internet/Internet-ports-80-and-443/td-p/499329
[77]:https://tecadmin.net/authoritative-non-authoritative-dns-server/
[78]:https://community.cloudflare.com/t/what-is-the-difference-between-proxied-and-dns-only/173310
[79]:https://www.computerhope.com/jargon/d/dns-resolver.htm
[80]:https://unix.stackexchange.com/questions/612416/why-does-etc-resolv-conf-point-at-127-0-0-53
[81]:https://www.howtouselinux.com/post/dns-port
[82]:https://www.noip.com/support/knowledgebase/port-80-redirect/
[83]:https://www.noip.com/
[84]:https://en.wikipedia.org/wiki/Cloudflare
[85]:https://portforward.com/how-to-port-forward/
[86]:https://www.dnsstuff.com/clear-flush-dns-server-cache-windows
[87]:https://wiki.onap.org/display/DW/Nmap
[88]:https://www.youtube.com/watch?v=eL-PBGDsARY
[89]:https://www.avast.com/c-static-vs-dynamic-ip-addresses
[90]:https://en.wikipedia.org/wiki/Firewall_(computing)
[91]:http://www.netfilter.org/
[92]:https://help.ubuntu.com/community/UFW
[93]:https://help.ubuntu.com/community/Gufw
[94]:https://www.linux.com/learn/tutorials/863701-an-introduction-to-uncomplicated-firewall-ufw
[95]:https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server
[96]:https://docs.docker.com/network/bridge/#use-the-default-bridge-network
[97]:https://docs.docker.com/network/bridge/
[98]:https://thehomelab.wiki/books/dns-reverse-proxy/page/create-domain-records-to-point-to-your-home-server-on-cloudflare-using-nginx-progy-manager
[99]:https://www.youtube.com/watch?v=NV2eKYmQF6Q
[100]:https://thehomelab.wiki/books/dns-reverse-proxy/page/create-domain-records-to-point-to-your-home-server-on-cloudflare-using-nginx-progy-manager
[101]:
[102]:
[103]:
[104]:
[105]:
[106]:
[107]:
[108]:
[109]:
[110]:
