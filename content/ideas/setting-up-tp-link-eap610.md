<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----



# WiFi Access Point
WiFi access points (APs) don’t have the necessary routing function to form a network.
Consequently, for this setup to work, you’ll need a router.
In this case, a standard non-WiFi one will work and I choose pfSense in my solution.

Wireless access points (AP) generally come in residential and enterprise level solutions.
The [TP-Link EAP610][03], aka Omada EAP610 or Omada Business WiFi 6 AX1800,
is an enterprise level AP supporting the [WiFi 6 (aka 802.11ax) standard][09].
It also supports the legacy wireless standards of IEEE 802.11ax/ac/n/g/b/a
and works in the frequency bands of 2.4 GHz and 5 GHz
(not the 6 GHz since it is not a WiFi 6E access point)
and claims a signal speed of up to 1201 Mbps in 5 GHz band and up to 574 Mbps in the 2.4 GHz band.

WiFi 6 (802.11ax) APs do not improve the performance or range of any legacy WiFi clients (802.11a/b/g/n/ac).
However, as we see more WiFi 6 clients mixed into the client population, the efficiency improvements gained by WiFi 6 client devices will free valuable airtime for those older clients, therefore improving the system’s overall efficiency.
WiFi 6 is nearly three times faster than the previous fastest Wi-Fi standard.
It also is better able to handle multiple devices simultaneously than previous WiFi standards.

The WiFi 6 (aka 802.11ax) standard is radically different from previous generations of WiFi
and so it makes no sense to install WiFi 5 (aka 802.11ac) equipment.
This is particularly true when you have a large number of wireless clients.
The more clients start switching to WiFi 6,
the less busy the radio environment will be.

>**NOTE:** Since my purchase of the TP-Link EAP610,
>a newer version has beeen released, the [TP-Link EAP 620 V3][12].
>This version is smaller in size
>and is designed for many more simultaneous clients.
>As a result, the 620 V3 might be more desirable.

# WiFi 6 (802.11ax)
Where previous generations of WiFi focused on increasing data rates and speed,
[WiFi 6 and 6E][04] (also known as 802.11ax) is the new generation of
WiFi technology with a new focus on efficiency and performance.
WiFi 6 technology is all about better and more efficient use of the existing radio frequency medium,
including better handling higher density  of clients
through a new channel-sharing capability that promises true multi-user communications
on both the downlink and uplink.
It also uses a new client power-saving mechanism
that schedules wake-times to improve client battery life
(great for battery operated IoT devices).
The WiFi 6E standard takes advantage of the new 6 GHz spectrum available for
WiFi which more than double the usable channels of the 2.4 GHz and 5 GHz channels combined.

**The bottom line summary:**
The WiFi 6 (aka 802.11ax) standard will quadruple the capacity for more devices than WiFi 5 (aka 802.11ac)
and WiFi 6 supports flexible channel sizes and resource units that allow operators to offer more efficient IoT support.

More information on WiFi 6:

* [What is WiFi 6? Fastest WiFi? Learn about New AX WiFi Routers from TP-Link!](https://www.youtube.com/watch?v=bQTc72t64z0&t=114s)
* [What is 802.11ax (Wi-Fi 6)?](https://www.extremenetworks.com/wifi6/what-is-80211ax/)
* [WiFi 6 & 6E for Dummies](https://www.extremenetworks.com/wp-content/uploads/2021/09/9781119807889_WiFi-6-For-Dummies_-Extreme-Networks-2nd-Special-Edition.pdf)
* [David Coleman (CWNE#4) on the new 802.11ax (Wi-Fi 6) Wi-Fi standard](https://www.youtube.com/watch?v=rmyrgDSBD4I)
* [WI-FI 6, Why it's the BIGGEST update to Wi-Fi EVER! - 802.11ax](https://www.youtube.com/watch?v=8cmmVEoftEM)
* [When to migrate to Wi-Fi 6?](https://www.youtube.com/watch?v=CZe0VMbaBjw)
* [Does the Number of Spatial Streams in 802.11ax Really Matter?](https://www.extremenetworks.com/extreme-networks-blog/does-the-number-of-spatial-streams-in-802-11ax-really-matter/)
* [What is WiFi 6??? - Speed/Range Test vs WiFi 5 - AX vs AC](https://www.youtube.com/watch?v=T2LdR1K0xNo)

# TP-Link EAP610 (AX1800 WiFi 6)
The question of when to buy a new access point, as always, rests mainly on the cost of such equipment.
The [TP-Link EAP610 (AX1800 WiFi 6)][16] is a budget version of a WiFi 6,
with impressive [specifications][10],
suitable for residential use but engineered for business.
I purchased this $100 access point as part of my migration off a leased FiOS router
to a self-hosted router + firewall + AP home network.

* [TP-Link EAP 610 Review: Adding Wi-Fi 6 to My Home](https://hometechhacker.com/tp-link-eap-610-review-adding-wi-fi-6-to-my-home/)
* [TP-Link EAP 225/EAP 245 V3 Access Point Review](https://hometechhacker.com/tp-link-eap-225-v3-ac1350-access-point-review/)
* [TP-Link Omada Mesh Review: Not Plug-n-Play, but Effective and Affordable](https://dongknows.com/tp-link-omada-class-diy-mesh-review/)
* [TP-Link Omada - Complete Overview](https://www.youtube.com/watch?v=44gYQcHlCFk)

# Omada Controller Software
[Omada EAP][01] is a [Software Defined Networking (SDN)][02] platform
that integrates network devices, including access points,
switches and gateways, providing centralized management.
All devices are controlled from a single interface,
ideal for business solutions using multiple EAPs.

The [TP-Link Omada Hardware Controller (OC200)][05]
is a hardware controller providing centralized management
for up to 100 Omada access points, switches, and routers.
Alternatively, you can install the [Omada software controller][07] on a computer. In this case, you can increase the total APs to up to 500.
You need to use a controller from the beginning. If you’re already using an AP or APs individually and later want to add a controller, you’ll need to reset them all to factory settings and build the mesh from scratch, using the controller — more below.
Conversely, once a controller is involved, you can no longer manage any AP individually — until you reset it.
Ideally, for a business, you should have a controller running at all times. However, for a home, you might get away with having it on only during the setup process or when you want to change some settings or monitor the system.

>**NOTE:** The $25 to $30 TP-Link TL-SG108E switch I'm using for my home network is not
>[controllable via the Omada SDN platform][06].
>You'll need to spend 3 to 4 times as much to get a Omada SDN compatible switch.

* [Omada Software Controller](https://www.tp-link.com/us/business-networking/omada-sdn-controller/omada-software-controller/v5/)

* [User Guide: Omada SDN Controller](https://static.tp-link.com/upload/software/2022/202201/20220121/1910013128-Omada%20SDN%20Controller%20User%20Guide%205.0%20(windows&linux).pdf)
* [Omada SDN Controller User Guide][09]
* [How to Set Up the Whole Network of Gateway, Switches, and EAPs Using Omada SDN Controller | TP-Link](https://www.youtube.com/watch?v=-mkU3rI9coE)
* [Instructions for Managing the Omada EAP Networks](https://www.tp-link.com/en/landing/omada-eap-instruction/)
* [Omada EAP Product Overview](https://static.tp-link.com/upload/product-overview/2021/202107/20210730/EAP%20Datasheet.pdf)



------



# Setup TP-Link EAP610 WiFi 6 Access Point
Omada EAPs support [two configuration modes][11]:

* **Controller Mode** is the preferred method for centrally managing many EAPs in a large-scale wireless network.
You can control all EAPs via a single browser screen all AP, see their statistics, logs, etc. You also have advanced functions frequently used in large-scale network.
* **Standalone Mode** is designed for singly managing a small number of EAPs in a relatively small-sized wireless network.
Each EAP can be configured individually by a mobile app or a management web page resident on the AP.

I choose to manage my EAP via a Web Browser in Standalone Mode.
I followed these steps to set up my EAP:

1. Connect wirelessly by using the SSID of the EAP
(the default SSID is printed on the label at the bottom of the EAP).
2. Launch a web browser and enter `http://tplinkeap.net` in the address bar
(in my case, `192.168.2.14:80`, `admin`, <your standard password>)
Login using `admin` for both the username and password to log in.
3. Set up a new username and password for secure management purpose.
Modify the wireless parameters and reconnect your wireless devices to the new wireless network.

* [User Guide For TP-Link Omada Access Points](https://www.manuals.ca/tp-link/eap610-outdoor/manual)
* [Instructions for Managing the Omada EAP Networks](https://www.tp-link.com/en/landing/omada-eap-instruction/)
* [TP-Link EAP610 Wireless Access Point Installation Guide](https://manuals.plus/tp-link/eap610-wireless-access-point-manual)

#### Step X: Setup AP in Standalone Mode
TP-Link provides a [website to you get started in Omada EAPs][17]
and a [quick installation guide][19].
Read the instructions and determine your optimal management method in your situation,
and then follow the steps provided to set up your network of each method.
To configure and manage a small number of APs, Standalone Mode is recommended.

1. Create an Account on the [TP-Link Product Registration System][08] to get a TP-Link ID.
You'll need this fo the setup.
2. [Download the TP-Link Omada App on your mobile device][18] if you wish to use it.
It can be downloaded from Apple's App Store or Google Play.
3. Connect your mobile device to the EAP by using the default SSID
 printed on the label at the bottom of the product.
4. Open the Omada App, and wait for the EAP to appear on the Standalone APs page.
Tap on the EAP you want to configure.
The Omada App is designed to help you quickly configure the common settings.
5. If you want to configure advanced settings, use the web page of your EAP.
    * Connect wirelessly to the EAP by using the default SSID printed on the label at the bottom of the product
    * Launch a web browser and enter `http://tplinkeap.net` in the address bar.  Use `admin` for both Username and Password to log in.

#### Step X: Install Controller Software
* https://www.tp-link.com/us/support/download/eap610/#Controller_Software

#### Step X: EAP 610 setup with Omada SDN
* [TP-Link EAP 610 Review: Adding Wi-Fi 6 to My Home](https://hometechhacker.com/tp-link-eap-610-review-adding-wi-fi-6-to-my-home/)

#### Step X: Update the Firmware
* https://www.tp-link.com/us/support/download/eap610/#Firmware

#### Step X: Speed Test
* https://www.tp-link.com/us/support/faq/3105/





[01]:https://static.tp-link.com/upload/product-overview/2021/202107/20210730/EAP%20Datasheet.pdf
[02]:https://www.tp-link.com/us/omada-sdn/
[03]:https://www.tp-link.com/baltic/business-networking/omada-sdn-access-point/eap610/
[04]:https://www.extremenetworks.com/wp-content/uploads/2021/09/9781119807889_WiFi-6-For-Dummies_-Extreme-Networks-2nd-Special-Edition.pdf
[05]:https://www.tp-link.com/us/business-networking/omada-sdn-controller/oc200/
[06]:https://www.tp-link.com/sa/omada-sdn/product-list/
[07]:https://www.tp-link.com/us/support/download/eap610/#Controller_Software
[08]:https://myproducts.tp-link.com
[09]:https://www.tp-link.com/us/user-guides/omada-sdn-software-controller/conventions.html
[10]:https://www.tp-link.com/baltic/business-networking/omada-sdn-access-point/eap610/#specifications
[11]:https://www.tp-link.com/us/configuration-guides/methods_for_managing_the_omada_eaps_network/?configurationId=21103#choose_the_management_mode_according_to_your_wireless_network_size_1_1
[12]:https://hometechhacker.com/tp-link-eap-620-v3-review-smaller-size-wi-fi-6/
[13]:
[14]:
[15]:
[16]:https://hwp.media/articles/review_of_tp_link_eap620_hd_wi_fi_6_ax1800_access_point/
[17]:https://www.tp-link.com/en/landing/omada-eap-instruction/
[18]:https://play.google.com/store/apps/details?id=com.tplink.omada
[19]:https://static.tp-link.com/upload/manual/2021/202110/20211027/7106509391-EAP660%20HDIG.pdf
[20]:
[21]:
[22]:
[23]:
[24]:
[25]:
[26]:
[27]:
[28]:
[29]:
[30]:
