<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>



-----



* [SparkFun VR IMU Breakout - BNO086 (Qwiic)](https://www.sparkfun.com/products/22857)




Read this for it good discription of GNSS & NMEA messages
* [Global Positioning Basics](https://www.youtube.com/watch?v=kUUNY-gWT6U&list=PLxCxJVCmDz7oZ05xk2eG27APw5xmEeZaU)
* [Global Positioning Basics - 6 NMEA Messaging Protocol](https://www.youtube.com/watch?v=2f96rrnE0FU)
* [ANSI C Basic Lightweight NMEA Parser for GPS](https://www.beyondlogic.org/ansi-c-basic-lightweight-nmea-parser-for-gps/)
* [NMEA 2000 Explained - A Simple Intro](https://www.csselectronics.com/pages/nmea-2000-n2k-intro-tutorial)

* [How To Make GPS Tracker](https://cellularnews.com/mobile-accessories/how-to-make-gps-tracker/)

# Table of Contents
* Background
    * [Polynesian Wayfinding](https://hackaday.com/2024/02/01/polynesian-wayfinding-traditions-let-humans-roam-the-pacific-ocean/)
    * [Navigation Technologies](#background-navigation-technologies)
    * [GNSS Technologies](#global-navigation-satellite-systems-gnss)
* BerryGPS Setup
    * [Setup for Raspbery Pi Zero](#raspberry-pi-zero-setup)
    * [Setup for OzzMaker's BerryGPS](#setup-for-ozzmakers-berrygps)
    * [Setup for OzzMaker's IMU](#setup-for-ozzmakers-imu)
* Ultimate GPS Setup
    * [Setup for Adafruit's Ultimate GPS](#setup-for-adafruits-ultimate-gps)
* GNSS Tools
`xgps`, `xgpsspeed`, `cgps`, `lcdgps`, `gegps` via `man xgps`.
pip install gps
pip install pynmea2
sudo apt -y install gpsd-clients gpsd
sudo apt -y install python-gps gnuplot
You will find more information about `xgps`, `xgpsspeed`, `cgps`, `lcdgps`, `gegps` via `man xgps`.
`xgps`, `cgps`, `gpsmon`, `gegps`, `gpsprof`, `gunplot`, `xgpsspeed`, `xgpx`
`gpscat`,  `gpspipe`, `gpxlogger`

# Linux GNSS Tools
* [A Beginner’s Guide To Using gpsd (GPS Devices) In Linux](https://kickstartembedded.com/2022/07/23/a-beginners-guide-to-using-gpsd-in-linux/)
* [Tutorial – gpsd](https://www.linux-magazine.com/Issues/2018/210/Tutorial-gpsd)
* [Getting GPS to work on a Raspberry PI](https://area-51.blog/2012/06/18/getting-gps-to-work-on-a-raspberry-pi/)

## gpsd Daemon
`gpsd` is a service daemon that monitors one or more Global Navigation Satellite Systems (GNSS)
or Automatic Identification System (AIS) receivers
attached to a host computer through serial or USB ports.
All data on the location/course/velocity of the sensor is available
to be queried on TCP port 2947 of the host computer.

```bash
# displays current GNSS position/time/velocity information
cgps
#OR
cgps -s          # -s flag is there to tell the command not to write raw data to the screen

# watches packets coming from a GPS and displays them along with diagnostic information
gpsmon
#OR
gpsmon -n        # -n forces gpsmon to request NMEA0183 packets instead of the raw datastream from gpsd

# At its simplest, gpspipe takes a parameter that tells it which format to use and just dumps the stream from gpsd to the standard output
# You could use gpspipe to send all the information to a file and keep track of a trip or a run
gpspipe -r       # stream raw NMEA sentences to the terminal
#OR
gpspipe -w       # stream json formatted gpsd sentences to the terminal
```

For `cgps`, the 3D FIX section tells you it has enough data for a 3D fix on your location (i.e. altitude).
The Err lines tell you the error in your position.
If you leave it running you should see the Err values change every second or so.

# Generate NMEA Data
A drawing tool for generating GPS logs in NMEA format.
Also can inport NMEA files for displaying.

* [NMEA Generator](https://www.nmeagen.org/)





<!-- ----------------------------------------------------------------------------------------------------------------------------- -->







* [Send Location & Make Call using SOS Button | IOT Projects | GPS Projects](https://www.youtube.com/watch?v=E-5vazIDznc)
* [Getting Started with A9G Board | GSM + GPRS + GPS](https://www.youtube.com/watch?v=Yi5dgZBiq7g&list=RDCMUC7raRsx4ojx3cyXT3x9-PuQ&start_radio=1)
    * [Ai Thinker A9G GSM/GPRS+GPS/BDS Development Board](https://www.amazon.com/Module-Development-Wireless-Transmission-Positioning/dp/B07QDR4ZP6)
    * [A9G GSM/GPRS+GPS Module](https://www.dfrobot.com/product-2114.html)
    * [A9G Module SKU TEL0134](https://wiki.dfrobot.com/A9G_Module_SKU_TEL0134)
    * [A9G based GPS Tracker, SOS Button & Audio Spy Project | Multipurpose IoT Project | ESP32 Projects](https://www.youtube.com/watch?v=--gt-wCcEiM)
    * [Find My Cat -- the GPS Tracker for Pets](https://www.instructables.com/Find-My-Cat-the-GPS-Tracker-for-Pets/)

* [https://github.com/features/copilot](https://www.seeedstudio.com/Grove-GPS-Air530-p-4584.html)

* [Circuit Walker Sneakers pt. 1: Accelerometer Filtering w/ Tony D!](https://www.youtube.com/watch?v=zr4Pu3F-yJw)

* [Maidenhead Locator System (aka Grid Squares)](https://www.karhukoti.com/Maidenhead-Grid-Square-Locator/)




# GPS / Map Display Servers
* [Traccar](https://www.traccar.org/)
* [Linxup GPS Fleet Tracker, Vehicle Tracker, and Monitoring System with Real-Time Location GPS Tracking Reports](https://www.amazon.com/dp/B006TZGJDC/ref=syn_sd_offsite_desktop_128)



* [GPS Basics](https://learn.sparkfun.com/tutorials/gps-basics)
* [How GPS Works, And How It Got Better Than The Designers Ever Imagined](https://www.youtube.com/watch?v=qJ7ZAUjsycY)
* [GPS Tracking Comparisons](https://www.sparkfun.com/tutorials/169)
* [Building a GPS System](https://www.sparkfun.com/gps)
* [Building A GPS With Bug Eyes And Ancient Wisdom](https://hackaday.com/2019/09/06/building-a-gps-with-bug-eyes-and-ancient-wisdom/)
* [Building A GPS Receiver From The Ground Up](https://hackaday.com/2024/01/02/building-a-gps-receiver-from-the-ground-up/)
    * [GitHub: leaningktower/Analog-GPS-data-receiver](https://github.com/leaningktower/Analog-GPS-data-receiver)

* [Add GPS Time and Location to a Raspberry Pi Project](https://www.rs-online.com/designspark/add-gps-time-and-location-to-a-raspberry-pi-project)
* [Product Showcase: SparkFun GNSS Receiver MAX-M10S](https://www.youtube.com/watch?v=Yh8pLKs7aaY)
* [Adafruit Ultimate GPS on the Raspberry Pi](https://learn.adafruit.com/adafruit-ultimate-gps-on-the-raspberry-pi?view=all)
* [Adafruit Ultimate GPS](https://learn.adafruit.com/adafruit-ultimate-gps/)
* [SMA to uFL/u.FL/IPX/IPEX RF Adapter Cable](https://www.adafruit.com/product/851)
* [Adafruit GPS library](https://github.com/adafruit/Adafruit_GPS)
* [Python library for Raspberry PI for Ultimate GPS based on MTK3339 with serial interface as sold by Adafruit](https://github.com/PrzemoF/mtk3339)
* [Introduction to GPS Data: NMEA & RTCM](http://www.geodetic.gov.hk/smo/gsi/data/ppt/NMEAandRTCM.ppt)
* [GPS Chipset](http://wiki.openstreetmap.org/wiki/GPS_Chipset)
* [how I made a decent map with a GPS unit and Ubuntu Breezy GNU/Linux](http://cs.brown.edu/~dap/gps.htm)
* [Data On the Go](http://www.linux-magazine.com/Issues/2014/166/GPS-Tools)
* [NMEA data](http://www.gpsinformation.org/dale/nmea.htm#intro)
* [NMEA Decoder](http://freenmea.net/decoder)
* [Python library for parsing the NMEA 0183 protocol (GPS)](https://github.com/Knio/pynmea2)
* [NMEA GPS Library for Microcontrollers -2-](https://www.pocketmagic.net/nmea-gps-library-for-microcontrollers-2/)
* [Locating the Hard-to-Find Geospatial Answers](https://www.directionsmag.com/article/7637)

* [GPS Times, Atomic Clock Frequencies, and the Increasing Accuracy of GPS](https://www.allaboutcircuits.com/technical-articles/gps-times-atomic-clock-frequencies-increasing-accuracy-of-gps/)
* [Make a GPS Clock With Arduino](https://www.allaboutcircuits.com/projects/how-to-make-a-gps-clock-with-arduino/)

* [The xgps client](http://www.catb.org/gpsd/xgps-sample.html)
* [gps, xgps, xgpsspeed, cgps, lcdgps, gegps - test clients for gpsd](http://manpages.ubuntu.com/manpages/zesty/man1/gps.1.html)
* gpsd - https://github.com/biiont/gpsd
* gpsd - https://wiki.openstreetmap.org/wiki/Gpsd
* Detail documentation of gpsd - [gpsd — a GPS service daemon](http://www.catb.org/gpsd/)

* check this out for more information - https://learn.adafruit.com/adafruit-ultimate-gps/resources
    * Garmin GPS tutoral - http://www8.garmin.com/aboutGPS/
    * Trimble GPS Tutoral - http://www.trimble.com/gps_tutorial/

* [GPSBabel](https://www.gpsbabel.org/)
lets you convert proprietary data formats from a hundred or so different GPS receivers into `.GPX` files that are then easy to work with.
You can converts waypoints, tracks, and routes between popular GPS receivers such as Garmin or Magellan and mapping programs like Google Earth or Basecamp.
It also has powerful manipulation tools for such data. such as filtering duplicates points or simplifying tracks.
From there, [using 200 lines of Python](https://github.com/bunnie/watchmap) ([here](https://www.bunniestudios.com/blog/?p=5863)), you can plot the GPS data on a map and display it as a webpage.

* [nRF Cloud P-GPS](https://developer.nordicsemi.com/nRF_Connect_SDK/doc/latest/nrf/libraries/networking/nrf_cloud_pgps.html)
* [nRF Cloud](https://nrfcloud.com/#/)
* [Autonomous Drone Dodges Obstacles Without GPS](https://hackaday.com/2021/11/03/autonomous-drone-dodges-obstacles-without-gps/)
* [GPS Flight Modes](https://droneshopcanada.ca/blogs/drone-tips-and-tricks/124373447-dji-phantom-3-flight-modes)

# Antenna Improvements
* [NEW PI ZERO GAINS UNAPPROVED ANTENNAS YET AGAIN](https://hackaday.com/2021/12/13/new-pi-zero-gains-unapproved-antennas-yet-again/)
* [GNSS Antenna Splitter (Power Divider) with DC Pass - SPX-21223 - SparkFun Electronics](https://www.sparkfun.com/products/21223)

# Loko
* [Low Power Mode for Custom GPS Tracker](https://hackaday.com/2022/03/28/low-power-mode-for-custom-gps-tracker/)
* [Loko-the Tiniest GPS tracker with 270 days battery](https://hackaday.io/project/166619-loko-the-tiniest-gps-tracker-with-270-days-battery)

# DashCam
Combining the GPS location information onto a video stream

* [Making a DashCam Using the Raspberry Pi Zero (pt.1)](https://www.hackster.io/BnBe_Club/making-a-dashcam-using-the-raspberry-pi-zero-pt-1-9dd3ad)
* [How to Build a Raspberry Pi Body Camera](https://www.tomshardware.com/how-to/raspberry-pi-body-camera)
* [Building a Blockchain Police Bodycam PoC for $25](https://www.digitalmarketnews.com/building-a-blockchain-police-bodycam-poc-for-25/)
* [Building A Dashcam With The Raspberry Pi Zero W](https://www.linuxjournal.com/content/building-dashcam-raspberry-pi-zero-w)
* [DIY Dashcam: Build a Car Security Camera](https://www.technicallywizardry.com/diy-dashcam-raspberry-pi-zero-w-motion-eye/)

# logging
* [Use logzero for simple logging in Python](https://opensource.com/article/20/2/logzero-python)

# GPS Jamming and Spoofing
* [How to Fool a GPS](https://www.ted.com/talks/todd_humphreys_how_to_fool_a_gps?language=en)
* [GPS Jamming and Spoofing: When Good Signals Go Bad](https://www.directionsmag.com/article/8107)
* [Teardown: Mini GPS Jammer](https://hackaday.com/2020/09/08/teardown-mini-gps-jammer/)
* [Knowing Your Place: The Implications Of GPS Spoofing And Jamming](https://hackaday.com/2022/05/23/knowing-your-place-the-implications-of-gps-spoofing-and-jamming/)

# GPS-Tracker Using LoRa
* [Create Your Own GPS-Tracker Using LoRa](https://dzone.com/articles/create-your-own-gps-tracker-using-lora)
* [Wio terminal GPS](https://www.hackster.io/SeeedStudio/wio-terminal-gps-ad70e2)
* [LoRa GPS Tracker with Wio Terminal](https://www.hackster.io/idreams/lora-gps-tracker-with-wio-terminal-5d8647)



-----



# Investigate This For Ideas
* [unsurv offline - compact GNSS receiver with ESP32](https://www.crowdsupply.com/unsurv-technologies/unsurv-offline)
    * [step_counting](https://github.com/unsurv/unsurv-offline/tree/master/software/examples/step_counting)



I investigate here two GPS solutions for the Raspberry Pi:

* [Adafruit's Ultimate GPS][41] which uses the [MediaTek MTK3339 chipset][42]
* Sparkfun
* [Ozzmaker's BerryGPS-IMU V3][20] which uses the [uBlox CAM-M8][70]
but also has [IMU sensor LSM9DS1][68] and [Barometric Sensor BMP280][69]

| Features                        | MediaTek MTK3339 |   uBlox CAM-M8   |
|:--------------------------------|:----------------:|:----------------:|
| **Power Consumption**           |                  |                  |
|   Acquisition                   | 25 mW            |                  |
|   Tracking                      | 18 mW            |                  |
| **Current Consumption (@3.3V)** |                  |                  |
|   Acquisition                   | 25 mA            | 26 mA            |
|   Tracking                      | 20 mA            | 23 mA            |
| **Sensitivity**                 |                  |                  |
|   Acquisition (cold start)      | -148 dBm         | -148 dBm         |
|   Acquisition (hot start)       | -163 dBm         | -156 dBm         |
|   Tracking                      | -165 dBm         | -164 dBm         |


| Features                        | MediaTek MTK3339 |   uBlox CAM-M8   |
|:--------------------------------|:----------------:|:----------------:|

Sources:
* [MT3339 All-in-One GNSS Datasheet](https://d86o2zu8ugzlg.cloudfront.net/mediatek-craft/documents/mt3339/MT3339_Datasheet.pdf)
* [u-blox M8 Concurrent GNSS Antenna Modules](https://www.u-blox.com/sites/default/files/CAM-M8-FW3_DataSheet_%28UBX-15031574%29.pdf)

# BerryGPS First Fix
When you see most of the NMEA data is empty (repeated ',' present),
the GPS is trying to obtain a fix.
On first power up, it can take your GPS module awhile to get a fix.
It could be longer than 10 minutes in some situations,
it all depends on interference and if your GPS has clear access to the sky.
see https://ozzmaker.com/wp-content/uploads/2016/08/NMEA-data0.png

When you GPS has been up and running for awhile and has a fix,
all the GPS data is provided.
Also, if your GPS has a fix, you would also see green flashing LED in the middle of the BerryGPS board.
see https://ozzmak.com/wp-content/uploads/2016/08/NMEA-data1.png

# Other GPS / GNSS Modules
* [Gravity: GNSS Positioning Module - I2C&UART](https://www.dfrobot.com/product-2651.html?tracking=63da1e73804b0)
* [GPS Module,Navigation Satellite Positioning NEO-6M](https://www.amazon.com/dp/B0B31NRSD2)

# Data Logging
* [The Pythonic Guide To Logging](https://timber.io/blog/the-pythonic-guide-to-logging/)
* [logzero: Python logging made easy](https://logzero.readthedocs.io/en/latest/)
* [Use logzero for simple logging in Python](https://opensource.com/article/20/2/logzero-python)
* [OpenLog Data Logger](https://learn.sparkfun.com/tutorials/openlog-hookup-guide)

## Data Logging for NMEA Output
* [Using PySerial, PyNMEA2, and Raspberry Pi to log NMEA output](https://fishandwhistle.net/post/2016/using-pyserial-pynmea2-and-raspberry-pi-to-log-nmea-output/)

## Plotting
* [Python Data Science Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/)
* [Geographic Data with Basemap](https://jakevdp.github.io/PythonDataScienceHandbook/04.13-geographic-data-with-basemap.html)
* [OpenCPN Chart Plotter Navigation](https://opencpn.org/index.html)
* [How to Transform a Reference Frame in Python Using NumPy](https://python.plainenglish.io/reference-frame-transformations-in-python-with-numpy-and-matplotlib-6adeb901e0b0)

# Raspberry Pi Zero
* [Raspberry Pi Zero Guide: Projects, Specs, GPIO, Getting Started](https://www.tomshardware.com/features/raspberry-pi-zero)
* Adafruit LoRa Raspberry Pi Zero Bonnet - what about the LoRa version to support forwarding GPS / IMU data for pre-processing or post-processing
    * [Single Channel LoRaWAN Gateway for Raspberry Pi](https://learn.adafruit.com/raspberry-pi-single-channel-lorawan-gateway)
    * [Adafruit LoRa Radio Bonnet with OLED - RFM95W @ 915MHz - RadioFruit](https://www.adafruit.com/product/4074)
    * [SX1308 Raspberry Pi Zero LoRa Gateway Board](https://www.tindie.com/products/will123321/sx1308-raspberry-pi-zero-lora-gateway-board/)
    * [for case ideas, see this](https://learn.adafruit.com/raspberry-pi-wearable-time-lapse-camera/3d-printing)

## UPS for Raspberry Pi Zero
* [PiSugar S and PiSugar S Pro – Lower cost batteries for Raspberry Pi](https://www.cnx-software.com/2021/07/12/pisugar-s-and-pisugar-s-pro-lower-cost-batteries-for-raspberry-pi/)



----



# Background: Navigation Technologies
When GPS was first released to consumers,
it wasn’t even in the hands or understanding of most people.
It was used for pretty unique and esoteric stuff, with a simple GPS receivers.
They were pretty much just displayed current coordinates including latitude, longitude, and altitude - not much else.
These old units are big, heavy, slow, and use a ton of power for what they do.
Modern GPS units are light, small, cheap, and use very little power.

* [Navigation: Maryland School of Sailing](https://www.youtube.com/playlist?list=PLDjZqs-Y1cMyCX3cZ5FfkXdyhywllJeJw)

* [An introduction to inertial navigation](https://www.cl.cam.ac.uk/techreports/UCAM-CL-TR-696.pdf)
* [Quantum Atomic Interferometer For Precision Motion Sensing](https://hackaday.com/2021/12/28/quantum-atomic-interferometer-for-precision-motion-sensing/)

* [A Brief History of GPS](https://aerospace.org/article/brief-history-gps)
* [The central place of GPS in our lives](https://plus.maths.org/content/recognising-place-gps-has-our-lives?nl=0)
* [How Etak Paved the Way to Personal Navigation](https://hackaday.com/2018/06/29/how-etak-paved-the-way-to-personal-navigation/)
* [An Introduction to GNSS](https://www.novatel.com/an-introduction-to-gnss/chapter-1-gnss-overview/)
* [GPS vs GNSS](https://www.sparkfun.com/news/4276)
* [Understanding GNSS Orbits](https://www.sparkfun.com/news/4278)
* [New-Age Satellite-Based Navigation STAN: Simultaneous Tracking and Navigation with LEO Satellite Signals](https://insidegnss.com/new-age-satellite-based-navigation-stan-simultaneous-tracking-and-navigation-with-leo-satellite-signals/)
* [Tracking The Satellites That Keep Us On Track; Monitoring GPS, Galileo, BeiDou, And GLONASS](https://hackaday.com/2019/09/24/tracking-the-satellites-that-keep-us-on-track-monitoring-gps-galileo-beidou-and-glonass/)
* [Not Just GPS: New Options For Global Positioning](https://hackaday.com/2020/07/07/not-just-gps-new-options-for-global-positioning/)
* [Coarse Materials: GPS and GNSS for Geospatial Professionals](https://www.e-education.psu.edu/geog862/home.html)

* [Can Maths Tell Us Where We Are?](https://www.youtube.com/watch?v=XJlVPlvkzdk)
* [SPECIAL TOPICS 2 - GPS](https://www.youtube.com/watch?v=16xHIBmul_o&list=PLX2gX-ftPVXXGdn_8m2HCIJS7CfKMCwol)

##  Maps & Coordinate Systems
* [Latitude, Longitude and Coordinate System Grids](https://gisgeography.com/latitude-longitude-coordinates/)
* [Marble](https://marble.kde.org/index.php)

## Time and Navigation
* [Time and Navigation](https://timeandnavigation.si.edu/)

## Dead Reckoning (DR)
Dead Reckoning is the process of determining current position by
combining previously determined positional data with speed and heading.
This process can also be applied to determine future positions as well.

You can calculates speed and heading through the use of an internal inertial measurement unit (IMU).
The addition of an wheel ticks
and IMU allows higher precision and more accurate readings in between GNSS data refreshes.

* [What is Dead Reckoning (DR)?](http://www.furuno.com/en/gnss/technical/tec_dead)
* [The GENIUS of Inertial Navigation Systems Explained](https://www.youtube.com/watch?v=Pq_PDaYclAw)
* [LN-3 inertial navigation system](https://en.wikipedia.org/wiki/LN-3_inertial_navigation_system)
* [SparkFun GPS-RTK Dead Reckoning ZED-F9R Hookup Guide](https://learn.sparkfun.com/tutorials/sparkfun-gps-rtk-dead-reckoning-zed-f9r-hookup-guide)
* [Basics of 6DOF and 9DOF sensor fusion](https://www.embeddedcomputing.com/technology/analog-and-power/basics-of-6dof-and-9dof-sensor-fusion)
* [ESP32 precision GPS receiver (incl. RTK-GPS Tutorial). How to earn money with it (DePIN)](https://www.youtube.com/watch?v=Oc1LBFDj2MA)

## Space Navigation
* [Star Trackers: Telling Up From Down In Any Space](https://hackaday.com/2020/04/02/star-trackers-telling-up-from-down-in-any-space/)

# Where Am I?
* [The Longitude Problem - Improving Navigation with the Harrison Clocks](https://www.youtube.com/watch?v=zlRxWJ_kGEA)

## Direction Finding
* [Where’s That Radio? A Brief History Of Direction Finding](https://hackaday.com/2021/08/19/wheres-that-radio-a-brief-history-of-direction-finding/)

# Decoding GPS Signals
* [Number Crunching GPS For The DIYer](https://hackaday.com/2020/07/02/number-crunching-gps-for-the-diyer/)

## Search and Rescue Satellite Aided Tracking (SARSAT)
* [The Voice of GPS](https://hackaday.com/2023/06/23/the-voice-of-gps/)
* [Receiving voice transmissions from GPS satellites || Satellite reception pt.10](https://www.youtube.com/watch?v=U_pCHTeamn8)

## Automatic Identification System (AIS)
## Automatic Transmitter Identification System (ATIS)
* https://en.wikipedia.org/wiki/Automatic_identification_system
* https://en.wikipedia.org/wiki/Automatic_Transmitter_Identification_System_(marine)



-----



# Global Navigation Satellite Systems (GNSS)
Global Navigation Satellite Systems (GNSS) is the acronym that encompasses
those systems that allow users to compute their position based on
signals transmitted by satellites, world-wide.
The obvious example is GPS,
but this term also includes other systems such as
Russia's [GLONASS][61], Eroupean Union's [Galileo][62], China's [BeiDou][63], India's [IRNSS/NavIC][91], and Japans [QZSS][92].

GPS provides positioning of an object to the earth.
It uses timely signals generated by satellites revolving around the earth.
GPS includes a constellation of 24 satellites and extra for backup purpose.
Four satellites are used for getting the precise position, this process is known as [trilateration][37].

GPS technology uses standalone receivers, where the location is directly calculated. This technique is prone to errors such as uncorrected satellite clock errors, orbital parameter satellite error, ionospheric and tropospheric delays, multipath errors, geometric errors and datum selection errors. To reduce these errors new technologies are evolved. GPS can gain nominal accuracy of 10-15 meters.

## Global Positioning System (GPS) Background Information
The Global Positioning System (GPS) is a satellite-based radio navigation system
started by the Department of Defense in 1973 and is operated today by the United States Space Force.
GPS is available for free to anybody with a device that can receive transmissions from the many GPS satellites.
GPS allows users to accurately determine the location of objects on or above the surface of the Earth.
Most GPS receivers transmit [National Marine Electronics Association (NMEA)][60]
sentences that provide information that includes latitude and longitude,
altitude, time, bearing, speed, and a great many other variables at 9600 baud.

Low cost, consumer grade GPS devices often have an accuracy of about five to 10 meters (~30 ft.),
so it’s not really useful for determining the distance between objects in close proximity.
Expensive industrial systems have an accuracy range measured in centimeters.
But, if you want to know where on the planet you are in a general sense,
(for example, maritime navigation or monitoring the movement of buses around a city’s streets)
a low cost, consumer grade GPS device is well suited to such a purpose.

GPS data has its roots in military and defense activities such as ensuring missile accuracy.
Over time, as the military adopted other technologies,
GPS was repurposed for civilian uses typically associated with surveying and map cartography.
In general, GPS data describes a device’s location in terms of longitude, latitude, altitude,
and the time that the transmission was received.
GPS data is transmitted in a variety of formats,
but essentially the information reports where and when you are on the planet.

### GPS Data Format
location data is received by a listening GPS device from a GPS satellite as radio waves.
The GPS listening device converts the binary stream into lines of text.
Each line is comma-delimited to identify unique data items.
In GPS parlance, a delimited line is called a sentence and some examples are below:

```
$GPRMC,044840.00,A,3401.21044,N,11824.67722,W,0.165,,010621,,,D*60
$GPVTG,,T,,M,0.165,N,0.306,K,D*21
$GPGGA,044840.00,3401.21044,N,11824.67722,W,2,07,1.34,29.5,M,-32.9,M,,0000*56
$GPGSA,A,3,21,32,46,27,08,22,10,,,,,,3.07,1.34,2.76*0F
$GPGSV,3,1,12,01,18,319,17,08,27,257,20,10,44,068,33,18,00,142,*73
$GPGSV,3,2,12,21,39,313,23,22,20,296,14,23,16,089,,27,22,221,32*7A
$GPGSV,3,3,12,31,28,168,20,32,70,025,31,46,49,199,30,51,49,161,*7E
$GPGLL,3401.21044,N,11824.67722,W,044840.00,A,D*7F
```

There are 60 different formats for GPS sentences.
However, today only a handful of them are in general use.
The more common GPS sentence formats are:

* [GPGGA][80]: Global positioning system fix data (time, position, fix type data)
* [GPGLL][81]: Geographic position, latitude, longitude
* [GPVTG][82]: Course and speed information relative to the ground
* [GPRMC][83]: Time, date, position, course, and speed data
* [GPGSA][84]: GPS receiver operating mode, satellites used in the position solution, and DOP values.
* [GPGSV][85]: The number of GPS satellites in view, satellite ID numbers, elevation, azimuth, and SNR values.

### Beware of Data Format Misinterpretation
When it comes to GPS, there are a few formats for reporting latitude and longitude.
The difference in the formats will affect how you process incoming data.
Maritime navigation typically uses earth location expressed in degrees / minutes /seconds.
Fore example:

* Latitude of 38° 52' 44.941" N is 38 degrees, 52 minutes, 44.941 seconds, North
* Longitude of 76° 58' 54.521" W is 76 degrees, 58 minutes, 54.521 seconds, West

Over time a decimal format became more prevalent, and the above example becomes:

* Latitude 38.879150390625
* Longitude -76.9818115234375

When a location is North of the equator,
it has a positive number for its location; South has a negative value.
When a location is East of the prime meridian in Greenwich, England, it has a positive number.
Locations West of the prime meridian have a negative number.

The lat & long of GPS sentance is in a `ddmm.mmmm` and `dddmm.mmmm` formats
In the `ddmm.mmmm` and `dddmm.mmmm` formats the `dd` and `ddd` digits indicate degrees.
The `mm.mmmm` digits indicate the minute and fraction of a minute.
You need to be very careful in making the conversions
and its best to use the standard conversion libraries provied by Python and other languages.

## What is GPS NMEA Data?
[NMEA is a standard data format][34] supported by all GPS manufacturers,
much like ASCII is the standard for digital computer characters in the computer world.
NMEA stands for National Marine Electronics Association,
and in addition to GPS receivers, it’s also used by
[echo sounder][86], [sonar][87], [anemometer][88], [gyrocompass][89], and [autopilot][90] devices.

NMEA sentences are basically comma-delimited sentences that convey
various essential information for accurately obtaining the location of the system.
The purpose of NMEA is to give equipment users the ability to mix and match hardware and software.
NMEA-formatted GPS data also makes life easier for software developers
so they can write software for a wide variety of GPS receivers
instead of having to write a custom interface for each GPS receiver.

But like so many standards,
NMEA is confusing since there are many NMEA messages, not just one.
Different kinds of GPS receivers with different capabilities will have
different types of NMEA messages with different capabilities.
And there is no physical or data link layer standard for NMEA.
NMEA data can be transmitted via different types of communications interfaces
such as RS-232, USB, Bluetooth, WiFi, UHF, and many others.

For details on the NMEA message structure, check out the articles:

* [NMEA Sentence Decoding](http://www.shantek.net/gps/NMEA_SentenceDecoding.html)
* [GPS - NMEA sentence information](http://aprs.gids.nl/nmea/)
* [What Exactly Is GPS NMEA Data?][34]
* [An architect's guide to GPS and GPS data formats](https://www.redhat.com/architect/architects-guide-gps-and-gps-data-formats)
* [NMEA Solution Output Format](https://anavs.com/knowledgebase/nmea-format/)
* [NMEA data](http://www.gpsinformation.org/dale/nmea.htm#PGRMM)
* [Online NEMA tools](http://freenmea.net/)
* [NMEA 0183 Interface Standard](https://www.nmea.org/content/STANDARDS/NMEA_0183_Standard)
* [NMEA 0183](https://en.wikipedia.org/wiki/NMEA_0183)
* [NMEA 2000](https://en.wikipedia.org/wiki/NMEA_2000)

The raw GPS data being produced are called [NMEA sentences][48].
You'll notice there are a few different kinds of NMEA sentences,
but the most common are
([NMEA Reference Manual][57] or [MTK3339 Data Sheet][42] or [GeoS NMEA Data Protocol v3.0][65]):

* [$GPRMC - Recommended minimum specific GPS/Transit data][49]
* [$GPGGA - Global Positioning System Fix Data][50]
* [$GPVTG - Track made good and ground speed][51]
* [$GPGSA - GPS DOP and active satellites][52]
* [$GPGSV - GPS Satellites in view][53]
* [$GPZDA - Date & Time (UTC, day, month, year, and local time zone)][59]

> **NOTE:** NMEA is the abbreviation for the [National Marine Electronics Association][55].
>They develop specification that defines the interface between various pieces of marine electronic equipment.
>[NMEA sets the standards for data format supported by all GPS manufacturers][56].

## Language of GPS
Grid Square - http://www.gatorradio.org/Operating_Training_Aides/Ham_US_Grids%202005.pdf

## Using Starlink Network
* [GPS? With Starlink, We Don’t Need It Any More!](https://hackaday.com/2021/10/10/gps-with-starlink-we-dont-need-it-any-more/)

## What are GPS L1, L2, and L5 Frequencies?
Global Positioning System (GPS) satellites circle the Earth twice a day in very precise orbits. They continuously transmit signals that allow GPS receivers on the ground to calculate their location, speed, and direction.

GPS first began operations with two signals, L1 and L2. L1 operates at a frequency of 1575.42 MHz, whereas L2 operates at a frequency of 1227.60 MHz. These GPS signals include two ranging codes: P (Y) or Precision code and C/A (Carrier Acquisition) code. The first code is only for civilian usage, while the second is only for military use. These ranges codes are used to calculate the distance to the satellite as well as to uniquely identify the navigation message.

Although the GPS system has nearly reached its full operational capabilities, modernization and implementation of a new GPS system have recently begun due to increased demand for better service and technological improvements. The insertion of L5 GPS signals is part of the US Department of Defense’s modernization activities.

Now there are three civilian GPS frequencies: L1 at 1575.42 MHz, L2 at 1227.60 MHz, and L5 at 1176.45 MHz. Each frequency has unique properties that make it better suited for certain types of applications. For example, L1 frequency is used to track GPS satellite location, L2 frequency is used to track the health of the GPS satellites and the L5 frequency is used to improve accuracy for civilian use such as aircraft precision approach guidance.

* [Everything You Need To Know About GPS L1, L2, and L5 Frequencies](https://gisresources.com/everything-you-need-to-know-about-gps-l1-l2-and-l5-frequencies/)
* [A Pure L5 Mobile Receiver](https://insidegnss.com/a-pure-l5-mobile-receiver/)

## What is Virtual Reference Station (VSR)?
* [What is Virtual Reference Station?](https://gisresources.com/what-is-virtual-reference-station/)
* [How VSR Works?](https://gisresources.com/how-vrs-work/)
* [Challenges and Benefits of VRS](https://gisresources.com/challenges-and-benefits-of-vrs/)
* [Errors can be Reduced in VRS](https://gisresources.com/errors-can-be-reduced-in-vrs_page-virtual-reference-station/)



-----



# Choosing GPS Technology
* [How To Choose The Right GPS Module For Your Project](https://hackaday.com/2020/08/14/how-to-choose-the-right-gps-module-for-your-project/)
* [Number Crunching GPS For The DIYer](https://hackaday.com/2020/07/02/number-crunching-gps-for-the-diyer/)


## GPS Technology
* [Hackaday Dictionary: The Global Positioning System (GPS)](https://hackaday.com/2015/11/12/hackaday-dictionary-the-global-positioning-system-gps/)
* [GPS for Dummies](https://books.google.com/books?id=Hbz4LYIrvuMC&pg=PA62&lpg=PA62&dq=comparison+of+gps+chips&source=bl&ots=HFGMKxCAOV&sig=C3wryIscPn01Nair4wJXMaKyEds&hl=en&sa=X&ved=0ahUKEwiSsZDgv57VAhXLej4KHenWBN44FBDoAQgzMAM#v=onepage&q=comparison%20of%20gps%20chips&f=false)
* [Adding GPS to Your Electronic Product (and How to Scale Up)](http://makezine.com/2016/07/06/adding-gps-to-your-electronic-product-and-how-to-scale-up/)
* [GPS Buying Guide](https://www.sparkfun.com/pages/GPS_Guide)
* [Do Chipset Channels Matter?](http://www.gpsreview.net/gps-chipset-channels/)
* http://www.furuno.com/en/gnss/technical/
* [GPS Visualizer's coordinate calculators & distance tools](http://www.gpsvisualizer.com/calculators)

## GPS Assisatance
### P-GPS Mode
Predicted GPS (P-GPS) is a form of assistance that reduces the Time to First Fix (TTFF), the time needed by a GNSS module to estimate its position.
A form of assistance provided to devices trying to obtain a Global Navigation Satellite System (GNSS) fix, where the device can download up to two weeks of predicted satellite Ephemerides data. It enables devices to determine the exact orbital location of the satellite without connecting to the network every two hours with a trade-off of reduced accuracy of the calculated position over time. It is available through nRF Cloud.

### AGPS
* [A-GPS vs. GPS](http://www.diffen.com/difference/A-GPS_vs_GPS)

## GNSS Correction
Unaided, GNSS-based positioning is subject to a variety of errors
that limit achievable accuracies to several meters.
These errors are caused primarily by

* satellite clock drift
* slight deviations from the predicted orbits
* signal delays incurred in the charged ionosphere and the troposphere

GNSS correction services use a variety of techniques, delivery mechanisms, and core technologies
to overcome these errors and achieve decimeter or even centimeter-level positioning accuracy.

* [What is Correction Data?](https://www.sparkfun.com/news/7138)
* [PPP-RTK GNSS correction services (PointPerfect)](https://www.u-blox.com/en/technologies/ppp-rtk-gnss-correction-services-pointperfect)
* [u-blox using a Raspberry Pi to improve GNSS positioning services](https://blog.adafruit.com/2024/01/16/u-blox-using-a-raspberry-pi-to-improve-gnss-positioning-services/)
* [Precise Point Positioning (PPP)](https://www.novatel.com/an-introduction-to-gnss/chapter-5-resolving-errors/precise-point-positioning-ppp/)

### GNSS + INS (Inertial Navigation System)
GNSS/INS is the use of GNSS satellite signals to correct or calibrate a solution from an inertial navigation system (INS).
The GPS gives an absolute drift-free position value that can be used to reset the INS solution or can be blended with it by use of a mathematical algorithm, such as a Kalman filter. The angular orientation of the unit can be inferred from the series of position updates from the GPS. The change in the error in position relative to the GPS can be used to estimate the unknown angle error.

The benefits of using GPS with an INS are that the INS may be calibrated by the GPS signals and that the INS can provide position and angle updates at a quicker rate than GPS. For high dynamic vehicles, such as missiles and aircraft, INS fills in the gaps between GPS positions. Additionally, GPS may lose its signal and the INS can continue to compute the position and angle during the period of lost GPS signal. The two systems are complementary and are often employed together.

### Real-Time Kinematic (RTK) GNSS Correction Services
Conventional Real-Time Kinematic (RTK) GNSS correction services
determine the magnitude of the GNSS errors by observing the satellite signals
from one or several fixed reference points called GNSS base stations.
They then use IP-based communication to transfer the lump sum of all observed errors,
to the end user called the GNSS rover.

RTK-based solutions require two-way communication between the GNSS receiver
and the GNSS correction service provider and achieve centimeter-level positioning accuracy in ten to twenty seconds.
Also, the GNSS rover must remain within a roughly 30 kilometer radius from the nearest base station.

### Precise Point Positioning (PPP) GNSS Correction Services
PPP is a positioning technique that removes or models GNSS system errors,
that remains valid across vast geographical expanses,
to provide a high level of position accuracy from a single receiver.
A PPP solution depends on GNSS satellite clock and orbit corrections,
generated from a network of global reference stations.
Once the corrections are calculated, they are delivered to the end user via satellite or over the Internet.
These corrections are used by the receiver,
resulting in decimetre-level or better positioning with no base station required.

Because it only requires unidirectional communication (IP-based or via satellite L-band),
the service can be delivered to any number of users.
Conventional PPP high precision positioning can take three minutes to half an hour
to deliver a position estimate with below 10 centimeter accuracy,
making it a viable solution for static applications, such as surveying,
but a poor fit for more dynamic ones, such as drones, micromobility, precision agriculture, and others.

### State Space Representation (SSR) / PPP-RTK GNSS Correction Services
Network based correction methods (GPS-RTK and GPS-PPP)
can provide GPS fixes to centimeter level accuracy under ideal conditions.
However, these solutions are very sensitive to the environment — such as bridges, trees, and buildings.
The triditional / well established way to overcome this challenge
and improve precision GPS reliability is to use high-accuracy IMU aiding at a low-level in the position solution.

In recent years, these established approaches to determining GNSS corrections
have been combined into PPP-RTK GNSS corrections services
(sometimes also referred to as state space representation (SSR) correction services)
that deliver the best of both worlds:
combining accuracy close to that of RTK and quick initialization times with the broadcast nature of PPP.

Like PPP-based solutions, PPP-RTK GBSS rely on a model of GNSS errors with broad geographical validity
and broadcast the different GNSS error components (or states) using one-way communication.
The GNSS receivers then compute the GNSS corrections for their specific location.
Additional statistical information can further support the algorithms used by the GNSS receiver L5 channel.

The benefits are:

* PPP-RTK-enabled GNSS receivers can deliver centimeter-level positioning within seconds
* A single GNSS correction data stream can be concurrently broadcast to any number of GNSS receivers
* Redundant IP and satellite-based communications increase the reliability and availability of the service
* Continental coverage enables a seamless positioning experience

### Differential Global Positioning Systems (DGPS)
[DGPS (Differential GPS)][35] is essentially a system to provide positional corrections to GPS signals.
DGPS is designed to be more accurate than GPS.
DGPS are enhancements to the GPS which provide improved location accuracy,
in the range of operations of each system,
from the 15-meter nominal GPS accuracy to about 10 cm in case of the best implementations.
DGPS uses a fixed, known position to adjust real time GPS signals to eliminate [pseudorange errors][36].
The stationary GPS receiver needs to be with 100km of the roving GPS receiver.
DGPS corrections improve the accuracy of position data only.
DGPS has no effect on results that are based on speed data.
DGPS accuracy will be effected by the distance between the transmitter & rover,
and ionosphere, troposphere and multipath conditions.

* [How Does DGPS (Differential GPS) Work?](https://racelogic.support/01VBOX_Automotive/01General_Information/Knowledge_Base/How_Does_DGPS_(Differential_GPS)_Work%3F)
* [Difference Between GPS and DGPS](https://techdifferences.com/difference-between-gps-and-dgps.html)
* [How Not To Build Your Own DGPS Base Station](https://hackaday.com/2018/03/30/fail-of-the-week-how-not-to-build-your-own-dgps-base-station/)
* [Differential GPS Explained](https://www.esri.com/news/arcuser/0103/differential1of2.html)

## DGNSS
Differential Global Navigation Satellite System (DGNSS),
is an enhancement to GNSS that was developed to correct these errors and inaccuracies in the GNSS system,
allowing for more accurate positioning information.
The advantage of DGNSS is that it is useful over a longer baseline
(distance between a base station and rover receivers), and a DGNSS is less expensive.
The technology required to achieve the higher accuracy of RTK performance
makes the cost of an RTK-capable receiver higher than one that is DGNSS-capable only.

## GPS-PPK / Post Processing Kinematic (PPK)
Post-Processed Kinetic (PPK) can be used with a traditional, non-RTK GPS chip
and perfrom the after the positioning data has been collected.

* [PPK Or RTK – Which is best?](https://coptrz.com/ppk-or-rtk-which-is-best/)

## GPS-RTK
Real Time Kinematic (RTK)

An excellent hands on introduction to GPS-RTK is [RTK Overview](http://rtkexplorer.com/rtk-overview/)
including the software tools [RTKLIB](https://www.rtklib.com/) and [RTKNAVI](https://rtknavi.com/).

* [How RTK works](https://www.youtube.com/watch?v=ieearzWTCZw)
* [Different Methods of Setting up the RTK Base](https://www.youtube.com/watch?v=p7L-3E-OM-c)
* [WHAT IS NTRIP?](https://www.agsgis.com/What-is-NTRIP_b_42.html)
* [Real-Time Kinematic (RTK)](https://www.novatel.com/an-introduction-to-gnss/chapter-5-resolving-errors/real-time-kinematic-rtk/)
* [SparkFun GPS-RTK2 Board](https://www.sparkfun.com/products/15136)
* [SparkFun GPS-RTK Board - NEO-M8P-2](https://www.sparkfun.com/products/15005)
    * [What is GPS RTK?](https://learn.sparkfun.com/tutorials/what-is-gps-rtk)
    * [GPS-RTK Hookup Guide](https://learn.sparkfun.com/tutorials/gps-rtk-hookup-guide)
* [EYE ON NPI - u-blox C099-F9P Application Board for ZED-F9P GNSS RTK Module](https://www.youtube.com/watch?v=RXyBcWh85DM)
* [SparkFun GPS-RTK Dead Reckoning ZED-F9R Hookup Guide](https://learn.sparkfun.com/tutorials/sparkfun-gps-rtk-dead-reckoning-zed-f9r-hookup-guide)
* [Crowd Supply: RTK Rover](https://www.crowdsupply.com/hyfix/rtk-rover)


### Networked Transport of RTCM via Internet Protocol (NTRIP)
Networked Transport of RTCM via Internet Protocol (NTRIP)
is a protocol used for streaming corrections over the Internet from a base station to a rover to achieve cm-level accuracy.

The Radio Technical Commission for Maritime Services (RTCM) is an international non-profit scientific, professional and educational organization.
Of particular interest is Special Committee (SC) 104 on Differential Global Navigation Satellite Systems (DGNSS) which defines the transmission standard for the correction information which is used by the various VERIPOS services. The standard typically used by the service providers in the offshore industry is 'RTCM recommended Standards for Differential GNSS Service (RTCM Paper 136-2001/SC104-STD)'.

RTCM (aka RTCM SC-104) is a communication protocol for sending differential GPS (DGPS) to a GPS receiver from a secondary source like a radio receiver. The standard is named for the Special Committee 104 (SC 104) of the [Radio Technical Commission for Maritime Services (RTCM)][73] that created it.

* Reference for Global Navigation Satellite Systems: [Navipedia](https://gssc.esa.int/navipedia/index.php?title=Main_Page)
* [RTK Standards](https://gssc.esa.int/navipedia/index.php/RTK_Standards)

* [What is NTRIP](https://support.pix4d.com/hc/en-us/articles/4633640503709-What-is-NTRIP)
* [What Is NTRIP and How to Use It for RTK with Reach](https://blog.emlid.com/what-is-ntrip-and-how-to-use-it-for-rtk-with-reach/)
* [Common issues with using NTRIP for differential corrections](https://support.oxts.com/hc/en-us/articles/360012992679-Common-issues-with-using-NTRIP-for-differential-corrections)

### The Correction Signal
RTCM SC-104 is a standard that defines the data structure for differential correction information for a variety of differential correction applications. It was developed by the Radio Technical Commission for Maritime Services (RTCM) and has become an industry standard for communication of correction information.

* https://www.e-education.psu.edu/geog862/node/1838

### SNIP
SNIP is a Networked Transport of RTCM via Internet Protocol (NTRIP) Caster application
that combines user-friendly software with an active data-pushing feature to bring you all the benefits of NTRIP technology.

* [SNIP](https://www.use-snip.com/)

Many of the various low cost L1-only uBlox chips, including the 6T and 8 series (as well as the latest F9P)
can be used for traditional RTK navigation and positioning.

*[Using RTCM2 with uBlox GNSS](https://www.use-snip.com/kb/knowledge-base/using-rtcm2-with-ublox-gnss/)

## Real-Time Kinematic vs. Differential GPS
* [Real-Time Kinematic and Differential GPS](https://www.e-education.psu.edu/geog862/node/1828)


## Pulse Per Second (PPS) Signal from the GPS
A pulse per second (PPS or 1PPS) is an electrical signal that has a width of less than one second and a sharply rising or abruptly falling edge that accurately repeats once per second. PPS signals are output by radio beacons, frequency standards, other types of precision oscillators and some GPS receivers.

* [Why do GPS receivers have a 1 PPS output?](https://electronics.stackexchange.com/questions/30750/why-do-gps-receivers-have-a-1-pps-output)
* [Add GPS Time and Location to a Raspberry Pi Project](https://www.rs-online.com/designspark/add-gps-time-and-location-to-a-raspberry-pi-project)
* [PPS (Pulse per Second) ...simple as that!](https://www.linkedin.com/pulse/pps-pulse-per-second-simple-deepak-kaira/)
* [What’s More Accurate than a GPS Clock? The OpenPPS GPS Clock](https://hackaday.com/2019/05/11/whats-more-accurate-than-a-gps-clock-the-openppc-gps-clock/)
    * [OpenPPS](http://www.rocketmanrc.com/openpps.html)

### Ground Control Points (GCP)
Ground Control Points (GCPs) are defined as points on the surface of the earth of known location used to geo-reference Landsat Level-1 data. GCPs are updated as needed to continually improve Landsat data. GCPs can be downloaded and used as reference data.

* [Ground Control Points](https://www.usgs.gov/landsat-missions/ground-control-points)
## GPS Time Coordinate System
The [World Geodetic System 1984][38] [(WGS84)][67]
(also known as WGS 1984, EPSG:4326)
is comprised of a terrestrial reference coordinate system, a geodetic datum
([Horizontal Datum][71] + [Vertical Datum][72]), and a [ellipsoid modeling the earth][58].

WGS84 is comprises of a reference [ellipsoid modeling the earth][58],
a standard coordinate system, altitude data and a [geoid][39].
It uses the Earth’s center of mass as the coordinate origin.
[Geodesists][40] believe the error is less than 2 centimeters

## Magnetic North vs Geographic (True) North
* [Magnetic North vs Geographic (True) North Pole](https://gisgeography.com/magnetic-north-vs-geographic-true-pole/)

## GPS Position Accuracy
[Dilution of precision](https://en.wikipedia.org/wiki/Dilution_of_precision_(navigation))
is a term used in GPS navigation to specify the error
in positional measurement precision resulting from sub-optimal satellite geometry.

* [GPS Position accuracy and how to tell if you have a good fix?](https://ozzmaker.com/gps-position-accuracy-and-how-to-tell-if-you-have-a-good-fix/)

## Python Libraries for GIS and Mapping
* [Python Libraries for GIS and Mapping](https://gisgeography.com/python-libraries-gis-mapping/)
* [Python3 GPS Client Tools](https://confluence.clazzes.org/display/PYTOOLS/Python3+GPS+Client+Tools)
* [The Heat Of The Moments – Location Visualization In Python](https://hackaday.com/2019/12/05/the-heat-of-the-moments-location-visualization-in-python/)
* [WebGIS Development in 2023: A Guide to the Tools and Technologies I Use for Building Advanced Geospatial Applications](https://medium.com/@ramizsami/webgis-development-in-2023-a-guide-to-the-tools-and-technologies-i-use-for-building-advanced-9bd3277b10dd)

## GNSS-SDR
[GNSS-SDR][64] is and open source Global Navigation Satellite Systems software-defined receiver.

## VBOX Automotive
VBOX is a data acquisition systems by RACELOGIC used for measuring the speed and position of a moving vehicle.
VBOX data loggers can record high accuracy GPS speed measurements, distance, acceleration,
braking distance, heading, slip angle, lap times, position, cornering forces and more.

* [VBOX 3i | 100Hz Data Logger](https://www.vboxautomotive.co.uk/index.php/en/products/data-loggers/vbox-3i)
* [Racelogic](https://racelogic.support/)



----



# Sensor Fusion
* [Understanding Sensor Fusion and Tracking](https://www.youtube.com/playlist?list=PLn8PRpmsu08ryYoBpEKzoMOveSTyS-h4a)
* [Understanding Kalman Filters](https://www.mathworks.com/videos/series/understanding-kalman-filters.html)
* [Control Engineering](https://engineeringmedia.com/)
* [The Educational Resource Compendium](https://resourcium.org/)
* [Control Systems Lectures](https://www.youtube.com/channel/UCq0imsn84ShAe9PBOFnoIrg)
    * [and more](https://engineeringmedia.com/videos)
* [SPECIAL TOPICS 1 - THE KALMAN FILTER](https://www.youtube.com/watch?v=CaCcOwJPytQ&list=PLX2gX-ftPVXU3oUFNATxGXY90AULiqnWT)



----



# GPS Data Formats
* [The Ultimate List of GIS Formats and Geospatial File Extensions](https://gisgeography.com/gis-formats/)
* [Vector vs Raster: What’s the Difference Between GIS Spatial Data Types?](https://gisgeography.com/spatial-data-types-vector-raster/)

## GPX File Format
A GPX file is a GPS data file saved in the GPS Exchange format,
which is an open standard XML format that can be freely used by GPS programs.
It contains longitude and latitude location data that may include
waypoints, routes, and tracks.

GPX files can be used by a variety of applications including Google Earth, GPSRouteX, and GPX Viewer.
GPX files store three types of data:

* Waypoint - Includes GPS coordinates of a point. It may also include other descriptive information.
* Route - Includes a list of track points, which are waypoints for turn or stage points, that lead to a destination.
* Track - Includes a list of points that describe a path.

## SPARTN Data Format
The Secure Position Augmentation for Real-Time Navigation (SPARTN) format is an industry-driven standard for communication of
GNSS high accuracy correction data between service providers and end users.

* [SPARTN](https://www.spartnformat.org/)


----


# u-blox Products
ZED-F9 is a family of multi-band GPS-RTK recievers, covering all four GNSS constellations (GPS, GLONASSS, Galileo, BeiDou),
achieving centimeter accuracy with low energy consumption.
These devices use u-blox's PointPerfect GNSS cloud-based correction data and derived from a local RTK base station or NTRIP remote base station.
These devices also support L5 multi-band

multi-GNSS systems can access more than one range of frequencies from a single constellation or different constellations.
multi-band GPS systems and can provide much greater stability and improved accuracy for both standard and autonomous navigation.

RTK technology has enabled precise, centimeter-level accuracy for GPS positioning.
It works by utilizing a ground-based, fixed, and pre-surveyed sensor to send corrections to the rover system.
This is a bit like setting your hand on something stable to get your bearings after spinning around a few turns.
An issue with RTK is the “fix” time a single band RTK system takes.
This means the device will need to wait for 1, 2, or even 5+ minutes sometimes
for the device to catch enough signal from the GPS constellation in order to
have enough usable data to start the vehicle.
That’s far too long for many people and applications.
The single-band receiver can only detect information on the L1 frequency
which significantly limits the speed these devices can get a fix on the precise location
and may affect the accuracy of the information.
By contrast, multi-GNSS systems can process several different frequency bands,
which can reduce RTK initialization and fix solutions to a considerable degree,
typical within a few seconds.

ZED-F9P Module
* ZED-F9P-02B: u-blox F9 high precision GNSS module with Satellite Based Augmentation System (SBAS) - $200 for unit 1 at DigiKey
* ZED-F9P-04B: u-blox high precision GNSS module with Secure Position Augmentation for Real Time Navigation (SPARTN) and Centimetre-level Augmentation Services (CLAS) for Japan - $200 for unit 1 at DigiKey
* ZED-F9P-15B: u-blox high precision GNSS module with L1/L5 (aka Multi-Band GNSS) - $129 for unit 1 at DigiKey
    * https://gisresources.com/everything-you-need-to-know-about-gps-l1-l2-and-l5-frequencies/
    * https://www.u-blox.com/en/press-releases/u-blox-announces-first-timing-solutions-based-l1-and-l5-gnss-signals
* [ZED-F9P Use Cases](https://www.sparkfun.com/rtk)


* [A first look at the u-blox ZED-F9P dual frequency receiver](https://rtklibexplorer.wordpress.com/2018/11/30/a-first-look-at-the-u-blox-zed-f9p-dual-frequency-receiver/)
* [u-blox Precise Positioning](https://www.youtube.com/watch?v=NalwVqdcENk)
* [ZED-F9P Module](https://www.u-blox.com/en/product/zed-f9p-module)
* [SparkFun GNSS Combo Breakout](https://www.sparkfun.com/products/22560)



----



# Raspberry Pi Zero Setup
I have set up all my Raspberry Pi's as [headless devices][01].
For one thing, I want to SSH into my devices so I don't want
or need a monitor/keyboard.
The real trick on going headless is doing the initial setup of the device
without an HDMI monitor or a keyboard / mouse,
required by the [typical RPi setup][28].
Using just a SD Card reader/writer, a USB WiFi adapter,
and a Linux machine, I can do the whole setup.

If you determined to have WiFi for your RPi Zero
(the one without WiFi, like the Zero W has),
it can be done.
It's easy to just use a [Micro USB OTG Adapter][26] and a [WiFi USB Adapter][27].
With this in place, you just need to provision the RPi Zero
like any Raspberry Pi for WiFi connectivity.
This can be done by following "Step 3: Configure your WiFi" within
["HowTo: Set-Up the Raspberry Pi as a Headless Device"][25].

With USB Gadget support,
you can plug your Pi directly into your PC and get to it without any 3rd party software
and the Pi can use a separate wireless network such as your phone.
This helps create a setup that’s friendly for travel and requires very little cost.

* [enable the USB Gadget support on the Raspberry Pi Zero W](https://back7.co/home/weekend-project-portable-pi-zero-usb-gadget)

#### Step 1: Download Raspberry Pi Image - DONE
Before you can load a copy of the latest Raspberry Pi image onto your micro SD Card,
you must first download the official Raspberry Pi operating system, [Raspbian][13]
(in my case, the version is [Stretch][11]).
You can get that download [here][12].

>**NOTE:** I installed Raspbian Buster Lite
>(Version:September 2019, Release date:2019-09-26, Kernel version:4.19)

The Raspbian download site also lists a check sum for the download file.
(In my case, I down loaded the Raspbian file to `/home/jeff/Downloads/`.)
Check whether the file has been changed from its original state
by checking its digital signature (SHA1 hash value).

```bash
# validate file is uncorrupted via check of digital signature
$ sha256sum 2019-09-26-raspbian-buster-lite.zip
64c4103316efe2a85fd2814f2af16313abac7d4ad68e3d95ae6709e2e894cc1b 2019-09-26-raspbian-buster-lite.zip
```

Next you need to unzip the file to retrieve the Linux image file:

```bash
$ unzip 2019-09-26-raspbian-buster-lite.zip
Archive:  2019-09-26-raspbian-buster-lite.zip
  inflating: 2019-09-26-raspbian-buster-lite.img
```

#### Step 2: Write Raspberry Pi Image to SD Card - DONE
Next using Linux, you have copied the Raspbian image onto the SD card mounted to your system.
I'll be using the [Rocketek 11-in-1 4 Slots USB 3.0 Memory Card Reader][14] to create my SD Card.
Make sure to [choose a reputable SD Card][15] from [here][24], don't go cheap.

When using your card reader,
you'll need to know the device name of the reader.
The easiest way to find this is just unplug your card reader from the USB port,
run `df -h`, then plug it back in, and run `df -h` again.

```bash
# with the SD card reader unplugged
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  2.1M  1.6G   1% /run
/dev/sda3       110G   61G   44G  59% /
tmpfs           7.8G  833M  7.0G  11% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/loop3      157M  157M     0 100% /snap/gnome-3-28-1804/110
/dev/loop0       43M   43M     0 100% /snap/gtk-common-themes/1313
/dev/loop5       55M   55M     0 100% /snap/core18/1279
/dev/loop1      3.8M  3.8M     0 100% /snap/gnome-system-monitor/111
/dev/loop4       90M   90M     0 100% /snap/core/8213
/dev/loop6      141M  141M     0 100% /snap/gnome-3-26-1604/97
/dev/loop17      15M   15M     0 100% /snap/gnome-characters/367
/dev/loop13     1.0M  1.0M     0 100% /snap/gnome-logs/81
/dev/loop8      1.0M  1.0M     0 100% /snap/gnome-logs/73
/dev/loop16     157M  157M     0 100% /snap/gnome-3-28-1804/91
/dev/loop12     141M  141M     0 100% /snap/gnome-3-26-1604/98
/dev/loop9       45M   45M     0 100% /snap/gtk-common-themes/1353
/dev/loop15     4.3M  4.3M     0 100% /snap/gnome-calculator/536
/dev/loop10     4.3M  4.3M     0 100% /snap/gnome-calculator/544
/dev/sda1       461M  117M  321M  27% /boot
/dev/md0        917G  254G  617G  30% /home
/dev/sdb        3.6T  473G  3.0T  14% /mnt/backup
tmpfs           1.6G   64K  1.6G   1% /run/user/1000
/dev/loop18      90M   90M     0 100% /snap/core/8268
/dev/loop2       55M   55M     0 100% /snap/core18/1288
/dev/loop11     3.8M  3.8M     0 100% /snap/gnome-system-monitor/123
/dev/loop19      15M   15M     0 100% /snap/gnome-characters/375

# with the SD card reader plugged in USB
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  2.1M  1.6G   1% /run
/dev/sda3       110G   61G   44G  59% /
tmpfs           7.8G  833M  7.0G  11% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/loop3      157M  157M     0 100% /snap/gnome-3-28-1804/110
/dev/loop0       43M   43M     0 100% /snap/gtk-common-themes/1313
/dev/loop5       55M   55M     0 100% /snap/core18/1279
/dev/loop1      3.8M  3.8M     0 100% /snap/gnome-system-monitor/111
/dev/loop4       90M   90M     0 100% /snap/core/8213
/dev/loop6      141M  141M     0 100% /snap/gnome-3-26-1604/97
/dev/loop17      15M   15M     0 100% /snap/gnome-characters/367
/dev/loop13     1.0M  1.0M     0 100% /snap/gnome-logs/81
/dev/loop8      1.0M  1.0M     0 100% /snap/gnome-logs/73
/dev/loop16     157M  157M     0 100% /snap/gnome-3-28-1804/91
/dev/loop12     141M  141M     0 100% /snap/gnome-3-26-1604/98
/dev/loop9       45M   45M     0 100% /snap/gtk-common-themes/1353
/dev/loop15     4.3M  4.3M     0 100% /snap/gnome-calculator/536
/dev/loop10     4.3M  4.3M     0 100% /snap/gnome-calculator/544
/dev/sda1       461M  117M  321M  27% /boot
/dev/md0        917G  254G  617G  30% /home
/dev/sdb        3.6T  473G  3.0T  14% /mnt/backup
tmpfs           1.6G   68K  1.6G   1% /run/user/1000
/dev/loop18      90M   90M     0 100% /snap/core/8268
/dev/loop2       55M   55M     0 100% /snap/core18/1288
/dev/loop11     3.8M  3.8M     0 100% /snap/gnome-system-monitor/123
/dev/loop19      15M   15M     0 100% /snap/gnome-characters/375
/dev/sdf2       1.8G  1.1G  634M  64% /media/jeff/rootfs
/dev/sdf1        41M   41M   512 100% /media/jeff/0298-4814
```

Note that in my example above, the new device is `/dev/sdf1` and `/dev/sdf2`.
The last part (the number 1) is the partition number
but we want to write to the whole SD card, not just one partition.
Therefore you need to remove that part when creating the image.
With this information, and know the location of the Raspbian image and
where we need to write the Raspbian image to the SD Card
(see more detail instructions [here][16]).

```bash
# go to directory with the RPi image
cd ~/Downloads/Raspbian

# unmount the sd card reader
sudo umount /dev/sdf1 /dev/sdf2

# write the image to the sd card reader
sudo dd bs=4M if=2019-09-26-raspbian-buster-lite.img of=/dev/sdf

# ensure the write cache is flushed
sudo sync

# (optional) check the integrity of the sd card image
sudo dd bs=4M if=/dev/sdf of=copy-from-sd-card.img
sudo truncate --reference 2019-09-26-raspbian-buster-lite.img copy-from-sd-card.img
diff -s 2019-09-26-raspbian-buster-lite.img copy-from-sd-card.img
```

Remove SD card reader on your computer and then reinstall it.
We’re going to set up the network interfaces next.

>**NOTE:** You could immediately put the SD Card in the RPi and boot it up,
>but you will have no WiFi access and you'll need to use the Ethernet interface,
>or if there is no Ethernet interface,
>you'll need to use a console cable to make the file modification
>outline in the next step.
>[Adafruit has good description on how to use a console cable][17]
>and the how to [enable the UART for the console][18].

#### Step 3: Setup Networking - DONE
We now we need to setup
the hostname and networking features for the Raspberry Pi.
We do this by creating this file in

Using your card reader wuth the SD Card install,
plug it back into a USB port and find the file
`/media/jeff/rootfs/etc/network/interfaces`
modify this network interfaces file to look like this:

```bash
# Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
# Version:      0.5


# interfaces(5) file used by ifup(8) and ifdown(8)

# PLEASE NOTE that this file is written to be used with dhcpcd
# For static IP, consult /etc/dhcpcd.conf and 'man dhcpcd.conf'
# Also see https://raspberrypi.stackexchange.com/questions/39785/dhcpcd-vs-etc-network-interfaces


# include files from /etc/network/interfaces.d
source-directory /etc/network/interfaces.d

# The loopback network interface
auto lo
iface lo inet loopback

# establish ethernet (wired) network interface
iface eth0 inet manual

# establish wifi connection for embedded wifi
allow-hotplug wlan0
iface wlan0 inet manual
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

# establish wifi connection for dongle
allow-hotplug wlan1
iface wlan1 inet manual
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```

Next, you modify your `/media/jeff/rootfs/etc/wpa_supplicant/wpa_supplicant.conf`
WiFi file to look like this:


```bash
# Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
# Version:      0.5

# country code environment variable, required for RPi 3
country=US

# path to the ctrl_interface socket and the user group
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev

# allow wpa_supplicant to overwrite configuration file whenever configuration is changed
update_config=1

# 1 = wpa_supplicant initiates scanning and AP selection ; 0 = driver takes care of scanning
ap_scan=1

# home wifi network settings
network={
    id_str="home"                   # needs to match keyword you used in the interfaces file
    ssid="<home-ssid>"              # SSID either as an ASCII string with double quotation or as hex string
    mode=0                          # 0 = managed, 1 = ad-hoc, 2 = access point
    scan_ssid=0                     # = 1 do not broadcast SSID ; = 0 SSID is visible to scans
    proto=WPA RSN                   # list of supported protocals; WPA = WPA ; RSN = WPA2 (also WPA2 is alias for RSN)
    key_mgmt=WPA-PSK WPA-EAP        # list of authenticated key management protocols (WPA-PSK, WPA-EAP, ...)
    psk="<home-password>"           # pre-shared key used in WPA-PSK mode ; 8 to 63 character ASCII passphrase
    pairwise=CCMP                   # accepted pairwise (unicast) ciphers for WPA (CCMP, TKIP, ...)
    auth_alg=OPEN                   # authentication algorithms (OPEN, ShARED, LEAP, ...)
    priority=3                      # priority of selecting network (larger numbers are higher priority)
}

# jetpack wifi network settings
network={
    id_str="jetpack"                # needs to match keyword you used in the interfaces file
    ssid="<jetpack-ssid>"           # SSID either as an ASCII string with double quotation or as hex string
    mode=0                          # 0 = managed, 1 = ad-hoc, 2 = access point
    scan_ssid=0                     # = 1 do not broadcast SSID ; = 0 SSID is visible to scans
    proto=WPA RSN                   # list of supported protocals; WPA = WPA ; RSN = WPA2 (also WPA2 is alias for RSN)
    key_mgmt=WPA-PSK WPA-EAP        # list of authenticated key management protocols (WPA-PSK, WPA-EAP, ...)
    psk="<jetpack-password>"        # pre-shared key used in WPA-PSK mode ; 8 to 63 character ASCII passphrase
    pairwise=CCMP                   # accepted pairwise (unicast) ciphers for WPA (CCMP, TKIP, ...)
    auth_alg=OPEN                   # authentication algorithms (OPEN, ShARED, LEAP, ...)
    priority=5                      # priority of selecting network (larger numbers are higher priority)
}
```

#### Step 4: Setup Hostname - DONE
If you want to change the hostname, do the following:

```bash
sudo sed -i 's/raspberrypi/berrygps/' /media/jeff/rootfs/etc/hosts
sudo sed -i 's/raspberrypi/berrygps/' /media/jeff/rootfs/etc/hostname
```

#### Step 5: Enable SSH on Raspberry Pi - DONE
SSH is disabled by default in Raspberry Pi,
hence you’ll have to enable it when you turn on the Pi after a fresh installation of Raspbian.
SSH can be enabled by placing a file named `ssh`, without any extension,
onto the boot partition of the SD card.

```bash
# SSH can be enabled by placing a file named "ssh", without any extension,
# onto the boot partition of the SD card.
touch /media/jeff/boot/ssh
```

>**NOTE:** I'm not sure, but I believe this little trick
>only works on the first boot of the Raspberry Pi.

Now unmount the SD Card and move to the next step.

```bash
# unmount the sd card reader
sudo umount /dev/sdf1 /dev/sdf2
```

# Step 6: Finding Your Raspberry Pi IP Address - DONE
Next we'll power up the RPi Zero, but first,
lets check what IP address are being used on our WiFi network.
Place the SD-Card into the Raspberry Pi, power it up,
and login via ssh via WiFi or via Ethernet.

I will be run this Raspberry Pi headless,
and that can make login into them via `ssh` a challenge.
A typical secinario is you power up the device
and the interaction you have is this:

```bash
# attempting to log into a headless raspberry pi
$ ssh -X pi@berrygps
ssh: Could not resolve hostname berrygps: Temporary failure in name resolution
```

I'm quite sure DHCP has assigned an IP Address but DNS is failing to resolver the hostname `raspeberry`.
This will typically be resolved by DNS, but it never happens quick enough for me.
A simple trick to find your RPi is to `nmap` scan your network for open port 22,
the port supporting SSH, which must be open on the Raspberry Pi.

```bash
# scan for open port 22 on your network BEFORE powering up the rpi
$ nmap -T5 -n -p 22 --open 192.168.1.0/24 | grep "Nmap scan" | awk '{ print $5 }'
192.168.1.13
192.168.1.200
192.168.1.250

# scan for open port 22 on your network AFTER powering up the rpi
192.168.1.13
192.168.1.200
192.168.1.230
192.168.1.250
```

So the Raspberry Pi is amount this list of IP Addresses,
but I still have to decide which of the port-22-open devices is the RPi.

But there’s an even quicker way, that’s also more precise.
It turns out the Raspberry Pi Foundation actually has a range of MAC addresses all to themselves!
These ranges will have a prefix assigned, the [Organizationally Unique Identifiers (OUI)][76],
for the Ethernet or WiFi network interface on the Raspberry Pis.
The best resource to find the most current OUI assignments
is from the [MAC Address Block Large (MA-L) Public Listing at the IEEE][78].
A complete list of OUI assignments is compiled daily and is available [here][77].

According to this list there is a single OUI/MA-L assignment for the Raspberry Pi Foundation:

```
DC-A6-32   (hex)		Raspberry Pi Trading Ltd
				        Maurice Wilkes Building, Cowley Road
				        Cambridge    CB4 0DS
				        GB
```

But I also often use WiFi dongles from Edimax on my Raspberry Pis.
A search of the [OUI/MA-L assignment list][19] provides:

```
00-1F-1F   (hex)		Edimax Technology Co. Ltd.
00-50-FC                No. 278, Xinhu 1st Road
00-0E-2E                Taipei City  Neihu Dist  248
00-00-B4                TW
08-BE-AC
74-DA-38
80-1F-02

```

So `arp -a` can dump the candidate devices IP Addresses via this command:

```bash
# list of Edimax devices with open port 22 on your network
$ arp -a | grep -e 00:1f:1f -e 00:50:fc -e 00:0e:2e -e 00:00:b4 -e 08:be:ac -e 74:da:38 -e 80:1f:02

? (192.168.1.230) at 74:da:38:70:1c:08 [ether] on eth0
```

>**NOTE:** Sometimes the arp table has old cashed IP Addresses which are not live devices.
>See the article ["How to clear ARP cache on Linux or Unix"][79]
>to understand how to flush this cache.

So, we can now log into the Raspberry Pi via `ssh -X pi@berrygps` or `ssh -X pi@b192.168.1.230`.

#### Step 7: Update Linux Packages - DONE
On the Raspberry Pi, update the Linux packages.

```bash
# commandline utility for applications upgrade
sudo apt-get -y update && sudo apt-get -y dist-upgrade

# clean up any packages no longer needed
sudo apt-get -y autoremove
```

#### Step 8: Configure the Raspberry Pi - DONE
You could now run the `sudo raspi-config`
(see [raspi-config documentation][10] and [here][08])
This is an interactive script that allowing you to configured multiple devices settings.
Also, set the time zone and reboot.

```bash
# perfrom the raspi-config operations on the command-line normally done via UI tool
# raspi-config nonint do_hostname <hostname>   # modify the host name
#sudo raspi-config nonint do_ssh 0                   # enable ssh
sudo raspi-config nonint do_spi 0                   # SPI controller (/dev/spidev0.0 and /dev/spidev0.1) can be enabled
sudo raspi-config nonint do_i2c 0                   # enabling I2C bus /dev/i2c-1
sudo raspi-config nonint do_serial 0                # enable serial console and allows console cables to work
sudo raspi-config nonint do_onewire 0               # enable 1-wire
sudo raspi-config nonint do_camera 0                # enable camera
sudo raspi-config nonint do_expand_rootfs           # expand partition to use 100% of remaining space
sudo raspi-config nonint do_boot_behaviour B1       # require password to get console access

# set the time zone for your raspberry pi device
sudo timedatectl set-timezone "America/New_York"

# reboot to make sure all these commands take effect
sudo shutdown -r now
```

#### Step 9: Updating Firmware for Raspberry Pi - DONE
After a successful upgrade and reboot,
use `hostnamectl` and `vcgencmd` if you wish to see your current Raspbian version
and firmware version.
See how below:

```bash
# check you current OS version
 $ hostnamectl
   Static hostname: berrygps
         Icon name: computer
        Machine ID: 6ee07b9e27044479a87a5be0b6c1e96b
           Boot ID: b4d390ca43fd42568b2fd02181cfdfc5
  Operating System: Raspbian GNU/Linux 10 (buster)
            Kernel: Linux 4.19.75+
      Architecture: arm

# check the firmware version
$ sudo /opt/vc/bin/vcgencmd version
Sep 24 2019 17:39:25
Copyright (c) 2012 Broadcom
version 6820edeee4ef3891b95fc01cf02a7abd7ca52f17 (clean) (release) (start_x)
```

In the case of the Raspberry Pi, you will want to also upgrade the firmware regularly.
[Raspbian][07] is the standard Linux operating system distribution for the RPi,
but it doesn't include firmware.
Never the less, tools for updating the firmware are included in the Raspbian distribution of Linux.

```bash
# install firmware update tool
sudo apt-get -y install rpi-update

# check for and install any required Raspberry Pi firmware upgrades
sudo BRANCH=next rpi-update

# if firmware is installed, reboot
sudo shutdown -r now
```

Return the tools `hostnamectl` and `vcgencmd` to see how your
kernel and firmware may have changed from the earlier step.

Once these tools have been installed,
periodically you can update the firmware via the commands below:

```bash
# periodically you can update the firmware via the command
sudo apt-get install rpi-update

# check for and install any required Raspberry Pi firmware upgrades
sudo BRANCH=next rpi-update

# if firmware is installed, reboot
sudo shutdown -r now
```

#### Step 10: Development Package Installs - DONE
While the Raspberry Pi comes with a fairly robust set of Linux packages,
it could use some beefing up for most uses.
For example, while the distribution is likely to already have some Python packages installed,
execute the following to make sure you have all that is needed:

```bash
# package management tools
sudo apt-get -y install software-properties-common

# python 3 development libraries including TK and GTK GUI support
sudo apt-get -y install python3-dev python3-tk python-imaging-tk
sudo apt-get -y install libgtk-3-dev libboost-all-dev
sudo apt-get -y install build-essential cmake

# install pip
wget https://bootstrap.pypa.io/get-pip.py
sudo python3 get-pip.py
rm get-pip.py

# install virtual environment tools
sudo pip3 install virtualenv virtualenvwrapper

# install pyenv
curl -s https://raw.githubusercontent.com/pyenv/pyenv-installer/master/bin/pyenv-installer | bash

# general development tools
sudo apt-get -y install gnome-terminal jq markdown vim screen

# software version control tools
sudo apt-get -y install git git-lfs

# secure hash algorithms (SHA) tools, specifically SHA256
sudo apt-get -y install hashalot

# install some X Window utilities
sudo apt-get -y install x11-apps x11-xserver-utils xterm wmctrl

# general development tools
sudo apt-get -y install markdown vim vim-gtk libcanberra-gtk-module
sudo apt-get -y install microcom screen
sudo apt-get -y install build-essential i2c-tools libssl-dev

# so you can discover hosts via Multicast Domain Name System (mDNS)
sudo apt-get -y install avahi-daemon
```

#### Step 11: Load Personal Tools - DONE
Now that all the Linux packages have been loaded,
time to install my personal tools on the device.

```bash
# setup your bash environment
rm ~/.bashrc ~/.bash_logout
git clone https://github.com/jeffskinnerbox/.bash.git ~/.bash
ln -s ~/.bash/inputrc ~/.inputrc
ln -s ~/.bash/bashrc ~/.bashrc
ln -s ~/.bash/bash_login ~/.bash_login
ln -s ~/.bash/bash_logout ~/.bash_logout
ln -s ~/.bash/bash_profile ~/.bash_profile
ln -s ~/.bash/dircolors.old ~/.dircolors

# source/load the changes into your profile
source ~/.bashrc

# setup your vim environment
git clone http://github.com/jeffskinnerbox/.vim.git ~/.vim
ln -s ~/.vim/vimrc ~/.vimrc
mkdir ~/.vim/backup
mkdir ~/.vim/tmp
cd ~/.vim
git submodule init
git submodule update
cd ~

# setup your x windows environment
git clone http://github.com/jeffskinnerbox/.X.git ~/.X
ln -s ~/.X/xbindkeysrc ~/.xbindkeysrc
ln -s ~/.X/Xresources ~/.Xresources
ln -s ~/.X/xsessionrc ~/.xsessionrc

# rebuilding $HOME/.Xauthority to avoid MIT magic cookie error
touch ~/.Xauthority
xauth generate :0 . trusted
xauth add ${HOST}:0 . `xxd -l 16 -p /dev/urandom`
```

#### Step 12: Setup Python Development Environment - DONE
Now create a Python Virtual Environment to support the Python tools that will be used.

```bash
# create virtual environment - berrygps
$ mkvirtualenv berrygps -p python3
Already using interpreter /usr/bin/python3
Using base prefix '/usr'
New python executable in /home/pi/.virtualenvs/berrygps/bin/python3
Also creating executable in /home/pi/.virtualenvs/berrygps/bin/python
Installing setuptools, pip, wheel...
done.
virtualenvwrapper.user_scripts creating /home/pi/.virtualenvs/berrygps/bin/predeactivate
virtualenvwrapper.user_scripts creating /home/pi/.virtualenvs/berrygps/bin/postdeactivate
virtualenvwrapper.user_scripts creating /home/pi/.virtualenvs/berrygps/bin/preactivate
virtualenvwrapper.user_scripts creating /home/pi/.virtualenvs/berrygps/bin/postactivate
virtualenvwrapper.user_scripts creating /home/pi/.virtualenvs/berrygps/bin/get_env_details

# activate the virtual environment
workon berrygps

pip install gps

# exit/deactivate virtualenv
deactivate
```


----


# Setup for OzzMaker's BerryGPS

Sources:
* [BerryGPS setup Guide for Raspberry PI][23]
* [BerryGPS and BerryGPS-IMU Quick Start Guide][22]



I purchased the [BerryGPS-IMU v3][20],
which is designed to fit perfectly with the Raspberry Pi Zero,
but compatible with all other versions of the Raspberry Pi.
This location tracking board includes sensors for
GPS, Accelerometer, Gyroscope, Magnetometer (Compass), Barometric/Altitude, and Temperature.
The BerryGPS-IMU uses the same sensors found on the [BerryIMU][21].
This means that all of the guides and code used for the BerryIMU can also be used with the BerryGPS-IMU.
Read the post ["BerryGPS and BerryGPS-IMU Quick Start Guide"][22]
for a more complete description of the BerryGPS-IMU v3.

The OzzMaker products website list several useful postings concerning the BerryGPS-IMU v3 board"

* General
    * [BerryGPS and BerryGPS-IMU Quick Start Guide][22]
    * [BerryGPS setup Guide for Raspberry PI][23]
* GPS
    * [BerryGPS Data logger using a BerryGPS][29]
    * [Navigating with Navit on the Raspberry Pi][33]
    * [Use u-Center graphical interface to control GPS](http://ozzmaker.com/using-u-center-to-connect-to-a-raspberry-pi-with-an-attached-berrygps-imu-gsm/)
    * [Getting Started with U-Center for u-blox](https://learn.sparkfun.com/tutorials/getting-started-with-u-center-for-u-blox/all)
    * [Using python with a GPS receiver on a Raspberry Pi](http://ozzmaker.com/using-python-with-a-gps-receiver-on-a-raspberry-pi/)
    * [Real-time GPS tracking with a Raspberry Pi](http://ozzmaker.com/real-time-gps-tracking-with-a-raspberry-pi/)
    * [How to save GPS data to a file using Python](http://ozzmaker.com/how-to-save-gps-data-to-a-file-using-python/)
* IMU
    * [IMU Attitude Estimation](http://philsal.co.uk/projects/imu-attitude-estimation)
    * [Guide to interfacing a Gyro and Accelerometer with a Raspberry Pi](http://ozzmaker.com/berryimu/)
    * [Guide to interfacing a Gyro and Accelerometer with a Raspberry Pi - Kalman Filter](http://ozzmaker.com/guide-interfacing-gyro-accelerometer-raspberry-pi-kalman-filter/)
    * [Create a Digital Compass with the Raspberry Pi – Part 1 – “The Basics”](http://ozzmaker.com/compass1/)
    * [Create a Digital Compass with the Raspberry Pi – Part 2 – “Tilt Compensation”](http://ozzmaker.com/compass2/)
    * [Create a Digital Compass with the Raspberry Pi – Part 3 – “Calibration”](http://ozzmaker.com/compass3/)
    * [Create a Digital Compass with the Raspberry Pi – Part 4- “Smartphone Replica”](http://ozzmaker.com/compass04/)
    * [Converting values from an Accelerometer to Gs – “ Proper Acceleration”](http://ozzmaker.com/accelerometer-to-g/)
    * [How to Create an Inclinometer using a Raspberry Pi and an IMU](http://ozzmaker.com/inclinometer-using-raspberry-pi-imu/)
    * [Raspberry Pi Digital Spirit Level]()

#### Step 1: Physical Assembly of the BerryGPS-IMU - DONE
Consult the post ["BerryGPS and BerryGPS-IMU Quick Start Guide"][22]
to understand how to assemble the unit.

#### Step 2: Disable Serial Console - DONE
BerryGPS uses the serial port assigned to console on the Raspberry Pi,
so we need to disable the console and make use of its pins for GPS NMEA messages.
On RPi Zero, console is assign `/dev/ttyAMA0` and
`/dev/serial0` is assigned as an alias to console.
We'll free up `/dev/serial0` for GPS use.

```bash
# current tty assignment for console
$ ls -l /dev/serial0 /dev/ttyAMA0
lrwxrwxrwx 1 root root       7 Dec 27 15:11 /dev/serial0 -> ttyAMA0
crw--w---- 1 root tty  204, 64 Dec 27  2019 /dev/ttyAMA0

# serial console needs to be disabled and then the serial port enabled
# select 'interfacing options' -> Serial Port -> No -> Yes and then Yes to reboot
sudo raspi-config               # execute in interactive mode

# reboot the rpi
sudo shutdown -r now

# verify new assignment of console (tty1)
$ cat /boot/cmdline.txt
console=tty1 root=PARTUUID=6c586e13-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait
```

#### Step 3: Verify You Can View GPS Data - DONE
Now it time to see if we got things working
by looking raw GPS data, [NMEA sentences][02], from device `/dev/serial0`.
NMEA sentences contain all the requered GPS data (e.g longatute, latitude, number of statilites, etc.).
There is are several ways to see this data:

```bash
# cat the data to stdout
cat /dev/serial0

# scroll the data on a terminal
screen /dev/serial0 9600,cs8

# or using the ttyAMA0 device
cat /dev/ttyAMA0
screen /dev/ttyAMA0 9600,cs8
```

Every second or two, any of the satellites picked up by the GPS chip puts out some information,
and that information is encoded in sentences, or what you see on each line.
Each sentence encodes specific pieces of information separated by commas,
which has a different meaning based on the first 5 (or so) characters.
The exact specification is proprietary,
but there is a [good online reference][02].

If your [GPS has a fix][03], you would also see the green LED flash on the BerryGPS
and the NMEA data will have almost all the comma delimited spaces filled in.
If you have no fix, then no green LED and most of the NMEA data is empty.gg
On first power up, it can take your GPS module 10 minutes to get a fix in some situations.



-------



# Sharing GPS Data Locally & Over Network
Many applications may wish to use location GPS data simultaneously.
Another complicating factor is that there are several incompatible GNSS protocols for delivering location information,
including flavors of NMEA-0183, Rockwell and SiRF binary protocols, AIS, and others.
To solve these problems,
`gpsd` is a service daemon that can monitor a locally attached GPS receiver of any type
and provides the data via an Internet Protocol (IP) network to
potentially multiple client applications in a server-client application architecture.
This network interface provides a standardized data format for multiple concurrent client applications, such as Kismet or GPS navigation software.

`gpsd` provides data to port 2947 where `systemd` is listening.
By default in Debian this port is local only,
any external requests for GPS data ios blocked.
I want to get `gpsd` to accept incoming requests over the network on port 2947
and stream the GPS NMEA data.

I'll be install `gpsd` but I will not be using the default installation where the daemon starts automatically.
Starting with the Raspberry Pi OS releases “Jessie”,
it require disabling a service that `gpsd` installs (see [here][102]).
This service has `systemd` listen on a local socket and run `gpsd` when clients connect to it,
however it will also interfere with other `gpsd` instances that are manually run,
and in general apears to cause problems using a GPS device.
Some sources ([here][103] and [here][104]) appear to claim that an installation from source will fix the issue
but seems like too much work for my needs.

I want to create a simple client/server connection is between two devices
(the GPS device `berrygps` and my desktop linux `desktop`).
`berrygps` (IP address `192.168.1.151`) acts as a server, aka the listener,
waiting for a TCP/IP connection to a port where GPS data will be streaming out.
The `desktop` (IP address `192.168.1.200`) acts as a client, aka the connector,
who connects to a port via TCP/IP to consume the streaming GPS data.
It is claimed that you can do this natively with `gpsd`,
but because I will **not** be using `gpsd` with automatic start,
I'll show another way with `netcat`.

## Sharing GPS Data Locally
There are a number of ways to configure the Raspbery Pi for reciveing GPS data
(for example, see [here][23] and [here][102]).
I'm going to install the `gpsd` daemon, make it manageble from `systemctl`
but choose to disable it and invoke it manually.
This way, I have the option to fall back to `systemctl` management and have `gpsd` start at boot time.

#### Step X: Install `gpsd` Daemon and Tools - DONE DONE
The Linux utility [`gpsd`][04] is a daemon that receives data from a GPS receiver,
acts as a layer between your applications and the actual GPS hardware,
parsing errors, and providing a more readable, well-defined interfaces to any GPS module.
All the GPS data on the location/course/velocity is available
to be queried on TCP port 2947 of the Linux computer hosting the GPS sensor.

Companion libraries of tools called `gpsd-clients`, `libgps-dev`, and `libgps`,
provide the NMEA data back to multiple applications such as:

* [`xgps`][94] - This is a simple client for `gpsd` with an X interface. It displays current GNSS position/time/velocity information and (for GNSS receivers that support the feature) the locations of accessible satellites.
* [`gpsmon`][05] - This watches packets coming from a GPS and displays them along with diagnostic information. It supports commands that can be used to tweak GPS settings in various ways; some are device-independent, some vary with the GPS chipset type.
* [`cgps`][06] - This is a client resembling `xgps`, but without the pictorial satellite display and able to run on a serial terminal or terminal emulator.
* [`gegps`][95] - This program collects fixes from gpsd and feeds them to a running instance of Google Earth for live location tracking.
* [`lcdgps`][95] - A client that passes `gpsd` data to [`lcdproc`][93], turning your car computer into a very expensive and nearly feature-free GPS receiver. Currently assumes a 4x40 LCD and writes data formatted to fit that size screen. Also displays 4- or 6-character Maidenhead grid square output.
* [`gpsprof`][09] - This performs accuracy, latency, skyview, and time drift profiling on a GPS. It emits to standard output a GNUPLOT program that draws one of several illustrative graphs. It can also be told to emit the raw profile data.
* [`xgpsspeed`][95] - This is a speedometer that uses position information from the GPS.
* [`gegps`][95] - This program collects fixes from `gpsd` and feeds them to a running instance of Google Earth for live location tracking.
* [`gpscat`][96] - Program for logging and packetizing GPS data streams. It takes input from a specified file or serial device (presumed to have a GPS attached) and reports to standard output.
* [`gpspipe`][97] - A tool to connect to gpsd and output the received sentences to stdout. This makes the program useful as a pipe from gpsd to another program or file.
* [`gpxlogger`][98] - This program collects fixes from `gpsd` and logs them to standard output in GPX (a XML profile for track logging).
* [`gpsfake`][100] - This program is a test harness for `gpsd` and its clients. It opens a pty (pseudo-TTY), launches a `gpsd` instance that thinks the slave side of the pty is its GNSS device, and repeatedly feeds the contents of one or more test logfiles through the master side to the GNSS receiver. So you would record the log from a real GNSS receiver with `gpspipe -R > gps.log` and later use `gpsfake` to replay it during testing without GNSS receiver.

Be default, `gpsd` is configured to start at boot and run in the background as a daemon.
While a daemon service has its uses, it can get in our way.
Therefore, at this time, the daemon service will be turned off.
Also, we need to edit the `gpsd` config file so that `gpsd` uses the correct serial device.

```bash
# install, gpsd, gpsmon, cgps, etc
sudo apt -y install gpsd gpsd-clients libgps-dev

# install gpsprof
sudo apt -y install python-gps gnuplot

# supporting libraries
sudo apt -y install pkg-config libcairo2-dev gcc python3-dev libgirepository1.0-dev
sudo pip3 install gobject PyGObject

# the gpsd daemon will automatically start boot time but lets disable this features
sudo systemctl stop gpsd gpsd.socket
sudo systemctl disable gpsd gpsd.socket

# check the status of the gpsd systemd service
systemctl status gpsd gpsd.socket

# updated gpsd configuration file
sudo sed -i 's/DEVICES=\"\"/DEVICES=\"\/dev\/serial0\"/' /etc/default/gpsd

# reboot the rpi
sudo shutdown -r now
```

You can start the `gpsd` manually and test out some tools via the following:

```bash
# start the gpsd daemon
# note: option `-N` doesn't daemonize bur run in foreground in stead. This switch is mainly useful for debugging
sudo gpsd /dev/serial0 -F /var/run/gpsd.sock

# check to see if gpsd is running
ps aux | grep gpsd

# display current GNSS position/time/velocity information,
# and for GNSS receivers that support the feature) the locations of accessible satellites
cgps
# OR
# surpress scrolling NEMA messages on the screen
cgps -s
# OR
# watch packets coming from a GPS and displays them along with diagnostic information
gpsmon
# OR
# connect to gpsd and output the received NMEA sentences to stdout
# this program useful as a pipe from gpsd to another program or file
#    -r = output raw NMEA sentences
#    -R = causes super-raw (gps binary) data to be output
#    -d = causes gpspipe to run as a daemon
#    -l = causes gpspipe to sleep for ten seconds before attempting to connect to gpsd
#    -o = output to file
gpspipe -r
# OR
# perform accuracy, latency, skyview, and time drift profiling on a GPS
gpsprof -n 10
gpsprof -n 50 | gnuplot -persist
# OR
# for logging and packetizing GPS data streams, take input from a specified file
# file or serial device (presumed to have a GPS attached) and reports to standard output
gpscat /dev/serial0

# stop the gpsd daemon
sudo killall gpsd
```

#### Step X: Remove `gpsd` Daemon and Tools - DONE NOT DONE
If for any reason you need to completely remove the `gpsd` daemon
and its supporting packages, configuration file, etc.,
do the following:

```bash
# stop and disable any gpsd service that might be running
sudo systemctl stop gpsd gpsd.socket
sudo systemctl disable gpsd gpsd.socket
sudo killall gpsd

# remove the packages and any configuration files for them
sudo apt remove --purge gpsd gpsd-clients libgps-dev

# removes orphaned packages, i.e. packages installed as dependency, but nolong needed by any package
sudo apt autoremove

# restart the pi
sudo shutdown -r now
```



-------



## Share GPS Data Remotely
See the article ["nc Command (Netcat) with Examples"][74] for insight on how this is done.

#### Step X: Using gpsd to Supply NMEA to Remote Machine - DONE
First establish the server and then connect the client to the server, as shown below:

```bash
# if not already running, start the gpsd daemon
# note: option `-N` doesn't daemonize bur run in foreground in stead. This switch is mainly useful for debugging
sudo gpsd /dev/serial0 -F /var/run/gpsd.sock

# on the server, establish the streaming gps NMEA data on port 1499 (or any unoccupied port)
gpspipe -r | netcat -lkv 1499       # executed on 'berrygps', ip 192.168.1.151

# on the client, consume the streaming gps and send to stdout
netcat -v 192.168.1.151 1499        # executed on the client, 'desktop'
# - or -
netcat -v berrygps 1499             # executed on the client, 'desktop'
```

This works fine when you have one client,
but **what if you have multipe clients** that wish to consume the same streaming GPS data?
For this, you can use another tool called [`ncat`][75].
Do the following:

```bash
# on the server, establish the streaming gps NMEA data on port 1499 (any unoccupied port)
gpspipe -r | ncat -lkv 1499         # executed on 'berrygps', ip 192.168.1.151

# on the client, consume the streaming gps and send to stdout
netcat -v 192.168.1.151 1499        # executed on the client, 'desktop'
# - or -
netcat -v berrygps 1499             # executed on the client, 'desktop'
```

#### Step X: Viewing GPS Data on Remote Machine
Since the NMEA data supplied to the remote machine is **not** native `gpsd` output
destine for gps-tools (i.e. its missing setup data),
you can't use tools like `cgps`, `gpsmon`, etc.
Never the less, are number of freely available Python scripts and tools
which we can used to view meaningful information
from the GPS unit, like longitude, latitude and ground speed.

```bash
netcat -v 192.168.1.151 1499 | ./nmea-parser.py
```


----



# Setup for OzzMaker's IMU



-----



# Setup for Adafruit's Ultimate GPS
[!ultimate-gps](https://cdn-learn.adafruit.com/assets/assets/000/003/714/medium640/raspberry_pi_gps_pi_usbconnection2.jpg?1396801034)
I also purchased [Adafruit's Ultimate GPS][41] which uses the [MediaTek MTK3339 chipset][42].
This is a high-quality GPS module that can track up to 22 satellites concurrently,
has an module has a standard ceramic patch antenna
with an excellent high-sensitivity receiver (-165 dBm tracking and -145 dBm acquisition!),
and a built in antenna but with a option for active external antenna.
It has a 10Hz update rate (i.e. it can do up to 10 location updates per second)
giving it a high speed, high sensitivity logging or tracking capability.
Its power usage is very low, only 20mA during navigation and 25mA during tracking.
It claims a warm/cold start time of 34 seconds,
a maximum tracking velocity of 515 meters/s,
a position accuracy of 1.8 meters, and velocity accuracy of 0.1 meters/s.
The module supports DGPS/WAAS/EGNOS,
it is FCC E911 compliance with AGPS support,
jammer detection / reduction,
and multi-path detection / compensation.

The module supports an optional CR1220 coin cell to keep the real-time clock (RTC)
running, allowing warm starts and a tiny red LED.
The LED blinks at about 1Hz while it's searching for satellites
and blinks once every 15 seconds when a fix is found to conserve power.
Data is provided via a serial [NMEA 0183][46], 9600 baud (default) output.

The GPS module has a built in data-logging capability.
There is a microcontroller inside the module,
with some empty FLASH memory,
and the firmware allows sending commands to do internal logging to that FLASH.
You simply tell the microcontroller "Start Logging".
After that message is sent, the microcontroller can go to sleep
and does not need to wake up to talk to the GPS anymore to reduce power consumption.
The time, date, longitude, latitude, and height is logged every 15 seconds
and only when there is a satellite fix.
The internal FLASH can store about 16 hours of data.
It also will automatically append data so you don't have to worry
about losing data if power is lost.
With the current firmware, is not possible to change what is logged and how often.

Adafruit provides some excellent write-up on how to configure and use this device:

* [Adafruit Ultimate GPS](https://learn.adafruit.com/adafruit-ultimate-gps/overview)
* [Adafruit Ultimate GPS on the Raspberry Pi](https://learn.adafruit.com/adafruit-ultimate-gps-on-the-raspberry-pi?view=all)
* [Adafruit's GPS Library LOCUS](https://github.com/adafruit/Adafruit_GPS)

## External GPS Antenna
With the module, I also purchase an external [active GPS antenna][43] that draws about 10mA
and will give you an additional 28 dB of gain
(but it has a 5 meter cable so may not see this gain).
You'll also need a [console cable][44] to easily make use of this GPS module.

There is also a GNSS Multi-Band antenna, such as the [ANN-MB-00 GNSS multiband antenna][66].
A multiband antenna is unique from other GNSS/GPS antennas
in that it is designed to receive both the classic L1 GPS band
and the newly launched (started in 2005) L2 GPS band.

For information about NMEA sentence that cover antenna status - https://cdn-learn.adafruit.com/downloads/pdf/adafruit-ultimate-gps.pdf

#### Step 1: GPS Module Pinouts - DONE
[Adafruit's tutorial][45] provides an excellent description of the GPS module pins
and how to connect the console cable and external antenna
can be found in the tutorial "[Adafruit Ultimate GPS on the Raspberry Pi][47]".

[!gps-module-pinout](https://cdn-learn.adafruit.com/assets/assets/000/003/713/medium640/raspberry_pi_UltimateGPS_bb.png?1396801027)

#### Step 2: Setup Console Cable - DONE
Once you plug the console cable into the RPi,
the adapter should show up as a device file `/dev/ttyUSBX`
(where the 'X' will be '0', '1', '2', etc. depending on what other `ttyUSB` adapters are present.
So do the following:

```bash
# before you plug in the console cable
$ ls /dev/ttyUSB*
ls: cannot access /dev/ttyUSB*: No such file or directory

# after you plug in the console cable
ls /dev/ttyUSB*
/dev/ttyUSB0
```

This shows a new device file `/dev/ttyUSB0`.
This is your serial connection to the GPS module.

With the console cable plugged into the USB port of the RPi and GPS module wired,
you can do a quick check on what the device is doing:

```bash
# quick check of GPS module
$ sudo cat /dev/ttyUSB0
$GPGGA,164440.093,,,,,0,00,,,M,,M,,*71

$GPGSA,A,1,,,,,,,,,,,,,,,*1E

$GPGSV,1,1,01,01,,,31*7B

$GPRMC,164440.093,V,,,,,0.00,0.00,060180,,,N*4B

$GPVTG,0.00,T,,M,0.00,N,0.00,K,N*32

$GPGGA,164440.093,,,,,0,00,,,M,,M,,*71


```

To monitor continuously, its best to open up a serial terminal to check for activity.
Follow these steps:

```bash
# mointor gps data continously
sudo screen /dev/ttyUSB0 9600

# "ctrl-A" followed by ":quit" to stop and get out of screen
```

It may 30 or more seconds before the red LED stops blinking at 1 second intervals.
During this time, the GPS module is attempting to get a fix on the GPS satellites.
If needed, [use the external antenna to get a GPS fix][54].
The module will automatically detect an external active antenna is attached and switch over to use it.

>**NOTE:** uFL connectors are small and delicate.
>The are not engineered for for repeated connections/disconnections.
>Once you attach a uFL adapter, it is best to just let remain on the module.

#### Step 3: Installing the GPS Daemon (gpsd) - DONE
The Raspberry Pi is successfully receiving the serial data that the GPS module provides
but its very cryptic.
There is a daemon that properly parsing the raw GPS data called `gpsd`.
It acts as a layer between your applications and the actual GPS hardware,
parsing errors, and providing a more readable, well-defined interfaces to any GPS module.

At this point,
you can use the same procedure (Steps 4 onward) used for the OzzMaker BerryGPS device.

#### Step X: Changing Baud Rate of GPS Module
* [How to change the baud rate and update rate of MTK GPS module](https://hobbyking.com/media/file/201626144X19082X53.pdf)
* [MediaTek MTK33X9 GPS Chipset Command Generator](https://forum.micropython.org/viewtopic.php?t=726)
* [MTK NMEA PROPRIETARY COMMAND](https://www.pitlab.com/autopitlot/doc/MTK_commands.pdf)
* [PMTK command packet](http://www.pvelectronics.co.uk/PA6B/PA6B_commands.pdf)

#### Step X: Battery Backup
* https://learn.adafruit.com/adafruit-ultimate-gps/battery-backup
* [How to trade-off location accuracy against battery life in cellular IoT asset trackers](https://blog.nordicsemi.com/getconnected/how-to-trade-off-location-accuracy-against-battery-life-in-cellular-iot-asset-trackers)

#### Step X: Built In Logging
* https://learn.adafruit.com/adafruit-ultimate-gps/built-in-logging

#### Step X: Using Raspberry Pi UART Instead of USB
* https://learn.adafruit.com/adafruit-ultimate-gps-on-the-raspberry-pi?view=all#using-uart-instead-of-usb


----


# WiFi Scan Mapping
* [Creepy Wireless Stalking Made Easy](https://hackaday.com/2016/12/04/creepy-wireless-stalking-made-easy/)

# GPS Data Logger and Mapping
The posts ["BerryGPS Data logger using a BerryGPS"][29]
and [Navigating with Navit on the Raspberry Pi][33]
explains how to log and map GPS data
from a BerryGPS-IMU and then how to plot this data onto [Google Maps][30] and other maps
(e.g. [OpenStreetMap][31], [National Maps][32], etc.).

* [What I love about OpenStreetMap](https://opensource.com/article/21/8/openstreetmap)
* [Contribute to OpenStreetMap from your phone](https://opensource.com/article/21/8/streetcomplete-quests)

# Using the Python GPS Library
With the `gpsd` process running,
execute the Python program below:

```python
import gps3 requests

# Listen on port 2947 (gpsd) of localhost
session = gps.gps("localhost", "2947")
session.stream(gps.WATCH_ENABLE | gps.WATCH_NEWSTYLE)

while True:
    try:
        report = session.next()
		# Wait for a 'TPV' report and display the current time
		# To see all report data, uncomment the line below
		# print report
        if report['class'] == 'TPV':
            if hasattr(report, 'time'):
                print report.time
    except KeyError:
		pass
    except KeyboardInterrupt:
		quit()
    except StopIteration:
		session = None
		print "GPSD has terminated"
```

# Real-Time GPS Tracking
* [Real-Time GPS Tracking](https://www.instructables.com/id/Real-Time-GPS-Tracking/)

# Using the Node.js GPS Library
* GPS.js is an extensible parser for NMEA sentences - https://www.npmjs.com/package/gps
* wrapper to start and stop gpsd from your program - https://www.npmjs.com/package/node-gpsd
* https://www.npmjs.com/browse/keyword/gps

# Serial Studio
Serial Studio is a multi-platform, multi-purpose serial data visualization program. The goal of this project is to allow embedded developers & makers to easily visualize, present & analyze the data generated by their projects and devices, without the need of writing specialized computer software for each project.

* [Serial Studio: Easily Visualise And Log Serial Data](https://hackaday.com/2021/01/31/serial-studio-easily-visualise-and-log-serial-data/)
* [Introducing Serial Studio, a dashboard software for serial port projects](https://www.alex-spataru.com/blog/introducing-serial-studio)
* [Serial Studio One Year On](https://hackaday.com/2022/01/15/serial-studio-one-year-on/)
* [Serial-Studio](https://github.com/Serial-Studio/Serial-Studio)

# Other Tools
* http://www.visualgps.net/
* [7 of the Best Free Linux GPS Tools](http://www.linuxlinks.com/article/20110522052357647/GPSTools.html)

# Open Source GPS/GNSS Hardware
* [New open-source wireless GPS/GNSS hardware for IoT and autonomous applications](https://www.geospatialworld.net/news/new-open-source-wireless-gps-gnss-hardware-for-iot-and-autonomous-applications/)

# GPS Tracking Terminal
* [LoRa GPS Tracker with Wio Terminal](https://www.hackster.io/idreams/lora-gps-tracker-with-wio-terminal-5d8647)
* [Wio terminal GPS](https://www.hackster.io/SeeedStudio/wio-terminal-gps-ad70e2)
* [S.O.S Enabled GPS Tracker](https://www.hackster.io/scottpowell69/s-o-s-enabled-gps-tracker-620407)

# A Practical Guide Quaternions
* [Today’s the Day You Finally Learn Quaternions](https://hackaday.com/2022/09/05/todays-the-day-you-finally-learn-quaternions/)
* [Fantastic Quaternions - Numberphile](https://www.youtube.com/watch?v=3BR8tK-LuB0)
* [Visualizing quaternions (4d numbers) with stereographic projection](https://www.youtube.com/watch?v=d4EgbgTm0Bg)

* [Quaternions are Amazing and so is William Rowan Hamilton!](https://www.youtube.com/watch?v=CdwxpSInhvU)
* [How Maxwell's Equations (and Quaternions) Led to Vector Analysis](https://www.youtube.com/watch?v=M12CJIuX8D4)
* [Quaternions](https://www.youtube.com/playlist?list=PLpzmRsG7u_gr0FO12cBWj-15_e0yqQQ1U)
* [The rotation problem and Hamilton's discovery of quaternions I | Famous Math Problems 13a](https://www.youtube.com/watch?v=uRKZnFAR7yw)
* [The rotation problem and Hamilton's discovery of quaternions (II) | Famous Math Problems 13b](https://www.youtube.com/watch?v=0_XoZc-A1HU)
* [The rotation problem and Hamilton's discovery of quaternions III | Famous Math Problems 13c](https://www.youtube.com/watch?v=g22jAtg3QAk)
* [The rotation problem and Hamilton's discovery of quaternions IV | Famous Math Problems 13d](https://www.youtube.com/watch?v=MkNfQtINEjo)



[01]:http://internetofthingsagenda.techtarget.com/definition/headless-system
[02]:http://www.gpsinformation.org/dale/nmea.htm
[03]:https://en.wikipedia.org/wiki/Time_to_first_fix
[04]:https://gpsd.gitlab.io/gpsd/index.html
[05]:https://gpsd.gitlab.io/gpsd/gpsmon.html
[06]:https://manpages.debian.org/jessie/gpsd-clients/cgps.1.en.html
[07]:http://www.raspbian.org/
[08]:https://raspberrypi.stackexchange.com/questions/28907/how-could-one-automate-the-raspbian-raspi-config-setup#47958
[09]:https://gpsd.gitlab.io/gpsd/gpsprof.html
[10]:http://elinux.org/RPi_raspi-config
[11]:https://www.raspberrypi.org/blog/raspbian-stretch/
[12]:https://www.raspberrypi.org/downloads/raspbian/
[13]:https://www.raspbian.org/
[14]:http://www.amazon.com/gp/product/B00GVRHON2?psc=1&redirect=true&ref_=oh_aui_detailpage_o00_s01
[15]:http://www.wirelesshack.org/best-micro-sd-card-for-the-raspberry-pi-model-2.html
[16]:https://www.raspberrypi.org/documentation/installation/installing-images/linux.md
[17]:https://www.bitpi.co/2015/02/11/how-to-change-raspberry-pis-swapfile-size-on-rasbian/
[18]:https://cdn-learn.adafruit.com/downloads/pdf/adafruits-raspberry-pi-lesson-5-using-a-console-cable.pdf
[19]:http://standards-oui.ieee.org/oui.txt
[20]:http://ozzmaker.com/product/berrygps-imu/
[21]:http://ozzmaker.com/product/berryimu-accelerometer-gyroscope-magnetometer-barometricaltitude-sensor/
[22]:http://ozzmaker.com/berrygps-berrygps-imu-quick-start-guide/
[23]:http://ozzmaker.com/berrygps-setup-guide-raspberry-pi/
[24]:http://www.jeffgeerling.com/blogs/jeff-geerling/raspberry-pi-microsd-card
[25]:http://jeffskinnerbox.me/posts/2016/Apr/27/howto-set-up-the-raspberry-pi-as-a-headless-device/
[26]:https://www.amazon.com/gp/product/B015GZOHKW
[27]:https://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY
[28]:https://www.raspberrypi.org/help/noobs-setup/
[29]:http://ozzmaker.com/gps-data-logger-using-berrygps/
[30]:https://cloud.google.com/maps-platform/
[31]:https://www.openstreetmap.org
[32]:https://www.usgs.gov/core-science-systems/national-geospatial-program/national-map
[33]:http://ozzmaker.com/navigating-navit-raspberry-pi/
[34]:https://www.gpsworld.com/what-exactly-is-gps-nmea-data/
[35]:https://techdifferences.com/difference-between-gps-and-dgps.html
[36]:https://racelogic.support/01VBOX_Automotive/01General_Information/Knowledge_Base/How_Does_DGPS_(Differential_GPS)_Work%3F
[37]:https://gisgeography.com/trilateration-triangulation-gps/
[38]:https://confluence.qps.nl/qinsy/latest/en/world-geodetic-system-1984-wgs84-182618391.html
[39]:https://gisgeography.com/geoid-mean-sea-level/
[40]:https://gisgeography.com/geodesy/
[41]:https://www.adafruit.com/product/746
[42]:https://cdn-shop.adafruit.com/datasheets/GlobalTop-FGPMMOPA6C-Datasheet-V0A-Preliminary.pdf
[43]:https://electronics.stackexchange.com/questions/130509/gps-antenna-when-is-an-active-antenna-really-necessary
[44]:https://www.adafruit.com/product/954
[45]:https://learn.adafruit.com/adafruit-ultimate-gps/pinouts
[46]:https://en.wikipedia.org/wiki/NMEA_0183
[47]:https://learn.adafruit.com/adafruit-ultimate-gps-on-the-raspberry-pi?view=all
[48]:http://aprs.gids.nl/nmea/
[49]:http://aprs.gids.nl/nmea/#rmc
[50]:http://aprs.gids.nl/nmea/#gga
[51]:http://aprs.gids.nl/nmea/#vtg
[52]:http://aprs.gids.nl/nmea/#gsa
[53]:http://aprs.gids.nl/nmea/#gsv
[54]:https://learn.adafruit.com/adafruit-ultimate-gps/external-antenna
[55]:https://www.nmea.org/
[56]:http://gpsworld.com/what-exactly-is-gps-nmea-data/
[57]:https://www.sparkfun.com/datasheets/GPS/NMEA%20Reference%20Manual1.pdf
[58]:https://gisgeography.com/ellipsoid-oblate-spheroid-earth/
[59]:http://aprs.gids.nl/nmea/#zda
[60]:http://www.gpsinformation.org/dale/nmea.htm#nmea
[61]:https://www.glonass-iac.ru/en/
[62]:https://www.esa.int/Our_Activities/Navigation/Galileo/What_is_Galileo
[63]:http://www.beidou.gov.cn/
[64]:https://gnss-sdr.org/
[65]:http://geostar-navi.com/files/docs/geos3/geos_nmea_protocol_v3_0_eng.pdf
[66]:https://www.sparkfun.com/products/15192
[67]:http://support.virtual-surveyor.com/en/support/solutions/articles/1000261351-what-is-wgs84-
[68]:https://learn.sparkfun.com/tutorials/lsm9ds1-breakout-hookup-guide/all
[69]:https://learn.adafruit.com/adafruit-bmp280-barometric-pressure-plus-temperature-sensor-breakout/overview
[70]:https://cdn.sparkfun.com/assets/0/b/0/f/7/u-blox8-M8_ReceiverDescrProtSpec__UBX-13003221__Public.pdf
[71]:https://gisgeography.com/horizontal-datum/
[72]:https://gisgeography.com/vertical-datum/
[73]:https://www.rtcm.org/
[74]:https://phoenixnap.com/kb/nc-command
[75]:https://man7.org/linux/man-pages/man1/ncat.1.html
[76]:https://en.wikipedia.org/wiki/Organizationally_unique_identifier
[77]:http://standards.ieee.org/develop/regauth/oui/public.html
[78]:https://standards.ieee.org/products-services/regauth/oui/index.html
[79]:https://coderseye.com/how-to-clear-arp-cache-on-linux-or-unix/
[80]:https://www.redhat.com/architect/architects-guide-gps-and-gps-data-formats#GPGGA
[81]:https://www.redhat.com/architect/architects-guide-gps-and-gps-data-formats#GPGLL
[82]:https://www.redhat.com/architect/architects-guide-gps-and-gps-data-formats#GPVTG
[83]:https://www.redhat.com/architect/architects-guide-gps-and-gps-data-formats#GPRMC
[84]:https://www.redhat.com/architect/architects-guide-gps-and-gps-data-formats#GPGSA
[85]:https://www.redhat.com/architect/architects-guide-gps-and-gps-data-formats#GPGSV
[86]:https://en.wikipedia.org/wiki/Echo_sounding
[87]:https://en.wikipedia.org/wiki/Sonar
[88]:https://en.wikipedia.org/wiki/Anemometer
[89]:https://en.wikipedia.org/wiki/Gyrocompass
[90]:https://en.wikipedia.org/wiki/Autopilot
[91]:https://www.isro.gov.in/irnss-programme
[92]:https://qzss.go.jp/en/
[93]:http://lcdproc.omnipotent.net/
[94]:https://www.mankier.com/1/xgps
[95]:https://manpages.debian.org/testing/gpsd-clients/gegps.1.en.html
[96]:https://gpsd.gitlab.io/gpsd/gpscat.html
[97]:https://manpages.ubuntu.com/manpages/lunar/en/man1/gpspipe.1.html
[98]:https://manpages.ubuntu.com/manpages/jammy/man1/gpxlogger.1.html
[99]:https://gpsd.gitlab.io/gpsd/troubleshooting.html
[100]:https://man.archlinux.org/man/gpsfake.1.en
[101]:https://systemd.io/
[102]:https://learn.adafruit.com/adafruit-ultimate-gps-hat-for-raspberry-pi/use-gpsd
[103]:https://www.satsignal.eu/raspberry-pi/UpdatingGPSD.html#64
[104]:https://forums.raspberrypi.com/viewtopic.php?t=138711
[105]:
[106]:
[107]:
[108]:
[109]:
[110]:

