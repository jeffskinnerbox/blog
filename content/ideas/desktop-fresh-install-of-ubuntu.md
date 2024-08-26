<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------


# Background
I first establish my Linux desktop environment in 2013 with Ubuntu 13.04.
I repeatedly upgraded desktop, generally twice a year, with the latest release.
When the year 2022 came around, Ubuntu 22.04 is available for another upgrade.
After these 9+ years, obtaining a smooth / flawless upgrades is very unlikely.
I have to face the fact that my Ubuntu system is a bit messed up,
and despite trying numerous ways to fix it,
the easiest way out seems to be to reinstall Ubuntu.
So I did just that in 2022 and these notes were written to help document that procedure.

It is now 2024, and I'm replacing my Linux hardware ... motherboard, CPU, memory, and SSD for the operating system are all being upgraded.
The only thing not being replace are the hard drives, and its contents, for my user `/home` directories.
These directories are on a pair of 1T RAID hard drives containing all that I have created.
I plan to move these drives, without any changes, to my new hardware environment with a fresh Ubuntu OS install.

Below is how I did the Ubuntu fresh install.
No rocket science hear, in fact, its just repeat what may have been done years ago.
Never the less, I wanted to keep good notes on what I did,
so when the day come when it needs to be done again,
I have a record I can review.

The most important thing of all is obvious:
make sure to backup everything you hold dear & want to keep,
and also backup everything else.
In 2013 I expected this day to come, so I mounted my `/home` directory
on a RAID 1 (aka mirrored) 1TB drive.
This gave me confidence that I could survive a single disk failure
(which it did) and this RAID 1 configuration could be easily ported
to a fresh install (it did not ... most likely because I don't understand Linux's RAID tools).
I survived this because I had also automated backups of my `/home` directory,
taken every 4 hours.
The backed up version of `/home` has all my files and all the configuration files
(e.g. [`.bash`][05], [`.vim`][06], [`.conky`][07], etc.), for my working environment.

This 2024 upgrade has gone smoother the Ubuntu install spotted the RADI disks
and made the appropriate OS modifications,
making the reestablishment of the `/home` directory happen easily.



---------------



# Install Ubuntu 23.10 - DONE
First, [download Ubuntu from its website][01].
Once you have got the ISO image, it’s time to [create a live USB][02] from it,
and [perform the install][03].

**NOTE:** With version 22.04, Ubuntu switches to the Wayland display server by default once again.
Wayland continues to be used in Ubuntu 23.10.

**NOTE:** Once the Ubuntu OS is installed,
your likely going to need terminal access to perfrom the operations listed below.
On Ubuntu, you can popup a terminal via the keyboard sequance of `Cntl+Alt+T`.

**NOTE:** If you wan to see the console messages created during the boot,
press the `F1` key.

**NOTE:** If for any reason you to access the motherboard for things like
BIOS setting, drive boot order, modification of suspend state, etc.,
you can do this by pressing the `Del` (aka Delete key) during a reboot.



---------------



#  Establish Fail-Safe User Account - DONE
To assure I have a [fail-safe][41] measure to recover from human errors,
I'll create a user account, with root privileges,
just in case I screw-up the establishment of the `/home`
directory.

For this user account,
make sure to place its home directory **some where other than `/home`**.
Its the failure of the `/home` directory that represents the greatest threat to having a good day.
The sole purpose of this fail-safe user account to maintain an healthy account
even if you blow away the `/home` directory.
You'll have this user account when you screw up big time,
potentially allowing you to survive your stupidity!

In Ubuntu, there are two command-line tools that you can use to create
a new user account: `useradd` and `[adduser][04]`.
`useradd` is a low-level utility.
`adduser` is a script that acts as a friendly interactive frontend for `useradd`.
A quick and easy way to add a user is by invoke the command:
`sudo adduser <username>`.

>**NOTE:** If you want the new user to be able to perform administrative tasks,
>you need to add the user to the `sudo` group: `sudo usermod -aG sudo username`.

>**NOTE:** To delete the user, invoke the `deluser` command and pass the username
>as the argument: `sudo deluser <username>`.
>If you want to delete the user and its home directory and mail spool,
>use the `--remove-home` flag: `sudo deluser --remove-home username>`.

Source:
* [How to Add and Delete Users on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-add-and-delete-users-on-ubuntu-18-04)

#### Step 1: Create User Account - DONE
This fail-safe user account's home directory will reside on
the disk where the operating system resides under the `/mnt` directory
and be in the same group as my user account.
The `/mnt` directory is the safe place to reside because we'll be messing
with the other drives and if they could get corrupted, we can use this account.

```bash
# add the user
sudo adduser --home /mnt/jeff-admin --ingroup jeff jeff-admin

# give the new account root privileges
sudo usermod -aG sudo jeff-admin
```

#### Step 2: Delete User Account
Once this "fresh install" process is completed,
there is little need for this special user account.
At that time, you can delete this account via:

```bash
# check if the user has any important files in its home directory
ls /mnt/jeff-admin

# delete the user itself, and deleting any of their files
sudo deluser --remove-home jeff-admin

# remove any files
sudo rm -rf /mnt/jeff-admin

# to prevent a new user created with the same name from being accidentally given sudo privileges
# remove references to jeff-admin
sudo visudo
```

**Don't do this step now but return to it when all the work is completed.**



---------------



# Install Your Favorate Tools
As I work throught this installation process,
I'm going to want to use all my firmular tools,
tools like Gnome Terminal, Curl, Chrome browser, NeoVim, etc.
Lets get these installed.

#### Step 1: Supporting Packages - DONE
```bash
# install packages for general use
sudo apt -y install trash-cli gnome-terminal git jq vim tmux wmctrl curl stow xclip

# install basic networking tools
sudo apt -y install net-tools nmap traceroute arp-scan netdiscover

# packages which let apt get packages over HTTPS
sudo apt -y install apt-trans port-https ca-certificates curl software-properties-common

# install packages for for creation of raid
sudo apt -y install smartmontools mdadm

# install tools required by ansible
sudo apt -y install sshpass lookup acl
```

Next we will update the packages on your system
and install codecs for proprietary files with restricted copyright
(MP3, AVI, MPEG, Microsoft fonts) and Adobe Flash Player.

>**NOTE:** During `sudo apt-get update && sudo apt-get dist-upgrade` below, I got the message:
>*Warning: os-prober will be executed to detect other bootable partitions.
>Its output will be used to detect bootable binaries on them and create new boot entries.
>Found Ubuntu 23.10 (23.10) on `/dev/sdb6` Adding boot menu entry for UEFI Firmware Settings ...*
>I got a similar message during `sudo apt-get -y install smartmontools mdadm`.
>
>It appears the upgrade triggered the preparation of the OS to support RAID,
>and I benefited from this when I move my RAID hard drive onto this fresh install.

```bash
# update the packages on your system
sudo apt update && sudo apt dist-upgrade

# install codecs for proprietary files with restricted copyright
sudo apt install ubuntu-restricted-extras

# tools need for video card install
sudo apt install hwinfo

# install the spice client for use with proxmox
# NOTE: kvm conflicts with virtualbox
#sudo apt-get install qemu-kvm virt-viewer
```

You can't use Virtualbox alongside KVM,
choose one or the other, since they hypervisors fight over control.
you can temporally disable KVM or VirtualBox modules and then re-enable them when you want.

>**NOTE:** KVM and VitualBox **do not** play nice together.
>[VirtualBox will throw a Guru Meditation error][47] if KVM is installed.

```bash
# are kvm and virtualbox modules installed
$ sudo lsmod | grep -e vbox -e kvm
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               610304  2 vboxnetadp,vboxnetflt
kvm_intel             368640  4
kvm                  1028096  1 kvm_intel

# check if any processes are using kvm
ps aux | grep kvm

# unload the running kvm modules
# this temporary stop kvm until reinstalled or when you reboot
sudo rmmod kvm-intel kvm
```

#### Step 2: Install Your `.dotfiles` - DONE
Within my GitHub, I maintain my dotfiles and the mainteance tool that I use is `stow`.
Let's pull down the latest `.dotfiles` reposaitory and an install anything required:

```bash
# make sure you have install your version of the .dotfiles
cd $HOME
git clone https://github.com/jeffskinnerbox/.dotfiles.git

# put into you '.bashrc' file the environment variable for the path to `.config` directory
export XDG_CONFIG_HOME=$HOME/.config

# stow all your dotfile package - aka create your symlinks for your configuration files
stow --dir=$HOME/.dotfiles --target=$HOME --stow pkg-X
stow --dir=$HOME/.dotfiles --target=$HOME --stow pkg-i3
stow --dir=$HOME/.dotfiles --target=$HOME --stow pkg-vim
stow --dir=$HOME/.dotfiles --target=$HOME --stow pkg-tmux
stow --dir=$HOME/.dotfiles --target=$HOME --stow pkg-bash
stow --dir=$HOME/.dotfiles --target=$HOME --stow pkg-conky
stow --dir=$HOME/.dotfiles --target=$HOME --stow pkg-screen
stow --dir=$HOME/.dotfiles --target=$XDG_CONFIG_HOME --stow pkg-nvim
stow --dir=$HOME/.dotfiles --target=$XDG_CONFIG_HOME --stow pkg-yamllint
stow --dir=$HOME/.dotfiles --target=$XDG_CONFIG_HOME --stow pkg-ansible-lint
```

#### Step 3: Install Miniconda for Python Work - DONE
[Python][67] is such a success in large part because of its very active community
in which people share their awesome solutions.
Unfortunately, there is a price.
[Python packages][68] you used get updated with a better way to solve their problem.
These changes can be breaking changes for the code you have written.

There are several ways to deal with this issue and I have choosen to manage it by using
[Miniconda][70], a much smaller base installation than [Anaconda][69],
but with the ability to scale up to the whole Anaconda distribution, if you chose to do so.
The Miniconda Python system requires ~400MB of disk space, where Anaconda requires ~3GB of disk space

The following steps install Miniconda.
Not only will Miniconda will be installed but your `bash` shell environment
(specifically the files `.bashrc` or `.bash_profile`)
will be updated to include Miniconda in the `$PATH`.
Also, if the environment variable `$PYTHONPATH` is set, you will get a warning like
"_please verify that your $PYTHONPATH only points to directories of packages that are compatible with the Python interpreter in Miniconda3_"

```bash
# create a directory to install miniconda in
mkdir -p ~/.miniconda3

# download latest miniconda version
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/.miniconda3/miniconda.sh

# run the install script
bash ~/.miniconda3/miniconda.sh -b -u -p ~/.miniconda3

# delete the install script
rm -rf ~/.miniconda3/miniconda.sh

# add a conda initialize to your bash   <-- DO NOT run `conda init bash` if you plan to use `~/.dotfile` since it already contains the changes needed for `~/.bashrc`
#~/.miniconda3/bin/conda init bash

# verify the installation by listing the contents of the install
conda list

# list the envirnments established (should only be 'base')
conda env list
```

Following the steps above, restart the terminal and Miniconda is ready to go.

To uninstall Miniconda, you follow these steps:

```bash
# backup any important data and python environments
conda env export > environment.yml

# locate miniconda directory and delete it
ls -a ~ | grep miniconda
rm -rf ~/.miniconda3

# remove conda configuration files (optional)
rm -rf ~/.condarc ~/.conda

# open file editor and remove miniconda path from .bashrc or .bash_profile
#    open the file in a text editor, find the line that contain
#    references to miniconda and remove them
```

