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

Review this again - [A Complete Guide to Flashing and Setting Up ExpressLRS](https://oscarliang.com/setup-expresslrs-2-4ghz/)

The software foundation of EdgeTX is OpenTX.  Same is true for EdgeTX Companion.
This video shows you how to setup your models via EdgeTX Companion.
[How to install OpenTX Companion and set up your first model](https://www.youtube.com/watch?v=iwndEhssna8)






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
* [Radiomaster Boxer Max ELRS - The Best Gets Better](https://www.youtube.com/watch?v=r1kwoq1jxIg)

## Should I Use Mode 1 or Mode 2?
Mode 1 or Mode 2 has only indirectly to do with your quadcopter,
it is more about the radio.
It tells you about the position of the throttle stick.
The difference: In mode 1 the throttle is on the right side,
in mode 2 the throttle is controlled with the left hand (both the up/down axis).
By far, Mode 2 is the most prevailent, at least if for Europe or the USA.
In Australia and other regions, it can also be that you find more Mode 1 pilots.
**Use Mode 2, so throttle is on your left hand.**

Sources:
* [MODE 1 VS. MODE 2](https://fpvracingdrone.org/from-a-to-z/mode-1-vs-mode-2/)

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

>**NOTE ANTENNA:** Install the provided antenna in the top of the radio BEFORE
>installing batteries and turning on the radio.
>**DO NOT** operate the radio without the antenna installed and the internal RF module powered on.
>Doing so will damage the internal RF module and will not be covered under warranty.

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
[ExpressLRS Quick Start: Typical Updating Steps - Simplest EdgeTX Updating Procedure](https://www.expresslrs.org/quick-start/transmitters/updating/#via-etx-passthrough:~:text=Simplest%20EdgeTX%20Updating%20Procedure)

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

1. On the [EdgeTX Buddy](https://buddy.edgetx.org/#/flash) site, download the `.bin` file by clicking on the **Download .bin** button at the bottom of the page.
2. With your Boxer radio powered on, plug your radio into your computer via USB.
3. When prompted by your radio for the USB mode, select **USB Storage**.
4. On you computer, copy the `.bin` file to the `FIRMWARE` directory on the Boxer.
5. Now on the Boxer enter the `FIRMWARE` directory, via **SYS** > press **Page Down** (2/7) to **FIRMWARE**.
6. Highlight the `.bin` file you copied over and do a long press on the scroll button.  Select **Flash bootloader**.
7. Power off the Boxer.  Now push both yaw/roll trim buttons inward (see [this description](https://oscarliang.com/flash-edgetx/#Flash-EdgeTX-firmware-in-the-radio)).  Then press and hold the power button.
8. Power down the Boxer and then power backup.  Check if the firmware has been updated by **SYS** > press **Page Down** (7/7) > **VERSION**.

Sources:
* [EdgeTX Buddy • How-to Install EdgeTX via Web Browser](https://www.youtube.com/watch?v=zvakNqu_5Ec)
* [How to Update EdgeTX in your Radio (flashing to the latest version or migrate from OpenTX)](https://oscarliang.com/flash-edgetx/)
* [EdgeTX Bootloader Masterclass • Learn How to Flash Your Radio Like the Pros](https://www.youtube.com/watch?v=LItyAkJlcdU)

#### Step 3: Calibrate Boxer Gimbals - DONE
Calibration of your drone’s gimbal is important to ensure all gimbal motors are functioning properly and there is no restricted movement for the gimbal.
Calibartion allows the gimbal processor to check the motion range of each axis, determine & set the correct offsets required to centre the sticks on each axis.

I followed the calibration methodology in the sources below.
To get going, power on the Boxer and enter **SYS** > **Page Up** (6/7) to **HARDWARE** > highlight **Calibration** and click the scroll bar.

* [You're calibrating your gimbals wrong (solves Tango 2 THROTTLE warning)](https://www.youtube.com/watch?v=I6n_Ak860lA)
* [RadioMaster Boxer | Gimbal Calibration](https://www.youtube.com/watch?v=NvyQfvWZ6M4)
* [$130 for the gimbals alone?! Yup. RadioMaster AG01 all metal CNC gimbals for TX16S](https://www.youtube.com/watch?v=NU0F5BXIb4E)



-----



# Update ExpressLRS on Radiomaster Boxer
The steps below are for installing ExpressLRS within the RadioMaster Boxer,
both the Lua Script and the firmware.
This is done with the aid of the `expresslrs-configurator` program.

I'll also include here the updating of the ExpressLRS firmware on the receiver.
Strictly speaking, this isn't related to the RadioMaster Boxer, but I include it here for completeness.

Sources:
* [How to Setup Radiomaster Boxer | Upgrades, Tips and Tricks][11]
* [GitHub: ExpressLRS](https://github.com/ExpressLRS)
* [ExpressLRS: Quick Start][10]

## Flash ExpressLRS Transmitter (RadioMaster Boxer)
>**NOTE:** The procedure below is for an Internal ExpressLRS module Boxer transmitter (ExpressRLS built into the radio),
>**not** the External ExpressRLS Module (plugs into the back of the Boxer radio).

The definitive source for this procedure is the
["How to Setup Radiomaster Boxer | Upgrades, Tips and Tricks"][11] article
and the ["ExpressLRS Quick Start"][10] webpage.

Other sources:
* [Intro to Express LRS • For ELRS Novices](https://www.youtube.com/watch?v=AdgBoYJNI0M)
* [A Complete Guide to Flashing and Setting Up ExpressLRS](https://oscarliang.com/setup-expresslrs-2-4ghz/)
* [Easiest Way To Flash and Bind ExpressLRS!](https://www.youtube.com/watch?v=MFFUsN9ZHSU&t=13s)
* [ExpressLRS definitive getting started guide][09]

#### Step 1: Download and Install ExpressLRS Configurator - DONE
Download the latest [ExpressLRS Configuator][13], in my case it version 1.6.0.
I'm using Linux, so my install goes as follows (install notes are [here][14]:

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

#### Step 2: Update ExpressLRS Lua Script - DONE
This step makes sure your Boxer radio has the latest ExpressRLS Lua script installed.
This script isn't expected to change frequently,
but this may need to be updated at some point in the future, like major point releases.

You update the ExpressRLS Lua script by using the ExpressRLS utility `expresslrs-configurator`.
Execute `expresslrs-configurator` and fill out the form using your Boxer as the target.
You need to follow the procedures outlined from 8:33 min to 11:59 min in the video [here][09].

I did this and installed the Lua script for ExpressLRS v3.3.0.
This Lua file was called `elrsV3.lua`.

#### Step 3: Update ExpressLRS Internal Module Fimware - DONE
There are three methods to update the ExpressLRS firmware on the Boxer.
For the Roadmaster Boxer, which has EdgeTX and an Internal ExpressLRS Module,
you can use the EdgeTXPassthrough method.

You need to follow the procedures outlined in the ExpressRLS Quick Start documentation located [here][12].
To summarize these steps:

1. First, you must make sure the USB-VCR is in CLI mode. You can check this via **SYS** > **Page Down** to HARDWARE page (6/7) > Scroll down to "USB-VCP" and it should be in **CLI** mode.
2. Use the USB-C port on the top of the Boxer, plugin a cable to you desktop computer.
3. You will be prompted to make a selection. Select **USB Serials (VCP)**.
4. On you desktop computer (Linux), check whether the Radio is being recognized correctly.  Execut the command `lsusb | grep -i stm` and you should get a message that says, in part,  `STMicroelectronics Virtual COM Port`.
5. On you desktop computer, execute the `expresslrs-configurator` script.
6. Firmware Version: In the congfigurator, choose the latest firmware Release
7. Target: Select **RadioMaster 2.4 GHz** as the device category, and **RadioMaster Boxer Internal 2.4GHz TX** as the device.
8. Flashing Method: Select **EdgeTXPassthrough** as your flashing method.
9. Regulatory Domains: Configure your regulatory domain **REGULATORY_DOMAIN_ISM_2400** (for FCC)
10. Binding Phrase Setup: Enter your **BINDING_PHRASE** (I use my name).
11. Click the **Flash** button. Wait for the process to finish. A Green Success bar will show up in the ExpressLRS Configurator.
12. Unplug your Radio from USB. Check if the ExpressRLS firmware got updated via **SYS** > select **ExpressLRS** >
scroll to the bottom and under **[BIND]** you should see the ExpressLRS version number (3.3.0 in my case) followed by "ISM2G4".

Sources:
* [ExpressRLS Quick Start:a Typical Updating Steps](https://www.expresslrs.org/quick-start/transmitters/updating/)
* [Finally! Quick Set Up For ExpressLRS! How To Wire, Flash, & Program Your ELRS Radio & Receiver!](https://www.youtube.com/watch?v=XJDtHMifkl8)



------



# Update ExpressLRS on Quadcopter Reciever

## Flash ExpressLRS Receiver (aka Receiver / Flight Controller)
* [ExpressLRS definitive getting started guide][09]
* starting at 2:40 minutes - [How To Setup Radiomaster Boxer ExpressLRS in 5 Minutes](https://www.youtube.com/watch?v=biY5iH1Wz7I)
* [Easiest Way To Flash and Bind ExpressLRS!](https://www.youtube.com/watch?v=MFFUsN9ZHSU)
* [BETAFPV ELRS Recovery Dongle | Quick & Easy Way to Unbrick Your Receiver](https://www.youtube.com/watch?v=HHZ3abmm5Zs)
* [How-to Flash Radiomaster ER4 Express LRS Receiver with BetaFPV Dongle](https://www.youtube.com/watch?v=kiADI0JcC20)
* [How-to Flash Radiomaster ER6 ER8 receivers with Dongle](https://www.youtube.com/watch?v=sS8a5RfwXlw)

# Binding Phrase
* [How To Bind Any & ALL Whoop & Micro Drones To ELRS !! Your Complete Set-Up Guide !! ExpressLRS](https://www.youtube.com/watch?v=X4IzcO16Dxo)
    * [ExpressLRS: SPI Receivers](https://www.expresslrs.org/hardware/spi-receivers/)
* go to 13:04 minutes - [Build an FPV drone in 2023 - Part 7 - Bind the ELRS Receiver](https://www.youtube.com/watch?v=Dz7bdXWKC1Q)

#### Step X: xxx
#### Step X: xxx
#### Step X: xxx
#### Step X: xxx



-----



# Settings
Boxer ELRS units are equipped with an internal ELRS module, capable of providing 25mW-1000mW RF
output. In non-extreme circumstances, 100mW output at 500Hz update rate is recommended, as higher
RF output and update rates may significantly reduce battery life and generate excessive heat.

## EdgeTX Companion
EdgeTX Companion is a computer program that allows you to connect to your
EdgeTx radio via USB and perform backups, modifications, etc. using your laptop/desktop.
It has some great features that allow you to set up quadcopter, plane, etc.
and actually simulate the controls to see whether everything is correct.
If it is, you can then write that setup to your radio’s SD card via the USB connection.

Sources:
* start at 13:08 minutes - [EdgeTX Companion is Here! Watch this first](https://www.youtube.com/watch?v=VAEiwWaNEas)
* [Looking for EdgeTX Companion? See this link](https://edgetx.org/getedgetx/)
* [EdgeTX Companion v2.8: Complete Start to Finish Intro](https://www.youtube.com/watch?v=DpwbyMruoF8)
* [Companion User Manual](https://edgetx.gitbook.io/edgetx-user-manual/edgetx-companion/companion-user-manual)
* [RadioMaster Boxer](https://www.youtube.com/playlist?list=PLHSMllXIT6nbZI13nYcbGslWFXwYfi9Le)
* [OpenTx Tutorial • Beginner Series](https://www.youtube.com/playlist?list=PLy3TC1ILJYTjqDXFB84oXVWZG14zyMYYt)

#### Step X: Download EdgeTX Companion - DONE
Download EdgeTX Companion for Linux can be done at [this site][20].

```bash
# dsownload the edgetx companion zip file and unzip
cd ~/Downloads/EdgeTX-Companion
wget https://github.com/EdgeTX/edgetx/releases/download/v2.9.1/edgetx-cpn-linux-v2.9.1.zip
unzip edgetx-cpn-linux-v2.9.1.zip

# copy the appimage to some place in your path abd make it executable
cp ~/Downloads/EdgeTX-Companion/EdgeTx_Companion_2.9.1-x86_64.AppImage ~/bin
chmod ug+x ~/bin/EdgeTx_Companion_2.9.1-x86_64.AppImage
```
start at 13:08 minutes -start at 13:08 minutes -
Now create the following file `~/.local/share/applications/edgetx-companion.desktop`
and make it executable:

```bash
##!/usr/bin/env xdg-open

# Creating a Custom Application Launcher in Ubuntu 22 - https://www.dgendill.com/posts/technology/2023-04-23-ubuntu22-custom-shortcuts-appliation-launchers.html
# How to create a desktop shortcut to a website - https://askubuntu.com/questions/1269788/how-to-create-a-desktop-shortcut-to-a-website
# How to create desktop shortcut launcher on Ubuntu 22.04 Jammy Jellyfish Linux - https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-22-04-jammy-jellyfish-linux #How do I create a new application launcher in Ubuntu 22.04?
# How do I create a new application launcher in Ubuntu 22.04? - https://askubuntu.com/questions/1428517/how-do-i-create-a-new-application-launcher-in-ubuntu-22-04
# Fix "Add to Favorites" for custom apps in Ubuntu - https://averagelinuxuser.com/ubuntu_custom_launcher_dock/
# Registering AppImage Files as a desktop app - https://askubuntu.com/questions/902672/registering-appimage-files-as-a-desktop-app

# https://edgetx.org/getedgetx
[Desktop Entry]
Version=1.0
Terminal=false
Type=Application
Name=EdgeTX Companion
Exec=/home/jeff/bin/EdgeTx_Companion_2.9.1-x86_64.AppImage
Icon=/home/jeff/.local/share/applications/edgetx-logo.png
Categories=Application;IDE;
Comment=Perform EdgeTX backups, modifications, etc. using your laptop/desktop
```

#### Step X: Create Backup of Boxer Configuration - DONE but did not work
As you make changes to you EdgeTX configuration, keeping a backup of your EdgeTX firmware and settings is essential.
You can use EdgeTX Companion to very easily save copies of EdgeTX radio settings and firmware.

To do backups, EdgeTX Companion make use of the Device Firmware Upgrade Utilities ([`dfu-util`][21]).
Make sure to install it first as shown below:

```bash
# install the required backup utilities
sudo apt install dfu-util

# add the following UDEV rule to the file /etc/udev/rules.d/77-mm-usb-device-blacklist.rules
# required for dfu-util - https://github.com/redbear/Duo/blob/master/docs/dfu-util_installation_guide.md
ATTRS{idProduct}=="d058", ATTRS{idVendor}=="2b04", MODE="664", GROUP="plugdev"
```

If you can't open the DFU device or some other error, reboot and try again.

Now to do the backup, follow these steps:

1. Turn on RadioMaster Boxer **before** connecting it with a USB cable
2. Connect the RadioMaster Boxer to your computer with USB cable
3. Make sure you are in USB mode, that is, select **USB Storage (SD)** in the Boxer menu. This makes Boxer appears as a hard drive on your computer
4 Using the EdgeTX Companion, select the button in the left-hand menu that is titled **Read Models and Settings From Radio**.
Save the Models & Settings on your computer via the **Save** button the the top menu with an identifiable name (e.g. `EdgeTX-settings-backup-10-30-23.etx`)
* Using the EdgeTX Companion, select the button in the left-hand menu that is titled **Read Firmware From Radio**.
Save the firmware on your computer via the **Save** button with an identifiable name (e.g. `EdgeTX-firmware-backup-10-30-23.bin`)

Sources:
* [EdgeTX Companion: Backup an EdgeTX radio in under a minute](https://www.youtube.com/watch?v=D24JtWshVpc)
* [EdgeTX Companion Backup & Restore Models & Radio Settings](https://www.youtube.com/watch?v=vW7N0DmKqLw)
* [dfu-util Installation Documentation](https://github.com/redbear/Duo/blob/master/docs/dfu-util_installation_guide.md)

#### Step X: Create Backup of Boxer Configuration - DONE
As you make changes to you EdgeTX configuration, keeping a backup of your EdgeTX firmware and settings is essential.
To do this, use this proceddure:

1. With your radio powered on, plug your radio into your computer via USB.
2. When prompted by your Boxer radio for the USB mode, select **USB Storage**.
3. Press **SYS** > **Page Down** (2/7) > **Backup**
4. With your computer, copy the entire contents of your SD card to a safe place on your computer. You can use these files again if you need to roll back the update.

#### Step X: Fillout EdgeTX Companion Profile
Using the **Gear** (aka Settings), fillout the **Profile** tab in EdgeTX Companion.



---------



# EdgeTX Snippets
These short write-up and videos concerning "how-to" for some common needs on EdgeTx
* [EdgeTX Snippets](https://www.youtube.com/playlist?list=PLy3TC1ILJYTjWBv9HIpj_Eb5yA_W9Neua)

#### Step X: Create Audible Low Battery Alert
Using one logical switch and one special function,
you can implement an audio alert for low battery on the quadcopter.

On the EdgeTX Conpanion Tool:
* **Logical Switches** tab (I used `L01` logical switch)
    * **Function** is `a<x`
    * **V1** is `Batt`
    * **V2** is `3.7V`
    * **AND Switch** is `----`
    * **Duration** is `0.0`
    * **Delay** is `5.0`
* **Special Functions** tab:
    * **Switch** is `L01`
    * **Action** is `Play Value`
    * **Parameters** is`Batt`
    * `Repeat 10s`

Sources:
* goto 4:25 minutes - [Just The Tip - Ep 05 - OpenTX / EdgeTX Secrets Revealed - Audible Low Battery Alerts!](https://www.youtube.com/watch?v=0DrPrh-HwE0)

#### Step X: Built-In Curves and Custom Curves
* [Adjusting Throttle Curve in Betaflight and EdgeTX: Tips for Smoother Throttle Control](https://oscarliang.com/throttle-curve/)
* [MODEL CURVES screen explanation : How to use curves](https://www.apollomaniacs.com/ipod/howto_ar_drone_opentx_radio_bind_model_curvemenu_en.htm)
* [Custom Curves](https://rcdiy.ca/opentx-transmitter-firmware/model-menus/custom-curves/)
* [Curves - EdgeTX User Manual](https://edgetx.gitbook.io/edgetx-user-manual/b-and-w-radios/model-select/curves)
* [EdgeTX Snippet • Built-In Curves vs Custom Curves](https://www.youtube.com/watch?v=cJuvl3mHxt8)
* [EdgeTX Snippet • Learn About Weights and Expo](https://www.youtube.com/watch?v=jL8Jbd53-3E)

#### Step X: Control Screen Brightness via Knob
* [Screen brightness on a knob? // EDGETX GLOBAL FUNCTIONS HOW-TO](https://www.youtube.com/watch?v=CSWXkPCldP8)

#### Step X: 6-Position Buttons
* [Tutorial: Using 6-Position Buttons on Radiomaster Boxer to Change VTX Channel](https://www.youtube.com/watch?v=L95xTSwAehg)

#### Step X: Using Trim Switches for Angle Mode
In angle mode your quadcopter continuously drifts, it is likely that your gyroscope / acelarometer requires some trim.

Sources:
* [It's finally ok to use your trim switches // EDGETX HOW-TO](https://www.youtube.com/watch?v=36dYW2X0-4w)
* [Your trim switches are useless. Let's fix that. (OpenTX n-position switch from momentary tutorial)](https://www.youtube.com/watch?v=wa43z6XohW4)



---------




## Create a Model
A model refers to a configuration or template used in a radio-controlled device,
such as a model sailplane or drone.
It includes various settings and options that define the behavior and characteristics of the device.
Models can be created, managed, and labeled in the Manage Models screen.
https://edgetx.gitbook.io/edgetx-user-manual/edgetx-user-manual/user-manual-for-color-screen-radios/select-model

Sources:
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

## Throttle Lock
* [Throttle Lock for Radiomaster Boxer with EdgeTX: My NEW FAVORITE!](https://www.youtube.com/watch?v=zLcB24e8ZEc)

## Throttle Scaling
* [Betaflight OpenTX Throttle Scaling | TAME YOUR 2S TINY WHOOP](https://www.youtube.com/watch?v=K7t6U_2dLlk)
* [Betaflight Rates tuning. How to make your quad feel right for the way you like to fly](https://www.youtube.com/watch?v=RneayCxDN4A&t=14s)
* [Adjusting Throttle Curve in Betaflight and EdgeTX: Tips for Smoother Throttle Control](https://oscarliang.com/throttle-curve/)


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

* [pascallanger/DIY-Multiprotocol-TX-Module](https://github.com/pascallanger/DIY-Multiprotocol-TX-Module)

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
[11]:https://oscarliang.com/setup-radiomaster-boxer/#Updating-Internal-ExpressLRS-Module
[12]:https://www.expresslrs.org/quick-start/transmitters/updating/#via-etx-passthrough
[13]:https://github.com/ExpressLRS/ExpressLRS-Configurator/releases
[14]:https://github.com/ExpressLRS/ExpressLRS-Configurator#linux
[15]:
[16]:
[17]:
[18]:
[19]:
[20]:https://edgetx.org/getedgetx/
[21]:https://dfu-util.sourceforge.net/
[22]:
[23]:
[24]:
[25]:
[26]:
[27]:
[28]:
[29]:
[30]:

