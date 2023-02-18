<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="http://www.foxbyrd.com/wp-content/uploads/2018/02/file-4.jpg" title="These materials require additional work and are not ready for general use." align="center">
</div>


-----


Your phone is constantly searching for all WiFi networks which you already connect in the past (unless you did remove as "saved"), saying to anyone who is listening for those public packets where you have been before, and of course, your unique device MAC address.

Those public packets are named as "probe requests" and are used by smartphones to connect faster to wifi networks than if it waits for the network send a Beacon frame to announce the SSID.

This program just listen for those "probe requests" and prints to serial port the information. For now only shows the RSSI (bigger values are near devices), the MAC address of the device and the SSID (if available) of the wifi network which is looking for.





# "The Watcher"
The concept is this:
To make people aware of the fragility of privacy and anonymity,
create an electronic artwork that display personal information about people when they are nearby.

As a person walks by,
the artwork automatically collects from them mobile phone
or other electronic device RF emissions (aka RF exhaust) from the person.

This can be done by making use of:
* sniff MAC address from WiFi devices and store for later identity
* facial & voice recognition
* radar & PIR sensors
* synthetic voice to ask question to help the analysis
  (e.g. Speak to them to move closer to capture voice print or get information like a name to tag a picture.)
* API dips into Open-Source Intelligence (OSINT)
* use DNS exfiltration (e.g. DNS DriveBy) to avoid any need for Internet connection
* etc

