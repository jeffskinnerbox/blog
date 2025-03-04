

---------------


# Linux Hypervisor Setup

* [Linux Hypervisor Setup (libvirt/qemu/kvm)](https://www.youtube.com/watch?v=HfNKpT2jo7U)
* [Headless Virtual Machines, Headless Servers](https://www.youtube.com/watch?v=Q2OHR-uJMcU&list=PLJvGMqQH5qsmuTuDRAzX1Cy9MdSmf7hnu)


## KVM
KVM (Kernel-based Virtual Machine) is a full virtualization solution for Linux on x86 hardware containing virtualization extensions (Intel VT or AMD-V).
KVM was added to the Linux Kernel (version 2.6.20) in February of 2007.

* [QEMU/KVM for absolute beginners](https://www.youtube.com/watch?v=BgZHbCDFODk)
* [Amazing Privacy Ideas with KVM Virtual Machines](https://www.youtube.com/watch?v=NIdu4haRWx0)


## QEMU
[QEMU (Quick EMUlator][A1] calls itself a generic and open source machine emulator and virtualizer.
A machine emulator that can run operating systems & programs for one machine on a different machine.
Mostly QEMU is not used as emulator but as virtualizer in collaboration with KVM kernel components.
In that case it utilizes the virtualization technology of the hardware to virtualize guests.

QEMU is a type 2 hypervisor that runs within user space and performs virtual hardware emulation, whereas KVM is a type 1 hypervisor that runs in kernel space, that allows a user space program access to the hardware virtualization features of various processors.

Proxmox VE vs Qemu: What are the differences? - <https://stackshare.io/stackups/proxmox-ve-vs-qemu>
Qemu/KVM Virtual Machines - <https://pve.proxmox.com/wiki/Qemu/KVM_Virtual_Machines>

* [QEMU: A proper guide!](https://www.youtube.com/watch?v=AAfFewePE7c)
* [The Ultimate System - QEMU and VM Setup](https://www.youtube.com/watch?v=K2gliga5Vwc)
* [Stop using Virtualbox, Here's how to use QEMU instead](https://www.youtube.com/watch?v=Kq849CpGd88)
* [Virtualisation with QEMU](https://documentation.ubuntu.com/server/how-to/virtualisation/qemu/index.html)
* [Installing KVM / QEMU on Ubuntu 24.04 and fixing the NAT](https://blog.wirelessmoves.com/2024/10/installing-kvm-qemu-on-ubuntu-24-04-and-fixing-the-nat.html)
* [Install and Use Qemu on Ubuntu](https://itsfoss.com/qemu-ubuntu/)
* [How to Install QEMU/KVM on Ubuntu to Create Virtual Machines](https://www.tecmint.com/install-qemu-kvm-ubuntu-create-virtual-machines/)

[A1]:https://www.qemu.org/


# libvirt


## Virt-Manager

* [Virt-Manager Is The Better Way To Manage VMs](https://www.youtube.com/watch?v=p1d_b_91YlU)
* [Virtual Machine Manager: Virt-Manager](https://virt-manager.org/)


---------------


# KVM

KVM (Kernel-based Virtual Machine) is a full virtualization solution for Linux on x86 hardware containing virtualization extensions (Intel VT or AMD-V).
KVM was added to the Linux Kernel (version 2.6.20) in February of 2007.

* [QEMU/KVM for absolute beginners](https://www.youtube.com/watch?v=BgZHbCDFODk)
* [Amazing Privacy Ideas with KVM Virtual Machines](https://www.youtube.com/watch?v=NIdu4haRWx0)


---------------

>**NOTE:** I could not get file sharing to work, or more accurately stated,
>the effort required wasn't worth it.
>As of Feb 2025, it appears that Quickemu has not advance enough to
>include file shareing to make it easy to install.
>I choose to wait and reexamine Quickemu at a future date.
>
>Why do I think this, see the "TBD" in the "File Sharing" section off
>[05 Advanced quickemu configuration](https://github.com/quickemu-project/quickemu/wiki/05-Advanced-quickemu-configuration)
>writen in on May 13, 2024


# QEMU

[QEMU (Quick EMUlator][A1] calls itself a generic and open source machine emulator and virtualizer.
A machine emulator that can run operating systems & programs for one machine on a different machine.
Mostly QEMU is not used as emulator but as virtualizer in collaboration with KVM kernel components.
In that case it utilizes the virtualization technology of the hardware to virtualize guests.

QEMU is a type 2 hypervisor that runs within user space and performs virtual hardware emulation.
Whereas KVM is a type 1 hypervisor that runs in kernel space,
that allows a user space program access to the hardware virtualization features of various processors.

* [QEMU: A generic and open source machine emulator and virtualizer](https://www.qemu.org/)
* [How to Use QEMU to Boot Another Operating System](https://www.howtogeek.com/devops/how-to-use-qemu-to-boot-another-os/)
* [Proxmox VE vs Qemu: What are the differences?](https://stackshare.io/stackups/proxmox-ve-vs-qemu)
* [Qemu/KVM Virtual Machines](https://pve.proxmox.com/wiki/Qemu/KVM_Virtual_Machines)
* [QEMU: A proper guide!](https://www.youtube.com/watch?v=AAfFewePE7c)
* [Stop using Virtualbox, Here's how to use QEMU instead](https://www.youtube.com/watch?v=Kq849CpGd88)
    * [Setup Qemu in Debian Linux](https://christitus.com/vm-setup-in-linux/)


## Quickemu Project
[Quickemu Project][A2] can quickly create and run Windows, macOS,
and Linux virtual machines from the terminal on Linux and macOS.
It consits of three primary subsystems:

* [Quickget][A7] downloads the Quickemu Project's supported OS and creates the configuration file required by QEMU.
* [Quickemu][A4] is a wrapper for the excellent QEMU that automatically
"does the right thing" when creating virtual machines.
No requirement for exhaustive configuration options.
You decide what operating system you want to run and Quickemu takes care of the rest.
* [Quickgui][A3] is a graphical user interface for the Quickemu virtual machine manager.
Quickgui enables you to create and manage virtual machines from a simple and elegant interface.
Nearly 1000 operating systems supported including Windows, macOS, BSDs, and 100s of Linux distros.
All with automated downloads and configuration.

All Quickemu is doing is automating the installation and initialization.
It configures everything for you;
there's no need to worry about managing virtualized components.
You just choose the operating system you want,
and after the scripts do their job, you can start working in it.
Quickemu automates the setup of hundreds of operating systems,
including Windows Server, macOS, Ubuntu, Fedora, and FreeBSD.


## Install Quickemu on Ubuntu
Quickemu is easiest to install when you're on Ubuntu or Debian.
On Ubuntu and its derivatives, you can instead add the Quickemu PPA to your repositories.

I'm most interested in running Window 11,
so in the steps below,
I'll be retriving the Quickemu image for Windows 11 but I could do many other operating systems if desired.

Sources:

* [Quickemu](https://github.com/quickemu-project/quickemu)
* [Quickemu Installation](https://github.com/quickemu-project/quickemu/wiki/01-Installation)
* [Get Windows on Linux in 10 Minutes With These 2 Commands](https://www.howtogeek.com/get-windows-on-linux-in-10-minutes-with-quickemu/)
* [Installing Qemu/KVM on Ubuntu 24.04](https://absprog.com/post/qemu-kvm-ubuntu-24-04)


#### Step 1: Install Quickemu Package - DONE
Quickemu is available from a PPA for Ubuntu users.
To install Quickemu and all the dependencies,
run the following in a terminal:

```bash
# install the quickemu repository
sudo apt-add-repository ppa:flexiondotorg/quickemu
sudo apt update

# install quickemu
sudo apt install quickemu quickgui

# quick test
$ quickemu --help
             _      _
  __ _ _   _(_) ___| | _____ _ __ ___  _   _
 / _' | | | | |/ __| |/ / _ \ '_ ' _ \| | | |
| (_| | |_| | | (__|   <  __/ | | | | | |_| |
 \__, |\__,_|_|\___|_|\_\___|_| |_| |_|\__,_|
    |_| v4.9.7, using qemu 8.2.2
--------------------------------------------------------------------------------
 Project - https://github.com/quickemu-project/quickemu
 Discord - https://wimpysworld.io/discord
--------------------------------------------------------------------------------

Usage
  quickemu --vm ubuntu.conf <arguments>

Arguments
  --access                          : Enable remote spice access support. 'local' (default), 'remote', 'clientipaddress'
  --braille                         : Enable braille support. Requires SDL.
  --delete-disk                     : Delete the disk image and EFI variables
  --delete-vm                       : Delete the entire VM and its configuration
  --display                         : Select display backend. 'sdl' (default), 'cocoa', 'gtk', 'none', 'spice' or 'spice-app'
  --fullscreen                      : Starts VM in full screen mode (Ctl+Alt+f to exit)
  --ignore-msrs-always              : Configure KVM to always ignore unhandled machine-specific registers
  --kill                            : Kill the VM process if it is running
  --offline                         : Override all network settings and start the VM offline
  --shortcut                        : Create a desktop shortcut
  --snapshot apply <tag>            : Apply/restore a snapshot.
  --snapshot create <tag>           : Create a snapshot.
  --snapshot delete <tag>           : Delete a snapshot.
  --snapshot info                   : Show disk/snapshot info.
  --status-quo                      : Do not commit any changes to disk/snapshot.
  --viewer <viewer>                 : Choose an alternative viewer. @Options: 'spicy' (default), 'remote-viewer', 'none'
  --width <width>                   : Set VM screen width; requires '--height'
  --height <height>                 : Set VM screen height; requires '--width'
  --ssh-port <port>                 : Set SSH port manually
  --spice-port <port>               : Set SPICE port manually
  --public-dir <path>               : Expose share directory. @Options: '' (default: xdg-user-dir PUBLICSHARE), '<directory>', 'none'
  --monitor <type>                  : Set monitor connection type. @Options: 'socket' (default), 'telnet', 'none'
  --monitor-telnet-host <ip/host>   : Set telnet host for monitor. (default: 'localhost')
  --monitor-telnet-port <port>      : Set telnet port for monitor. (default: '4440')
  --monitor-cmd <cmd>               : Send command to monitor if available. (Example: system_powerdown)
  --serial <type>                   : Set serial connection type. @Options: 'socket' (default), 'telnet', 'none'
  --serial-telnet-host <ip/host>    : Set telnet host for serial. (default: 'localhost')
  --serial-telnet-port <port>       : Set telnet port for serial. (default: '6660')
  --keyboard <type>                 : Set keyboard. @Options: 'usb' (default), 'ps2', 'virtio'
  --keyboard_layout <layout>        : Set keyboard layout: 'en-us' (default)
  --mouse <type>                    : Set mouse. @Options: 'tablet' (default), 'ps2', 'usb', 'virtio'
  --usb-controller <type>           : Set usb-controller. @Options: 'ehci' (default), 'xhci', 'none'
  --sound-card <type>               : Set sound card. @Options: 'intel-hda' (default), 'ac97', 'es1370', 'sb16', 'usb-audio', 'none'
  --sound-duplex <type>             : Set sound card duplex. @Options: 'hda-micro' (default: speaker/mic), 'hda-duplex' (line-in/line-out), 'hda-output' (output-only)
  --extra_args <arguments>          : Pass additional arguments to qemu
  --version                         : Print version
```

To enable file sharing, copy & paste, and other functions,
you should also install the following package (more about this below):

```bash
# install the spice client on the ubuntu host
sudo apt install spice-client-gtk
```


#### Step X: Install Virtual Machine Manager
The [Virtual Machine Manager (`virt-manager`)][A8] provides a graphical user interface (GUI)
for managing local and remote virtual machines via [`libvirt`][A9].
In addition to the `virt-manager` utility itself,
the package also contains a collection of other helpful tools like `virt-install`, `virt-clone` and `virt-viewer`.

 `virt-manager` presents a summary view of running VM,
 their live performance & resource utilization statistics.
 Wizards enable the creation of new VMs, and configuration & adjustment of a VM’s resource allocation & virtual hardware.
 An embedded VNC and SPICE client viewer presents a full graphical console to the guest VMs.

I include `virt-manager` as part of the installation of `quickemu` beacuse of its
usefulness as a debugging too.

```bash
# install virt-manager
sudo apt install virt-manager

# to use virt-manager, use the following
sudo virt-manager
```

Sources:

* [QEMU/KVM for absolute beginners](https://www.youtube.com/watch?v=BgZHbCDFODk)
* [Installing and using Virtual Machine Manager on Ubuntu](https://www.youtube.com/watch?v=PdfuzxJAOlo)


#### Step 2: Make Your Working Directory - DONE
Since you will be downloading an ISO file, configuration file, etc.,
create a working direct for you OS instance.

```bash
# create your working directory
mkdir -p ~/tmp/test-quickemu
```

It is here you will also be placing any working files you will like to load into the you OS.
In my case, I'll be doing my taxes with TurboTax
and so I'll place my last years tax filing in the following directory:

```
# create directory for file sharing (aka working files)
mkdir -p ~/tmp/test-quickemu/shared
```

Now move any working files you wish to share with the OS into this directory.


#### Step 3: Select and Install Your Target OS - DONE
I want to install Windows 11.
To get a list of supported operating systems,
use the command below:

```bash
# change to your working directory
cd ~/tmp/test-quickemu

# list all the supported operating systems
quickget --list

# find your target operating systems
$ quickget --list | grep -i English | grep -i Windows
windows 10 English (United States)
windows 10 English International
windows 11 English (United States)
windows 11 English International
windows-server 2016 English (United States)
windows-server 2019 English (United States)
windows-server 2022 English (United States)

# down load your target operating system
$ quickget windows 10 "English (United States)"
Downloading Windows 10 (English (United States))
 - Parsing download page: https://www.microsoft.com/en-us/software-download/windows10ISO
 - Getting Product edition ID: 2618
 - Permit Session ID: 1aaed4f5-9698-4a04-b581-3d2c2250d66c
 - Getting language SKU ID: 16067
 - Getting ISO download link...
 - URL: https://software.download.prss.microsoft.com/dbazure/Win10_22H2_English_x64v1.iso
################################################################################################################# 100.0%
Downloading VirtIO drivers...
################################################################################################################# 100.0%
Downloading Spice drivers...
################################################################################################################# 100.0%
################################################################################################################# 100.0%
################################################################################################################# 100.0%
Making unattended.iso
Making windows-11-English-United-States.conf
 - Setting windows-11-English-United-States.conf executable

To start your Windows virtual machine run:
    quickemu --vm windows-11-English-United-States.conf
```


#### Step 4: Bring Up the Quickemu Guest VM - DONE
To launch your Quickemu virtual machine,
all you need to know is the name of the configuration file (with a `.conf` extension) that Quickemu created:

```bash
# bring up the virtual machine (aka guest)
quickemu --vm windows-11-English-United-States.conf --display spice --public-dir ./shared
```

<!-- vvvvvvvvvvvv THIS DID NOT WORK, REMOVE AND USE SAMBA METHOD vvvvvvvvvvvv -->
#### Step X: Enable File Sharing Between Quickemu Host & Guest
To share files from a Quickemu host running Ubuntu
with a Quickemu guest running Windows,
there are two methods:

1. For one, you can leverage the built-in Samba sharing functionality within Quickemu.
This will allowing you to access a shared folder on the Ubuntu host
directly from the Windows guest through a network path.
To do this, you simply configure the shared folder on the Ubuntu host
and then access it on the Windows guest using the provided network address in the Quickemu settings.
2. A second method is to use SPICE.
You enable the Quickemu SPICE functionality with the `--display spice` commandline flag,
and then install the SPICE guest tools on the Windows guest.
This allows you to access the host's shared folder directly within the Windows file explorer using the SPICE protocol.

On the Ubuntu host,
launch your Quickemu instance use the command with the commandline flag
`--display spice` to activate SPICE.
Also ensure you have the SPICE client installed on your host machine
using the package `spice-client-gtk`.
Using the following:

```bash
# install the spice client on the ubuntu host
sudo apt install spice-client-gtk

# change to your working directory
cd ~/tmp/test-quickemu

# bring up the virtual machine (aka guest)
quickemu --vm windows-11-English-United-States.conf --display spice --public-dir ./shared
```

On the Windows guest, once the Windows guest is running,
install the SPICE guest tools package to enable file sharing functionality.
here is how you install the SPICE guest tools on the Windows guest:

1. Start the Windows VM.
2. Open your favorite browser, inside the Windows VM.
3. Go to [SPICE Website Download Page][A5].
4. Scroll down to **Windows binaries**.
5. In the first sentence you should see:
"Windows SPICE Guest Tools (spice-guest-tools)"
Click -> [**spice-guest-tools**][A6] to download it on the Guest VM.
6. Run through the installer. The defaults should be fine.
7. Restart the Windows gusest VM.

After installation, the shared folder on the host should be accessible directly
within the Windows file explorer, mounted as a network drive.

Sources:

* [How-to install Windows SPICE Guest Tools on QEMU/KVM Virtual Machine Manager](https://dev.to/sonandrew/how-to-install-windows-spice-guest-tools-on-qemukvm-virtual-machine-manager-2e51)
* [Enable WebDAV Publishing IIS in Windows 11](https://winsides.com/how-to-enable-webdav-publishing-iis-windows-11/)
* [Simple and Effective Virtualization in Linux (QEMU + Quickemu)](https://www.youtube.com/watch?v=TXAh4pcpnMY)
* [Sharing Folders Between Host and Guest in QEMU/KVM Using VirtioFS](https://absprog.com/post/qemu-kvm-shared-folder)
<!-- ^^^^^^^^^^^^ THIS DID NOT WORK, REMOVE AND USE SAMBA METHOD ^^^^^^^^^^^^ -->


#### Step X: Enable File Sharing Between Quickemu Host & Guest

* [Canonical Ubuntu Tutorials: Install and Configure Samba](https://ubuntu.com/tutorials/install-and-configure-samba#1-overview)



[A2]:https://github.com/quickemu-project
[A3]:https://github.com/quickemu-project/quickgui
[A4]:https://github.com/quickemu-project/quickemu
[A5]:https://www.spice-space.org/download.html
[A6]:https://www.spice-space.org/download/windows/spice-guest-tools/spice-guest-tools-latest.exe
[A7]:https://github.com/quickemu-project/quickemu/blob/master/quickget
[A8]:https://virt-manager.org/
[A9]:https://libvirt.org/


---------------


# Multipass

* [Launching Ubuntu instances with Multipass](https://www.youtube.com/watch?v=Z91l6ZdQjhI)
* [Linux Fu: Easy VMs](https://hackaday.com/2022/11/01/linux-fu-easy-vms/)
* [Multipass: Ubuntu VMs on demand for any workstation](https://canonical.com/multipass)
* [How to create a VM with Multipass](https://ubuntu.com/server/docs/how-to-create-a-vm-with-multipass)

```bash
# install multipass
sudo snap install multipass

# list your commandline options
$ multipass
Usage: multipass [options] <command>
Create, control and connect to Ubuntu instances.

This is a command line utility for multipass, a
service that manages Ubuntu instances.

Options:
  -h, --help     Displays help on commandline options
  -v, --verbose  Increase logging verbosity. Repeat the 'v' in the short option
                 for more detail. Maximum verbosity is obtained with 4 (or more)
                 v's, i.e. -vvvv.

Available commands:
  alias         Create an alias
  aliases       List available aliases
  authenticate  Authenticate client
  delete        Delete instances
  exec          Run a command on an instance
  find          Display available images to create instances from
  get           Get a configuration setting
  help          Display help about a command
  info          Display information about instances
  launch        Create and start an Ubuntu instance
  list          List all available instances
  mount         Mount a local directory in the instance
  networks      List available network interfaces
  purge         Purge all deleted instances permanently
  recover       Recover deleted instances
  restart       Restart instances
  set           Set a configuration setting
  shell         Open a shell on a running instance
  start         Start instances
  stop          Stop running instances
  suspend       Suspend running instances
  transfer      Transfer files between the host and instances
  umount        Unmount a directory from an instance
  unalias       Remove aliases
  version       Show version details
```

So `multipass` is now installed and ready to go.
Let's see what virtual machine images are avalable to us:

```bash
# see all the images available from multipass
$ multipass find
Image                       Aliases           Version          Description
snapcraft:core18            18.04             20201111         Snapcraft builder for Core 18
snapcraft:core20            20.04             20210921         Snapcraft builder for Core 20
snapcraft:core22            22.04             20220426         Snapcraft builder for Core 22
snapcraft:devel                               20221101         Snapcraft builder for the devel series
core                        core16            20200818         Ubuntu Core 16
core18                                        20211124         Ubuntu Core 18
18.04                       bionic            20221014         Ubuntu 18.04 LTS
20.04                       focal             20221018         Ubuntu 20.04 LTS
22.04                       jammy,lts         20221101.1       Ubuntu 22.04 LTS
22.10                       kinetic           20221101         Ubuntu 22.10
appliance:adguard-home                        20200812         Ubuntu AdGuard Home Appliance
appliance:mosquitto                           20200812         Ubuntu Mosquitto Appliance
appliance:nextcloud                           20200812         Ubuntu Nextcloud Appliance
appliance:openhab                             20200812         Ubuntu openHAB Home Appliance
appliance:plexmediaserver                     20200812         Ubuntu Plex Media Server Appliance
anbox-cloud-appliance                         latest           Anbox Cloud Appliance
charm-dev                                     latest           A development and testing environment for charmers
docker                                        latest           A Docker environment with Portainer and related tools
jellyfin                                      latest           Jellyfin is a Free Software Media System that puts you in control of managing and streaming your media.
minikube                                      latest           minikube is local Kubernetes
```

```bash
# launch a ubuntu bionic (18.04) instance
# default is one cpu core, a gigabyte of ram, and 5G of disk storage
$ multipass launch bionic
Launched: integral-anemone

# launch a ubuntu kinetic (22.10) instance
# with 2 cpu, 6G of ram, a 10G disk, and named test-sys
$ multipass launch -c 2 -m 6G -d 10G -n test-sys kinetic
Launched: test-sys

# launch a default ubuntu
$ multipass launch
Launched: courageous-cichlid

# list all the virtual machines
$ multipass list
Name                    State             IPv4             Image
courageous-cichlid      Running           10.110.155.186   Ubuntu 22.04 LTS
integral-anemone        Running           10.110.155.156   Ubuntu 18.04 LTS
test-sys                Running           10.110.155.244   Ubuntu 22.10

# log into a running instance
multipass test-sys shell

# stop all the virtual machines
multipass stop test-sys courageous-cichlid integral-anemone

# list all the virtual machines
$ multipass list
Name                    State             IPv4             Image
courageous-cichlid      Stopped           --               Ubuntu 22.04 LTS
integral-anemone        Stopped           --               Ubuntu 18.04 LTS
test-sys                Stopped           --               Ubuntu 22.10

# delete all the images
multipass delete test-sys courageous-cichlid integral-anemone
$ multipass list
Name                    State             IPv4             Image
courageous-cichlid      Deleted           --               Not Available
integral-anemone        Deleted           --               Not Available
test-sys                Deleted           --               Not Available

# purge all the images
multipass purge
$ multipass list
No instances found.
```


---------------


