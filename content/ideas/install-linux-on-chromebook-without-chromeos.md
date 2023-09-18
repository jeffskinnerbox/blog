<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/we-do-this-not-because-it-is-easy.jpg" title="U.S. President John F. Kennedy said this in his moon speech at Rice University in Houston, Texas, on September 12, 1962:

 We choose to go to the moon.  We choose to go to the moon in this decade and do the other things, not because they are easy, but because they are hard, because that goal will serve to organize and measure the best of our energies and skills, because that challenge is one that we are willing to accept, one we are unwilling to postpone, and one which we intend to win, and the others, too." align="center" width=500px height=375px>
</div>


-----


# Install Xubuntu on Chromebook Without ChromeOS
I have an [Acer Chromebook 14 CB3-431][01] which was manufactured & purchased in 2017 for $275 via Amazon.
The Acer Chromebook 14 Acer comes with a Intel Celeron N3160 processor,
4GB LPDDR3 RAM, 32GB of SSD storage, and a very stylish aluminum enclosure.
As far as Google is concerned, this Chromebook has passed its end-of-life date,
Google calls it [Auto Update Expiration (AUE)][02] date,
and it is no longer receiving software updates.
It has been used lightly, so it has much more life in it.
I plan to install Linux and use it as an experimental platform
software compatibility testing, try new tools, etc.
I find myself reluctant to do such things on my desktop Linux system in fear of screwing up my configuration.
I plan to setup this Chromebook with Xubuntu, and hopefully,
such that I can do a quick OS re-install after what might be a destructive experiment.

>**NEWS FLASH:** On Sept 14, 2023, Google announced that ["Chromebooks will get 10 years of automatic updates"](https://blog.google/outreach-initiatives/education/automatic-update-extension-chromebook/)

Sources:

* [The 8 Best Linux Distros for Chromebooks](https://www.makeuseof.com/best-linux-distros-for-chromebooks/)
* [Best Linux Distro For Chromebook](https://www.electronicshub.org/best-linux-distro-for-chromebook/)
* [Lubuntu vs Xubuntu](https://www.educba.com/lubuntu-vs-xubuntu/)

## GalliumOS vs Lubuntu vs Xubuntu
One of the key decision is what variant of Linux do I want to use?
I'm a long time user of Ubuntu on my desktop,
so some version of Linux on the Debian / Ubuntu tree would make most sense.
I also want a [lightweight Linux][03] give the minimal
memory / storage / processing power of the Acer Chromebook.

A bit of online research points me to a [GalliumOS][04] vs [Lubuntu][05] vs [Xubuntu][06] choice.
Much could be said about pros/cons of each of these Linux version (see Sources below)
but I came to Xubuntu as the best choice for me.

## Remote Access / Screen Sharing
I want to set up the Chromebook's environment to support the lightweight GUI of Xubuntu,
that being the [Xfce Desktop Environment][12].
You may also want to setup the Chromebook with [Virtual Network Computing (VNC)][21].
With VNC, you can remote desktop into Linux so I can take full advantage of the desktop GUI menu system.
There are in fact [many remote desktop software packages][32] available to choose from,
but only small number seem to have any following in the Linux world,
and VNC is the de-facto remote desktop protocol for Linux.

VNC has two major components:

* **VNC Server (aka Remote Server / Remote Host)** - The remote host is the computer you're connecting too.  You must configure it to allow connection requests.  These configurations include screen-sharing permissions, internal firewall rules, and possibly external firewall rules and port forwarding.
The VNC Server will be installed on the Chromebook which is booting Xubuntu.
It is this machine that we want to remotely log into via a VNC graphical session running in a window on the Local Client.
* **VNC Viewer (aka Local Client / Local Host)** - The local host is the computer you're using when you want to reach out and connect to a remote host.  It must have an application to make and manage the request.
The VNC Viewer will be installed on my Linux desktop which is booting Ubuntu.
It is this machine that we want to view the Remote Server VNC graphical session.

## Multiple VNC Servers and Clients
I found that setting up a VNC server on Linux can be very tedious and time-consuming.
Ubuntu has created some utilities to make it easier but it is specifically for the Ubuntu platform.
After some experimentation, I have a preference for [X11vnc][56]
and but operates differently than most VNC servers.
It it captures the X Window session on the remote by continuously polling the X server's frame buffer for changes.
This approach  allows the user to control the remote X11 desktop (any ... KDE, GNOME, Xfce, etc.)
as if the user were sitting in front of it.

The tools I recommend for VNC service on Linux are:

* **X11vnc**: Is a VNC Server that “publishes” an existing physical X display over VNC, allowing remote clients to connect with it using a VNC viewer. That is, they can see the actual running desktop windows, as if they were in front of the server.
* **noVNC**: Is a VNC Viewer that can give you maximum flexibility. [noVNC][55] is an open Source VNC client using HTML5 (WebSockets, Canvas), that runs well in any modern browser, including mobile browsers (iOS and Android).

If you intend to install VNC for remote access / screen sharing,
see the companion file `install-vnc-on-linux-for-remote-access-and-screen-sharing.md`.


--------


# Installing Xubuntu on Chromebook
I'll be installing Xubuntu on your Chromebook by completely replacing Chrome OS.
You'll find the tutorial below in the Sources will give you everything you need.
The basic installation steps to doing the ChromeOS replacement with Xubuntu are:

1. Create your USB installer with the Xubuntu image.
1. Disable Write Protection on the Acer Chromebook 14
1. Flash Chromebook firmware with Coreboot
1. Boot your device into Xubuntu using USB installer
1. Set-up your Xubuntu laptop

Sources:

* [How To: Install Ubuntu on Chromebook and REMOVE ChromeOS](https://dbtechreviews.com/2018/09/how-to-install-ubuntu-on-chromebook-and-remove-chromeos/)
* [Acer Chromebook 14 - How to Install GaliumOS + Product Review][11]
* [install-chromeos-flex-on-chromebook.md](xxx)


#### Step 1: Create USB Installer for Xubuntu Image - DONE
[Ventoy][07] is an open source multiboot USB drive supporting ISO/WIM/IMG/VHD(x)/EFI files.
With Ventoy, you don’t need to format the USB drive for each new installation,
you just need to copy the ISO file to the USB drive, boot it,
and Ventoy will give you a [boot menu to select your ISO images][08].
Most type of BIOS and OS are supported.
To install Ventoy on the USB flash drive,
just follow the installation directions [here][09].

```bash
# get the latest version of ventoy
cd ~/Downloads

# goto https://github.com/ventoy/Ventoy/releases
# and download the version of ventoy
wget https://github.com/ventoy/Ventoy/releases/download/v1.0.73/ventoy-1.0.73-linux.tar.gz

# uncompress the ventoy image
tar -xvzf ventoy-1.0.73-linux.tar.gz

# execute the install script
# where /dev/XXX is the USB device (eg /dev/sdf)
cd ventoy-1.0.73
sudo bash ./Ventoy2Disk.sh -i /dev/sde
```

Now you just copy (aka 'drag & drop')
any of the ISO files you wish to install onto the USB flash drive.
There is no need to do a `dd` disk copy.
When you boot from the Ventoy prepared USB flash drive,
you get a menu of the images you can boot & install.

>**Note:** To updating Ventoy when a new version of Ventoy is released, you can update it to the USB drive.
>All the ISO files will be unchanged.
>Upgrade operation is in the same way with installation.
>`Ventoy2Disk.sh` will prompt you for update if the USB drive already installed with Ventoy.

Sources:

* [How to Create a Multiboot USB with Ventoy Fast, Simple, and Easy Guide](https://www.youtube.com/watch?v=z1FyoCswwAc)
* [Ventoy: How to Create a Multiboot USB Drive with Multiple ISO Files](https://linuxiac.com/ventoy-create-bootable-usb/)

#### Step 2: Download Xubuntu Image to Flash Drive - DONE
[Download the Xubuntu][10] ISO image and place it on your USB flash drive.
In my case, I copied the ISO into the Ventoy USB drive I created earlier.

#### Step 3: Disable Write Protection on Acer Chromebook 14 - DONE
All Chromebooks come with physical write protection,
which is an extra layer of security to stop anything from being installed that shouldn’t be.
This include write protection of a new OS like ChromeOS Flex.
This write protection needs to be removed,
via physical means (aka open the device and change it physically),
to do our install of ChromeOS Flex.

The [first sources below][11] give you all the instructions needed,
and it is outline as follows:

* First, remove all the screws from the back cover and remove it.
It's easiest to remove if you pull up starting where the hinges are located.
* Remove the screw identified in the [first sources below][11]
(the screw almost dead center, next to the ribbon cable).
* Optional - You could wrapped the screw in electrical tape and taped them
into a void on the inside of the Chromebook.
If for some reason I want to replace the screw, I have them on the inside for safe keeping.
* Reassemble the Chromebook.

Sources:

* [ Disabling FW Write Protection on Acer Chromebook 14 - tight screw](https://www.reddit.com/r/GalliumOS/comments/6qttgs/help_disabling_fw_write_protection_on_acer/)
* [Acer Chromebook 14 - How to Install GaliumOS + Product Review][11]
* [Acer Chromebook 14 Teardown](https://www.ifixit.com/Teardown/Acer+Chromebook+14+Teardown/76353)
* [Acer Chromebook 14 Teardown](https://ifixit-guide-pdfs.s3.amazonaws.com/pdf/ifixit/guide_76353_en.pdf)

#### Step 4: Flash Chromebook with Coreboot Firmware - DONE
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
After explicitly saying I wanted to proceed,
the script will proceeded to download the appropriate ROM file.
* After the flash of the full ROM firmware completed successfully,
chose "P" on the menu to power off.

Sources:

* [HOWTO: Flash full ROM (i.e. coreboot) and install GalliumOS on Dell Chromebook 11 Candy][22]
* [MrChromebox.tech](https://mrchromebox.tech/#home)

#### Step 5: Boot Chromebook into Xubuntu Using USB Flash Drive - DONE
Now put the USB flash drive into the Chromebook and power up the system.
The system will first boot into Ventoy where you will be given a list of images.
Select the Xubuntu ISO, Xubuntu will be loaded, and then the image is loaded.
The specifics of the procedure is as follows:

* Turn off the Chromebook you want to run Xubuntu
and then insert the USB installer.
* To boot the device from the USB drive, press the power button on,
and immediately begin repeatedly pressing Coreboot boot key, which is the `Esc` key.
* You get a Coreboot menu and you should select "Boot Menu" and hit the "Entry" key.
* At the next menu, select "USB:" and hit the "Entry" key.
Ventoy gives you a list of ISO files, scroll down to select Xubuntu via "Entry" key.
* On the next screen, select "Try or Install Xubuntu" and it should begin loading Xubuntu.
* When prompted, respond to the screen until you complete the installation of Xubuntu.
Installation will take less than 20 minutes.

At this point, you are loading Xubuntu Linux.
Proceed to connect with your WiFi, do normal installation including updates,
write OS to the disk, create your login, etc.

>**NOTE:** If the Bootloader appears to hang, and you want to force a shutdown,
>press the power key and hold it down for about 5 seconds.

Sources:

* [How to Enable Developer Mode on a Chromebook][13].
* [Installing Linux on Chromebook 14](https://www.youtube.com/watch?v=s7oaFGYV29E)
* [2 Easy Ways to Enable USB Booting on Chromebook][14].


-------


# Set-up Xubuntu on the Chromebook
If you compare [Ubuntu desktop][15] with [Ubuntu server][16],
the main difference will be the absence of GUI on the server edition.
Ubuntu Server is basically a striped down version of Ubuntu desktop without the graphical modules.
The graphical desktop environment consumes a lot of system resources and for this reason,
the server operating systems do not include a desktop environment by default.
You may use an Ubuntu server on 512 MB of RAM
but an Ubuntu desktop will need at least 2 GB of RAM to function decently.
Some desktop environments need more system resources (like GNOME)
while some use fewer system resources (like Xfce, MATE etc).

There are numerous ways to install a GUI on Ubuntu 20.04.
One of the easiest ways is with a tool called `tasksel`,
which streamlines the process for us by automatically installing the correct
display manager, window manager, desktop environment, and other package dependencies.

Three major components makeup your GUI: display manager, window manager, and desktop environment

* A [display manager][25] (also known as a “login manager”)
is an application responsible for launching a display server
and managing user authentication and login session.
A few display managers are gdm, gdm3, lightdm, slim, kdm etc.,
The default gdm3 is the popular display manager for GNOME desktop environment,
however, it is a resource-intensive display manager.
To conserve system resources, you can install lighter display managers such as lightdm, slim, etc.
* A [window manager][28], often considered part of the desktop environment,
controls the placement and appearance of windows within GUI or also used standalone.
* [GNOME is the default desktop environment][26] for Ubuntu with many features and a wide community.
Find out from here the [various desktop environments][27] you have to pick from.

For Ubuntu, the default display manager is [gdm3][32], window manager + desktop environment is [GNOME][26].
For Xubuntu, the default display manager is [lightdm][33], window manager is [xfwm4][34], and desktop environment is [Xfce][12].

>**NOTE:** Window managers are unique to [Xorg][29].
>The equivalent of window managers on [Wayland][30] are called compositors
>because they also act as [compositing window managers][31].


Sources:

* [Ubuntu 20.04 GUI installation](https://linuxconfig.org/ubuntu-20-04-gui-installation)
* [How to Install a Desktop (GUI) on an Ubuntu Server](https://phoenixnap.com/kb/how-to-install-a-gui-on-ubuntu)
* [How to switch between the CLI and GUI on a Linux server](https://www.redhat.com/sysadmin/configure-systemd-startup-targets)
* [How to install a Desktop Environment (GUI) on Ubuntu Server](https://itsfoss.com/install-gui-ubuntu-server/)
* [How to Run Multiple Desktop Environments on one Linux PC](https://journalxtra.com/linux/desktop/multiple-desktops-on-one-linux-pc-now-thats-greedy/)

#### Step 1: Install Tasksel - DONE
[Tasksel][24] is a Debian/Ubuntu tool that installs multiple related packages
as a coordinated "task" onto your system.
This function is similar to that of meta-packages, and in fact,
most of the tasks available from `tasksel` are also available as meta-packages
from the Ubuntu package managers (such as Synaptic Package Manager or KPackageKit).
Because the package managers now have most of the tasks as meta-packages,
`tasksel` is not installed by default on editions of Ubuntu
(such as Desktop editions) that have package managers.
`tasksel` is still installed by default on server editions.

```bash
# updating the apt package index and installing the tasksel tool
sudo apt update
sudo apt install tasksel

# list all of the GUIs available for selection
# in the first column of the list, u (uninstalled) means software is not installed
# and i (installed) means software is installed
tasksel --list-tasks

# to open the tasksel user interface menu to install software applications
# where you see an asterisk (*) without the red highlighter,
# it means that software is already installed
sudo tasksel

# to add / remove a tasksel package, use the following syntax
sudo tasksel install <tasksel_name>
sudo tasksel remove <tasksel_name>
```

Sources:

* [How To Install And Configure VNC On Ubuntu 20.04?](https://www.imaginelinux.com/install-and-configure-vnc-on-ubuntu/)

#### Step 2: Install Desktop Environment Using Tasksel - DONE
`tasksel` will download and install all of the packages required for the desktop environment.
Depending on which GUI is being installed,
you may be prompted during installation on whether or not you wish to change
the default window manager for the system.

```bash
# install the default xubuntu desktop environment
sudo tasksel install xfce-desktop
```

At this point, the GUI could be started, but we want it to start automatically.
In case the GUI is not starting at all, make sure your system boots into the graphical target.
To do so execute:

```bash
# after installation, reboot your system
reboot

# make sure your system boots into graphical user interface
sudo systemctl set-default graphical.target
```

You may need to select your desired desktop flavor on the login page
(aka display manager) before you login.
In case the GUI is not starting at all,
make sure your system boots into the graphical target.
To do so execute: `sudo systemctl set-default graphical.target`.



[01]:https://www.amazon.com/gp/product/B01CVOLVPA/
[02]:https://support.google.com/chromebook/answer/9367166?hl=en#:~:text=Auto%20Update%20Expiration%20policy,receive%20software%20updates%20from%20Google.
[03]:https://en.wikipedia.org/wiki/Light-weight_Linux_distribution
[04]:https://galliumos.org/
[05]:https://lubuntu.me/
[06]:https://xubuntu.org/
[07]:https://www.ventoy.net/en/index.html
[08]:https://www.ventoy.net/en/screenshot.html
[09]:https://www.ventoy.net/en/doc_start.html
[10]:https://xubuntu.org/download/
[11]:https://www.youtube.com/watch?v=7Ng8D6qi6a8
[12]:https://www.xfce.org/
[13]:https://www.androidpolice.com/how-to-enter-chromeos-developer-mode/
[14]:https://www.wikihow.com/Enable-USB-Booting-on-Chromebook
[15]:https://ubuntu.com/blog/desktop
[16]:https://ubuntu.com/download/server
[17]:https://mrchromebox.tech/
[18]:https://www.coreboot.org/users.html
[19]:https://www.quora.com/What-is-difference-between-BIOS-UEFI-bootloader-and-firmware
[20]:https://mrchromebox.tech/#fwscript
[21]:https://www.tightvnc.com/
[22]:https://www.reddit.com/r/GalliumOS/comments/8cydt1/howto_flash_full_rom_ie_coreboot_and_install/
[23]:https://en.wikipedia.org/wiki/Framebuffer
[24]:https://help.ubuntu.com/community/Tasksel
[25]:https://wiki.debian.org/DisplayManager
[26]:https://ubuntu.com/blog/whats-new-in-ubuntu-desktop-20-04-lts
[27]:https://linuxconfig.org/the-8-best-ubuntu-desktop-environments-22-04-jammy-jellyfish-linux
[28]:https://wiki.archlinux.org/title/window_manager
[29]:https://wiki.archlinux.org/title/xorg
[30]:https://wiki.archlinux.org/title/Wayland
[31]:https://en.wikipedia.org/wiki/Compositing_window_manager
[32]:https://manpages.ubuntu.com/manpages/xenial/man8/gdm3.8.html#:~:text=gdm3%20is%20the%20equivalent%20of,conf%20for%20its%20configuration.
[33]:https://wiki.ubuntu.com/LightDM
[34]:https://manpages.ubuntu.com/manpages/bionic/en/man1/xfwm4.1.html

[55]:https://novnc.com/info.html
[56]:https://en.wikipedia.org/wiki/X11vnc