* [The Watchman](https://www.hackster.io/taunoerik/the-watchman-dd1f4e)

* [Virtual Peephole](https://www.hackster.io/carolinebuttet/virtual-peephole-355c1c)
* [Virtual Peephole](https://projecthub.arduino.cc/carolinebuttet/848e2c2e-bbe4-4bee-aa08-9e84c9c7c05e)
    * [Insecam](http://www.insecam.org/)
    * [EarthCam](https://www.earthcam.com/)
* [Door Viewer Peephole](https://www.amazon.com/Viewer-Peephole-220-degree-Rotating-Privacy/dp/B07DVT97QW)

* [The Watcher](https://en.wikipedia.org/wiki/The_Watcher_(2022_TV_series)

# DNS DriveBy
* [AlexLynd / ProbeHunter](https://github.com/AlexLynd/ProbeHunter)
* [DNS DriveBy: Stealthy GPS Tracking Using Open Wi-Fi](https://www.hackster.io/alexlynd/dns-driveby-stealthy-gps-tracking-using-open-wi-fi-65730a)
* [Stealthy GPS Tracker & Drive-by Telemetry Using Open Wi-Fi](https://alexlynd.com/Stealthy-Drive-by-GPS-Tracker-ESP8266/)
* [GitHub for DNS-DriveBy](https://github.com/AlexLynd)

# Other Ideas
* [Whisper AI](https://openai.com/blog/whisper/)
* [Stanford Webinar - GPT-3 & Beyond](https://www.youtube.com/watch?v=-lnHHWRCDGk&t=509s)

----------

# Capturing the Data


## Access Point Mapping
Access point mapping, also called [war driving][AA], is the act of locating, typically using GPS, characterizing,
and possibly exploiting connections to wireless local area networks while driving around a city or elsewhere.
Typically when doing war driving, you need a vehicle, a laptop computer,
a wireless Ethernet card set to work in [promiscuous mode][AB],
and some kind of antenna that can work at long range.
The objective is to capture the location of WiFi access point, its open or password protection status,
and other technical parameters.
In the case of war driving, the access point may also be exploited / hacked.

## Active and Passive Scanning
There are two ways to discover WiFi networks:

* **Passively** waiting and listening for announcements (beacon frames) from access points.
* **Actively** asking every WiFi device around if they are an access point (probe requests)
When an access point receives a probe request frame, it will reply with a probe response frame.

Probe requests are a type of WiFi management frame.
They are not encrypted, since they contain no user data.
They are used simply for network discovery.
But it's common that a device will actively ask for a specific network name.
Meaning the probe request will contain the SSID of your known network in clear text.

>**NOTE:** In other words, your phone might be leaking the name of your home network constantly.
>And not just that, it's probably broadcasting the names of every network you ever connected to!

This data can be used to identify you because your phone is likely to have a unique list of known networks.
In addition, services like [WiGLE][AG] can be used to pinpoint an SSID to a specific location.
So by simply listening for probe requests,
you can track how many WiFi clients are nearby and where they have been.
Plus the metadata provided by the MAC address of said clients like the name of the manufacturer.
Too top it off, WiFi clients tend to send probe requests regularly making it possible to track movement.

Probe requests can also be used as a form of denial of service attack.
If a client broadcasts a lot of probe requests with random SSIDs,
the access point can become overwhelmed and the network get clogged.

If this isn't enough, you could collect the SSID from a received probe request from a client,
open a new WiFi network with the same SSID, and wait for a probe response from the client.
The client who sent the request will then automatically connect to that network, thinking it knows it.
But really, it could be a malicious network that's sniffing all your traffic.
(**NOTE:** This is actually a feature oin the [WiFi Pineapple from Hak5][AH].)
There are limits to this type of attack.
You must use the right type of encryption
and the client may not switch if it already has a stronger network signal.

## Access Point Beacon Frames
Becon Frames are transmitted periodically (~100ms) by access-points to announce the presence of a wireless LAN and to synchronise the members (Hi. I’m Mr. AccessPoint. My SSID is XYZ and I’m alive!).
Becon Frames broadcast out to tell any listening devices that this SSID is available and has particular features / capabilities.
Client devices depend upon these beacon frames to discover what networks are available (passive scanning), and to ensure that the networks that they are associated with are actually still present and available.

## WiFi Probe Request Sniffing
You might believe your access points is always broadcasting to make themselves visible to devices,
and you think the device's see a familiar SSID and they join.
Not always!
WiFi clients will also send out probe requests,
blindly hoping that a nearby familiar access point will realise
"Hey, I know that device!
I'll beacon myself so the device can see me and then elect to connect to me".
So probe requests are an 802.11 WiFi packet type that function to automatically
connect network devices to the wireless access points (APs) that they have previously associated with.

Not only can you 'fingerprint' someone by their unique list of 'advertised'
saved networks their device progressively iterates through broadcasting,
you can see where they've been in the real world.
If you believe you know someone's phone via MAC Address,
you can see their past advertised networks and use a tool like Wigle
to see where that network has been recorded in the real world.

* [WiFi Probe Requests Explained](https://blog.spacehuhn.com/probe-request)
* [Capturing Beacons and Probe Requests of Public WiFi Access Points - The Why, How, and Stats](https://blog.samcater.com/capturing-beacons-and-probe-requests-of-public-wifi-access-points-the-why-how-and-stats/)

## MAC Randomization
Some WiFi client (Apple phones for one) will sometime attempt to protect themselves
from being tracked via MAC randomization.
s is where a WiFi clients returns a randomized MAC addresses when responding to a probe requests.
This makes it a lot harder to fingerprint and track a device.
You can easily get the impression that there are more devices around than there actually are.

## Open WiFi
If your out of your home and looking to get an Internet connection,
you could potentially use any open, unsecured wireless network access point you find.
You only barrier for easy automated access is the [captive portal][AK]
that an open WiFi network typically have installed.
If your going to use a randomly found open WiFi network,
you must have a have a way to bypass entering data on the captive portal.
DNS Exfiltration could potentially used to sneak data out of a network by
hiding data as a domain name (aka CNAME record) instead of sending a typical web request.
I say potentially, because if the open WiFi network does ingress DNS traffic filtering,
it could potentially block the data.

### Open WiFi Security Risk
Before you connect with an open WiFi, however, you should know the risks of using open WiFi networks.
In an open WiFi network all information is sent unsecured, without [network layer encryption][AD],
aka plain text.
Open WiFi networks are not using [WiFi protected Access (WPA)][AC],
[WPA2][AC] or [WPA3][AE] security.
Plain text can be intercept, read, and even manipulate to cause you havoc.
So use of a open WiFi network does present risks.
For more on this, see ["Is It Safe to Use an Open Wireless Network?"][AF].

## ???
### Canary Tokens
* [Canary Tokens](https://canarytokens.org/generate)

## DNS Data Exfiltration
DNS is a protocol that lends itself to abuse because it’s largely unmonitored and unrestricted.
DNS is core fuction of the Internet, and as a result, its communication must be supported.
This fact leaves room its explotation.
[DNS Data Exfiltration][AI] is just one way to misuse the DNS protocol.
[Command and Control (C2)][AJ] is another.

DNS Exfiltration is a way to exchange data between two computers without any direct connection.
The data is exchanged through DNS protocol on intermediate DNS servers.
During the exfiltration phase, where the DNS protocol is compromised,
a large amount of unstructured data can be sent
between attacker and victim va data encoded as a CNAME record.

To understand how DNS data exfiltration works, check out the following:

* [How Does DNS Exfiltration Work?](https://www.youtube.com/watch?v=fQ4Y8napHzw)
* [Bypassing Firewalls with DNS Tunnelling (Defence Evasion, Exfiltration and Command & Control)](https://www.youtube.com/watch?v=49F0co_VrTY)

## DNS Data Exfiltration Setup

* [DNS exfiltration of data: step-by-step simple guide][AI]
* [DNS Exfiltration & Tunneling: How it Works & DNSteal Demo Setup](https://helgeklein.com/blog/dns-exfiltration-tunneling-how-it-works-dnsteal-demo-setup/)
* [Easy Data Exfiltration with CanaryTokens](https://alexlynd.com/blog/easy-data-exfiltration-with-canarytokens/)
* [dnscat2](https://github.com/iagox86/dnscat2)
* [dnsteal 2.0](https://github.com/m57/dnsteal)

## Sniffing WiFi Probes
* [mgp25 / Probe-Hunter](https://github.com/mgp25/Probe-Hunter)




[AA]:https://www.techtarget.com/searchmobilecomputing/definition/war-driving
[AB]:https://en.wikipedia.org/wiki/Promiscuous_mode
[AC]:https://www.lifewire.com/what-are-wep-wpa-and-wpa2-which-is-best-2377353
[AD]:https://www.lifewire.com/introduction-to-network-encryption-817993
[AE]:https://www.lifewire.com/what-is-wpa3-wi-fi-4845626
[AF]:https://www.lifewire.com/is-it-safe-to-use-an-open-wireless-network-2378210
[AG]:https://wigle.net/
[AH]:https://shop.hak5.org/products/wifi-pineapple
[AI]:https://hinty.io/devforth/dns-exfiltration-of-data-step-by-step-simple-guide/
[AJ]:https://www.dnsfilter.com/blog/c2-server-command-and-control-attack
[AK]:https://www.linksys.com/what-is-a-captive-portal.html
[AL]:
[AM]:
[AN]:






###############################################################################







* [LILYGO Launches ESP32-S3-Based T-Camera S3 for TinyML Computer Vision Projects](https://www.hackster.io/news/lilygo-launches-esp32-s3-based-t-camera-s3-for-tinyml-computer-vision-projects-47d1a46249ec)
* [T-Camera S3 – An ESP32-S3 board with camera, display, PIR motion sensor, and microphone](https://www.cnx-software.com/2022/12/20/t-camera-s3-an-esp32-s3-board-with-camera-display-pir-motion-sensor-and-microphone/)


The objective is to detect the presence of a person by multiple sensory clues
such as their image but also via motion, heat, sound, or RF exhaust then may make.

* [Building My Perfect Smart Home Presence Detection Sensor!](https://www.youtube.com/watch?v=Viqvx7hMMJs)
    * [I Built My Own Presence Detection Sensor!](https://www.youtube.com/watch?v=VEqWlOeJ2YA)
    * [This New Sensor Is A GAME CHANGER For Your Smart Home!](https://www.youtube.com/watch?v=Leru0rCS8b0)
    * [4 EASY Presence Detection Setups in Home Assistant](https://www.youtube.com/watch?v=Lu0hunynWJY)
    * [mmWave Radar - Human Presence Detection (9m)](https://www.dfrobot.com/product-2282.html)
    * [I'm Making My Own Smart Home Motion Sensor!?](https://www.youtube.com/watch?v=boWsjJlgzag)

* [The BEST Smart Home Room Presence Detection I've Tried!](https://www.youtube.com/watch?v=p7C2QvmsM8M)

* [Everything Presence One](https://shop.everythingsmart.io/en-us)
    * [Everything Presence One](https://github.com/EverythingSmartHome/everything-presence-one)
    * [Everything Presence One - Official Case](https://www.printables.com/model/302846-everything-presence-one-official-case)
    * [My Smart Home Presence Sensor Is Finally Here!](https://www.youtube.com/watch?v=cH5sJFk_2wo&t=6s)
    * [This Smart Home Sensor Blew My Mind! 🤯 mmWave](https://www.youtube.com/watch?v=jVjrgQSWlLI)


* [Person Detection with TensorFlow and Arduino](https://www.hackster.io/little_lookout/person-detection-with-tensorflow-and-arduino-47ae01)
* [TensorFlow Object Detection with Home-Assistant](https://www.hackster.io/robin-cole/tensorflow-object-detection-with-home-assistant-7cc04b)
* [Step Detection System By A Way With Arduino](https://www.hackster.io/juan-salvador-aleixandre-talens/step-detection-system-by-a-way-with-arduino-bc6f3a)

# Motion
# Heat
* [Grid-EYE](https://www.sparkfun.com/products/14607)
# Radar
distance-and-proximity-measurement-sensors.md

# Sound
* [Ambi-Alice Goes Down the Rabbit Hole of Ambisonic Microphones](https://hackaday.com/2021/08/27/ambi-alice-goes-down-the-rabbit-hole-of-ambisonic-microphones/)

## Volume Unit (VU) Meter
A volume unit (VU) meter or standard volume indicator (SVI) is a device displaying a representation of the signal level in audio equipment.

* [The VU Meter And How It Got That Way](https://hackaday.com/2018/08/09/the-vu-meter-and-how-it-got-that-way/)
* [Round LCDs Put To Work In Rack Mount Gauge Cluster](https://hackaday.com/2022/05/13/round-lcds-put-to-work-in-rack-mount-gauge-cluster/)
* [Building A Top-Notch Electret Microphone](https://hackaday.com/2020/11/02/building-a-top-notch-electret-microphone/)
* [Remoticon Video: Making Microphones And Finding Sound](https://hackaday.com/2020/12/08/remoticon-video-making-microphones-and-finding-sound/)
* [MEMS Microphone](https://www.sparkfun.com/products/18011)

# RF Exhaust
* wifi-and-ble-presence-detection-and-tracking.md
* [Secure and cool Remote Controls (Touchless, AES128 encryption, with a T-Beam watch and a cat)](https://www.youtube.com/watch?v=cXh0T1CWtyg)



* [Presence detection with Raspberry Pi, Home Assistant and Monitor](https://www.youtube.com/watch?v=-uRq4L6bxrI&feature=youtu.be)




I want to building a radio listening device that will pickup WiFi & BLE devices,
and (potentially using a network of these devices)
estimate the location of where these device a physically located.
This can be use to:

* to get an estimate of the amount people traffic in a particular area as in
[Monitor Foot Traffic Using Radio](https://hackaday.com/2018/04/06/monitor-foot-traffic-using-radio/)
* xxx
* I'm trying to do what most every advertising platform attempts to do but provides that infromaton to you.
See [Skyhook Wireless Developer Site](http://www.skyhookwireless.com/developers)


----


# Kali
Kali Linux is a Debian-derived Linux distribution designed for digital forensics and penetration testing.

* [Kali Linux 2017.3 hands-on: The best alternative to Raspbian for your Raspberry Pi](https://www.zdnet.com/article/kali-linux-2017-3-hands-on-the-best-alternative-to-raspbian-for-raspberry-pi/)
* [Wifi Autoscaning w/ Raspberry Pi and Kali Linux](http://cdf123x.blogspot.com/2013/04/wifi-autoscaning-w-raspberry-pi-and.html)
* [Kali Linux Tools Listing](https://tools.kali.org/tools-listing)
* [An introduction to the Kismet packet sniffer](https://www.linux.com/news/introduction-kismet-packet-sniffer)
* [Kali Linux Tutorial](https://www.tutorialspoint.com/kali_linux/index.htm)

----

# Presence and Identity

## Sound
* [LASER MIC MAKES EAVESDROPPING REMARKABLY SIMPLE](https://hackaday.com/2010/09/25/laser-mic-makes-eavesdropping-remarkably-simple/)
* [Building A Top-Notch Electret Microphone](https://hackaday.com/2020/11/02/building-a-top-notch-electret-microphone/)
* [Remoticon Video: Making Microphones And Finding Sound](https://hackaday.com/2020/12/08/remoticon-video-making-microphones-and-finding-sound/)
* Coms Over TCP/IP / Sound & Video Transmission - [Nerfnet Tunnels TCP/IP Over NRF24L01 Radios](https://hackaday.com/2020/12/04/nerfnet-tunnels-tcp-ip-over-nrf24l01-radios/)

## Motion
Mimic Go is a portable security device that can be affixed to surfaces or standalone items and sound an alarm when it detects any movement. This means the Mimic Go can be used to monitor fixed locations, like a table or couch, or individual items, like a laptop or purse. The device does not use cameras, microphones or GPS; instead, it relies on an accelerometer, magnetometer, temperature sensor and motion sensor to detect changes in surroundings.
* [Mimic Go](https://smartmimic.com/mimic-go/)
* [Mimic Track](https://smartmimic.com/mimic-track/)

## Video
The Person Sensor includes a camera and microcontroller in a tiny package, and comes pre-loaded with an ML algorithm that can detect people.

* [The Whole Package](https://www.hackster.io/news/the-whole-package-301ee0887def)
* [Sensing a Shift in Edge ML](https://www.hackster.io/news/sensing-a-shift-in-edge-ml-b7761fa3bf5f)
* [Meet the Person Sensor from Useful Sensors!](https://www.sparkfun.com/news/5468)
    * [Auto-Lock your Screen with a Person Sensor](https://www.youtube.com/watch?v=YYvKbOyhNNk&t=1s)
    * [usefulsensors/person_sensor_docs](https://github.com/usefulsensors/person_sensor_docs)
    * [dupontgu/person-sensor-circuitpython](https://github.com/dupontgu/person-sensor-circuitpython)


## Sensing WiFi and BLE Devices
* [Tracking people via WiFi (even when not connected)](https://www.crc.id.au/tracking-people-via-wifi-even-when-not-connected/)
* [Presence detection using phone’s WiFi and Node-RED](https://harizanov.com/2014/03/presence-detection-using-phones-wifi-and-node-red/)
* [Using Raspberry Pi Access Point to Track Devices](https://www.yetanotherblog.com/2014/03/25/using-raspberry-pi-access-point-to-track-devices/)
* [Tracking Devices via Raspberry Pi (Part Two)](https://www.yetanotherblog.com/2014/03/25/tracking-devices-via-raspberry-pi-part-two/)
* [Real-Time Rogue Wireless Access Point Detection with the Raspberry Pi](http://www.linuxjournal.com/content/real-time-rogue-wireless-access-point-detection-raspberry-pi?page=0,0)
* [Portable WiFi Analyzer](https://www.instructables.com/id/Portable-WiFi-Analyzer/)

Detects all Beacons and their mac addresses within range, Detects All AP's in range, Gets GPS Lat/Long positioning,
Gets GPS UTC Time, Logs all this to SD card and displays the information
* [RESQ Hunts For Lost Hikers From The Air](https://hackaday.com/2020/08/12/resq-hunts-for-lost-hikers-from-the-air/)

## Using ESP8266
* [HakByte: Remotely Track Devices over Wi-Fi with the ESP Bug](https://www.youtube.com/watch?v=1uSg9JoDGeU)
* [Monitor Foot Traffic Using Radio](https://hackaday.com/2018/04/06/monitor-foot-traffic-using-radio/)
* [ESP32-Paxcounter is a proof-of-concept device for metering passenger flows in realtime](https://hackaday.com/2018/04/06/monitor-foot-traffic-using-radio/)
* [Quickie WiFi Scanner](http://hackaday.com/2016/02/24/quickie-wifi-scanner/)
* [WiFi Scanner -Know the WiFi Signal around you](https://community.seeedstudio.com/WiFi-Scanner--Know-the-WiFi-Signal-around-you--p-220.html)
* [esp8266locationtracker - Opportunistically track and transmit the location of a ESP8266](https://github.com/dancudds/esp8266locationtracker)
* [ESP8266 Turned Secretive WiFi Probe Request Sniffer](https://hackaday.com/2020/09/20/esp8266-turned-secretive-wifi-probe-request-sniffer/)
* [Hunting Rogue Access Points with the ESP8266](https://hackaday.com/2017/12/28/antenna-alignment-and-hunting-rogue-access-points-with-the-esp8266/)
* [WarWalking With The ESP8266](http://hackaday.com/2016/10/23/warwalking-with-the-esp8266/)
* [Dope Scope - A directional WiFi Sniffing device that fits in the palm of your hand](http://warcollar.com/products/dopescope.html)
* [ESP8266 Sniffer](https://www.hackster.io/kosme/esp8266-sniffer-9e4770)
* [ESP8266 Friend Detector](https://www.hackster.io/ricardooliveira/esp8266-friend-detector-12542e)
* [Wi-Fi Sniffer as Sensor for Humans](https://www.youtube.com/watch?v=fmhjtzmLrg8)
* [Remote Wifi Sniffing Station with an ESP8266](https://www.youtube.com/watch?v=_GQMZg_5FPE)
    * [ETHERNET CONTROLLER DISCOVERED IN THE ESP8266](https://hackaday.com/2016/04/01/ethernet-controller-discovered-in-the-esp8266/)
    * [espthernet](https://github.com/cnlohr/espthernet)
    * https://www.amazon.com/HiLetgo-ENC28J60-Ethernet-Network-Arduino/dp/B00WX1NRO0

----

# Location

## Geoloaction, Geocodes, Maps
* [Unwired Lab Location API](https://unwiredlabs.com/)
* [Geocoding](https://unwiredlabs.com/docs/#geocoding) is the process of converting addresses (like a street address) into geographic coordinates (like latitude and longitude)
* [Reverse geocoding](https://unwiredlabs.com/docs/#reverse-geocoding) is the process of converting geographic coordinates into a human-readable address.
* [Obtain Nearest Address to a Longitude-latitude Point](https://dzone.com/articles/obtain-nearest-address-to-a-longitude-latitude-poi)
* [A Plan To Replace Geographic Coordinates on Earth With Unique Strings of Three Words](https://www.smithsonianmag.com/science-nature/plan-replace-geographic-coordinates-earth-unique-strings-three-words-180949946/)
* [3 Word Address](http://what3words.com/)
* [Plus Code](https://plus.codes/)

## ZIP Code
* [What the ZIP in ZIP Code Really Means](https://medium.com/knowledge-stew/what-the-zip-in-zip-code-really-means-4342492a4f1b)

## Location Platforms
Use Skyhook Precision Location on a Raspberry Pi device running Raspbian Linux.
The device will continuously record its location, even when disconnected from the internet or not.

* [Skyhook Wireless Developer Site](http://www.skyhookwireless.com/developers)

## Geolocation Without GPS Module
* [Location using ESP8266 | Geolocation Without GPS Module](https://electronicsforu.com/electronics-projects/gps-geolocation-using-esp8266-projects)
* A consolidated location and information of wireless networks world-wide to a central database: [Wireless Geographic Logging Engine (WiGLE)](https://en.wikipedia.org/wiki/WiGLE)
    * [WiGLE.net](https://wigle.net/)

#Bluetooth
* [Get Apple To Track Your Bluetooth Devices For You](https://hackaday.com/2021/03/05/get-apple-to-track-your-bluetooth-devices-for-you/)

# WiFi and Cell ID Positioning
Wi-Fi “sniffing” is a great way to do rough location processing.
A sensor reads the MAC ID and signal strength of WiFi Access Points nearby,
sends that data to the cloud.
A WiFi MAC ID database,
like [Google](https://developers.google.com/maps/documentation/geolocation/intro#wifi_access_point_object),
[Wigle](https://wigle.net/),
[SkyHook](http://www.skyhookwireless.com/submit-access-point),
or a cell site ID with [Polet](https://www.polte.com/),
[OpenCellid](https://opencellid.org/),
[Mozilla Location Service (MLS)](https://location.services.mozilla.com/)
calculates location.

Traditionally, getting WiFi information required a fairly expensive Wi-Fi module,
Semtech has released the LR1110.
This chip includes a GPS processor, WiFi scanner, and a Lora radio

* [Combain](https://combain.com/)
* [How Google--and everyone else--gets Wi-Fi location data](http://www.zdnet.com/article/how-google-and-everyone-else-gets-wi-fi-location-data/)
* [OpenCellid](https://opencellid.org/) - The world's largest Open Database of Cell Towers from [Unwired Labs](http://unwiredlabs.com/)
* [Location using ESP8266 | Geolocation Without GPS Module](https://electronicsforu.com/electronics-projects/gps-geolocation-using-esp8266-projects)
* A consolidated location and information of wireless networks world-wide to a central database: [Wireless Geographic Logging Engine (WiGLE)](https://en.wikipedia.org/wiki/WiGLE)

## Indoor Location
* [WiFinder](https://github.com/mpescimoro/wi-finder)
* [whereami](https://github.com/kootenpv/whereami)
    * [wherearehue](https://github.com/DeastinY/wherearehue)
* multiple object tracker projects on github
    * https://github.com/search?q=topic%3Agps-tracker&type=Repositories
    * https://github.com/search?q=topic%3Awifi-fingerprints&type=Repositories
    * https://github.com/search?q=topic%3Alocation-services&type=Repositories

### Framework for Internal Navigation and Discovery (FIND)
* [Framework for Internal Navigation and Discovery (FIND)](https://www.internalpositioning.com/)
* [FIND FAQ](https://www.internalpositioning.com/faq/)
* [Offical version writen in Go - FIND GitHub](https://github.com/schollz/find3)
* [Python version - FIND GitHub](https://github.com/kootenpv/find)
* [find-lf - extension of FIND, the Framework for Internal Navigation and Discovery](https://github.com/schollz/find-lf)
* [Track Wi-Fi Devices In Your Home](https://hackaday.com/2016/12/25/track-wi-fi-devices-in-your-home/)
* [Creepy Wireless Stalking Made Easy](https://hackaday.com/2016/12/04/creepy-wireless-stalking-made-easy/)

----

# Gathering Atributes

## Probe Requests Sniffing
First, you use this as a “presence detection” mechanism.
You can track the presence of people in a specific area.
Being at home, I could detect when my neighbor is back at home and uses his laptop.
Then, the detected SSID’s could help you to learn a lot about your potential victim.
The goal is to “put a face” on the MAC address. You can learn the type of device/ISP they use.
You can learn about the habits (and later to perform social engineering). hotel SSID’s, restaurant SSID’s etc.

* [Show me your SSID’s, I’ll Tell Who You Are!](https://blog.rootshell.be/2012/01/12/show-me-your-ssids-ill-tell-who-you-are/)
* Build movement-aware applications: [HyperTrack](https://www.hypertrack.com/)
    * [HyperTrack Documentation](https://docs.hypertrack.com/)

----

# Telemetry Over Opportunistic WiFi Links

## Open / Captive Portal Hotspots
* [TOWL - Telemetry over Opportunistic WiFi Links](http://www.phreakmonkey.com/2016/08/towl-telemetry-over-opportunistic-wifi.html)

## Using Management Frames
* [Smuggler - An interactive 802.11 wireless shell without the need for authentication or association](https://www.trustwave.com/Resources/SpiderLabs-Blog/Smuggler---An-interactive-802-11-wireless-shell-without-the-need-for-authentication-or-association/)
* [Chura-Liya](https://github.com/interference-security/Chura-Liya)
* [Beacon Stuffing Beacon Frames and Injection](https://www.youtube.com/watch?v=SPY3W_Kmq8U)

## DNS Tunneling
* [How DNS Tunneling Works](http://inside-out.xyz/technology/how-dns-tunneling-works.html)
* [DNS 101: An introduction to Domain Name Servers](https://www.redhat.com/sysadmin/dns-domain-name-servers)
* [DNS Tunneling: Getting The Data Out Over Other Peoples’ WiFi](http://hackaday.com/2016/08/07/getting-the-data-out-over-other-peoples-wifi/)
* [hy big ISPs aren’t happy about Google’s plans for encrypted DNS](https://arstechnica.com/tech-policy/2019/09/isps-worry-a-new-chrome-feature-will-stop-them-from-spying-on-you/)
* [Nameserver Transfer Protocol (NSTX)](http://thomer.com/howtos/nstx.html)
* [iodine](http://code.kryo.se/iodine/)
* [dnscat2 – DNS Tunnel Tool](http://www.darknet.org.uk/2016/01/dnscat2-dns-tunnel-tool/)
* [Tunneling Data and Commands Over DNS to Bypass Firewalls](https://zeltser.com/c2-dns-tunneling/)
* [PowerShell DNS Command & Control with dnscat2-powershell](http://www.blackhillsinfosec.com/?p=5578)

### Domain Name Server (DNS)
* [Introduction to the Domain Name System (DNS)](https://opensource.com/article/17/4/introduction-domain-name-system-dns)
* [Build your own DNS name server on Linux](https://opensource.com/article/17/4/build-your-own-name-server)
* [dnsd: DNS encoder, decoder, and server](https://github.com/ansuz/modern-dnsd)
* [DNS Is Still the Achilles Heel of the Internet](https://www.darkreading.com/partner-perspectives/f5/dns-is-still-the-achilles-heel-of-the-internet/a/d-id/1329019)
* [Firefox Announces New Partner in Delivering Private and Secure DNS Services to Users](https://blog.mozilla.org/blog/2019/12/17/firefox-announces-new-partner-in-delivering-private-and-secure-dns-services-to-users/)

# Capturing Cellphone IMSI
An international mobile subscriber identity (IMSI) is a unique number, usually fifteen digits, associated with Global System for Mobile Communications (GSM) and Universal Mobile Telecommunications System (UMTS) network mobile phone users. The IMSI is a unique number identifying a GSM subscriber.

* [You Can Easily Get Into Anybody’s Smartphone with this Tool](https://www.techtimes.com/articles/246754/20200103/you-can-easily-get-into-anybody-s-smartphone-with-this-tool.htm)
* [How to make a simple $7 IMSI Catcher](https://www.youtube.com/watch?v=UjwgNd_as30)

# Seeing WiFi
* [Building a Camera That Can See Wifi | Part 3 SUCCESS!](https://www.youtube.com/watch?v=g3LT_b6K0Mc&t=154s)

# Electronic Art / Sculpture
What if the presence detection said "hi" to the people entering the room or house?
What if it took their picture or other action?

* [This Dynamic Piece of Art Responds to Its Picture Being Taken](https://www.hackster.io/news/this-dynamic-piece-of-art-responds-to-its-picture-being-taken-fe22bf39e189)
* [ARTWORK THAT KNOWS WHEN YOU ARE TAKING A PICTURE OF IT](https://taunoerik.art/2022/09/04/artwork-that-knows-when-you-are-taking-a-picture-of-it/)



