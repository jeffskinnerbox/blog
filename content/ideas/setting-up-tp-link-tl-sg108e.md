<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----


I latter replace the 8-port [TP-Link TL-SG108E][06] (MAC Address 5C:A6:E6:17:38:98) with the 16-port [TP-Link TL-SG116E][07] (MAC Address 30:DE:4B:9E:37:CF).


[TP-Link TL-SG108E switch][06]
[TP-Link TL-SG108E Version 6.6][06]

* [TL-SG108E User Guide](https://static.tp-link.com/res/down/doc/TL-SG108E_V2_UG.pdf)
* [TL-SG108E Installation Guide](https://static.tp-link.com/res/down/doc/TL-SG105E_V2_IG.pdf)
* [p-link - TL-SG108E - Just cheap managed switches for me from now on!](https://www.youtube.com/watch?v=x1-7_cbov4s)
* [TL-SG108E Unboxing and BASIC Setup Tutorial (TP-Link Smart Ethernet Switch)](https://www.youtube.com/watch?v=8V3ftwdV3Jg)


# Managed & Unmanged Smart Switch
Unmanaged switches are plug and play.
You connect one of the ports to your existing LAN via Ethernet to receive
additional physical Ethernet port connectivity via the switch.

A managed switch is required to provide support for the VLANs.
Make sure the switch supports 802.1Q, which is the ability to apply VLAN tags to traffic.
A Smart switch offers some basic management features like QoS for a lag-free experience
and VLAN for security,
but a managed switch typically can provide a broader set of features.

I purchased the [TP-Link TL-SG108E][06] to establish my Ethernet LAN.
While not a Managed Switch, it is a Smart Switch, poviding the most popular management features.
Out of the box, it’s a simple switch which you can just plug in and use without any configuration.
It comes with [TP-Link browser-based management software][01] so you can:

* [monitor the ports on the switch][02] so you can see what is using up all your network
* set the QoS on ports (so you can make sure your VOIP calls get priority over video streaming)
* set up ports with higher priority (so your media server gets priority over your kid’s machines)
* set up [VLANS][03] (so you can segment your LAN and limit access like keeping your IoT or WiFi off your core home network)

* [Managed VS Unmanaged Switches and Support For InterVLAN Routing / Layer Three Switch Routing](https://www.youtube.com/watch?v=WqAqeS4tDL8)
* [Do I Need a Managed Switch For My Smart Home?](https://planetechusa.com/do-i-need-a-managed-switch-for-my-smart-home-network)
* [Building my lan: do I need a managed switch for my VLANs?](https://forum.netgate.com/topic/158556/building-my-lan-do-i-need-a-managed-switch-for-my-vlans)
* [can i run VLANs on unmanaged switches?](https://www.reddit.com/r/homelab/comments/a1k464/can_i_run_vlans_on_unmanaged_switches/)
* [Managed vs Unmanaged Switch – What are the Differences](https://lazyadmin.nl/home-network/managed-vs-unmanaged-switch/)
* [Managed vs Unmanaged Switch: Which One Can Satisfy Your Real Need?](https://community.fs.com/blog/managed-vs-unmanaged-switch-which-one-can-satisfy-your-real-need.html)
* [Converting single NIC mini-pc into pfSense router/firewall by using virtual LAN configuration on a managed switch](https://www.joe0.com/2019/11/16/converting-single-nic-mini-pc-into-pfsense-router-firewall-by-using-virtual-lan-configuration-on-a-managed-switch/)



#### Step 1: Power Up and Access the Switch - DONE
To find out the IP address of the switch (and all the other device on your LAN),
power up the switch, connected it to you LAN, and use the following to find the IP address:

```bash
# flush the arp cache of old data
sudo ip -s -s neigh flush all

# power up the switch and attach it to the network

# scan the network to wake up the switch user interface
nmap -sP 192.168.1.0/24

# identifying all devices on a network - print fqdn, ip address, mac address, nic
echo -e "\nFQDN IP-Address MEC-Address NIC" | awk '{ printf("%-45s %-15s %-19s %-8s\n", $1, $2, $3, $4) }' ; arp -a | sed 's/(// ;  s/)//' | awk '{ printf("%-45s %-15s %-19s %-8s\n", $1, $2, $4, $7) }' | sort -k3
```

But there’s an even quicker way, that’s also more precise.
It turns out hardware vendors actually has a range of MAC addresses all to themselves!
These ranges will have a prefix assigned, the [Organizationally Unique Identifiers (OUI)][12],
for the Ethernet or WiFi network interface on their device.
The best resource to find the most current OUI assignments
is from the [MAC Address Block Large (MA-L) Public Listing at the IEEE][13].
You have to register for IEEE site, but [OUILookup][14] is open to the public.

Alternatively, you can search directly for the MAC address of the device, if you know it.
For my switch, it happens to be printed on the bottom of the device.
Search for the MAC address via:

```bash
# ping scan the network to assure host becomes visible and then search for the MAC address
$ nmap -sP 192.168.1.0/24 > /dev/null ; arp -na | grep "at 5c:a6:e6"
? (192.168.1.21) at 5c:a6:e6:17:38:98 [ether] on eth0

# OR
# finding IPs and identifying devices on your network
sudo netdiscover -c 3 -s 10 -L -N -r 192.168.1.0/24

# OR
# search for all the OUI's registered to tp-link
$ nmap -sP 192.168.1.0/24 > /dev/null ; arp -na | grep -i -e "5c:a6:e6" -e "60:32:B1" \
    -e "C0:C9:E3" -e "F8:8C:21" -e "80:EA:07" -e "E4:C3:2A" -e "90:9A:4A" -e "84:D8:1B" \
    -e "3C:84:6A" -e "D0:37:45" -e "60:3A:7C" -e "54:A7:03" -e "B0:BE:76" -e "34:E8:94" \
    -e "AC:84:C6" -e "94:D9:B3" -e "B0:95:8E" -e "C0:25:E9" -e "24:69:68" -e "80:89:17" -e "00:27:19"
```

>**NOTE:** If the switch cannot receive an IP address from a DHCP server,
>it uses the static IP address of 192.168.0.1, with a subnet mask of 255.255.255.0.

With the switch plugged into the LAN,
and assuming it receives an IP address from a DHCP server in your network,
point your browser at the IP address captured with the above scripts.
The default login / password is `admin` / `admin`.

#### Step X: Update Switch Firmware - DONE
To update the firmware,
goto the [TP-Link offical download page][10].

#### Step X: Setting Up VLANs
* [What are VLANs? -- the simplest explanation](https://www.youtube.com/watch?v=MmwF1oHOvmg)
* [VLAN vs Subnet: What Are Their Differences?](https://www.fiber-optic-transceiver-module.com/vlan-vs-subnet.html)
* [Native VLAN - the DEFINITIVE illustration](https://www.youtube.com/watch?v=Fmq1E1Qr2W4)
* [Converting single NIC mini-pc into pfSense router/firewall by using virtual LAN configuration on a managed switch](https://www.joe0.com/2019/11/16/converting-single-nic-mini-pc-into-pfsense-router-firewall-by-using-virtual-lan-configuration-on-a-managed-switch/)



[01]:https://www.youtube.com/watch?v=x1-7_cbov4s
[02]:https://www.metricfire.com/blog/10-best-open-source-switch-port-monitoring-tools/
[03]:https://www.linkedin.com/pulse/importance-using-vlans-segment-network-traffic-mike/
[04]:
[05]:
[06]:https://www.tp-link.com/us/business-networking/easy-smart-switch/tl-sg108e/
[07]:https://www.tp-link.com/us/business-networking/easy-smart-switch/tl-sg116e/
[08]:
[09]:
[10]:https://www.tp-link.com/us/support/download/tl-sg108e/v6.6/
[11]:
[12]:https://en.wikipedia.org/wiki/Organizationally_unique_identifier
[13]:https://standards.ieee.org/products-services/regauth/oui/index.html
[14]:https://ouilookup.com/
[15]:
[16]:
[17]:
[18]:
[19]:
[20]:


