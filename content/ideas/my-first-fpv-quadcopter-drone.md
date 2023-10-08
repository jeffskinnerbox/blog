<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/we-do-this-not-because-it-is-easy.jpg" title="U.S. President John F. Kennedy said this in his moon speech at Rice University in Houston, Texas, on September 12, 1962:

 We choose to go to the moon.  We choose to go to the moon in this decade and do the other things, not because they are easy, but because they are hard, because that goal will serve to organize and measure the best of our energies and skills, because that challenge is one that we are willing to accept, one we are unwilling to postpone, and one which we intend to win, and the others, too." align="center" width=500px height=375px>
</div>



-----


I got the itch to build & fly my own FPV quadcopter drone.
This came after I first built (and I continue to rebuild) a RC Car, which was in large part 3D printed.
It safe to say that my real desire was to 3D print & build a quadcopter,
but I felt it was too big of a first project.
The RC Car project is now done (well ... not completely but it's time to move on),
I wanted to turn my attention to the quadcopter.
I looked into 3D printed the quadcopter plans but quickly concluded
that just tuning a quadcopter flight controller for flight, learning how to fly it myself,
and then fly the drone with minimal crashes will be a significant challenge in itself.
I needed a way to pickup some basic skills without over committing myself in time, effort, and money.

The FPV quadcopter community have effectively solved this problem with the "[Tiny Whoop][15]".
This style of quadcopters are small enough to fly indoors safely but agile enough to be fast & aerobatic in the outdoors.
The have shrouded propellers so you can fly around people safely and can absorb many crashes.
There are several tiny whoop sizes,
typically measure in prop size (31mm, 2 prop up to 45mm, 3 prop)
and/or frame size (65mm to 80mm), and/or weight (28g to 34g),
and/or battery size (usually operate on 1S or 2S LiPo batteries).

An added benefit of the tiny whoops is their light weight.
The latest FAA rules requires all [Unmanned Aircraft Systems (UAS)][17] to be [FAA registered][18]
and equiped with [RemoteID][16] for any aircraft of 250 grams or more.
Tiny whoops are well under the 250g threshold.
Never the less, the rule for **operating** any UAS in the National Airspace System (NAS) is [14 CFR Part 107][07],
referred to as the Small UAS Rule.
The bottomline is that while my tiny whoop doesn't require a RemoteID nor FAA registration,
I must take The [Recreational UAS Safety Test (TRUST)][04] and carry proof of test passage when flying.

>**NOTE:** To understand what FAA rules apply to a light weight tiny whoop,
>the FAA has an online tool "[What Kind of Drone Flyer Are You?][08]"
>This tool points me to "[Fly under the rules for Recreational Flyers and Community Based Organizations][06]".
>This concerns the rules for recreational flying above the 250 gram threshold.

## My Quadcopter Selection
Tiny whoop's are often operated indoors,
and it is generally agreed that a 65mm tiny whoop is the best for indoor use.
Its crash resistant and least likely to break anything in your house.
If indoor racing is your objective, than a 65mm tiny whoop
(e.g. [Happymodel Mobula 6 1S 65mm](https://www.racedayquads.com/products/happymodel-bnf-mobula6-elrs-65mm-brushless-whoop-choose-rx)
[NewBeeDrone Hummingbird V3](https://www.youtube.com/watch?v=XzxtZYpigO0) might be best pick.

My main focus is on outdoor use, so more power and maneuverability is my goal.
I choose a slightly larger and more powerful quadcopter,
the 80mm [BetaFPV Meteor75 Pro 1S](https://betafpv.com/collections/brushless-series-except-hd/products/meteor75-pro-brushless-whoop-quadcopter)
([checkout this video][21] and this [review][23]).
It has analog FPV video system ([C03 FPV camera](https://betafpv.com/products/c03-fpv-micro-camera) and [M03 5.8GHz 350mW VTX](https://betafpv.com/products/m03-25-350mw-5-8g-vtx)),
[45mm 3-Blade  1.5mm shaft propellers](https://betafpv.com/collections/40mm-propellers/products/gemfan-45mm-2-blade-3-blade-propellers-1-5mm-shaft-4pcs?variant=40100902273158),
[BT 2.0 550mAh 1S LiPo battery](https://betafpv.com/collections/new-arrivals/products/bt2-0-550mah-1s-battery-4pcs),
[F4 1S 5A AIO Brushless Flight Controller](https://betafpv.com/collections/brushless-flight-controller/products/f4-1s-5a-aio-brushless-flight-controller-elrs-2-4g),
[22000KV 1102 brushless motors](https://betafpv.com/collections/brushless-motors/products/1102-13500kv-brushless-motors?variant=40162473902214),
[ExpressRLS controlled](https://www.expresslrs.org/),
whoop quadcopter kit from [BetaFPV](https://betafpv.com/).

* [The Best Tiny Whoops and Accessories | Micro Indoor FPV Drones](https://oscarliang.com/best-tiny-whoop/)

## Additional Equipment
To make my tiny whoop Meteor75 Pro quadcopter usable,
I need additional equipment and tools.
Primarily, this includes:

* Radio Controller - [RadioMaster Boxer](https://www.radiomasterrc.com/collections/boxer-1/products/boxer-radio-controller-m2)
    * [RadioMaster](https://www.radiomasterrc.com/)
    * [Edge TX](https://edgetx.org/)
    * [ExpressLRS](https://www.expresslrs.org/)
* Power for the Radio Controller - [Battery for RadioMaster Boxer](https://www.radiomasterrc.com/products/21700-5000mah-battery-for-tx16s-mkii)
* Power for the Quadcopter - [BetaFPV 550mAh 1S LiPo Batteries](https://www.getfpv.com/betafpv-550mah-1s-lipo-hv-battery-4pcs-bt2-0.html)
* Charger for Quadcopter Battries - [1S Battery Storage Charger and Discharger](https://viflydrone.com/products/vifly-whoopstor-6-ports-1s-battery-storage-charger-discharger)
* Setup & Tuning of the Quadcopter Flight Controller - [BetaFlight][19]

Conspicuously absent from this list are goggles ... "What's the point of [first person video (FPV)][20]", you say?!
There are hard choose and compromises that must be made with the selection of goggles.
Not least of which is the desire to pick goggles suitable for future (aka unknown) projects.
Getting a good pair of feature rich, quality goggles is a must, but given their expense, I don't want to make a hasty decision.
I'm going to go without goggles for now and focus on learn how to fly and tune a quadcopter.
This might inform me on what I ultimate want from my goggles,
but in any event, I'm taking the time to make sure I fell good about what how I'm spending my money.

## Anticipated Tuning and Modifications
I got several ideas from these sources about changes I would like to consider:

* [2023 Ultimate Guide to Tiny Whoops: Are you using the right stuff?](https://www.youtube.com/watch?v=lgeeR8TiuP0)
* [Best Tiny Whoop Drones & Parts](https://www.fpvknowitall.com/fpv-shopping-list-tiny-whoop/)

Specific ideas I want to try:

* Throttle Expo - [Adjusting Throttle Curve in Betaflight and EdgeTX: Tips for Smoother Throttle Control](https://oscarliang.com/throttle-curve/)
* Motor limiting - [Throttle Limit in Betaflight 3.4: Longer flights and cooler motors](https://flexrc.com/2018/07/12/throttle-limit-in-betaflight-3-4-longer-flights-and-cooler-motors/)
* More powerful motors - try 2600KV to 3200KV motors
* Singularity 5.8 VTX Antenna (Ultra-Short) - [TinyWhoop Store](https://www.tinywhoop.com/collections/antennas/products/singularity-rhcp-20mm-ufl-vtx-antenna)
* Crash Recovery - [Winning Whoop racers use Betaflight crash_recovery. Should you?](https://www.youtube.com/watch?v=5YyxIft9wKM&t=8s) vs Angle Mode - [Betaflight Angle Mode is about to get AWESOME! You can try it TODAY](https://www.youtube.com/watch?v=ILeLo1lWjBk)
* Turtle Mode - [How to setup TURTLE MODE in BETAFLIGHT 2022 (Tutorial)](https://www.youtube.com/watch?v=jibqPPc4I9o)
    * [This EdgeTX "custom curve" makes turtle mode even better!](https://www.youtube.com/watch?v=22ueY-bvGnI)

# Next Quadcopter Build
* 65mm Tiny Whoops - the classic FPV quadcopter used for indoor racing.
    * [802 19000kv Motors](https://www.amazon.com/19000KV-Brushless-Motors-SE0802-Snapper7/dp/B07J9QHJXF)
    * [Happymodel Bwhoop65 65mm](https://www.amazon.com/Happymodel-Bwhoop65-Brushless-Mobula6-Quadcopter/dp/B089N5Q94N)
    * [BETAFPV F4 1S Brushed Flight Controller](https://www.amazon.com/BETAFPV-Brushed-Flight-Controller-Receiver/dp/B07DMDZ1LH/)
    * [Gemfan 31mm Props 1219 3-Blade Prop](https://www.amazon.com/Gemfan-3-Blade-Propeller-0703-1103-Brushless/dp/B094VJTLHG/)
    * [BT2.0 300mAh 1S Battery (67mm long)](https://www.amazon.com/BETAFPV-Battery-Connector-Brushless-Meteor65/dp/B081C8LJHT/)
    * [BETAFPV BT2.0 Connector 55mm 22AWG](https://www.amazon.com/dp/B081C5RLJ9?th=1)
    * [AIO FPV video camera+transmitter+antenna combo](https://www.amazon.com/AKK-200mW-Switchable-600TVL-Camera/dp/B072V1F8V3/)
* 160mm 3" Ducted Prop Shendrones CineWhoop -
Cinewhoops are quadcopters specifically designed for capturing chrisp and stable video. They are smaller and safer than your 5” FPV quadcopter. They usually run 3” propellers that are protected in ducts that give them more lift and ability to hover in place.


### What Are Cinewhoops?
[What is a CineWhoop?](https://www.youtube.com/watch?v=lXhyc_qYT2Y)
Cinewhoops are drones specifically designed for capturing chrisp, stable, high-definition video that DJI drones can’t capture. They are small, stable and much safer than your 5” FPV drone. They usually run 3” propellers that are protected in ducts that give them more lift

* [What is a CineWhoop?](https://www.youtube.com/watch?v=lXhyc_qYT2Y)
* [Which is the Best Cinewhoop?](https://oscarliang.com/cinewhoop/)
* [Cinewhoops](https://dronenodes.com/cinewhoop-cinematic-fpv-drones/)
* [REVIEW: Renegade FPV's 'Slammed' Shendrones Squirt! - BEST Cinewhoop Drone of 2022!](https://www.youtube.com/watch?v=uu3r5VIPnhQ)
* [iFlight BumbleBee HD V3 3" Cinewhoop Frame Kit](https://www.getfpv.com/iflight-bumblebee-hd-v3-3-cinewhoop-frame-kit.html)
* [SHEN DRONES SQUIRT V2 3" CINEWHOOP FRAME - CARBON & HARDWARE ONLY (DUCTS SOLD SEPARATELY) - CHOOSE VERSION](https://pyrodrone.com/products/shen-drones-squirt-v2-3-cinewhoop-frame-carbon-hardware-only-ducts-sold-separately-choose-version)
* [Shen Drones Squirt V2 3" Cinewhoop w/ Ducts, Variable Angle Hero 7/8 Mount - Analog/DJI](https://www.getfpv.com/shen-drones-squirt-v2-3-cinewhoop-w-variable-angle-hero-7-8-mount-analog-dji.html)
* [Thingiverse: Shendrones Squirt Parts](https://www.thingiverse.com/search?q=Shendrones+Squirt&page=1&type=things&sort=relevant)

* [How to Build an FPV Drone (Cinewhoop Squirt V2)](https://www.youtube.com/watch?v=f4zVFpEBHUY)
* [How To Build a Cinewhoop | Squirt V2.1 FPV Drone](https://www.youtube.com/watch?v=QHZHjqiaLZU)
* [How to build a CINEWHOOP (ducted HD FPV drone) feat. Shendrones Squirt V2 - BUILD LOG](https://www.youtube.com/watch?v=1dMOtOmZGeA)

* [2023 Freestyle FPV Drone Build For Total Beginners](https://www.youtube.com/playlist?list=PLwoDb7WF6c8l24IM83wIS94XzhuMVC2gx)

### How Ducts Work?
* [How Cinewhoop ducts work and when you should use them](https://www.youtube.com/watch?v=7f2DZIC8a1k)


-----



* [Pilot's Handbook of Aeronautical Knowledge](https://www.faa.gov/sites/faa.gov/files/uas/recreational_fliers/where_can_i_fly/airspace_101/pilot_handbook.pdf)
* [Flowstate: The FPV Drone Documentary](https://www.youtube.com/watch?v=6-yhHfuw1kI)

 EdgeTX - EdgeTX is an open-source firmware for remote control transmitters used in hobbyist RC (radio-controlled) flying and other activities. It is highly customizable, allowing users to configure their transmitters and adjust settings to suit their individual preferences and specific needs.
 Crossfire - [TBS Crossfire Beginner Guide (2023 Update)](https://www.youtube.com/watch?v=Ypn71lIu8l8)



# Great Sources of FPV Quadcopter Information
* Chris Rosser's [website](https://www.cncdrones.com/) and [videos](https://www.youtube.com/@ChrisRosser) for drone engineering & physics
* [MiniQuad Test Bench](https://www.miniquadtestbench.com/) for motor and ESC testing
* Joshua Bardwell's [website](https://www.fpvknowitall.com/) and [videos](https://www.youtube.com/@JoshuaBardwell)
* Oscar Liang's [website](https://oscarliang.com/) and [videos](https://www.youtube.com/@OscarLiang1)
* [rotorbuilds](https://rotorbuilds.com/)
* [Drone Nodes](https://dronenodes.com/how-to-build-a-drone/)
* [Pilot Institute](https://pilotinstitute.com/)
* FPV Freedom Coalition

## Detail Builds
* [2023 Freestyle FPV Drone Build For Total Beginners](https://www.youtube.com/playlist?list=PLwoDb7WF6c8l24IM83wIS94XzhuMVC2gx)





# Betaflight and Emuflight
From Emuflight Github Site:
_EmuFlight differs from Betaflight in flight code, methodology and purpose. Hardware support and general setup between EmuFlight and Betaflight continues to be near identical. EmuFlight stays up to date with the latest Betaflight merging almost all code changes, the main differences being related to flight code.  Due to the small development team of EmuFlight we don’t have the development resources that Betaflight does, and as a result we share most our code and will improve as Betaflight improves. At some point in the future EmuFlight may deviate from Betaflight to a larger extent._

* [Emuflight vs Betaflight](https://www.youtube.com/watch?v=Ad_di2L5PM8)
* [Joshua Bardwell](https://www.youtube.com/@JoshuaBardwell)
* [Betaflight 4.3 Complete Walkthrough](https://www.youtube.com/watch?v=LkBWRiEGKTI&list=PLwoDb7WF6c8nT4jjsE4VENEmwu9x8zDiE)
* [My favorite Tiny Whoop so far: Rotor Riot Vision40](https://www.youtube.com/watch?v=2KoYOt1MmR8)
* [1s VS 2s - Which Should YOU Buy?!](https://www.youtube.com/watch?v=ZK-QAzY6nu4)

# Beginers Guide FPV Drone
* [Getting Started with FPV](https://fpvfc.org/getting-started-with-fpv)
* [How to Start Flying FPV DRONES in 2023](https://www.youtube.com/watch?v=GdkeR-66Ock)
* [The Idiot's Guide to Making a DIY Drone! (I am the Idiot)](https://www.youtube.com/watch?v=DeSDjjicGWY)
* [First FPV Drone Build? Don't Make These Mistakes](https://www.youtube.com/watch?v=frGircHfuWU)
* [I Built an FPV Drone](https://www.youtube.com/watch?v=Ll_WNair6dA)
* [FPV Drone Bundles at ANY PRICE! (2021 Beginner's Guide)](https://www.youtube.com/watch?v=DZcWSK4vozQ&t=0s)
* 3 years old - [An FPV Beginner's Guide: What I Learned When Getting Started](https://www.youtube.com/watch?v=DLJHdM4-LuI)
* [FPV Drones – How to start in 2023? DJI O3](https://www.youtube.com/watch?v=YJsnMCcjSbA)
* [Ultimate Beginners Guide to Building A FPV Freestyle Drone](https://www.youtube.com/watch?v=5ed6y2rgaq8)
* [FPV Drones – How to start in 2023? DJI O3](https://www.youtube.com/watch?v=YJsnMCcjSbA)

# What FPV Stores for Parts?
GetFPV
Pyrodrone
RaceDayQuads
OscarLiang
[rotobuilds: FPV Part list and Build Logs](https://rotorbuilds.com/)

# Radio Transmitter / Controller
Sometimes called a radio transmitter, or just radio, or just transmitter, or just controller.
RadioMaster Boxer - $160
Radiomaster - RadioMaster TX16S - $200 / RadioMaster TX12 - $100

* [How to Setup Radiomaster Boxer | Upgrades, Tips and Tricks](https://oscarliang.com/setup-radiomaster-boxer/)

* [Choosing the Best Radio Transmitter for Your FPV Drone: A Beginner’s Guide](https://oscarliang.com/radio-transmitter/)
* In 2022 - [How To Buy Your First FPV Controller](https://www.youtube.com/watch?v=wpZ8xKIaNgs)
* In 2023 - [How To Buy Your FIRST FPV Controller (2023)](https://www.youtube.com/watch?v=4mBPew9HIfw)
* [Why I Fly ExpressLRS, Not Crossfire](https://www.youtube.com/watch?v=Wy9SmlijVOI)
* [I can't believe how good this radio feels // RADIOMASTER BOXER REVIEW](https://www.youtube.com/watch?v=5Fi9csa-wP8)

* [Affordable FPV Controllers That DON’T SUCK!](https://www.youtube.com/watch?v=Az5G4nq8F3M)
* [Cheap vs. Expensive FPV Controllers - What's the Difference?](https://www.youtube.com/watch?v=SrN6ps4NM10)
* [2023 BEST Radios for Fpv Drones - BUYER'S GUIDE](https://www.youtube.com/watch?v=KOYla-wqFYg)

# FPV Simulators
Orqa FPV.Skydive
VelociDrone FPV Racing Simulator
LiftOff

* [Best PC FPV Simulator // WE TRIED THEM ALL](https://www.youtube.com/watch?v=I7lUTEJM62g)

# FPV Goggles
Analog is the oldest, most affordable, and most prevalent technology, it’s available in 5.8GHz, 2.4GHz and 1.2/1.3GHz. In contrast, digital technology, which offers superior image quality, is newer and gaining popularity. Digital is expected to become mainstream in the near future.
This decades-old technology is not proprietary to any specific company, allowing anyone to create components for the system. Consequently, it is the most widely available system on the market.
Until mid-2019, analog was the only FPV option. There are dozens of cameras, video transmitters, and goggles from multiple manufacturers, all compatible with each other. Analog is the most affordable way to enter the world of FPV.

Price for an analog FPV solution:
* Camera: $15 – $40
* Video Transmitter (VTX): $15 – $40
* FPV Goggles: $80 – $500

Currently there are three digital FPV systems available for FPV drones, all of them are 5.8GHz systems, and none of the them are cross-compatible with each other as they are all proprietary systems.
Currently the available digital FPV system are: DJI, HDZero and Walksnail Avatar

FPS Systems Available
* Analog - analog camera, good for micro quads since light and low power consumption
* DJI V2 & DJI O3 - typically too heavy & power hungry for small quads
* Walksnail (FatShark Dominator)
* HDZero - HDZero camera, you can use to upgrade analog goggles

* [Choosing the Best VTX (Video Transmitter) for FPV Drones – The Ultimate Beginner Guide](https://oscarliang.com/video-transmitter/)
* [Ultimate FPV Goggles Guide: Find the Best FPV Headset for Every FPV System](https://oscarliang.com/fpv-goggles/#Digital-vs-Analog-Choosing-Your-Ideal-FPV-System)
* [Which FPV System Should You Buy in 2023? Analog, DJI, HDZero, Walksnail Avatar](https://oscarliang.com/fpv-system/)
* [Ranking DJI 03 vs HD-Zero, WalkSnail, Analog from WORST to BEST](https://www.youtube.com/watch?v=nxMSTc8lZ38)
* [Best FPV Goggle 2023 Buyer's Guide // DJI v. HDZERO v. WALKSNAIL v. ANALOG](https://www.youtube.com/watch?v=TMOeIQ4VRX4&t=77s)
* [HDZero vs Analog vs DJI - Penetration & Image Quality Test - small bando](https://www.youtube.com/watch?v=cdA7dYMcdmo)
* [Cheap vs. Expensive FPV Goggles - What's the Difference??](https://www.youtube.com/watch?v=oOEbygcWk-w)
* [The best FPV goggle for almost everybody (except DJI) // HDZERO GOGGLE REVIEW](https://www.youtube.com/watch?v=TPnGVad9Cm8)
* [ImmersionRC PowerPlay DVR - better than using the FatShark DVR?](https://www.youtube.com/watch?v=Vyr_1_ylpu4)


## SKYZONE
* SKYZONE KY04X $529 - [Skyzone 04X Review - The Best For Analog & HDZero For Now](https://www.youtube.com/watch?v=wzc8U-jnxmI)
    * [SkyzoneFPV Steadyview Fusion Board V3.3 🧮 // Did They Fix Mix Mode?](https://www.youtube.com/watch?v=ocFtdzqnmqI)
* SKYZONE SKY04O $429 - [SKYZONE SKY04O FPV Goggle with OLED Screen and 60FPS DVR Steadyview Receiver](https://www.skyzonefpv.com/products/skyzone-sky04o-fpv-goggle-with-oled-screen-and-60fps-dvr-steadyview-receiver)
* SKYZONE Ground Station - [Skyzone Steadyview X Review](https://www.youtube.com/watch?v=IMRyGvRCT2o)

## HDZero
* [HDZero FPV Goggles Review - Best FPV Goggle Available Today?](https://www.youtube.com/watch?v=HTBcYi6Zokw)
* [$495 for HDZero Goggles, They Are Seriously IMPRESSIVE!](https://www.youtube.com/watch?v=ajCuxmh_Opc)
* [This Goggle WINS Drone Racing // HDZero Goggles + Nano90 Camera Full Review + Testing](https://www.youtube.com/watch?v=GW6gNMK7Ah0)
* [HDZero Goggle Review](https://atxairborne.com/hdzero/hdzero-goggle/hdzero-goggle-review/)
    * [Recommended Accessories for the HDZero Goggle](https://atxairborne.com/hdzero/hdzero-goggle/recommended-accessories-for-the-hdzero-goggle/)
* [HDZero Goggles with the Walksnail VRX! : 60fps and 100fps Test](https://www.youtube.com/watch?v=at11dEuJyGo)



# VR Headset
* [Open Source VR Headset For $200](https://hackaday.com/2020/09/13/open-source-vr-headset-for-200/)
* [AKK 5.8G RC832 Mini FPV Receiver Double-Screen Display for FPV Quadcopter Drone](https://www.amazon.com/gp/product/B01FXFZ0NS)
* [AKK A2 5.8Ghz 200mW FPV Transmitter Raceband 600TVL 1/4 Cmos Mini FPV Micro AIO Camera with Clover Antenna for FPV Drone](https://www.amazon.com/gp/product/B06VSW41LN)

# Optical Flow LIDAR Sensor
This is a sensor to enable position hold and altitude hold on a drone.
What Is Optical Flow? Optical flow is the distribution of the apparent velocities of objects in an image. By estimating optical flow between video frames, you can measure the velocities of objects in the video.

* [Beginners Guide To Optical Flow Sensor with LIDAR on Drone | MATEKSYS 3901-L0X Optical Flow & LIDAR](https://www.youtube.com/watch?v=rrZgKg54QgE)
* [PX4FLOW - Optical Flow Sensor](https://ardupilot.org/copter/docs/common-px4flow-overview.html)

# Radio Controller
## Radio Control Link Protocols
What are all the common radio control (RC) protocols in FPV,
and how they fit into the communication system in an FPV drone,
and what their differences are.

900 MHz - bandwidth is small so 5 to 8 pilots in the air
2.4 GHz - bandwidth is much larger so it can support 50 ... where you want to be


* ACCST - one of the first and showing its age
* ACCESS - FrSky ecosystem only
* FrSky R9 - 900MHz, FrSky ecosystem only, but R9 hardware will run ExpressLRS
* TBS Crossfire - 900MHz and up to 2 Watts, outsanding range, stable and good performance but not the best latency
* Ghost - 2.4 GHz, you can trade-off range & latency, TBS Crossfile range is superior
* TBS Tracer - 2.4 GHz, TBS competitive response to Ghost, excellent latency at the expense of range so great for racers
* [ExpresLRS](https://www.expresslrs.org/) - 900 MHz & 2.4 GHz, best combination of range & latency

Sources:
* [Crossfire vs. Tracer vs. Ghost vs. ExpressLRS vs. R9 vs. ACCESS vs. ACCST | RC control link shootout](https://www.youtube.com/watch?v=a8cy5BK5SbU)
* [FPV Protocols Explained (CRSF, SBUS, DSHOT, ACCST, PPM, PWM and more)](https://oscarliang.com/rc-protocols/)

### ExpressLRS
[ExpressLRS (ELRS)](https://www.expresslrs.org/) is an open source project focusing on developing a radio control (RC) link. The link is primarly designed for first-person view (FPV) crafts (e.g Multicopters, Planes). ELRS aims to provide the best completely open source, high refresh radio control link, minimising latency while maximising range. A vast range of hardware in both 900 Mhz and 2.4 GHz frequencies is available.

ExpressLRS vs FrSky

ExpressLRS is an open source,  high perfromance, low lantancy long range link.

* [Intro to Express LRS • For ELRS Novices](https://www.youtube.com/watch?v=AdgBoYJNI0M)
* [ExpressLRS Facts You Need To Know](https://www.youtube.com/watch?v=DUzgdlZrH2g)
* [How to setup your Radio for ExpressLRS | ExpressLRS Setup Guide](https://www.youtube.com/watch?v=M45lx3yKK_4)
* [How to setup the BetaFPV Lite Radio SE ELRS | | ExpressLRS V1](https://www.youtube.com/watch?v=W0NWdmL_L0k)
* [ExpressLRS definitive getting started guide](https://www.youtube.com/watch?v=J3Hg2f7RL1A)
* [Easiest Way To Flash and Bind ExpressLRS!](https://www.youtube.com/watch?v=MFFUsN9ZHSU)
* [SPI-based ExpressLRS receivers are the worst](https://www.youtube.com/watch?v=G1dK7nk5Ds4)
* [Discover the Power (annoyance) of ExpressLRS Model Match](https://www.youtube.com/watch?v=3S6eUWCqvUY)
* [The next leap forward in ExpressLRS performance: GEMINI](https://www.youtube.com/watch?v=PZVUGKmBD24)

* [Which ExpressLRS Receiver Should I Buy? - FPV Questions](https://www.youtube.com/watch?v=cOp5Jdms7xQ)
* [Which ExpressLRS module should you get?](https://www.youtube.com/watch?v=JGS7Azztthw)
* [Ultra-tiny receiver too weak for daily use? Nah. (ExpressLRS HappyModel EP2)](https://www.youtube.com/watch?v=Z8C2ItQzEx4)

### Whats the Differance between ELRS vs 4-in-1 vs MPM CC2500?
In the RadioMaster lineup, you can get 3 different modules: Ranger, Micro, Nano.
The Ranger and Micro fit into a JR Bay.
A Nano fits into a Nano Bay.
https://forum.flitetest.com/index.php?threads/whats-the-difference-between-4in1-and-cc2500.71435/

| Manufacturer           |  RF Chip  |      Example Protocols                        |
|:----------------------:|:---------:|:---------------------------------------------:|
| Cyprus Semiconductor   | CYRF6936  |   DSM/DSMX, Walkera Devo, J6Pro               |
| Texas Instriments      | CC2500    |   FrSky, Futaba SFHHS                         |
| Amiccom                | A7105     |   FlySky, FlySky AFHDS2A, Hubsan              |
| Nordic Semiconductor   | NR24L01   |   HiSky, Syma, ASSAN, and most Chinese models |

[pascallanger/DIY-Multiprotocol-TX-Module](https://github.com/pascallanger/DIY-Multiprotocol-TX-Module)

## Radio Control Operating Systems
EdgeTX -
OpenTX -

Sources:
* [How to upgrade to EdgeTX (What's EdgeTX???)](https://www.youtube.com/watch?v=L-j_mJhiJp8)
* [Six reasons why you should switch to EdgeTX today (I've switched)](https://www.youtube.com/watch?v=nAK7UNYSRMY)

### EdgeTX
* [EdgeTX 2.5 means it's time to switch away from OpenTX. Here's how.](https://www.youtube.com/watch?v=shmse1VBiaA)
* [How-To Convert from OpenTX to EdgeTX MASTER CLASS • 100% Works](https://www.youtube.com/watch?v=0WnpfE78-KU)

### OpenTX
OpenTX is open source firmware for RC radio transmitters. The firmware is highly configurable and brings much more features than found in traditional radios.

Sources:
* [OpenTX](https://www.open-tx.org/)
* [Everybody should be using these FPV Lua Scripts](https://www.youtube.com/watch?v=RCS72GVR0gs)

# Drones
Drones are defined as "an unmanned aircraft or ship guided by remote control or onboard computers",
and have been around for over [100 hundred years][01].
These remote-controlled flying crafts have become an increasingly popular project to work on,
including building and racing them.
[FPV Drone Racing][02] has become a popular sport and it even has its own league.
The Drone Racing League was created in 2015 and features racing with custom-built drones that traveling over 100 MPH.

## Should I Build or Buy?
For me, there is an obvious choose.
I want to build my drone for the challenge, learning opportunity, and maximum flexibility of design.

## What is Your Mission?
I have no specific task I want my drone to perform,
at least not this version.
I just want the challenge and learn some new things.
I do have some very loose ideas about what I may do next,
but it requires this build to go successfully so I can build on it.

I don't want a drone that has significant lifting capacity.
The more you can lift, the more the weight goes up, and more expensive the components used to build it.
Never the less, out fit it with add-on latter,
like a camera, sensors, or additional communication capabilities would be nice.
So having a drone design that can take on more weight is something to consider.

Some thoughts:
* Autonomous Vehicle Competition - https://avc.sparkfun.com/
* High School Autonomous Vehicle Competition - https://www.anl.gov/education/high-school-autonomous-vehicle-competition
* Drone Racing
* Drone Combat - https://www.amazon.com/battle-drone/s?k=battle+drone

### What Size Drone?
Mini / Micro -  EMAX Tiny Hawk - https://emax-usa.com/collections/tinyhawk-series
Tiny Whoop
3" (aka 3 inch) VS. 5" (aka 5 inch) - [3" vs 5" Freestyle](https://www.youtube.com/watch?v=sMsWprbCPUg&t=199s)

### Work or Play?
This is all play, but in time, maybe what I create could be useful for me or to others.

### What Size Drone?
Some people decide that buying a Whoop class drone ( something small enough to fit in the palm of your hand) is the best way to get started due to their size, ability to survive crashes, and can be flown indoors.

* [Building a Tiny Whoop Micro Drone](https://oscarliang.com/building-tiny-whoop-micro-drone/)
* [TINY WHOOP TUTORIALS](https://www.tinywhoop.com/pages/tutorials)
* [How to Build a Tiny Whoop! a Super Fast Micro FPV Quadcopter](https://www.instructables.com/How-to-Build-a-Tiny-Whoop-a-Super-Fast-Micro-Fpv-Q/)
* [Whoopee – Inductrix “Tiny Whoop” Frame for 8.5mm Motors](https://oscarliang.com/whoopee-micro-frame/)
* [Whoopee - Tiny Whoop alike frame for 8.5mm Motors](https://www.thingiverse.com/thing:1700311)
* [FT Tiny Whoop Brushless Kit](https://store.flitetest.com/ft-tiny-whoop-brushless-kit/)
* [My favorite Tiny Whoop so far: Rotor Riot Vision40](https://www.youtube.com/watch?v=2KoYOt1MmR8)
    * [Vision40 40mm HD Built & Tuned Drone - 1S or 2S](https://rotorriot.com/products/vision40-40mm-hd-built-tuned-drone)
* [The most advanced 65mm Whoop I've ever seen | HAPPYMODEL MOBEETLE6 FULL REVIEW](https://www.youtube.com/watch?v=1ipOgKfwOrk)
* [Best Tiny Whoop Drones & Parts](https://www.fpvknowitall.com/fpv-shopping-list-tiny-whoop/)

* [The best low-budget FPV drone kit for beginners | EMAX EZ-PILOT PRO](https://www.youtube.com/watch?v=pxeQZ15DX5Q)

* [Micro Quadcopter 3D Prints](https://www.thingiverse.com/thing:1221911/remixes)
https://www.google.com/search?q=5+inch+class+drone&sca_esv=568551326&sxsrf=AM9HkKn1RQ0jZ67hO7Q4wDekxGe-Zxyhtw%3A1695752100864&ei=pB8TZaWVNMWgiLMP1c6sQA&ved=0ahUKEwil9-Ts8MiBAxVFEGIAHVUnCwgQ4dUDCBA&uact=5&oq=5+inch+class+drone&gs_lp=Egxnd3Mtd2l6LXNlcnAiEjUgaW5jaCBjbGFzcyBkcm9uZTIFECEYoAEyCBAhGBYYHhgdMggQIRgWGB4YHTIIECEYFhgeGB0yCBAhGBYYHhgdMggQIRgWGB4YHTIIECEYFhgeGB0yCBAhGBYYHhgdMggQIRgWGB4YHTIIECEYFhgeGB1IuidQngpYvxVwAHgCkAEAmAFooAG9BKoBAzUuMbgBA8gBAPgBAcICBBAAGEfCAgUQABiABMICBhAAGBYYHsICBRAhGKsCwgIHECEYoAEYCuIDBBgAIEGIBgGQBgg&sclient=gws-wiz-serp

Others prefer to jump right in to the 5" FPV racing quadcopters class and build their own.
* [Building the Ultimate 5-inch FPV Freestyle Drone](https://www.youtube.com/watch?v=XB6b0HrDGeA)
* [How to Build 5inch Freestyle FPV Drone in 2022 - For Professionals](https://www.youtube.com/watch?v=9mcIlWwHPJI)

### What Are Cinewhoops?
[What is a CineWhoop?](https://www.youtube.com/watch?v=lXhyc_qYT2Y)
Cinewhoops are drones specifically designed for capturing chrisp, stable, high-definition video that DJI drones can’t capture. They are small, stable and much safer than your 5” FPV drone. They usually run 3” propellers that are protected in ducts that give them more lift

* [What is a CineWhoop?](https://www.youtube.com/watch?v=lXhyc_qYT2Y)
* [Which is the Best Cinewhoop?](https://oscarliang.com/cinewhoop/)
* [Cinewhoops](https://dronenodes.com/cinewhoop-cinematic-fpv-drones/)
* [REVIEW: Renegade FPV's 'Slammed' Shendrones Squirt! - BEST Cinewhoop Drone of 2022!](https://www.youtube.com/watch?v=uu3r5VIPnhQ)
* [iFlight BumbleBee HD V3 3" Cinewhoop Frame Kit](https://www.getfpv.com/iflight-bumblebee-hd-v3-3-cinewhoop-frame-kit.html)
* [SHEN DRONES SQUIRT V2 3" CINEWHOOP FRAME - CARBON & HARDWARE ONLY (DUCTS SOLD SEPARATELY) - CHOOSE VERSION](https://pyrodrone.com/products/shen-drones-squirt-v2-3-cinewhoop-frame-carbon-hardware-only-ducts-sold-separately-choose-version)
* [Shen Drones Squirt V2 3" Cinewhoop w/ Ducts, Variable Angle Hero 7/8 Mount - Analog/DJI](https://www.getfpv.com/shen-drones-squirt-v2-3-cinewhoop-w-variable-angle-hero-7-8-mount-analog-dji.html)
* [Thingiverse: Shendrones Squirt Parts](https://www.thingiverse.com/search?q=Shendrones+Squirt&page=1&type=things&sort=relevant)

* [How to Build an FPV Drone (Cinewhoop Squirt V2)](https://www.youtube.com/watch?v=f4zVFpEBHUY)
* [How To Build a Cinewhoop | Squirt V2.1 FPV Drone](https://www.youtube.com/watch?v=QHZHjqiaLZU)
* [How to build a CINEWHOOP (ducted HD FPV drone) feat. Shendrones Squirt V2 - BUILD LOG](https://www.youtube.com/watch?v=1dMOtOmZGeA)

* [2023 Freestyle FPV Drone Build For Total Beginners](https://www.youtube.com/playlist?list=PLwoDb7WF6c8l24IM83wIS94XzhuMVC2gx)

### How Ducts Work?
* [How Cinewhoop ducts work and when you should use them](https://www.youtube.com/watch?v=7f2DZIC8a1k)

### Indoor or Outside?
What Is Optical Flow? Optical flow is the distribution of the apparent velocities of objects in an image. By estimating optical flow between video frames, you can measure the velocities of objects in the video.
* [How to Fly a Drone Indoors](https://dojofordrones.com/optical-flow-project/)
* [PX4FLOW - Optical Flow Sensor](https://ardupilot.org/copter/docs/common-px4flow-overview.html)



-------



# FPV Advocacy Groups
* [Academy Of Model Aeronautics (AMA)](https://www.modelaircraft.org/) - AMA is a nonprofit community of enthusiasts who come together to celebrate model aviation.
* [FPV Freedom Coalition](https://fpvfc.org/) - The FPV Freedom Coalition was created to advocate for recreational FPV pilots through education and safety guidelines to protect our access to ample airspace. Through this, we protect the ability of FPV pilots to fly and to do so safely, armed with the knowledge that they need to interact with the general public in a positive and respectful way. Together, we seek to unite the community into a single voice through which our concerns and needs can be heard.
* [Flite Test Community Association (FTCA)](https://ftca.flitetest.com/) - FTCA is designed to be the hub where the people identifying with the community can rally together to promote the future of model aviation. Our vision is simple, we want to bring hope for the future of the hobby.
* [Pilot Institute](https://pilotinstitute.com/) - The Pilot Institute have helped over 250,000 people become airplane and drone pilots. Their courses are designed by industry experts to help you pass FAA tests for s starting a drone business or learning to fly.

* [Should you join the AMA? What about the FPV Freedom Coalition (Dave Messina Interview)](https://www.youtube.com/watch?v=4SQgqLSpNEM)

# Where can I Find Local FRIA Sites?
Where can I find a [FAA-Recognized Identification Areas (FRIAs)][11] sites?
While the FAA promises to maintain a [list of FAA approved FRIA sites][22], they appear to be struggling to keep it up to date.
A potentially better alternative is to search the [AMA's list of FRIA Sites](https://www.modelaircraft.org/fria-flying-sites)
(or using "search" at [AMA Club Flying Site](https://www.modelaircraft.org/club-finder)).
Another possibility are school based organizations like [STEM+C sites](https://stemplusc.org/stemc-cbo/)

# What Are My Local FRIA Sites?
Make sure all your aircraft over 250gm have you name, AMA number,and FAA number are
visible on the outside  of your aircraft, and obey the 400 ft altitude limit for flying within the
Washington DC area and the National Capital Region Special Flight Rules Area (SFRA).

* [Loudoun County Aeromodelers Association (LCAA)](https://www.modelaircraft.org/club/loudoun-county-aeromodelers-association)
* [DCRC Club](https://www.modelaircraft.org/club/dcrc-club)
* [Plane Crazy R/Cers](https://www.modelaircraft.org/club/plane-crazy-rcers)



-------



# FAA Requlations / Where Can I Fly?
The legal flying space and FAA direction can be confusing, and frankly, are evolving.

## What About FAA Registration?
Anyone flying a drone is responsible for flying within FAA guidelines and regulations.
That means it is up to you as a drone pilot to know the Rules of the Sky, and where it is and is not safe to fly.

There are 3 ways how drone pilots can operate their aircraft:

1. Operate a Standard Remote ID Drone. Such a drone has built-in Broadcast Remote ID functionality and can transmit identification and location information of the drone and control station according to the FAA requirements.
2. Pilots of other drones, older or custom, must use a Broadcast Remote ID device attached to the drone chassis or one that comes in the form of an upgrade integrated with the drone. These drones must be operated within a visual line of contact with their pilots (VLOS) and transmit Broadcast Remote ID according to FAA requirements.
3. UAS operations without Remote ID equipment are only allowed at [FAA-Recognized Identification Areas (FRIAs)][11]. Community-based organizations or schools run these areas.

No FAA or Remote ID Registration

You must use the paper (N-number) registration process if:
* recreational drones/unmanned aircraft that weigh 0.55 pounds (250 grams) or more and all drones flying under Part 107.

* [Getting Started: Congratulations on your new drone!](https://www.faa.gov/uas/getting_started)
* [Federal Aviation Administration (FAA): FAADroneZone][09]
* [Mobile App: B4UFLY by Aloft](https://play.google.com/store/apps/details?id=gov.faa.b4ufly2&form=MY01SV&OCID=MY01SV)
* [Web App: B4UFLY by Aloft](https://b4ufly.aloft.ai)
* [Mobile App: Drone Scanner](https://play.google.com/store/apps/details?id=cz.dronetag.dronescanner&hl=en_US&gl=US)
* [First Person View Freedon Coalition (FPVFC)](https://fpvfc.org/)
Dronescanner
OpenDroneID

## What About Global Registration?
This database is comprised of a country directory with summaries and/or links to national drone laws. The objective is to provide humanitarian and non-humanitarian actors with a database of relevant national regulations, additional resources, and links to original regulatory documents to ensure that drones are deployed safely and in compliance with national regulations.
* [Global Drone Regulations Database](https://droneregulations.info/)

## What is Remote ID?
* [What is Remote ID?](https://drone-remote-id.com/)
* [RemoteID: Fight It? Ignore It? Comply with it?! Turns out it doesn't matter.](https://www.youtube.com/watch?v=Kt_uEgF5ikE&t=0s)
* [TOP 18 Remote ID for Drones Questions ANSWERED -LIVE with the FAA](https://www.youtube.com/watch?v=_GkvNlRYtqc)

* [A RemoteID module. Made by RC pilots. For RC pilots // FLITE TEST EZ ID](https://www.youtube.com/watch?v=l-gT53DdNHE)

In the USA, March 16, 2024 (originally September 16, 2023):
All drone pilots must meet the operating requirements of Part 89. For most, this will mean:
Flying a drone with Remote ID capability (Standard Remote ID Drone)
Equipping a non-Standard Remote ID drone with an Remote ID broadcast module (add-on device)
Flying within FRIA (learn more about FRIA here)

The only exception is using non-commercial drones below 249 grams (0.55 lb). Remote ID for these “small” drones is only required if the drone is operated under rules that require registration, such as Part 107.

### Can I Build My Own Remote ID?
* [RemoteID Cloaking Device How-To! Spoofer generates fake RemoteID signatures!](https://www.youtube.com/watch?v=Q8jn_6EmYxE)
* [RIDS - Remote ID Spoofer](https://github.com/jjshoots/RemoteIDSpoofer)

### What Must Be Done for FAA Compliance?
If you drone is less than 0.55 pounds, there are no regulations.
However, in order to fly drone over 0.55 pounds, there are FAA rules you must complie with.
The rule for operating unmanned aircraft systems (UAS) or drones under 55 pounds
in the National Airspace System (NAS) is [14 CFR Part 107][07],
referred to as the Small UAS Rule.
To understand what FAA rules apply to your drone,
the FAA has an online tool "[What Kind of Drone Flyer Are You?][08]"
This tool points me to "[Fly under the rules for Recreational Flyers and Community Based Organizations][06]".

However, if you want to fly a drone for purely recreational purposes,
there is a limited statutory exception ("carve out") that provides a basic set of requirements.
What must you do:

* **Take the TRUST exam** -
You must obtain a Remote Pilot Certificate (TRUST) from the FAA.
This certificate demonstrates that you understand the regulations, operating requirements, and procedures for safely flying drones.
* **Register your drone** -
* **Use Remote ID** -
* **Use the B4UFLY mobile app** -

https://www.youtube.com/watch?v=DmUryg09OKQ
Rule 1: Fly Strictly for Recreational Purposes (4:11)
Rule 2: Community Based Organization Guidelines (6:11)
Rule 3: Maintain Visual Line of Sight (7:06)
Rule 4: Do Not Interfere (8:21)
Rule 5/6: Get Authorization (8:54)
Rule 7: TRUST Certification (10:01)
Rule 8: Register Your Drone (11:06) .................... free registration stickers - https://pilotinstitute.com/free/
Rule 9: Don't Do Dangerous Operations (12:23)

That is it.
Below are some of details to address these three tasks.

### What is B4UFLY?
B4UFLY can notify a drone pilot if the FAA has restrict access to certain volumes of airspace
where drones or other aircraft are not permitted to fly without special permission.
Drone pilots should be familiar with:

* **Prohibited Areas** Prohibited area. A prohibited area is airspace within which no person may operate an aircraft without the permission of the using agency.
* **Restricted Areas** A restricted area is airspace within which the flight of aircraft, while not wholly prohibited, is subject to restriction. Restricted areas are designated when determined necessary to confine or segregate activities considered hazardous to nonparticipating aircraft.
* **Temporary Flight Restrictions (TFRs)** TFRs are defined areas of airspace where the FAA limits aircraft operations because of:
    * Temporary hazardous conditions, such as a wildfire, hurricane, or chemical spill.
    * A security-related event, such as the United Nations General Assembly.
    * Other special situations, like VIP movement.

* [Operating Restrictions](https://www.faa.gov/uas/getting_started/where_can_i_fly/airspace_restrictions/tfr)
* [Web App: B4UFLY by Aloft](https://b4ufly.aloft.ai)
* [B4UFLY Check the Map Episode 1: Drone Operations Near Small Airports in Uncontrolled Airspace](https://www.youtube.com/watch?v=74hO2IgijG0)
* [B4UFLY Check the Map Episode 2 Beginner’s Guide to Getting Your Drone Off the Ground On Demand](https://www.youtube.com/watch?v=DmUryg09OKQ)
* [B4UFLY Check the Map Part 3: Restricted Airspaces Webinar On-Demand](https://www.youtube.com/watch?v=XZ_oMYGr7Uo)
* [B4UFLY & LAANC Tutorials](https://www.youtube.com/watch?v=bEFuIpC9lTk&list=PLghwttwDCA46RbCv6Ry_KU0Y5hmc4v4Hg)

### What is LAANC?
* [LAANC Made Easy - How obtain authorization to fly drones in FAA controlled airspace](https://www.youtube.com/watch?v=dT6dwhw7aZs)
### What is Notify & Fly?

### The Recreational UAS Safety Test (TRUST)
Anyone flying their drone in the United States for recreational reasons needs to
pass [The Recreational UAS Safety Test (TRUST)][04] exam to legally fly.
The exam is online, takes about 30 minutes, and is free of charge.
You must download and print your certificate immediately upon finishing.
There are multiple [approved Test Administrators][05] to provide TRUST as an online test.
While flying and asked by law enforcement officers,
you must present a copy of your certificate.
If you lose your certificate, you will need to re-take the TRUST exam.

To pass the TRUST exam, you need to understand recreational flying requirements.
Visit the FAA's Recreational Flyers page to [learn about rules for recreational flyers][06].
Download the FAA's B4UFLY mobile app for more recreational drone flying resources.

* [TRUST Exam: Pilot Institue](https://trust.pilotinstitute.com/)

### Drone FAA Registration
Regulations DO apply to ALL model aircraft, even those under .55 pounds.
There is no lower weight limit exemption.
If your drone is between .55 pounds (250 grams) and 55 pounds (25 kilograms),
you must register your drone through the [FAA's Drone Zone][09],
and the registration number must be present on the outside of your drone.

.............. free registration stickers - https://pilotinstitute.com/free/

### Commercial Drone Pilot Require Part 107 Certification
You do not need a drone license when you fly your drone strictly for fun as a hobby, recreational use (no side jobs or in-kind work allowed).
You’ll need an FAA-issued Part 107 Certificate to start piloting commercial drone flights for work or business.
In order to fly your drone under the FAA 's Small UAS Rule (Part 107), you must obtain a Remote Pilot Certificate from the FAA . This certificate demonstrates that you understand the regulations, operating requirements, and procedures for safely flying drones

* [Drone License: A Step-by-Step Guide to FAA Part 107 Certification for U.S. Commercial Drone Pilots](https://uavcoach.com/drone-certification/)
* [Part 107 Made Easy.](https://pilotinstitute.com/course/part-107-remote-pilot/)

### Remote ID Rules for Home-Built FPV Drones
A person designing or producing a Standard Remote ID drone or broadcast module for operation in U.S. airspace must show that they have met the requirements of the Remote ID rule by following an FAA-accepted Means of Compliance (MOC). A Means of Compliance describes the methods by which the person complies with the performance-based requirements for Remote ID.
* [Remote ID for Industry and Standards Bodies](https://www.faa.gov/uas/getting_started/remote_id/industry)

_Also, producers of a kit that contains all of the parts and instructions necessary for a drone must meet the production requirements of the Remote ID rule and submit a Declaration of Compliance. The person that puts together a "kit" drone does not need to submit a Declaration of Compliance if they are building it for their own recreation or education but must still meet the operational requirements of the Remote ID rule when flying it._

* [Remote ID Modules for Drones: Everything You Need to Know](https://pilotinstitute.com/remote-id-modules/)
* [OpenDroneID](https://ardupilot.org/dev/docs/opendroneid.html#opendroneid)
* [Remote ID Rules for Home-Built FPV Drones](https://pilotinstitute.com/homebuilt-remote-id-rules/)
* [Is your drone flight Remote ID compliant? 4 ways to know](https://www.thedronegirl.com/2023/04/21/is-your-drone-flight-remote-id-compliant/)
* [Google Search: Remote ID](https://www.google.com/search?q=+Remote+ID+Module&sca_esv=568076549&cs=1&sxsrf=AM9HkKmzZTlBfmSs4bjfXsZBGrqlIx961g%3A1695743424389&ei=wP0SZcWaF9PU5NoP7Z-RyAU&ved=0ahUKEwjF-sLD0MiBAxVTKlkFHe1PBFkQ4dUDCBA&uact=5&oq=+Remote+ID+Module&gs_lp=Egxnd3Mtd2l6LXNlcnAiESBSZW1vdGUgSUQgTW9kdWxlMgoQABiKBRixAxhDMggQABiKBRiRAjIFEAAYgAQyBRAAGIAEMgUQABiABDIFEAAYgAQyBRAAGIAEMgUQABiABDIFEAAYgAQyBRAAGIAESLsSUPALWPALcAF4AZABAJgBVqABVqoBATG4AQPIAQD4AQHCAgoQABhHGNYEGLAD4gMEGAAgQYgGAZAGCA&sclient=gws-wiz-serp)
* [Google Search: how to make your own Remote ID](https://www.google.com/search?q=how+to+make+your+own+Remote+ID&sca_esv=568238426&sxsrf=AM9HkKn2gtL2zWHy-Ob4L0lT-aOoPXRa9A%3A1695662165457&ei=VcARZd67G7DQ5NoPsZ-MoAo&ved=0ahUKEwieup_oocaBAxUwKFkFHbEPA6QQ4dUDCBA&uact=5&oq=how+to+make+your+own+Remote+ID&gs_lp=Egxnd3Mtd2l6LXNlcnAiHmhvdyB0byBtYWtlIHlvdXIgb3duIFJlbW90ZSBJRDIIECEYoAEYwwRInTZQyAxY-zJwAXgBkAEAmAGRAaAB3w2qAQQxOC4zuAEDyAEA-AEBwgIHECMYsAMYJ8ICChAAGEcY1gQYsAPCAgoQABiKBRiwAxhDwgIOEAAY5AIY1gQYsAPYAQHCAhYQLhiKBRjHARjRAxjIAxiwAxhD2AECwgITEC4YigUY5QQYyAMYsAMYQ9gBAsICBxAjGLACGCfCAgcQABgNGIAEwgIGEAAYBxgewgIFEAAYgATCAgYQABgIGB7CAgQQABgewgIIEAAYCBgHGB7CAgYQABgeGA3CAggQABgIGB4YDcICChAAGAgYHhgNGArCAggQABiKBRiGA8ICBRAAGKIEwgIIEAAYiQUYogTCAgoQIRigARjDBBgK4gMEGAAgQYgGAZAGE7oGBggBEAEYCboGBggCEAEYCA&sclient=gws-wiz-serp)

## Where can I Fly?
FAA rules apply to the entire National Airspace System -- there is no such thing as "unregulated" airspace. Drone operators should be familiar with the difference between controlled and uncontrolled airspace, and where you can legally fly. Controlled airspace is found around some airports and at certain altitudes where air traffic controllers are actively communicating with, directing, and separating all air traffic. Other airspace is considered uncontrolled in the sense that air traffic controllers are not directing air traffic within its limits.

In general, you can only fly your drone in uncontrolled airspace below 400 feet above the ground (AGL).

* [Where Can I Fly?](https://www.faa.gov/uas/getting_started/where_can_i_fly)
* [No Drone Zone](https://www.faa.gov/uas/resources/community_engagement/no_drone_zone)
* [Airspace 101 – Rules of the Sky](https://www.faa.gov/uas/getting_started/where_can_i_fly/airspace_101)
* [B4UFLY App](https://www.faa.gov/uas/getting_started/b4ufly)

If your drone doesn't have Remote ID capabilities, you’re not out of flying options completely.
You can fly a drone without Remote ID capabilities in a [FAA-Recognized Identification Area (FRIA)][11].
These are geographic areas (typically open fields and fairgrounds) that are recognized by the FAA where unmanned aircraft not equipped with Remote ID are still allowed to fly.
hese tend to be sites like fields owned by flying clubs, model aircraft groups or universities, so link up with a local group to help request more sites.
The FAA has a map through ArcGIS that can be a bit cumbersome to navigate. But, if you click the layer tab and select the boxes for “Recreational Flyer Fixed Sites,” they display quite nicely.
https://faa.maps.arcgis.com/apps/webappviewer/index.html?id=9c2e4406710048e19806ebf6a06754ad

FRIA applications are limited to [FAA-Recognized Community Based Organizations][12] educational institutions like primary and secondary schools, trade schools, colleges, universities,
and non-profit groups that are 501(c) or 501(a) in the Internal Revenue Code.

I live in the Washington DC area and the National Capital Region is governed by a Special Flight Rules Area (SFRA).
Specifically a 30-mile radius of Ronald Reagan Washington National Airport,
which restricts all flights in the greater DC area.
The airspace around Washington, D.C. is more restricted than in any other part of the country. Rules put in place after the 9/11 attacks establish "national defense airspace" over the area and limit aircraft operations to those with an FAA and Transportation Security Administration authorization. Violators face stiff fines and criminal penalties.

The the DC area SFRA is divided into a 15-mile radius inner ring and a 30-mile radius outer ring.
Specifically, the FAA state.... [DC Area Prohibited & Restricted Airspace](https://www.faa.gov/uas/resources/community_engagement/no_drone_zone/dc)

1. Flying an unmanned aircraft within the 15-mile radius inner ring is prohibited without specific FAA authorization.
2. Flying a drone for recreational or non-recreational use between 15 and 30 miles from Washington, D.C. is allowed under these operating conditions:
    * Aircraft must weigh less than 55 lbs. (including any attachments such as a camera)
    * Aircraft must be registered and marked
    * Fly below 400 ft.
    * Fly within visual line-of-sight
    * Fly in clear weather conditions
    * Never fly near other aircraft

## How Do I Assure Where and How I'm Flying is Safe and Allowed?
Recreational pilots must know where they are flying with respect to authorized airspace.
Download the FAA's B4UFLY mobile app
Download the FAA's B4UFLY mobile app for more recreational drone flying resources.

* [Safety Guidelines for Recrational Fliers](https://ftca.flitetest.com/safety-guidelines/)

* [FAA’s UAS Data Delivery System](https://udds-faa.opendata.arcgis.com/)
* [See FAA UAS Data on a Map](https://faa.maps.arcgis.com/apps/webappviewer/index.html?id=9c2e4406710048e19806ebf6a06754ad)
    * UAS Flight Restrictions are shown as red polygons. UAS Flight Restrictions apply to all UAS flight operations, and remain in effect 24 hours a day, 7 days a week.

Fly at or below 400 feet in Class G (uncontrolled) airspace.
Note: Anyone flying a drone in the U.S. National Airspace System (NAS) is responsible for flying within the FAA guidelines and regulations. That means it is up to you as a drone pilot to know the rules: Where Can I Fly?

Class G airspace (uncontrolled) is that portion of airspace that has not been designated as Class A, Class B, Class C, Class D, or Class E airspace. Rules governing VFR flight have been adopted to assist the pilot in meeting the responsibility to see and avoid other aircraft.
Class Golf (Class G) airspace is the uncontrolled "govern free" airspace which is void from Air Traffic Control (ATC) jurisdiction
Class G airspace supports both Instrument Flight Rules (IFR) and Visual Flight Rules (VFR) operations within
https://www.cfinotebook.net/notebook/national-airspace-system/class-golf-airspace
https://www.cfinotebook.net/notebook/national-airspace-system/national-airspace-system

[Leesburg VA airport has a Class E airspace](https://www.federalregister.gov/documents/2014/01/03/2013-31062/establishment-of-class-e-airspace-leesburg-va).
Leesburg is also within the [DC Area Prohibited & Restricted Airspace](https://www.faa.gov/uas/resources/community_engagement/no_drone_zone/dc)
but outside the 15-mile radius inner ring that prohibits drone flying without specific FAA authorization
You can fly a drone in the Class G airspace around the Leesburg airport.
Only airports located in Class A, B, C, D, & E2 controlled airspace require LAANC authorizations to operate near or around.
Read more about Class E airspace [here](https://www.aloft.ai/blog/class-e-airspace-and-laanc/).

[Leesburg Appeals to FAA on Remote Tower Shutdown](https://www.loudounnow.com/news/leesburg-appeals-to-faa-on-remote-tower-shutdown/article_fb867388-c33d-11ed-a97a-efa712d08176.html)

* [Can I fly my drone near small airports in Class G uncontrolled airspace?](https://www.aloft.ai/blog/can-i-fly-my-drone-near-small-airports-in-class-g-uncontrolled-airspace/)

## What is a No Drone Zone?
The FAA uses the term "[No Drone Zone][10]" to help people identify areas where they cannot operate a drone or unmanned aircraft system (UAS). The operating restrictions for a No Drone Zone are specific to a particular location. You can find out if there are airspace restrictions where you are planning to fly using the B4UFLY mobile app.

## Where Can I Learn About Building a Drone?
* [How to Build a Drone | A DIY Guide](https://dojofordrones.com/build-a-drone/)
* [How to Build a Drone](https://dronenodes.com/how-to-build-a-drone/)
* [DIY drone: Learn How to Build Your Own Quadcopter Drone](https://interestingengineering.com/innovation/diy-drone-learn-how-to-build-your-own-quadcopter-drone)
* [How to design Complete Drone Overview](https://grabcad.com/tutorials/how-to-design-complete-drone-overview)
* [Street League: Build Guide](https://streetleague.io/build-guide/)

* [The Top 6 Frames to 3D Print for Your DIY Drone](https://www.makeuseof.com/top-frames-to-3d-print-for-diy-drone/)
* [Brushed Micro Quad Parts List](https://oscarliang.com/brushed-micro-quad-parts-list/)
* [Exploring Ground-Effect With A Quadcopter](https://hackaday.com/2023/09/23/exploring-ground-effect-with-a-quadcopter/)

* [Rotor Riot](https://rotorriot.com/)

* [Ultimate Beginners Guide to Building A FPV Freestyle Drone](https://www.youtube.com/watch?v=5ed6y2rgaq8)
* [How to make Fpv drone at home](https://www.youtube.com/watch?v=iZD_fAE8kZ8)



## Where Can I Learn About Flying a Drone?
* [Drone Programming With Python Course | 3 Hours | Including x4 Projects (2021)](https://www.youtube.com/watch?v=LmEcyQnfpDA)
* [Learn Multirotors From First Principles](https://hackaday.com/2021/04/11/learn-multirotors-from-first-principles/)
* [ArduPilot](https://ardupilot.org/copter/docs/copter-introduction.html)
* [Pilot Institute](https://pilotinstitute.com/courses/drones/)
* [FPV Freedom Coalition](https://fpvfc.org/)
* [FPV Trick Tutorials!](https://www.youtube.com/watch?v=QnQH5U-XTpU&list=PLBlZ_AJ8LoaNWUhWPM2Owwjqkzhht0dR3)
* [How To 10 FPV Freestyle Tricks | LEARN THESE FIRST](https://www.youtube.com/watch?v=0EqJ9C8KuTQ)

## Where Can I Drone Flying Community?
* [Flite Test Community Association (FTCA)](https://ftca.flitetest.com/)
* [Street League](https://streetleague.io/)
* [Tiny Whoop][15]

## Where Can I Find a Local FPV Community?
[MultiGP](https://www.multigp.com/)
is the World's largest Drone Racing League & FPV Community.
MultiGP chapters welcome all pilots regardless of their skill levvel.

[Northern Virginia Radio Control](https://www.multigp.com/chapters/view/?chapter=Northern-Virginia-Radio-Control)

## 4S or 6S Battries?
* [Using LiPo Batteries for FPV Drones: A Beginner’s Guide with Top Product Recommendations](https://oscarliang.com/lipo-battery-guide/)
* [LiPo Batteries](https://dronenodes.com/best-lipo-drone-battery-explained/)
* [Choosing Between a 4S and 6S FPV Drone? #shorts](https://www.youtube.com/shorts/Cv7yHN4IRWw)

### My Choose
Teensy-controlled, Arduino-programmable quadcopter! For hobbyist, engineers and drone enthusiasts.
* [Carbon Aeronautics](https://www.youtube.com/@carbonaeronautics/videos)
* [GitHub: Carbon Aeronautics](https://github.com/CarbonAeronautics?tab=repositorie)
* [Cheap and Simple Radio Control Making for RC Models. DIY RC 4-Channel](https://www.youtube.com/watch?v=bD7rQbnSbek)
* [DIY Arduino RC Receiver | Radio Control for RC Models and Arduino Projects](https://www.youtube.com/watch?v=tzNROquPEHQ)
* [How To Make Drone With Hand-made Radio Control. DIY Drone](https://www.youtube.com/watch?v=yFBvC_zRie)
* [DIY 6 Channels Radio Control For Models. How To Make İt](https://www.youtube.com/watch?v=pjBnFZGfsjI)

* [Making a Long Range Remote Control. DIY 1 to 8-Channel Arduino RC PART-1](https://www.youtube.com/watch?v=jtXkYjStimo)
* [Making a 2400 meters LONG RANGE 8-Channel & Digital Trim Radio Control For RC Models. PART-2](https://www.youtube.com/watch?v=RSDfMaanKXM)

* [DIY Arduino based RC Transmitter](https://www.youtube.com/watch?v=-BDCmwNssiw)
* [DIY Arduino RC Receiver | Radio Control for RC Models and Arduino Projects](https://www.youtube.com/watch?v=tzNROquPEHQ)



-----




# Flight Controller (FC) Hardware & Software
# What are F4, F7 and H7 Flight Controllers?
Flight controllers (FC in short) are circuit boards that have an array of environmental sensors,
such as gyroscopes, accelerometers, barometer, compass, GPS, etc.
along with signals from the pilot, within a [PID feedback control loop][14] to help you fly you quadcopter.

F1, F3, F4 and F7 are the most commonly used processors in mini quads. F3 was the successor of F1, F4 was the successor for F3 and F7 was the replacement for F4. All these 4 processors are based on STM32 architecture which uses 32 bit processing

* **F1** processor is the oldest processor and has the lowest processing capability of all the above processors. It is actually an outdated processor with Betaflight ending support to F1 FC’s in 2017.
* **F3** was essentially a F1 FC with increased number of UART’s (It is discussed in detail below) and increased flash memory (memory used to store the FC’s firmware codes). Some smaller FC’s use this processor even now because of their compact size and exceptional processing power.
* **F4** was a giant leap in mini quad processors with more than double the processing power that of an F3. But there are limitations with F4 processors with no support for [SmartAudio][13] natively which is not a big deal for most people. Still F4 FC’s are the most popular choice for their functionality and affordability.
* **F7** processor is the big daddy of mini quad FC’s. F7 FC’s became available mid of 2018 and these are the most recent processors. F7 FC’s are packed with upto 8 UART’s which can be used for telemetry, GPS, camera control etc.., F7 FC’s come with dual Gyros (MPU6000 which is noise resistant and ICM20602 which can run 32K gyro sampling).

* [How to Setup SmartAudio for VTX Control (change VTX settings from OSD)](https://oscarliang.com/vtx-control/)

The processing power of an F7 flight controller is better than the processing power that an F4 & F3 flight controller brings to the table.
But then a feature-packed F4 is cheaper than the cheapest F7.
F4 flight controllers work just fine in today’s world,
but a year or 2 from now they would struggle to hold up demanding needs.

Picking the right flight controller that suits your needs is a daunting task.
There are dozens of flight controllers out in the market to choose from with different hardware and software.
There are a lot of parameters to consider before buying a flight controller,
and the sources below could potentially help in making that decission:

Sources:
* [How to Choose a Flight Controller for FPV Quadcopter](https://dronenodes.com/drone-flight-controller-fpv/)

## FC Hardware
## FC Software
Betaflight, Cleanflight, Raceflight, KISS are some of the major flight control firmware’s widely used in flying a mini quad. Each firmware is optimized for a particular function.

* [BF4.3 Complete Tuning Guide](https://www.youtube.com/watch?v=Ro4YMCLJ1dU&list=PLFPBjpbd5xKRnjNpYMep7MxovfhMBIzxP)

* [Betaflight](https://betaflight.com/) is the most popular option with its easy GUI (graphical user interface) and under constant development by its developers. Betaflight is flexible and a powerful flight controller firmware perfect for a beginner which requires little to no coding experience. Another major advantage that Betaflight has is that it supports a large number of flight controllers.
* Emuflight
* [Cleanflight](https://cleanflight.com/)
* [Raceflight](https://github.com/rs2k/raceflight) focus entirely for acrobatic and racing drones. Raceflight stands out by deleting non essential codes (like GPS). By deleting these codes Raceflight freed up processing power which can be used to do other useful functions like running faster looptimes for example.
* [KISS](http://kiss.flyduino.net/) is a closed source firmware developed by FlyDuino. KISS products are powerful and up to date with the current trends on the market and runs on proprietary boards from KISS.
* [INAV](https://github.com/inavFlight/inav/wiki): Navigation-enabled flight control software


# Build or Buy Flight Controller (FC)
ArduPilot is a open source autopilot system supporting many vehicle types:
multi-copters, traditional helicopters, fixed wing aircraft, boats, submarines, rovers and more.
The source code is developed by a large community of professionals and enthusiasts.

* [Six Degrees Of Freedom Omnicopter With Ardupilot](https://hackaday.com/2021/01/09/six-degrees-of-freedom-omnicopter-with-ardupilot/)
* [ArduPilot](https://ardupilot.org/)
* [Cube Pilot](https://cubepilot.org/)
    * [What is CubePilot?](https://docs.cubepilot.org/user-guides/#what-is-cubepilot)

## Quadcopter Build Videos
Seeing how a quadcopter is built and understanding why its built that way, can be very instructive.
Below you will find several video that do just this.

Build Videos:
* [How to Start Flying FPV DRONES in 2023](https://www.youtube.com/watch?v=GdkeR-66Ock)
* [How To Build Budget Cinematic FPV Drone 2020](https://www.youtube.com/playlist?list=PLoPtpxJIxgnZ8oxpQ3GyTiOGzH-QLWnzn)
* [ULTIMATE FPV Freestyle Drone Build - 2023 Step by Step](https://www.youtube.com/watch?v=6THiVUfn38Q)

* [FPV Tools and Materials for Building Drones and Fixed Wings](https://oscarliang.com/fpv-tools/)



-----



## Components of a Drone Build
What is required to construct a drone, support the building process, and the use of the drone?
And since building and using something should not be done without insight
into the principles on which it operates (aka [theory of operation][03]),
what topic / skills do you need to master before or during the build?

* Required
    * Frame
    * Motors
    * Propeller
    * Flight Stack
        * Flight Controller (FC)
            * Orientation Sensor
            * Movement Sensor
            * Altitude Sensor
        * Electronic Speed Controller (ESC)
    * Power Distribution
        * Battery
        * Power Wiring
    * Controller
        * Handheld Radio Transmitter
        * Quad Radio Reciever
* First Person Viewing (FPV)
    * Video Radio Receiver (VRX)
    * Video Radio Transmitter (VTX)
* Cinematography
    * Camera
    * Video Post Processing
* Geo-Positioning
    * GPS Compass Module
* Recommended
    * Battery Consumption Sensor
    * Telemetry Radio Transmitter
    * Telemetry Radio Receiver
* Nice To Have
    * Autopilot - https://ardupilot.org/copter/docs/common-autopilots.html
    * Optical Flow LIDAR Sensor
    * Lost Drone Buzzer
    * Gimbal & Stabilization
    * Global Positioning Sensor
    * Directional Antenna
    * Smart Return Home
    * Auto-Land
    * Follow Me
    * Fail Safe

## Combat Quadcopter (Battle Mode)
* [Battle Drones](https://www.amazon.com/s?k=battle+drones&crid=3ELYIU54LX2MJ&sprefix=battle+drone%2Caps%2C151&ref=nb_sb_ss_ts-doa-p_1_12)

## Ryze Tech Tello
* [Ryze Tech Tello](https://www.ryzerobotics.com/tello)
* [Ryze Tech Tello](https://www.amazon.com/gp/product/B07BDHJJTH/)
* [Drone Programming With Python Course | 3 Hours | Including x4 Projects (2021)](https://www.youtube.com/watch?v=LmEcyQnfpDA)
* [Buying a Ryze Tello Drone? Watch This First!](https://www.youtube.com/watch?v=yQoC_n6126A)
* [Ultimate Drone Buying Guide for Total Beginners 2020](https://www.youtube.com/watch?v=9mzwPoxKxEw)

### Omnicopter
* [SIX DEGREES OF FREEDOM OMNICOPTER WITH ARDUPILOT](https://hackaday.com/2021/01/09/six-degrees-of-freedom-omnicopter-with-ardupilot/)

### Raspberry Pi Drone
* [Raspberry Pi Drone: How to Build Your Own](https://all3dp.com/2/raspbery-pi-drone-simply-explained/)
* [SRD-1 - 3D Printed Drone (Arduino + Raspberry)](https://www.element14.com/community/community/project14/attackofthedrones/blog/2021/05/25/srd-1-open-source-3d-printed-drone)

### ESP32 Drone
* [ESP32 Drone](https://hackaday.io/project/188578-esp32-drone)

## First and Esay Flying
* [A Drone for the Rest of Us](https://hackaday.com/2022/09/29/a-drone-for-the-rest-of-us/)

* [Raspberry PI Pico W Copter is Ready for Take Off](https://www.tomshardware.com/news/raspberry-pi-pico-w-copter)

* [Micro Coreless Quadcopter](https://rbklabs.in/micro-coreless-quadcopter/)
    * [Frame - QX95](https://www.amazon.com/QX95-Brushed-Racing-Quadcopter-Frame/dp/B08LTNT16B)
    * [Brushed/coreless motors - 2 x CW and 2 x CCW - 8520 Coreless](https://www.amazon.com/s?k=8520+Coreless&i=toys-and-games&crid=1GJ7TRJSESA5H&sprefix=8520+coreless%2Ctoys-and-games%2C69&ref=nb_sb_noss_2)
    * [AIO Flight Controller - (FC + Brushed motor controllers in a tiny package) - F3 Evo v2.0](https://www.aliexpress.us/item/3256804569063647.html)
    * [Propellers  - 2 x CW and 2 x CCW - 55mm]()
    * [1S lipo battery - 600mAh 25C]()
    * [Radio Receiver - FlySky FS-A8S](https://www.aliexpress.us/item/3256804292515470.html)
    * [BetaFlight][19]

# EACHINE E58 WiFi FPV Quadcopter
* [EACHINE E58 WIFI FPV With 2MP Wide Angle Camera High Hold Mode Foldable RC Drone Quadcopter RTF](https://www.eachine.com/de/EACHINE-E58-WIFI-FPV-With-2MP-Wide-Angle-Camera-High-Hold-Mode-Foldable-RC-Drone-Quadcopter-RTF-p-1045.html)
* [Eachine E58 720P Folding FPV Camera Drone Flight Test Review](https://www.youtube.com/watch?v=Qp0qRJMhreU)

# FPV Flight Simulators
* [DroneDJ: An FPV professional offers his take on the new DJI FPV drone](https://www.youtube.com/watch?v=2W9dJmeM-Ik&list=TLGGkG2l79GO-8EwOTA0MjAyMQ)
* [Linux FPV drone simulators](https://www.swalladge.net/archives/2019/11/15/fpv-drone-simulators-linux/)

# Flight Mechanics
* [Orbital Mechanics for Engineering Students](http://www.nssc.ac.cn/wxzygx/weixin/201607/P020160718380095698873.pdf)



# Toroidal Propeller
* [Propellers](https://www.youtube.com/watch?v=TbAkcKPHqt8&t=25s)
* [Toroidal Propellers Make Drones Less Annoying](https://hackaday.com/2023/01/28/toroidal-propellers-make-drones-less-annoying/)
* [ Turned MIT Award Winning Toroidal Propeller Into A PC Fan](https://www.youtube.com/watch?v=4ImeOKgD_Dw)


* [UAV Communications And Mission Systems](https://www.aeronetworks.ca/2021/01/uav-communications-and-mission-systems.html)

* [Reverse Engineering A 900 MHz RC Transmitter And Receiver](https://hackaday.com/2022/02/20/reverse-engineering-a-900-mhz-rc-transmitter-and-receiver/)



# RC Link Protocol
* [ExpressLRS: Open Source, Low Latency, Long Range RC Protocol](https://hackaday.com/2021/01/19/expresslrs-open-source-low-latency-long-range-rc-protocol/)

# Regulations / FAA Rules
* [Federal Aviation Administration Announces Major Drone Rule Changes](https://hackaday.com/2020/12/29/federal-aviation-administration-announces-major-drone-rule-changes/)

# Drones
* [8 open source drone projects](https://opensource.com/article/18/2/drone-projects)
* [Build a PRO FPV Racing Drone for ONLY $99 Full guide - 2018 UAVFUTURES $99 Build](https://www.youtube.com/watch?v=GFNGUDT_9_c)
* [Making Autonomous Racing Drones Lean And Mean](https://hackaday.com/2019/05/31/making-autonomous-racing-drones-lean-and-mean/)
* [Drone Theory 101: Part 1. The basics, and how an fpv quadcopter functions!](https://www.youtube.com/watch?v=K05UwsiqZ_E)
* [Build Your Own Selfie Drone With Computer Vision](https://hackaday.com/2019/06/30/build-your-own-selfie-drone-with-computer-vision/)
* [Quadcopter With Tensegrity Shell Takes A Beating And Gets Back Up](https://hackaday.com/2020/11/05/quadcopter-with-tensegrity-shell-takes-a-beating-and-gets-back-up/)

## Mini-Drone
* [Micro Quadcopter Designed In OpenSCAD](https://hackaday.com/2021/04/02/micro-quadcopter-designed-in-openscad/)
* [Resilient AI Drone Packs It All In Under 250 Grams](https://hackaday.com/2021/03/15/resilient-ai-drone-packs-it-all-in-under-250-grams/)
* [The world’s smallest autonomous racing drone](https://robohub.org/the-worlds-smallest-autonomous-racing-drone/)
    * [Eachine TRASHCAN](https://www.eachine.com/Eachine-TRASHCAN-75mm-Crazybee-F4-PRO-OSD-2S-Whoop-FPV-Racing-Drone-0803-16000KV-1200TVL-Adjustable-Camera-25-or-200mW-VTX-Swtichable-p-1328.html)
* [How to Build a Cool & Cheap 3D Printed Mini Drone](https://www.youtube.com/watch?v=gpKcrYcMFKM)
    * [How to build a cool & cheap 3D printed micro drone](https://blog.prusaprinters.org/how-to-build-a-3d-printed-micro-drone/)
* [DIY BEGINNER'S GUIDE to 3D Printed Drones](https://www.youtube.com/watch?v=T9N3-FDHv30)
* [Top 10 3D printed drones](https://www.3dnatives.com/en/top-3d-printed-drones-101220185/)
* [3D Printed Racing Drone - Will It Survive?](https://www.youtube.com/watch?v=vjvlB7RjnYI)
* [ESPcopter: A Fully Customizable Drone](https://hackaday.com/2019/09/25/espcopter-a-fully-customizable-drone/)
* [Tiny Drones Navigate Like Real Bugs](https://hackaday.com/2019/11/06/tiny-dones-navigate-like-real-bugs/)
* [The Ball-Drone Project](https://hackaday.io/project/169823-the-ball-drone-project)
* [STORM Racing Drone (SRD6-GPS / NAZA V2)](http://www.helipal.com/storm-racing-drone-gps-rtf-naza-v2.html)
* [Flies Like A Quadcopter, But This Drone Design Has Only One Propeller](https://hackaday.com/2020/11/02/flies-like-a-quadcopter-but-this-drone-design-has-only-one-propeller/)
* [How to Build an FPV Drone (under $150)!](https://www.instructables.com/How-to-Build-an-FPV-Drone-under-150/)

* [Micro 105 FPV Quadcopter](https://www.thingiverse.com/thing:1221911)
* [Micro 105 FPV Quadcopter - 3D Printed](https://www.instructables.com/Micro-105-FPV-Quadcopter-3D-Printed/)

* [Crazyflie 2.1](https://www.seeedstudio.com/crazyflie-V2-1-p-2894.html)
* [Crazyflie 2.1](https://www.bitcraze.io/products/crazyflie-2-1/)


### NanoLongRange
* [The #NanoLongRange by Dave_C_FPV](https://www.thingiverse.com/thing:4769576)
* [Attack of the Flying 18650s](https://hackaday.com/2021/03/03/attack-of-the-flying-18650s/)

# Hackable Drones
* [A Hackable Drone Without All The Wiring](https://hackaday.com/2020/05/02/a-hackable-drone-without-all-the-wiring/)

# Open Source RC Radio Tggransmitters
* [OpenTX](https://www.open-tx.org/)

# First Person Video (FPV)
* [first person video (FPV)][20]
* [FPV Obsession](http://fpvobsession.com/)

# On Screen Display (OSD)
* [How to Choose OSD For QuadCopter](https://oscarliang.com/best-osd-quadcopter-fpv-data-on-screen-display-video/)

# Autopilot and Ground Station Software
* [The world’s smallest autonomous racing drone](https://robohub.org/the-worlds-smallest-autonomous-racing-drone/)
* [Paparazzi UAV](http://wiki.paparazziuav.org/wiki/Main_Page)
* [ArduPilot](https://ardupilot.org/index.php)
* [Building a Self-Driving Go Kart](https://www.youtube.com/watch?v=PYFKGDfunfY)
    * [Tesla go-kart upgraded with self-driving autopilot](https://www.geeky-gadgets.com/self-driving-autopilot-go-cart/)

## PX4 Open Source Autopilot
* [PX4 Open Source Autopilot](https://px4.io/)
* [TAKING REVERSE ENGINEERING TO THE SKIES: CHEAP DRONE GETS PX4 AUTOPILOT](https://hackaday.com/tag/stm32f405rg/)

# Motors to Use
* [How to pick the best motor for your quadcopter, now with PHYSICS!](https://www.youtube.com/watch?v=RXy00orSpfU)
* [Motor KV 100% Explained: Why go from 4S ➡️6S➡️8S?!](https://www.youtube.com/watch?v=uvyi6hPIt8w)

* motor with position sensing
    * [IQ Motor Module](https://www.crowdsupply.com/iq-motion-control/iq-motor-module)


* [Jumper T8SG V2.0 Plus Carbon Special Edition Hall Gimbal Multi-protocol Advanced Transmitter for Flysky Frsky - Mode 2 (Left Hand Throttle)](https://www.banggood.com/Jumper-T8SG-V2_0-Plus-Carbon-Special-Edition-Hall-Gimbal-Multi-protocol-Advanced-Transmitter-for-Flysky-Frsky-p-1442802.html?ID=42482&cur_warehouse=CN)

* [Lego Drone Finally Takes Off](https://hackaday.com/2020/01/15/lego-drone-finally-takes-off/)

# Camera: Runcam Thumb Pro
* [Better Than a Naked GoPro?? - Runcam Thumb Pro](https://www.youtube.com/watch?v=A_r4BAtYpZE)
* [Tiny 4k Action Camera: Runcam Thumb Pro 4k](https://www.youtube.com/watch?v=CiXqm016ljc)
* [Gyroflow](https://gyroflow.xyz/)

# Flight Controller
* [Cheap vs. Expensive FPV Controllers - What's the Difference?](https://www.youtube.com/watch?v=SrN6ps4NM10)

* [DIY Flight Controller: How to build your own flight controller](https://www.youtube.com/playlist?list=PLUo0zMUQehP8k8IROYb-iXnCTw5TACZ5P)
* [dRehmFlight: Customizable Flight Stabilisation For Your Weird Flying Contraptions](https://hackaday.com/2021/02/15/drehmflight-customizable-flight-stabilisation-for-your-weird-flying-contraptions/)
* [Open Source Motion Controller For DIY Drones](https://hackaday.com/2021/03/24/open-source-motion-controller-for-diy-drones/)
* [Radio Control Joby Aircraft Uses Six Tiltrotors To Fly](https://hackaday.com/2022/01/29/radio-control-joby-aircraft-uses-six-tiltrotors-to-fly/)

* [Special Lecture: F-22 Flight Controls](https://www.youtube.com/watch?v=n068fel-W9I)

* [Cleanflight](https://cleanflight.com/)
    * [Cleanflight - open source firmware for flight controllers](https://www.instructables.com/Micro-105-FPV-Quadcopter-3D-Printed/)
    * [Cleanflight - Configurator](https://chrome.google.com/webstore/detail/cleanflight-configurator/enacoimjcgeinfnnnpajinjgmkahmfgb)
    * [GitHub: cleanflight/cleanflight](https://github.com/cleanflight/cleanflight)

* [Flight Controller Wiring For Beginners](https://www.youtube.com/playlist?list=PLwoDb7WF6c8lCcjOh26ZVQsLQtjGPQcgy)

# Flight Computer
* [The Difference Between a Drone Flight Controller and Flight Computer](https://www.youtube.com/watch?v=PlKeFj5teo4)
* [Flight Controller and Flight Computer](https://www.youtube.com/results?search_query=Flight+Controller+and+Flight+Computer)
* [Drone Simulation and Control](https://www.youtube.com/playlist?list=PLn8PRpmsu08oOLBVYYIwwN_nvuyUqEjrj)

## Automomous Flight and Obstacle Avoidance
Predicted GPS (P-GPS) is a form of assistance that reduces the Time to First Fix (TTFF), the time needed by a GNSS module to estimate its position.
A form of assistance provided to devices trying to obtain a Global Navigation Satellite System (GNSS) fix, where the device can download up to two weeks of predicted satellite Ephemerides data. It enables devices to determine the exact orbital location of the satellite without connecting to the network every two hours with a trade-off of reduced accuracy of the calculated position over time. It is available through nRF Cloud.

* [nRF Cloud P-GPS](https://developer.nordicsemi.com/nRF_Connect_SDK/doc/latest/nrf/libraries/networking/nrf_cloud_pgps.html)
* [nRF Cloud](https://nrfcloud.com/#/)
* [Autonomous Drone Dodges Obstacles Without GPS](https://hackaday.com/2021/11/03/autonomous-drone-dodges-obstacles-without-gps/)
* [GPS Flight Modes](https://droneshopcanada.ca/blogs/drone-tips-and-tricks/124373447-dji-phantom-3-flight-modes)

# Serial Studio
Serial Studio is a multi-platform, multi-purpose serial data visualization program. The goal of this project is to allow embedded developers & makers to easily visualize, present & analyze the data generated by their projects and devices, without the need of writing specialized computer software for each project.

* [Serial Studio: Easily Visualise And Log Serial Data](https://hackaday.com/2021/01/31/serial-studio-easily-visualise-and-log-serial-data/)
* [Introducing Serial Studio, a dashboard software for serial port projects](https://www.alex-spataru.com/blog/introducing-serial-studio)
* [Serial Studio One Year On](https://hackaday.com/2022/01/15/serial-studio-one-year-on/)
* [Serial-Studio](https://github.com/Serial-Studio/Serial-Studio)

# Finding lost Drone
* [Lost A Lightweight Quadcopter? Here Are The Best Ways To Find It](https://hackaday.com/2021/03/06/lost-a-lightweight-quadcopter-here-are-the-best-ways-to-find-it/)

# Other
* [The Drone That Can Play Dodgeball](https://hackaday.com/2020/03/23/the-drone-that-can-play-dodgeball/)
* [UHF Radio Beacon for Lost RC Models](https://blog.tindie.com/2020/04/uhf-radio-beacon-lost-rc-models/)
* [A DIY Functional F-35 Is No Simple Task](https://hackaday.com/2020/04/27/a-diy-functional-f-35-is-no-simple-task/#more-407964)
* [A Micro RC Plane Builder Shares His Tricks](https://hackaday.com/2017/02/10/a-micro-rc-plane-builder-shares-his-tricks/)
* [Let’s Take A Closer Look At This Robotic Airship](https://hackaday.com/2020/07/22/lets-take-a-closer-look-at-this-robotic-airship/)
* [The Unique Challenges of Aerial Robotics](https://hackaday.com/2022/06/10/the-unique-challenges-of-aerial-robotics/)

# Landing Sensor
* [Mini Laser Distance Range Sensor (4m, I2C, IP67)](https://www.dfrobot.com/product-2727.html)

# GPS Sensor
* [Upgrade your drone GPS now! M10 receivers are here!](https://www.youtube.com/watch?v=eBzQLVYOy9Y)
* [Flywoo GM10 Mini V3 GPS - M10 For Under $20](https://www.youtube.com/watch?v=uXH0ToYuCcs)
* [Betaflight 4.4 GPS Rescue - Can You Now Trust It ?](https://www.youtube.com/watch?v=puN6glQ8GsQ)



---------



# Airplane

## Modeling Wing Sections
* [A Guide To 3D Printing Model Aircraft Wings](https://hackaday.com/2022/08/26/a-guide-to-3d-printing-model-aircraft-wings/)

## RC Airplane
* [Intro to Aerodynamics: How Do Airplanes Fly?](https://www.youtube.com/watch?v=Z1FAAJ4hUaQ)

* [WiFi Controlled Plane Is Cheap Flying Fun](https://hackaday.com/2019/04/12/wifi-controlled-plane-is-cheap-flying-fun/)
* [Dynamic Soaring: 545 MPH RC Planes Have No Motor](https://hackaday.com/2020/09/24/dynamic-soaring-545-mph-rc-planes-have-no-motor/)

## Classic Airplanes

### Rubberband Powered Airplane
* [Building the WORLDS LARGEST Rubber-Band Plane](https://www.youtube.com/watch?v=PJk245qi-PI)
    * [Project AIR: Rubber Band Plane](https://store.projectair.co.uk/products/rubber-band-plane)

### Simple Airplane
* [How To Make Simple RC Airplane For Simple Radio Control. DIY RC Aiplane & Arduino RC](https://www.youtube.com/watch?v=9SMyBN-B3Vo)
* [Cheap and Simple Radio Control Making for RC Models. DIY RC 5-Channel](https://www.youtube.com/watch?v=ExtHHmFACKk)
* [How To Make RC Trainer Airplane. DIY Model Airplane For Beginners](https://www.youtube.com/watch?v=LzZ4Oqk_J1Y)
* [KendinYap](https://www.youtube.com/channel/UCgjJGE17yfovAvWUzEJFENA)
* [Parkjet](https://www.parkjets.com/)

### F-22 Raptor
* [Making a RC Airplane using Cardboard | Homemade F-22 Raptor](https://www.youtube.com/watch?v=iQsswBpzjpo)

## VTOL Airplanes

### F-35 VTOL
* [Foam F-35 Learns To Hover](https://hackaday.com/2021/07/15/foam-f-35-learns-to-hover/)
* [Making an INSANE Hovering RC F-35 VTOL](https://www.youtube.com/watch?v=RqdcZD0ZoUk)
* [Super-Maneuverable RC VTOL F-35 Parkjet](https://www.youtube.com/watch?v=Ds-ODWydxeY)
* [The Real Life Sci-Fi of Vertical Take-Off Planes](https://www.youtube.com/watch?v=4GfqB7P6uAE)

### Tri-Mode VTOL
* [Winged Drone Gets Forward Flight Capability](https://hackaday.com/2022/10/02/winged-drone-gets-forward-flight-capability/)

### Tilt-Rotor VTOL
* [Optimising An RC Tilt-Rotor VTOL](https://hackaday.com/2022/08/22/optimising-a-rc-tilt-rotor-vtol/)

### Quadrotor BBplane VTOL
* [QBIT: VTOL Tailsitter Flies With Quadcopter Control Software](https://hackaday.com/2021/08/02/vtol-tailsitter-flies-with-quadcopter-control-software/)



---------



# Rocket / Parachutes / Balloon / Other
* [Advanced Model Rocket Flight Computer Reaching For The Star](https://hackaday.com/2020/10/02/advanced-model-rocket-flight-computer-reaching-for-the-stars/)
* [Three-Stage Thrust Vectoring Model Rocket With Tiny Flight Computers](https://hackaday.com/2021/09/05/three-stage-thrust-vectoring-rocket/)
* [Using SPACE SHUTTLE Software in Model Rockets](https://www.youtube.com/watch?v=EHfsZGN3cYo)
* [FreeCAD Takes Off With A Rocket Design Workbench](https://hackaday.com/2021/04/02/freecad-takes-off-with-a-rocket-design-workbench/)
* [BPS.Space Succesfully Lands A Model Rocket](https://hackaday.com/2022/08/05/bps-space-succesfully-lands-a-model-rocket/)
* [How To Land A Model Rocket Vertically](https://hackaday.com/2023/06/21/how-to-land-a-model-rocket-vertically/)
* [Did I Make the World's Smallest Rocket Flight Computer?](https://www.youtube.com/watch?v=5TTcbMv5tDc)

* [GPS Guided Parachutes For High Altitude Balloons](https://hackaday.com/2021/01/07/gps-guided-parachutes-for-high-altitude-balloons/)

## Flying Stick
* [When Sticks Fly](https://hackaday.com/2022/05/11/when-sticks-fly/)

## Smoke Stopper / ShortSaver
* [ViFly ShortSaver is the smoke stopper you always wanted](https://www.youtube.com/watch?app=desktop&v=f37FeWSYrmo)



[01]:https://www.digitaltrends.com/cool-tech/history-of-drones/
[02]:https://thedroneracingleague.com/learn-more/
[03]:https://en.wikipedia.org/wiki/Theory_of_operation
[04]:https://www.faa.gov/uas/recreational_flyers/knowledge_test_updates
[05]:https://www.faa.gov/uas/recreational_flyers/knowledge_test_updates#TAs
[06]:https://www.faa.gov/uas/recreational_flyers
[07]:https://www.ecfr.gov/current/title-14/chapter-I/subchapter-F/part-107
[08]:https://www.faa.gov/uas/getting_started/user_identification_tool
[09]:https://faadronezone-access.faa.gov/#/
[10]:https://www.faa.gov/uas/resources/community_engagement/no_drone_zone
[11]:https://www.faa.gov/uas/getting_started/remote_id/fria
[12]:https://www.faa.gov/uas/recreationalfliers/faa-recognized-community-based-organizations
[13]:https://oscarliang.com/vtx-control/#:~:text=SmartAudio%20is%20a%20protocol%20between,settings%20remotely%20is%20so%20easy.
[14]:https://en.wikipedia.org/wiki/Proportional%E2%80%93integral%E2%80%93derivative_controller
[15]:https://www.tinywhoop.com/
[16]:https://www.faa.gov/uas/getting_started/remote_id
[17]:https://www.faa.gov/uas
[18]:https://www.faa.gov/uas/getting_started/register_drone
[19]:https://betaflight.com/
[20]:https://www.techtarget.com/whatis/definition/first-person-view-FPV
[21]:https://www.youtube.com/watch?v=P6UDOajLE8E
[22]:https://udds-faa.opendata.arcgis.com/datasets/faa::recreational-flyer-fixed-sites/about
[23]:https://www.firstquadcopter.com/reviews/betafpv-meteor75-pro/
[24]:
[25]:
[26]:
[27]:
[28]:
[29]:
[30]:

