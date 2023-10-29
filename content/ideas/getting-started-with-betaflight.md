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


Review this again - [Betaflight 4.3 Complete Walkthrough](https://www.youtube.com/playlist?list=PLwoDb7WF6c8nT4jjsE4VENEmwu9x8zDiE)
[How to Setup Betaflight Firmware](https://oscarliang.com/betaflight-firmware-setup/)
[Betaflight 4.3 EASY Setup Guide -- PRESETS FAST!](https://www.youtube.com/watch?v=znyiaN5dSxc)
[Betaflight FPV Drone Tuning In 10 Simple Steps](https://oscarliang.com/fpv-drone-tuning/)
[How to Setup RPM Filters in Betaflight: Unlock Smooth FPV Flight Performance](https://oscarliang.com/rpm-filter/)
[Betaflight Air Mode is bad for Whoops. Until now. Maybe.](https://www.youtube.com/watch?v=tCTI2J0QCwc)



# What is a Flight Controller?
Flight controllers (FC) are circuit boards that have an array of environmental sensors,
such as gyroscopes, accelerometers, barometer, compass, GPS, etc.
along with signals from the pilot, within a [PID feedback control loop][14] to help you fly your quadcopter.

# FC Software
Betaflight, Cleanflight, Raceflight, KISS are just some of the major flight control firmware’s widely used in flying quadcopters.
Each firmware is optimized for a particular function.
Betaflight is the most widely used and the default supported nearly all FC providers.

* Quadcopter Freestyle and Racing
    * [Betaflight](https://betaflight.com/) is the most popular option with its easy GUI (graphical user interface) and under constant development by its developers. Betaflight is flexible and a powerful flight controller firmware perfect for a beginner which requires little to no coding experience. Another major advantage that Betaflight has is that it supports a large number of flight controllers.
    * [Cleanflight](https://cleanflight.com/) can be used on multirotor aircraft and fixed-wing aircraft. It supports a variety for shapes and motor counts, not limited to quadcopters, hexacopters, octocopters, tricopters and planes.
    * [Raceflight](https://github.com/rs2k/raceflight) focus entirely for acrobatic and racing drones. Raceflight stands out by deleting non-essential codes (like GPS). By deleting these codes Raceflight freed up processing power which can be used to do other useful functions like running faster looptimes for example.
    * [KISS](http://kiss.flyduino.net/) is a closed source firmware developed by FlyDuino. KISS products are powerful and up to date with the current trends on the market and runs on proprietary boards from KISS.
    * [Emuflight](https://emuflight.github.io/) differs from Betaflight in flight code, methodology and purpose. Hardware support and general setup between EmuFlight and Betaflight continues to be near identical. EmuFlight stays up to date with the latest Betaflight merging almost all code changes, the main differences being related to flight code.  Due to the small development team of EmuFlight we don’t have the development resources that Betaflight does, and as a result we share most our code and will improve as Betaflight improves. At some point in the future EmuFlight may deviate from Betaflight to a larger extent. See the ["Emuflight vs Betaflight"](https://www.youtube.com/watch?v=Ad_di2L5PM8) video.
* Quadcopter Autonomous Flying
    * [INAV](https://github.com/inavFlight/inav/wiki) is a navigation-enabled flight control softwares being actively developed.  It currently supports RTH (Return To Home) with a predefined climb height, position hold, waypoints, "follow-me" and many more features.
    * [ArduPilot](https://ardupilot.org/) is used to "pilot" many thing, including multi-copters, traditional helicopters, fixed wing aircraft, rovers, submarines and antenna trackers. The ‘Ardu’ part of the ArduPilot name comes from Arduino used in some of its early development environment.

See [this article][15] for a larger list of FCs and more complete description.

* [Firmware for FPV Drone Flight Controller Overview][15]
* [Flight Controller Explained: Understanding FPV Drone Control Systems](https://oscarliang.com/flight-controller-explained/)
* [Flight Controller Processors Explained: F1, F3, F4, G4, F7, H7](https://oscarliang.com/f1-f3-f4-flight-controller/)

# What are F4, F7 and H7 Flight Controllers?
FC have evolved over time, so you will find

* mutiple physical sizes (45mmx45mm, 30mmx30mm, 20mmx20mm, 16mmx16mm),
* CPU classifications of speed & memory (F1 - 72MHz & 128KB, F3 - 72MHz & 256KB, F4 - 168MHz & 512KB to 1MB, F7 - 216MHz & 512KB to 1MB, and H7 - 480MHz & 2MB),
* bundled feature sets (FC only, FC + PDB + ESC, FC + PDB + OSD + VTX, FC + PDB + RX + OSD + ESC + SD Card)

F1, F3, F4 and F7 are the most commonly used processors in mini quads. F3 was the successor of F1, F4 was the successor for F3 and F7 was the replacement for F4. All these 4 processors are based on STM32 architecture which uses 32 bit processing
F4, F7 and H7 are the all great processors while F1 and F3 are no longer supported in the latest versions of Betaflight due to insufficient storage for the expanding firmware.

* **F1** processor is the oldest processor and has the lowest processing capability of all the above processors. It is actually an outdated processor with Betaflight ending support to F1 FC’s in 2017.
* **F3** was essentially a F1 FC with increased number of UART’s (It is discussed in detail below) and increased flash memory (memory used to store the FC’s firmware codes). Some smaller FC’s use this processor even now because of their compact size and exceptional processing power.
* **F4** was a giant leap in mini quad processors with more than double the processing power that of an F3. But there are limitations with F4 processors with no support for [SmartAudio][13] natively which is not a big deal for most people. Still F4 FC’s are the most popular choice for their functionality and affordability.
* **F7 / H7** processors are the big daddy of mini quad FC’s. F7 FC’s became available mid of 2018 and these are the most recent processors. F7 FC’s are packed with upto 8 UART’s which can be used for telemetry, GPS, camera control etc.., F7 FC’s come with dual Gyros (MPU6000 which is noise resistant and ICM20602 which can run 32K gyro sampling).

F4, F7 and H7 are the all great processors while F1 and F3 are no longer supported in the latest versions of Betaflight due to insufficient storage for the expanding firmware.

The FC can also serve as a hub for other drone peripherals like ESC, GPS, LED, servos, radio receiver FPV camera and VTX.
As technology advances, flight controllers are getting smaller, more feature-packed, and using better processors and hardware.

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
* [The Best Flight Controllers For FPV Drones](https://oscarliang.com/top-5-best-fc-mini-quad/)
* [One Board Does It ALL! F7 Flight Controller & 50 Amp ESC Loaded With Features All On One Board!!](https://www.youtube.com/watch?v=WiCGVKussyQ)

# Build or Buy Flight Controller (FC)
ArduPilot is a open source autopilot system supporting many vehicle types:
multi-copters, traditional helicopters, fixed wing aircraft, boats, submarines, rovers and more.
The source code is developed by a large community of professionals and enthusiasts.

* [Six Degrees Of Freedom Omnicopter With Ardupilot](https://hackaday.com/2021/01/09/six-degrees-of-freedom-omnicopter-with-ardupilot/)
* [ArduPilot](https://ardupilot.org/)
* [Cube Pilot](https://cubepilot.org/)
    * [What is CubePilot?](https://docs.cubepilot.org/user-guides/#what-is-cubepilot)

# SmartAudio for VTX Control
* [How to Setup SmartAudio for VTX Control (change VTX settings from OSD)](https://oscarliang.com/vtx-control/)



-------



# Flight Controller (FC)

## What is Betaflight?
[Betaflight][01] is the name of a flight control software, used for flying multi-rotor radio controlled aircraft.
Betaflight has its origins in the [Baseflight][02] and [Cleanflight][03] open source projects.
The intent of the Betaflight project was to create a high performance 'beta' testbed.
This project has grown into the most widely used flight firmware in the FPV drone racing and freestyle community,
mainly due to its cutting edge performance, features, reliability and wide range of hardware support.
This fork differs from Baseflight and Cleanflight in that it focuses on flight performance, leading-edge feature additions, and wide target support.

At the time of writing this document, Betaflight Configurator was at version 10.9.0,
Betaflight firmware was at version 4.4.2 (my [80mm Meteor75 Pro 1S][04] quadcopter arrived with 4.4.0 firmware),
and the flight controller was the [F4 1S 5A AIO Brushless Flight Controller (aka BETAFPVF411)][05].

Sources:
* [Betaflight 4.3 Complete Walkthrough](https://www.youtube.com/watch?v=LkBWRiEGKTI&list=PLwoDb7WF6c8nT4jjsE4VENEmwu9x8zDiE)
* [BF4.3 Complete Tuning Guide](https://www.youtube.com/watch?v=Ro4YMCLJ1dU&list=PLFPBjpbd5xKRnjNpYMep7MxovfhMBIzxP)
* [Betaflight 4.3 Rates Tuning: Rates are even more important than PIDs for flight feel in 4.3](https://www.youtube.com/watch?v=_WqKaJ79HGU)
* [Betaflight 4.4 Tuning Guide + Tips and Tricks for the BEST tune!](https://www.youtube.com/watch?v=sNAV4gx_gBY)
* [New Betaflight 4.4 features I'm actually excited about (get it yourself today!)](https://www.youtube.com/watch?v=YzE0V4GFzTw)

### Betaflight Configurator
Betaflight Configurator is a crossplatform (i.e. Windows, Mac, Linux) configuration tool for the Betaflight flight control system.
It runs as an application under different operating systems and allows you to configure the Betaflight software running on any supported Betaflight target. Downloads are available in Releases.
Various types of aircraft are supported by the tool and by Betaflight, e.g. quadcopters, hexacopters, octocopters and fixed-wing aircraft.

* [GitHub: betaflight/betaflight-configurator](https://github.com/betaflight/betaflight-configurator)
* [How to Download & Install Betaflight Configurator](https://www.youtube.com/watch?v=uXdDLCtR3Yo)
* [Betaflight 4.3 Install, Flash, Setup Tab | COMPLETE WALKTHROUGH PART 1](https://www.youtube.com/watch?v=LkBWRiEGKTI&list=PLwoDb7WF6c8nT4jjsE4VENEmwu9x8zDiE)

### Betaflight Mobile App
* [FPV APP You Should Have (iOS/Android Mobile)](https://oscarliang.com/fpv-app/)

# Electiconic Speed Controller (ESC)

## What is BLHeli_S?
BLHeli_S probably does not need an introduction - the wildly popular ESC firmware used on almost every EFM8 based ESC in the quadcopter hobby.
Tried and tested, supports every analog and digital protocol out there.

## What is BLHeli_32?
https://www.youtube.com/watch?v=BJQoXRqmCtE
https://github.com/blheli-configurator/blheli-configurator
https://play.google.com/store/apps/details?id=org.blheli.BLHeli_32&hl=en&gl=US

## What is ESC Configurator?
https://esc-configurator.com/



-------



## Install Betaflight

#### Step 1: Download Betaflight Configurator - DONE
The location of the latest Betaflight Configurator is located on [its GitHub page][30].
You find the link on the right within the "Releases" block.
In my case, the Betaflight Configurator version was 10.9.0.
This release contains all of the changes necessary to support version 4.4.0 of the Betaflight firmware.

```bash
# download the comnfigurator
cd ~/Downloads
wget https://github.com/betaflight/betaflight-configurator/releases/download/10.9.0/betaflight-configurator_10.9.0_amd64.deb

# install the .deb file
sudo dpkg -i betaflight-configurator_10.9.0_amd64.deb

# if you get an error on the dpkg command, run this
sudo apt --fix-broken install
```

The `betaflight-configurator` is now installed and ready to be executed but its not likley in you `$PATH`.
The installation process place the executable in the `/opt/betaflight/betaflight-configurator/` directory.
So you can execute the Betaflight Configurator by entering
`/opt/betaflight/betaflight-configurator/betaflight-configurator` on the commandline
or select the Betaflight Configurator icon from Ubuntu's **Activities** button at the top left of the screen.

>**NOTE:** According to the [Filesystem Hierarchy Standard][31],
>`/opt` is for "the installation of add-on application software packages".
>`/usr/local` is "for use by the system administrator when installing software locally".
>This convention (not widely inforced),
>is to avoid clashes with files that are part of the operating system,
>which would either be overwritten or overwrite the local ones otherwise.

If you wish to remove the `betaflight-configurator`, do the following:

```bash
# remove betaflight-configurator
sudo dpkg -r betaflight-configurator
```

Sources:
* [How to Download & Install Betaflight Configurator](https://www.youtube.com/watch?v=uXdDLCtR3Yo)
* [Betaflight on Linux Tutorial](https://www.youtube.com/watch?v=JH7hWao8bjE)
* [What is the difference between /opt and /usr/local?](https://unix.stackexchange.com/questions/11544/what-is-the-difference-between-opt-and-usr-local)

#### Step 2: Configure/Setup the Betaflight Configurator - DONE
Start the Betaflight Configurator (as describe in the earlier step),
and select the **Gear** on the left side menu column.
Select the following options:

* Permanently enable Expert Modes
* Reopen last tab on connection
* Advance CLI AutoComplete
* Enable virtual connect mode
* Enable show warnings

Now at the top right, make sure you in **Virtual Mode (Experimental)**.
Using a USB cable (capable of data and power delivery),
plugin the cable to you quadcopter (with the battery removed) and your computer.
Betaflight Configurator will likely atomatically connect to you quadcopter's flight controller.
If not, click on the **Connect** button at the top right.

Sources:
* [Betaflight 4.3 Install, Flash, Setup Tab | COMPLETE WALKTHROUGH PART 1](https://www.youtube.com/watch?v=LkBWRiEGKTI)




## Configure Your Flight Controller
* [Betaflight 4.3 EASY Setup Guide -- PRESETS FAST!](https://www.youtube.com/watch?v=znyiaN5dSxc)
* [Betaflight 4.3 Complete Walkthrough](https://www.youtube.com/watch?v=LkBWRiEGKTI&list=PLwoDb7WF6c8nT4jjsE4VENEmwu9x8zDiE)
* [BF4.3 Complete Tuning Guide](https://www.youtube.com/watch?v=Ro4YMCLJ1dU&list=PLFPBjpbd5xKRnjNpYMep7MxovfhMBIzxP)

#### Step 1: Screen Shot of Ports
Assuming you got a pre-configured flight controller for your quadcopter that works,
it is wise to record your port settings.
You do this so that when things don't work after you flash the firmware, you have it for your referance.

* Click the **Ports** tab so its deisplayed on your screen
* Take a screen shot.  I use window picture capture tool `import screenshot.png` on Ubuntu from the ImageMagick package.

Sources:
* see 1:22 minutes - [Betaflight 4.3 EASY Setup Guide -- PRESETS FAST!](https://www.youtube.com/watch?v=znyiaN5dSxc)

#### Step 2: Backup Flight Control Configuration - DONE
It’s important to always back up your Betaflight config before updating
Flight Controller firmware because it can erase your previous settings.

On the left side menu column,
select the **Presets** icon, which looks like a magic wand.
In the **Presets** tab, you have the buttons to **Save backup**, it will save it in a text file.
Press this button
The result is the same as entering `diff all` in **CLI**.

To restore it, simply use the **Load backup** button.

Sources:
* [How to Backup & Restore Betaflight Configuration](https://oscarliang.com/backup-restore-betaflight-config/)
* [Betaflight CLI | How to Restore Rotor Riot Settings](https://www.youtube.com/watch?v=D4AjJi8sUhM)
* [Betaflight 4.3 Install, Flash, Setup Tab | COMPLETE WALKTHROUGH PART 1](https://www.youtube.com/watch?v=LkBWRiEGKTI)

#### Step 3: Calibration of Accelerometer & Magnetometer - DONE
Now go to the **Setup** (Wrench icon) tab to calibrate the accelerometer.
To do this, set the quadcopter on a level surface and click the **Calibration Accelerometer** button.

To calibration magnetometer, you need to be away from metal objects and electrical fields.
In addition, you need to move the quadcopter in all directions.
Doing all this while connected to a USB cable near a computer is **not** going to give you great results.

To be more sucessful, there is a way to do this calibration in the field using just your radio transmitter.
This is demonstrated at 7:46 minutes on the video
["iNav Drone Complete Tutorial - Part 6 - Calibrate Compass and Accelerometer"][32]
and in [iNav's "Controls.md" documentation][33].

#### Step 4: Check Motor Order - DONE
Go to the **Motors** tab to make sure the motors are properly ordered and spin in the right direction.
See 3:44 minutes of the video ["Betaflight 4.3 EASY Setup Guide -- PRESETS FAST!"](https://www.youtube.com/watch?v=znyiaN5dSxc)
and 16:22 minutes of the video ["How I REALLY configure my own quadcopter"](https://www.youtube.com/watch?v=fC_EbT2J_m8)
for instruction on what must be done.

#### Step 5: Check and Change Motor Direction
You have to make sure the quadcopter's motors are spinning the correct direction
before putting propellers on for the first flight.
If one or multiple motors are spinning the wrong direction,
the quad will probably flip over, move erratically, or just not take-off.
The default motor spin directions is:
(1) all propellers spin into the front and back of the drone or,
(2) an alternative is all propellers spin out from the front & back.

You can reverse the rotation of the motor by simply swapping **any** 2 of the 3 wires between the motor and ESC.
It doesn’t matter which two wires, the result would be the same.
In some FC/ESC combinations you can make this change in Betaflight, but not always.

Using Betaflight, go to the **Motors** tab and click on **Motor direction**

If you **cannot** make the change via Betaflight,
you can either swap the motor wires, or simply change a setting in the ESC configurator without soldering.
To use the non-soldering way, you'll need to do it via [ESC Configurator](https://esc-configurator.com/)

* [ESC Configurator](https://esc-configurator.com/)
* [Bluejay ESC Firmware](https://betafpv.com/collections/brushless-flight-controller/products/f4-1s-5a-aio-brushless-flight-controller-elrs-2-4g)
* [How to Change Motor Direction in an FPV Drone?](https://oscarliang.com/change-motor-spin-direction-quadcopter/)

#### Step 6: Flight Controller Orientation - DONE
Go to the **Setup** tab to make sure the  FC orientation (aka heading, pitch, and roll) are proerply set.
See 7:02 minutes of the video ["Betaflight 4.3 EASY Setup Guide -- PRESETS FAST!"](https://www.youtube.com/watch?v=znyiaN5dSxc)
for instruction on what must be done.

#### Step X: Setup Your Betaflight Modes
* [Betaflight Modes Explained and How to Setup](https://oscarliang.com/betaflight-modes/)


-----



# Betaflight Presets
* [How to create your own Betaflight 4.3 presets and include them in the configurator](https://www.youtube.com/watch?v=OVDMQWwRlV4)
* [Betaflight 4.3 EASY Setup Guide -- PRESETS FAST!](https://www.youtube.com/watch?v=znyiaN5dSxc)
* [GitHub: Firmware Presets](https://www.youtube.com/watch?v=OVDMQWwRlV4)



-----



# Build & Flash Betaflight Firmware
* 10:01 minutes - Always back up your config before flashing! - [New Betaflight 4.4 features I'm actually excited about (get it yourself today!)](https://www.youtube.com/watch?v=YzE0V4GFzTw)
* 11:04 minutes - Cloud builds extend the life of older/slower hardware - [New Betaflight 4.4 features I'm actually excited about (get it yourself today!)](https://www.youtube.com/watch?v=YzE0V4GFzTw)
* 15:16 minutes - After flashing, how to safely restore your backup - [New Betaflight 4.4 features I'm actually excited about (get it yourself today!)](https://www.youtube.com/watch?v=YzE0V4GFzTw)



-----



# Betaflight Tuning
* [Build an FPV drone in 2023 - Part 8 - Betaflight Channel Mapping and Endpoints](https://www.youtube.com/watch?v=EDnQEep2X4I&list=PLwoDb7WF6c8l24IM83wIS94XzhuMVC2gx&index=8)
* [Build an FPV drone in 2023 - Part 9 - Betaflight Aux Modes](https://www.youtube.com/watch?v=ekgYYWN7eI4&list=PLwoDb7WF6c8l24IM83wIS94XzhuMVC2gx&index=9)
* [Build an FPV drone in 2023 - Part 10 - Betaflight Motor Setup](https://www.youtube.com/watch?v=CBZxFdJUFRg&list=PLwoDb7WF6c8l24IM83wIS94XzhuMVC2gx&index=10)
* [Build an FPV drone in 2023 - Part 11 - Final Betaflight Setup](https://www.youtube.com/watch?v=PJR_uiPi95M&list=PLwoDb7WF6c8l24IM83wIS94XzhuMVC2gx&index=11)


-----



# How to Setup Betaflight Firmware
* [How to Setup Betaflight Firmware](https://oscarliang.com/betaflight-firmware-setup/)

## Install Betaflight Configurator



-----



## Backup Flight Control Configuration
* [How to Backup & Restore Betaflight Configuration](https://oscarliang.com/backup-restore-betaflight-config/)

# Betaflight Tuning
* [Build an FPV drone in 2023 - Part 8 - Betaflight Channel Mapping and Endpoints](https://www.youtube.com/watch?v=EDnQEep2X4I&list=PLwoDb7WF6c8l24IM83wIS94XzhuMVC2gx&index=8)
* [Build an FPV drone in 2023 - Part 9 - Betaflight Aux Modes](https://www.youtube.com/watch?v=ekgYYWN7eI4&list=PLwoDb7WF6c8l24IM83wIS94XzhuMVC2gx&index=9)
* [Build an FPV drone in 2023 - Part 10 - Betaflight Motor Setup](https://www.youtube.com/watch?v=CBZxFdJUFRg&list=PLwoDb7WF6c8l24IM83wIS94XzhuMVC2gx&index=10)
* [Build an FPV drone in 2023 - Part 11 - Final Betaflight Setup](https://www.youtube.com/watch?v=PJR_uiPi95M&list=PLwoDb7WF6c8l24IM83wIS94XzhuMVC2gx&index=11)



-----



# GPS Sensor
* [Upgrade your drone GPS now! M10 receivers are here!](https://www.youtube.com/watch?v=eBzQLVYOy9Y)
* [Flywoo GM10 Mini V3 GPS - M10 For Under $20](https://www.youtube.com/watch?v=uXH0ToYuCcs)
* [Betaflight GPS Rescue Configuration (my best settings)](https://www.youtube.com/watch?v=-bYavyTRvx8)
* [Betaflight 4.4 GPS Rescue - Can You Now Trust It ?](https://www.youtube.com/watch?v=puN6glQ8GsQ)



-----



# FPV Simulators
If you play sims, you MUST be using EdgeTX 2.6 or later!
This version fixes a latance bug.

* [5 Best FPV Simulators (With Quick Reviews)](https://www.youtube.com/watch?v=Q288X0I-jIo)
* [Best PC FPV Simulator // WE TRIED THEM ALL](https://www.youtube.com/watch?v=I7lUTEJM62g)
    * [Orqa FPV.SkyDive](https://skydive.orqafpv.com/) - best of the free simulators, available on Windows & OSX & Stream
    * [VelociDrone](https://www.velocidrone.com/) - best FPV racing multi-player simulator, excellent physics (changes for battery, prop, etc changes), available on Windows & OSX
    * [Uncrashed](https://store.steampowered.com/app/1682970/Uncrashed__FPV_Drone_Simulator/) - best free-style simulator (no multi-player mode), available on Windows & OSX
    * [FPV FreeRider](https://fpv-freerider.itch.io/fpv-freerider) - best for minimal graphics / low spec PC's
    * [DRL Simulator](https://www.drl.io/drlsim) - best overall value, good onboarding for new pilots, available on Windows & OSX
    * Best Simulators for Micro-Quads
        * [VelociDrone](https://www.velocidrone.com/) - best overall, available on Windows & OSX
        * [Tiny Whoop Go](https://tinywhoopgo.com/) - best free, available on Windows & OSX
        * [LiftOff Micro-Drones](https://www.liftoff-game.com/our-products/liftoff-micro-drones) - models Joshua Bardwell flying yard, good training for indoor flying, available on Windows & OSX & Steam

* [The Best FPV Drone Simulators Round-up](https://oscarliang.com/fpv-simulator/#tldr-Herere-My-Favourites)
* [Linux FPV drone simulators](https://www.swalladge.net/archives/2019/11/15/fpv-drone-simulators-linux/)
* [Connect Any Transmitter To FPV Simulator | BETAFLIGHT GAME CONTROLLER](https://www.youtube.com/watch?v=wuobzowLfj0)

## What is Steam?
[Steam][20] is an online platform where you can download and play thousands of games on Linux,
and also discuss them with the community.
Steam can also use [Proton to play Windows games on Linux][21].
The [Proton compatibility layer][22] is changing the gaming landscape on Linux.

After purchase,  Steam client lets users install games directly to your Steam account in the cloud.
In addition, Steam users have the flexibility of posting their reviews, uploading self-made content, and more.
The Steam client also has several features, such as access to a friend list,
making an automatic update, in-game voice chat, and sharing games among friends.
Steam works on Windows, TV, mobile, Linux, and MacBook devices.
To use it, you just need a broadband connection to achieve a high-speed internet connection
and a modern system to play games unstoppably.

#### Step 1: Install Steam - DONE
First, go to the [Stream cloud store][20] and create an account.
You can do this via the login button at the top right.

```bash
# add the multiverse repository, which is a repository that includes non-free software titles
sudo add-apt-repository multiverse
sudo apt update

# install steam
sudo apt install steam
```

After the Steam installation completes, open Steam from the commandline via `stream` or from your desktop menu.
On its first run, Steam will download and apply a full update, so allow that to complete.

Now do the following:

1. Now install the free version FPV.SkyDive by first searching for it within the Steam client,
and then click to the icon to get to the "FPV SkyDive : FPV Drone Simulator",
then select "Play Game" or "Add to Library".
2. FPV.SkyDive will be installed within your `$HOME` directory within a hiden directory,
in my case `/home/jeff/.steam`.
3. On the Steam client, click the button **Play Now**.

* [How to install Steam on any Ubuntu-based Linux distro so you can play a world of games](https://www.zdnet.com/article/how-to-install-steam-on-any-ubuntu-based-linux-distribution-so-you-can-play-a-world-of-games/)
* [How to Install Steam on Linux and Play Your Favorite Games](https://geekflare.com/install-steam-on-linux/)

#### Step 2: Install




[01]:https://betaflight.com/
[02]:https://github.com/multiwii/baseflight
[03]:https://cleanflight.com/
[04]:https://betafpv.com/collections/brushless-series-except-hd/products/meteor75-pro-brushless-whoop-quadcopter
[05]:https://betafpv.com/collections/brushless-flight-controller/products/f4-1s-5a-aio-brushless-flight-controller-elrs-2-4g
[06]:
[07]:
[08]:
[09]:
[10]:

[13]:https://oscarliang.com/vtx-control/#:~:text=SmartAudio%20is%20a%20protocol%20between,settings%20remotely%20is%20so%20easy.
[14]:https://en.wikipedia.org/wiki/Proportional%E2%80%93integral%E2%80%93derivative_controller
[15]:https://oscarliang.com/fc-firmware/

[20]:https://store.steampowered.com/
[21]:https://www.howtogeek.com/738967/how-to-use-steams-proton-to-play-windows-games-on-linux/
[22]:https://www.howtogeek.com/752212/what-is-proton-for-steam-and-how-does-it-affect-gaming-on-linux/
[23]:
[24]:
[25]:
[26]:
[27]:
[28]:
[29]:
[30]:https://github.com/betaflight/betaflight-configurator
[31]:https://www.pathname.com/fhs/
[32]:https://www.youtube.com/watch?v=1x1zEUMZ7cc
[33]:https://github.com/iNavFlight/inav/blob/master/docs/Controls.md
[34]:
[35]:
[36]:
[37]:
[38]:
[39]:
[40]:

