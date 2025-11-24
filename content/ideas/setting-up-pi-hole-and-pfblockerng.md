<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
    title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>

---------------

Gemini Prompt:

```text
I want to block access to some website on my home guest network.
If I could, I would like to host this utility on a Ubuntu system as a docker container.
What a the three most popular open source utilities for doing this?
```

Gemini Response: Pi-hole, AdGuard Home, andSquid (with a filter plugin)

Gemini Prompt:

```text
Can I set up Pi-hole so that it functions only on my guest network and not on my primary network (or others)?
```

Gemini Response:  Yes, absolutely. This is a very common and excellent use case for Pi-hole.

Gemini Prompt:

```text
Can I set up Pi-Hole so that it blocks only for specific devices?  How would I do this?
```

Gemini Response: Yes, absolutely. This is one of the most powerful features of Pi-hole, and it's called Group Management.
                 The core idea is that you create different "groups," assign blocklists to those groups,
                 and then assign your devices (which Pi-hole calls "clients") to the groups you want.

---------------

* [How I use Pi-hole and Tailscale for whole-network ad blocking](https://www.xda-developers.com/how-i-use-pi-hole-and-tailscale-for-whole-network-ad-blocking/)
* [I use Tailscale for everything now, and it's the most boring but incredible software I run](https://www.xda-developers.com/use-tailscale-for-everything-its-boring-but-incredible/)
* [5 ways I'm using Tailscale for more than just remote access](https://www.xda-developers.com/ways-tailscale-is-more-than-just-remote-access/)

# Local DNS: Pi-hole

The most popular open-source utilities ([Pi-hole][01], [AdGuard Home][02], and [Squid][03])
for block ads and access to websites fall into two main categories:

1. **DNS Sinkholes:** These act as your network's DNS server. When a device on your guest network tries to access a blocked domain,
   the utility sees it on a blocklist and instead of returning the real IP address, it returns a fake one (like 0.0.0.0),
   effectively blocking the site. This is the easiest and most common method for a home network.
1. **Web Proxies:** These require all web traffic to pass through them. They inspect the requests
   and can block not only entire domains but also specific URLs, keywords, or content types.
   This is more powerful but significantly more complex to set up for a guest network
   (it requires a "transparent proxy" configuration on your router).

Here is a quick comparison to help you choose:

| Feature | Pi-hole | AdGuard Home | Squid |
|:-----------:|:-----------:|:-----------:|:-----------:|
| Method | DNS Sinkhole | DNS Sinkhole | Web Proxy |
| Blocks... | Entire Domains | Entire Domains | Domains, URLs, paths |
| Setup (Guest Network) | Easy (via DHCP) | Easy (via DHCP) | Complex (Requires transparent proxy) |
| Primary Use | Ad & Website Blocking | Ad & Website Blocking | Granular Content Filtering |

## Set up Pi Hole so that it functions only on my guest network and not on my primary network (or others)?

### Method 1: The Router DHCP Method (Recommended)

This is the cleanest approach.
The logic is simple: you configure your router to tell only your guest devices to use the Pi-hole for DNS.

  **How it Works:**
  Your router's DHCP server is responsible for giving every device that connects an IP address.
  It also tells that device which DNS server to use.
  Most modern routers allow you to set different DHCP settings for your Main Network and your Guest Network.

1. Find your Pi-hole's IP: First, make sure your Pi-hole server (your Ubuntu system)
   has a static IP address on your network (e.g., 192.168.1.10). You must do this so its address doesn't change.
1. Log in to your router: Access your router's admin panel (usually at 192.168.1.1 or 192.168.0.1).
1. Configure Guest Network DNS:

* Find the Guest Network settings.
* Look for the DHCP or LAN settings specifically for the guest network.
* Find the DNS server setting. By default, it's probably set to "Automatic" or shows your ISP's DNS.
* Change this to Manual and enter the static IP address of your Pi-hole (e.g., 192.168.1.10).

1. Configure Primary Network DNS:

* Now, go to your Primary or Main Network settings (under LAN or DHCP).
* Ensure the DNS server listed here is not your Pi-hole.
* Set it to a public DNS provider like Cloudflare (1.1.1.1) or Google (8.8.8.8).

That's it. Now, when a guest connects, your router tells them to use the Pi-hole for DNS,
and they get filtered. When you connect to your main network,
your router tells you to use 1.1.1.1, and you are not filtered.

### Method 2: The Pi-hole Group Management Method

Use this method if your router is basic and doesn't allow you to set different DNS servers for your guest and main networks.

  **How it Works:**
  In this setup, all devices on all your networks use the Pi-hole for DNS.
  However, you use Pi-hole's powerful Group Management feature to create a "Guests" group and apply blocking only to them.
  Your main network devices will be in a "Default" group that has no blocking.

**Prerequisite:**
This method works best if your router places your guest network on a separate IP subnet
(e.g., Main Network is 192.168.1.x and Guest Network is 192.168.2.x).
This is a standard feature of most guest networks.

1. Log in to your Pi-hole Admin Panel.
1. Go to Group Management > Groups.
1. Create a new group called "Guests" and add a description.
1. Go to Group Management > Adlists.
1. Assign your blocklists to the "Guests" group. Make sure no adlists are assigned to the "Default" group.
1. Go to Group Management > Clients.
1. In the "Add a new client" section:

* IP address: Enter the entire IP range for your guest network using CIDR notation.
    For example, if your guest network is 192.168.2.x, you would enter 192.168.2.0/24.
* Comment: Give it a clear name like "Guest Network Subnet".
* Click Add.

1. In the list of clients below, find the 192.168.2.0/24 entry you just created.
1. Click the "Group assignment" setting for it and assign it only to the "Guests" group. Un-check "Default".

Now, any device that joins your network will be in the "Default" group (no blocking).
But as soon as Pi-hole sees a request from a device in the 192.168.2.x range,
it will automatically apply the "Guests" group rules to it.

## Set up Pi-Hole so that it blocks only for specific devices?

The core idea is that you create different "groups," assign blocklists to those groups,
and then assign your devices (which Pi-hole calls "clients") to the groups you want.

  How it Works:
  By default, all your devices are in the "Default" group, and all your blocklists apply to this group.
  To block only specific devices, you will essentially reverse this:

  1. You will create a new group (e.g., "Blocked Devices").
  1. You will move all your blocklists to this new group.
  1. You will remove all blocklists from the "Default" group.
  1. You will add the specific devices you want to block to your new "Blocked Devices" group.

  This way, any device that connects is "unblocked" by default,
  but the specific devices you add to the "Blocked Devices" group will get the full filtering.

Here is a step-by-step guide to do this.

**Prerequisite:** Identify Your Devices
Before you can block a device, you need a reliable way to identify it.
Pi-hole can do this by its IP address or MAC address.

* IP Address (Good): This is the easiest to find.
  You can see it in your Pi-hole dashboard's "Top Clients" list or your router's client list.
* Static IP (Better): For this to be reliable, the device's IP must not change.
  You should set a Static IP or DHCP Reservation in your router for the devices you want to manage.
  For example, you can tell your router to always give your "Kids_Tablet" the IP address 192.168.1.50.
* MAC Address (Best): This is a unique hardware identifier for a device's network card. Pi-hole can identify clients by this,
  which is ideal because it won't change even if the IP address does.

**Step-by-Step Configuration**

1. Log in to your Pi-hole Admin Panel
   Go to your Pi-hole's web interface (e.g., http://<pi-hole-ip>/admin).
1. Step 1: Create a New Group

* In the left-hand menu, go to Group Management > Groups.
* the "Add a new group" section, type a name. Let's call it Blocked_Devices.
* Add.

1. Step 2: Add Your Devices (Clients)

* Go to Group Management > Clients.
* You will see a list of "Known clients" that Pi-hole has already seen on your network. You can find your device's IP in this list.
* Click Add a new client.
* In the "IP address or MAC address" box, enter the Static IP (e.g., 192.168.1.50) or the MAC address of the device you want to block.
* Add a comment to remember what it is (e.g., "Kids Tablet").
* Click Add.

1. Step 3: Assign the Client to Your New Group

* In the "List of configured clients" table at the bottom, find the device you just added.
* Click on the Group assignment dropdown for that client.
* By default, it is only in the "Default" group. Uncheck "Default" and check "Blocked_Devices".
* Click Apply.

1. Step 4: Assign Your Blocklists to the New Group

* This is the most important step. You are telling Pi-hole which groups should which lists apply to.
* Go to Group Management > Adlists.
* You will see your list of adlists. By default, they are all assigned to the "Default" group.
* For each adlist, click its Group assignment dropdown.
* Uncheck "Default" and check "Blocked_Devices".
* Click Apply after each change (or at the bottom of the list).

1. Step 5: Update Gravity
   After you re-assign lists, you must tell Pi-hole to rebuild its blocking database.

* Go to Tools > Update Gravity.
* Click the big Update button.

That's It!
Now, your setup is complete:

* **New or unknown devices** will be in the "Default" group, which has no adlists assigned to it (so they won't be blocked).
* **The specific devices** you added to the "Blocked_Devices" group will have all of your adlists applied to them, and they will be filtered.

You can repeat Steps 3 and 4 to add more devices or more custom blocklists to this group at any time.

## Using Pi-Hole as a Local DNS Server

With Pi-hole, you can create DNS Entries (A Records) for the clients on your network
and also set up Aliases (pointers to A Records)
so that you can start using DNS at home instead of relying on IP addresses.

* [Using Pi-Hole for Local DNS - Fast, Simple, and Easy Guide](https://www.youtube.com/watch?v=kKsHo6r4_rc)

## You Need Two

When Your Pi-hole Server Goes Down, Your Whole Network Goes Down

* [7 Things I Wish I Knew Before Running a Pi-hole](https://www.howtogeek.com/things-i-wish-i-knew-before-running-a-pi-hole/)
* [I tried many Pi-hole tweaks, and here are the 5 that actually made a difference](https://www.xda-developers.com/pi-hole-tweaks-made-difference/)
* [High Availability Pi-Hole? Yes please!](https://www.youtube.com/watch?v=IFVYe3riDRA&list=RDCMUCOk-gHyjcWZNj3Br4oxwh0A&index=8)
* [Pi-hole Syncing… But Smarter...](https://www.youtube.com/watch?v=OcSBggDyeJ4)
* [I now have two Pi-holes on my network instead of one, and if you have the spare resources, I highly recommend it](https://www.xda-developers.com/two-pi-holes-spare-resources-recommend/)

[01]:https://pi-hole.net/
[02]:https://adguard.com/en/adguard-home/overview.html
[03]:https://cloudinfrastructureservices.co.uk/how-to-block-websites-using-squid-proxy-server/

# Pi-hole

[P-hole][01]
You can run Pi-hole in a container, or deploy it directly to a supported operating system via our automated installer.
I plan to use it only on my Guest network (at least for now), and install it as a container via Docker Compose.

[Pi-hole v6 - Configuration and Overview][02]

## Install Pi-hole Docker Container

I got my `docker-compose.yml` file from [Pi-hole documentation: Docker][03].

## Pi-hole Themes

* [I Took My Pi-Hole to the Next Level With This Custom Theme](https://www.howtogeek.com/took-pi-hole-to-next-level-with-custom-theme/)

## Setup Pi-Hole as a Recursive DNS Server

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

* [Pi-hole v6 - Configuration and Overview](https://www.youtube.com/watch?v=mnry95ay0Bk) - with cloudflare and docker
* [Raspberry Pi DNS-Over-HTTPS (DoH) for Pi-Hole](https://pimylifeup.com/rapberry-pi-dns-over-https/)
* [The ULTIMATE Pi-hole Setup? (Pi-hole, Unbound, Nebula Sync, Keepalived)](https://www.youtube.com/watch?v=6sznCZ7ttbI)

* [5 advanced firewall rules to lock down your home lab](https://www.xda-developers.com/advanced-firewall-rules-to-lock-down-your-home-lab/)

* [Stuff a Pi-hole in your router because your browser is about to betray you](https://www.theregister.com/2025/03/08/pi_hole_6_flyby/)
* [Setting up a secondary Pi-Hole on my home network](https://www.dzombak.com/blog/2024/02/Setting-up-a-secondary-Pi-Hole-on-my-home-network.html)
* [You're running Pi-Hole wrong! Setting up your own Recursive DNS Server!](https://www.youtube.com/watch?v=FnFtWsZ8IP0)

* [Make the FBI happy: install an ad blocker](https://medium.com/enrique-dans/make-the-fbi-happy-install-an-ad-blocker-c6f3ba2ef3a2)

# Setup pfBlockerNG

pfBlockerNG provides advertisement and malicious content blocking along with geo-blocking capabilities.

* [How to Setup pfBlockerNG](https://protectli.com/kb/how-to-setup-pfblockerng/)
* [Tutorial: pfsense and pfBlockerNG Version 3](https://www.youtube.com/watch?v=xizAeAqYde4)
* [Which one is better and the difference between Pi-Hole and pfBlockerNG](https://www.youtube.com/watch?v=6wToQrcvkF8)
* [Wrangling DNS on Your Network, Part 4: Pi-hole vs. pfBlockerNG](https://blog.flippedbits.io/2020/07/wrangling-dns-on-your-network-part-4-pi-hole-vs.-pfblockerng/)

* <https://www.google.com/search?q=pfBlockerNG+vs+pi-hole&sxsrf=APq-WBuzoyfZq_rI-1gtiNroGx5b5RDSlA%3A1647566646921&ei=Nt8zYq_zN6O7ggf5u6jYBw&ved=0ahUKEwiv5u6FwM72AhWjneAKHfkdCnsQ4dUDCA4&uact=5&oq=pfBlockerNG+vs+pi-hole&gs_lcp=Cgdnd3Mtd2l6EAMyBQgAEKIEMgUIABCiBDIFCAAQogQ6BwgAEEcQsAM6BwgAELADEEM6BAgAEEM6BQgAEIAEOgYIABAWEB46BQghEKABSgQIQRgASgQIRhgAUM4GWMcmYIYoaAFwAXgAgAFbiAGoBZIBAjExmAEAoAEByAEKwAEB&sclient=gws-wiz>

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

* <https://github.com/vmstan/gravity-sync>

### Stop Ads & Data Collection

* [Stop your snooping smart TV — how to turn off data collection for every brand](https://www.tomsguide.com/how-to/stop-your-snooping-smart-tv-how-to-turn-off-data-collection-for-every-brand)

### Intrusion Detection

* [Pi Alert - Open Source, Self Hosted, Network Device Change Notific
ation and Intrusion Detection](https://www.youtube.com/watch?v=oKl3WFQloE4)