Sources:
* [Install Miniconda on Linux from the command line in 5 steps](https://javedhassans.medium.com/install-miniconda-on-linux-from-the-command-line-in-5-steps-403912b3f378)
* [How to Uninstall Miniconda on Linux: A Guide](https://saturncloud.io/blog/how-to-uninstall-miniconda-on-linux-a-guide/)

#### Step 4: Google Chrome - DONE
My go-to browser is Chrome and you can install it on Ubuntu from [here][50].

```bash
# download the latest Google Chrome .deb package
mkdir tmp
cd tmp
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

# installing packages on Ubuntu
sudo apt install ./google-chrome-stable_current_amd64.deb
```

Installing Chrome will also add the repository to your package manager.
Use the following command to keep Chrome up to date on your system.

```bash
# to update chrome, use the following
sudo apt install google-chrome-stable
```

If you decide that you’d like to remove Chrome from your system in the future,
use the following command to uninstall the web browser.

```bash
# use the following to remove chrome
sudo apt purge google-chrome-stable
```

#### Step 5: NeoVim - DONE
There are several sources for [NeoVim][51],
but I have found that [Snap][54] has one of the most up to date versions.
I installed NeoVim via the Snap Store using this method:

```bash
# neovim nightly & stable are available on the snap store

# stable builds for i386 architecture - latest/stable v0.9.4
sudo snap install nvim --classic

# to update snap package for neovim
sudo snap refresh nvim

# check the nvim version
$ nvim --version | grep NVIM
NVIM v0.9.4
```

On a fresh install of NeoVim,
if you open `nvim` and enter the following command [`:checkhealth`][52] in Command mode
you'll get a lengthy report with some lines containing warnings and errors.
Let's fix these problems.

First off, make sure you have installed Neovim version 0.9 or greater (and we have done so).
Also install [Nerd Fonts][53] but this comes with the `/home` directory we mounted from the old computer.
A key thing to do is fix copy & paste by installing the appropriate clipboard:

```bash
# check for type of display server you are running (wayland / X11)
$ echo $XDG_SESSION_TYPE
wayland

# if your using X Window's X11 protocol
sudo apt install xsel

# if your using X Window's Wayland protocol
sudo apt install wl-clipboard
```

To fix complaints about lack of Python, Node.js, `ripgrep` support,
you need to install Python, Node.js, and other tools.
This should be already established on the `/home` drive.
**Note** that I'm using Miniconda for my Python envirnment
you must activate the `base` envirnment, if not already done via your shell.

```bash
# activate you python envirnment
conda activate base

# neovim python support
pip install pynvim

# neovim node support
npm i -g neovim        # install failed for some reason

# ripgrep (executable is called `rg`) is need by for telescope
sudo apt install ripgrep
```

#### Step 6: Tmux - DONE
The [Tmux Plugin Manager][77] (also known as `tpm`)
is designed to automatically manage the `tmux` plugins
and those plugins are [listed here][78].
By adding few lines into your `.tmux.conf` file,
you can easily activate plugins and extend the power of tmux beyond its default offering.

First, make sure you have install the all the reqired `.dotfiles` and it `.tmux`:

```bash
# install your version of the .tmux.conf file (along with all your other dotfiles)
git clone https://github.com/jeffskinnerbox/.dotfiles.git

# install the files via 'stow'
stow --dir=$HOME/.dotfiles --target=$HOME --stow pkg-tmux

# install xclip and wl-clipboard utilities to support cut&paste
sudo apt install wl-clipboard xclip
``````

Execute `tmux`, and once it is up & running,
enter `<perfix> I` (my `<prefix>` is `ctrl-s`)
to install all the plugins listed in the configuration file.
Next, exit and restart `tmux`.

If this appears to run fine, install your personalized configuration file that support your workflow.
Mine is found at `~/.dotfiles/tmux-pkg/tmux.conf`.

```bash
# create link to tmux configuration file (the modern way to manage dot files)
mkdir -p $XDG_CONFIG_HOME/tmux
trash $XDG_CONFIG_HOME/tmux/tmux.conf
ln -s ~/.dotfiles/tmux-pkg/tmux.conf $XDG_CONFIG_HOME/tmux/tmux.conf
```


---------------



# Setup Dual Monitor
My installation of the new motherboard and Ubuntu had no problem supporting one of the two monitors I'm using.
Now its time to bring the second monitor up and working.

Sources:

* [How do dual monitors work?](https://www.youtube.com/watch?v=rjNCWK_MfZs)
* [How to Use Onboard Graphics for Second Monitor](https://www.youtube.com/watch?v=8iT1pgPo-1E)
* [How to Setup Dual Monitor | Windows | Linux | MAC](https://www.technowifi.com/how-to/how-to-setup-dual-monitor/)
* [Raspberry Pi Adds Second Laptop Monitor](https://hackaday.com/2023/03/15/raspberry-pi-adds-second-laptop-monitor/#more-581185)
* [A Primer on Screen Blanking Under Xorg](https://shallowsky.com/linux/x-screen-blanking.html)
* [xscreensaver - extensible screen saver and screen locking framework](https://manpages.ubuntu.com/manpages/xenial/man1/xscreensaver.1.html)

## Procedure Used in 2022 - DONE, NOT
With my 2022 refresh of my Linux desktop computer,
I upgrading to a dual monitor configuration.
To do this,  I did the following:

1. Purchase another monitor display equivalent to my existing display
([32" LG 32GN50T-B Monitor Ultragear FHD SYNC][28]) and a [dual monitor stand][29].
2. Purchase a video card ([MSI Geforce 210][26] / [N210-MD1G/D3][27]) to drive the second monitor screen.
3. Need to modify BIOS on [motherboard (Intel Desktop Board DZ77GA-70K)][25] to support dual monitor.
4. Within Ubuntu on the **Settings** > **Displays** app, I'll need to configure the two displays
5. Set the brightness, color setting, etc. on the two displays to be visually equivalent.

#### Step 1: Wayland or X11 Display Manager - DONE, NOT
I read on the web that Wayland doesn't work well with a dual monitor setup, at least at in 2022.
I no long belive this is the case.
In 2022, to avoid this challenge, I choose to continue to use X11.

You can check for the display manager that you’re using with this command:

```bash
# check for type of display server (wayland / X11)
$ echo $XDG_SESSION_TYPE
wayland
```

You can also switch between Xorg (aka X11) and Wayland when you login.
You find a bottom at the lower right hand corner of the login screen.
The video "[How to Switch Between Xorg and Wayland in Ubuntu 20.04 18.04][21]"
shows how this is done.

Sources:
* [36C3 ChaosWest: X11 and Wayland: A tale of two implementations](https://www.youtube.com/watch?v=b8OY4VtYx1s)
* [WAYLAND: what is it, and is it ready for daily use?](https://www.youtube.com/watch?v=g1BoZnekkyM)
* [Wayland Is The Future Of Linux, What About Now?](https://www.youtube.com/watch?v=lm2aireP-wc)

The Ubuntu 24.04 releases feature the Wayland as its default display server.
This change is significant because it replaces the traditional Xorg Server,
which was the longstanding default before Wayland.
This change did appear to give me support problems with my MSI Geforce 210 graphics card.
I did the following to make X11 the default at boot time:

#### Step 1A: Choosing X11 or Wayland - DONE
**NOTES For 2024 Upgrade to Ubuntu 24.04**
Wayland is not shown as an option on the login screen
(or the cog icon of the login screen doesn't show at all).
I did the following to fix this:

1. Edit the `/etc/gdm3/custom.conf` file
2. Ensure that `WaylandEnable=true` is set in that file and make sure that it's uncommented (does not start with a #)
3. Reboot the system

Source:
* [NVIDIA Ubuntu Driver Guide](https://github.com/oddmario/NVIDIA-Ubuntu-Driver-Guide?tab=readme-ov-file#wayland-is-not-shown-as-an-option-on-the-login-screen-or-the-cog-icon-of-the-login-screen-doesnt-show-at-all)

#### Step 1B: Replace Nvidia Drivers - DONE, NOT
**NOTES For 2024 Upgrade to Ubuntu 24.04**
An alternative to using X11, and there for use the Ubuntu 24.04 default of Wayland,
is to install new Nvidia drivers.
From what I have read online,
it appears driver files with "NVIDIA driver 555.*.*" in their name is what is needed.
I choose not to install them at this time, but it will be required at some future date.

So you don't have to use Wayland in Ubuntu 24.04,
but it is the default desktop session for NVIDIA users with the
official NVIDIA Linux graphics driver in Ubuntu 24.10.

Sources:
* [How to Check NVIDIA Driver Version on Linux](https://linuxconfig.org/how-to-check-nvidia-driver-version-on-your-linux-system)
* [How to install Nvidia drivers on Ubuntu](https://www.xda-developers.com/how-to-install-nvidia-drivers-on-ubuntu/)
* [Ubuntu 24.10 Now Defaults To Wayland On NVIDIA](https://www.phoronix.com/news/Ubuntu-24.10-GDM-Wayland-NVIDIA)

#### Step 2: Modify BIOS on Motherboard - DONE, NOT
To enable multiple display, you first must enable it on the computer's motherboard.
In my case with the Intel DZ77GA-70K motherboard, I had to goto
**Advance Settings** > **Devices & Peripherals** > **Video**.

* For **Integrated Graphics Device** set to **Enable if Primary**
* For **Primary Video Adaptor** set to **Int Graphics (IGD)**

Sources:
* [Intel DZ77GA-70K Visual BIOS Overview](https://www.youtube.com/watch?v=dpZr2khbPWQ)
* [How To Enable Motherboard HDMI Port for Multiple Monitors - Use Graphics Card & Integrated Graphics](https://www.youtube.com/watch?v=_Ftk8jQhsqE)
* [How to clear CMOS on DZ77Ga-70k?](https://community.intel.com/t5/Intel-Desktop-Boards/How-to-clear-CMOS-on-DZ77Ga-70k/m-p/199753)
* [Bios Setup Configuration Jumper Settings - Intel DZ77GA-70K Specification](https://www.manualslib.com/manual/440805/Intel-Dz77ga-70k.html?page=64)

#### Step 3: Install Monitors and Video Card - DONE, NOT
I followed the install procedures that came with the devices.
It was basically "plug & play".

I did not install any special driver for the video card.
You find may references on the web about installing [Linux Nvidia drivers][30],
and may stories about things going wrong.
Try using the video card without new drivers first;
its likely good enough unless your a gamer.

#### Step 4: Configure Ubuntu for Multiple Displays - DONE, NOT
Within Ubuntu on the **Settings* > **Displays** app,
you'll need to configure the two displays.
This requires some playing around for what you prefers.
It's easy to do but [this website][31] might help.

Also, you'll want the two displays to be visually equivalent.
This involves setting the brightness, color setting, etc. to be the same on both displays.
For my displays, this required using [this feature][32].

>**NOTE:** Some of the information on the Web can be confusing concerning dual monitor.
>Ubuntu 22.04 has a different [Gnome Tweaks][18] and [Settings][19] apps
>from previous version, so documentation can be misleading.

Sources:

* [Connect another monitor to your computer](https://help.ubuntu.com/stable/ubuntu-help/display-dual-monitors.html)
* [How to install Tweak Tool on Ubuntu 22.04 LTS Jammy Jellyfish Linux](https://linuxconfig.org/how-to-install-tweak-tool-on-ubuntu-22-04-lts-jammy-jellyfish-linux)
* [Ubuntu 20.04: Workspaces and Multiple Monitors](https://www.thegygers.com/2020/07/30/ubuntu-20-04-workspaces-and-multiple-monitors/)
* [Switch workspace on dual monitor 22.04](https://askubuntu.com/questions/1403554/switch-workspace-on-dual-monitor-22-04)
* [Ubuntu: How to set each workspace to a separate monitor](https://superuser.com/questions/13096/ubuntu-how-to-set-each-workspace-to-a-separate-monitor)
* [How To Configure Your Monitors With Xrandr in Linux](https://linuxconfig.org/how-to-configure-your-monitors-with-xrandr-in-linux)

## Procedure Used in 2024 - DONE
In 2024, I have been using two moniors for sometime, with Wayland, and the video card works fine.
All that needs to be done is set the motherboard and Ubuntu for dual monitors.

#### Step 1: Modify BIOS on Motherboard - DONE
My new motherboard is the [MSI PRO Z690-A ProSeries][55]
and I continued to use the old video card ([MSI Geforce 210][26] / [N210-MD1G/D3][27])
to drive the second monitor screen.

I set the BIOS of the motherboard to initial graphics adapter would be the CPUs Intgrated Graphics Device (IGD).
I found that multi-monitor support was activated by default, but enable this if not.

Sources:
* [MSI PRO Z690-A ProSeries: Manual & Documents][56]

#### Step 2: Configure Ubuntu for Multiple Displays - DONE
Within Ubuntu on the **Settings* > **Displays** app,
you'll need to configure the two displays.
This requires some playing around for what you prefers.
It's easy to do but [this website][31] might help.


---------------



# Set-Up Networking - DONE
It appears the virtualization of network devices and applications,
the world of Linux networking has evolved into a confusing mess.
There is currently (at least) four approaches to networks in Linux:

1. The oldest of the four uses the /`etc/network/interfaces` file
and `ifup` / `ifdown` scripts to manage these interfaces.
While this is an old approach, its well understood and works,
but not well suited for the casual Linux user or complex configurations.
Proxmox is an example where this method is used.
2. After that came the network manager daemon (often written [NetworkManager][09])
which has GUI interfaces available.
NetworkManager is a daemon that sits on top of Linux kernel
and provides a mechanism to configuration the network interfaces.
It manages your network devices
and attempts to keep network connectivity active when available.
It manages Ethernet, WiFi, mobile broadband (WWAN), and PPPoE devices
while also providing VPN integration with a variety of different VPN services.
3. And most recently the `systemd-networkd` daemon
(often abbreviated just 'networkd')
which is based on `systemd` unit files.
4. Ubuntu has switched to [Netplan][12] for the configuration of network interfaces.
Netplan uses a YAML-based configuration approach,
with the aim of makes the configuration process simple.
Netplan has replaced the old `/etc/network/interfaces` configuration file
and accommodates the needs of both NetworkManager or `systemd-networkd`.
By default the only file present on a fresh installed Ubuntu 22.04 system
is [`/etc/netplan/01-network-manager-all.yaml`][13].

Sources:

* [How to Use NetPlan in Ubuntu 18.04](https://www.youtube.com/watch?v=HlOY1ucz_DY)
* [Why did Ubuntu change the network configuration](https://askubuntu.com/questions/1005390/why-did-ubuntu-change-the-network-configuration)
* [Ubuntu Bionic: Netplan](https://ubuntu.com/blog/ubuntu-bionic-netplan)
* [Ubuntu 22.04 network configuration](https://linuxconfig.org/ubuntu-22-04-network-configuration)
* [Netplan network configuration tutorial for beginners][13]
* [How to switch back networking to /etc/network/interfaces on Ubuntu 20.04 Focal Fossa Linux](https://linuxconfig.org/how-to-switch-back-networking-to-etc-network-interfaces-on-ubuntu-20-04-focal-fossa-linux)
* [How to configure networking with Netplan on Ubuntu](https://vitux.com/how-to-configure-networking-with-netplan-on-ubuntu/)
* [Have a Plan for Netplan](https://www.linuxjournal.com/content/have-plan-netplan)
* [Ubuntu netplan gateway4 has been deprecated](https://tizutech.com/ubuntu-netplan-gateway4-has-been-deprecated/)
* [Netplan reference](https://netplan.io/reference/)
* [Netplan configuration examples](https://netplan.io/examples/)
* [How to Configure Netplan Network? – LAB Examples](https://getlabsdone.com/how-to-configure-netplan-network/)

#### Step 1: Check How is Your Network Being Managed - DONE
To see how your network is being managed,
first you must know if you're system is initializing with `systemd`
or the older `init` as it's first process.
`init` is planned to be replaced by `systemd` on may instances of Linux.
(Debian and Ubuntu, for example now use `systemd` instead of `init`).

You can check if your system uses `systemd` with this:

```bash
# check if your system is using systemd
pidof systemd && echo "systemd" || echo "other"
```

So if you are **NOT** running `systemd`,
then clearly you can rule out `systend-networkd`.

If you **ARE** running `systemd`,
then check which network service daemons are running with these two commands:

```bash
# check for which network service is running
sudo service systemd-networkd status | grep Active
sudo service network-manager status | grep Active
```

If you see either "Active: active (running)" or "Active: inactive (dead)" reported for each one.

But there is one finally consideration.
Even if one of these two daemons are running,
that it doesn't necessarily mean your network hardware interfaces are being managed by them.

* Any interfaces defined in `/etc/network/interfaces` can be ignored by network-manager
(see "managed=false | true" in [networkmanager.conf(5)][10] Linux manual page)
* The daemon systemd-networkd will only manage network addresses and routes
for any link for which it finds a `*.network` file with an appropriate [Match] section.
(see ".network" in [systemd-networkd.service(8)][11] Linux manual page).

```bash
# check if your system is using systemd
$ pidof systemd && echo "systemd" || echo "other"
1593
systemd

# conclusion: all three are still posible

# check for which network service is running
$ sudo service systemd-networkd status | grep Active
     Active: inactive (dead)
$ sudo service network-manager status | grep Active
Unit network-manager.service could not be found.

# conclusion: network-manager (aka networkmanager) is not being used

# check for a /etc/network/interfaces file
$ FILE=/etc/network/interfaces ; [ -f $FILE ] && echo "The file $FILE exist." || echo "The file $FILE does not exist."
The file /etc/network/interfaces does not exist.

# conclusion: /etc/network/interfaces is not being used

# final conclusion: systemd is being used
```

Sources

* [Am I running NetworkManager or networkd?](https://askubuntu.com/questions/1031439/am-i-running-networkmanager-or-networkd)

#### Step 2: Configuring Your Ethernet Connection - DONE
All of the above is a bit overwhelming.
I just want to do some basic configuration of my networks.
The install of Ubuntu defaulted to DHCP Ethernet connection with no WiFi.
I want to change this so the Ethernet is a static IP
and WiFi is also operational using DHCP
(assuming the motherboard supports WiFI, in my case it does not).

You can make these updates with `Settings` app in the Ubuntu desktop toolbar.
I used the settings below:

```
# static ip address for ethernet connection
IP Address  192.168.1.200
Gateway     192.168.1.1
Net Mask    255.255.255.0
DNS         192.168.1.1, 1.1.1.1, 1.0.0.1
```

Make sure to reboot when completed and validate the change.

#### Step X: Configuring Your WiFi Connection - DONE, NOT
Again using the `Settings` app in the Ubuntu desktop toolbar,
configure your WiFi for a DHCP connection.

#### Step X: Configure Your Network via Netplan - DONE, NOT

```yaml
#
# 01-network-manager-all.yaml
#
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    eth0:
      dhcp4: false
      addresses: [192.168.1.200/24]
      #gateway4: 192.168.1.1
      routes:
        - to: default
          via: 192.168.1.1
      nameservers:
        addresses: [192.168.1.1, 8.8.8.8, 8.8.4.4]
```

This was error free but I could route to Internet sites ...

```yaml
#
# 01-network-manager-all.yaml
#
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    eth0:
      dhcp4: false
      addresses: [192.168.1.200/24]
      #gateway4: 192.168.1.1
      routes:
        - to: default
          via: 192.168.1.1
          table: 101
      nameservers:
        addresses: [192.168.1.1, 8.8.8.8, 8.8.4.4]
  wifis:
    wlan0:
      dhcp4: true
      access-points:
        "<ssid>":
          password: "<password>"
      routes:
        - to: default
          via: 192.168.1.1
          table: 102
      nameservers:
        addresses: [192.168.1.1, 8.8.8.8, 8.8.4.4]
```

#### Step X: Test and Apply Your Network Configuration - DONE, NOT
* **`netplan try`** is used to try a configuration,
and optionally roll it back if the user doesn’t confirm it after a certain amount of time.
The default timeout is of 120 seconds but it can be changed using the --timeout option.
* **`netplan generate`** command converts the settings in the yaml files to configurations
appropriate to the renderer in use, but does not apply them.
(**NOTE:** Generally, it is not meant to be called directly:
it is invoked by `netplan apply` which additionally applies the changes without a “revert” timeout.)
* **`netplan apply`** will implement the configuration

Testing the Netplan configuration:

```yaml
# testing the netplan configuration
sudo netplan try --timeout 20

# now apply the new configurations
sudo netplan apply
```

In case you see any error, try debugging to investigate the problem.
To run debug, use the following command

```yaml
# run in debug mode to investigate problems
sudo netplan apply --debug
```

#### Step X: Restart the Network Service - DONE, NOT
Once all the configurations are successfully applied,
restart the Network-Manager service by running the following command:

```bash
# restart the network-manager service
sudo systemctl restart network-manager
# OR
# restart system-networkd
sudo systemctl restart system-networkd

# verify if the new configurations are successfully applied
ip address
```



---------------



# Mount NFS, SSDs, and RAID Drive - DONE
First, you'll need to find what disks you have install,
regardless if they are mounted or not.
You can do this with the `fdisk` command and via the `/etc/fstab` file.

Sources:
* [How To Manage RAID Arrays with mdadm on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-manage-raid-arrays-with-mdadm-on-ubuntu-16-04)
* [HOWTO: Repair a broken Ext4 Superblock in Ubuntu](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

## Procedure Used in 2024 - DONE
The procedure I used in 2024 was much easier since the Ubuntu install script
detected that I had some RAID disks and it condition the operating install to prepare for the RAID install.
The steps below document how this RAD activation went so that my
`/home` directory could be seamlessly ported to the new hardware.

#### Step 1: Gather Data - DONE
I want to mount my RAID drive and the Ubuntu install said that it sensed the RAID instance.
less gather some more information:

```bash
# gather some facts about the drives avalable mounted or unmouted
$ sudo fdisk -l | grep Disk | grep -v loop | grep -v dos
Disk /dev/nvme0n1: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: CT500P3PSSD8
Disklabel type: gpt
Disk identifier: 185E6172-8674-4D1B-9E24-816F168E112F
Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-1CH1
Disk identifier: 0xe9fd17be
Disk /dev/sdb: 119.24 GiB, 128035676160 bytes, 250069680 sectors
Disk model: Samsung SSD 840
Disk identifier: 0x0008f01d
Disk /dev/sdc: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-1SB1
Disk identifier: 0xe9fd17be
Disk /dev/md0: 931.39 GiB, 1000069595136 bytes, 1953260928 sectors
```

This tells us ...
* `/dev/nvme0n1` - This is the 500G NVME M.2 SSD drive and used to boot my new computer, only 221G partision is being sensed and the other particions are not.
* `/dev/sda` - This is one of the 1T RAID drives used for my old computers `/home/jeff`.
* `/dev/sdb` - This is my old computer's Samsung SSD I used for booting my old computer
* `/dev/sdc` - This is one of the 1T RAID drives used for my old computers `/home/jeff`.
* `/dev/md0` - This this is the RAID drive version used for my old computers `/home/jeff`.

I want to restablish the `/dev/md0 RAID` (made fron `/dev/sda` & `/dev/sdc`),
mount it as `/home/jeff`, and mount `/dev/sdb` it as `/old_computer` so I can temprarally access it if I wish too.

Now gathering some more information:

```bash
$ sudo fdisk -l /dev/sda /dev/sdc
Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-1CH1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xe9fd17be

Device     Boot Start        End    Sectors   Size Id Type
/dev/sda1        2048 1953525167 1953523120 931.5G 83 Linux


Disk /dev/sdc: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-1SB1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xe9fd17be

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdc1        2048 1953525167 1953523120 931.5G 83 Linux
```

```bash
$ sudo fdisk -l /dev/md0
Disk /dev/md0: 931.39 GiB, 1000069595136 bytes, 1953260928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
```

#### Step 2: Temporary Mount of RAID - DONE
Sensing that everything was ready for the RAID to be mounted,
I temporarily mounted the RAID with
and measure the amount of data it contained just to see if all was well:

```bash
# temporarily mount the raid drive
sudo mount /dev/md0 /mnt/jeff-admin

# measure the data on the raid drive to see if you have any access problems
du -h /mnt/jeff-admin
```

All seems well so next I will permanently mounting the RAID drive by updating the /`etc/fstab` file.

#### Step 3: Mount RAID at Boot Time - DONE
To make sure that the array is reassembled automatically at boot,
I'm going to add the new filesystem mount options to the /`etc/fstab` file.

```bash
# make a backup of your working fstab
sudo cp /etc/fstab /etc/fstab.bak

# inject command to automatic mount array at boot
echo '/dev/md0 /home ext4 defaults,nofail,discard 0 0' | sudo tee -a /etc/fstab

# inspect /etc/fstab
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during curtin installation
/dev/disk/by-uuid/711cf65d-d8e2-4b88-8df2-7a2f9380d889 / ext4 defaults 0 1
# / was on /dev/nvme0n1p3 during curtin installation
/dev/disk/by-uuid/0bd118bd-c18f-4231-9184-29bebc0cbdca / ext4 defaults 0 1
# /boot/efi was on /dev/nvme0n1p1 during curtin installation
/dev/disk/by-uuid/0919-A14F /boot/efi vfat defaults 0 1
/swap.img	none	swap	sw	0	0
/dev/md0 /home ext4 defaults,nofail,discard 0 0
```

We can use [`sudo blkid -o list` or `blkid --uuid <device>`][59]
to identify the device name and UUID:

```bash
# mount = /   - Crucial P3 Plus 500GB PCIe 4.0 3D NAND NVMe M.2 SSD
$ blkid --uuid 711cf65d-d8e2-4b88-8df2-7a2f9380d889
/dev/nvme0n1p2

# mount = /   - Crucial P3 Plus 500GB PCIe 4.0 3D NAND NVMe M.2 SSD
$ blkid --uuid 0bd118bd-c18f-4231-9184-29bebc0cbdca
/dev/nvme0n1p3

# mount = /boot/efi  - Crucial P3 Plus 500GB PCIe 4.0 3D NAND NVMe M.2 SSD
$ blkid --uuid 0919-A14F
/dev/nvme0n1p1
```

Now if you do a `df -h`, and compare, you'll see a problem here.
The device `/dev/nvme0n1p2` (aka uuid = `711cf65d-d8e2-4b88-8df2-7a2f9380d889`)
never gets monuted.
I believe this is because both `/dev/nvme0n1p2` and `/dev/nvme0n1p3` used the same mount point `/`.
I'm going to make the mount point for `/dev/nvme0n1p2` be `/home2`.
Also, my old Samsung SSD drive, left installed just in case I hade boot problems,
was temporally mounted on `/media/jeff`.

I want to fix all this, so here is my approach:

1. We need to remove the existing `/home` directory so the `/etc/fstab` can mount the drive in its place.
I'll replace the contents of `/home` with the backup login I created earlier.
2. Change mount point of  `/dev/nvme0n1p2` to `/home2`.
3. For my backup process (addressed later) crate a mount for my Synology DS220+ NAS.
4. Make sure to create to create all mount point in the `/etc/fstab` file

```bash
# move the /home directory to a safe place
mkdir /mnt/jeff-admin/tmp
mv /home /mnt/jeff-admin/tmp

# to get a complete list of disk drives uuid
sudo blkid -o list

# create the new mount points and validate its access rights
sudo mkdir /home2
ls -l / | grep home
``
# create the new mount points and validate its access rights
sudo mkdir /old_computer
ls -l / | grep old_computer
```

Here is the `/etc/fstab` file I install:

```bash
#                   <file system>                         <mount point>   <type>   <options>               <dump>  <pass>
# was /dev/nvme0n1p1 during installation - Crucial P3 Plus 500GB PCIe 4.0 3D NAND NVMe M.2 SSD
/dev/disk/by-uuid/0919-A14F                                 /boot/efi      vfat     defaults                  0       1

# was /dev/nvme0n1p2 during installation - Crucial P3 Plus 500GB PCIe 4.0 3D NAND NVMe M.2 SSD
/dev/disk/by-uuid/711cf65d-d8e2-4b88-8df2-7a2f9380d889      /home2         ext4     defaults                  0       1

# was /dev/nvme0n1p3 during installation - Crucial P3 Plus 500GB PCIe 4.0 3D NAND NVMe M.2 SSD
/dev/disk/by-uuid/0bd118bd-c18f-4231-9184-29bebc0cbdca      /              ext4     defaults                  0       1

# was /swap.img during installation
swap.img                                                    none           swap        sw                     0       0

# was /dev/md0 RAID disk formed from /dev/sda and /dev/sdc during installation - Seagate 1TB HDD (model ST1000DM003)
#/dev/disk/by_uuid/126e8dc9-e13c-440f-bb02-dc266378329f      /home          ext4     defaults,nofail,discard   0       0   # <-- doesn't seem to work
/dev/md0                                                    /home          ext4     defaults,nofail,discard   0       0

# was /dev/sdb6 during installation - Samsung Electronics 840 Pro Series 2.5-Inch 128GB SSD
/dev/disk/by-uuid/65e559c7-e595-4ab6-89a1-7b27d071bc3d      /old_computer  ext4     defaults                  0       1
```

Now test if the RAID array `/dev/md0` and the unmounted partition `/dev/nvme0n1p2`
gets auto-mounted by doing a rebooting.

```bash
# do a reboot
sudo shutdown -r now

# check the filesystem
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           3.2G  2.4M  3.2G   1% /run
efivarfs        256K   97K  155K  39% /sys/firmware/efi/efivars
/dev/nvme0n1p3  211G   19G  181G  10% /
tmpfs            16G     0   16G   0% /dev/shm
tmpfs           5.0M   16K  5.0M   1% /run/lock
/dev/sdb6       109G   41G   63G  40% /old_computer
/dev/nvme0n1p2  246G   28K  233G   1% /home2
/dev/nvme0n1p1  1.1G  6.1M  1.1G   1% /boot/efi
/dev/md0        916G  467G  403G  54% /home
tmpfs           3.2G   96K  3.2G   1% /run/user/1000
```

The above shows all is well now.

#### Step 4: Set Up a NFS Mount - DONE
NFS is a distributed file system protocol that allows you to mount remote directories on your server.
This lets you manage storage space in a different location and write to that space from multiple clients.
We have two servers in our architecture, with one sharing part of its filesystem (Synology NAS) with the other (`desktop`).
Each of these should have a non-root user with sudo privileges,
a firewall set up with UFW, and private networking if it’s available to you.
I'll refer to the server that shares its directories as the **host** and the server that mounts these directories as the **client**.

On the **host** you must have installed the `nfs-kernel-server` package,
which should already have been done when NFS was activated on the Synology NAS.
We will now focus on the **client** server.

>**NOTE:** I'm mounting the **host** (aka Synology NAS) on the directory `/home2/nfs/synology-nas`.
>I'm choosing a file system that doesn't involve my OS root directery (aka `/`).
>I'm do this becasue in the past, when I have had device mounting problems,
>I would end up filling my root directory with files and causing my OS to crash.
>By using `/home2` when have these problems, I fill up a file system but the OS continues without crashing.

Lets install on the **client** required software and test that NFS is working between
the **cxlient** (aka `desktop`) and the **host** (aka Synology NAS):

```bash
# install the required nfs client utilities
sudo apt install nfs-common
```

```bash
# make a mount point for the nas filesystem and set permissions
sudo mkdir -pv /home2/nfs/synology-nas

# mount the nas filesystem on you desktop linux
sudo mount 192.168.1.201:/volume1/NetBackup /home2/nfs/synology-nas

# test if you can see the remote directories contents (must have some files there)
$ sudo ls /home2/nfs/synology-nas/
test-file.txt

$ sudo touch /home2/nfs/synology-nas/test-file-2.txt
$ sudo ls /home2/nfs/synology-nas/
test-file-2.txt  test-file.txt

# unmount the file system
sudo umount /home2/nfs/synology-nas

# if the above doesn't work, unmount the file system via this
# also do a reboot to clean-up any mess from the '--force --lazy'
sudo umount --force --lazy /home2/nfs/synology-nas
sudo reboot
```

If the above is working properly, let make this mounting occure at boot time
so we can schedule regular backups via `cron` (done in a later step).
Places the following code within `/etc/fstab`:

```bash
#                   <file system>                         <mount point>                  <type>    <options>               <dump>  <pass>
# was /dev/nvme0n1p1 during installation - Crucial P3 Plus 500GB PCIe 4.0 3D NAND NVMe M.2 SSD
/dev/disk/by-uuid/0919-A14F                                 /boot/efi                     vfat     defaults                  0       1

# was /dev/nvme0n1p2 during installation - Crucial P3 Plus 500GB PCIe 4.0 3D NAND NVMe M.2 SSD
/dev/disk/by-uuid/711cf65d-d8e2-4b88-8df2-7a2f9380d889      /home2                        ext4     defaults                  0       1

# was /dev/nvme0n1p3 during installation - Crucial P3 Plus 500GB PCIe 4.0 3D NAND NVMe M.2 SSD
/dev/disk/by-uuid/0bd118bd-c18f-4231-9184-29bebc0cbdca      /                             ext4     defaults                  0       1

# was /swap.img during installation
swap.img                                                    none                          swap     sw                        0       0

# was /dev/md0 RAID disk formed from /dev/sda and /dev/sdc during installation - Seagate 1TB HDD (model ST1000DM003)
#/dev/disk/by_uuid/126e8dc9-e13c-440f-bb02-dc266378329f      /home                         ext4    defaults,nofail,discard   0       0   # <-- doesn't seem to work
/dev/md0                                                    /home                         ext4     defaults,nofail,discard   0       0

# was /dev/sdb6 during installation - Samsung Electronics 840 Pro Series 2.5-Inch 128GB SSD
/dev/disk/by-uuid/65e559c7-e595-4ab6-89a1-7b27d071bc3d      /old_computer                 ext4     defaults                  0       1

# mount of rsync/rsnapshot backup site - Synology DS220+ NAS
192.168.1.201:/volume1/NetBackup                            /home2/nfs/synology-nas       nfs      rw,sync                   0       0
```

#### Step 5: Final Check of All Mounts - DONE
Now test if the NFS link to the Synology NAS gets auto-mounted by doing a rebooting.

```bash
# do a reboot
sudo shutdown -r now

# check the filesystem
$ df -h
Filesystem                                Size  Used Avail Use% Mounted on
tmpfs                                     3.2G  2.4M  3.2G   1% /run
efivarfs                                  256K   97K  155K  39% /sys/firmware/efi/efivars
/dev/nvme0n1p3                            211G   19G  181G  10% /
tmpfs                                      16G  203M   16G   2% /dev/shm
tmpfs                                     5.0M   16K  5.0M   1% /run/lock
/dev/nvme0n1p2                            246G   36K  233G   1% /home2
/dev/sdb6                                 109G   41G   63G  40% /old_computer
/dev/nvme0n1p1                            1.1G  6.1M  1.1G   1% /boot/efi
/dev/md0                                  916G  467G  403G  54% /home
192.168.1.201:/volume1/NetBackup          7.0T  128G  6.9T   2% /home2/nfs/synology-nas
tmpfs                                     3.2G   92K  3.2G   1% /run/user/1000

# test if you can see the remote directories contents (must have some files there)
$ sudo ls /home2/nfs/synology-nas/
test-file-2.txt  test-file.txt
```

The above shows NFS is working and the `/home` directory appears to mount as a RAID.
Lets inspect the RAID for its health status:

```bash
# do a reboot
sudo shutdown -r now

# check if the raid has been mounted on /home
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           1.6G  2.0M  1.6G   1% /run
/dev/sda6       109G   14G   90G  14% /
tmpfs           7.8G     0  7.8G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
/dev/md0        916G   28K  870G   1% /home
/dev/sda3       512M  5.3M  507M   2% /boot/efi
tmpfs           1.6G   96K  1.6G   1% /run/user/1001

# check raid configuration and health
$ sudo mdadm --detail /dev/md0
/dev/md0:
           Version : 1.2
     Creation Time : Tue May  3 22:07:00 2022
        Raid Level : raid1
        Array Size : 976630464 (931.39 GiB 1000.07 GB)
     Used Dev Size : 976630464 (931.39 GiB 1000.07 GB)
      Raid Devices : 2
     Total Devices : 2
       Persistence : Superblock is persistent

     Intent Bitmap : Internal

       Update Time : Fri Apr 12 13:12:10 2024
             State : active
    Active Devices : 2
   Working Devices : 2
    Failed Devices : 0
     Spare Devices : 0

Consistency Policy : bitmap

              Name : desktop:0  (local to host desktop)
              UUID : 56ea45a5:da6e9b9b:99224085:1941111a
            Events : 2459477

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8        0        1      active sync   /dev/sda
```

All looks good!

Sources:
* [How to check RAID configuration in Linux](https://www.cyberciti.biz/faq/how-to-check-raid-configuration-in-linux/)
* [How To Set Up an NFS Mount on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-20-04)
* [How to Use NFS to Mount Synology to Linux as a Storage Space?](https://linuxhint.com/nfs-mount-synology-linux/)



---------------



# Restart Rsnapshot Backup Processing - DONE
To get your backup work again,
you should read the document
`/home/jeff/blogging/content/articles/network-backups-via-rsync-and-rsnapshot.md`.

A large fraction of this work is done for you by reclaiming and mounting
the `/home` directory (done in an earlier step)
and using the scripts within `/home/bachup_user/bin`.

In summary, the steps you need to perform, using the documentation above as your guide:

1. You'll need to to install `rsync`, `rsnapshot`, and related software.
2. Make changes to `full-backup.sh` so the `DESTINATION` point to your storage location.
3. Modify the `/etc/rsnapshot.conf` to reflect you implementation of the backup.
4. Do your first backups manually as a test and set the foundation for the `cron` automation.
5. To get automated backups running, update the `crontab` file for the user `backup_user` and restart it.

#### Step 1: Install Required Backup Software - DONE
The installation of required software for backups has been already done early,
but just  in case you missed it:

```bash
# install rsync, grsync, and rsnapshot
sudo apt install rsync grsync rsnapshot
```

#### Step 2: Make Changes to `full-backup.sh` - DONE
The environment variable `DESTINATION` in `/home/backup_user/bin/full-backup.sh`
needs to be changed to `DESTINATION="/home2/nfs/synology-nas/desktop/full-backup/$DIR"`.

#### Step 3: Make Changes to `nsnapshot.conf` - DONE
You need to create a configuration file `/etc/nsnapshot.conf`.
This configuration file should look like this:

```
#################################################
# rsnapshot.conf - rsnapshot configuration file #
#################################################
#                                               #
# PLEASE BE AWARE OF THE FOLLOWING RULE:        #
#                                               #
# This file requires tabs between elements      #
#                                               #
#################################################

#######################
# CONFIG FILE VERSION #
#######################

config_version	1.2


# location where backups will be stored
snapshot_root	/home2/nfs/synology-nas/desktop

# rsync command executed on the remote system
cmd_rsync	/usr/bin/rsync

# incremental backup rules
retain		hourly	6
retain		daily	7
retain		weekly	4
retain		monthly	3

# rsnapshot's log file
logfile	/var/log/rsnapshot.log

# All rsync commands have at least these options set.
rsync_short_args	-aev
rsync_long_args	--delete --numeric-ids --relative --delete-excluded

# ssh args passed
ssh_args	-i /home/backup_user/.ssh/id_rsa

# systems to be backed up, what high level directory name is to be used
# and the additional arguments to pass to rsync
backup	/	desktop/	exclude_file=/home/backup_user/rsync-exclude-desktop
#backup	backup_user@RedRPi:/	RedRPi/	exclude_file=/home/backup_user/rsync-exclude-RPi,+rsync_long_args=--rsync-path=/home/backup_user/bin/rsync-wrapper.sh
#backup	backup_user@BlackRPi:/	BlackRPi/	exclude_file=/home/backup_user/rsync-exclude-RPi,+rsync_long_args=--rsync-path=/home/backup_user/bin/rsync-wrapper.sh
#backup	Sara@SaraPC:/	SaraPC/	exclude_file=/home/backup_user/rsync-exclude-windows,+rsync_long_args=--fake-super
```

>**NOTE:** The configuration file requires tabs between elements
>and all directories require a trailing slash.
>Just open the configuration file using a text editor such as `vim` or `nvim` ... but be careful.
>Many editors are set to convert any tabs entered by the user to spaces.
>This can be a source of great confusion and frustration!

#### Step 4: Perform Some Manual Backups - DONE
To validate that your `rsnapshot` and its configuration files are set-up properly,
execute the commands `sudo /usr/bin/rsnapshot hourly`.
Because its the first instance of making a backup,
its likely to run for several hours, but that is OK.
Its import to run it manually like this since, once its automated via `cron`,
long running backups could overlap in time.

```bash
# execute your first backup manual - this will run a long time (626 GB took 4.5 hours)
sudo /usr/bin/rsnapshot hourly
```

At a later time, take a snapshot of a full backup for you long term records.

```bash
# take a full backup
sudo /home/backup_user/bin/full-backup.sh
```

#### Step 5: Automating (Scheduling) Backups via `crontab` - DONE
Linux [cron][57] is used to schedule commands to be executed periodically.
You can setup commands or scripts, which will be repeatedly run at a set time.

>**NOTE:** The cron service (daemon) runs in the background and constantly checks the `/etc/crontab` file,
>and `/etc/cron.*/` directories.
>It also checks the `/var/spool/cron/` directory.
>Review the article [CronHowTo][58] to see how you can schedule and run tasks
>in the background automatically at regular intervals using `crontab` files.
>Crontab ( **cron** **tab**le ) is a file which contains the schedule of cron entries to be run and at specified times.

How to use `cron`:

* To use `cron` for tasks meant to run only for your user profile,
add entries to your own user's `crontab` file.
To edit the `crontab` file: `crontab -e`. To list `crontab` contents: `crontab -l`.
* Commands that normally run with superuser privileges should be added to the root `crontab`.
To edit the root `crontab` file: `sudo crontab -e`. To list `crontab` contents: `sudo crontab -l`.
* To perform these operation as <user>, do the following: `sudo crontab -u <user> -e` and  `sudo crontab -u <user> -l`.
* you can load the content of a file into `cron` by doing the following: `crontab <file>`

For our application, the `backup_user` account we established is for backup `cron` job.
You can use `sudo crontab -l` to list the contents of crontab.
To update it, use `crontab -e` and enter the following:

```bash
# create a `crontab` for user `backup_user`
sudo crontab -u backup_user -e

# copy the text below into the `crontab`
```

```
# Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
# Version:      1.5.0

# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# Instead of the first five fields, one of eight special strings may be applied:
# string         meaning
# ------         -------
# @reboot        Run once, at startup.
# @yearly        Run once a year, "0 0 1 1 *".
# @annually      (same as @yearly)
# @monthly       Run once a month, "0 0 1 * *".
# @weekly        Run once a week, "0 0 * * 0".
# @daily         Run once a day, "0 0 * * *".
# @midnight      (same as @daily)
# @hourly        Run once an hour, "0 * * * *".
#
# Examples
# @reboot <command> #Runs at boot
# @yearly <command> #Runs once a year [0 0 1 1 *]
#
#
#
# For more information see the manual pages of crontab(5) and cron(8)
#
#     +------------- minutes (0 - 59)
#     |      +----------- hour (0 - 23)
#     |      |          +--------- day of month (1 - 31)
#     |      |          |         +------- month (1 - 12)
#     |      |          |         |         +----- day of week (0 - 6) (Sunday = 0)
#     |      |          |         |         |            +--- command to be executed
#     |      |          |         |         |            |
#     |      |          |         |         |            |
#     m      h         dom       mon       dow
#   minute  hour  day-of-month  month   day-of-week   command
      0     */4         *         *         *         /home/backup_user/bin/rsnapshot-wrapper.sh hourly
     30      2          *         *         *         /home/backup_user/bin/rsnapshot-wrapper.sh daily
     30     10          *         *         6         /home/backup_user/bin/rsnapshot-wrapper.sh weekly
     30     14          1         *         *         /home/backup_user/bin/rsnapshot-wrapper.sh monthly
```

For `crontab` execute of the backup process,
I created a wrapper script and placed it in `/home/backup_user/bin/rsnapshot-wrapper.sh`.

Check on the validity of what you created and restart `cron` to make sure the changes are in effect:

```bash
# validate you work
sudo crontab -u backup_user -l

# also validate here - this is where a user's crontab is stored
sudo cat /var/spool/cron/crontabs/backup_user

# restart cron to make sure the changes you made are put into effect
sudo service cron restart
```

Sources:
* [CronHowTo][58]
* [List Cron Jobs on Linux](https://www.linode.com/docs/guides/how-to-list-cron-jobs/)
* [Cron Vs Anacron: How to Schedule Jobs Using Anacron on Linux](https://www.tecmint.com/cron-vs-anacron-schedule-jobs-using-anacron-on-linux/)
* [Use anacron for a better crontab](https://opensource.com/article/21/2/linux-automation)



---------------



# Get Printer Working - DONE

Sources:
* [Use a Raspberry PI Zero W as a Wireless Print Server](https://community.element14.com/products/raspberry-pi/raspberrypi_projects/b/blog/posts/use-a-raspberry-pi-zero-w-as-a-wireless-print-server)
* [CUPS and Raspberry Pi AirPrinting](https://www.developer.com/mobile/cups-and-raspberry-pi-airprinting/)
* [How to Turn a Printer into a Wireless Printer with Raspberry Pi](https://www.youtube.com/watch?v=hdwqQjDjMzU)
* [Create your own Canon Printer server with Raspberry Pi](https://www.youtube.com/watch?v=3powPeY5_-k)
* [Turn your USB Printer into a Wireless Printer! 2019](https://www.youtube.com/watch?v=4g9vnk28480)
* [Turn USB Printer to WiFi Printer for $15 | Convert Any USB Printer Wireless](https://www.youtube.com/watch?v=P3XRi-CD1a0)

#### Step 1: Install and Configure CUPS on Print Server - DONE
On many Linux  installations,
support for printers via CUPS is pre-configured and is an active service after a freash install.
To check if CUPS is active, use the following command:

```bash
# check the operational status of cups
systemctl status cups
```

If you find CUPS active, then you can go to the next step,
but if not, do teh installation below:

```bash
# install some prerequisite software
sudo apt install -y build-essential git autoconf libtool

# install some of your developer tools

# install cups and its libraries
sudo apt install -y cups libcups2-dev libcupsimage2-dev
```

#### Step 2: Configure CUPS - DONE
Getting a printer working can involve the
editing of the file `/etc/cups/cupsd.conf` and other such manual operations.
The better approach for most any printer you have is to just plugin the printer
into the computer and let CUPS sense it and do it automatic configuration.
That is what I did with my [HP LaserJet P2045][60].
The using the GUI, I went to **Settings** > **Printers** and did any fine tuning
required (but nothing was required).

>**NOTE:** If the print does not automatically sense the printer,
>using the GUI go to  **Settings** > **Printers** > select the **Add Printer...** button.



---------------



# Development Tools: Docker & Portainer - DONE
**Docker** is a popular application that simplifies the process of managing application processes in containers.
Containers let you run your applications in resource-isolated processes.
They’re similar to virtual machines, but containers are more portable,
more resource-friendly, and more dependent on the host operating system.

For applications depending on several services,
orchestrating all the containers to start up, communicate,
and shut down together can quickly become unwieldy.
**Docker Compose** is a tool that allows you to run multi-container
application environments based on definitions set in a YAML file.
It uses service definitions to build fully customizable environments
with multiple containers that can share networks and data volumes.

Adopting container orchestration platforms like Kubernetes can be hard.
**[Portainer][39]** is a popular Docker UI that helps you visualise your
containers, images, volumes and networks.
Portainer helps you centrally configure, manage and secure containerized environments,
regardless of where they are hosted.
It helps you take control of the Docker resources on your machine, avoiding lengthy terminal commands.

>**NOTE:** By default, the docker command can only be run the root user
>or by a user in the docker group, which is automatically created during Docker’s installation process.

Sources:

* [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)
* [Install the Compose plugin](https://docs.docker.com/compose/install/linux/#install-using-the-repository)
* [How to Install Portainer on Ubuntu](https://www.wundertech.net/portainer-on-ubuntu/)
* [Install Portainer CE with Docker on Linux](https://docs.portainer.io/start/install-ce/server/docker/linux)

## Docker Engine & Docker Compose

#### Step 1: Install Docker - DONE
Ubuntu is my go-to Linux OS and installing on Ubuntu is fairly straight-forward.
I'll used the installation scripts below.
This involves adding a new package source,
adding the GPG key from Docker to ensure the downloads are valid,
and then install the Docker package.

While not the absolute latest Docker version,
I’ll install Docker from the Dockers official Ubuntu repository,
instead of Docker's generic repository.

```bash
# before you can install docker engine, you need to uninstall any previous installed conflicting packages
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt remove $pkg; done

# clean up any existing docker related data
rm /var/lib/docker/*

# update your existing list of ubunutu packages
sudo apt update

# install a few prerequisite packages
sudo apt install apt-transport-https ca-certificates curl gnupg software-properties-common

# add docker's official gpg key
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# add the docker repository to apt sources
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

# check to make sure you are about to install from docker repo or ubuntu repo
apt-cache policy docker-ce
```

From the above last command,
you'll see the installation will be from the Docker repository for what ever version of Ubuntu you are running.
Now lets install Docker:

```bash
# install docker packages
sudo apt install docker-ce

# check to see if docker is running
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# docker should be running, but make sure
sudo service docker start

# verify that the docker engine installation is successful running
sudo docker run hello-world
```

#### Step 2: Upgrade Docker - DONE
Docker and Docker Compose will be automatically upgraded by Ubuntu from the official Ubuntu repository for Docker.

#### Step 3: Install Docker Compose - DONE
To ensure we get the latest version,
we’ll install Docker Compose from the official Docker repository.
To do that, we’ll add a new package source,
add the GPG key from Docker to ensure the downloads are valid,
and then install the package.

```bash
# download docker compose
sudo apt update
sudo apt install docker-compose-plugin

# verify that the installation of docker compose was successful
docker compose version
```

#### Step 4: Upgrade Docker Compose - DONE
Docker Compose will be automatically by Ubuntu from the official Ubuntu repository for Docker.

## Portainer
Portainer gives users a way to manage their Docker containers,
accross multiple sites, through a web interface.
Portainer also gives you the ability to use stacks,
which is an easy way to create new containers and allows them to be created using a docker-compose format.

**NOTE:** Instructions below must be performed on Ubuntu 22.04 or greater.

#### Step 1: Install Portainer - DONE
Before you install Portainer on Ubuntu,
you must ensure that you have Docker installed on Ubuntu first.

```bash
# create the volume for storing persistent data
sudo docker volume create portainer_data

# install the portainer container (ports 8000 is for agents and 9000 for web ui)
sudo docker run -d -p 8000:8000 -p 9000:9000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest

# check if portainer is running
sudo docker ps -a -s

# log into portainer and setup your password, etc.
#google-chrome https://localhost:9443   # <-- for https access
google-chrome https://localhost:9000   # <-- for https access
```

Now using your browser, log into portainer via this URL: `localhost:9000`.

#### Step 2: Upgrading Portainer - DONE, NOT
To [upgrade to the latest version of Portainer Server][40],
you must do it from the commandline.
Use the following commands to stop Portainer, then remove the old version,
and finally do a new install of Portainer.

```bash
# stop and remove the portainer container
sudo docker stop portainer
sudo docker rm portainer

# pull down the latest version of portainer
sudo docker pull portainer/portainer-ce:latest

# reinstall portainer
sudo docker run -d -p 8000:8000 -p 9000:9000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```

You may want to also upgrade the Portainer Agent and this must be done separately:

```bash
# stop and remove the portainer agent container
sudo docker stop portainer_agent
sudo docker rm portainer_agent

# pull nd start the updated version of the image
sudo docker pull portainer/agent:latest
sudo docker run -d -p 9001:9001 --name portainer_agent --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /var/lib/docker/volumes:/var/lib/docker/volumes portainer/agent:latest
```

#### Step 3: Refresh Portainer Stacks - DONE
Using your [GitHub repository for your HomeLab Portainer Stacks][61],
redeploy your stacks to you `desktop` computer.



---------------



# 3D Printer Slicer - UltiMaker Cura
[UltiMaker Cura][62] is free, very popular 3D printing software, a slicer, that can be fine-tune 400+ settings.
3D printing slicer software essentially acts as the middleman between the 3D model and printer.

Sources:
* [UltiMaker Cura 5.7.0][62]
* [How to Use Ultimaker Cura 5: A Beginner's Guide 2023][66]

#### Step 1: Install Cura - DONE
The installation method chosen by UltiMaker is the [AppImage][63] method.
Not my favorite install method but [things are getting better][65], and most importantly,
UltiMaker doesn't give you a choose if you want the latest version.
You'll find Ubuntu does maintain a repository for Cura but is way out of date.

You need to install [FUSE 2][64] to make AppImages work in Ubuntu 23.04+.
You do not need to add a PPA or compile anything; the `libfuse2` package is available
in the Ubuntu Universe repo (enabled by default usually).

```bash
# you need to install libfuse2 in ubuntu
sudo apt install libfuse2

# download the AppImage
cd ~/bin
wget https://github.com/Ultimaker/Cura/releases/download/5.7.0/UltiMaker-Cura-5.7.0-linux-X64.AppImage

# make sure the appimage is executable
chmod a+x UltiMaker-Cura-5.7.0-linux-X64.AppImage

# make a more friendly symbolic link to the executable
ln -s UltiMaker-Cura-5.7.0-linux-X64.AppImage cura
```

Now you have to execute Cura for the first time so it can configure itself.
This configuration step will take about a minute so don't prematurely quit this process.

```bash
# configure cura
cura
```

#### Step 2: Configure Cura - DONE
To find your Cura configuration file, select the tab **Help** > **Show Configuration Folder**.
It will display `~/.config/cura/5.7`.
When you install Cura, it should find your old configuration file and use it.
That is what happen whne I installed Cura, so there is nothing to do here.


#### Step 3: Adding a Custom Cura Icon to the Side Bar (aka Desktop Entry Files)
When using AppImage instead of Ubuntu's package management,
the new application will not automatically integrate with the Ubuntu desktop.
So there will not be any Cura Icon in the side bar.

To remedy this, I'm going to manual create one.
I followed the procedure outline in the Sources below.


```bash
# applications desktop configuration is stored here
ls ~/.local/share/applications

# move icon into directory
sudo cp ~/Downloads/logo.png ~/.local/share/applications/cura-logo.png
```

Create your configuration for cura button on the side bar
by placing in the following text in the file `~/.local/share/applications/cura.desktop`:

```bash
#!/usr/bin/env xdg-open

# Guide to Desktop Entry Files in Linux - https://www.baeldung.com/linux/desktop-entry-files
# Creating a Custom Application Launcher in Ubuntu 22 - https://www.dgendill.com/posts/technology/2023-04-23-ubuntu22-custom-shortcuts-appliation-launchers.html
# How to create a desktop shortcut to a website - https://askubuntu.com/questions/1269788/how-to-create-a-desktop-shortcut-to-a-website
# How to create desktop shortcut launcher on Ubuntu 22.04 Jammy Jellyfish Linux - https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-22-04-jammy-jellyfish-linux #How do I create a new application launcher in Ubuntu 22.04?
# How do I create a new application launcher in Ubuntu 22.04? - https://askubuntu.com/questions/1428517/how-do-i-create-a-new-application-launcher-in-ubuntu-22-04
# Fix "Add to Favorites" for custom apps in Ubuntu - https://averagelinuxuser.com/ubuntu_custom_launcher_dock/
# Registering AppImage Files as a desktop app - https://askubuntu.com/questions/902672/registering-appimage-files-as-a-desktop-app

# https://ultimaker.com/software/ultimaker-cura/
[Desktop Entry]
Version=5.7.0
Terminal=false
Type=Application
Name=Cura
Exec=/home/jeff/bin/cura
Icon=/home/jeff/local/share/applications/cura-logo.png
Categories=Application;IDE;
Comment=3D printing software / slicer
```

Now make the file executable:

```bash
# file must be executable
chmod a+x ~/.local/share/applications/cura.desktop
```

Sources:
* [Guide to Desktop Entry Files in Linux](https://www.baeldung.com/linux/desktop-entry-files)
* [Creating a Custom Application Launcher in Ubuntu 22](https://www.dgendill.com/posts/technology/2023-04-23-ubuntu22-custom-shortcuts-appliation-launchers.html)
* [How to create a desktop shortcut to a website](https://askubuntu.com/questions/1269788/how-to-create-a-desktop-shortcut-to-a-website)
* [How to create desktop shortcut launcher on Ubuntu 22.04 Jammy Jellyfish Linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-22-04-jammy-jellyfish-linux)
* [How do I create a new application launcher in Ubuntu 22.04?](https://askubuntu.com/questions/1428517/how-do-i-create-a-new-application-launcher-in-ubuntu-22-04)
* [Fix "Add to Favorites" for custom apps in Ubuntu](https://averagelinuxuser.com/ubuntu_custom_launcher_dock/)
* [Registering AppImage Files as a desktop app](https://askubuntu.com/questions/902672/registering-appimage-files-as-a-desktop-app)
* [Adding a Custom Application to the Side Bar (Ubuntu 20.04)](https://www.youtube.com/watch?app=desktop&v=RUX8OYi81Y8)

#### Step 4: Check Your Print Settings

Sources:

This series if focused on showing you everything you need to know to allow you print perfect prints with your 3D printer using Ulitmaker Cura 5 software.
* [Cura Slicer Tutorials](https://www.youtube.com/playlist?list=PLv65CP2QM2rFHMu6OGJVkwC3ictFhB00n)
* [Ultimaker Cura 5 Tutorials](https://www.youtube.com/playlist?list=PLv65CP2QM2rG0eX2ZhAyA0_A8nbQV9V29)
    * [How to Use Ultimaker Cura 5: A Beginner's Guide 2023][66]
    * [3D Printing Perfection: Fine-Tune Top and Bottom Settings in Ultimaker Cura 5](https://www.youtube.com/watch?v=OygRJrpTNC8)
    * [Getting the Right Flow: Ultimaker Cura 5 Flow Rate Settings](https://www.youtube.com/watch?v=ARsczJrNJb8)
    * [Maximizing Bed Adhesion with Ultimaker Cura’s Skirts, Brims, and Rafts](https://www.youtube.com/watch?v=bruKY-L5eu8)
    * [Cura 5 Quality Settings 101: The Ultimate Guide to Great 3D Prints!](https://www.youtube.com/watch?v=vkItGhXxDGw)
    * [3D Printing Perfection: Things You Must Check Before Every Cura 5 Print](https://www.youtube.com/watch?v=HV5XA0oR9c4)



---------------



# Install


---------------



# Setup Thunderbird



---------------



# Setup Uninterruptible Power Supplies (UPS)
I purchased a [uninterruptible power supply][67],
specifically the [APC Back-UPS NS 1080][68],
to smooth out the power dips that are far too frequent in my home.
I need to get this operational again.

Linux has a software daemon called [`apcupsd`][69] (the name stands for APC UPS Daemon)
that allows the computer to interact with (almost all recent)
[American Power Conversion Corp (APC)][70] UPS'.
During a power failure, `apcupsd` informs users about the loss of utility power
and that a shutdown may occur.
If utility power is not restored,
a system shutdown will follow when the battery is exhausted, a specified timeout expires,
a specified battery charge percentage is reached,
or a specified battery runtime
(based on internal UPS calculations and determined by power consumption rates) expires.
If the utility power is restored before one of the these shutdown conditions is met,
`apcupsd` will inform users of this and the shutdown will generally be cancelled.

[67]:http://en.wikipedia.org/wiki/Uninterruptible_power_supply
[68]:https://www.apc.com/us/en/product/BN1080G/apc-powersaving-backups-pro-ns-1080va/
[69]:http://en.wikipedia.org/wiki/Apcupsd
[70]:http://www.apc.com/
[71]:https://help.ubuntu.com/community/apcupsd
[72]:http://linux.die.net/man/8/chkconfig
[73]:http://www.apcupsd.com/manual/manual.html#apcupsd-status-logging

## UPS Installation
For my UPS,
the  `apcupsd` daemon will be communicating with the UPS via a USB connection.
To make sure that your USB subsystem can see the UPS,
plug in the UPS and connect the USB cable to your computer.
Then just run `lsusb` from a shell prompt (see below, output included):

```bash
# the lsusb command can show you the hubs connected to your system
$ lsusb | grep American
Bus 001 Device 007: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
```

#### Step 1: Install `apcupsd` - DONE
The `apcupsd` daemon is easy to install
and is well documented at "[apcupsd - Official Ubuntu Documentation][71]".
If you want to see the stats of the UPS through the browser,
you can also install `apcupsd-cgi` package.

```bash
# install the apcupsd daemon and browser package
sudo apt install apcupsd apcupsd-cgi
```

Next you edit the `apcupsd` configuration file `/etc/apcupsd/apcupsd.conf`.
Here are the modifications I made to this file:

```bash
# UPS name, max 8 characters
UPSNAME HOME_UPS

# Defines the type of cable connecting the UPS to your computer.
UPSCABLE usb

# Battery date - 8 characters, date battry was installed
BATTDATE <mm/dd/yy>

# the type of UPS you have
UPSTYPE usb

# with a usb type UPS apcupsd can autodetect the device,
# so you should comment out the DEVICE setting
#DEVICE /dev/ttyS0

# UPS should do a self test every two weeks
SELFTEST 336
```

Now you must edit the file `/etc/default/apcupsd`.

```bash
# Defaults for apcupsd initscript

# Apcupsd-devel internal configuration
APCACCESS=/sbin/apcaccess
ISCONFIGURED=yes
```

#### Step 2: Starting Things Up - DONE
To start/stop the `apcupsd` daemon manually, just execute this command:

```bash
# start the apcupsd daemon
sudo /etc/init.d/apcupsd start

# to check if the demon is in fact running
ps aux | grep --invert-match grep | grep apcupsd

# stop the apcupsd daemon
sudo /etc/init.d/apcupsd stop
```

The UPS daemon can be manual started/stopped, but also,
the command `/etc/init.d/apcupsd` is automatically invoked at system startup and shutdown
and is governed by the [`chkconfig`][72] procedures.

To get a snapshot of the UPS's status, run the command `apcaccess status`.

See the output below:

```bash
# UPS status check
$ sudo apcaccess status

APC      : 001,017,0422
DATE     : 2024-04-26 12:50:06 -0400
HOSTNAME : desktop
VERSION  : 3.14.14 (31 May 2016) debian
CABLE    : USB Cable
DRIVER   : USB UPS Driver
UPSMODE  : Stand Alone
STARTTIME: 2024-04-26 12:36:43 -0400
STATUS   : COMMLOST
MBATTCHG : 5 Percent
MINTIMEL : 3 Minutes
MAXTIME  : 0 Seconds
NUMXFERS : 0
TONBATT  : 0 Seconds
CUMONBATT: 0 Seconds
XOFFBATT : N/A
STATFLAG : 0x05000100
END APC  : 2024-04-26 12:57:46 -0400
```

This shows that the UPS daemon is configured to do the following thing:

| Parameter | Value | Description |
|:----------------- |:--------------:|:--------------- |
| MBATTCHG | 5% | If the battery charge percentage (BCHARGE) drops below this value, apcupsd will shutdown your system. Value is set in the configuration file (BATTERYLEVEL). |
| MINTIMEL | 3 Min | apcupsd will shutdown your system if the remaining runtime equals or is below this point.  Value is set in the configuration file (MINUTES). |
| MAXTIME  | 0 Sec | apcupsd will shutdown your system if the time on batteries exceeds this value.  A value of zero disables the feature. Value is set in the configuration file (TIMEOUT). |

These parameters say something about how the UPS is perfroming
(see [apcupsd Status Logging][73] section in the apcupsd User Manual):

| Parameter | Value | Description |
|:----------------- |:--------------:|:--------------- |
| STARTTIME | time stamp | The time/date that `apcupsd` was started (ex. 2015-02-07 10:59:39 -0500). |
| STATUS   | ONLINE | The current status of the UPS (ONLINE, ONBATT, etc.) |
| LINEV    | 121.0 V | The current line voltage as returned by the UPS. |
| LOADPCT  |  20.0% | The percentage of load capacity as estimated by the UPS. |
| BCHARGE  | 100.0% | The percentage charge on the batteries. |
| TIMELEFT |  36.1 | The remaining runtime left, in minutes on batteries as estimated by the UPS. |
| LOTRANS  | 088.0 V | The line voltage below which the UPS will switch to batteries. |
| HITRANS  | 142.0 V | The line voltage above which the UPS will switch to batteries. |
| SELFTEST | NO | The results of the last self test, and may have the following values: OK - self test indicates good battery, BT - self test failed due to insufficient battery capacity, NG - self test failed due to overload, NO - No results (i.e. no self test performed in the last 5 minutes) |



---------------



# MyMedia - Music Streaming to Echo
I like to play music from my computer library stream it to my Amazon Echo (aka Alexa).
To do this, I choose to use [My Media for Alexa][20].
It cost only $5.50/year, and [My Media Alexa Skill](https://www.amazon.com/bizmodeller-My-Media/dp/B06XPP135L)
Installation instructions are in [video][34] on the [myMedia homepage][33].

You have two methods of doing an install of MyMedia:
Docker and Ubuntu package manager.
My preferred method is via Docker.
You find the install methodology documented [here][42]
and the specific instructions for my installation can be found here:
`~/src/docker-containers/mymeda`.

# Plex - Music Streaming to Echo
See `/home/jeff/blogging/content/ideas/desktop-fresh-install-of-ubuntu.md`.



---------------



# Apache Web Server - Infrastructure to Support WebPages - DONE, NOT
The Apache HTTP server is the most widely-used web server in the world.
There are a variety of reasons may choose to install the Apache Web Server.
You can use it for testing HTTP server for testing,
or host your own blog or wiki using static web pages, as I plan to do.

#### Step 1: Installing Apache - DONE, NOT
```bash
# installing apache
sudo apt update
sudo apt install apache2

# check if the apache service is running
sudo systemctl status apache2

# check if apache renders a webpage
google-chrome http://localhost:80

# try each ip address list to see if you render a webpage
$ hostname -I
192.168.1.200 192.168.1.27 172.20.0.1 172.17.0.1 172.18.0.1
```

#### Step X: Adjust the Firewall - DONE, NOT
Before using Apache as an external facing webserver,
it’s necessary to modify the firewall settings to allow outside access to the default web ports.
If you followed the installation process above,
you should have a UFW firewall configured to restrict access to your server.

During installation, Apache registers itself with UFW to provide a few application profiles
that can be used to enable or disable access to Apache through the firewall.
List the `ufw` application profiles by running the following:

```bash
# list the ufw application profiles
$ sudo ufw app list
Available applications:
  Apache
  Apache Full
  Apache Secure
  CUPS
```

There are three profiles available for Apache:

* **Apache:** This profile opens only port 80 (normal, unencrypted web traffic)
* **Apache Full:** This profile opens both port 80 (normal, unencrypted web traffic) and port 443 (TLS/SSL encrypted traffic)
* **Apache Secure:** This profile opens only port 443 (TLS/SSL encrypted traffic)

```bash
# verify the ufw status
# if never used, it should be inactive
# inactive = ufw is turned off and currently not enforcing any rules
$ sudo ufw status
Status: inactive

# establish your profile
$ sudo ufw allow 'Apache'
Rules updated
Rules updated (v6)

# activate ufw
$ sudo ufw enable
Firewall is active and enabled on system startup

# verify the change by checking the status
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
Apache                     ALLOW       Anywhere
Apache (v6)                ALLOW       Anywhere (v6)
```

#### Step X: Setting Up Virtual Hosts - DONE, NOT
Apache can run multiple websites on a single server,
each of which can be customized and configured independently.
The basic unit that describes a site or a domain is called a virtual host.
This allows the administrator to use one server to host multiple domains or sites
with a single interface or IP address by using a mechanism.

https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-22-04
https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-16-04

Source:
* [How To Install the Apache Web Server on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-22-04)
* [How To Set Up Apache Virtual Hosts on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-16-04)



---------------



# Establish Synology Backup Processing
I'm using a Synology small office NAS to perfrom hourly backup of my Linux desktop system.
Its a 2-bay [DiskStation DS220+][38] and much of its operation is not impacted by my
refresh of the Ubuntu OS.

What does have to be done is the reastablishment of my rsync/rsnapshot tools & process.
I was using a USB attached drive in the past but now moving to the Synology NAS as a shared drive.
I'm not using Active Backup for Business since its not currently supported on my version of Ubuntu.

Sources:
* /home/jeff/blogging/content/articles/network-backups-via-rsync-and-rsnapshot.md
* /home/jeff/src/synology-nas/backup-tool/README.md
* [How I configured my Synology NAS and Linux to use rsync for backups](https://obsolete29.com/posts/2022/04/30/how-i-configured-my-synology-nas-and-linux-to-use-rsync-for-backups/)
* [How do I back up data from a Linux device to my Synology NAS via rsync?](https://kb.synology.com/en-global/DSM/tutorial/How_to_back_up_Linux_computer_to_Synology_NAS)
* [Backup a Linux PC to a Synology NAS using Rsync!](https://www.wundertech.net/how-to-backup-a-linux-pc-to-a-synology-nas-using-rsync/)
* [How to Use rsync on Synology NAS](https://linuxhint.com/use-rsync-synology-nas/)
* [Backup and Restore Your Linux System with rsync](https://averagelinuxuser.com/backup-and-restore-your-linux-system-with-rsync/)

#### Step 1: Install Required Software - DONE
Rsync should already be installed on most Linux system.
You can install it, and the [grsync][04] & [rsnapshot][08] tools, using this command:

```bash
# install rsync, grsync, and rsnapshot
sudo apt install rsync grsync rsnapshot
```

For the backup process, I need to move files from the **client** (`desktop`) to the **host** (Synology NAS).
I can do this via the [Network File System (NFS)][EE] or SMB
(call [Samba][FF] on Linux and is a free software re-implementation of the [SMB networking protocol][GG]).
The article "[NFS vs SAMBA vs CIFS][HH]" and "[NFS vs SMB – Which one to choose?][II]" pointed me to NFS as my solution.
First, make sure NFS is activated on the Synology NAS (procedures outlined [here][JJ]),
but you also need a NFS client on the source.

The NFS Client is my Ubuntu desktop Linux box,
and I configured it with these commands:

```bash
# install the required nfs client utilities
sudo apt install nfs-common
```

We'll configure the NFS envirnment and our backup tools in a later step.

[EE]:https://www.atera.com/blog/what-is-nfs-understanding-the-network-file-system/
[FF]:https://en.wikipedia.org/wiki/Samba_(software)
[GG]:https://en.wikipedia.org/wiki/Server_Message_Block
[HH]:https://linuxconfig.org/nfs-vs-samba-vs-cifs
[II]:https://bobcares.com/blog/nfs-vs-smb/
[JJ]:https://linuxhint.com/nfs-mount-synology-linux/

#### Step 1: Create Backup User and Validate - DONE
On the Linux desktop, you need to assure there is a `backup_user` login,
with a UID of less that 500,
which will run the rsync / rsnapshot utilities
and have `ssh` authentication keys.

>**NOTE:** I choose a UID of 400 so that the `backup_user`
>would not appear on the Ubuntu/Debian login screen list.
>To hide a user from the Ubuntu/Debian login screen list,
>you should be able to add the name to the hidden-users
>list in the file `/etc/lightdm/users.conf`, but there is a [problem][45].
>The is an alternative, and that is to choose a UID value less than 500
>(See the "minimum-uid" in `/etc/lightdm/users.conf`).

```bash
# validate that the backup_user home directory still exist, contains scripts, and has user ID of 400
ls -la /home/backup_user

# validate that backup_user login doesn't currently exist
cat /etc/passwd | grep backup_user
```

#### Step 2: Create Backup User - DONE
On the Linux desktop, you need to assure there is a `backup_user` login,
that login has a UID of 400, and it has the approprate SSH keys and filesystem access.
The `backup_user` is not root, and therefore, the utilities it uses for backups
(`rsync` and `rsnapshot`)
can't freely move through the whole directory system, write files, and such.
Using the [`visudo`][43] command,
we'll need to edit the [`/etc/sudoers`][44] file by adding the approprate line items.

Lets first create the `backup_user` account on `desktop`:

```bash
# create the backup_user account
$ sudo adduser backup_user -u 400
[sudo] password for jeff:
info: Adding user 'backup_user' ...
info: Adding new group 'backup_user' (400) ...
info: Adding new user 'backup_user' (400) with group `backup_user (400)' ...
useradd warning: backup_user's uid 400 outside of the UID_MIN 1000 and UID_MAX 60000 range.
warn: The home directory '/home/backup_user' already exists.  Not touching this directory.
warn: Warning: The home directory '/home/backup_user' does not belong to the user you are currently creating.
New password:
Retype new password:
passwd: password updated successfully
Changing the user information for backup_user
Enter the new value, or press ENTER for the default
	Full Name []: backup_user
	Room Number []:
	Work Phone []:
	Home Phone []:
	Other []:
Is the information correct? [Y/n] Y
info: Adding new user 'backup_user' to supplemental / extra groups 'users' ...
info: Adding user 'backup_user' to group 'users' ...

# make sure everything has the proper owenrship
sudo chown backup_user:backup_user /home/backup_user
sudo chown backup_user:backup_user /home/backup_user/*
sudo chown backup_user:backup_user /home/backup_user/.*

# if a public ssh key doesn't already exist, create one
sudo su backup_user
cd ~
ssh-keygen -N "" -f ~/.ssh/id_rsa
exit
```

#### Step 3: Add backup_user to sudo List - DONE
The `backup_user` is not root, and therefore, the utilities it uses for backups
(`rsync` and `rsnapshot`)
can't freely move through the whole directory system , write files, and such.
Using the [`visudo`][43] command,
edit the [`/etc/sudoers`][44] file by adding the apropriate
to the bottom of the file.

A [better approach][50] is to put be to put the access rules for the backup_user account in a single file.
In this case, put the rules below in a file call `backup_user` in a directory `/etc/sudoers.d/`.

```bash
# create the target file and exit
sudo vi /etc/sudoers.d/backup_user

# add the following - allows this user to not need a password to sudo the specified command(s)
backup_user    ALL=NOPASSWD:    /usr/bin/rsync
backup_user    ALL=NOPASSWD:    /usr/bin/rsnapshot

# make sure root owns this file
$ ls -l /etc/sudoers.d/backup_user
-rw-r--r-- 1 root root 186 Apr 10 21:44 /etc/sudoers.d/backup_user
```

>**NOTE:** Why is there this `/etc/sudoers.d/` directory?
>Changes made to files in `/etc/sudoers.d/` remain in place if you upgrade the system.
>This can prevent user lockouts when the system is upgraded.
>Ubuntu/Debian tends to like this behavior.
>Other distributions are using this layout as well.

#### Step 4: Increased Security of backup_user Account - DONE
The final step is to lock all this down.
To increase the security of the overall scheme,
on the remote systems and on the local system,
remove the user password from the `backup_user`
and set the shell to a NOOP command.

```bash
# increase security by deleting password and remove login shell
sudo passwd --delete backup_user
sudo usermod -s /bin/false backup_user
```



---------------



# Fix Desktop Environment

#### Step 1: Re-Establish Desktop Layout - DONE
Install GNOME Extensions, GNOME Tweaks tool, and other such things using the following commands:

```bash
# gnome extension - gnome shell integration
# first, go to here - https://chrome.google.com/webstore/detail/gnome-shell-integration/gphhapmejobijbbhgpjhcjognlahblep
sudo apt install chrome-gnome-shell
sudo apt install gnome-shell-extensions

# install gnome tweaks tool
sudo apt install gnome-tweaks
```

Now go to **Activities** (top left of desktop) and install
`Extentions` and `Tweaks` application and pin them to your menu.
You can use this utility to change the Themes and other settings.

Open Extensions, find **Desktop Icons NG (DING)** and turn it off.
This will remove the folders on your desktop.

Sources:
* [Customize the Ubuntu Dock with dconf-editor](https://www.youtube.com/watch?v=uiAtZiYZao8)
* [Gnome Tweaks 40 No Longer Manage Extensions, Use This Tool Instead](https://ubuntuhandbook.org/index.php/2021/05/gnome-tweaks-40-no-longer-manage-extensions/)
* [How to Use GNOME Shell Extensions](https://itsfoss.com/gnome-shell-extensions/)

#### Step 2: Disable Auto-Suspend in Linux - DONE
I'm using a based `rsnapshot` script in `cron` to schedule frequent backups of my filesystem.
These backups take place every 4 hours (12am, 4am, 8am, 12pm, 4pm, 8pm)
with daily, weekly, and monthly summarizations of those backups taking place at diferent point of the day
The challege I'm having is my computer will go into a suspend state when its not use for some time period.

The easiest ways to disable auto-suspend on your computer is via the GUI Settings.
In Ubuntu, and similar distributions, you just navigating to **Settings** > **Power**.
Click on **Automatic Suspend** and toggle the two setting options so that your computer
does not automatically suspend when on battery power or plugged in.

Sources:
* [How to Disable Auto-Suspend in Linux](https://www.makeuseof.com/disable-auto-suspend-in-linux/)

#### Step 3: Get Conky Working - DONE
Conky is a light-weight system monitor for X Window that displays any information on your desktop.
It is highly configurable as it is able to monitor literally any aspect of your system
from hard-drive temperature through number of users logged in to currently played music song.

```bash
# install conky
sudo apt install conky-all

# hardware monitoring tools to check temperature
sudo apt install lm-sensors

# install your version of the .conkyrc file (along with all your other dotfiles)
git clone https://github.com/jeffskinnerbox/.dotfiles.git

# launch conky using test resource file
conky -c ~/.dotfiles/pkg-conky/src/conky-test

# to test, launch conky using your $HOME directory conky resource file
conky
```

The `lm-sensors` package taps into the tempature sensors within CPUs, GPUs, SSDs, and some cards.
Here is a listing of what the command `sensors` can provide:

```bash
# list tempature sensor
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +29.0°C  (high = +80.0°C, crit = +100.0°C)
Core 0:        +25.0°C  (high = +80.0°C, crit = +100.0°C)
Core 4:        +24.0°C  (high = +80.0°C, crit = +100.0°C)
Core 8:        +26.0°C  (high = +80.0°C, crit = +100.0°C)
Core 12:       +25.0°C  (high = +80.0°C, crit = +100.0°C)
Core 16:       +25.0°C  (high = +80.0°C, crit = +100.0°C)
Core 20:       +25.0°C  (high = +80.0°C, crit = +100.0°C)
Core 28:       +24.0°C  (high = +80.0°C, crit = +100.0°C)
Core 29:       +24.0°C  (high = +80.0°C, crit = +100.0°C)
Core 30:       +24.0°C  (high = +80.0°C, crit = +100.0°C)
Core 31:       +24.0°C  (high = +80.0°C, crit = +100.0°C)

acpitz-acpi-0
Adapter: ACPI interface
temp1:        +27.8°C  (crit = +105.0°C)

nouveau-pci-0100
Adapter: PCI adapter
GPU core:    900.00 mV (min =  +0.85 V, max =  +1.00 V)
temp1:        +40.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

nvme-pci-0200
Adapter: PCI adapter
Composite:    +34.9°C  (low  =  -0.1°C, high = +84.8°C)
                       (crit = +94.8°C)
Sensor 1:     +34.9°C  (low  = -273.1°C, high = +65261.8°C)
Sensor 2:     +44.9°C  (low  = -273.1°C, high = +65261.8°C)
Sensor 8:     +34.9°C  (low  = -273.1°C, high = +65261.8°C)
```

By default, Conky monitors the `eth0` & `wlan0` network interface,
but there’s a good chance that your network interface uses a different name.
Obtain your network interface name and then replace the `eth0` & `wlan0` values.
You can get your network interface via this command:

```bash
# list network interfaces that are up & working
$ ip address | grep '^[0-9]' | grep 'state UP' | grep 'qlen'
2: enp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
3: wlx94dbc95110ca: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
```

I also added the parameter `xinerama_head = 1` to the `.conkyrc` file
so that when using a multi-display setup, Conky appears in my desired screen.
Make updates to the `~/.conkyrc` file as required.
You need to add:

```
xinerama_head = 1,  -- for multi-display, select the display to post conky (index starts at 0)
```

You'll want to have start Conky when you login into your account.
You could start it via **Activities** > **Startup Applications**
and edit this to include

```bash
# conky startup script
conky --pause=5 --config=/home/jeff/.conkyrc
```
Make sure to comment out any conky related items in the `$HOME/.xsessionrc` file
to avoid multiple instances of Conky.

Sources:

* [Ubuntu 20.04 System Monitoring with Conky widgets](https://linuxconfig.org/ubuntu-20-04-system-monitoring-with-conky-widgets)
* [How to Configure the Conky System Monitor](http://mylinuxramblings.wordpress.com/2010/03/23/how-to-configure-the-conky-system-monitor/)
* [How To: Configuring Conky](http://lusule.wordpress.com/2008/08/07/how-to-4/)

#### Step 4: Downloading Video Files - DONE
If your interested in capturing a YouTube video,
there is a very easy approach give in this video: [How to Download youtube videos on Ubuntu linux][14].
Unfortunately, appears YouTube has caught on, and this no longer works.

There is a commandline alternate, `youtube-dl`, documented here:
[Youtube-dl: Perfect tool for downloading YouTube videos in Ubuntu][15] and
[Install YouTube-DL – A Command Line Video Download Tool for Linux][16].
You can find the source and a complete listing of
[`youtube-dl` command line options on Github][17].

Despite its name, `youtube-dl` claims to download videos from not only YouTube.com
but Google Video, Photobucket, Facebook, Yahoo, and many more similar sites.
`youtube-dl` also allows to choose specific available video quality format to download
(or let the program itself automatically download higher quality video)
download user specified list, and much more.

**Note** that `youtube-dl` is a Python script.
I'm using Miniconda for my Python envirnment and
you must activate the `base` envirnment, if not already done via your shell.

To install it, do the following:

```bash
# work within miniconda envirnment
conda activate base

# install with the Python 3 pip package which is used to upgrade youtube-dl
pip3 install --upgrade youtube-dl

# youtube-dl sometimes makes use of ffmpeg
sudo apt install ffmpeg
```

When the time comes to upgrade Youtube-dl use:
`pip3 install --upgrade youtube-dl`.

>**NOTE:** `*.mp4` happens to be the default file output format for `youtube-dl`.

>**NOTE:** There is a alternative to `youtube-dl` called [`yt-dlp`][49].
>`yt-dlp` is a feature-rich command-line audio/video downloader with support for thousands of sites.
>Check out ["How to Use YT-DLP: The Complete Guide (2024)"][48].

#### Step 5: Install VLC Media Player - DONE
The default video media player on Ubuntu appears to be poor.
Lets replace with a better tool, the [VLC media player][08].

```bash
# vlc media player for ubuntu
sudo snap install vlc
```

Next, let make VLC the default video play.
You can do this by opening the **Settings** app,
selecting **Default Applications** and update the **Video** menu.

>**NOTE:** Alternatively, you could make VLC the default video play for `*.mp4` files.
>Right click any `*.mp4` video file, choose **Properties**.
>Choose **Open With** and there you can select **VLC media player**
>and the option **Set as default** (bottom right).

#### Step 6: Play Sound Initiated by Login - DONE
My experiance with computers dates back to well before the use of
[broadband connections][73], before the Internet, to [Arpanet][71].
I remember well the sound of a successful login with a [dialup modem][72].
I want to hear that sound again here when I login.

1. Click on the **Activity** button at the top-left of the dispaly
2. Type in the **Search** field **Startup Applications** and select the popup botton-box
3. Edit **Play a Sound** and include the following command **`paplay /home/jeff/Sound/dialup-modem-handshake.ogg`**.

You need to make sure the utility `paplay` is installed.
Do the following:

```bash
# install paplay
sudo apt install pulseaudio-utils

# test paplay
paplay /home/jeff/Sound/dialup-modem-handshake.ogg
```

Sources:
* [The sound of the dialup, pictured](https://www.windytan.com/2012/11/the-sound-of-dialup-pictured.html)
* [How to make application run at Startup in Ubuntu?](https://byteshiva.medium.com/how-to-make-application-run-at-startup-in-ubuntu-6fca4a459bc8)



---------------



# Development Tools: VirtualBox
I chose to installing VirtualBox from Oracle’s package repositories and
used the website "[How to Install VirtualBox on Ubuntu][22]" as my guide.

#### Step 1: Install VirtualBox
Often the default Ubuntu repositories do not have the latest versions of the software,
so instead, you chose to install from Oracle’s package repositories.
Unfortunately, Virtualbox doesn't support Ubuntu 22.04 at this time and my efforts
to _gerrymander_ it did not work.
So instead, I'll install VirtualBox is by using the official Ubuntu repositories.

```bash
# install virtualbox
sudo apt-get update
sudo apt-get install virtualbox-qt

# what is the virtualbox version
$ VBoxManage -version
6.1.32_Ubuntur149290
```

#### Step 2: Install VirtualBox Extension Pack
Now we'll install the VirtualBox Extension Pack.
It adds additional tools like USB 2.0 and 3.0, Remote Desktop, and encryption.
Make sure to use the latest version from the [Oracle website][23].

```bash
# install the virtualbox extension pack
sudo apt-get install virtualbox-ext-pack
```


---------------



# Development Tools: Vagrant

#### Step 1: Install Vagrant
At the time of writing this post,
the latest stable version of Vagrant is version 2.2.18.
You can check the [Vagrant Download page][24] to see if a newer version is available to use instead.

```bash
# download and install gpg keys for vagrant repository
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -

# add the vagrant repository
sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"

# update ubuntu package index and install vagrant
sudo apt-get update && sudo apt-get install vagrant

# what is the vagrant version
$ vagrant --version
Vagrant 2.2.19
```

#### Step 2: Installing Vagrant's VirtualBox Guest Addition
Along with the Vagrant install,
it is essentially to installed and keep updated the Guest Addition package.
Keeping the tools update is problematic enough,
but then you realize not all boxes available from the official repository even have Guest Additions installed.
Luckily, there is a plugin that can manage installing and updating the tools automatically.

```bash
# install guest addition plugin
$ vagrant plugin install vagrant-vbguest
Installing the 'vagrant-vbguest' plugin. This can take a few minutes...
Vagrant failed to properly resolve required dependencies. These
errors can commonly be caused by misconfigured plugin installations
or transient network issues. The reported error is:

Unable to resolve dependency: user requested 'vagrant-hostsupdater (= 1.1.1.160)'

# you are likely to get an error and this should clear that problem
$ vagrant plugin update vagrant-hostupdater
Updating plugins: vagrant-hostupdater. This may take a few minutes...
Successfully uninstalled vagrant-libvirt-0.8.2
Updated 'vagrant-hostsupdater' to version '1.2.4'!
Updated 'vagrant-scp' to version '0.5.9'!
```

#### Step 3: Future Vagrant Upgrades
In the future, as you upgrade vagrant,
the guest additions will fall out of synch.
Use these commands to update the vagrant.

```bash
# to update your plugins after a vagrant upgrade
vagrant plugin update vagrant-vbguest

# to repair your plugins if broken
vagrant plugin repair vagrant-vbguest
```


---------------



# Development Tools: Arduino
For someone like myself, who is at home with Linux as my OS and Vim as my editor,
using the [Arduino IDE][74] for Arduino coding is a step back into the stone age.
If you are used to doing these things yourself and controlling the organization of your code
then the Arduino IDE does some really arbitrary and annoying things.

What follows is how I installed the [Arduino IDE][74], the [Arduino CLI][75]
and used it with [GNU Make (aka Makefile)][76].
Doing this, I can create an all command line (or nearly all)
software development experance while still leveraging the popularity of the Arduino IDE platform.

[74]:https://www.arduino.cc/en/main/software
[75]:https://github.com/arduino/arduino-cli
[76]:https://www.gnu.org/software/make/

#### Step 1: Uninstall Old Arduino IDE - DONE
If you upgrading your Arduino IDE,
the first thing you want to do is uninstall the old version.
The Arduino IDE package comes with an uninstall script but it doesn't do a complete removal
of all the configuration files and modifications you have likely make over time.
You'll need to save and then reinstall those things you have added.
The procedure below should do the trick.

Copy any of your sketch and personal libraries you may wish to keep.
Don't worry about public libraries since they can be reinstalled from sources.

Sources
* [Uninstall Arduino IDE](https://support.arduino.cc/hc/en-us/articles/360021325733-Uninstall-Arduino-IDE)

```bash
# to find the path to the arduino ide
$ whereis arduino
arduino: /home/jeff/bin/arduino

# copy your executable
cp -r ~/bin/arduino ~/tmp/arduino

# remove the arduino ide confguration files
trash ~/.arduinoIDE

# remove any appimage you have for arduino ide
trash -r -f ~/bin/arduino-ide*.AppImage

# remove the cli version of arduino
trash ~/bin/arduino-cli ~/bin/arduino
```

#### Step 2: Installing Arduino IDE - DONE
You could install the Arduino IDE via the Ubuntu Software Center and search for Arduino,
but likely to be an older Arduino IDE version.
Alternatively, you can install as an AppImage file.
The newest version of the Arduino can be downloaded from the [Arduino download page][74].
(**NOTE:** Using this method Arduino software won't automatically be updated,
so you should check Arduino website every few months and download
a new version if one is available.)

```bash
# download the software - arduino-ide_2.3.2_Linux_64bit.zip
# from https://www.arduino.cc/en/software

# download the appimage file
cd ~/bin
wget https://downloads.arduino.cc/arduino-ide/arduino-ide_2.3.2_Linux_64bit.AppImage
```

Before we can launch the Arduino IDE,
we need to first make it an executable file.
This is done by:

* right-click the file,
* choose **Properties**,
* select **Permissions** tab,
* tick the **Allow executing file as program** box.

Now make it executable from your `bin`:

```bash
# make the appimage executable
cd ~/bin
chmod ug+x arduino-*.AppImage

# make it executable as 'arduino'
ln -s /home/jeff/bin/arduino-ide_2.3.2_Linux_64bit.AppImage /home/jeff/bin/arduino
```

Source:
* [Downloading and installing the Arduino IDE 2.0](https://docs.arduino.cc/software/ide-v2/tutorials/getting-started/ide-v2-downloading-and-installing)

#### Step 3: Quick Test - DONE
Lets do a quick check on the install:

```bash
# execute arduino ide
cd ~
arduino

# or
arduino &>/dev/null &
```

This will also create the directories `$HOME/Arduino` to hold your sketchbook
and the directories `$HOME/.arduino15` and  `$HOME/.arduinoIDE`

When the Arduino Software IDE is properly installed you can execute
the IDE via the command `arduino &>/dev/null &` or the desktop icon.

>**NOTE:** It might happen that when you upload a sketch
>(after you have selected your board and serial port),
>you get an error Error opening serial port.
>If you get this error, you need to [set serial port permission][75].

#### Step 4: Setup Your Arduino IDE Preferences - DONE
Normally, running the `arduino` command starts the IDE,
optionally loading any `.ino` files specified on the commandline.
Also, it normally puts all your Arduino sketches and project libraries within
a common directory defaulting to `$HOME/Arduino`.
Lets change this location:

1. Create the directory `$HOME/src/arduino/sketchbooks`
2. Start the Arduino IDE, select the menu button **File** > **Preferences**
3. Change the "Sketchbook location" to `$HOME/src/arduino/sketchbooks`
(make sure you do this via the **Browse** button) and save it.
4. Restart the Arduino and the directory will be prepared automatically for you

>**NOTE:** Some preferences, but not all,
>can be controlled from the Preferences dialog within the Arduino environment (see [here][76]).
>More preferences can be edited directly in the file `$HOME/.arduino15/preferences.txt`
>but only edit when the Arduino IDE is **not** running.

#### Step 5: Remove Old Sketch Directory - DONE
When you create your fist sketch,
the new `sketchbook` directory create above will have a subdirectory `libraries`.
`$HOME/src/arduino/sketchbooks/libraries` is where all your libraries will go
(both downloads and personal ones you create).
Now that your sketches and libraries have a new location,
make sure to remove the default location created during the Arduino IDE install:

```bash
# remove the old sketchbook location
rm -r -f ~/Arduino
```

>**NOTE:** Improperly installing libraries can be a major source of confusion within the Arduino world.
>Check out Adafruit's "[All About Arduino Libraries][18]" for their proper care and feeding.

#### Step 6: Move Back Saved Sketches - DONE
If you you saved any sketch from a previous install,
you can simply copy them into the `$HOME/src/arduino/sketchbooks` directory.
For example:

```bash
# copy your old sketches into you new sketchbook
cp -r ~/tmp/sketchbooks ~/src/arduino
```




---------------



# Development Tools: Ansible
One of the beauties of Ansible is that it will not add a database,
and there will be no daemons to start or keep running.
You only need to install it on one machine
and it can manage an entire fleet of remote machines from that central point.
It does not leave software installed or running on them,
so there’s no real question about how to upgrade Ansible when moving to a new version.

There are multiple ways for you can install Ansible on your system.
You can install Ansible via a Linux PPA (Personal Package Archives)
(see  the **NOTE** below or "[How To Install and Configure Ansible on Ubuntu 22.04][36]")
or via a Pyhton's `pip` package management system (as done will be done here).

Some good videos for learning Ansible can be found [here][37].

#### Step 1: Installing Ansible
I'm using the preferred method of Python Package Manager (`pip`)
since it installs the most current version of Ansible:

```bash
# check if you have ansible installed and its version (you should have at least 2.10)
$ ansible --version
ansible 2.9.6
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/home/jeff/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  executable location = /usr/bin/ansible
  python version = 3.8.10 (default, Jun  2 2021, 10:49:15) [GCC 9.4.0]

# remove the old version of ansible
sudo apt remove ansible

# install ansible via pip
#python3 -m pip install ansible
pip install ansible

# test the ansible installation
$ ansible --version
ansible [core 2.12.5]
  config file = None
  configured module search path = ['/home/jeff/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /home/jeff/.local/lib/python3.10/site-packages/ansible
  ansible collection location = /home/jeff/.ansible/collections:/usr/share/ansible/collections
  executable location = /home/jeff/.local/bin/ansible
  python version = 3.10.4 (main, Apr  2 2022, 09:04:19) [GCC 11.2.0]
  jinja version = 3.1.2
  libyaml = True
```

If you wish to upgrade Ansible,
then you use this command:

```bash
# upgrade ansible to the latest version
#python3 -m pip install --upgrade ansible
pip install --upgrade ansible
```

To remove a `pip` installed Ansible, use this command:

```bash
# remove ansible
#python3 -m pip uninstall ansible
pip uninstall ansible
```

>**NOTE:** If you prefer PPA installation of Ansible on your system,
>run the following commands:
>
>```bash
># update and install prerequisites
>sudo apt-get update
>sudo apt-get upgrade
>sudo apt-get install software-properties-common
>
># add ansible official repository to your system’s software source and install ansible
>sudo apt-add-repository -y ppa:ansible/ansible
>sudo apt-get update
>sudo apt-get install -y ansible
>
># test the ansible installation
>$ ansible --version
>ansible 2.6.1
>  config file = /etc/ansible/ansible.cfg
>  configured module search path = [u'/home/jeff/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
>  ansible python module location = /usr/lib/python2.7/dist-packages/ansible
>  executable location = /usr/bin/ansible
>  python version = 2.7.14 (default, Sep 23 2017, 22:06:14) [GCC 7.2.0]
>```

#### Step 2: Install Docker Extension
To manage Docker containers on remote machines,
you need to install the Docker Ansible-Galaxy extension for Ansible:

```bash
# install the docker extension for ansible
ansible-galaxy collection install community.docker

# check to see if it is installed
$ ls ~/.ansible/collections/ansible_collections/community
```

#### Step 3: Set Your Ansible Path
Now configure your environmental variable `ANSIBLE_ROLES_PATH`.
This path is where Ansible Galaxy will save every role you install
and where Ansible will look when resolving the imports from your playbook.
The default path is `$HOME/.ansible`.
Make sure that the user installing the roles has write permissions on the directory.

I put put the following in my `.bashrc` file:

```bash
# setup for ansible environment
#export ANSIBLE_ROLES_PATH="$HOME/src/ansible-roles"

# using default path ANSIBLE_ROLES_PATH="$HOME/.ansible"
```

#### Step 4: Installing Vim Plugin for Ansible
The Vim plugin, `ansible-vim` is a syntax plugin for Ansible 2.x,
it supports YAML playbooks, Jinja2 templates, and Ansible's hosts files.

#### Step 5: Clone Ansible Galaxy Roles - NOT DONE
The `ansible-galaxy install ...` command clones the role repository found on Ansible Galaxy.
These repositories are an excellent starting point for roles you may be interested in creating.

```bash
# clone your desired ansible roles from galaxy to default directory (~/.ansible/roles)
ansible-galaxy install geerlingguy.git

# clone your desired ansible roles from galaxy to current directory
ansible-galaxy install geerlingguy.dotfiles ---roles-path=./
```

####################### REMOVE TEXT BETWEEN THESE LINES ########################
#### Step 6: Create Your Remote Hosts
The Ansible host computers could exist anywhere as long as they are reachable via SSH.
For this exercise, I'm going to assume the host is on my Ansible server
as Vagrant instances.

So our next step will be to create our Vagrant file that will for our Nginx.

```bash
# list the boxes you have installed on your host
$ vagrant box list
ubuntu/trusty64 (virtualbox, 20180227.0.1)
ubuntu/xenial64 (virtualbox, 20180706.0.0)

# move to directory for vagrant vm
cd  ~/src/vagrant_machines
mkdir nginx
cd nginx

# create a base Vagrantfile (Ubuntu 16.04) and bring it up
vagrant init ubuntu/xenial64
vagrant up

# login to the machine to make sure its working
vagrant ssh
```
####################### REMOVE TEXT BETWEEN THESE LINES ########################

#### Step 6: Set Up SSH Keys
Ansible primarily communicates with client computers through SSH.
While it has the ability to handle password-based SSH authentication,
using SSH keys can help to keep things simple.

For our example here, where we are creating our Ansible hosts as Vagrant instances,
this setup and exchange of SSH keys isn't necessary.
It will be necessary if the Ansible host is remote.

##### Copying Public Key Using ssh-copy-id
A simpler method is to use the `ssh-copy-id` tool
included by default in many operating systems.
Launched from the Ansible server, the syntax is:
`ssh-copy-id username@remote_host`.

##### Copying Public Key Using SSH
If you do not have `ssh-copy-id` available,
but you have password-based SSH access to an account on your server,
you can upload your keys using a conventional SSH method:

```bash
# copying public key using ssh
cat ~/.ssh/id_rsa.pub | ssh username@remote_host "mkdir -p ~/.ssh && touch ~/.ssh/authorized_keys && chmod -R go= ~/.ssh && cat >> ~/.ssh/authorized_keys"
```

##### Copying Public Key Manually
Assuming SSH is already established on your Ansible server,
use the `cat` command to print the contents of your
non-root user’s SSH public key file to the terminal’s output:

```bash
# copy this public ssh key
cat ~/.ssh/id_rsa.pub
```

Copy the resulting output to your clipboard,
then open a new terminal and connect to one of your Ansible hosts using SSH,
and do the following:

1. Switch to the client machine’s root user.
1. As the root user, open the `authorized_keys` within the `~/.ssh` directory:
1. In the file, paste your Ansible server user’s SSH key, then save the file.




* [shelleg/ansible-role-portainer](https://github.com/shelleg/ansible-role-portainer)

* [Ansible and Docker: the Best Combination for an Efficient Software Product Management](https://medium.com/@cabot_solutions/ansible-and-docker-the-best-combination-for-an-efficient-software-product-management-28c86cfebe90)
* [ANSIBLE — DOCKER WITH PORTAINER ON UBUNTU SERVER INSTALLATION](https://medium.com/@dmarko484/ansible-docker-with-portainer-on-ubuntu-server-installation-45a69e07785c)
* [Automate Docker with Ansible deployments - The Digital Life](https://www.the-digital-life.com/deploy-docker-with-ansible/)



---------------


# Install Guacamole

```bash
# check the status of the ufw firewall
sudo ufw status

# enable the firewall
sudo ufw enable

# check the status
$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW IN    Anywhere
22/tcp (v6)                ALLOW IN    Anywhere (v6)
```


---------------



# Development Tools: Install Docker Containers

#### Install Homer
Install the following
* /home/jeff/src/homer-dashboard

```bash
# launch homer container via docker
sudo docker run -d --name="homer-dashboard" \
  -p 8080:8080 \
  -v /home/jeff/src/homer-dashboard/assets/:/www/assets \
  --restart=always \
  b4bz/homer:latest

# check if homer up & running
google-chrome http://localhost:8080
```

#### Install Netdata
Install the following
* /home/jeff/src/netdata

```bash
# launch netdata container via docker
sudo docker run -d --name="netdata" \
  -p 19999:19999 \
  -v netdataconfig:/etc/netdata \
  -v netdatalib:/var/lib/netdata \
  -v netdatacache:/var/cache/netdata \
  -v /etc/passwd:/host/etc/passwd:ro \
  -v /etc/group:/host/etc/group:ro \
  -v /proc:/host/proc:ro \
  -v /sys:/host/sys:ro \
  -v /etc/os-release:/host/etc/os-release:ro \
  --restart unless-stopped \
  --cap-add SYS_PTRACE \
  --security-opt apparmor=unconfined \
  netdata/netdata

# check if netdata up & running
google-chrome http://localhost:19999
```



---------------


# Setup Markdown to PDF / HTML Tools
You can create a PDF or HTML file from a Markdown formatted text file
using a single command line in Ubuntu

```bash
# install the required tools
sudo apt-get install pandoc texlive-latex-base texlive-fonts-recommended texlive-extra-utils texlive-latex-extra markdown

# convert markdown file to PDF
pandoc documentation.txt -o documentation.pdf
pandoc README.md -o README.pdf

# convert markdown file to HTML
pandoc file.md -f markdown -t html -s -o file.html

# or use markdown
markdown file.md > file.html
```

Source:
* [Markdown to PDF – quick howto for linux users (Ubuntu)](https://blog.podkalicki.com/markdown-to-pdf-quick-howto-for-linux-ubuntu/)



---------------

#### Rename Interface
* [ubuntu 22.04 persistent network interface names](https://www.google.com/search?q=ubuntu+22.04+persistent+network+interface+names&sxsrf=ALiCzsYPpufekZV53gZk1KxELS1wlUxmRQ%3A1653143932949&ei=fPmIYu_KOYzWytMP2O-JwAQ&ved=0ahUKEwjv-IqH6fD3AhUMq3IEHdh3AkgQ4dUDCA4&uact=5&oq=ubuntu+22.04+persistent+network+interface+names&gs_lcp=Cgdnd3Mtd2l6EAM6BwgAEEcQsAM6BwgjELACECdKBAhBGABKBAhGGABQsQpYgh5g9iFoAnABeACAATyIAdoCkgEBN5gBAKABAcgBCMABAQ&sclient=gws-wiz)
* [How to rename a network interface in 20.04](https://askubuntu.com/questions/1317036/how-to-rename-a-network-interface-in-20-04)
* [A sysadmin's guide to network interface configuration files](https://opensource.com/article/22/8/network-configuration-files)



[01]:https://ubuntu.com/download/desktop
[02]:https://www.ventoy.net/en/index.html
[03]:https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview
[04]:https://linuxize.com/post/how-to-create-users-in-linux-using-the-useradd-command/
[05]:https://github.com/jeffskinnerbox/.bash
[06]:https://github.com/jeffskinnerbox/.vim
[07]:https://github.com/jeffskinnerbox/.conky
[08]:https://www.videolan.org/
[09]:https://ubuntu.com/core/docs/networkmanager
[10]:https://linux.die.net/man/5/networkmanager.conf
[11]:https://man7.org/linux/man-pages/man8/systemd-networkd.8.html
[12]:https://netplan.io/
[13]:https://linuxconfig.org/netplan-network-configuration-tutorial-for-beginners
[14]:http://www.youtube.com/watch?v=3qY2XgyCB0w
[15]:http://www.tecmint.com/install-youtube-dl-command-line-video-download-tool/
[16]:http://www.tecmint.com/install-youtube-dl-command-line-video-download-tool/
[17]:https://github.com/rg3/youtube-dl
[18]:https://linuxconfig.org/how-to-install-tweak-tool-on-ubuntu-22-04-lts-jammy-jellyfish-linux
[19]:https://www.omgubuntu.co.uk/2022/04/installed-ubuntu-22-04-do-these-things-next
[20]:http://mymediaalexa.com/
[21]:https://www.youtube.com/watch?v=8PxjgKyyrO0
[22]:https://phoenixnap.com/kb/install-virtualbox-on-ubuntu
[23]:https://www.virtualbox.org/wiki/Downloads
[24]:https://www.vagrantup.com/downloads
[25]:https://aphnetworks.com/reviews/intel_desktop_board_dz77ga_70k
[26]:https://www.amazon.com/dp/B003XM568I
[27]:https://us.msi.com/Graphics-Card/N210-MD1GD3/support
[28]:https://www.lg.com/us/monitors/lg-32gn50t-b-led-monitor
[29]:https://www.amazon.com/dp/B00MIBN71I
[30]:https://www.cyberciti.biz/faq/ubuntu-linux-install-nvidia-driver-latest-proprietary-driver/
[31]:https://frameboxxindore.com/apple/you-asked-how-do-i-enable-dual-monitors-in-ubuntu.html
[32]:https://www.manualslib.com/manual/1905901/Lg-Ultragear-32gn500.html?page=6#manual
[33]:http://mymediaalexa.com/
[34]:https://www.youtube.com/watch?v=Pv4Aw5-ONy0
[35]:http://mymediaalexa.com/#section-3
[36]:https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-ansible-on-ubuntu-22-04
[37]:https://serversforhackers.com/c/ansible-installation-and-basics
[38]:https://www.synology.com/en-us/products/DS220+
[39]:https://www.portainer.io/
[40]:https://docs.portainer.io/v/ce-2.9/admin/upgrade/docker
[41]:https://en.wikipedia.org/wiki/Fail-safe
[42]:https://www.mymediaalexa.com/home/docker#download
[43]:http://www.sudo.ws/sudo/sudoers.man.html
[44]:http://www.sudo.ws/visudo.man.html
[45]:http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/
[46]:https://www.amazon.com/bizmodeller-My-Media/dp/B06XPP135L
[47]:https://ostechnix.com/virtualbox-guru-meditation-critical-error-in-linux/
[48]:https://www.rapidseedbox.com/blog/yt-dlp-complete-guide
[49]:https://github.com/yt-dlp/yt-dlp
[50]:https://dl.google.com/linux
[51]:https://neovim.io
[52]:http://vimcasts.org/episodes/neovim-checkhealth/
[53]:https://www.geekbits.io/how-to-install-nerd-fonts-on-linux/
[54]:https://ubuntu.com/core/services/guide/snaps-intro
[55]:https://www.amazon.com/dp/B09KKYS967
[56]:https://www.msi.com/Motherboard/PRO-Z690-A/support#manual
[57]:http://en.wikipedia.org/wiki/Cron
[58]:https://help.ubuntu.com/community/CronHowto
[59]:https://unix.stackexchange.com/questions/638633/is-there-a-way-to-retrieve-uuid-information-of-an-unmounted-hard-drive
[60]:https://support.hp.com/us-en/product/details/hp-laserjet-p2035-printer-series/3662025
[61]:https://github.com/jeffskinnerbox/homelab-portainer-stacks/tree/main/stacks/desktop
[62]:https://ultimaker.com/software/ultimaker-cura/
[63]:https://appimage.org/
[64]:https://www.omgubuntu.co.uk/2023/04/appimages-libfuse2-ubuntu-23-04
[65]:https://www.youtube.com/watch?v=jaYZqc7Luag
[66]:https://www.youtube.com/watch?v=qHJSz4V7DJk
[67]:https://www.python.org/
[68]:https://pypi.org/
[69]:https://www.anaconda.com/download
[70]:https://docs.conda.io/projects/miniconda/en/latest/
[71]:https://en.wikipedia.org/wiki/ARPANET
[72]:https://en.wikipedia.org/wiki/Dial-up_Internet_access
[73]:https://en.wikipedia.org/wiki/Broadband
[74]:https://www.arduino.cc/en/software
[75]:https://www.arduino.cc/en/Guide/Linux
[76]:https://www.arduino.cc/en/hacking/preferences
[77]:https://github.com/tmux-plugins/tpm
[78]:https://github.com/tmux-plugins/list
[79]:
[80]:

