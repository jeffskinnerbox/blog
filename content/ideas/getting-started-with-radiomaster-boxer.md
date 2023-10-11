<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----


**ExpressLRS v3.3.0 is out now! Check it out on GitHub.** - https://github.com/ExpressLRS/ExpressLRS
**EdgeTX "Providence" v2.9.1** - https://buddy.edgetx.org/#/flash



After much much online research and grinding of my teeth,
I settled on the [RadioMaster Boxer][01] as my Radio Transmitter / Controller
(and a [big battery][04]) for my quadcopter build project.
It came with a carrying case and I purchased it through Amazon for $160 in October of 2023.
The reviews were great, it feels right in my hands,
and it attempts to address all the trouble spots in previous generation of RadioMaster products.
It naively supports [EdgeTX][02] and [ExpressLRS][03] (making it "cutting edge"...for now),
with nearly all the features of the [RadioMaster TX16S][05] except for weight/large-size,
it abundance of switches, and the slick color touch-screen user interface.

I used the following articles and videos to help make the selection of the RadioMaster Boxer:

* [Choosing the Best Radio Transmitter for Your FPV Drone: A Beginner’s Guide](https://oscarliang.com/radio-transmitter/)
* In 2022 - [How To Buy Your First FPV Controller](https://www.youtube.com/watch?v=wpZ8xKIaNgs)
* In 2023 - [How To Buy Your FIRST FPV Controller (2023)](https://www.youtube.com/watch?v=4mBPew9HIfw)
* [Why I Fly ExpressLRS, Not Crossfire](https://www.youtube.com/watch?v=Wy9SmlijVOI)
* [I can't believe how good this radio feels // RADIOMASTER BOXER REVIEW](https://www.youtube.com/watch?v=5Fi9csa-wP8)
* [Affordable FPV Controllers That DON’T SUCK!](https://www.youtube.com/watch?v=Az5G4nq8F3M)
* [Cheap vs. Expensive FPV Controllers - What's the Difference?](https://www.youtube.com/watch?v=SrN6ps4NM10)
* [2023 BEST Radios for Fpv Drones - BUYER'S GUIDE](https://www.youtube.com/watch?v=KOYla-wqFYg)

# Buttons, Switches, and Knobs
* **SYS** -
* **RTN** -
* **PAGE >** -
* **PAGE <** -
* **TELE** -

* **MDL** -
* **Skroll/Select** -

* **T1** -
* **T2** -
* **T3** -
* **T4** -

* **SA** -
* **SB** -
* **SC** -
* **SD** -

* **S1** -
* **S2** -

* **SE** -
* **SF** -



-----



# Setup RadioMaster Boxer

* [How To Setup Radiomaster Boxer ExpressLRS in 5 Minutes](https://www.youtube.com/watch?v=biY5iH1Wz7I)

## Configure EdgeTX Radio Settings

#### Step 0: Get Things Ready - DONE
I installed the battery and charged it in the Boxer.
I also found the latest user manuals for [RadioMaster][06], [EdgeTX][07], and [ExpressRLS][08].

Batteries and charging
Boxer has a built-in USB-C charging function for 3.7V lithium batteries. The charging circuit is only designed
to charge 2x 3.7V Li-ion 18650 or 2x 3.7V Li-Poly batteries (2s 7.4v Lipo battery pack), the nominal battery
voltage is 3.7V, the charged voltage is 4.2V/Cell.
Do not use LiFE battery packs or 18650 lithium-ion batteries with a nominal voltage of 3.6v with a fully
charged voltage of 4.10V. Charging the incorrect type of battery may damage the charger or cause a fire.
If using Li-ion, ensure the cells are not protected and are button-top cells.
Please check the voltage and condition of the battery regularly and never charge unattended. Always charge

ANTENNA: Install the provided antenna in the top of the radio BEFORE installing batteries and turning on the
radio. DO NOT operate the radio without the antenna installed and the internal RF module powered on. Doing
so will damage the internal RF module and will not be covered under warranty.

#### Step 1: Power Up the Boxer - DONE
Press the power button and hold until all four boxes appear on the screen.
If you get a throttle warning, move the throttle gimbal all the way down.
If you get a switch warning, move all the swithced to the up position.

In the unlikely event that you need to update the "MODELS" folder on the Boxer,
follow the procedure outlined in the video [RadioMaster Boxer Quick Start Guide (EdgeTX)](https://www.youtube.com/watch?v=V2kYjWx9Sa4)

#### Step X: Tools (1/7)
#### Step X: SD Card (2/7)
#### Step X: Radio Setup (3/7)
The Boxer has a wide range of configurations.
**SYS** > **Page Down** 2 times to page 3/7, Radio Setup

* starting at 3:54 minutes - [Complete EdgeTX Radio Settings Guide: How-To Configure the Radiomaster Boxer](https://www.youtube.com/watch?v=x80b77pMpfA)

#### Step X: Global Functions (4/7)
#### Step X: Trainer (5/7)
#### Step X: Hardware (6/7)

#### Step X: Version (6/7)
You go here to get your EdgeTX firmware version information.
My Boxer arrived with EdgeTX version 2.8.0-factory (2022-11-30).

* starting at 30:40 minutes - [Complete EdgeTX Radio Settings Guide: How-To Configure the Radiomaster Boxer](https://www.youtube.com/watch?v=x80b77pMpfA)




-----



# Update EdgeTX

## Flash EdgeTX Firmware to RadioMaster Boxer
There are several ways to install or update EdgeTX on your radio transmitter.
You can use the online tool EdgeTX Buddy or manually install/update the bootloader and firmware using the bootloader method.
I'm using the online tool.

[EdgeTX](https://edgetx.org/)
[EdgeTX User Manual](https://edgetx.gitbook.io/edgetx-user-manual/)

I followed the [EdgeTX User Manual](https://edgetx.gitbook.io/edgetx-user-manual/) instructions located [here](https://edgetx.gitbook.io/edgetx-user-manual/edgetx-user-manual/installing-and-updating-edgetx/update-from-opentx-to-edgetx-1)
You can also use the methods outline in the article "[How to Update EdgeTX in your Radio (flashing to the latest version or migrate from OpenTX)](https://oscarliang.com/flash-edgetx/)".

#### Step 1: Backup Your Current EdgeTX Configuration - DONE
* With your radio powered on, plug your radio into your computer via USB.
* When prompted by your Boxer radio for the USB mode, select **USB Storage**.
* Press **SYS** > **Page Down** (2/7) > **Backup**
* With your computer, copy the entire contents of your SD card to a safe place on your computer. You can use these files again if you need to roll back the update.

#### Step 2: Flash EdgeTX Firmware - DONE
* With the Boxer powered off, plug your radio into your computer via USB. This will connect your radio to the computer via DFU mode.
* Go to the [EdgeTX Buddy](https://buddy.edgetx.org/#/flash) website to get the latest firmware.
* Select the desired firmware version (v2.9.1 was what I selected) and the radio model (RadioMaster Boxer). The select **Flash via USB** at bottom of the page.
* On the next screen, select the **SMT32 Bootloader** device and click **Next**.
* You will be presented with a confirmation screen to verify your settings. Click the **Start Flashing** button.

If this doesn't work (and it didn't for me ... Appears to be Linux permissions problems),
you can update the SD card directly using this process ([explained here](https://oscarliang.com/flash-edgetx/#How-to-Migrate-from-OpenTX-to-EdgeTX)):

* On the [EdgeTX Buddy](https://buddy.edgetx.org/#/flash) site, download the `.bin` file by clicking on the **Download .bin** button at the bottom of the page.
* With your Boxer radio powered on, plug your radio into your computer via USB.
* When prompted by your radio for the USB mode, select **USB Storage**.
* On you computer, copy the `.bin` file to the `FIRMWARE` directory on the Boxer.
* Now on the Boxer enter the `FIRMWARE` directory, via **SYS** > press **Page Down** (2/7) to **FIRMWARE**.
* Highlight the `.bin` file you copied over and do a long press on the scroll button.  Select **Flash bootloader**.
* Power off the Boxer.  Now push both yaw/roll trim buttons inward (see [this description](https://oscarliang.com/flash-edgetx/#Flash-EdgeTX-firmware-in-the-radio)).  Then press and hold the power button.
* Power down the Boxer and then power backup.  Check if the firmware has been updated by **SYS** > press **Page Down** (7/7) > **VERSION**.

Sources:
* [EdgeTX Buddy • How-to Install EdgeTX via Web Browser](https://www.youtube.com/watch?v=zvakNqu_5Ec)
* [How to Update EdgeTX in your Radio (flashing to the latest version or migrate from OpenTX)](https://oscarliang.com/flash-edgetx/)
* [EdgeTX Bootloader Masterclass • Learn How to Flash Your Radio Like the Pros](https://www.youtube.com/watch?v=LItyAkJlcdU)

#### Step 3: Calibrate Boxer Gimbals
Power on the Boxer and enter **SYS** > **Page Down** (6/7) to **HARDWARE**

* [RadioMaster Boxer | Gimbal Calibration](https://www.youtube.com/watch?v=NvyQfvWZ6M4)



-----


# Update ExpressLRS
* [GitHub: ExpressLRS](https://github.com/ExpressLRS)
* [ExpressLRS: Quick Start][10]

## Flash ExpressLRS Transmitter (RadioMaster Boxer)
>**NOTE:** The procedure below is for an Internal ExpressLRS module Boxer transmitter (ExpressRLS built into the radio),
>**not** the External ExpressRLS Module (plugs into the back of the Boxer radio).

The definitive source for this procedure is the [ExpressLRS Quick Start][10] webpage.

* [Intro to Express LRS • For ELRS Novices](https://www.youtube.com/watch?v=AdgBoYJNI0M)
* [A Complete Guide to Flashing and Setting Up ExpressLRS](https://oscarliang.com/setup-expresslrs-2-4ghz/)
* [Easiest Way To Flash and Bind ExpressLRS!](https://www.youtube.com/watch?v=MFFUsN9ZHSU&t=13s)
* [ExpressLRS definitive getting started guide][09]
* [How-To Upgrade OpenTX to EdgeTX 2.9.x • DO NOT FLASH Before You Watch This Video](https://www.youtube.com/watch?v=NYbOLLoV-GA)

#### Step 1: Download and Install ExpressLRS Configurator - DONE
Download the latest [ExpressLRS Configuator](https://github.com/ExpressLRS/ExpressLRS-Configurator/releases),
in my case it version 1.6.0.
I'm using Linux, so my install goes as follows (install notes are [here](https://github.com/ExpressLRS/ExpressLRS-Configurator#linux)):

```bash
# download the .deb file for the Configurator
cd ~/Downloads
wget https://github.com/ExpressLRS/ExpressLRS-Configurator/releases/download/v1.6.0/expresslrs-configurator_1.6.0_amd64.deb

# install the .deb file
sudo dpkg -i expresslrs-configurator_1.6.0_amd64.deb

# if you get an error on the dpkg command, run this
sudo apt --fix-broken install
```

If you wish to remove the `expresslrs-configurator`, do the following:

```bash
# remove expresslrs-configurator
sudo dpkg -r expresslrs-configurator
```

#### Step 2: Install ExpressLRS Lua Script - DONE
This step makes sure your Boxer radio has the latest ExpressRLS Lua script installed.
You do this by using the ExpressRLS utility `expresslrs-configurator`.
Execute `expresslrs-configurator` and fill out the form using your Boxer as the target.
You need to follow the procedures outlined from 8.33 min to 11:59 min in the video [here][09].

Sources:
* [ExpressLRS definitive getting started guide][09]
* [Finally! Quick Set Up For ExpressLRS! How To Wire, Flash, & Program Your ELRS Radio & Receiver!](https://www.youtube.com/watch?v=XJDtHMifkl8)





# Flash ExpressLRS Module (aka Receiver / Flight Controller)
* starting at 2:40 minutes - [How To Setup Radiomaster Boxer ExpressLRS in 5 Minutes](https://www.youtube.com/watch?v=biY5iH1Wz7I)
* [Easiest Way To Flash and Bind ExpressLRS!](https://www.youtube.com/watch?v=MFFUsN9ZHSU)
* [BETAFPV ELRS Recovery Dongle | Quick & Easy Way to Unbrick Your Receiver](https://www.youtube.com/watch?v=HHZ3abmm5Zs)
* [How-to Flash Radiomaster ER4 Express LRS Receiver with BetaFPV Dongle](https://www.youtube.com/watch?v=kiADI0JcC20)
* [How-to Flash Radiomaster ER6 ER8 receivers with Dongle](https://www.youtube.com/watch?v=sS8a5RfwXlw)

# Binding Phrase
* [How To Bind Any & ALL Whoop & Micro Drones To ELRS !! Your Complete Set-Up Guide !! ExpressLRS](https://www.youtube.com/watch?v=X4IzcO16Dxo)
    * [ExpressLRS: SPI Receivers](https://www.expresslrs.org/hardware/spi-receivers/)



-----



# Settings
Boxer ELRS units are equipped with an internal ELRS module, capable of providing 25mW-1000mW RF
output. In non-extreme circumstances, 100mW output at 500Hz update rate is recommended, as higher
RF output and update rates may significantly reduce battery life and generate excessive heat.

## Create a Model
* [How To Setup Radiomaster Boxer ExpressLRS in 5 Minutes](https://www.youtube.com/watch?v=biY5iH1Wz7I)

## Telemetry Screens
* [EdgeTX Telemetry Screens on B&W Radios • Radiomaster Boxer and Zorro](https://www.youtube.com/watch?v=pfart7tdTdo)
* [Telemetry - EdgeTX User Manual](https://edgetx.gitbook.io/edgetx-user-manual/b-and-w-radios/model-select/telemetry)
* [Telemetry Scripts](https://luadoc.edgetx.org/part_i_-_script_type_overview/telemetry)
* [MODEL TELEMETRY screen explanation : How to use telemetry](https://www.apollomaniacs.com/ipod/howto_ar_drone_opentx_radio_bind_model_telemetry_en.htm#Variometer_alarm_setting)

## Data Logging
* [How to Log Telemetry Data in EdgeTX/OpenTX Radios (GPS Coordinates, LQ, RSSI, Voltage etc)](https://oscarliang.com/log-telemetry/)
* [EdgeTX Setting Up Telemetry Data Logging to your Radio](https://www.youtube.com/watch?v=SsbnONkErbc)
* [How to Log Telemetry Data in EdgeTX/OpenTX Radios (GPS Coordinates, LQ, RSSI, Voltage etc)](https://www.fpvcrazy.net/2023/02/11/how-to-log-telemetry-data-in-edgetx-opentx-radios-gps-coordinates-lq-rssi-voltage-etc/)


-----



# Model selection and protocol selection (ELRS version)
Boxer ELRS units are equipped with an internal ELRS module, capable of providing 25mW-1000mW RF
output. In non-extreme circumstances, 100mW output at 500Hz update rate is recommended, as higher
RF output and update rates may significantly reduce battery life and generate excessive heat.
Bind instructions
1：Turn off the transmitter
2：Cycle power to the receiver 3 times, the receiver LED will flash twice- indicating bind mode.
3：Turn on the transmitter, long press the SYS button and choose the ExpressLRS LUA under the
TOOLS menu. Scroll down to [Bind] and press enter.
4：The LED on the receiver should now be solid, indicating successful bind.



-----



# Betaflight Tuning






-----






# FPV Simulators
Orqa FPV.Skydive
VelociDrone FPV Racing Simulator
LiftOff

* [Best PC FPV Simulator // WE TRIED THEM ALL](https://www.youtube.com/watch?v=I7lUTEJM62g)

### Whats the Difference between ELRS vs 4-in-1 vs MPM CC2500?
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
EdgeTX - EdgeTX is an open-source firmware for remote control transmitters used in hobbyist RC (radio-controlled) flying and other activities. It is highly customizable, allowing users to configure their transmitters and adjust settings to suit their individual preferences and specific needs.

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

* [How to Setup Radiomaster Boxer | Upgrades, Tips and Tricks](https://oscarliang.com/setup-radiomaster-boxer/)




[01]:https://www.radiomasterrc.com/collections/boxer-1/products/boxer-radio-controller-m2
[02]:https://edgetx.org/
[03]:https://www.expresslrs.org/
[04]:https://www.radiomasterrc.com/products/21700-5000mah-battery-for-tx16s-mkii
[05]:https://www.radiomasterrc.com/collections/tx16s
[06]:https://www.radiomasterrc.com/pages/user-manuals
[07]:https://github.com/EdgeTX/edgetx-user-manual/tree/main/b-and-w-radios
[08]:https://www.expresslrs.org/quick-start/getting-started/
[09]:https://www.youtube.com/watch?v=J3Hg2f7RL1A
[10]:https://www.expresslrs.org/quick-start/getting-started/
[11]:
[12]:
[13]:
[14]:
[15]:
[16]:
[17]:
[18]:
[19]:
[20]:

