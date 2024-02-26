<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----



* [PiHole on Docker and Kubernetes (I almost gave up)](https://www.youtube.com/watch?v=NRe2-vye3ik)
* [High Availability Pi-Hole? Yes please!](https://www.youtube.com/watch?v=IFVYe3riDRA&list=RDCMUCOk-gHyjcWZNj3Br4oxwh0A&index=8)
* [Setting up a secondary Pi-Hole on my home network](https://www.dzombak.com/blog/2024/02/Setting-up-a-secondary-Pi-Hole-on-my-home-network.html)
* [You're running Pi-Hole wrong! Setting up your own Recursive DNS Server!](https://www.youtube.com/watch?v=FnFtWsZ8IP0)

* [Make the FBI happy: install an ad blocker](https://medium.com/enrique-dans/make-the-fbi-happy-install-an-ad-blocker-c6f3ba2ef3a2)




# Setup pfBlockerNG
pfBlockerNG provides advertisement and malicious content blocking along with geo-blocking capabilities.

* [How to Setup pfBlockerNG](https://protectli.com/kb/how-to-setup-pfblockerng/)
* [Tutorial: pfsense and pfBlockerNG Version 3](https://www.youtube.com/watch?v=xizAeAqYde4)
* [Which one is better and the difference between Pi-Hole and pfBlockerNG](https://www.youtube.com/watch?v=6wToQrcvkF8)
* [Wrangling DNS on Your Network, Part 4: Pi-hole vs. pfBlockerNG](https://blog.flippedbits.io/2020/07/wrangling-dns-on-your-network-part-4-pi-hole-vs.-pfblockerng/)

* https://www.google.com/search?q=pfBlockerNG+vs+pi-hole&sxsrf=APq-WBuzoyfZq_rI-1gtiNroGx5b5RDSlA%3A1647566646921&ei=Nt8zYq_zN6O7ggf5u6jYBw&ved=0ahUKEwiv5u6FwM72AhWjneAKHfkdCnsQ4dUDCA4&uact=5&oq=pfBlockerNG+vs+pi-hole&gs_lcp=Cgdnd3Mtd2l6EAMyBQgAEKIEMgUIABCiBDIFCAAQogQ6BwgAEEcQsAM6BwgAELADEEM6BAgAEEM6BQgAEIAEOgYIABAWEB46BQghEKABSgQIQRgASgQIRhgAUM4GWMcmYIYoaAFwAXgAgAFbiAGoBZIBAjExmAEAoAEByAEKwAEB&sclient=gws-wiz

# Setup Pi-Hole as a Recursive DNS Server
 With Pi-Hole you can also completely bypass 3rd party DNS servers like `8.8.8.8`, `1.1.1.1`, `208.67`, `222.222`, or the ones ran by your ISP.

There are two types of DNS servers: authoritative and recursive.

Pi-hole is a DNS Forwarder
Unbound is a DNS Resolver / DNS Cashing Server

The first question that needs to be answered is why you might want to setup Unbound on Pi-hole. Ultimately, the answer is somewhat simple, and it’s mostly privacy related. When you use Pi-hole, you generally configure an upstream DNS provider. The first thing you need to realize is that all traffic is being sent from your external IP address, so depending on who you’re sending the data to, you’re trusting them with your internet traffic.

The other issue is that periodically, these services will go down. In that case, it might appear as if your internet “stopped” working, when the reality is that it simply cannot resolve DNS names. While this is infrequent, it does happen.

When you install Unbound, you become your DNS provider. This ensures that your privacy is maintained, and you will no longer be impacted by potential service outages.


* [DNS Resolver](https://www.computerhope.com/jargon/d/dns-resolver.htm)
* [Authoritative and Recursive DNS](https://umbrella.cisco.com/blog/what-is-the-difference-between-authoritative-and-recursive-dns-nameservers)

* [You're running Pi-Hole wrong! Setting up your own Recursive DNS Server!](https://www.youtube.com/watch?v=FnFtWsZ8IP0)
* [Stop Giving Away your Data and Web Profile. Use Pi-hole with Unbound DNS. Make Privacy Number 1!](https://www.youtube.com/watch?v=PN6xDD-CGXE)
* [Is adding 3 MILLION domains to your Pi-Hole Block List a good thing?](https://www.youtube.com/watch?v=0wpn3rXTe0g)
* [Unbound](https://www.nlnetlabs.nl/projects/unbound/about/)
* [Unbound Pi-hole Setup | Learn how to Increase your Privacy!](https://www.wundertech.net/use-unbound-to-enhance-the-privacy-of-pi-hole-on-a-raspberry-pi/)

* [Setting up Pihole on proxmox with pfsense](https://www.youtube.com/watch?v=lxbuK5HQlX4)

# Using Pi-Hole as a Local DNS Server
With Pi-Hole, you can create DNS Entries (A Records) for the clients on your network
and also set up Aliases (pointers to A Records)
so that you can start using DNS at home instead of relying on IP addresses.

* [Using Pi-Hole for Local DNS - Fast, Simple, and Easy Guide](https://www.youtube.com/watch?v=kKsHo6r4_rc)

# Setup Pi-Hole
Pi-hole is a general purpose network-wide ad-blocker that protects your network from ads and trackers without requiring any setup on individual devices. It is able to block ads on any network device (e.g. smart appliances), and, unlike browser add-ons, Pi-hole blocks ads on any type of software.

This is basically a black hole for advertising and telemetry requests on your network. The request goes from your device to your router, which uses the pi-hole as a DNS server. The Pi-Hole decides whether the request should be relayed back to your router or not. The website thinks it served you an ad, or sent telemetry data somewhere, but it just goes into a "DNS Sink"...the Pi-Hole. Ad-heavy news/sports/badaudioreview websites run MUCH faster, and it's fun to watch all the BS getting re-routed into the "DNS Sink" from your apps, smart TVs, etc. It even blocks ad services inside iPhone/iPad apps, since it runs at the router.

It's inferior to browser extensions like Adblock or uBlock because those can collapse the space left by the blocked ad. It's nonetheless a decent project, even teaches newbies to configure their own recursive resolver through unbound.

* [Goodbye telemetry and ads – running Pi-Hole in a home network](https://jussiroine.com/2021/07/goodbye-telemetry-and-ads-running-pi-hole-in-a-home-network/)
* [Review: Pi-hole on Windows 10](https://www.andrewdenty.com/blog/2020/04/24/review-living-with-pi-hole-on-windows-10.html)
* [Should you use Pi-Hole for blocking ads? (using a Raspberry Pi 4)](https://www.mbreviews.com/pi-hole-for-blocking-ads-raspberry-pi-4/)
* [Pi-hole review: Network-level ad and tracker blocking](https://home-assistant-guide.com/2020/09/20/pi-hole-review-network-level-ad-and-tracker-blocking/)

* [Docker Compose File for Pi-Hole](https://github.com/xcad2k/boilerplates/blob/main/docker-compose/pihole/pihole.yaml)

* [How to update Pi-hole easily](https://varhowto.com/update-pi-hole/)

* [Raspberry Pi - Setup Pi-Hole for DNS Security](https://www.youtube.com/watch?v=KiJ8JFR_y1w)
* [block ADULT sites and other BAD STUFF on your home network (EASY)](https://www.youtube.com/watch?v=BSplICgr7iU)
* [BLOCK EVERYTHING w/ PiHole on Docker, OpenDNS and IFTTT](https://www.youtube.com/watch?v=dH3DdLy574M&t=0s)

# Gravity Sync
* https://github.com/vmstan/gravity-sync

### Stop Ads & Data Collection
* [Stop your snooping smart TV — how to turn off data collection for every brand](https://www.tomsguide.com/how-to/stop-your-snooping-smart-tv-how-to-turn-off-data-collection-for-every-brand)

### Intrusion Detection
* [Pi Alert - Open Source, Self Hosted, Network Device Change Notification and Intrusion Detection](https://www.youtube.com/watch?v=oKl3WFQloE4)

