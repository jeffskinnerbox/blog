<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>

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

* [Setting Up Virtual Machines with QEMU, KVM, and Virt-Manager on Debian/Ubuntu](https://linuxconfig.org/setting-up-virtual-machines-with-qemu-kvm-and-virt-manager-on-debian-ubuntu)

* [QEMU: A proper guide!](https://www.youtube.com/watch?v=AAfFewePE7c)
* [The Ultimate System - QEMU and VM Setup](https://www.youtube.com/watch?v=K2gliga5Vwc)
* [Stop using Virtualbox, Here's how to use QEMU instead](https://www.youtube.com/watch?v=Kq849CpGd88)
* [Virtualisation with QEMU](https://documentation.ubuntu.com/server/how-to/virtualisation/qemu/index.html)
* [Installing KVM / QEMU on Ubuntu 24.04 and fixing the NAT](https://blog.wirelessmoves.com/2024/10/installing-kvm-qemu-on-ubuntu-24-04-and-fixing-the-nat.html)
* [Install and Use Qemu on Ubuntu](https://itsfoss.com/qemu-ubuntu/)
* [How to Install QEMU/KVM on Ubuntu to Create Virtual Machines](https://www.tecmint.com/install-qemu-kvm-ubuntu-create-virtual-machines/)

# My Virtualization Technology Life Style

There is a wide verity of [virtualization technology][18] available for software development, testing, and deployment.
It allows you to run multiple virtual machines (VMs) on a single physical machine, each with its own isolated operating system and resources.
I have used [Vagrant][15] and [VirtualBox][16] for several years
for many projects it can take considerable time to setup and get productive.
I have lately been used Proxmox, which can be easier to set up, its main drawback for me is that you must dedicate the whole hardware box to Proxmox.
(since its a [type 1 hypervisor][19]).
And of course I have used Docker, mainly for installing standalone applications/tools but not for standalone operating system environments.
All these tools have served me well by giving me what I need but setup can be challeging.
I have make use of [Ansible][17], which can be very helpful for building out a VM one created,
but still doesn't address that initial set step that is getting im my way.

I work mainly in Ubuntu, and I'm looking for something I can bring up VMs quickly,
and get me productive with very little effort.
For example, I need to bring up Windows from time-to-time (e.g. at tax time, Turbox).
This is a once a year event to bring up the Windows OS, have Internet access, transfer from y host tax data into the VM,
file my taxes, print a copy, transfer back to my host a copy my data, and be done until next year.
I currently do this with Vagrant using Windows 10 but I need to move to Windows 11
and I don't what to go through a lengthy / error prone setup process.

## Using Quickemu / Multipass

After a bit of on-line research, Quickemu or Multipass seem more like what I'm looking for as my user experience.
In this document, I plan to focus on using a host with Debian or Ubuntu Linux distributions
using Quickemu to creat my VMs.
Never the less, I also plan to dive into Multipass, QEMU, KVM (Kernel-based Virtual Machine), and Virt-Manager.

First, lets understand the roles of QEMU, KVM, Virt-Manager, Multipass, and Quickemu:

* [QEMU][01] is an open-source machine emulator and virtualizer that allows you to run
operating systems and software designed for a different hardware and OS architecture.
* [KVM][11] is a virtualization module in the Linux kernel that allows the kernel to function as a [type 1 hypervisor][10].
* [Virt-Manager][09] is a graphical interface for managing virtual machines through [libvirt][09].
* [Multipass][12] is a tool for creating and managing Ubuntu virtual machines (VMs) on Linux, macOS, and Windows.
* [Quickemu][02] is a wrapper around QEMU that automatically "does the right thing" when creating virtual machines.
No requirement for exhaustive configuration options.
You decide what operating system you want to run and Quickemu takes care of the rest.

Launch instances of Ubuntu and [initialise them with cloud-init metadata][13]
in the same way you would on AWS, Azure, Google, IBM and Oracle.
So you can simulate your own cloud deployment on your workstation.
On Linux, you can use QEMU and Virt-Manager with Multipass VMs
because Multipass leverages the `libvirt` backend.
Your allows to manage your Multipass instances through tools like Virt-Manager,
essentially using QEMU as the underlying virtualization technology on Linux systems.
Multipass on Windows will use Hyper-V or Virtualbox, and on macOS it can use QEMU or Virtualbox.

**Key points About Multipass:**
Multipass is designed to create and manage Ubuntu-based Linux virtual machines,
meaning it only readily supports launching Ubuntu images by default;
you cannot use it to run a Windows operating system directly within a Multipass VM.

**Key Point About QEMU:**
You can run a wide verity of operating systems within a QEMU VM.
You can run a Windows ISO image within a QEMU VM,
and run it just like you would on a physical computer.
Although, you may need to install additional drivers like [VirtIO][14]
to optimize performance within the virtual environment.

**Key Point About Quickemu:**
Quickemu has the ease of use benefits of Multipass
and the OS arachitecture supported flexibility of QEMU.
Quickemu can leverage all the tools QEMU can explote (e.g. Virt-Manager, etc.) when needed,
but Quickemu make the setup as simple as possible,
and does this for a wide range of guest operating system.

---------------

# Install Foundational Tools

Before focusing in on Quickemu and Multipass,
I want to provide a mini-introduction to QEMU / Virt-Manager and install them
since they form the foundation of Quickemu.
You will find these tools useful, if not necessary at time,
to get what you need for your Quickemu implementation.

## QEMU

[QEMU (Quick EMUlator][01] calls itself a generic and open source machine emulator and virtualizer.
A machine emulator that can run operating systems & programs for one machine on a different machine.
Mostly QEMU is not used as emulator but
QEMU is a commandline application,
type 2 hypervisor that runs within user space and performs virtual hardware emulation.

I don't want to do a deep dive on installing & using QEMU, but if you read/view the sources listed below,
you will get some good insight into the workings of QEMU.
Via these sources, hopefully you can see the power of QEMU but also the challenges of using it.

Sources:

* [How to Use QEMU to Boot Another Operating System](https://www.howtogeek.com/devops/how-to-use-qemu-to-boot-another-os/)
* [QEMU: A proper guide!](https://www.youtube.com/watch?v=AAfFewePE7c)
* [Stop using Virtualbox, Here's how to use QEMU instead](https://www.youtube.com/watch?v=Kq849CpGd88)
* [Setup Qemu in Debian Linux](https://christitus.com/vm-setup-in-linux/)
* [Installing Qemu/KVM on Ubuntu 24.04](https://absprog.com/post/qemu-kvm-ubuntu-24-04)

## Install QEMU & VirtManager on Ubuntu

* [How To install QEMU KVM & VirtManager on Ubuntu || Run Virtual Machines On Ubuntu][20]
* [How to Install KVM on Ubuntu 24.04 Step-by-Step][21]
* [Installing and using Virtual Machine Manager on Ubuntu](https://www.youtube.com/watch?v=PdfuzxJAOlo)

#### Step 1: Check for Virtualization Support - DONE

As your first installation step,
make sure your host system is capable of supporting virtualization and support the creation of VMs.

```bash
# check if your hardware virtualization enabled
$ lscpu | grep Virtualization
Virtualization:                       VT-x

# make sure you can use all your cpu cores by print the number available
$ egrep -c '(vmx|svm)' /proc/cpuinfo
32
```

When `lscpu` shows `Virtualization: VT-x`,
it means your CPU supports Intel's Virtualization Technology (VT-x),
which is a hardware feature that enables virtualization technologies like KVM and VMware.

#### Step 2: Install QEMU and Virt-Manager - DONE

Next we need to install the QEMU/KVM software to support virtualization.
This includes [Virtual Machine Manager (`virt-manager`)][08] which provides a graphical user interface (GUI)
for managing local and remote virtual machines via [`libvirt`][09].
[Libvirt][09] is an open-source virtualization API that manages virtualization technologies like KVM, QEMU, and VMware ESXi.
It's used to create, modify, monitor, and manage virtual machines.

In addition to the `virt-manager` GUI utility itself,
the package also contains a collection of other helpful tools like:

* `virt-manager` - presents a summary view of running VM, their live performance & resource utilization statistics.
 Wizards enable the creation of new VMs, and configuration & adjustment of a VM’s resource allocation & virtual hardware.
 An embedded VNC and SPICE client viewer presents a full graphical console to the guest VMs.
* `virt-install`
* `virt-clone`
* `virt-viewer`
* `libvirt-daemon-system` - configuration file management
* `libvirt-clients` - host client to manage/control VMs
* `bridge-utils` - a tool to create/manage network bridege devices

Its important to be aware of `virt-manager` as part of the `quickemu` ecosystem
beacuse of its usefulness for extending the capabilities of `quickemu` installation and for debugging too.

```bash
# update your repository
sudo apt update

# install qemu, virt-manager, and all there tools
sudo apt install qemu-kvm virt-manager libvirt-daemon-system virtinst libvirt-clients bridge-utils ssh-askpass

# reboot to make sure it is all working
sudo shutdown -r now

# check the status of your install
sudo systemctl status libvirtd

# if its not running or inactive, do the following
sudo systemctl enable libvirtd.service
sudo systemctl start libvirtd.service
```

Sources:

* [Installing and using Virtual Machine Manager on Ubuntu](https://www.youtube.com/watch?v=PdfuzxJAOlo)
* [Virt-Manager Is The Better Way To Manage VMs](https://www.youtube.com/watch?v=p1d_b_91YlU)
* [Virtual Machines Inside Linux - Virt-Manager](https://www.youtube.com/watch?v=rKH8XhPfJjE)

#### Step 3: Update the libvirt Group - DONE

Add the current user (or what eve users that need to manage QEMU VMs)
to the appropriate groups to administer the virtual machines.

```bash
# list the groups you have on your system
$ groups
jeff adm cdrom sudo dip plugdev users lpadmin libvirt

# add your current user to the libvirt group
sudo useradd -g $USER libvirt
sudo useradd -g $USER libvirt-kvm

# check if curent user (i.e. jeff) has been added to the libvirt group
$ groups jeff
jeff : jeff adm cdrom sudo dip plugdev users lpadmin libvirt

# test the virt-manager app and make sure you connect with no errors
virt-manager
```

#### Step 4: Creating VM With QEMU & Virt-Manager - DONE

For an example of how to create a VM just using QEMU & Virt-Manager (no Quickemu), check out the video
"[How To install QEMU KVM & VirtManager on Ubuntu || Run Virtual Machines On Ubuntu][20]"
Also checkout "[How to Install KVM on Ubuntu 24.04 Step-by-Step][21]" for another example.

#### Step 5: Advanced Tips & Tricks with QEMU, KVM, and Virt-Manager - DONE

The [**QEMU Guest Agent**][22] (`qeum-guest-agent`) facilitates improved communication between
the host and the guest VMs, enabling functionalities such as file transfers,
graceful shutdowns, and system information queries.
To take advantage of these features, install the guest agent in your VMs:

```bash
# install qemu guest agent on linux guest
sudo apt install qemu-guest-agent
sudo systemctl enable --now qemu-guest-agent

# install qemu guest agent on windows guest
<see Sources listed below>
```

To **attach USB devices** directly to a VM,
go to the VM’s hardware details in Virt-Manager, add a USB host device,
and select the device you wish to attach.

You can execute **command-line administration** of Virt-Manager GUI functionality,
especially for remote administration or scripting.
Here are some basic commands:

```bash
# list all running vm
sudo virsh list --all

# start a vm
sudo virsh start vm_name

# shutdown a vm
sudo virsh shutdown vm_name

# get vm information
sudo virsh dominfo vm_name
```

Sources:

* [Setting Up Virtual Machines with QEMU, KVM, and Virt-Manager on Debian/Ubuntu](https://linuxconfig.org/setting-up-virtual-machines-with-qemu-kvm-and-virt-manager-on-debian-ubuntu)
* [Installing the QEMU guest agent on virtual machines](https://docs.openshift.com/container-platform/4.8/virt/virtual_machines/virt-installing-qemu-guest-agent.html)

---------------

# Quickemu Project

The [Quickemu Project][02] takes the QEMU / Virt-Manager functional
and puts a wrapper around it further reduce the complexity of creating VMs.
With Quickemu, you can quickly create and run Windows, macOS,
and Linux virtual machines from the terminal on a Linux and macOS machine.
It consits of three primary subsystems:

* [Quickget][07] downloads the Quickemu Project's supported OS and creates the configuration file required by QEMU.
* [Quickemu][04] is a wrapper for the excellent QEMU that automatically
"does the right thing" when creating virtual machines.
No requirement for exhaustive configuration options.
You decide what operating system you want to run and Quickemu takes care of the rest
and creates a default configuration that works.
* [Quickgui][03] is a graphical user interface for the Quickemu virtual machine manager.
Quickgui enables you to create and manage virtual machines from a simple and elegant interface.
Nearly 1000 operating systems supported including Windows, macOS, BSDs, and 100s of Linux distros.
All with automated downloads and configuration.

What Quickemu is doing is automating the installation and initialization.
It configures everything for you;
there's no need to worry about managing vitalized components.
You just choose the operating system you want,
and after the scripts do their job, you can start working in it.
Quickemu automates the setup of hundreds of operating systems,
including Windows Server, macOS, Ubuntu, Fedora, and FreeBSD.

If you need to enhance the Quickemu configuration this it supplies
(e.g. add networking, disk access, etc.) you can use the QEMU / Virt-Manager tools to do so.
Some typical enhancements will be shown below.

## Install Quickemu on Ubuntu

Quickemu is easiest to install when you're on Ubuntu or Debian.
On Ubuntu and its derivatives, you can instead add the Quickemu PPA to your repositories.
I assume that you have done the installation of QEMU & Virt-Manager as outline above.

I'm most interested in running Window 11,
so in the steps below,
I'll be retriving the Quickemu image for Windows 11 but I could do many other operating systems if desired.

Sources:

* [Quickemu](https://github.com/quickemu-project/quickemu)
* [Quickemu Installation](https://github.com/quickemu-project/quickemu/wiki/01-Installation)
* [Get Windows on Linux in 10 Minutes With These 2 Commands](https://www.howtogeek.com/get-windows-on-linux-in-10-minutes-with-quickemu/)
* [How to create optimized virtual machines with Quickemu on Linux](https://linuxconfig.org/how-to-create-optimized-virtual-machines-with-quickemu-on-linux)

#### Step 1: Install Quickemu Package - DONE

To enable file sharing, copy & paste, and other functionson the host computer,
you should install the following package (more about this later):

```bash
# install the spice client on the ubuntu host
sudo apt install spice-client-gtk
```

Quickemu is available from a PPA for Ubuntu users.
To install Quickemu and all the dependencies,
run the following in a terminal:

```bash
# install the quickemu repository
sudo apt-add-repository ppa:flexiondotorg/quickemu
sudo apt update

# install quickemu
sudo apt install quickemu quickgui

# cheatsheet for quickemu
quickemu --help

# cheatsheet for quickget
quickget --help
```

Here are some of the most basic options:

```bash
# run a specific vm by referencing its configuration file
quickemu --vm <path/to/vm.conf>

# run a specific vm with a spice display
quickemu --vm <path/to/vm.conf> --display spice

# kill a running virtual machine
quickemu --kill --vm <path/to/vm.conf>

# delete a virtual machine, its configuration, and all related files / directories
quickemu --delete-vm --vm <path/to/vm.conf>
```

#### Step 2: Make Your Working Directory - DONE

Since you will be downloading an ISO file, configuration file, etc.,
create a working direct for you OS instance.

```bash
# create your working directory
mkdir -p ~/src/virtual-machines/quickemu/windows-11
```

It is here in the `shared` directory you will place any working files you will like to load into the you OS.
In my case, I'll be doing my taxes with TurboTax
and so I'll place my last years tax filing in the following directory:

```
# create directory for file sharing (aka working files)
mkdir -p ~/src/virtual-machines/quickemu/windows-11/shared
```

Now move any working files you wish to share with the OS into this directory.

#### Step 3: Select and Install Your Target OS - DONE

I want to install Windows 11.
To get a list of supported operating systems,
use the command below:

```bash
# change to your working directory
cd ~/src/virtual-machines/quickemu/windows-11

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
$ quickget windows 11 "English (United States)"
Downloading Windows 11 (English (United States))
 - Parsing download page: https://www.microsoft.com/en-us/software-download/windows11
 - Getting Product edition ID: 3113
 - Permit Session ID: c28e4301-0bd0-40c7-825d-debc5a8498ba
 - Getting language SKU ID: 18480
 - Getting ISO download link...
 - URL: https://software.download.prss.microsoft.com/dbazure/Win11_24H2_English_x64.iso
################################################################################################################################# 100.0%
Downloading VirtIO drivers...
################################################################################################################################# 100.0%
Downloading Spice drivers...
################################################################################################################################# 100.0%
Making unattended.iso
Making windows-11-English-United-States.conf
 - Setting windows-11-English-United-States.conf executable

To start your Windows virtual machine run:
    quickemu --vm windows-11-English-United-States.conf
```

```bash
To start your Windows virtual machine run:
 quickemu --vm windows-11-English-United-States.conf
```

**I GOT THIS ERROR:** [bug: win11 installation encountered an unexpected error. #1475](https://github.com/quickemu-project/quickemu/issues/1475)
Now using:
    `quickget windows 10 "English (United States)"`
    `quickemu --vm windows-10-English-United-States.conf`

#### Step 4: Bring Up the Quickemu Guest VM - DONE

To launch your Quickemu virtual machine,
all you need to know is the name of the configuration file (with a `.conf` extension) that Quickemu created:

```bash
# bring up the virtual machine (aka guest)
quickemu --vm windows-11-English-United-States.conf --display spice --public-dir ./shared
```

#### Step 5: Enable File Sharing Between Quickemu Host & Guest

Sharing data between guest and host system is necessary in many scenarios.
If the guest is a Linux system,
you can simply add a shared folder that will be automatically mounted.
[However, this does not work if the guest is Windows][23].
There are work arounds and I'm going to use one of them here.

```bash
quickemu --public-dir /home/jeff/src/virtual-machines/quickemu/windows-10/shared \
         --viewer spicy --width 1400 --height 1050 \
         --vm windows-10-English-United-States.conf
```

Sources:

* [Sharing a folder a windows guest under virt-manager](https://www.guyrutenberg.com/2018/10/25/sharing-a-folder-a-windows-guest-under-virt-manager/)

#### Step 6: Set Up a Samba Server on Ubuntu Host

Having a Samba server on Ubuntu enables file and printer sharing across a network,
particularly beneficial for mixed operating system environments,
allowing Windows clients to access resources on Linux/Unix systems and vice versa.

The first task is to install Samba:

```bash
# install samba
sudo apt update
sudo apt install samba
```

On the quickemu host, we first establish a user account for Samba
(called `samba` wich is needed for security),
create a Server Message Block (SMB) protocol password for the `samba` account,
create a directory that will be shared by the `samba` account,
changed the ownership of the shared directory to the `samba` account,
establish the read/write permissions for the shared directory,
update the Samba seervices configuration file,
make sure your host firewall is open for Samba services,
and restart Samba services to get everything working together.

_I used my standard password for all._

```bash
# create user account and account password for samba
sudo adduser samba

# create a SMB password for the Samba account we created
sudo smbpasswd -a samba

# create the directory you wish to share
cd ~/src/virtual-machines/quickemu/windows-10
mkdir shared

# copy any external files you want windows to access to the `shared/` directory
cp <file-needed-by-windows> shared/

# change the ownership of the `shared/` directory and all it contents to the Samba account
sudo chown -R samba:samba shared

# establish the read/write permission for the shared directory
sudo chmod -R 0775 shared
```

Next we need to configure the Samba server via a configuration file in the `/etc/samba/` directory.
Edit the `/etc/samba/smb.conf` and make these additions at the bottom of the file:

```bash
# Setup to support file sharing between quickemu host (ubuntu) and guest (windows).
# Access will password protected.
[share]
   path = /home/jeff/src/virtual-machines/quickemu/windows-10/shared
   browsable = yes
   read only = no
   guest ok = no
```

Make sure you Ubuntu host firewall is **not** blocking Samba networking:

```bash
# check your fire wall status
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere
22/tcp (v6)                ALLOW       Anywhere (v6)

# allow samba sbm packet to flow
sudo ufw allow Samba

# check your fire wall status
sudo ufw status
```

Now we will restart the Samba server to get sharing up and working:

```bash
# start samba service
sudo systemctl restart smbd.service

# check the status of the samba service
sudo systemctl status smbd.service
```

Sources:

* [Set Up a Samba Server on Ubuntu 24.04: Step-by-Step Guide for File Sharing](https://www.youtube.com/watch?v=2gW4rWhurUs)

#### Step 7: Initialize & Test Samba Service With Guest Windows VM

To connect to a Samba server from Windows 10,
login to your Windows 10 guest VM and do the following:

1. Open File Explorer
2. Right-click on **This PC** (in the left pane of File Explorer) and pop-up a menu
3. rSselect from the menu **Add a network location**
4. Follow the wizard to connect to the Samba share site:
    1. Select **Choose a custom network location**
    2. For network address, enter `\\192.168.1.200` and click **Browse...**
    3. Select **Share** from the pop-up window and click **Next** until finished
5. You'll now find your shared directory in the left pane of File Explorer

>**NOTE:** If you get prompted for credentials,
>enter the Samba username & password we created in the earlier step.

To disconnect the Windows guest VM from the Samba server:
[How to Disconnect from a Server or File Share](https://kb.mlml.sjsu.edu/books/network-services/page/how-to-disconnect-from-a-server-or-file-share)

Sources:

* [Set Up a Samba Server on Ubuntu 24.04: Step-by-Step Guide for File Sharing](https://www.youtube.com/watch?v=2gW4rWhurUs)
* [Setting up Simple Samba File Shares](https://www.youtube.com/watch?v=7Q0mnAT1MRg)
* ChatGPT Prompt: "on windows 10, how do you connect with a samba server"
* ChatGPT Prompt: "on windows 10, how do you disconnect from a samba server"

#### Step 8: Enable Copy & Paste Between Ubuntu Host and Windows 10 Guest

To enable copy & paste between a QuickEMU Ubuntu host and a Windows 10 guest,
install the SPICE Windows guest tools on the guest VM and start QuickEMU with `--display spice`,
and ensure a SPICE agent channel is defined in the VM's configuration.

Install SPICE Guest Tools in the Windows VM by:
    1. Start the Windows guest VM.
    2. Download the `spice-guest-tools-latest.exe` file from the SPICE website:
    <https://www.spice-space.org/download/windows/spice-guest-tools/spice-guest-tools-latest.exe>.
    i3. Install the downloaded executable.

To test copy & paste, use the follow to start the Windows 10 VM:

```bash
# start windows 10 vm with copy & paste enabled
quickemu --display spice --width 1400 --height 1050 --vm windows-10-English-United-States.conf
```

Sources:

* ChatGPT Prompt: "activate copy & paste between quickemu ubuntu host and windows guest"

---------------

# Multipass - NOT COMPETED OR TESTED

Ubuntu Multipass is used to quicky launch & manage Linux virtual machines on Linux, MacOS and Windows.
From a developer’s perspective, it is an interesting alternative to Docker or VirtualBox.
It feels easier and simpler to use.

* [Ubuntu VMs on demand for any workstation](https://canonical.com/multipass)
* [Boost your development environment with Ubuntu Multipass](https://letsdebug.it/post/21-ubuntu-multipass/)
* [Multipass: Ubuntu Virtual Machines Made Easy](https://dev.to/mattdark/multipass-ubuntu-virtual-machines-made-easy-3am9)
* [A Comprehensive Guide to Multipass: Simplifying Virtual Machine Management](https://dev.to/adityapratapbh1/a-comprehensive-guide-to-multipass-simplifying-virtual-machine-management-b0c)

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

[01]:https://www.qemu.org/
[02]:https://github.com/quickemu-project
[03]:https://github.com/quickemu-project/quickgui
[04]:https://github.com/quickemu-project/quickemu
[07]:https://github.com/quickemu-project/quickemu/blob/master/quickget
[08]:https://virt-manager.org/
[09]:https://libvirt.org/
[10]:https://ubuntu.com/blog/kvm-hyphervisor
[11]:https://linux-kvm.org/page/Main_Page
[12]:https://canonical.com/multipass
[13]:https://ubuntu.com/blog/using-cloud-init-with-multipass
[14]:https://wiki.osdev.org/Virtio
[15]:https://www.vagrantup.com/
[16]:https://www.virtualbox.org/
[17]:https://docs.ansible.com/
[18]:https://www.youtube.com/watch?v=E3azDp1K8X0
[19]:https://www.youtube.com/watch?v=pUb8vVL5wo0
[20]:https://www.youtube.com/watch?v=4m6eHhPypWI
[21]:https://www.youtube.com/watch?v=qCUmf5gyOYY
[22]:https://pve.proxmox.com/wiki/Qemu-guest-agent
[23]:https://askubuntu.com/questions/899916/how-to-share-folder-with-windows-10-guest-using-virt-manager-kvm
