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
[How to Tune Stick Response](https://www.youtube.com/watch?v=KnvONsC0dHU)






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
* Betaflight 4.3
    * [NEW Betaflight 4.3 - Full Setup & Walkthrough](https://www.youtube.com/watch?v=udOHBCORSrE)
    * [Betaflight 4.3 Complete Walkthrough](https://www.youtube.com/watch?v=LkBWRiEGKTI&list=PLwoDb7WF6c8nT4jjsE4VENEmwu9x8zDiE)
    * [BF4.3 Complete Tuning Guide](https://www.youtube.com/watch?v=Ro4YMCLJ1dU&list=PLFPBjpbd5xKRnjNpYMep7MxovfhMBIzxP)
    * [Betaflight 4.3 Rates Tuning: Rates are even more important than PIDs for flight feel in 4.3](https://www.youtube.com/watch?v=_WqKaJ79HGU)
    * [Betaflight 4.3.x Release](https://www.youtube.com/playlist?list=PLcYNkvInloJHTrzHe5vaucUEOL41Raqcl)
    * [Betaflight 4.3 Setup for Whoops](https://www.youtube.com/watch?v=xdcPO6NIUnc)
* Betaflight 4.4
    * [Betaflight 4.4 Tuning Guide + Tips and Tricks for the BEST tune!](https://www.youtube.com/watch?v=sNAV4gx_gBY)
    * [New Betaflight 4.4 features I'm actually excited about (get it yourself today!)](https://www.youtube.com/watch?v=YzE0V4GFzTw)
    * [Betaflight 4.4 Features DISAPPEAR ... because of Cloud Build?](https://www.youtube.com/watch?v=YmTq68M-NkU)
    * [Why Betaflight 4.4 GPS Sucks, and How To Fix It](https://www.youtube.com/watch?v=5fBDqeAoqvI)
* Betaflight 4.5
    * [These Betaflight 4.5 Features Are Worth Upgrading For!](https://www.youtube.com/watch?v=FMbBfef_R-g)
* General
    * [Calibrate & Trim Betaflight Tiny Whoop Accelerometer | HOW TO FIX ANGLE MODE](https://www.youtube.com/watch?v=otJNzZrE-yk)

### Betaflight Configurator
[Betaflight Configurator][06] is a crossplatform (i.e. Windows, Mac, Linux) configuration tool for the Betaflight flight control system.
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



# Betaflight Flight Modes
One of the features of Betaflight is the ability to configure multiple flight modes.
Flight modes allow the pilot to switch between different settings for the flight controller,
which can dramatically affect the behaviour of the quadcopter.

You can find all the modes in the **Modes** tab in Betaflight Configurator.
Within **Modes** that not all the modes are really flight modes,
some are feature related while others are event triggers.
I'm listing below some of the flight modes and event triggers / features.
See the "Sources" for more adetails.

* **Flight Modes**
    * **ACRO Mode** is the default mode (sometimes called manual mode and rate mode)
    is an aggressive flying style, where the word stands for “acrobatics”.
    The drone is flying without any assistance from the flight controller.
    Every movement will require direct command input from the pilot.
    Acro mode is considered the “[ultimate flight mode][07]” for FPV drone flying.
    The stick position dictates how fast the quadcopter will spin around the stick axis'.
    In Acro mode, you are controlling the drone’s angular velocity of rotation with the stick instead of the angle.
    That means if you push your pitch stick forward and hold it there,
    the drone will continue to rotate at a constant rate,
    instead of just remaining at an angle like it would in self-level mode.
    To return to its level position, you would have to move the stick to the opposition direction.
    * **ACRO TRAINER** s designed for beginners to safely learn to fly in acro mode.
    It’s basically ACRO mode with a tilt angle limit that prevents your drone from flipping over leading to crashes.
    * **ANGLE Mode** self-levels the quadcopter when the sticks are released to the cantered position.
    It limits the maximum angle the drone can tilt and so it won’t get out of control.
    It behaves like an assisted/stabilized quadcopter, making it easier for beginners to fly.
    * **HORIZON Mode** mode is basically Angle mode with the ability to do flips & rolls when the stick pass a certain threshold.
    When you move the sticks back to center the drone will self-level.
* **Event Triggers / Features**
    * **ARM** is a safty feature used to enable the quadcopter for flight.
    Once it’s armed, the motors will spin. If you have the **MOTOR STOP** option enabled
    the motors will not spin when the drone is armed until you increase throttle.
    * **GPS RESCUE** requires a working GPS module in your quadcopter.
    You can [configure GPS Rescue mode][08], when it’s activated, your drone should fly back to where it took off.
    * **FAILSAFE** will simulate a radio link loss. This is used for testing the quadcopter’s behaviour in failsafe.
    This is great if you are testing things like GPS rescue mode.
    * **AIRMODE** (aka Air Mode) is not really a flight mode, but a feature.
    You will not see this in the **Modes** tab but available in the Betaflight **Configuration** tab.
    It basically allows better control at zero throttle. This is particularly useful for freestyle and acrobatic flying.
    * **ANTI-GRAVITY** reduces dips (sudden pitch-down) on rapid throttle changes, [see this post for detailed explanation][09].
    Same as Airmode, if you have turn-on “Anti-Gravity – Permanently enabled” in the **PID Controller** tab,
    you won’t see this in the **Modes** tab.
    * **BEEPERON**, previously known as BEEPER.
    It’s for activating the buzzer in the drone (if available), useful for locating a crashed drone.
    * **BLACKBOX** is for starting and stopping [Blackbox logging][10].
    * **FLIP OVER AFTER CRASH**, also know as Turtle mode, is used when you’ve crashed and stuck up-side down,
    you can use this mode to “flip” your quadcopter over and hopefully take off again,
    so you don’t have to walk all the way over to pick it up.
    It does it by spinning one side of the motors in the opposite direction

There are two primary types of flight modes,
and most drones come equipped with them: the self-level mode and the acro mode.
To sum up the differences:

* Acro Mode (aka Rate & Manual Modes):
    * It uses only the Gyro sensor
    * Requires stick input to manually return to level
    * Pitch and roll inputs determine how **fast** the craft rotates around the axis
* Self-level Mode (aka Angle & Horizon Modes):
    * Uses both Gyro and Accelerometer sensors
    * Remains level without stick input
    * Pitch and roll inputs determine how **far** the craft will rotate on the given axis

>**NOTE:** Acro Trainer, Angle, and Horizon modes require the accelerometer and gyroscope to work.
>If these modes are missing in the Betaflight **Modes** tab,
>chances are you've disabled accelerometer or gyroscope in the Betaflight **Configuration** tab.

Sources:
* [Betaflight Modes Explained and How to Setup](https://oscarliang.com/betaflight-modes/)
* [Acro Mode vs. Self-Level Mode][07]
* [How to Setup GPS Rescue Mode in Betaflight][08]
* [Anti Gravity and I Term Relax][09]
* [Different Flight Modes for Drones](https://insidefpv.com/different-flight-modes-for-drones/)
* [Learn the Different FPV Drone Flight Modes & How to Set Up](https://academy.wedio.com/fpv-drone-flight-modes/)

## Two Main Flight Modes: Self-Level & Acro
The flight modes assist with how the flight controller (the computer chip that controls the drone's motors) helps the pilot with flying the drone.

In Self- level mode, the flight controller can take over as soon as the pilot takes their hands off the transmitter's sticks and keeps the drone level - this is why it is particularly recommended for beginners.

On the other hand, in Acro-mode, if the pilot takes their hands off the transmitter's sticks, the drone only continues its flight in the same orientation. This is why the pilot needs to hang tight and make constant adjustments.

## Self-Leveling Modes: Angle & Horizon
These are self-stabilization mode (Self-Leveling Modes) that  means the drone returns to horizon again after every stick input. So, unfortunately, no looping or flip is possible because there is always a maximum tilt angle.


### Angle Mode
Angle mode is a self-level mode that has to do with the tilt of your drone. Here, you need to learn how to properly move your roll/pitch stick to its top position.

So that you can still fly flips and loops with self-stabilization, there is an interim solution, the Horizon Mode.

In that way, the aircraft only reaches the maximum angle that it's allowed to tilt (generally 45 degrees, yet it is adjustable) while also ensuring it won't flip over.

As the stick reaches the centre once again, your drone will return to its initial position. Having this much control over your drone is ideal when shooting in tighter places.

## Acro Mode
Here's where things get a bit more complicated. As it is fully manual, Acro mode is the "ultimate flight mode" for freestyle flying and drone racing.

Levelling the aircraft falls entirely in your hands because letting go of the stick means its roll and pitch position remains the same. Constant adjustments are needed to keep the drone from crashing.

In Acro mode, you control the drone's rotation with the stick instead of the angle - hence, it is the perfect acrobatic mode.

That means if you push your pitch stick forward and hold it there, the drone will continue to rotate at a constant rate instead of just remaining at an angle like it would in self-level mode.

Returning to its level position requires moving the stick in the opposite direction.

Acro mode uses the RC sticks to control the angular velocity of the copter in each axis. Release the sticks and the vehicle will maintain its current attitude and will not return to level (attitude hold). Acro mode is useful for aerobatics such as flips or rolls, or FPV when smooth and fast control is desired.

Acro mode is where the flight controller changes the flight path of the drone with the help of the acceleration sensor.

You might notice that Acro mode isn't available as an option in the modes tab, and that's because Acro mode is automatically enabled as soon as you arm the quadcopter.

Here the acceleration sensor is switched off, and the drone is only held stable by the gyroscope. This means that if you’ve made a direction over the stick and let go of it, the drone will stay in exactly that position or inclination. So if you press to the left and tilt the drone to the left and then just let go of the stick stay the drone will tilt to the left and continue flying to the left.
this is the only way to fly loops and flips and the like in one fluid movement. In addition, you always have the same angle for the curve as long as the stick is in the center. To the left and right are only corrections of the flight curve, the racer does not start to leave his curve track on his own.

### Horizon Mode
The Horizon Mode (or Stability Mode) allows me to have the drone roll or yaw more than the maximum angle of inclination. This means that as long as I can move the stick forwards or sideways hold down the drone keeps turning. As soon as I let go of the stick, the drone starts to raise itself again.

Unlike Angle mode, you can do flips and rolls when the stick is at full deflection in Horizon mode. Though, when the pilot's hand leaves the controller, the craft level remains the same.

Doing flips in Horizon mode is not fully acrobatic and is sort of like a toy-grade push button flip.

When using both Angle and Horizon mode, you might run into a problem - they might be missing in the modes tab. This is because the accelerometer is disabled within Betaflight. Some people disable ACC because they only fly in Acro mode.

Disabling ACC will save some workload on the processor. There is a checkbox to enable/disable the accelerometer in the Configuration tab.

### Should I Fly Acro Mode?
For beginners, Self-Leveling or Horizon Mode may sound quite seductive.
But the self-stabilization causes an extremely unsteady behavior when you attempt any loops or acrbatic flying.
It may sound a bit strange for beginners, but the Acro Mode flies (as soon as you master it)
much quieter and more beautiful than anything else,
where the flight controller changes the flight path of the drone with the help of the acceleration sensor.

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
* [Chris Rosser PID Tuning Method](https://www.youtube.com/playlist?list=PLwoDb7WF6c8kaR47eDBKnF34aOoMNw4be)

* [Easy tuning guide for betaflight 4.4](https://www.youtube.com/watch?v=FGKRipkHU3Q)
* [Betaflight 4.4 Tuning Guide + Tips and Tricks for the BEST tune!](https://www.youtube.com/watch?v=sNAV4gx_gBY)
* [How to Get that Perfect PID Tune in Betaflight 4.4 | 2023](https://www.youtube.com/watch?v=N5DbiWFjbh8)



#### Step 1: Screen Shot of Ports
Assuming you got a pre-configured flight controller for your quadcopter that works,
it is wise to record your port settings.
You do this so that when things don't work after you flash the firmware, you have it for your referance.

* Click the **Ports** tab so its deisplayed on your screen
* Take a screen shot.  I use window picture capture tool `import screenshot.png` on Ubuntu from the ImageMagick package.

Sources:
* see 1:22 minutes - [Betaflight 4.3 EASY Setup Guide -- PRESETS FAST!](https://www.youtube.com/watch?v=znyiaN5dSxc)

#### Step 2: Backup Flight Controller Configuration - DONE
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

Now do this -
* [How to stop your drone drifting and calibrate the accelerometer!](https://www.youtube.com/watch?v=Z5IduP4HDfU)
* [Perfect Accelerometer Calibration](https://www.youtube.com/watch?v=jyP-U78P29Y)

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
To use the non-soldering way, you'll need to do it via [ESC Configurator](https://esc-configurator.com/).

Sources:
* [ESC Configurator](https://esc-configurator.com/)
* [Bluejay ESC Firmware][05]
* [How to Change Motor Direction in an FPV Drone?](https://oscarliang.com/change-motor-spin-direction-quadcopter/)

#### Step 6: Flight Controller Orientation - DONE
Go to the **Setup** tab to make sure the  FC orientation (aka heading, pitch, and roll) are proerply set.
See 7:02 minutes of the video ["Betaflight 4.3 EASY Setup Guide -- PRESETS FAST!"](https://www.youtube.com/watch?v=znyiaN5dSxc)
for instruction on what must be done.

#### Step X: Setup Your Betaflight Modes
* [Betaflight Modes Explained and How to Setup](https://oscarliang.com/betaflight-modes/)

#### Step X: Setup Turtle Mode (Flip Over After Crash) - DONE
Turtle mode (now called “Flip Over After Crash” in Betaflight) allows a user to attempt to flip the quadcopter upright, if inverted,
by reversing the direction of adjacent pairs of motors
and producing thrust to un-invert the vehicle after a crash.
Once in this mode, moving the roll and/or pitch stick of the transmitter away from center
will reverse and spin up the designated pair of motors,
increasing thrust to maximum at full stick throw.
The user can quickly jab the transmitter stick to attempt to flip the vehicle upright.
Once flipped upright, exit the mode for normal operation to resume.

The procedurely, Turtle mode cannot be entered unless throttle is zero.
Upon entry to turtle mode the motors stay disarmed, but the notfiy LEDs flash.
Raising the throttle, the motors arm, and motors spin. Lowering throttle to zero disarms the motors.
Motors spin only when throttle is raised.

>**NOTE:** [DShot][34] capable ESCs are required for this mode to function,
>allowing the DShot reverse command to be sent to the ESCs.
>`SERVO_DSHOT_ESC` must be set to “1” also to allow DShot commands to be sent.

To setup Turtle mode:
1. In Betaflight Configurator, **Motors** tab, select DShot protocol (DShot150, 300 and 600 all support turtle mode).
1. Goto the **Configuration** tab, set “Maximum Arm Angle” (Arming) to 180.
1. On Betaflights **Modes** tab, assign a switch on your radio to “Flip Over After Crash”. ( **NOTE:** “Flip Over After Crash” option would be missing and won’t appear until you have selected DShot Protocol.)

How to Use Turtle Mode?
1. When the quadcopter is flipped over, set "SA" switch to **Disarmed** and set throttle to zero.
2. Turn on Turtle mode via the "SD" switch, then set "SA" to **Armed** it (motors should NOT spin, yet)
3. Use your roll stick, the motors will start to spin and flip the quadcopter over; the longer you hold the roll stick, the more thrust it will generate
4. Once turned over, disarm immediately and turn off turtle mode
5. Now arm the quad again to take off

You might want to practice using Turtle mode on a flat surface, clear of people.
It might also help to get your quadcopter out of a tree if it gets stuck.
**DO NOT** overuse and force it if you can’t turn the quad over, it could burn out the motors and ESC’s.

Do you want to try this? ....
* [Edge TX Tricks - Double Arm to Turtle Mode on Jumper T-Pro](https://www.youtube.com/watch?v=3XmtHtgUxH0)
* [This EdgeTX "custom curve" makes turtle mode even better!](https://www.youtube.com/watch?v=22ueY-bvGnI)
* [activate OpenTX turtle mode with a momentary switch.](https://www.youtube.com/watch?v=g5bbTd8bK58)

Sources:
* [OpenTx Quick Tip – Setting Up Flip Over After Crash (Turtle) Mode](https://www.youtube.com/watch?v=Nuf3YptbjXw)
* [How to Setup Turtle Mode (Flip Over After Crash in Betaflight)](https://oscarliang.com/setup-turtle-mode-flip-over-after-crash/)
* [How to setup TURTLE MODE in BETAFLIGHT 2022 (Tutorial)](https://www.youtube.com/watch?v=jibqPPc4I9o)
* [This EdgeTX "custom curve" makes turtle mode even better!](https://www.youtube.com/watch?v=22ueY-bvGnI)
* [This "custom curve" makes turtle mode even better!](https://www.youtube.com/watch?v=22ueY-bvGnI)
* [Test Your Motors With Turtle Mode](https://www.youtube.com/watch?v=OhF-yngHRe4)

#### Step X: Dshot Motor Beeper to Help Find Quadcopter
* [Just The Tip - Ep 01 - Dshot Motor Beeper](https://www.youtube.com/watch?v=zWR0B7xqwMg)

#### Step X: Making Custom Voice Tracks & Sounds
I'm going to use [Audacity][16] to record the sound files that we'll install in EdgeTX.
I'll use a text-to-speech website called [TTS Demo][17] to create the spoken words that I need.

To install Audacity on my Ubuntu system, I used Snap using the procedure below:

```bash
# install snap
sudo apt update
sudo apt install snapd

# install audacity
sudo snap install audacity
```

Now follow the procedure in the source material, and you can create custom voice tracks for EdgeTX.

Sources:
* [OpenTX – Making Custom Sounds](https://www.youtube.com/watch?v=DqF7HUsFrnE)

#### Step X: Set Crash Recovery
* Crash Recovery - [Winning Whoop racers use Betaflight crash_recovery. Should you?](https://www.youtube.com/watch?v=5YyxIft9wKM&t=8s) vs Angle Mode - [Betaflight Angle Mode is about to get AWESOME! You can try it TODAY](https://www.youtube.com/watch?v=ILeLo1lWjBk)

#### Step X: Set Beeper On
* [Betaflight Modes Explained and How to Setup](https://oscarliang.com/betaflight-modes/)
* [Buzzer for Quadcopters](https://oscarliang.com/buzzer-quadcopters/)
* [Adding a Buzzer to the HGLRC Sector 5D](https://www.youtube.com/watch?v=mq1qKOL7H28)
* [Using ESC Beacon (Motor) as Lost Model Alarm](https://oscarliang.com/esc-beacon-lost-model-alarm/)

#### Step X: 3-Position Switch for Acro / Angle / Horizon Modes
[Betaflight Air Mode is bad for Whoops. Until now. Maybe.](https://www.youtube.com/watch?v=tCTI2J0QCwc&t=225s)

#### Step X: Set AirMode On or Off?
While called a "mode", its not really a flight mode, its a feature.

You'll find the AirMode feature in Betaflight's **Configuration** tab in hte **Other Features** section.
If you turn it on, then you can't turn it off while flying.
The result will be bouncing while landing and sticking to objects (e.g. walls) when you crash.
You can generally turn off AirMode if your not doing flips and rolls; which you are not if your in the early learning to fly stage.
So we will turn Air Mode off in Betaflight **Configurator** tab.

You'll also see setings for the AirMode feature in the Betaflight **Modes** tab.
Here we will enable Air Mode for Angle & Horizon Modes, but turned off when in Acro Mode.
This is explained in - [Why does my quadcopter bounce around on landing?](https://www.youtube.com/watch?v=5NIQguIzO94)

An alternative approach is given here - [Betaflight Air Mode is bad for Whoops. Until now. Maybe.](https://www.youtube.com/watch?v=tCTI2J0QCwc&t=225s)

Sources:
* What is Air Mode?
    * [Simple Explanation of Airmode](https://www.youtube.com/watch?v=hHl-83FSyD8)
    * [AIR MODE Flight Demo FPV - What is Air Mode? Air Mode VS Acro?? Airmode Explained](https://www.youtube.com/watch?v=HQ3ceM5LTEA)
    * [Betaflight Airmode](https://oscarliang.com/betaflight-airmode/)
* Stop Bouncing Landings & Sticking to the Wall
    * [Why does my quadcopter bounce around on landing?](https://www.youtube.com/watch?v=5NIQguIzO94)
    * [How To Land In Air Mode | BETAFLIGHT CLEANFLIGHT](https://www.youtube.com/watch?v=Y9FPOy8C6I4)
    * [Betaflight Air Mode is bad for Whoops. Until now. Maybe.](https://www.youtube.com/watch?v=tCTI2J0QCwc&t=225s)
* AirMode vs Idle Up
    * [What is Airmode? | BETAFLIGHT WITH AIR MODE EXPLAINED](https://www.youtube.com/watch?v=d2nRrVENEYM)
    * [How To Land In Air Mode | BETAFLIGHT CLEANFLIGHT](https://www.youtube.com/watch?v=Y9FPOy8C6I4)


* [Betaflight Air Mode is bad for Whoops. Until now. Maybe.](https://www.youtube.com/watch?v=tCTI2J0QCwc&t=225s)
* [Using Air Mode AND Idle Up?](https://www.youtube.com/watch?v=-oUFIwSRMtM&t=5s)
* [How To Land In Air Mode | BETAFLIGHT CLEANFLIGHT](https://www.youtube.com/watch?v=Y9FPOy8C6I4&t=21s)
* [EdgeTX Landing (or perching) mode - disable Air mode with a momentary switch and re-enable on throttle up](https://www.reddit.com/r/fpv/comments/11j1nvg/edgetx_landing_or_perching_mode_disable_air_mode/)


## AirMode vs Idle Up
Idle Up proceeded Air Mode in Betaflight.

Idle Up is set up in the transmitter to asure that the throttle is down at zero level is not completely stopping the motors so you retain flight control.

Air Mode is set in the flight controller (Betaflight) increases command authority at low throttle. You can lower you throttle as far as you wish.


* [What does NOT work in Angle Mode](https://www.youtube.com/watch?v=AI_-v30j58Q)

* Part 1 - [Air Mode vs Idle Up - what's the difference?](https://www.youtube.com/watch?v=zkTqc2CF3-g)
* Part 2 - [Using Air Mode AND Idle Up?](https://www.youtube.com/watch?v=-oUFIwSRMtM)

* [Behind the Scenes - FPV Airmode Off](https://www.youtube.com/watch?v=KW1Ysb5BqGo)

* [Throttle IDLE UP Step by Step! Setup | AIRMODE 👎| Ethix](https://www.youtube.com/watch?v=oMQidtp0F0k)
* [Idle up for Betaflight (Full tutorial version)](https://www.youtube.com/watch?v=jYhmNwDT-qI)

* [Betaflight 4.2 Low Throttle Instability How To Fix](https://www.youtube.com/watch?v=TeYMJy23vK4)

## Dynamic Idle (aka Dynamic Notch ??) Bug
[Propwash][12] is the airflow generated by an aircraft's propeller,
which can have significant effects on the performance of the aircraft, particularly during takeoff and landing.

* [What causes Propwash and how Betaflight Dynamic Idle can help!](https://www.youtube.com/watch?v=CAMcRbQh3xM)
* [Betaflight 4.4 Potential Dynamic Idle Bug](https://www.youtube.com/watch?v=97Hk2nTWHsY)

#### Step X: Set-up Betaflight Lau Script
* [Everybody should be using these FPV Lua Scripts](https://www.youtube.com/watch?v=RCS72GVR0gs)
* [Setup Betaflight LUA Script on OpenTX Radios](https://oscarliang.com/setup-betaflight-lua-script/)
* [Betaflight LUA • How-To Change Betaflight Settings From Your Radio • No Bluetooth/Wifi Required](https://www.youtube.com/watch?v=mEpbO9tD62k)


-----



# Betaflight Presets
* [How Do I Find A Good Preset In Betaflight For My FPV Drone?](https://www.youtube.com/watch?v=noksDbMM5vo)
* [How to create your own Betaflight 4.3 presets and include them in the configurator](https://www.youtube.com/watch?v=OVDMQWwRlV4)
* [How To Create Presets | Betaflight 4.3](https://www.youtube.com/watch?v=f5Ev8E-Vju4)
* [Betaflight 4.3 EASY Setup Guide -- PRESETS FAST!](https://www.youtube.com/watch?v=znyiaN5dSxc)
* [GitHub: Firmware Presets](https://www.youtube.com/watch?v=OVDMQWwRlV4)

* [Using Betaflight Presets | TIPs on Creating Presets](https://www.youtube.com/watch?v=abnKNv1dICQ)

When I started out with Acro mode (after breaking some props), i just practiced hovering at about a foot above ground, going front/back and left/right. If i felt too nervous or freaked out, i would just drop it and at that height i never damaged anything.



-----



# Build & Flash Betaflight Firmware
* 10:01 minutes - Always back up your config before flashing! - [New Betaflight 4.4 features I'm actually excited about (get it yourself today!)](https://www.youtube.com/watch?v=YzE0V4GFzTw)
* 11:04 minutes - Cloud builds extend the life of older/slower hardware - [New Betaflight 4.4 features I'm actually excited about (get it yourself today!)](https://www.youtube.com/watch?v=YzE0V4GFzTw)
* 15:16 minutes - After flashing, how to safely restore your backup - [New Betaflight 4.4 features I'm actually excited about (get it yourself today!)](https://www.youtube.com/watch?v=YzE0V4GFzTw)



-----



# Betaflight Tuning
Tuning an FPV quadcopter means adjusting settings in the flight controller software to make it fly the way we want.
Not just PID gains, there are many settings in Betaflight that affect flight characteristics,
including Feedforward, filters, rates and expo etc.
The amount of settings can be overwhelming even for experienced pilots,
but few key settings should be enough to improve your flying.
Your objects are:

* smooth cruising, no oscillation, wobbles or drifting
* no bounceback when doing flips and rolls
* as little propwash and wobble as possible when doing extreme manoeuvre
* the drone feels locked in and responsive to sticks

* [How to tune Betaflight 4.3 PIDs and Feedforward like a MAD SCIENTIST! Featuring the AOS 5 V2](https://www.youtube.com/watch?v=Hrijk8d1brg)

* [Basement tuning just got a lot easier! - USE ANGLE MODE!](https://www.youtube.com/watch?v=sqT4MACi3d8)

* [PID Tuning](https://www.youtube.com/playlist?list=PLPlPgQFfbIvEF6F7JmSgt17p3WMovM0pi)

* [Build an FPV drone in 2023 - Part 8 - Betaflight Channel Mapping and Endpoints](https://www.youtube.com/watch?v=EDnQEep2X4I&list=PLwoDb7WF6c8l24IM83wIS94XzhuMVC2gx&index=8)
* [Build an FPV drone in 2023 - Part 9 - Betaflight Aux Modes](https://www.youtube.com/watch?v=ekgYYWN7eI4&list=PLwoDb7WF6c8l24IM83wIS94XzhuMVC2gx&index=9)
* [Build an FPV drone in 2023 - Part 10 - Betaflight Motor Setup](https://www.youtube.com/watch?v=CBZxFdJUFRg&list=PLwoDb7WF6c8l24IM83wIS94XzhuMVC2gx&index=10)
* [Build an FPV drone in 2023 - Part 11 - Final Betaflight Setup](https://www.youtube.com/watch?v=PJR_uiPi95M&list=PLwoDb7WF6c8l24IM83wIS94XzhuMVC2gx&index=11)

## Acro Mode vs. Acro Trainer Mode
* [Betaflight 3.4 | Acro Trainer Mode (use this instead of angle mode)](https://www.youtube.com/watch?v=vH3eH7yI2SY)

* [Acro Mode vs. Self-Level Mode][07]

## Acro Mode vs Angle Mode
Angle mode uses a earth coordinate system.

* [Betaflight Angle Mode is about to get AWESOME! You can try it TODAY](https://www.youtube.com/watch?v=ILeLo1lWjBk)
* [Angle vs Acro Tiny Whoops In 2023](https://www.youtube.com/watch?v=MTIx3tyqz6U&t=70s)

## Learning & Tuning for a Newbee
* [How To Get Started With FPV Drone – The Ultimate Beginner’s Guide](https://oscarliang.com/fpv-drone-guide/)
* [Learn How to Fly FPV Drones – Tips and Practice](https://oscarliang.com/learn-flying-fpv-multirotors/)
* [Trouble Learning FPV – How to Improve my Flying?](https://oscarliang.com/learn-fpv-flying-faster/)

* [Acro Mode vs. Self-Level Mode][07]
* [Learn How to Fly FPV Drones – Tips and Practice](https://oscarliang.com/learn-flying-fpv-multirotors/)
* [Demystifying FPV Drone Rates: Betaflight & Actual Rates Explained](https://oscarliang.com/rates/)

* [Betaflight FPV Drone Tuning In 10 Simple Steps](https://oscarliang.com/fpv-drone-tuning/)
* [How to Tune FPV Drone Filters and PID with Blackbox][11]

The posting [Flying with stabilzation off...AUGHHHHH!!](https://intofpv.com/t-flying-with-stabilzation-off-aughhhhh)
and [Learning to Fly](https://intofpv.com/t-learning-to-fly) says the following:
* If you are all on default Rates for Pitch , roll and yaw you could go to the receiver Tab in cleanflight and adjust RC Rate, back it off to a good beginner start point of around 0.70, and then alter Expo to about 80, save and test fly.
* If your Rates for Roll, pitch and yaw are already populated with numbers like 0.70 etc Tone them down, it will make the quad very twitchy for a newbie on Rate mode.
* The part you need to train yourself on is Stick control. No more large aggressive stick movements in rate mode, as we all start off in rate we tend to just slam the sticks left and right up and down like when in Angle or Horizon modes, that is because we are fighting the stabilization. So, nice small movements on the sticks will make all the difference.
* Things to consider and get your head around. In stabilized modes when you roll, pitch or yaw and centre the sticks stabilization modes always try to bring the quad back to level, with rate mode if you pitch forward say 2mm stick the quad will tilt forward and hold that angle until you apply the opposite amount of back stick, self level modes will do this for you automatically.
* Set out a course like a figure 8 and use markers as a pathway, and practice flying the figure 8, don't focus on flips and rolls and all that cool stuff yet, just get to grips with control. Again I say..small stick inputs, and remember to use opposite stick to centre the quad again, as YOU, as the pilot are now the self leveller.
* When I started out with Acro mode (after breaking some props), i just practiced hovering at about a foot above ground, going front/back and left/right. If i felt too nervous or freaked out, i would just drop it and at that height i never damaged anything.

## Smoother Flights for Chinewhoops
* [Tips for Smoother Cinewhoop Flying](https://www.youtube.com/watch?v=IULJbyXzLXs)
* [Cinewhoop Betaflight Settings for Real Estate Fly Through Videos Tutorial | FPV Drones](https://www.youtube.com/watch?v=MK0i2Rd3B94)

## How to use Blackbox in Betaflight
It’s recommended to use “Blackbox” to tune your drone. Blackbox is a powerful tool that records flight data during your drone’s flight, providing valuable insights for tuning. By analyzing the data, you can fine-tune your drone’s PID settings and filters to achieve better performance..

* [How to use Blackbox in Betaflight FPV Drones][10]
* [How to Tune FPV Drone Filters and PID with Blackbox][11]
* [BetaFlight black box logging complete beginners setup guide. So easy a greasy FPV ninja can do it!](https://www.youtube.com/watch?v=J8-JUlw993A)
* [Download Betaflight Configurator & Blackbox Explorer](https://oscarliang.com/download-betaflight-configurator/)
* [How To Tune an FPV Drone with Black Box Logging for High Performance Freestyle](https://www.youtube.com/watch?v=xpNU4mDV7ew)

### How to use PIDToolBox and Blackbox Explorer
PIDtoolbox is a set of graphical tools for analyzing Blackbox log data.
Blackbox Explorer is an interactive log viewer for flight logs recorded with Blackbox.

* [PIDtoolbox](https://www.youtube.com/@PIDtoolbox)
* [PIDtoolbox](https://github.com/bw1129/PIDtoolbox)
* [PIDtoolbox: Professional PID Tuning Consultation](https://pidtoolbox.com/)
* [Interview with Brian White: The CREATOR of PID Toolbox!](https://www.youtube.com/watch?v=osd2RD62pfY)

* [Betaflight Blackbox Explorer](https://github.com/betaflight/blackbox-log-viewer)
* [Enhanced Blackbox Explorer](https://amir.ch/blackbox/)

#### Step X: Minimize Drone Drifting
There are a few common culprits of quadcopters not hovering inplace and drift about.
Here are the seven that could be causing this issue:

* **Imbalance of Weight** - For a stable drone flight, the centre of mass is essential. Even though drone motors can handle the imbalance weight of the drone, they will still drift around in the sky.
* **Accelerometers Need Calibrating** - Proper calibration of the drone will ensure that the sensors provide accurate information to the drone software. When the drone is properly calibrated, the functioning of both hardware and software will keep the drone stable and safe from collision.
* **Transmiter Gimbal Calibration** -
* **Transmitter Settings** -
* **Motor or ESC Problems** -
* **Propeller Issues** - Some drones have different propellers for each motor because of the placement of motors and design frame. In other cases the propelers might be damaged and need to be replaced.
* **Not in GPS Mode** -

* [Why does my drone drift? 5 simple things to check](https://www.youtube.com/watch?v=DnUH-zQc7U4)
* [How To Fix Drone Drift? (7 Ways To Fix)](https://www.droneihave.com/how-to-fix-drone-drift/)
* [Why does my drone fly backwards?](https://droneflyingpro.com/why-does-my-drone-fly-backwards/)
* [Calibrate & Trim Betaflight Tiny Whoop Accelerometer | HOW TO FIX ANGLE MODE](https://www.youtube.com/watch?v=otJNzZrE-yk)

#### Step X: PID Tuning / Rate Profile Settings
**Important** ...
* [Find YOUR perfect rates! With science!](https://www.youtube.com/watch?v=Ql62iRkLX3s)
* [I turned BF rates to max and learned something profound](https://www.youtube.com/watch?v=nJ-V7EAnpig&t=660s)
* [Betaflight Rates tuning. How to make your quad feel right for the way you like to fly.](https://www.youtube.com/watch?v=RneayCxDN4A&t=354s)
* [Betaflight 4.3 Rates Tuning: Rates are even more important than PIDs for flight feel in 4.3](https://www.youtube.com/watch?v=_WqKaJ79HGU)
* [Betaflight 4.2 what are ACTUAL RATES and how to convert them](https://www.youtube.com/watch?v=m3A9xgRmcws)

Rate profile name: Indoor

Rate Type: Actual

These are Betaflight defaults rates for the :
| Stick | Center Sensityity | Max Rate | Expo |
|:------|:-----------------:|:--------:|:----:|
| Roll  |        70         |    670   | 0.00 |
| Pitch |        70         |    670   | 0.00 |
| Yaw   |        70         |    670   | 0.00 |

These are my latest Betaflight rates:
| Stick | Center Sensityity | Max Rate | Expo |
|:------|:-----------------:|:--------:|:----:|
| Roll  |        70         |    620   | 0.50 |
| Pitch |        70         |    490   | 0.35 |
| Yaw   |        70         |    380   | 0.20 |

**Try this** at 1:36 minute - [These Actual Rates are Actually Butter: Finding the Right Actual Rates For You](https://www.youtube.com/watch?v=_aBU--FWH94)

These will give me more sensitivity in the throttle:
| Throttle Setting | My Value | Default |
|:-----------------|:--------:|:-------:|
| Throttle Limit   |   SCALE  |   OFF   |
| Throttle Limit % |    80    |   100   |
| Throttle MID     |   0.25   |  0.50   |
| Throttle EXPO    |   0.75   |  0.00   |

Sources:
* [Betaflight OpenTX Throttle Scaling | TAME YOUR 2S TINY WHOOP](https://www.youtube.com/watch?v=K7t6U_2dLlk)
* [Betaflight Rates tuning. How to make your quad feel right for the way you like to fly](https://www.youtube.com/watch?v=RneayCxDN4A&t=14s)
* [Adjusting Throttle Curve in Betaflight and EdgeTX: Tips for Smoother Throttle Control](https://oscarliang.com/throttle-curve/)



-----



# How to Setup Betaflight Firmware
* [How to Setup Betaflight Firmware](https://oscarliang.com/betaflight-firmware-setup/)

## Install Betaflight Configurator



-----



## Backup Flight Control Configuration
Within Betaflight, go to the **Presets** tab.

Source:
* [How to Backup & Restore Betaflight Configuration](https://oscarliang.com/backup-restore-betaflight-config/)



-----



# GPS Sensor
* [Just The Tip - Ep 03 - My Betaflight 4.2 / 4.3 GPS Rescue Setup & Settings - How To Set Any Quad](https://www.youtube.com/watch?v=5BCYAbUFfeU)
* [Just The Tip - Ep 04 - OpenTX / EdgeTX Secrets Revealed - Min Sats Alert & Display GPS Coordinates!](https://www.youtube.com/watch?v=Bnz-Sa3MtXU)

* [Upgrade your drone GPS now! M10 receivers are here!](https://www.youtube.com/watch?v=eBzQLVYOy9Y)
* [Flywoo GM10 Mini V3 GPS - M10 For Under $20](https://www.youtube.com/watch?v=uXH0ToYuCcs)
* [Betaflight GPS Rescue Configuration (my best settings)](https://www.youtube.com/watch?v=-bYavyTRvx8)
* [Betaflight 4.4 GPS Rescue - Can You Now Trust It ?](https://www.youtube.com/watch?v=puN6glQ8GsQ)



[01]:https://betaflight.com/
[02]:https://github.com/multiwii/baseflight
[03]:https://cleanflight.com/
[04]:https://betafpv.com/collections/brushless-series-except-hd/products/meteor75-pro-brushless-whoop-quadcopter
[05]:https://betafpv.com/collections/brushless-flight-controller/products/f4-1s-5a-aio-brushless-flight-controller-elrs-2-4g
[06]:https://github.com/betaflight/betaflight-configurator/releases
[07]:https://oscarliang.com/rate-acro-horizon-flight-mode-level/
[08]:https://oscarliang.com/setup-gps-rescue-mode-betaflight/
[09]:https://oscarliang.com/fpv-drone-tuning/#Step-6-Anti-Gravity-and-I-Term-Relax
[10]:https://oscarliang.com/blackbox/
[11]:https://oscarliang.com/pid-filter-tuning-blackbox/
[12]:https://skybrary.aero/articles/prop-wash
[13]:https://oscarliang.com/vtx-control/#:~:text=SmartAudio%20is%20a%20protocol%20between,settings%20remotely%20is%20so%20easy.
[14]:https://en.wikipedia.org/wiki/Proportional%E2%80%93integral%E2%80%93derivative_controller
[15]:https://oscarliang.com/fc-firmware/
[16]:https://www.audacityteam.org/
[17]:https://ttsdemo.com/

[20]:https://store.steampowered.com/

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
[34]:https://www.youtube.com/watch?v=okUrPLP_Eec
[35]:
[36]:
[37]:
[38]:
[39]:
[40]:

