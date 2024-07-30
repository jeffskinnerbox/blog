!--
M:qaaintaineraintainer:   <jeffskinnerbox@yahoo.com> / <www.jeffskinnerbox.me>
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----




* [Caddx Goggles X Questions Firmware & HDMI - Its Just Not Good Enough](https://www.youtube.com/watch?v=sjQYSTWbrqQ)
  * [Caddx Avatar HD Goggles X Update - How To & Discussion](https://www.youtube.com/watch?v=EhOi91cIbQ0)
* [Caddx Walksnail Goggles X FPV Goggles Antenna Ports - What Transmits & Receives](https://www.youtube.com/watch?v=8Wa_XjQBKqs)
* [CaddX FPV Goggles X Overheating Explored - What Is Going On?](https://www.youtube.com/watch?v=CCBAy7WU5jc)
  * [Goggles X New Firmware Update - Did The Fix The Thermal Issue ?](https://www.youtube.com/watch?v=NNnGt994mt4)
* [Caddx Walksnail Goggles X - Analog input problem](https://www.youtube.com/watch?v=EgTJesEsdgw)
  * [Caddx Walksnail Goggles X - Analog input update](https://www.youtube.com/watch?v=X3f7bJE8qpI)





# How Does FPV Video Work?

* [How Analog Video works in FPV!](https://www.youtube.com/watch?v=szJOUXineYw)
* [FPV Video Systems](https://www.youtube.com/playlist?list=PLFPBjpbd5xKT14YIDasgjmaefic4Qcd2R)
* [Explained: How FPV technology works - ANALOG](https://www.youtube.com/watch?v=8x9z36z_wvA)

Protocols in FPV can be divided into 3 groups:

```
<-- In Your Hands --><----------------------- On The Quadcopter ------------------------------------>
+-------+            +----------+           +-------------------+            +-----+        +-------+
| Radio |------------| Receiver |-----------| Flight Controller |------------| ESC |--------| Motor |
+-------+            +----------+           +-------------------+            +-----+        +-------+
         TX Protocols            RX Protocols                    ESC Protocols


<----------- In Your Hands ------------><-------------------- On The Quadcopter -------------------->
+---------+                 +----------+                     +-------------+               +--------+
| Goggles |<----------------| Reciever |<--------------------| Transmitter |<--------------| Camera |
+---------+                 +----------+                     +-------------+               +--------+
```

* TX Protocols – communication between radio transmitter (TX) and radio receiver (RX)
* RX Protocols – communication between radio receiver (RX) and flight controller (FC)
* ESC Protocols – communication between FC and ESC

* [FPV Protocols Explained (CRSF, SBUS, DSHOT, ACCST, PPM, PWM and more)](https://oscarliang.com/rc-protocols/)
* [GitHub: pascallanger/DIY-Multiprotocol-TX-Module](https://github.com/pascallanger/DIY-Multiprotocol-TX-Module)






# Quadcopter Video Systems
FPV goggles provide a first person video (FPV) image of your flying experiance and come in two technology categories: analog and digital.
Analog is the oldest, most affordable, and most prevalent technology, it’s available in 5.8GHz, 2.4GHz and 1.2/1.3GHz.
In contrast, digital technology, which offers superior image quality, is newer and gaining popularity.
How long before digital replaces analog FPV ... [who knows][08].

The decades-old analog technology is not proprietary to any specific company,
allowing anyone to create components for the system.
Consequently, it is the most widely available system on the market,
and until mid-2019, analog was the only FPV option.
There are dozens of cameras, video transmitters, and goggles from multiple manufacturers, all compatible with each other.
Analog is the most affordable way to enter the world of FPV.

Pros & Cons of Analog Solutions:

* Pros
  * Affordable
  * Widely available
  * Consistent and low latency
  * A vast selection of hardware (camera, VTX, goggles) from various manufacturers, you are not locked into a single brand
  * Various feature sets and price points
* Cons
  * Low image quality, akin to watching a 1970s TV with poor signal
  * More sensitive to interference and electrical noise
  * Variable hardware quality due to the vast number of manufacturers
* Price for typical analog FPV solution
  * Camera: $15 – $40
  * Video Transmitter (VTX): $15 – $40
  * FPV Goggles (VRX): $80 – $500

Currently there are three digital FPV systems available for FPV drones.
All of them are 5.8GHz systems, and none of the them are cross-compatible with each other as they are all proprietary systems.
Currently the available digital FPV system are: DJI, HDZero and Walksnail Avatar.
Despite this and because of its superior technical characteristics,
digital is expected to become mainstream in the near future.

Pros & Cons of Digital Solutions:

* Pros
  * Superior image quality compared to analog
  * More robust against interference than analog
  * Typically FPV goggles support AV input for analog systems
  * Appears to be the future of FPV flying
* Cons
  * More expensive than analog systems (currently)
  * You are locked into provider ecosystem
  * Variable latency, not ideal for racing but less of an issue for freestyle and cruising
  * Few nexpensive & small video transmitter, unsuitable for small FPV drones
* Price for typical digital FPV solution
  * Camera + Video Transmitter (VTX): $100 – $230
  * FPV Goggles (VRX): $240 – $650

So it appears to me that, if your budget allows for it, go digital!
The superior image quality provides an immersive FPV experience that analog just can’t match,
and the digital product manufactures are innovating & investing where analog is not.
Analog has lower latency (maybe important for a racer),
digital latency is not likely to be noticed by average flyer.
At the same time, analog is comparatively in expensive and will always have a use case that it is suited for.
To address this, key feature to look for within digital goggles is support of analog video transmitters, and some can!

Sources:

* [Review: Walksnail Avatar Goggles X – Enhanced Versatility, User Experience and Future-proofing](https://oscarliang.com/walksnail-avatar-goggles-x/)
* [Walksnail Goggles X For Avatar HD - All In One FPV With Some Compromises!](https://www.youtube.com/watch?v=ti3zyavDOow)
* [Is Walksnail Goggles X Your Ultimate FPV Goggle?](https://www.youtube.com/watch?v=9PXz_zB8qfY)
* [Avatar Goggles X: Latency Test, Flight Footage and Review](https://www.youtube.com/watch?v=giQUHcDA1cY)
* [Which FPV System Should You Buy in 2024? Analog, DJI, HDZero, Walksnail Avatar](https://oscarliang.com/fpv-system/)
* [Choosing the Best VTX (Video Transmitter) for FPV Drones – The Ultimate Beginner Guide](https://oscarliang.com/video-transmitter/)
* [Ultimate FPV Goggles Guide: Find the Best FPV Headset for Every FPV System](https://oscarliang.com/fpv-goggles/#Digital-vs-Analog-Choosing-Your-Ideal-FPV-System)
* [Which FPV System Should You Buy in 2023? Analog, DJI, HDZero, Walksnail Avatar](https://oscarliang.com/fpv-system/)
* [Best FPV Goggle 2023 Buyer's Guide // DJI v. HDZERO v. WALKSNAIL v. ANALOG](https://www.youtube.com/watch?v=TMOeIQ4VRX4&t=77s)
* [Cheap vs. Expensive FPV Goggles - What's the Difference??](https://www.youtube.com/watch?v=oOEbygcWk-w)
* [The best FPV goggle for almost everybody (except DJI) // HDZERO GOGGLE REVIEW](https://www.youtube.com/watch?v=TPnGVad9Cm8)
* [How Long Will It Be Until Analog Is No Longer Used For FPV? Digital Cost?][08]


# Is a Ham Radio License Needed When Flying FPV?
The short answer is yes, you need at least a Level 1: [Technician License][21] to operate FPV drones legally.
The vast majority of FPV VTX (video) systems operate in the 5.8 MHz ham radio bands, between 5650MHz to 5925MHz.
These frequencies are governed by [FCC Part 97][22] (aka ham radio, amateur radio).
Take a look at [this chart][28] for a visual representation
of the various FPV VTX bands, frequencies, and how they fall in the amateur range.

Anything that broadcasts a radio signal in the United States must follow the rules of the Federal Communications Commission (FCC).
According to the FCC there are basically two ways to operate equipment,
such as our FPV video transmitters (VTX), within the RF spectrum allocated for such use.

1. The first way is to use equipment that is certified by the FCC under part 15,
which means the company who created it has submitted it to the FCC for approval
and the FCC agrees that the equipment meets all the standards,
transmits at appropriate power levels, does not cause interference, and so on.
2. The second way to comply with the FCC rules is to have an amateur radio operators license.
In that case you have proven that you understand the FCC rules,
you know how to operate radio broadcasting equipment,
and you can be trusted to operate hardware that has the potential to cause interference to others.
This license then gives you permission to use these devices within appropriate power levels
on frequencies within the US amateur allocations.

Except in a few cases, none of the modern FPV video transmitters has an FCC part 15 certificate.
Therefore the person operating the equipment must have a Technicians level ham license in order to operate it.
This is why you see a warning on all the major FPV stores in the US when you try to purchase a VTX from their website.
They are letting you know that it is YOUR responsibility to follow the regulations and know how to use this equipment properly.

The FCC has determined that video links used as a part of an RC system are considered telecommand devices.
FCC HAM radio compliant FPV transmitters have a 1 watt limit for amateur devices being used for telecommand.
Devices over 1 watt output should not be used for telecommand of model aircraft.

In summary, the use and operation of FPV analog & digital VTX 5.8GHz product in the USA,
and many other countries, requires a license and some countries may forbid its use entirely.
In the USA, you will need a "HAM" amateur radio license.
Make sure to [learn more about HAM licenses][17], and [find a HAM license exam session in your area][18].
**It is your responsibility to ensure that the use of this product meets the requirements imposed by your government's rules and regulations for RF devices.**

* [Is a Ham Radio License Needed When Flying FPV?](https://fpvfc.org/ham-license)
* [Why Do You Need A Ham Radio License for Flying FPV Drones?](https://hamradioprep.com/fpv-drones-using-a-ham-radio-license/)
* [The Different Frequencies for FPV](https://oscarliang.com/fpv-frequency/)
* [5.8GHz FPV Channels & Frequency Chart (Analogue & Digital)](https://oscarliang.com/fpv-channels/)
* [HAM Radio License for FPV – All You Need to Know](https://myracingdrone.com/ham-radio-license-for-fpv-drone/)


# My Choose: Walksnail Avatar
I agonized over the decision of going with a digital video solution but not pricing myself out of the flexibility of analog solutions.
I even consider buying an inexpensive analog solution for now and upgrade to digital at a later date.
It seem like delaying going digital could even cost me more in the end.
Then the [Walksnail Avatar HD Goggles X][01] by [CaddxFPV][02] came up on my radar.
These goggles, which came on the market in the year of my search (2023), seem to have it all.

Sources:

* [Walksnail Goggles X For Avatar HD - All In One FPV With Some Compromises!](https://www.youtube.com/watch?v=ti3zyavDOow)
* [Future-Proof Digital FPV - Walksnail Goggles X](https://www.youtube.com/watch?v=-TlAkSeTkfU)
* [Walksnail Avatar HD Goggles X](https://caddxfpv.com/collections/walksnail-avatar-hd-goggles-x/products/walksnail-avatar-hd-goggles-x)


## Video Reciever (VRX): Walksnail Avatar HD Goggles X
My choose of FPV goggles were the [Walksnail Avatar HD Goggles X][01].
They are resonably prices at $459, which might have been discounted bacuse they were newly on the market.
Unlike many goggles, they appeared to have good antennas (4 Lollipop antennas) and didn't need to be replace (making the price even more attractive!).
Analog AV input and HDMI input means the goggles can work with a broad set of video recivers.
Wide 50deg field of view, 100FPS frame rate, 1920x1080 OLED screen resolution, resoanable average latency of 22ms,
built-in WiFi/Bluethooth/Gyro, and Bluetooth tethered app to configure the goggles.
To top it off, CaddxFPV appears be planning reciver module upgrades instead of whole goggle replacement for new features.

One thing that I think is missing from these goggle is DVR.
There is no way of recording video on the Walksnail Avatar HD Goggles X, unless you use the HDMI output port.
<-- NOT SURE THIS IS TRUE ... there is a SD-Card slot

* Product Features
  * Weight 290g
  * OLED screen 1920x1080
  * Field of view (FOV) 50°
  * Adjustable focus range of +2 to -6 diopter
  * Power 7-26V (aka 2S-6S) via XT60 to DC 5.5*2.1mm power cord
  * Inter-pupillary distance (IPD) mechanical range 57mm-72mm
  * Infrared Sensing to turn the screen on/off
  * Digital H.265 video encoding 1080p/100fps, 1080p/60fps, 720p/100fps, 720p/60fps
  * Supports 8 video channels (5.725-5.850GHz) with a range of 4km
  * Receiving module can be replaced (minimizing upgrade costs)
  * HDMI input to support external video transmitters (digital video)
  * HDMI output to external display devices to share your flight footage (digital video)
  * AV in via 3.5mm with 4 conductor TRRS/3 port (analog video)
  * Digital video recording (DVR) to SD card (supports 256G)
  * 4 [Left-hand circular polarized (LHCP)][06] stubby antennas ([2dBi gain][05])
* Product Options
  * Front cover supports DIY community
  * Lenses can be replaced
  * Built-in Gyro (in development)
  * Built-in Bluetooth/WiFi module (in development) for firmware upgrade, phone apps, live viewing, etc.

>**NOTE:** Because of the goggles antennas are left-hand polarized (LHCP),
>[you should make sure to use LHCP antenna on your quadcopter][07], or if you can't, a linear polirized antenna.


## Video Transmitter (VTX): Walksnail Avatar

* [Is this the best Digital FPV System? Walksnail Avatar V2 is here!](https://www.youtube.com/watch?v=d0VoBp9-sn4)


## On Screen Display (OSD)


### Race Mode

* [Walksnail Avatar for Racing? Nano V3 VTX Review](https://www.youtube.com/watch?v=Qn2wejRJWcY)
* [RACE MODE for Walksnail Avatar: Image Quality and Latency Testing](https://www.youtube.com/watch?v=O9iuNx8eXss)


### OLED Sunlight Damage
Sunlight can cause damage to your OLED screen.


### Avatar HD Latancy

* [Digital FPV Latency & Frame Delivery - DJI - HDZero - Avatar HD - A Lot To Understand.](https://www.youtube.com/watch?v=d7gfLaCHU2w)



-------






-------



# FPV Video Channels

* [5.8GHz FPV Channels & Frequency Chart (Analogue & Digital)](https://oscarliang.com/fpv-channels/)


# VR Headset

* [Open Source VR Headset For $200](https://hackaday.com/2020/09/13/open-source-vr-headset-for-200/)
* [AKK 5.8G RC832 Mini FPV Receiver Double-Screen Display for FPV Quadcopter Drone](https://www.amazon.com/gp/product/B01FXFZ0NS)
* [AKK A2 5.8Ghz 200mW FPV Transmitter Raceband 600TVL 1/4 Cmos Mini FPV Micro AIO Camera with Clover Antenna for FPV Drone](https://www.amazon.com/gp/product/B06VSW41LN)



--------



# FPV Ground Station
Using a ground station is a great way to improve your FPV feed.
I purchased the [SkyZone SteadyView X 5.8GHz receiver module as a ground station][10].

Sources:

* [NEW! Skyzone SteadyView X GroundStation Module: Analogue FPV is alive and well!](https://www.youtube.com/watch?v=OWhsxzaGRKI)
* [Skyzone Steadyview X Review](https://www.youtube.com/watch?v=IMRyGvRCT2o)
* [RapidFIRE Killer? SkyZone SteadyView X Ground-Station - Overview & Side By Side Comparison](https://www.youtube.com/watch?v=AW6FxBitkcw)
* [Flite Test - FPV Ground Station - REVIEW](https://www.youtube.com/watch?v=RG76qShdKuU)
* [FPV Ground Station Setup & Overview + Testing](https://www.youtube.com/watch?v=j4l6KQfhtUM)
* [BUILD AN FPV GROUNDSTATION - MY SETUP](https://www.youtube.com/watch?v=S2wnS1T5haY)
* [My Analog FPV Ground Station](https://www.youtube.com/watch?v=F2AFC-iG6sU)
* [OpenIPC FPV news will blow your mind! Tests with ExpressLRS and INAV](https://www.youtube.com/watch?v=3IhKBH3aWdE)


## SKYZONE SteadyView X 5.8Ghz Receiver Module
[Steadyview X][10] is the upgrade V3.3 version of steadyview receiver.
This receiver merge two signals to one, avoid image tearing and rolling in multi-path environment,
make image more stable and clear in challenging condition.
This video reciver has an [IPS screen][11] and [shuttle wheel][12],
use can the shuttle wheel to set the recieved channel.
This SteadyView X receiver also comes as a ground station KIT (i.e. not to be fitted on your goggles),
so it can be use with a monitor or goggles which have an analog audio/visual input port (aka AV IN, 3.5mm with 4 Conductor TRRS/3).
For powering the unit, it supports a voltage range of 7-26V (aka 2S-6S) via XT60 to Barrel connector power cable.
The kit also comes with 1 patch and 1 omi antenna.

Also, the Steadyview X have an [ELRS backpack build in][13].
User can use the [ELRS backpack][14] on the Steadview receiver,
along with ELRS transmitter (aka controller), to synchronize the VTX & VRX
to the same 5.8GHz channel.
You can see how this is done via [ExpressLRS ESP Backpack documentation][14]
and [this video for RadioMaster Boxer][15].

The SkyZone reciver operates in the frequency range of 5.3 to 6GHz within 6 bands and 8 channels in each band,
as shown below:

| BAND/CH |  CH 1 |  CH2  |  CH3  |  CH4  |  CH5  |  CH6  |  CH7  |  CH8  |
|:-------:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|
|    A    | 5865M | 5845M | 5825M | 5805M | 5785M | 5765M | 5745M | 5725M |
|    B    | 5733M | 5752M | 5771M | 5790M | 5809M | 5828M | 5847M | 5866M |
|    E    | 5705M | 5685M | 5665M | 5645M | 5885M | 5905M | 5925M | 5945M |
|    F    | 5740M | 5760M | 5780M | 5800M | 5820M | 5840M | 5860M | 5880M |
|    R    | 5658M | 5695M | 5732M | 5769M | 5806M | 5843M | 5880M | 5917M |
|    L    | 5362M | 5399M | 5436M | 5473M | 5510M | 5547M | 5584M | 5621M |


Read more: <https://manuals.plus/skyzone/steadyview-x-high-performance-receiver-manual#ixzz8Jp0IhZC8>

You can find the SteadyView+ELRS user manual and the SKY04X firmware [here][09].

Sources:

* [Skyzone Steadyview X Review](https://www.youtube.com/watch?v=IMRyGvRCT2o)
* [NEW! Skyzone SteadyView X GroundStation Module: Analogue FPV is alive and well!](https://www.youtube.com/watch?v=OWhsxzaGRKI)
* [My Analog FPV Ground Station](https://www.youtube.com/watch?v=F2AFC-iG6sU)
* [ELRS Backpack: Use Radio to Change VTX and HDZero Goggle Channel Simultaneously][15]
* [RapidFIRE Killer? SkyZone SteadyView X Ground-Station - Overview & Side By Side Comparison](https://www.youtube.com/watch?v=AW6FxBitkcw)
* [New Fusion V3.3 Board for Skyzone Steadyview/RapidMix Module Fixes Dark Rolling Issues](https://oscarliang.com/skyzone-steadyview-module-fusion-v3-3/)


## Antenna Tracker

* [Eagle Tree Antenna Tracker Tutorial](https://www.rcgroups.com/forums/showthread.php?2520717-Eagle-Tree-Antenna-Tracker-Tutorial-RCGroups-FPV-Video-Review)



------



# Field Monitor: FPV Monitor Shares Flights in Real Time

* [How to Make a 7" DIY Field Monitor for $40!](https://www.youtube.com/watch?v=xn7F37SM8t)
* [Raspberry Pi FPV monitor shares drone flights in real time](https://www.msn.com/en-us/news/technology/raspberry-pi-fpv-monitor-shares-drone-flights-in-real-time/ar-BB1lN5CX)
* [Raspberry Pi FPV monitor shares drone flights in real time](https://www.tomshardware.com/raspberry-pi/raspberry-pi-fpv-monitor-shares-drone-flights-in-real-time)
  * [BUILDING DIGIVIEW FPV Monitor - Apr-8-2024](https://www.youtube.com/watch?v=3cmDLvn4n60)



------



# Quick Start: Walksnail Avatar HD Goggles X
The [Walksnail.app][19] website and the instruction that come with the Goggle X provide the best information sources:

* [Quick Start Guide: Walksnail Avatar HD Goggles X - version 1.1](https://drive.google.com/file/d/1cHqAo9fJaTjIRYDzmEljbj7aH-69VpwK/view)
* [All WalkSnail & FatShark Avatar Firmware Releases](https://walksnail.app/firmware)
* [Caddx Avatar HD Goggles X Update - How To & Discussion](https://www.youtube.com/watch?v=EhOi91cIbQ0)

[OscarLiang.com][16] provides a very detailed outline on how to setup the Walksnail product line.
While necicsarily specific to the Avatar HD Goggles X, the procedures are informative:

* [How to Setup Walksnail Avatar Digital HD FPV System](https://oscarliang.com/setup-avatar-fpv-system/#How-to-Update-Firmware-on-GogglesVRX)


## How to Check Firmware Version on Goggles X


## How to Update Firmware on Goggles X
Here’s the summary:

Download the upgrade firmware with a file name like this: AvatarX_Gnd_X.X.X.img (X.X.X is the version number). Copy it to the root directory of the SD card. Make sure NOT to change the file name.
Insert SD card back in the goggles, and plug in the battery to power them on.
When you see the home screen, press and hold the link button on the Goggles for 8 seconds, and the Goggles should automatically restart and start beeping. (Do not power off during the upgrade.
The firmware update can take around 5 to 10 minutes, when complete, the beeping should stop and the goggles will reboot.



Flashing Firmware
You can download firmware files from one of these sites:

Official releases: <https://caddxfpv.com/pages/download>
Latest/Beta releases: <https://avatar-firmware.d3vl.com/>
Fatshark’s own download site: <https://fatshark.helpscoutdocs.com/article/174-dominator-with-avatarhd>
There are 4 firmware files, for different devices:

Avatar_Sky is for the VTX
Avatar_Gnd is for the Avatar/Fatshark Dominator HD goggles
AvatarSE_Gnd is for the VRX module
AvatarMini_Gnd is for the Fatshark Recon HD goggles
Make sure to power your goggles and VTX with a fully charged battery as the update can take up to 10 minutes. Powering down during update might brick your devices.

Fatshark Dominator HD goggles can flash the Avatar Goggles firmware (that’s what I’ve been doing and no issue so far), and according to many comments I’ve read online they are basically the same goggles just different in colors.

The Avatar Mini Gnd is for Fatshark Recon HD Goggles.



Download Avatar_Gnd_xx.xx.x.IMG
Take the SD card out of the goggles and insert it into your computer
Put the Avatar_Gnd_xx.xx.x.img file to the root directory of the SD card
Eject the SD card and put it it back into the Avatar goggles
Power up the goggles and wait until you see the Standby screen
Push and hold the Link button for 8-10 seconds. The headset screen will go black indicating the start of the update process
The update will take a few minutes
During the update, the goggles will beep. This is normal. DO NOT turn off the headset until the update is finished
When the update is complete, the beeping will stop and the headset will boot back up to the Standby screen


## Flight Video Recording
Cross-platform tool for rendering the flight controller On Screen Display (OSD) and SubRip Subtitle (SRT) data from the Walksnail Avatar HD FPV system on top of the goggle or VRX recording

* [Add Walksnail OSD To Your Flight Video after Your Flight!](https://www.youtube.com/watch?v=eI3lojDyZ8U)
* [GitHub: avsaase/walksnail-osd-tool](https://github.com/avsaase/walksnail-osd-tool)
* [What is an SRT File and How do I Make One?](https://www.youtube.com/watch?app=desktop&v=2Z1sxaLehdI)



[01]:https://caddxfpv.com/products/walksnail-avatar-hd-goggles-x
[02]:https://caddxfpv.com/
[05]:https://antennatestlab.com/antenna-education-tutorials/what-is-antenna-gain-dbi-scale
[06]:https://www.youtube.com/watch?v=mbHl3DgnN4k
[07]:https://www.drone24hours.com/uncategorized/what-is-the-difference-between-rhcp-and-LHCP-antenna/?lang=en
[08]:https://www.youtube.com/watch?v=JhxRcoPvkG8
[09]:https://www.skyzonefpv.com/pages/download
[10]:https://www.skyzonefpv.com/products/skyzone-steadyview-x-5-8ghz-ips-screen-receiver-module
[11]:https://www.hp.com/au-en/shop/tech-takes/post/what-is-an-ips-monitor
[12]:https://en.wikipedia.org/wiki/Jog_dial
[13]:https://cdn.shopifycdn.net/s/files/1/0597/9668/4956/files/SteadyView_ELRS_USER_Manual_V1.0.pdf
[14]:https://www.expresslrs.org/hardware/backpack/esp-backpack/
[15]:https://www.youtube.com/watch?v=ISzX80aK9T0
[16]:https://oscarliang.com/
[17]:https://www.arrl.org/ham-radio-licenses
[18]:https://hamradioprep.com/find-an-exam-near-you/
[19]:https://walksnail.app/
[20]:
[21]:https://www.arrl.org/getting-your-technician-license
[22]:https://www.arrl.org/part-97-text
[23]:
[24]:
[25]:
[26]:
[27]:
[28]:https://fpvfc.org/fpv-frequency-chart
[29]:
[30]:

