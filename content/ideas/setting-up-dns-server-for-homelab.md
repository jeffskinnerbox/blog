<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
        title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>

---------------

* 7 reasons you should a Local DNS server - [7 reasons you should turn your Raspberry Pi into a DNS server](https://www.xda-developers.com/reasons-should-turn-raspberry-pi-dns-server/)
* [Setting up a DNS caching server on your Raspberry Pi is easy - here's how it's done](https://www.xda-developers.com/dns-caching-server-on-raspberry-pi/)
* [5 advanced firewall rules to lock down your home lab](https://www.xda-developers.com/advanced-firewall-rules-to-lock-down-your-home-lab/)
* [Setting up a DNS caching server on your Raspberry Pi is easy - here's how it's done](https://www.xda-developers.com/dns-caching-server-on-raspberry-pi/)
* [Why You Shouldn't Use Your ISP's Default DNS Server](https://www.howtogeek.com/664608/why-you-shouldnt-be-using-your-isps-default-dns-server/)
* [How to Enable DNS Over HTTPS in Google Chrome](https://www.howtogeek.com/660088/how-to-enable-dns-over-https-in-google-chrome/)

Normally, your computer or router uses your ISP’s DNS resolver to query DNS names,
so [why run your own DNS resolver][01]?

* It can speed up DNS lookups
* If you run a mail server
* If you run your own VPN server on a VPS (Virtual Private Server)
* If you don’t like your Internet browsing history being stored on a third-party server

# Consider these DNS / Ad-Blockers

## Technitium

* [Technitium – A Powerful Privacy-Oriented DNS Server](https://www.fossery.com/app/technitium/)
* [Forget about Pi-hole, I switched to this more powerful self-hosted alternative](https://www.xda-developers.com/pihole-alternative-called-technitium/)
* [GitHub: TechnitiumSoftware/DnsServer](https://github.com/TechnitiumSoftware/DnsServer)
* [Technitium DNS Server](https://technitium.com/dns/)

## Bind9

* [You want a real Name Server at home? // DNS](https://www.youtube.com/watch?v=syzwLwE3Xq4)
* [BIND 9](https://www.isc.org/bind/)
* [Bind 9 Documentation](https://bind9.readthedocs.io/en/latest/index.html)
* [DockerHub: ubuntu/bind9](https://hub.docker.com/r/ubuntu/bind9)

* [How To Install And Configure DNS Server In Linux](https://www.youtube.com/watch?v=VjZD3kkBzRE&t=1195s)
* [How to Install and Configure a Private BIND DNS Server on Ubuntu 22.04?](https://www.cherryservers.com/blog/how-to-install-and-configure-a-private-bind-dns-server-on-ubuntu-22-04)
* [How To Configure BIND as a Private Network DNS Server on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-private-network-dns-server-on-ubuntu-20-04)
* [How to Set DNS Nameserver on Ubuntu](https://phoenixnap.com/kb/ubuntu-dns-nameservers)
* [Set Up Local DNS Resolver on Ubuntu 24.04 with BIND9](https://www.linuxbabe.com/ubuntu/set-up-local-dns-resolver-ubuntu-18-04-16-04-bind9)

## pfSense

* [Expert Tips for DNS Optimization in pfSense](https://www.youtube.com/watch?v=syzwLwE3Xq4)

## Candidate Tools

Pi-Hole
AdGuard Home
Unbound
PfBlockerNG
Squid & SquidGuard

* [You want a real DNS Server at home? (bind9 + docker)](https://www.youtube.com/watch?v=syzwLwE3Xq4)
* [How to set up your own open source DNS server](https://opensource.com/article/23/3/open-source-dns-server)
* [AdGuardHome vs Unbound Blacklist vs PiHole](https://www.reddit.com/r/OPNsenseFirewall/comments/pl73lh/adguardhome_vs_unbound_blacklist_vs_pihole/)

* [AdGuard for Desktop and Android: Why We Use the Full Version](https://www.youtube.com/watch?v=yVd3a6oacfU&t=242s)
* [Installing AdGuard Home on PFSense](https://broadbandforum.co/threads/installing-adguard-home-on-pfsense.205884/)
* [AdGuard Home vs. Pi-Hole vs. PfBlockerng: What’s Better for your home network?](https://blog.gravitywall.net/2022/04/04/adguard-home-vs-pi-hole-vs-pfblockerng-whats-better-for-your-home-network/)
* [A Brief Review of AdGuard Home: Definition, Benefits](https://www.sunnyvalley.io/docs/network-security-tutorials/what-is-adguard-home)
* [pfSense pfBlockerNG vs Pihole Pros and Cons](https://www.virtualizationhowto.com/2022/04/pfsense-pfblockerng-vs-pihole-pros-and-cons/)
* [How to Block Ads On All Your Devices With pfSense, Squid & SquidGuard](https://www.privacyaffairs.com/block-ads-with-pfsense/)

# Securing DNS

* [Pi-hole v6 - Configuration and Overview](https://www.youtube.com/watch?v=mnry95ay0Bk) - with cloudflare and docker
* [Pi-hole Syncing… But Smarter...](https://www.youtube.com/watch?v=OcSBggDyeJ4)
* [Raspberry Pi DNS-Over-HTTPS (DoH) for Pi-Hole](https://pimylifeup.com/rapberry-pi-dns-over-https/)

[01]:https://www.linuxbabe.com/ubuntu/set-up-local-dns-resolver-ubuntu-18-04-16-04-bind9
