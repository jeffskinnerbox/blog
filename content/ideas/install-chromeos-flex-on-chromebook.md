<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/we-do-this-not-because-it-is-easy.jpg" title="U.S. President John F. Kennedy said this in his moon speech at Rice University in Houston, Texas, on September 12, 1962:

 We choose to go to the moon.  We choose to go to the moon in this decade and do the other things, not because they are easy, but because they are hard, because that goal will serve to organize and measure the best of our energies and skills, because that challenge is one that we are willing to accept, one we are unwilling to postpone, and one which we intend to win, and the others, too." align="center" width=500px height=375px>
</div>


--------


[ChromeOS Flex][01] is also Google's play to
[modernize school’s existing PCs and Mac devices][02] at no additional cost.
Google has made it easy to manage ChromeOS Flex devices alongside existing Chromebooks,
saving schools money and bring them more solidly into the Chromebook camp.
Google is also making a [play for the business enterprise][03] too.
While ChromeOS Flex isn't for everyone,
its a great replacement for the
when your Chromebook has reached it Auto Update Expiration (AUE) date,
and you want to continue using ChromeOS (but **without** Linux).
You can continue to use a Chromebook beyond its Auto Update Expiry (AUE) date,
but there is a security risk over time.
Check out ["Google Confirms 5 New ‘High’ Level Security Flaws In Chrome"][25].

>**NEWS FLASH:** On Sept 14, 2023, Google announced that "[Chromebooks will get 10 years of automatic updates][26]"

# ChromeOS Flex Installation
I purchased in 2015 for $300 via Amazon a [Toshiba CB35-B3340 13.3-Inch Chromebook 2][06].
It has 64-bit Intel Celeron N2840 Processor (with Intel HD Graphics for Intel Atom® Processor Z3700),
4GB of DDR3L SDRAM memory, and 16GB SSD disk.
I purchased a Intel Chromebook specifically because I thought some day I might convert it to a Linux laptop
but my plan for this Chromebook is to install ChromeOS Flex.

>**NOTE:**There are two editions of the Toshiba Chromebook 2.
>One simple called Chromebook 2 with a 2.16 GHz Intel Celeron N2840
>and the other Chromebook 2 (2015 model) with a 1.70 GHz Intel Celeron 3215U.
>I have the Chromebook 2.
>This distinction could have been important when you create the ChromeOS Flex installer USB drive,
>but I found out later it didn't appear to matter.

ChromeOS Flex isn't a complete replacement of the Chromebook use case,
and so it has its [critical differences][23] and [some convincing strong points][24].
Google has a [list of ChromeOS Flex certified device][05],
all PCs and MACs, **no Chromebooks** are on the list
(clearly Google wants you to replace the Chromebook with another).
Google list a few promises and many cavities with this list of certified hardware,
including a certification expiration date.
Google also makes a point about the [differences between ChromeOS Flex and ChromeOS][09].
My Toshiba Chromebook appears to meet all the [criteria listed for ChromeOS Flex installation][07]
but not certified by Google for ChromeOS Flex.

[ChromeOS Flex can be installed on end-of-life (EOL) Chromebooks, but Google doesn’t recommend it][04].
Google [officially recommends you don’t][08] use Chrome OS Flex on computers that have reached AUE/EOL.
The company acknowledges that it works, but it won’t be supported.
And there is no falling back to your initial Chromebook configuration.
If the installation doesn't work,
Google does not provide steps for how to uninstall ChromeOS Flex.
Instead, Google recommends installing a different OS on your device,
using instructions provided by the device OEM or another OS provider.

The installation process involves disabling firmware write protection
in Chrome OS that ensures that a device is not tampered with before use.
The instructions on doing this vary on a device-by-device basis,
while some related documentation is out there from alternative operating systems for Chromebooks.
You might also need to flash custom (community-made) firmware.
In short, it’s not a straightforward process like on Macs or PCs.

The basic steps to doing the ChromeOS Flex install are:

1. Create your USB installer with the ChromeOS Flex image.
1. Disable Write Protection on Toshiba CB35-B3340
1. Flash Chromebook firmware with Coreboot
1. Boot your device using your USB installer.
1. Install ChromeOS Flex on your device.
1. Set up and enroll your ChromeOS Flex devices.

Sources for installation methodology:

* [How to install Chrome OS Flex](https://www.androidauthority.com/how-to-install-chrome-os-flex-3112924/)
* [How to install ChromeOS Flex on a Chromebook](https://www.androidpolice.com/install-chromeos-flex-chromebook-explainer/)
* [ChromeOS Flex installation guide: Prepare for installation][07]
* [How to Install Any Linux Distro on a Chromebook](https://linuxconfig.org/how-to-install-any-linux-distro-on-a-chromebook)
* [How to use a Chromebook after AUE date safely in 2022 and beyond](https://www.chromecomputing.com/how-to-use-a-chromebook-after-aue-date-safely-in-2022-and-beyond/)
* [Install Other OS on Toshiba Chromebook 2 (CB35-B3340)](https://newscrewdriver.com/tag/cb35-b3340/)
* [Transform a Toshiba Chromebook CB35 into a Linux Development Environment with GalliumOS](https://nickjanetakis.com/blog/transform-a-toshiba-chromebook-cb35-into-a-linux-development-environment-with-galliumos)

As a final note,
there maybe some ways around the Chromebooks secure boot protection if all fails.
This involves replacing the default BIOS firmware with an implementation of UEFI,
which in theory, allowing me to install any operating system that can boot off UEFI.
Check out ["Install Other OS on Toshiba Chromebook 2 (CB35-B3340)"][10]
and ["Install CloudReady (or other OS) on Toshiba Chromebook 2 (CB35-C3300)"][11].
I'm a bit skeptical if this can work without physically disabling write protection,
as I will do below.


--------


## Install of ChromeOS Flex
The procedure below is basically following the methodology outline in
["How to install ChromeOS Flex on a Chromebook"][15].
To get a good review on how we'll proceed,
it is wise to read this in totally before you proceed.

During this journey to get to ChromeOS Flex,
you might (in error or intentionally via the process below)
get a scary screen that says “ChromeOS is Missing or Damaged” “ChromeOS is Missing or Damaged”.
You can get your ChromeOS back (as long as you haven't yet upgraded the bootloader firmware)
via the “Chromebook Recovery Utility“.
The website ["ChromeOS is Missing or Damaged Fixed!"][21] can help you with this.

#### Step 1: Create USB Installer ChromeOS Flex Image - DONE
You could use the method outline in ["ChromeOS Flex Installation Guide: Create the USB installer"][12]
to create you installer USB drive.
This should be done on your Chromebook, via the Chrome browser,
ideally on the Chromebook you plan to install ChromeOS Flex.
This way, the appropriate parameters don't need to be entered by hand.

At the [same source][12], you'll also find instructions to create a
bootable USB drives using the Linux `dd` command-line utility.
This is the method I choose (the Chrome browser installer creation did work for me).
The methodology is as follows:

```bash
# download the latest chromeos flex installer image
wget https://dl.google.com/chromeos-flex/images/latest.bin.zip

# unzip this file to create the binary image for the usb drive
unzip latest.bin.zip

# create the usb image ... make sure your using the right /dev/*
sudo dd if=chromeos_15117.112.0_reven_recovery_stable-channel_mp-v2.bin of=/dev/sdf bs=4M status=progress
```

#### Step 2: Disable Write Protection on Toshiba CB35-B3340 - DONE
All Chromebooks come with physical write protection,
which is an extra layer of security to stop anything from being installed that shouldn’t be.
This include write protection of a new OS like ChromeOS Flex.
This write protection needs to be removed,
via physical means (aka open the device and change it physically),
to do our install of ChromeOS Flex.

The [first sources below][16] give you all the instructions needed,
and it is outline as follows:

* First, remove all the screws from the back cover and remove it.
It's easiest to remove if you pull up starting where the hinges are located.
* Next, remove all of the screws from the big metal motherboard cover,
and you'll see the exposed processor, and more importantly, the **write protection jumper**.
You must remove the silver metallic sticker here, your fingernail is enough.
* To prevent the metallic cover from bridging the connection when you put it back on,
cover up where you scraped the sticker off with a piece of electrical tape (aka electrical insulator).
* Reassemble the Chromebook.

Sources:
* [Disable write protect on Toshiba Chromebook 2][16]
* [HOW TO Disable write-protect on Toshiba Chromebook 2 (CB35-3340)](https://www.reddit.com/r/chromeos/comments/2ljid3/how_to_disable_writeprotect_on_toshiba_chromebook/)

#### Step 3: Flash Chromebook with Coreboot Firmware - DONE
Next we'll replace the Chromebook's BIOS firmware with [coreboot][18].
[MrChromebox][17] provides coreboot firmware images for the vast majority of
x86-based Chromebooks and Chromeboxes, providing a [modern UEFI bootloader][19].

The ["HOWTO..." sources below][22] give you all the instructions needed,
and is briefly outline as follows:

* After re-assembling the Chromebook,
force a boot to Recovery Mode (Hold down `Esc` / `Refresh` / `Power` simultaneously).
* Once you see the Recovery Mode boot screen, hit `Ctrl-D`,
and follow the prompts to disable OS verification (i.e. enter Developer mode).
Wait for this process to finish and the Chromebook to reboot back to the "OS verification Off" warning screen.
* At this point, hit Ctrl-D again to boot into "developer mode"(or just wait for it to go ahead and boot into ChromeOS).
* Using your Google account or the guests account, configure your wireless connection.
Click on "Browse as Guest" after you have wireless connectivity.
* In one of the browser's tabs, navigate to `http://mrchromebox.tech`
and navigate to ["Firmware Utility Script"][20].
* Open up a crosh shell in a new tab by hitting `Ctrl-Alt-T`.
In the crosh shell, type "shell" and you should have a normal BASH shell prompt.
* In the MrChromebox menu item "Firmware Utility Script",
you'll find the script you need to enter at the BASH prompt.
That script is listed below.

```bash
# double check the commands below
# make sure it matches the command on the mrchromebox.tech website

# download and run this script under chromeos (also works in linux)
#     if you encounter certificate related errors when downloading the script from chromos,
#     then add -k to the curl command and script command to bypass ssl certificate
cd; curl -LO https://mrchromebox.tech/firmware-util.sh && sudo bash firmware-util.sh
```

* When you running the above script,
if you see "Fw WP: Enabled", then hardware flash protection is still **enabled**,
and you do not want this (see [MrChromebox.tech documentation][20] for pictures).
If this is the case, you'll need to double check the work you did on disabling write protection.
Repeat the above until you see hardware flash protection is disabled.
* Once the script is running, from the menu, select option "2) Install/Update UEFI (Full ROM) Firmware".
* Follow the prompts to save the original firmware ROM file to a USB drive (for recover should this process goes badly).
After explicitly saying I wanted to proceed, the script will proceeded to download the appropriate ROM file.
* After the flash of the full ROM firmware completed successfully,
chose "P" on the menu to power off.

Sources:
* [HOWTO: Flash full ROM (i.e. coreboot) and install GalliumOS on Dell Chromebook 11 Candy (3120)][22]
* [MrChromebox.tech](https://mrchromebox.tech/#home)

#### Step 4: Boot Chromebook Using USB Installer - DONE
Next we want to boot the Chromebook from the USB drive.
To do this, you must enable take advantage of the Coreboot bootloader we just installed.
The procedure is as follows:

* Turn off the Chromebook where your to run ChromeOS Flex
and then insert the ChromeOS Flex USB installer.
* To boot the device from the USB drive, press the power button on,
and immediately begin repeatedly pressing Coreboot boot key, which is the `Esc` key.
* You get a Coreboot menu and you should select "Boot Menu" and hit the "Entry" key.
* At the next menu, select "USB:" and hit the "Entry" key.
The ChromeOS Flex image will begin to install.
* When prompted, respond to the screen until you reach the "Installing ChromeOS Flex" screen.
Installation will take less than 20 minutes and then automatically power down when complete.

At this point, you are in ChromeOS Flex, and it should be the familiar Chromebook look & feel.
Proceed to create your login, etc.

>**NOTE:** If the Bootloader appears to hang, and you want to force a shutdown,
>press the power key and hold it down for about 5 seconds.

Sources:

* ["ChromeOS Flex installation guide: Boot device using the USB installer"](https://support.google.com/chromeosflex/answer/11552352)
* ["How to Enable Developer Mode on a Chromebook"][13].
* ["2 Easy Ways to Enable USB Booting on Chromebook"][14].



[01]:https://chromeenterprise.google/os/chromeosflex/
[02]:https://edu.google.com/intl/ALL_us/chromebooks/chrome-os-flex/
[03]:https://cloud.google.com/blog/products/chrome-enterprise/chromeos-flex-ready-to-scale-to-pcs-and-macs
[04]:https://9to5google.com/2022/02/16/chrome-os-flex-chromebook-eol-aue/
[05]:https://support.google.com/chromeosflex/answer/11513094
[06]:https://www.amazon.com/gp/product/B00N99FXIS
[07]:https://support.google.com/chromeosflex/answer/11552529
[08]:https://support.google.com/chromeosflex/answer/11543105
[09]:https://support.google.com/chromeosflex/answer/11542901
[10]:https://newscrewdriver.com/2022/04/18/install-other-os-on-toshiba-chromebook-2-cb35-b3340/
[11]:https://www.ifixit.com/Guide/Install+CloudReady+(or+other+OS)+on+Toshiba+Chromebook+2+(CB35-C3300)/127415
[12]:https://support.google.com/chromeosflex/answer/11541904
[13]:https://www.androidpolice.com/how-to-enter-chromeos-developer-mode/
[14]:https://www.wikihow.com/Enable-USB-Booting-on-Chromebook
[15]:https://www.androidpolice.com/install-chromeos-flex-chromebook-explainer/
[16]:https://www.youtube.com/watch?v=JcZ711cxKdA
[17]:https://mrchromebox.tech/
[18]:https://www.coreboot.org/users.html
[19]:https://www.quora.com/What-is-difference-between-BIOS-UEFI-bootloader-and-firmware
[20]:https://mrchromebox.tech/#fwscript
[21]:https://dbtechreviews.com/2019/11/chromeos-is-missing-or-damaged-fixed/
[22]:https://www.reddit.com/r/GalliumOS/comments/8cydt1/howto_flash_full_rom_ie_coreboot_and_install/
[23]:https://www.theregister.com/2022/07/14/chrome_os_flex_launched/
[24]:https://www.androidpolice.com/chrome-os-flex-what-it-is-and-why-you-should-use-it/
[25]:https://www.forbes.com/sites/gordonkelly/2021/09/02/google-chrome-warning-high-security-hacks-threats-upgrade-chrome-now/?sh=5873d05745f8
[26]:https://blog.google/outreach-initiatives/education/automatic-update-extension-chromebook/

