<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----


Zero Trust Architecture is the practice of designing systems based on the principle of never trust, always verify, as opposed to the traditional trust, but verify principle . It has become quite a popular buzz word of late, in light of all the recent successful cyber attacks, compromising vast amounts of user data.
* [A Roadmap to Zero Trust Architecture](https://assets.ctfassets.net/slt3lc6tev37/9jyDLdW3VXPGwChDCCnrx/18edf82b3d4a36595e51c16ed5c62816/Zero-Trust-Roadmap-WP.pdf)
* [Zero Trust Hosting and Reverse Proxy via Cloudflare, SWAG and Authelia](https://www.linuxserver.io/blog/zero-trust-hosting-and-reverse-proxy-via-cloudflare-swag-and-authelia)
* [Say Goodbye to Reverse Proxy and Hello to Cloudflare Tunnels](https://noted.lol/say-goodbye-to-reverse-proxy-and-hello-to-cloudflare-tunnels/)
* [You should NOT use Cloudflare Tunnel (if you do this...)](https://www.youtube.com/watch?v=oqy3krzmSMA)


Cloudflare is most well-known as a [Content Delivery Network (CDN)][02],
but it has grown past that, and offers a range of services,
mostly covering networking and security.
For a good review of what Cloudflare is all about,
check out the post "[Everything You Need to Know About Cloudflare (and Some You Don’t)][01]".

For my purposes,
it is my Domain Name Server (DNS),
supports my ISPs non-static IP address via Dynamic DNS (DDNS),
and provides me a range of cloud-based security and management features.
Cloudflare can stops malicious traffic before it reaches my home server.
Cloudflare also proxies traffic destine for my home server,
thereby hiding my origin IP address,
so attackers cannot bypass Cloudflare and directly attack my server.
A Cloudflare service (called [Cloudflare Tunnels][03])
can also provide a secure tunnel from its proxy to my home LAN router,
eliminating the need for me to punch holes in router firewall (typically ports 80 and 433).

(check this out via `nslookup` with and without the Cloudflare proxie turned on).
A DNS lookup of an unproxied (grey-clouded) Cloudflare subdomain returns the IP address that you have entered for the record. Unproxied traffic goes directly to your origin server and does not receive any of the benefits of using Cloudflare.

# Cloudflare Tunnels
Cloudflare Tunnel exposes applications running on your local network without
requiring you to forward your applications port to your firewall and exposing it to the Internet.
With Cloudflare Tunnel, a lightweight daemon in your infrastructure (called `cloudflared`)
creates outbound-only secure tunnel connections to Cloudflare’s edge.
Cloudflare Tunnel can connect HTTP web servers, SSH servers, remote desktops, and other protocols safely to Cloudflare.
This way, your applications can serve traffic through Cloudflare
without being vulnerable to attacks that bypass Cloudflare by going directly to you external IP address.

Cloudflare Tunnels provides you a shield to mitigate things like Distributed denial-of-service (DDoS).
It also can provide SSL/TSL services for all your applications
and supports subdomains for you applications.
This eliminating the need for functions like HAProxy, Nginx Reverse Proxy, or Traefik
within you network infrastruture.
All these functions (and potentially more via Zero Trust policies) are giving to Cloudflare Tunnels.

Why do this, see "[How I survived a DDoS attack][11]".



* [EXPOSE your home network to the INTERNET!! (it's safe)](https://www.youtube.com/watch?v=ey4u7OUAF3c)

* [Cloudflare Access](https://dash.teams.cloudflare.com/2dbf9ab9f674a117b229f8c02d0cd234/onboarding)
* [Cloudflare Tunnel Setup Guide - Self-Hosting for EVERYONE](https://www.youtube.com/watch?v=hrwoKO7LMzk)
* [Free Cloudflare Tunnel To Home Assistant: Full Tutorial!](https://www.youtube.com/watch?v=4svVZGRMrsM)
* [Secure Remote Access to Home Assistant with Cloudflare Proxy](https://www.youtube.com/watch?v=AfiT6KSGXHM)
* [CLOUDFLARE tunnel on SYNOLOGY](https://www.youtube.com/watch?v=5IrtNxfzH1o)
* [How to Securely Access Your Wi-Fi Router From Anywhere](https://www.makeuseof.com/how-to-securely-remote-access-wifi-router/)
* [Access Your Self Hosted Services WITHOUT Port Forwarding](https://www.youtube.com/watch?v=VrV0udRUi8A)
* [Restrict Access to Your CloudFlare Tunnel Applications](https://www.youtube.com/watch?v=65FdHRs0axE)
* [Home Assistant Remote Access with Cloudflare Argo Tunnel](https://www.mostlychris.com/home-assistant-remote-access-with-cloudflare-argo-tunnel/)
    * [Using the Cloudflared Add-On](https://www.mostlychris.com/using-the-cloudflared-add-on/?ref=mostlychris-newsletter)

## XXX
Cloudflare Tunnel exposes applications running on your local web server on any network with an internet connection without manually adding DNS records or configuring a firewall or router.

Cloudflare Tunnel provides you with a secure way to connect your resources to Cloudflare without a publicly routable IP address. With Tunnel, you do not send traffic to an external IP — instead, a lightweight daemon in your infrastructure (cloudflared) creates outbound-only connections to Cloudflare’s edge.

[Using Cloudflare Tunnels For Hosting & Certificates Without Exposing Ports On Your Firewall](https://www.youtube.com/watch?v=eojWaJQvqiw&t=5s)
[Remote Access: Getting Started with CloudFlare Tunnels (Domains, DNS, Tunnels)](https://www.youtube.com/watch?v=Q5dG8g4-Sx0)



-----


# Domain Name Services (DNS)
Domain Name System (DNS), is a lookup service that translates a hostname
like `google.com` for example, to an IP address.
This is usually set to your modem or router’s IP address by default (same as the gateway address),
which will in turn use the DNS servers provided by your ISP (Internet Service Provider).

dnsmasq is a lightweight, easy to configure DNS forwarder, designed to provide DNS (and optionally DHCP and TFTP) services to a small-scale network. It can serve the names of local machines which are not in the global DNS.

The DNS Forwarder allows pfSense to resolve DNS requests using hostnames obtained by the DHCP service, static DHCP mappings, or manually entered information. The DNS Forwarder can also forward all DNS requests for a particular domain to a server specified manually.

The DNS Resolver in pfSense® software utilizes unbound, which is a validating, recursive, caching DNS resolver that supports DNSSEC, DNS over TLS, and a wide variety of options. It can act in either a DNS resolver or forwarder role.

* [How I configure a DHCP server on my personal network](https://opensource.com/article/22/7/configure-dhcp-server)
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




# DDNS
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

#### Step X: Cloudflare Dynamic DNS (DDNS)
* [DDNS on a Raspberry Pi using the Cloudflare API (Dynamic DNS)](https://www.youtube.com/watch?v=rI-XxnyWFnM)
* [CloudFlare DDNS - Update CloudFlare with Your Dynamic IP Address](https://www.youtube.com/watch?v=Nf7m3h11y-s)




# Setting Up Your DNS on Cloudflare
* [Cloudflare: A Complete Guide, Features & Walkthrough (2021)](https://www.youtube.com/watch?v=BlhbsHrmcDc&t=739s)
* [How to Transfer a Domain from GoDaddy to Cloudflare (Use Cloudflare as Your Domain Registrar!)](https://www.youtube.com/watch?v=81LtL2ZvD38)
* [How To Transfer Domain From Namecheap To CloudFlare Instantly](https://www.youtube.com/watch?v=2HhNFSsxFfM&t=300s)
* [How to set up DNS records for your domain in Cloudflare account](https://www.namecheap.com/support/knowledgebase/article.aspx/9607/2210/how-to-set-up-dns-records-for-your-domain-in-cloudflare-account/)

# Installing NGINX Proxy Manager While Using CloudFlare DNS
* [Secure Your Domain with NGINX Proxy Manager and CloudFlare (Including Uptime Kuma Demonstration)](https://www.youtube.com/watch?v=rj7DZdWMK2k)


# Securing Your Connections
* [What is DNS over TLS? Everything you need to know](https://www.thesslstore.com/blog/what-is-dns-over-tls/)
* [What is HTTP Strict Transport Security (HSTS)?](https://www.thesslstore.com/blog/what-is-hypertext-strict-transport-security-hsts/)
* [DNSSEC](https://support.dnsimple.com/articles/dnssec/)



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
You can disable the caching via the Nginx Proxy Manager UI, but it appears to be broken - https://gitub.com/jc21/nginx-proxy-manager/issues/389

Source:
* [How to Find Out What DNS Server Am I Using?](https://techwiser.com/check-your-dns-server/)
* [How to Flush DNS Cache](https://www.hostinger.com/tutorials/how-to-flush-dns)
* [How to flush the DNS cache on Linux](https://www.techrepublic.com/article/how-to-flush-the-dns-cache-on-linux/)
* [Flush DNS: What It Is, How to Do It & Why You Should](https://blog.hubspot.com/website/flush-dns)
* [How to Flush DNS Cache in Linux](https://beebom.com/how-flush-dns-cache-linux/)



-------



## Setup Domain Name and DNS / DDNS
Ultimately, I had to abandoned using Namecheap as my DNS because it didn't really support Let's Encrypt,
at least in the automated way that Nginx Proxy Manager expects it to.
With some effort, [you can get Let's Encript certificates to work on Namecheap](https://www.youtube.com/watch?v=bVbGW037fYk)
but I wanted the automation the proxy manager promised.

Also, there is very much more information on the web about Cloudflare than for Namecheap.
[Cloudflare][22] is best know as a Content Delivery Network but the also offer DNS and sercurity servcies
(check "[What is Cloudflare][99]" for more on this).
Cloudflare claims to be the world’s fastest
([certainly among the best](https://www.keycdn.com/blog/best-free-dns-hosting-providers#dns-hosting-providers-comparison))
and most reliable public DNS resolver
with advanced security with built-in DDoS mitigation and DNSSEC.


#### Step 1: Setup Domain Name Account on Namecheap - DONE
I have [purchased my domain name at Namecheap][72].
Most people know of [Namecheap][52] as a domain registration and management service,
but they also offer web hosting services.
In addition to domains and full web hosting packages,
Namecheap sells SSL certificates, privacy protection services, and more.
In addition to a solid [knowledge base][70], Namecheap offers 24/7 chat support.
For information, here is a [review of Namecheap][69].
To register a domain on Namecheap,
just follow the registration process document [here][73].

#### Step 2: Adding Your Domain to Cloudflare - DONE
Go to [Cloudflare and create an account][21].
When you start your account,
you'll be given an opportunity to register any domain you wish.
Cloudflare will pull in your current DNS records for you existing DNS provider.

Next, make sure to delete you domain records from its current registration site (Namecheap).
Modify the name service records to include Cloudflare's nameservers it provide you
(In my case `darwin.ns.cloudflare.com` and `princess.ns.cloudflare.com`).
For the free service, it could take as long as 24 hours for the registration process to complete.

When you add a new DNS record, it’s automatically set to “Proxied” but can be changed to “DNS Only”.
The DNS proxied means it will be shown a Cloudflare IP,
not your IP address, if you look it up.
Thus all attacks at that domain will DDoS Cloudflare and not you host directly.
Non-proxied means all traffic goes directly to your own IP without Cloudflare being a safety net in front.

Sources:
* [How to set up DNS records for your domain in Cloudflare account](https://www.namecheap.com/support/knowledgebase/article.aspx/9607/2210/how-to-set-up-dns-records-for-your-domain-in-cloudflare-account/)
* [Creating a Cloudflare account and adding a website](https://support.cloudflare.com/hc/en-us/articles/201720164#h_8ea0d664-3af3-4623-ae2d-052f98b10090)
* [Adding your domain to Cloudflare](https://community.cloudflare.com/t/step-1-adding-your-domain-to-cloudflare/64309)
* [Managing DNS records in Cloudflare](https://support.cloudflare.com/hc/en-us/articles/360019093151)

#### Step X: Setup Dynamic DNS (DDNS)
If you have a static external IP address,
DDNS will provide little to no value for you.
However, if you have a dynamic IP address (like most residental IP services provider give you),
some how, you need to update the publicly accessible DNS' with your new IP address.
DDNS will allow you to ensure you’re always connecting to your external IP address,
even where it could changing on you.

There are [many ways to solve this changing IP address problem][60].
You could run a process to detect and report the change,
or many routers can report their IP address to a Dynamic DNS server.
[Dynamic DNS (DDNS)][59] is a service that can be used to automatically update DNS records
if client PCs get their IP address changed.

[What is the difference between dynamic DNS and DNS][10]?
Dynamic DNS is a feature of DNS.
Early DNS systems were static and the IP addresses and name mapping were entered manually.
Dynamic DNS updates the IP mappings automatically when it changes.

[Duck DNS][58] is a dynamic DNS service provider, and its one of many.
The down side of DuckDNS is that you don't get to pick the domain name,
and you don't get the wide range of features of the profesional DNS services.

These sources could be helpful in setting up your DDNS:

* [DDNS on a Raspberry Pi using the Cloudflare API (Dynamic DNS)](https://www.youtube.com/watch?v=rI-XxnyWFnM)
* [How to Setup Cloudflare Dynamic DNS](https://adamtheautomator.com/cloudflare-dynamic-dns/)
* [CloudFlare DDNS - Update CloudFlare with Your Dynamic IP Address](https://www.youtube.com/watch?v=Nf7m3h11y-s)

This can all be accomplished even easilier with pfSense,
which I'm using for my home router & firewall.
I used the steps below to set up DDNS on pfSense and using my DNS provider, Cloudflare.

* [How to Set Up DDNS on pfSense using Cloudflare](https://www.wundertech.net/how-to-set-up-ddns-on-pfsense-using-cloudflare)
* [How to Set Up DDNS on pfSense using Cloudflare | QUICK TUTORIAL](https://www.youtube.com/watch?v=8GYs61ThGBM)



-------




#### Step X: Configure Cloudflare DNS With Subdomains
It is not always necessary to register a new domain name if you already have one (as I do via Namecheap).
Using your existing domain name, you can establish subdomains.
Rather than registering a new domain name,
you create a subdomain using the domain you already own.
For example, create subdomains `blog.domain.tld` or `forum.domain.tld`
(assuming you already hold the domain `domain.tld`).
If you desire, you can also add multiple levels of subdomains,
for instance `info.blog.domain.tld`.

The [`A` and `CNAME`][71] records are the two common ways,
and the only ones needed here,
to map a host to one or more IP addresses.
The `A` record points a name to a specific IP.
The `CNAME` record points a name to another name instead of to an IP.

To check if you DNS entries have propagation accross the Internet,
check our [DNS Checker][12].

* [How to Setup Cloudflare DNS (2022 update)](https://www.youtube.com/watch?v=XQKkb84EjNQ)
* [How To Set Up Cloudflare | Ultimate Tutorial](https://www.youtube.com/watch?v=f1EoQygkJ0E)

#### Step X: eMail Routing
Some self hosted apps, like Bitwarden, require email settings.

* [Cloudflare Email Setup (Free Professional Custom Email Setup)](https://www.youtube.com/watch?v=nNGcvz1Sc_8)

* [How to Set Up Your Synology MailPlus Server](https://www.youtube.com/watch?v=tBLjJWn-WBk)

* [STOP Paying for Custom Email!](https://www.youtube.com/watch?v=AT9MiUDtk4E)
* [You can Still use Gmail SMTP to Send E-Mails in 2023 and Here's How](https://noted.lol/setup-gmail-smtp-sending-2023/)
* [What is Mail Exchange record (MX) | Set up MX record in Office 365 | How MX record works](https://www.youtube.com/watch?v=-4nEu7dPSJk)
* [How To Set Up Cloudflare | Ultimate Tutorial](https://www.youtube.com/watch?v=f1EoQygkJ0E&t=837s)
* [Getting started with Cloudflare DNS: Adding MX records to Cloudflare](https://www.youtube.com/watch?v=6qsxs03V3X8)
* [Cloudflare Email Routing](https://developers.cloudflare.com/email-routing/)

#### Step X: Cloudflare Restricted Access
Cloudflare can leverage a 3rd party identity providers for restricting access to your CloudFlare Tunnels.
We'll look at both GitHub and Google.

In a future video we make take a look at Authelia as well, but not in this video.

* [Remote Access: Getting Started with CloudFlare Tunnels (Domains, DNS, Tunnels)](https://www.youtube.com/watch?v=Q5dG8g4-Sx0)
* [Restrict Access to Your CloudFlare Tunnel Applications](https://www.youtube.com/watch?v=65FdHRs0axE)
* [CloudFlare Tunnels: Restrict Access with Google and Github](https://www.youtube.com/watch?v=wdmbAo02ktQ)



-----



# Deploy Website with Cloudflare Pages & GitHub
Cloudflare Pages is a JAMstack platform for frontend developers to collaborate and deploy websites.
You can deploy a dynamic front-end website that is fast and deployed directly from your Git provider.

>**NOTE:** JAMStack, is a web development architecture pattern and solution stack. The initialism "JAM" stands for JavaScript, API and Markup and was coined by Mathias Biilmann in 2015. The idea of combining using JavaScript, APIs, and markup together has existed since the beginnings of HTML5.

* [Cloudflare Pages](https://pages.cloudflare.com/)
* [Deploy your website for free with Cloudflare Pages and GitHub!](https://www.youtube.com/watch?v=MTc2CTYoszY)
* [Introduction to Cloudflare Workers and Cloudflare Pages](https://www.youtube.com/watch?v=8W3X2hNULq0)



-----



# Install Cloudflare Tunnels
Cloudflare Tunnel provides you with a secure way to connect your servers to Cloudflare
without a publicly routable IP address.
With Cloudflare Tunnels, you do not send traffic to an external IP — instead,
a lightweight daemon in your infrastructure (called `cloudflared`)
creates outbound-only connections to Cloudflare’s edge.

The sources below provide all that is needed to get basic service up and going.
That said, may additional features are available and worth exploring
(see the **Additional Cloudflare Features** section below).

Sources:

* [Access Your Self Hosted Services WITHOUT Port Forwarding](https://www.youtube.com/watch?v=VrV0udRUi8A)
* [Cloudflare Tunnels: Getting Started with Domains, DNS, and Tunnels](https://www.youtube.com/watch?v=Q5dG8g4-Sx0)
* [Restrict Access to Your Cloudflare Tunnel Applications](https://www.youtube.com/watch?v=65FdHRs0axE)

* [Cloudflare Tunnel: Expose Your Home Network to the Internet Securely](https://theitbros.com/cloudflare-tunnel/)
* [EXPOSE your home network to the INTERNET!! (it's safe)](https://www.youtube.com/watch?v=ey4u7OUAF3c)
* [Using Cloudflare Tunnels For Hosting & Certificates Without Exposing Ports On Your Firewall](https://www.youtube.com/watch?v=eojWaJQvqiw&t=5s)
* [Remote Access: Getting Started with CloudFlare Tunnels (Domains, DNS, Tunnels)](https://www.youtube.com/watch?v=Q5dG8g4-Sx0)
* [Using Portainer with Docker and Docker Compose](https://earthly.dev/blog/portainer-for-dcm/)
* [How to use Cloudflare Tunnel in your Homelab (even with Traefik)](https://www.youtube.com/watch?v=yMmxw-DZ5Ec)

#### Step 1: Create Cloudflare Tunnel - DONE
The first step is establish a tunnel on Cloudflare.
I'm going to create one tunnel from Cloudflare to `firewall-router`
on my domain `jeffskinnerbox.me`.
You can configure and create the tunnels via the following steps:

* Log into your Cloudflare account at `https://dash.cloudflare.com/login`.
* From your Cloudflare home page right hand menu,
select the **Websites** and select the domain name your interested in establishing some Cloudflare Tunnels.
* From the right-hand menu,
select **Traffic** > **Cloudflare Tunnel*
Next you select the **Launch Zero Trust Dashboard** button.
This will launch the Zero Trust Dashboard to view your Tunnels
and create Zero Trust policies for your applications and your users.

>**NOTE:** The very first time you create the tunnels,
>you'll be asked for a "team name".
>This creates a unique (but changeable later) domain for your Cloudflare Zero Trust account.
>I choose `jeffskinnerbox`.
>I choose the free plan and used PayPal so I didn't have to provide a credit card.
>This will being you to the "Cloudflare Zero Trust" webpage.

Th create your tunnel:

* On the left-hand menu, you'll select **Access** > **Tunnels**.
* Select **Create a tunnel** and I named it `router-tunnel`
* Next you choose the environment the `cloudflared` daemon will run in.
I choose **Docker** and it provide me the Docker Shell script to load the daemon.
* Copy the tunnel token since it will be needed when establishing the daemon on your target server
* (i.e. `firewall-router`).

#### Step 2: Create the Public Hostname - DONE
Next, we'll identify the subdomain (aka public hostname) and associate it with the appropriate URL.

* Under the **Public Hostname** tab,
select the **Add a public hostname** button.
* Entered the following information:
Subdomain is "blog", Domain is "jeffskinnerbox.me", Path is left blank,
Type is "HTTP", and URL is "192.168.1.200:80".
* Now goto **Additional applications settings** > **TLS** and enable "No TLS Verify"
if your using a self signed certificate.

>**NOTE:** For my implementation, I didn't need to do the TLS step referenced above.
>I think Cloudflare functionality has changed.

Repeat this process for all the required services/subdomains you wish to support on firewall/router.
In my case, that is the following:

|  Tunnel Name  | Subdomain |       Domain      | Type |         URL        |
|:-------------:|:---------:|:-----------------:|:----:|:------------------:|
| router-tunnel |    blob   | jeffskinnerbox.me | HTTP |  192.168.1.200:80  |
| router-tunnel |    guac   | jeffskinnerbox.me | HTTP | 192.168.1.204:8194 |

#### Step 3: Install the Cloudflare Daemon - DONE
We now  that we have the tunnel and subdomains provisioned on Cloudflare,
we must now establish the Cloudflare daemon (`cloudflared`) on the target machine
(i.e. `firewall-router`) as a Docker container.
We'll do that with:

```bash
# docker script to load cloudflare daemon's on firewall/router
docker run -d  --name cloudflare-tunnel cloudflare/cloudflared:latest tunnel --no-autoupdate run --token <cloudflare-tunnel-token>
```

>**NOTE:** In the above Docker script, I added the `-d --name <tunnel-name>` after the `docker run`
>so it would run the container as a daemon and named the container.

>**NOTE:** Store your token carefully.
>This command includes a sensitive token that allows the connector to run.
>Anyone with access to this token will be able to run the tunnel.
>To get your token, go to left-hand menu and select
>**Traffic** > **Cloudflare Tunnel** > **Launch Zero Trust Dashboard** > **Access** > **Tunnels** > **Configure**.

Better yet, let use Stacks feature within Portainer to build & execute the `cloudflared` daemon.
Portainer Stacks is a thin wrapper around Docker Compose functionality.
A stack is a collection of one or more containers that collectively provide a complete application.
(Fore example, you could have a stack consisting of an API, a database, and a frontend web UI.)
In our case here, the collection of containers isn't needed but using a Docker Compose file makes managment easier.

```yaml
version: "3.9"
services:
  tunnel:
    container_name: cloudflare-tunnel
    image: cloudflare/cloudflared:latest
    restart: unless-stopped
    command: tunnel run
    environment:
      - TUNNEL_TOKEN=<cloudflare-tunnel-token>
```

Now I must go to where I want the daemon to run.
In my case, it on the Proxmox box where I have my pfSense firewall/router running
(hostname `firewall-router`).
I have a virtual machine (VM) running on the Proxmox box for containers called `docker-containers`.
I logged into this VM and ran the above script.

Once the script executes,
You should get Connector ID information on the page,
the Cloudflare Tunnel should be running on Portainer,
and your can move on to routing your first service to it via the **Next** button.

#### Step 4: Check the DNS Records and Test - DONE
Cloudflare needs to add the relevant `CNAME` records for your subdomain.
This is done automatically.
If you check Cloudflare's DNS Records
(via left-hand menu items **DNS** > **Records**),
you'll find the DNS record update for `blog.jeffskinnerbox.me`.

Also, try displaying the `blog.jeffskinnerbox.me` via the command below.

```bash
# check for my blog webpage on port 80 of my linux server 'desktop'
google-chrome blog.jeffskinnerbox.me
```

>**NOTE:** Its important to perfrom this test outside your LAN.
>It is possible that your LAN router will route the request
>successfully without reaching out to DNS.

#### Step 5: Close All Ports - DONE
One of the major benefits of Cloudflare Tunnels is that you have a secure (aka encripted)
tunnel established between your home router and the Cloudflare edge proxy.
There is no long any need to have any open ports on your router to the Internet.
All your traffic, coming or going, is being routed throught the Cloudflare tunnel.

Given this, for maximum security, lets make sure all the incoming ports on the router are closed.
The very first step is to check what ports are open:

>**NOTE:** Its important to test the blocking of the GUI on the WAN from outside your LAN.
>For example, use your mobile phone's browser but with the WiFi turned off.
>If you are testing from within the LAN then the router is likely detecting
>that your using its owns public IP address and isn't forwarding the traffic to your WAN interface.

```bash
# get the ip address for your router (provided by https://ipecho.net/)
$ curl ipecho.net/plain ; echo "   - external IP address"
71.171.85.67   - external IP address

# scan all ports (all 65536 ports) on your router that could be used to access the internet
$ nmap -p- 71.171.85.67
Starting Nmap 7.80 ( https://nmap.org ) at 2023-01-25 16:30 EST
Nmap scan report for pool-71-171-85-67.clppva.fios.verizon.net (71.171.85.67)
Host is up (0.0016s latency).
Not shown: 65532 filtered ports
PORT    STATE SERVICE
53/tcp  open  domain
80/tcp  open  http
443/tcp open  https

Nmap done: 1 IP address (1 host up) scanned in 203.17 seconds

# scan all ports (all 65536 ports) on cloudflare that could be used to access my router
$ nmap -p- jeffskinnerbox.me
Starting Nmap 7.80 ( https://nmap.org ) at 2023-01-25 22:15 EST
Nmap scan report for jeffskinnerbox.me (104.21.61.243)
Host is up (0.0070s latency).
Other addresses for jeffskinnerbox.me (not scanned): 172.67.217.38 2606:4700:3030::ac43:d926 2606:4700:3030::6815:3df3
Not shown: 65523 filtered ports
PORT     STATE SERVICE
80/tcp   open  http
443/tcp  open  https
2052/tcp open  clearvisn
2053/tcp open  knetd
2082/tcp open  infowave
2083/tcp open  radsec
2086/tcp open  gnunet
2087/tcp open  eli
2095/tcp open  nbx-ser
2096/tcp open  nbx-dir
8080/tcp open  http-proxy
8880/tcp open  cddbp-alt

Nmap done: 1 IP address (1 host up) scanned in 601.96 seconds
# you could find that pfsense admin UI is on port 80
google-chrome 71.171.85.67:80
```

I don't want router (aka pfSense) exposing its UI to the Internet!


-----


# How Effective is Cloudflare?
Using [Open-Source Intelligence (OSINT)][76] techniques,
there are ways to identify the IP addresses and hosting arrangements hidden behind Cloudflare
proxy services.

* [Finding Fraudsters Who Hide Behind Cloudflare](https://www.youtube.com/watch?v=UBZBL65Dv1w)


-----


# Cloudflare Authentication
At this point, your servers supported by Cloudflare Tunnels now have
forced usage of HTTPS security (so no one can view your data traveling over the Internet),
encrypted connections from Cloudflare to you server (so you can use HTTP locally on your LAN securely),
your IP address is hidden by the Cloudflare proxy (so no one can attack directly your IP address),
your protected from DDOS attaches (since Cloudflare can monitor and mitigate attacks).

But there is something missing and that is authentication by something other that just a password challege.
We could use an [authentication][05] & [authorization][06] apps such as [Authelia][04],
but here too, Cloudflare has something to offer.

# Cloudflare Access vs Authelia
Some would say
authelia is rather pointless with cloudflare access. If you are using cloudflare tunnels, you might as well use Access which will give you the 'login' like page similar to authelia's portal page. And also no reason to use a reverse proxy too like traefik That is what tunnels is.. Either use traefik and authelia together OR use cloudflare tunnels with access.

* [Authelia and Cloudflare Zero Trust](https://www.authelia.com/integration/openid-connect/cloudflare-zerotrust/)
* [Setup Authelia bare metal with OpenID and Cloudflare Tunnel on a hardened ProxMox LXC Ubuntu 22.04 LTS container](https://florianmuller.com/setup-authelia-bare-metal-with-openid-and-cloudflare-tunnel-on-a-hardened-proxmox-lxc-ubuntu-22-04-lts-container)
* [Authelia on docker without Nginx Proxy Manager](https://www.reddit.com/r/selfhosted/comments/vqesir/authelia_on_docker_without_nginx_proxy_manager/)
* [How To Access Your PCs and Servers from Anywhere Using Guacamole and CloudFlare Tunnels](https://www.youtube.com/watch?v=DGw6P5Lkj-U&t=2060s)
* [Say Goodbye to Reverse Proxy and Hello to Cloudflare Tunnels](https://noted.lol/say-goodbye-to-reverse-proxy-and-hello-to-cloudflare-tunnels/)


-----


# Additional Cloudflare Features

#### Step X: Cloudflare's 1.1.1.1 for Families
Cloudflare claims its mission is to make a [more private and safe Internet experiance][26].
Cloudflare's 1.1.1.1 DNS is designed for [private][23], security, and fast DNS resolution
but not for blocking or filtering content.
Never the less, Cloudflare has received requests to provide a version of the product
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



-------


Check out the following on Cloudflare:
* [Cloudflare Products](https://developers.cloudflare.com/products/)
* [Cloudflare Zero Trust](https://one.dash.cloudflare.com/2dbf9ab9f674a117b229f8c02d0cd234/home/quick-start)
* [Cloudflare Pages](https://developers.cloudflare.com/pages/)
    * [Deploy a Pelican site](https://developers.cloudflare.com/pages/framework-guides/deploy-a-pelican-site/)
* [Cloudflare Radar](https://radar.cloudflare.com/)
* [Cloudflare Speed Test](https://speed.cloudflare.com/)
* [Cloudflare Workers](https://workers.cloudflare.com/)
* [Comprehensive Protection Against Cyber Attacks](https://www.cloudflare.com/under-attack-hotline/)






[01]:https://www.webhostingsecretrevealed.net/blog/security/everything-you-need-to-know-about-cloudflare/
[02]:https://www.cloudflare.com/learning/cdn/what-is-a-cdn/
[03]:https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/
[04]:https://www.authelia.com/
[05]:https://www.authelia.com/overview/authentication/introduction/
[06]:https://www.authelia.com/overview/authorization/access-control/
[07]:
[08]:
[09]:
[10]:https://stevessmarthomeguide.com/dynamic-dns/
[11]:https://www.youtube.com/watch?v=VPcYMgTYQs0
[12]:https://dnschecker.org/
[13]:
[14]:
[15]:
[16]:
[17]:
[18]:
[19]:
[20]:
[21]:https://dash.cloudflare.com/sign-up
[22]:https://www.cloudflare.com/hpg/
[23]:https://blog.cloudflare.com/announcing-the-results-of-the-1-1-1-1-public-dns-resolver-privacy-examination/
[24]:https://blog.cloudflare.com/introducing-1-1-1-1-for-families/
[25]:https://www.amazon.com/Verizon-Fios-Updated-Version-Internet/dp/B07QM33Y51
[26]:https://blog.cloudflare.com/announcing-1111/
[27]:
[28]:
[29]:
[30]:

[50]:
[51]:
[52]:https://www.namecheap.com/
[53]:
[54]:
[55]:
[56]:
[57]:
[58]:https://www.duckdns.org/
[59]:https://wiki.debian.org/DDNS
[60]:https://hackaday.com/2020/08/25/linux-fu-your-own-dynamic-dns/
[61]:
[62]:
[63]:
[65]:
[66]:
[67]:
[68]:
[69]:https://digital.com/best-web-hosting/namecheap/
[70]:https://www.namecheap.com/support/knowledgebase/
[71]:https://support.dnsimple.com/articles/differences-a-cname-records/
[72]:https://www.youtube.com/watch?v=MoePjwotTUE
[73]:https://www.namecheap.com/support/knowledgebase/subcategory/35/registrations/
[74]:
[75]:
[76]:https://www.recordedfuture.com/open-source-intelligence-definition
[77]:https://tecadmin.net/authoritative-non-authoritative-dns-server/
[78]:https://community.cloudflare.com/t/what-is-the-difference-between-proxied-and-dns-only/173310
[79]:https://www.computerhope.com/jargon/d/dns-resolver.htm
[80]:https://unix.stackexchange.com/questions/612416/why-does-etc-resolv-conf-point-at-127-0-0-53
[81]:https://www.howtouselinux.com/post/dns-port
[86]:https://www.dnsstuff.com/clear-flush-dns-server-cache-windows
[99]:https://www.youtube.com/watch?v=NV2eKYmQF6Q
