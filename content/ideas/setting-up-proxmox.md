<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----


* [Getting into Proxmox](https://www.youtube.com/playlist?list=PLhMI0SExGwfADAlk-rmC-IG_JcYz175NX)
* [Low Power Cluster - Small, Efficient, BUT Powerful!](https://www.youtube.com/watch?v=8DeG3qO-HIA)
* [10 Watt HA Proxmox Cluster ft. ZimaBoard](https://www.youtube.com/watch?v=JfZuZ6zE7AI)

* [Create VMs on Proxmox in Seconds!](https://www.youtube.com/watch?v=1nf3WOEFq1Y)
* [Proxmox virtual machine *automation* in Terraform](https://www.youtube.com/watch?v=dvyeoDBUtsU)
* [Eleven of the Best Open Source Hypervisor Technologies](https://informationsecuritybuzz.com/eleven-of-the-best-open-source-hypervisor-technologies/)







# Upgrade from Proxmox 7 to 8
* [Upgrade from 7 to 8](https://pve.proxmox.com/wiki/Upgrade_from_7_to_8)
* [Proxmox VE 8.1 Brings SDN and More for its Popular Virtualization Platform](https://www.servethehome.com/proxmox-ve-8-1-brings-sdn-and-more-for-its-popular-virtualization-platform/)
* [Proxmox VE 8.1 Brings Software-Defined Networking and Secure Boot](https://www.storagereview.com/news/proxmox-ve-8-1-brings-software-defined-networking-and-secure-boot)
* [Upgrade Proxmox VE Version 7 to Version 8: The Complete Step-by-Step Guide](https://www.youtube.com/watch?v=i5cmx-mcUVA)
* https://pve.proxmox.com/wiki/Upgrade_from_7_to_8
* https://www.servethehome.com/proxmox-ve-8-0-is-out-upgrading-linux-and-more/
* https://www.virtualizationhowto.com/2023/06/proxmox-8-new-features-and-home-lab-upgrade-instructions/
* Proxmox Backup Server Version 3.0 Now Available
    * https://www.storagereview.com/news/proxmox-backup-server-version-3-0-now-available
    * https://www.proxmox.com/en/news/listid-1/mailid-200-proxmox-backup-server-3-0-available?tmpl=component&tmpl=component
* [Proxmox Backup Server 3.1 Released](https://www.storagereview.com/news/proxmox-backup-server-3-1-released)

# New Proxmox Installs
* [5 Things I Would Do On Fresh Install Of ProxMox](https://www.youtube.com/watch?v=xD9Xyt2mdSI)
* [Proxmox 10 tweaks you need to know](https://www.youtube.com/watch?v=bo33EQk9CCM)
* [Speed Up Your Proxmox Deployment With This Simple Trick](https://www.youtube.com/watch?v=WYmdoTPTusk)
* [Docker on Proxmox LXC 🚀 Zero Bloat and Pure Performance!](https://www.youtube.com/watch?v=-ZSQdJ62r-Q)
* [Software-Defined Network (SDN) Setup in Proxmox](https://www.youtube.com/watch?v=gYSxGCiLeto)
* [The correct way to install Docker in Proxmox using a unique feature LXC Containers](https://www.youtube.com/watch?v=s_rm8mpSGcY)





# Proxmox
Proxmox Virtual Environment (Proxmox VE)
is a complete open source server virtualization management solution.
It offers the ability to manage virtual server (VPS) technology with the Linux OpenVZ and KVM technologies.
Since Proxmox uses Linux Kernel-based Virtual Machines (KVM) for virtualization
and converts the host operating system to a hypervisor,
it is considered a [Type 1 hypervisor](https://phoenixnap.com/kb/what-is-hypervisor-type-1-2).
To top it off, Proxmox is [know][43] for its efficiency and ease of use compared to many alternatives.

It tightly integrates two virtualization technologies: the KVM hypervisor and Linux Containers (LXC), software-defined storage and networking functionality, on a single platform. With the integrated web-based user interface you can manage VMs and containers, high availability for clusters, or the integrated disaster recovery tools with ease.
You can manage virtual machines, containers, highly available clusters, storage and networks with an integrated, easy-to-use web interface or via CLI.

you can install Debian Buster with GUI and install
[Proxmox VE on top of it](https://pve.proxmox.com/wiki/Install_Proxmox_VE_on_Debian_Buster)
or you can install Proxmox VE from ISO installer and install a desktop environment like Gnome on top of it. This way, you can access the web interface with just https://localhost:8006

I plan to use the Protectli/Proxmox server as a firewall in a SOHO network with a switch or a SOHO wireless network.
This is my first instance of Proxmox (giving it the name `pve-1`) with the plan to
install additional instances of Proxmox when I establish a cluster of Raspberry Pis.
* https://protectli.com/kb/basic-soho-network-with-switch/
* https://protectli.com/kb/basic-soho-wireless-network/

>**NOTE:** For home labs, a popular alternative to Proxmox is the free version of VMware ESXi.
>ESXi is used in many enterprise environments, much more so than Proxmox.
>[So why not go with ESXi][35]?
>The free version of ESXi doesn’t have a REST API, and as such,
>you can't use automation tools like Ansible with it.

Virtualization
* [What is Virtualization?](https://www.youtube.com/watch?v=L8A9PHeyRrY)
* [vSphere, Hyper-V, and Proxmox - Which hypervisor is best?](https://www.youtube.com/watch?v=6XiWSnt3-9M)
* [you need to learn Virtual Machines RIGHT NOW!! (Kali Linux VM, Ubuntu, Windows)](https://www.youtube.com/watch?v=wX75Z-4MEoM)
* [Virtual Machines Pt. 2 (Proxmox install w/ Kali Linux)](https://www.youtube.com/watch?v=_u8qTN3cCnQ)
* [Introduction to Linux interfaces for virtual networking](https://developers.redhat.com/blog/2018/10/22/introduction-to-linux-interfaces-for-virtual-networking#)

Proxmox Training / Tutorials
* [Proxmox Full Course](https://www.youtube.com/watch?v=LCjuiIswXGs&list=PLT98CRl2KxKHnlbYhtABg6cF50bYa8Ulo)
* [Virtualize Everything! - Proxmox Install Tutorial](https://www.youtube.com/watch?v=azORbxrItOo)
* [STH Proxmox Articles](https://www.servethehome.com/?s=proxmox)

* The software build
    * [Proxmox VE Install and Setup Tutorial](https://www.youtube.com/watch?v=7OVaWaqO2aU)
    * [Virtualize Everything! - Proxmox Install Tutorial](https://www.youtube.com/watch?v=azORbxrItOo)
    * [Before I do anything on Proxmox, I do this first...](https://www.youtube.com/watch?v=GoZaMgEgrHw)
    * [Proxmox VE 7 Initial Installation Checklist](https://www.servethehome.com/proxmox-ve-7-initial-installation-checklist/)
    * [Quick installation](https://pve.proxmox.com/wiki/Quick_installation)
    * [Installation](https://pve.proxmox.com/wiki/Installation)
    * [Proxmox VE Documentation Index](https://pve.proxmox.com/pve-docs/)

* What can you do
    * [Virtualize Windows 11 with Proxmox the Right Way!](https://www.youtube.com/watch?v=fupuTkkKPDU)
    * [20 Ways to Use a Virtual Machine (and other ideas for your homelab)](https://www.youtube.com/watch?v=SVQmzaSabEQ)
    * [Terraform 1 and Proxmox; working as it should](https://vectops.com/2021/06/terraform-1-and-proxmox-working-as-it-should/)
    * [Protect your home network! // Sophos XG Firewall on Proxmox Walkthrough](https://www.youtube.com/watch?v=7pvgKc3WdEg)
    * [How to Build your Own Next-Generation Firewall (NGFW) at Home?](https://www.sunnyvalley.io/docs/network-security-tutorials/how-to-build-ngfw-for-home)
    * [How to Virtualize Your Home Router / Firewall Using efSense](https://www.youtube.com/watch?v=hdoBQNI_Ab8)
    * [Using Nginx Proxy Manager with pfSense, Proxmox, and Docker](https://www.youtube.com/watch?v=6aaSjwJhOog)
    * [your home router SUCKS!! (use pfSense instead)](https://www.youtube.com/watch?v=lUzSsX4T4WQ)
    * [How To Create VLANs in Proxmox For a Single NIC](https://www.youtube.com/watch?v=ljq6wlzn4qo)
    * [Proxmox VLAN Configuration: Linux Bridge Tagging, Management IP, and Virtual Machines](https://www.youtube.com/watch?v=stQzK0p59Fc)
    * [2020 Getting started with pfsense 2.4 Tutorial: Network Setup, VLANs, Features & Packages](https://www.youtube.com/watch?v=fsdm5uc_LsU)
    * [How to Virtualize Your Home Router / Firewall Using pfSense](https://www.youtube.com/watch?v=hdoBQNI_Ab8)

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

Proxmox VE vs Qemu: What are the differences? - https://stackshare.io/stackups/proxmox-ve-vs-qemu
Qemu/KVM Virtual Machines - https://pve.proxmox.com/wiki/Qemu/KVM_Virtual_Machines

* [QEMU: A proper guide!](https://www.youtube.com/watch?v=AAfFewePE7c)
* [Stop using Virtualbox, Here's how to use QEMU instead](https://www.youtube.com/watch?v=Kq849CpGd88)

[A1]:https://www.qemu.org/

# libvirt

## Virt-Manager
* [Virt-Manager Is The Better Way To Manage VMs](https://www.youtube.com/watch?v=p1d_b_91YlU)
* [Virtual Machine Manager: Virt-Manager](https://virt-manager.org/)

## Install Proxmox VE on Debian OS
Installation of Proxmox on a native bare metal is recommended,
but it may be desirable to install Proxmox on an existing Debian OS or within a Debian vitural machine.

>**Note:** Proxmox can only be installed on 64-bit hardware and a 64-bit operating system.

Sources:
* [Installing Proxmox on a Debian system](https://subscription.packtpub.com/book/virtualization-and-cloud/9781783980901/1/ch01lvl1sec13/installing-proxmox-on-a-debian-system)
* [How To Install Proxmox VE 6 on Debian 10 (Buster)](https://computingforgeeks.com/how-to-install-proxmox-ve-on-debian/)
* [Proxmox Virtual Environment Installation Guide (on Debien Server)](https://www.servermania.com/kb/articles/proxmox-virtual-environment/)
* [How to Install Proxmox Virtual Environment on a Dedicated Server](https://www.linuxbabe.com/linux-server/install-proxmox-ve)
* [Run Proxmox VE 6.0 using Vagrant](https://lunar.computer/posts/vagrant-proxmox-60/)

## Proxmox in VirtualBox
[Testing Proxmox in virtualbox?](https://www.reddit.com/r/Proxmox/comments/idvz7m/testing_proxmox_in_virtualbox/)
I want to test out Proxmox in Virtualbox / Vagrant before I got to install it on my server.
As KVM is not supported in Virtualbox,
will proxmox behave differently or will I be extremely limited with what I can do,
to the point where I wont benefit from testing it out in virtualbox?
As far as I understand Proxmox will have to run as a type 2 hypervisor within virtual box? If I've got that wrong I will fuck off back to the drawing board.

As long as you enable VT-x/AMD-V, Proxmox should work fine in a Virtualbox VM.
There's a wiki page for it, might be helpful: https://pve.proxmox.com/wiki/Proxmox_VE_inside_VirtualBox
You can, you just won't be able to run VMs without nesting support in virtualbox. Containers should still work.

## VMware vs Proxmox
Where organizations increasingly rely on virtualization and containerization,
Proxmox and VMware are two notable selections for deploying virtual machines (VM).
Though both vendors offer free options, Proxmox is fully open source and a favorite for home server aficionados.
The virtualization pioneer, VMware, sits squarely at the front of the VM industry,
offering advanced features and support for enterprise workloads.
Proxmox VE and VMware ESXi are two of the most popular virtualization solutions, although they differ in many respects.

* [VMware vs Proxmox](https://www.rippleweb.com/vmware-vs-proxmox/)
* [What is Proxmox Virtualization?](https://www.youtube.com/watch?v=GMAvmHEWAMU)
* [Proxmox vs. ESXi: Side-By-Side Comparison](https://www.wundertech.net/proxmox-vs-esxi/)

# Protectli Vault
* $450 (1.6GHz, Quad Core Celeron J3160, 8GB RAM, 120GB SSD, 4x Intel Gigabit Ethernet ports, AES-NI) - [Protectli Vault 4 Port, Firewall Micro Appliance/Mini PC](https://www.amazon.com/dp/B07G9NHRGQ?ref=ppx_yo2_dt_b_product_details&th=1)

* [Proxmox 101](https://medium.com/devops-dudes/proxmox-101-8204eb154cd5)

## Coreboot
The Protectli Vault comes with [Coreboot][24] which is a secure boot-firmware solution.
Coreboot is a replacement for BIOS / UEFI with a focus on boot speed, security and flexibility.
It is designed to boot your operating system as [fast as possible without any compromise to security][26].

The Intel [Advanced Encryption Standard New Instructions (AES-NI)][25]
is integrated into the Protectli Vault processor.
This improves the speed and security of applications performing encryption / decryption
using Advanced Encryption Standard (AES).

## rEFInd Boot Manager
[rEFInd][44] is a fork of the [rEFIt][45] boot manager for computers based on the [Extensible Firmware Interface (EFI) and Unified EFI (UEFI)][46]. Like rEFIt, rEFInd is a boot manager, meaning that it presents a menu of options to the user when the computer first starts up, as shown below. rEFInd is not a boot loader, which is a program that loads an OS kernel and hands off control to it. Many popular boot managers, such as the [Grand Unified Bootloader (GRUB)][47], are also boot loaders, which can blur the distinction in many users' minds. All EFI-capable OSes include boot loaders, so this limitation isn't a problem. If you're using Linux, you should be aware that several EFI boot loaders are available, so choosing between them can be a challenge.

* [Linux Fu: UEFI Booting](https://hackaday.com/2023/01/19/linux-fu-uefi-booting/)

# Bare Metal vs Virtualize vs Containerize
When spinning up self-hosted services in your Homelab environment,
when should I virtualize, containerize, or bare metal?

* [Virtualize vs. Containerize (Which should I choose?)](https://www.youtube.com/watch?v=pxwUXJmAER4)

# LastPass & Proxmox
I found that I couldn't login to Proxmox at times.
Proxmox simply would not move byond the login screen, as if I entered nothing at all.
This appears to be a conflict between Proxmox and LastPass.
The work around was to use Incognito mode in my Chrome browser.

* [Unable to log in on PVE servers with Firefox since update to 7.4-3](https://forum.proxmox.com/threads/unable-to-log-in-on-pve-servers-with-firefox-since-update-to-7-4-3.125557/)
* [Google Chrome Incognito Guide | Private Browsing Tutorial](https://www.youtube.com/watch?v=5wJKbyOe0qE)



-----



# Proxmox Networking
A bridge is created in Proxmox to make the VMs on the host system accessible via an additional IP.

## Create Private Network Bridge

## Create Private Network Bridge with NAT
create a private IP (NAT) setup for VMs

## Connect 2 Routers with Different Subnet
I want to make the transition from my test configuration to my implementation
as easy as possible.
So within Vault/Proxmox I was attempting to connect, via pfSense, my current home network
`192.168.1.0/24` with subnet `192.168.20.0/24`.
I was thinking that I could effectively move my Vault/Proxmox setup from my test configuration
and replace my FiOS router with minimal manual intervention and confusion on my part.
But I had nothing but problems when
making the Vault/pfSense WAN `192.168.1.202` and the LAN `192.168.20.0/24`.
First of all, I could not reliably reach the Internet or my FiOS gateway.
It would seem to work for some initial pings but then stop working.
Trouble shooting this kept mey busy for several days.
Come to find out, I made a newbie error in not understanding that.
The web-post "[Why can't I have the same subnet on WAN and LAN?][27]" explains it well.
The heart of the issue is that routers are designed to connect two or more **different subnets**,
ARP messages don't go past routing boundaries,
and the use of NAT by pfSense and the FiOS router is in [support of Internet routing][28],
not local routing (the killer stroke for my mental model of how networking works).

To make things worst,
I didn't have a good handle on the modern standard form of specification
of IP ranges & mask with the notation used via [Classless Inter-Domain Routing (CIDR)][29].
As a result, it was confusing my pfSense instance and me.

So I had conform to the "network rules of engagement" above to make things work.

1. Select two different IP network reserved for private networks.
One for WAN and the other is for the LAN side of pfSense.
    * Class A Addresses: `192.168.0.0` – `192.168.255.255` (65,536 IP addresses)
    * Class B Addresses: `172.16.0.0` – `172.31.255.255` (1,048,576 IP addresses)
    * Class C Addresses: `10.0.0.0` – `10.255.255.255` (16,777,216 IP addresses)
    * Local Link Addresses: `169.254.0.0` – `169.254.255.255` (16,777,216 IP addresses)

* [IP address classes explained | class A , B ,C ,D ,E | Free CCNA 200-301](https://www.youtube.com/watch?v=0dFNpNgiTAA)
* [Networking - What IP Address Ranges are Reserved as Private IP Addresses?](https://www.youtube.com/watch?v=NmCF5JiT8Mg)
* [What Is CIDR (Classless Inter-Domain Routing)?](https://www.keycdn.com/support/what-is-cidr)
* [What is a subnet? | How subnetting works](https://www.cloudflare.com/learning/network-layer/what-is-a-subnet/)
* [IP Subnet Calculator](https://www.calculator.net/ip-subnet-calculator.html)
* `sudo apt install ipcalc` - [IP Calculator](https://jodies.de/ipcalc)
* [CIDR to IPv4 Conversion]()

## OpenVSwitch
Open vSwitch is a virtual switch which enables you to create multiple virtual networks on a single physical host. In Proxmox, it’s a more flexible networking approach over the standard Linux Bridge method.
The default install of Proxmox does not contain the required packages for Open vSwitch so you will have to install them manually.

* [Linux Bridge vs OpenVSwitch — How to Improve Virtualization Network Performance](https://ioflood.com/blog/2021/07/08/linux-bridge-vs-openvswitch-how-to-improve-virtualization-network-performance/)
* [Installing Open vSwitch in Proxmox](https://www.jamescoyle.net/how-to/1485-installing-open-vswitch-in-proxmox)
* [Proxmox Configure Open vSwitch](https://codingpackets.com/blog/proxmox-configure-open-vswitch/)


-----



* [Building a homelab with Proxmox](https://www.remotelycurious.net/post/homelab/)

# Install Proxmox on Protectli Vault
Proxmox VE has been successfully installed on the Protectli Vault with both Legacy and coreboot BIOS.
Protectli provides [instructions on how to install Proxmox VE on the Vault][03].

* [Proxmox VE on the Vault][03]
* [How to Install Proxmox VE][05]
* [Proxmox 7.x Installation Guide][30]

#### Step 1: Download Ventoy (Optional) - DONE
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
<goto https://github.com/ventoy/Ventoy/releases>

# uncompress the ventoy image
tar -xvzf ventoy-1.0.64-linux.tar.gz

# execute the install script
# where /dev/XXX is the USB device (eg /dev/sdf)
cd ventoy-1.0.64
sudo bash ./Ventoy2Disk.sh -i /dev/sdf
```

Now you just copy (aka 'drag & drop')
any of the ISO files you wish to install onto the USB flash drive.
There is no need to do a `dd` disk copy.
When you boot from the Ventoy prepared USB flash drive,
you get a menu of the images you can boot & install.

>**Note:** To updating Ventoy when a new version of Ventoy is released, you can update it to the USB drive.
>All the ISO files will be unchanged.
>Upgrade operation is in the same way with installation.
>Ventoy2Disk.sh will prompt you for update if the USB drive already installed with Ventoy.

* [How to Create a Multiboot USB with Ventoy Fast, Simple, and Easy Guide](https://www.youtube.com/watch?v=z1FyoCswwAc)
* [Ventoy: How to Create a Multiboot USB Drive with Multiple ISO Files](https://linuxiac.com/ventoy-create-bootable-usb/)

#### Step 2: Download Proxmox ISO Image - DONE
The ISO image file is a [hybrid ISO image][12] of a disk.
It is an ISO image file (ready to burn to a CD or DVD)
and a raw sector (IMG) image file (ready to copy to a USB flash drive).
[Download the Proxmox VE ISO image installer][10],
then [copy it to a USB flash drive][11].
The flash drive needs to have at least 1 GB of storage available.

```bash
# download proxmox ve 7.1 iso installer
cd ~/Downloads
<goto https://www.proxmox.com/en/downloads>

# check if you have a clean download, compare to websites SHA256 sum
$ sha256sum proxmox-ve_7.1-2.iso
f469d2e419328c4b8715544c84f629161cc07024ce26ad63f00bc1b07de265df  proxmox-ve_7.1-2.iso

# plug-in flash drive and find its device name
df -h

# copy the iso image to a usb drive
$ sudo dd bs=1M conv=fdatasync if=./proxmox-ve_7.1-2.iso of=/dev/sdf
986+1 records in
986+1 records out
1033949184 bytes (1.0 GB, 986 MiB) copied, 158.805 s, 6.5 MB/s

# unmount the usb flash drive
sudo umount /dev/sdf1
```

#### Step 3: Boot Protectli Vault Using COM Port - DONE
The Protectli Vault come with an external COM port that can be used to view the Vault’s console output.
This COM port is simply a redirect from the Vault’s display output (whether HDMI or VGA).
You can uses this before an operating system boots,
giving the user the ability to use the COM port with a serial terminal
instead of the VGA or HDMI ports for things like adjusting BIOS settings
or installing via the USB port a operating system or Proxmox in our case.

[USB to RJ45 Console Cable](https://www.amazon.com/dp/B01AFNBC3K)
is an essential accessory for many brands of routers, switches, firewalls,
and wireless LAN controllers with CONSOLE port.

* [How to use the Vault’s COM port](https://protectli.com/kb/com-port-tutorial/)

On you desktop, execute `ls /dev/ttypUSB*` and make note of what gets listed.
Now plug in the USB end of the console cable, execute `ls /dev/ttypUSB*` again
and the new output is the device drive for your console cable.
In my case, it is `/dev/ttyUSB0`.

Now plug in the RJ45 end of the console cable to the Protectli Vault `COM` port.
On the desktop, execute the command `screen /dev/ttyUSB0 115200,cs8cls`.
To access the Vault’s BIOS, once the boot starts on the Protectli Vault,
repeatedly clicking the `DEL` key as the Vault boots.

#### Step 4: Update Protectli's BIOS - DONE
[Download the BIOS for FW4B][01] (Protectli Vault 4 Port Intel J3160).
As of this writing, there is an August 31, 2021 download available (BIOS_ID BSW4L011)
which happens to be the same version currently install.

* [BIOS Versions for the Vault][01]
* [How to perform a BIOS update](https://protectli.com/kb/bios-update/)

#### Step X: Boot Proxmox From USB - DONE
Proxmox VE is based on Debian.
This is why the install disk images (ISO files) provided by Proxmox
includes a Debian OS and is used to support Proxmox.
Neve the less, Proxmox VE is a bare-metal installer.
As a result, the complete Protectli Vault server is used
and all existing data will be removed from the drive.

Prior to installing Proxmox:

* Plug into the Protectli Vault a HDMI monitor and USB keyboard.
* Make sure the USB drive with Proxmox ISO is plugged into Protectli Vault's USB port
and connect the WAN port to the Internet / DHCP server.

Start the install of Proxmox:

* Apply power to the Protectli Vault which will start the boot process.
* To access the Vault’s BIOS, once the boot starts on the Protectli Vault,
repeatedly clicking the `DEL` key as the Vault boots.
* Tab to the **Boot** screen and make sure `UEFI: USB Disk 3.0 PMAP, Partition 2` is the first boot on the Protectli Vault.
* Tab to the **Save & Exit** screen and let it run until you get the menu of ISO files.
From the menu, select the Poxmox ISO.

When you get the Proxmox logo screen,
press 'Enter' to start the Proxmox installation wizard on the Protectli Vault.

During the running of the wizard, you'll need to enter some information
(see "[How to Install Proxmox VE][05]"):

* Select **Install Proxmox VE**
* Set the Management Interface to the Portectli Vault's OPT1 aka `enp3s0`
(this gives you a dedicated network interface for managment of the Proxmox system).
* I gave the the Proxmox instance the [fully qualified domain name (FQDN)][17]
`pve-1.jeffskinnerbox.me` (Other instance of `pve-*` coming to Raspberry Pi cluster
to test Proxmox cluster / hyperconverged storage at some future date!).
* Set the IP address of the Managment Interface to some static address on your LAN
(I choose `192.168.1.202`)
* Gateway set to `192.168.1.1` and DNS set to `192.168.1.1`.

Since this is a configuration for testing,
the Vault / Proxmox platform is being setup in a test configuration.
In time, this will be moved to replace my FiOS router and I will then have to change
the WAN, Gateway, and DNS IP address.

>**NOTE:** If for some reason you need to change your Proxmox IP address,
>check out "[How to Change Primary Proxmox VE IP Address][02]".

#### Step X: Prepare for Login / Configure Proxmox via GUI - DONE
We will do the remaining tasks via the Proxmox web browser.

* Plug an Ethernet cable on your home LAN and the other end to `WAN` port of the Proxmox box
(In effect, your home LAN is standing in for the Internet).
* Plug an Ethernet cable on your home LAN and the other end to `OPT1` port of the Proxmox box
(Your going to have a dedicate NIC for Proxmox's Management Browser GUI at the `OPT1` port).
* Point your browser to the Proxmox Management Interface IP address at port 8006
(i.e. URL https://192.168.1.202:8006).

At this point, your `/etc/network/interfaces` file should look somrhting like this:

```
# network interface settings; autogenerated
# Please do NOT modify this file directly, unless you know what
# you're doing.
#
# If you want to manage parts of the network configuration manually,
# please utilize the 'source' or 'source-directory' directives to do
# so.
# PVE will preserve these directives, but will NOT read its network
# configuration from sourced files, so do not attempt to move any of
# the PVE managed interfaces into external files!

auto lo
iface lo inet loopback

iface enp1s0 inet manual
#WAN interface of Portectli Vault

iface enp2s0 inet manual
#LAN interface of Portectli Vault

iface enp3s0 inet manual
#OPT1 interface of Portectli Vault

iface enp4s0 inet manual
#OPT2 interface of Portectli Vault

auto vmbr0
iface vmbr0 inet manual
        bridge-ports enp1s0
        bridge-stp off
        bridge-fd 0
#WAN interface used by pfSense

auto vmbr1
iface vmbr1 inet manual
        bridge-ports enp2s0
        bridge-stp off
        bridge-fd 0
#LAN created via pfSense

auto vmbr2
iface vmbr2 inet static
        address 192.168.1.202/24
        gateway 192.168.1.1
        bridge-ports enp3s0
        bridge-stp off
        bridge-fd 0
#Proxmox Management Interface
```

Now using the browser interface, move on to the next step.

>**NOTE:** SSH is enable on Proxmox,
>so you can also get terminal access the Proxmox box via `ssh root@192.168.1.202`
>but all configuration of Proxmox will mainly be done via its browser interface.

#### Step X: Set Proxmox to No-Subscription Repository - DONE
In its current configuration,
refreshing the Proxmox repositories we get a message stating you not authorized to access a repository,
since you don't have a support license.
To avoid this, Lets make the [modifications recommended by Proxmox][13] and [Unixcop][15]
and use the [Proxmox VE No-Subscription Repository][13].

The website "[Proxmox 7.x Installation Guide][30]" provides a good description
on how to set up the No-Subscription repository.
It basicly goes like this:

* Select **pve-1** > **Repositories** > **Add** and select "No-Subscription from the **Repository**
* Select the "pve-enterprise" line and then select **Disable**
* Select the "pve-no-subscription" line and then select **Enable**
* Select **pve-1** > **Updates** > **Refresh** - this updates your repositories
* Select **_Upgrade** wich puts you into a terminal where you can do the upgrade

In the future, you can use the above method to update Proxmox repositories
or via terminal using `ssh root@192.168.1.202` and enter the following:

```bash
# update proxmox packages
apt update
apt -y upgrade
```

#### Step X: Set Proxmox to No-Subscription Repository - DO NOT DO THIS
In its current configuration,
refreshing the Proxmox repositories we get a message stating you not authorized to access a repository,
since you don't have a support license.
To avoid this, Lets make the [modifications recommended by Proxmox][13] and [Unixcop][15]
and use the [Proxmox VE No-Subscription Repository][13].

Get to a shell via
the Proxmox GUI **Datacenter** > **pve-1** > **Shell**
or a terminal via `ssh root@192.168.1.202` so you can edit some files.
Edit the repository listing `/etc/apt/sources.list` so that it contains:

```bash
# debian repository
deb http://ftp.debian.org/debian bullseye main contrib
deb http://ftp.debian.org/debian bullseye-updates main contrib

# PVE pve-no-subscription repository provided by proxmox.com,
# NOT recommended for production use
deb http://download.proxmox.com/debian/pve bullseye pve-no-subscription

# security updates
deb http://security.debian.org/debian-security bullseye-security main contrib
```

And then comment out the entry within the file
`/etc/apt/sources.list.d/pve-enterprise.list` so it likes below:

```bash
# comment out when not used for production
#deb https://enterprise.proxmox.com/debian/pve bullseye pve-enterprise
```

You can now refresh the Proxmox packages without error via
terminal `ssh root@192.168.1.202`,
or you could do the refresh via the commandline within Proxmox GUI **Shell**.

```bash
# update your repository / packages
apt update

# upgrade the packages
apt dist-upgrade

# do a reboot for safe measure
shutdown -r now
```

Once you have done this commandline update procedure,
you should be able to do future refreshes via
the GUI **Datacenter** > **pve-1** > **Updates** > **Refresh**.

#### Step X: Install SPICE on Client - DONE
SPICE is a suite of tools for interfacing with desktop-oriented Virtual Machines.
To use SPICE, you'll need the client running on your desktop computer.
To do the install, follow the instructions below:

```bash
# install on your desktop computer the spice client
sudo apt-get install qemu-kvm virt-viewer
```

To enable SPICE on the Proxmox VM,
go to **Hardware** > **Display** > **Edit** > select **SPICE**

* [How to copy & paste in PROXMOX terminals?](https://forum.proxmox.com/threads/how-to-copy-paste-in-proxmox-terminals.36425/)
noVNC is a VNC server implemented in QEMU. It has no knowledge of what's going on in the VM. You may be able to copy command output to the guest's clipboard, but the VNC server has no way of accessing it. Copying to the host's clipboard via VNC can only be done if the VNC server is run in the guest.

noVNC isn't intended for everyday use, but for quick administration tasks. If you want to actually work on the VM you're much better of just SSHing into it. Then you can copy/paste into the terminal in whatever ways you're used to.

* [Desktop Virtualization using SPICE on Linux](https://www.youtube.com/watch?v=fhW3ddJIWTs)
* [SPICE Project](https://www.spice-space.org/)
* [Proxmox SPICE](https://pve.proxmox.com/wiki/SPICE)
* [Proxmox SPICE console](https://www.networkshinobi.com/proxmox-spice-console/)
* [Raspberry Pi THIN CLIENT for Proxmox VMs](https://www.youtube.com/watch?v=TuDrmq4RQzU)
* [How to install and use SPICE for VMs in Debian, Ubuntu or Mint](https://velenux.wordpress.com/2016/12/30/how-to-install-and-use-spice-for-vms-in-debian-ubuntu-or-mint/)

#### Step X: Remove the Nagging Subscription Message
When you log into Proxmox, you get the pop-up

_"You do not have a valid subscription for this server._
_Please visit www.proxmox.com to get a list of available options."_

This banner pops up because Proxmox wants you to purchase a support license.
To fix this, I followed the instruction provide in the video
"[Proxmox VE 7: Remove No Subscription Dialog on Login][16]"
(see text version [here][18]).

Click on **pve-1** > **Shell**
or via terminal `ssh root@192.168.1.202`
and enter the commands below:

```bash
#change to working directory
cd /usr/share/javascript/proxmox-widget-toolkit

# make a backup
cp proxmoxlib.js proxmoxlib.js.bak

# edit the file proxmoxlib.js
# search for “No valid subscription”
Ext.Msg.show({
  title: gettext('No valid subscription'),

# replace “Ext.Msg.show” with “void”
void({ //Ext.Msg.show({
  title: gettext('No valid subscription'),

# restart the proxmox web service, also may need to clear your browser cache
systemctl restart pveproxy.service

# check to see the service is active
systemctl status pveproxy.service
```

Now go to the Proxmox GUI, logout, reload the webpage via the browser, and log back in.
With this, you should no longer see the warning banner about having a subscription.

#### Step X: Increase Disk Storage - DONE
If you checkout how storage is allocated on `pve-1` via
**Datacenter** > **pve-1** > **local-lvm** and **local**,
you see that you have 70GB and 31GB of storage respectively.
You can combine this storage by following the instructions below.

Following the [recommendations of NetworkChuck][14] (at the 14:45 minute mark),
remove the `local-lvm` storage from Proxmox via
**Datacenter** > **Storage** > **local-lvm** > **Remove**.

Next, you want to reclaim this released storage space via
**Datacenter** > **pve-1** > **Shell**.
Using the shell window, enter the following commands:

```bash
# remove the data volume
$ lvremove /dev/pve/data
Do you really want to remove active logical volume pve/data? [y/n]: y
  Logical volume "data" successfully removed

# resize a logical volume (aka make it zero)
$ lvresize -l +100%FREE /dev/pve/root
  Size of logical volume pve/root changed from 29.50 GiB (7552 extents) to <111.74 GiB (28605 extents).
  Logical volume pve/root successfully resized.

# resize the file system
$ resize2fs /dev/mapper/pve-root
resize2fs 1.46.2 (28-Feb-2021)
Filesystem at /dev/mapper/pve-root is mounted on /; on-line resizing required
old_desc_blocks = 4, new_desc_blocks = 14
The filesystem on /dev/mapper/pve-root is now 29291520 (4k) blocks long.
```

To check for success in this realocation of storage,
goto **Datacenter** > **pve-1** > **local(pve-1)** > **Summary**.
This reallocates disk space giving a total of 118G for use with virtual machines
(increased from 31G)

#### Step X: Set Type of Storage Objects Permitted - DONE
Next, you need to specify what type of content allowed within the disk space storage.
You'll want to include disk images and containers, at a minimum.
**Datacenter** > **Storage** > **local** > **Edit**.
When the form pops up,
highlight **Disk image** and **Container** within the Content field,
then click **OK**.

#### Step X: Change to IP Address, Hostname, FQDN, and DNS - DONE
Proxmox uses the `hostname` as a nodes name,
so changing it works similar to changing the host name.
To rename a Proxmox host, you need to edit the following files:
`/etc/hosts` and `/etc/hostname`.
**NOTE:** This must be done on a empty node.

In my case, the hostname is `pve` and I wish to change it to `pve-1`.
The FQDN is `pve.fios-router.home` and I wish to change it to `pve-1.jeffskinnerbox.me`.
Here are the scripts to do this.

```bash
hostnamectl set-hostname pev-1.jeffskinnerbox.me

# update /etc/hosts file with host name
sed -i 's/pve/pve-1/g' /etc/hosts
sed -i 's/fios-router.home/jeffskinnerbox.me/g' /etc/hosts

# update the ip address (illustrative)
sed -i 's/192.168.1.XXX/192.168.1.ZZZ/g' /etc/hosts

# do the same for the /etc/hostname file
sed -i 's/pve/pve-1/g' /etc/hostname
```

If you wish to change the DNS,
its easy to do that within the Proxmox GUI.
Select **Datacenter** > **pve-1** > **DNS** and click on the **Edit** button.

If your node is in a cluster,
where it is not recommended to change its name,
adapt `/etc/pve/corosync.conf` so that the nodes name is changed also there.
See [here][31] for more information.

To make the update, follow the procedure below:

* [Renaming a PVE node](https://pve.proxmox.com/wiki/Renaming_a_PVE_node)
* [How to change hostname on Debian 10 Linux](https://www.cyberciti.biz/faq/how-to-change-hostname-on-debian-10-linux/)
* [Change PVE's static IP address, hostname and domain](https://www.reddit.com/r/Proxmox/comments/k4e3dx/change_pves_static_ip_address_hostname_and_domain/)

#### Step X: Download Some ISO Images - DONE
To create virtual machines,
you'll need to have move an ISO image to the Proxmox file system.
You can do this via
**Datacenter** > **local** > **ISO Images** > **Upload** or **Download from URL**.

A good set of ISO images to experiment with are:

* Ubuntu OS Variants
    * [xubuntu-20.04.3-desktop-amd64.iso](https://xubuntu.org/download/) - 1.5GB
    * [lubuntu-20.04.3-desktop-amd64.iso](https://lubuntu.me/downloads/) - 1.9GB
    * [ubuntu-20.04.3-live-server-amd64.iso](https://ubuntu.com/download/server) - 1.3GB
    * [fossapup64-9.5.iso](https://puppylinux.com/index.html#download) - 429MB
    * [lxle-18043-64.iso](https://lxle.net/download/) - 1.3GB
* Debian OS
    * [turnkey-core-17.0rc1-bullseye-amd64.iso](https://www.turnkeylinux.org/core) - 359MB
    (also see Proxmox container template 'turnkey-core')
* Other OS
    * [linuxmint-20.3-xfce-64bit.iso](https://linuxmint.com/edition.php?id=294) - 2.1GB
    * [archlinux-2022.02.01-x86_64.iso](http://mirror.rackspace.com/archlinux/iso/2022.02.01/archlinux-2022.02.01-x86_64.iso) - 852MB
    * [alpine-extended-3.15.0-x86_64.iso](https://alpinelinux.org/downloads/) - 690MB
    * [CentOS-8.5.2111-x86_64-boot.iso](http://mirrors.advancedhosters.com/centos/8.5.2111/isos/x86_64/) - 827MB
    * [windows-10-pro-020120.iso](https://www.microsoft.com/en-us/software-download/windows10ISO) - 5.3GB
* Applications
    * [pfSense-CE-2.6.0-RELEASE-amd64.iso](https://www.pfsense.org/download/) - 768MB
    * [pfSense-CE-2.5.2-RELEASE-amd64.iso](https://www.pfsense.org/download/) - 652MB
    * [kali-linux-2021.4a-installer-amd64.iso](https://www.kali.org/get-kali/#kali-bare-metal) - 3.1GB

There is a quicker way (sometimes) to load ISOs into Proxmox.
This can be done by do the following using a terminal (via `ssh root@192.168.1.202`)
or via **Datacenter** > **pev-1** > **Shell**:

```bash
# change directory to where the iso will be stored
cd /var/lib/vz/template/iso

# download using the url for the iso
wget http://mirror.rackspace.com/archlinux/iso/2022.02.01/archlinux-2022.02.01-x86_64.iso
wget https://mirror.us.leaseweb.net/ubuntu-cdimage/xubuntu/releases/20.04/release/xubuntu-20.04.4-desktop-amd64.iso
```

Once an ISO has ben downloaded, to create a VM,
simply click on **Create VM** and follow the prompts.

#### Step X: Download Some LXC Containers - DONE
Proxmox uses [Linux Containers (LXC)][32] as its underlying container technology.
Proxmox's primary goal is to offer containers that provides the benefits of using a VM,
but without the additional overhead.
This means that Proxmox Containers can be categorized as
[“System Containers”, rather than “Application Containers”][33].
Docker is widely used to package applications and services.

Proxmox container images, sometimes also referred to as “templates” or “appliances”,
are tar archives which contain everything to run a container.
Images/templates can be downloaded using the Proxmox GUI
or the commandline tool `pveam` (short for Proxmox VE Appliance Manager).
Pre-installed templates are available for mail gateways, system OS, and appliances from [Turnkey Linux][34].
Turnkey Linux is an open source project developing a free virtual appliance library that features the very best server-oriented open source software. Each virtual appliance is optimized for ease of use and can be deployed in just a few minutes on bare metal, a virtual machine and in the cloud.

The list of available templates is updated daily by Proxmox.
You can also trigger an update manually using `pveam`:

```bash
# update templates manually
pveam update

# list of available templates
pveam available

# List of available system templates
pveam available --section system

# list templates that have been downloaded
pveam list local
```

Before Proxmox can use a template, you need to download them into your storage.
You can do this via the GUI or commandline:

```bash
# example download of a template
pveam download local debian-10.0-standard_10.0-1_amd64.tar.gz
```

You can also create your own Proxmox containers.
See the following:

* [A sysadmin's guide to containers: What you need to know to understand how containers work](https://opensource.com/article/18/8/sysadmins-guide-containers)
* [Containers are Linux](https://www.redhat.com/en/blog/containers-are-linux)
* [Container Basics](https://www.sdxcentral.com/containers/definitions/containers-basics-update/)
* [6 container concepts you need to understand](https://opensource.com/article/20/12/containers-101)
* [Linux Container](https://pve.proxmox.com/wiki/Linux_Container)
* [Proxmox Creating an LXC Container](https://www.youtube.com/watch?v=h8qEXBp--WU)

Browse the container templates currently installed on Proxmox via
**Datacenter** > **pve-1** > **local (pve-1)** > **CT Templates** > **Templates**.

A good set of container templates to experiment with are:

* apline-3.14-default - 2.5MB
* ubuntu-20.04-standard - 214MB
* turnkey-wireguard - 262MB
* turnkey-openvpn - 208MB
* turnkey-ansible - 582MB

Once downloaded, to create a container,
simply click on **Create CT** and follow the prompts.

#### Step X: Enable Root SSH into a Proxmox LXC Container
By default a Proxmox LXC container allows root login only with public key authentication.
To login to a container with username/password login to your Proxmox host
and attach to the container with the following command.

Edit the ssh configuration file `/etc/ssh/sshd_config`
changing the line `PermitRootLogin without-password` to
`PermitRootLogin yes`.
Restart the ssh service via `service ssh restart` and check its status with `service ssh status`.
You should now be able to login to the container from ouside the console with `ssh root@<container>`.

Source:

* [SSH into a Proxmox LXC container](https://www.wissenschaft.com.ng/blog/ssh-into-a-proxmox-lxc-container/)

#### Step X: Secure Proxmox With A SSL Certificate
* [Secure Proxmox With A Proxmox SSL Certificate](https://blog.f2h.cloud/secure-proxmox-with-a-proxmox-ssl-certificate/)

#### Step X: Setup DHCP to Assign IP to Guest VM
Is this needed? Doesn't the Bridge do this?

* [How To Setup A Proxmox DHCP Server To Assign IPs To Guests](https://blog.f2h.cloud/proxmox-dhcp-server/)

#### Step X: Install Monitoring Tools - Netdata & Munin
* [Better Monitoring For Proxmox - Easy, Free And Awesome!](https://www.youtube.com/watch?v=fYl5poBJtE4)


-----



# Create Your First VM in Proxmox

## Create pfSense VM in Proxmox
* [Virtualizing with Proxmox VE](https://docs.netgate.com/pfsense/en/latest/recipes/virtualize-proxmox-ve.html)

## Create Windows 10 VM in Proxmox
* [Launching a Windows VM in Proxmox](https://www.youtube.com/watch?v=eyNlGAzf-L4)

#### Step X: Create a VM Using ISO Images
Once an ISO has ben downloaded, to create a VM,
simply click on **Create VM** and follow the prompts.

#### Step X: Remove VM or CT from Proxmox
To remove a VM from Poxmox, do the following:
**Click on VM or CT** > **Shutdown** > **More** > **Remove**

* [Proxmox - Remove VM](https://www.youtube.com/watch?v=DmI19Q8Lz-s)
* [Remove Node from Proxmox Cluster](https://tweenpath.net/remove-node-proxmox-cluster/)



-----



# Create Your First LXC Container
Often, when you hear "containers" you think of Docker but [containerization has a much longer history][21].
In fact, there are several kinds of container technologies that you can use.
There are Docker containers, Kubernetes containers, and Linux containers (LXC), just to name a few.

When you create a container in Proxmox, its a [Linux Containers (LXC)][19].
LXC is an operating-system-level virtualization method for running multiple
isolated Linux systems on a control host using a single Linux kernel, requiring no hardware emulation.
LXC's are more like an enhanced [chroot][20] than to full virtualization like QEMU or VMware.

Some would claim that the [Docker container technology is superior to LXC][22]
but under closer inspection, you could say [LXC & Docker are addressing different use cases][23].
This should not be a concern since you can use both LXC and Docker within Proxmox,
as illustrated in the example below.

* [Build your own container on Linux](https://opensource.com/article/22/2/build-your-own-container-linux-buildah)
* [Proxmox Creating an LXC Container](https://www.youtube.com/watch?v=h8qEXBp--WU)
* [LXC vs Docker & LXC 101](https://medium.com/@harsh.manvar111/lxc-vs-docker-lxc-101-bd49db95933a)
* [LXC vs LXD vs Docker – Evolution of the Container Ecosystem](https://www.devonblog.com/continuous-delivery/lxc-vs-lxd-vs-docker-evolution-of-the-container-ecosystem/)
* [Difference Between LXC and Docker][23]




-----




# Docker Containers on Proxmox
There are at least three different ways for running Docker containers on Proxmox.
You can do it via:

1. Directly on the underlying Proxmox OS - This is not really "in Proxmox" but outside it
and give you none of the advantages of the Proxmox hypervisor
(see "[Installing Docker and Portainer on Proxmox][36]")
2. Within a Ubuntu virtual machine (VM) - This will work but you have the overhead of the VM.
3. Within a LXC container - Docker & Portainer in an LXC container, this is a light weight approach
(see the "Sources" below).

In the steps below, I'll be using method 3 listed above.
I'll use a container template available from [Turnkey Linux][34].
Turnkey Linux is an open source project developing a free virtual appliance library
that features well respected server-oriented open source software.
Each virtual appliance is optimized for ease of use and can be deployed in just a few minutes on bare metal,
a virtual machine, or in the cloud.

Sources:

* [Docker in Proxmox LXC with Turnkey Core - Lower Resources by 80% Compared to VMs][37]
* [Running Docker under LXC Containers in ProxMox for Extra Granularization](https://www.youtube.com/watch?v=faoIeeZZ6ws)
* [Home Server: Installing Docker, Portainer & Home-Assistant on Proxmox][39]

## Install Docker

#### Step X: Using Docker Containers
If you want to run application containers, for example, Docker images,
Proxmox recommended that you run them inside a Proxmox Qemu VM.
This will give you all the advantages of application containerization, while also providing the benefits that VMs offer, such as strong isolation from the host and the ability to live-migrate, which otherwise isn’t possible with containers.

* [Install Proxmox and a Ubuntu VM with Portainer to manage docker containers](https://gist.github.com/zenxedo/626275e095f7f90898944a85d66b3be6)

#### Step X: Create Turnkey Core LXC Container - DONE
Select the Proxmox storage icon, **local (pre-1)**, on the lefthand menu.
Select **CT Templates** >  **Templates** > search for "turnkey-core"
(or "debian-11-standard") and download it.

Now we create the container by selecting the
**pre-1** > **Create CT**.
Within the Create: LXC Container wizard,
**Hostname** set to "docker-containers"
**Password** will be the password used on the commandline interface
make sure "Unprivileged container" unchecked
choose from the Template screen the Turnkey-core or  template
give the container 8GB of disk space (this can be adjusted later, if needed)
give it 2 CPU cores (this can be adjusted later, if needed)
give it 2048MB of ram & 512MB of swap (this can be adjusted later, if needed)
check **Bridge:** to "vmbr1" since it needs to be on my pfSense LAN
leave the DNS settings as the host
give it DHCP IP address allocation
Do not check **Start after created** and then click **Finish**

Next go to **Options** > **Features** > check the boxes for "keyctl" and "Nesting".
Then reboot the container to make sure the features are applied.

>**NOTE:** Unprivileged containers are when the container is created
>and run as a user as opposed to the root.
>This is the safest way to use a container,
>because if the container security gets compromised and the intruder breaks out of the container,
>they will find themselves as a nobody user with extremely limited privileges.

#### Step X: Update the Containers OS - DONE
Next we'll login to the LXC/docker container and update the OS.

Go to **201 (docker-containers)** > **Console**
and login as root.
You get a menu box and select **<Skip>** for the first two boxes.
On the third box, select **<Install>** and when the install is finished, enter **Ctrl-C**.

Now enter the following at the console CLI:

```bash
# update the os with latest software
apt-get update && apt-get -y upgrade
```

#### Step X: Install Docker and Docker Compose - DONE
To install Docker we'll use the instructions for Debian provided by Docker Docs found [here][38].

```bash
# install required perquisites
apt-get -y install ca-certificates curl lsb-release apt-transport-https gnupg2 software-properties-common

# add docker’s official gpg key
mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg

# set up the repository
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null

# install docker engine and docker compose
apt-get update
apt-get -y install docker-ce docker-ce-cli containerd.io docker-compose-plugin

# check status docker daemon
systemctl status docker

# check that docker is functioning properly
docker run hello-world

# check if hello-world is running
docker ps -a -s
```

>**NOTE:** Receiving a GPG error when running apt-get update?
>Your default umask may not be set correctly,
>causing the public key file for the repo to not be detected.
>Run the following command and then try to update your repo again:
>`sudo chmod a+r /etc/apt/keyrings/docker.gpg`.

## Install Portainer
Adopting container orchestration platforms like Kubernetes can be hard.
[Portainer][42] is a popular Docker UI that helps you visualise your
containers, images, volumes and networks.
Portainer helps you centrally configure, manage and secure containerized environments,
regardless of where they are hosted.
It helps you take control of the Docker resources on your machine, avoiding lengthy terminal commands.

Portainer can be deployed to Docker, Docker Swarm, or Kubernetes environments
and comprised of two elements: the Portainer Server, and the Portainer Agent.
I going to deploy Portainer via Docker below.

Sources:

* [Deploying Portainer CE in Docker](https://documentation.portainer.io/v2.0/deploy/ceinstalldocker/)
* [How to Install Portainer Docker UI Manager on Ubuntu 20.04 | 18.04 | 16.04](https://docs.fuga.cloud/how-to-install-portainer-docker-ui-manager-on-ubuntu-20.04-18.04-16.04)
* [How to Install Portainer 2.0 on your Docker](https://www.letscloud.io/community/how-to-install-portainer)

#### Step 1: Portainer Server Deployment - DONE
Use the following Docker commands to deploy the Portainer Server.

```bash
# create the volume for storing persistent data
docker volume create portainer_data

# install the portainer container (ports 8000 is for agents and 9000 for web ui)
docker run -d -p 8000:8000 -p 9000:9000 -p 9443:9443 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest

# check if portainer is running
docker ps -a -s
```

Now using your browser, you can log into Portainer via this URL: `<ip address on home LAN>:9000`.
I got the IP address via  running `ip address | grep "inet 192"`
which was `192.168.1.69` in my case.
on the Proxmox console for `docker-containers`.

#### Step 2: Portainer Agent Deployment
Use the following Docker commands to deploy the Portainer Agent.
Agents are installed on Docker nodes being managed remotely by Portainer.
The agent is not needed on standalone hosts,
however it does provide additional functionality if used:

```bash
# install the portainer agent container
docker run -d -p 9001:9001 --name portainer-agent --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /var/lib/docker/volumes:/var/lib/docker/volumes portainer/agent
```

#### Step 3: Manage Proxmox Docker Containers via Desktop Portainer
We now want to connect the Proxmox based `docker-containers` so it can be monitored
and managed from my `desktop` Portainer.
This is enabled by the Portainer Agent we install in the previous step.

* To connect your `docker-containers` Portainer Agent,
you do the following on your `desktop` Portainer.
* Select **Environments** from the lefthand menu.
* Select the **Add envirnment** button at top left.
* Select **Agent** and for **Name** enter "firewall / router",
for **Environment URL** enter `192.168.1.69:9001`
for **Public IP** enter `192.168.1.69:9001`
* Select **Add environment** at the bottom left of the page.

Now if you select **Home** from the lefthand main menu,
you'll see both your local docker containers and the ones on Proxmox where my router / firewall (aka pfSense) is hosted.

Source:

* [Installing Portainer and Portainer Agent - An update to show you an easier way to manage Docker](https://www.youtube.com/watch?v=-LPaWq1_GF0)
* [Add ALL of your Docker Hosts to ONE Portainer Dashboard Using the Portainer Edge Agent](https://www.youtube.com/watch?v=8YmQoQ7gAg8)



-----


# Docker Container for Uptime Kuma
* [GET NOTIFIED of an outage in your home lab or anywhere with Uptime Kuma and Home Assistant](https://www.youtube.com/watch?v=BNiWDNfqpc0)



-----



# Proxmox Upgrade
* [Before you upgrade to Proxmox 7, please consider this...](https://www.youtube.com/watch?v=RCSp6gT7LWs)
* [Updating Proxmox](https://www.youtube.com/watch?v=ICtiaW2ypT0&list=RDCMUC05NSijsZpNM_mbd0-qagLA&index=40)



-----



# Proxmox Security Features
* [Proxmox VE 7.1 Security Deep Dive](https://www.storagereview.com/review/proxmox-ve-7-1-security-deep-dive)

# Proxmox Cluster / Hyperconverged Storage
A minimum of two nodes are required to form a Proxmox cluster.

Using a bare metal cloud provider to create a cluster
* [Building a 5-node Proxmox VE Cluster in 20 Minutes for a Dollar](https://www.servethehome.com/building-5-node-proxmox-ve-cluster-20-minutes-dollar-phoenixnap-intel-supermicro/)

Illustrates how to run several Proxmox instances as a cluster with Ceph hyperconverged storage
* [Proxmox Install - The Best Free Hypervisor of 2021](https://www.youtube.com/watch?v=FwD93E4Jijk)

Complete guide on getting your cluster up and running
* [Building a Proxmox VE Lab Part 1 Planning](https://www.servethehome.com/building-a-proxmox-ve-lab-part-1-planning/)
* [Building a Proxmox VE Lab Part 2 Deploying](https://www.servethehome.com/building-a-proxmox-ve-lab-part-2-deploying/)
* [LOW Power / HIGH Availability Proxmox Cluster ft. ZimaBoard](https://www.youtube.com/watch?v=JfZuZ6zE7AI)
* [Setting Up My First Proxmox High Availability Cluster](https://www.youtube.com/watch?v=FZnVmt_DvUk)

# Proxmox Backup Server
Proxmox Backup Server is an enterprise backup solution that allows you to back up and restore virtual machines (VMs), containers, and physical hosts. Proxmox Backup Server supports incremental and deduplicated backups, which is a fancy way of saying that the storage space will be optimized and the same files won’t be stored twice. This helps to conserve hard drive space on the device running Proxmox Backup Server.

Proxmox Backup Server can be run in a Proxmox host, though it’s probably a good idea to install it on bare metal on a separate server (or at least a separate Proxmox server). This way, you have your Proxmox hypervisor backing up to your Proxmox Backup Server.

* [Backup Proxmox VE VMs Quickly and Easily](https://www.servethehome.com/backup-proxmox-ve-vms-quickly-and-easily/)
* [Getting Started With Proxmox Backup Server](https://ostechnix.com/getting-started-with-proxmox-backup-server/)
* [How To Install Proxmox Backup Server Step by Step](https://ostechnix.com/install-proxmox-backup-server/)
* [How to Set Up Proxmox Backup Server](https://www.wundertech.net/how-to-set-up-proxmox-backup-server/)
* [How to Backup Proxmox to a Synology NAS](https://www.wundertech.net/how-to-backup-proxmox-to-a-synology-nas/)

* [Proxmox Backup Server 2.0 - Install and Config](https://www.youtube.com/watch?v=AYQUoitoBtU)
* [Proxmox Backup Server: Full Getting Started Guide!](https://www.youtube.com/watch?v=33ubleU4OFc)
* [Proxmox Backup Server Install Tutorial](https://www.youtube.com/watch?v=jLBNm0fNIog)

## Proxmox Backup Server on Synology
* [Setting Up a Proxmox Backup Server](https://www.youtube.com/watch?v=n_JZ2aXMMmI)
* [How to Backup Proxmox to a Synology NAS](https://www.wundertech.net/how-to-backup-proxmox-to-a-synology-nas/)

# Proxmox VM Migration
* [ProxMox - Migration, Backup, and Restoration Tutorial](https://www.youtube.com/watch?v=BkVi2vRB75Q)



-----



# How to do Proxmox Networking
Proxmox network configuration can be done either via the GUI,
or by manually editing the file `/etc/network/interfaces`,
which contains the whole network configuration.
Using the GUI is still preferable, because it protects you from errors
but not all networking configuratiosn can be done via the GUI.

Proxmox VE does not write changes directly to the interfaces file `/etc/network/interfaces`.
Instead, instead it writesto a temporary file called `/etc/network/interfaces.new`.
This way you can do many related changes at once and you can ensure your changes are correct before applying.

Proxmox uses the following naming conventions for network devices
(see [here][04] for more details):

* Ethernet devices: `en*` are `systemd` network interface names.
* Bridge names: `vmbr[N]`, where 0 ≤ N ≤ 4094 (e.g. `vmbr0` - `vmbr4094`)
* Bonds: `bond[N]`, where 0 ≤ N (e.g. `bond0`, `bond1`, …)
* VLANs: Simply add the VLAN number to the device name, separated by a period (e.g. `eno1.50`, `bond1.30`)

Proxmox bridges are like physical network switches implemented in software.
All virtual guests can share a single bridge, or you can create multiple bridges to separate network domains.
Each host can have up to 4094 bridges.

Proxmox establishes a default bridge, named `vmbr0`,
during the installation process for Proxmox itself.
This default bridge is connected to the first Ethernet card.
For Protectli Vault, this Ethernet card services the WAN interface and is `enp1s0`.
**NOTE:** When the WAN port is used for interfacing the Internet,
typical for the Protectli Vault,
this means any VM or CT on this default bridge `vmbr0` is nakedly exposed to the Internet.
**You have been warned!**

If the WAN interface on the Protectli Vault is Internet facing,
Proxmox uses the default bridge `vmbr0` to provide Internet access to VMs,
but you'll need a public IP for each machine.
Virtual machines (VM) and containers (CT) behave as if they were directly connected to the physical network.
The network, in turn, sees each VM/CT as having its own MAC,
even though there is only one network cable connecting all of these VMs to the network.

If you are limited to one public IP address,
you can create a private bridge network use NAT to access Internet for your VMs.

* [Configuring Proxmox Basic Promox Network Settings](https://www.youtube.com/watch?v=acrZzXn6P8s)
* [How to setup NAT on Proxmox](https://cyberpersons.com/2016/07/27/setup-nat-proxmox/)

## Types of Proxmox Networks
* Linux Bridge – a method of connecting two Ethernet segments at the link layer, that is, without using higher-layer protocols such as IP. Since transmission is performed at the data link layer (layer 2 of the OSI model), all higher-layer protocols are transparently bridged.
* Linux Bond – a method of aggregating several network interfaces into a single logical bonded interface. Thus, bond provides load balancing or hot standby for a specific scenario.
* Linux VLAN – implementation on the Linux kernel of a virtual local computer network.
* OVS Bridge – implementation of the bridge based on Open vSwitch.
* OVS Bond – implementation of balancing based on Open vSwitch. Differs from the mode balancing implemented in the Linux kernel.
* OVS IntPort – VLAN implementation based on Open vSwitch.

* [HowTo: Proxmox Networking](https://www.flomain.de/2015/05/how-to-proxmox-networking/)
* [Proxmox VE (PVE) default network settings & autostart, bridge, bond, basics about PVE network etc.](https://dannyda.com/2021/10/29/proxmox-ve-pve-default-network-settings-autostart-bridge-bond-basics-about-pve-network-etc/)
* [How to do Network setup in Proxmox](https://webilicious.xyz/how-to-do-network-setup-in-proxmox-webilicious/)
* [How to: Create an internal only/isolated network for guest OS/Virtual Machines (VM) on Proxmox VE (PVE) like in VMware Workstation (Host-Only network but different)](https://dannyda.com/2020/06/01/how-to-create-an-internal-only-isolated-network-for-guest-os-virtual-machines-vm-on-proxmox-ve-pve-like-in-vmware-workstation-host-only-network-but-different/)

## linux Bridge vs OVS Bridge
The Linux bridge is software that acts as a virtual Ethernet switch.
This “bridges” the virtual network interfaces for each Virtual Machine
and the physical network interface card.
This software is installed automatically due to being part of the Linux kernel.

The simplicity of the Linux Bridge does come with some drawbacks.
Most notably, as one of the older solutions to this network problem,
it does not incorporate the currently known best practices for ensuring high performance software bridging.

Open vSwitch (aka OVS Bridge) provides an alternative to the standard built-in Linux bridge
and can be used with many different operating systems and virtualization platforms.
Some claim using Open vSwitch instead of Linux bridge brings with it noticeably increases in performance and stability.
That said, if you're not doing multi-gigabit than it probably doesn't matter.

Also consider that Open vSwitch supports most of the features you would find on a physical switch.
Advanced features like RSTP support, VXLANs, OpenFlow, and supports multiple VLANs on a single bridge.
If you need these features, it makes sense to switch to Open vSwitch.

* [Linux Bridge vs OpenVSwitch — How to Improve Virtualization Network Performance](https://ioflood.com/blog/2021/07/08/linux-bridge-vs-openvswitch-how-to-improve-virtualization-network-performance/)
* [Proxmox VE with Open vSwitch](https://www.networkshinobi.com/proxmox-ve-with-open-vswitch/)
* [Virtualised pfSense on Proxmox with Open vSwitch](https://webworxshop.com/virtualised-pfsense-on-proxmox-with-open-vswitch/)

## Proxmox Private vs Public Networks
* [How do I make my VMs accessible via a bridge?](https://faq.myloc.de/index.php?action=faq&cat=23&id=202&artlang=en)

### How To Configure A Proxmox Private Network
* [How To Configure A Proxmox Private Network](https://blog.f2h.cloud/how-to-configure-a-proxmox-private-network/)
* [How to: Create an internal only/isolated network for guest OS/Virtual Machines (VM) on Proxmox VE (PVE) like in VMware Workstation (Host-Only network but different)](https://dannyda.com/2020/06/01/how-to-create-an-internal-only-isolated-network-for-guest-os-virtual-machines-vm-on-proxmox-ve-pve-like-in-vmware-workstation-host-only-network-but-different/)

### How To Configure A Proxmox Public Network
* [How to Connect a VM to the Internet Using Proxmox VE](https://support.us.ovhcloud.com/hc/en-us/articles/360002394324-How-to-Connect-a-VM-to-the-Internet-Using-Proxmox-VE)

## Proxmox with Single Public IP and Shared with VMs
* [How to setup Proxmox with Single Public IP and share with VMs](https://www.youtube.com/watch?v=Q5l7VH6b5r4)

## How to Setup NAT on Proxmox
* [PVE 6.2 Private VM (NAT) network configuration setup](https://forum.proxmox.com/threads/pve-6-2-private-vm-nat-network-configuration-setup.71038/)
* [How to setup NAT on Proxmox](https://cyberpersons.com/2016/07/27/setup-nat-proxmox/)
* [How do I make my vServer reachable via an additional IP or NAT?](https://faq.myloc.de/?action=faq&cat=23&id=205&artlang=en)
* [Create Private Network Bridge on Proxmox VE with NAT](https://computingforgeeks.com/create-private-network-bridge-proxmox-with-nat/)



-----



# Proxmox Networking Best Practices
[best practice][05]
[Network Configuration][06]

## NAT & IP Masquerade
Most private networks are connected to the Internet through a firewall.
Internal computer are computers on the private network
and computers on the Internet are defined as external computers.
External and internal computers communicate with each other through the firewall,
but the firewall are setup to **note** transmit the private IP addresses on the Internet.
The firewall must substitute a valid private IP address to an Internet IP address and visa versa.
There are two techniques to accomplish this substitution:
[Network Address Translation (NAT) and IP Masquerade][40].

To make this all the more challenging,
for the two different address translation methods,
the term NAT is often used for IP Masquerade but
IP Masquerade is typically what is being used.
You might also see terms like “one-to-many NAT”
or “multipoint NAT” used instead of IP Masquerade.

Basically, NAT make use of a reusable pool of IP addresses for translation,
where IP Masquerade uses a pool of ports to support translation.
NAT is a one-to-one system, meaning that each private IP address
must be mapped to exactly one Internet IP address
and the available private IP addresses can quickly exhaust.
For IP Masquerade, there are many more ports that can be used
but it can run into a bottle neck if the external computer
attempts to open multiple IP connections to a single internal computer.

IP Masquerade overcomes this problem using a technique called [Port Forwarding][41].
Using Port Forwarding, you may program the IP Masquerade module
to forward any segments destined for a specific port on the firewall
to a port on a computer in the private network.

* [Network Address Translation (NAT) and IP Masquerade][40].
* [Linux Network Administrator's Guide, 2nd Edition: IP Masquerade and Network Address Translation](https://www.oreilly.com/openbook/linag2/book/ch11.html)

## Create a VM on Proxmox Private Network with Internet Access
In the scenario here,
we are using the Proxmox default public network (`vmbr0`)
as our gateway to the Internet.
There is an alternatively scenario where you establish

 This is useful if you do not have any public IPs.
A Proxmox private network (i.e. internal network with no WAN interface)
allows you to assign an internal IP to VMs and Containers.
This could be static IPs, or as done here, you could setup a DHCP server within this network.
In this configuration, we will

* The bridge `vmbr0` can route to the physical NIC (`enp1s0`) on Proxmox,
which can reach the public network (aka Internet).
* We will configure a private network (`vmbr1` with `10.10.10.0/24` as its network).
* We will then install a DHCP server on that private network (with IP address `10.10.10.1`).
* Next we configure the private network to allow VMs/CTs to access the Internet
using Proxmox's gateway on the Proxmox host (gateway at `192.168.1.1`).
* As a final step, we'll install a VM on the private network we created
and validate that it can reach the public network.

Let’s configure a private network on `vmbr1` which includes `10.10.10.1` for the address.
There is a DHCP server running on 10.10.10.1 and we forward all connections from the 10.10.10.0/24 subnet to the ethernet device on our server. This allows for outgoing connections on guests

* [How To Configure A Proxmox Private Network](https://blog.f2h.cloud/how-to-configure-a-proxmox-private-network/)

#### Step X: Create the Private Network
Within Proxmox,
Navigate to **Datacenter** > **pve-1** > **System** > **Network**.
Click on **Create** button, click on **Linux Bridge**.
We only need to enter the desired IPv4/CIDR, and Comment information.
Enter the **IPv4/CIDR** `10.10.10.0/24`.

Source:
* [How to: Create an internal only/isolated network for guest OS/Virtual Machines (VM) on Proxmox VE (PVE)](https://dannyda.com/2020/06/01/how-to-create-an-internal-only-isolated-network-for-guest-os-virtual-machines-vm-on-proxmox-ve-pve-like-in-vmware-workstation-host-only-network-but-different/)

#### Step X: Add DHCP to the Private Network
First, do a `pveam update` in the Proxmox console to download the latest LXC template.
We are going to run our DHCP server in a container,
so click the **Datacenter** > **pve-1** > **Create CT** button.
Now fill the form with **Hostname** is `dhcp-server`,
**Password** of your choose,
**Template** is `ubuntu-20.04-standard_20.04-1_a`,
**Disk** is 8GB, **CPU** is 1, **Memory** and **Swap** is 512MB.

For the **Network** tab,
**Bridge** is the network we just created `vmbr1`,
and **IPv4/CIDR** we use `10.10.10.1/24`,
and **Gateway** we leave blank.
Also leave blank **DNS** tab and hit **Confirm**

Now well be doing something needed temporally.
We'll select the public network used by Proxmox
(aka `vmbr0` - the one created by Proxmox VE by default)
so we can download the DHCP package.
Click on the container we have just created,
click on **Network** > **Add**.
Name it **eth1**, make sure "DHCP" is selected for **IPv4**,
for **Bridge** we select a Public network `vmbr0`
(aka one with internet - usually the one created by Proxmox by default).
Click **Add**.

>**NOTE:** `eth1` is for downloading the necessary DHCP package,
>but once done we will remove it.
>This will assure the DHCP server will be in the Private Network only.

Now we **Start** the container,
open the **Console** for the container,
use the root we install necessary package for running as a DHCP server:

```bash
# update the package list and do an upgrade
apt update && apt upgrade -y

# install the dhcp package
apt install isc-dhcp-server -y

# power down the container
poweroff
```

Now we'll remove the temporary access to the Internet via `vmbr0`.
Click **Datacenter** > **pve-1** > **dhcp-server** > **Network**.
Select the one with **IP address** is "dhcp”, **Remove** it, and start the container again.

Now we will establish the DHCP server for our private network `vmbr1`.
Login to the container via **Console**
and following command to configure the DHCP server:

```bash
# name the dhcp server and provide a ip address for it
sed -i 's/option domain-name \"example.org\"/option domain-name \"mylab.lab\"/' /etc/dhcp/dhcpd.conf
sed -i 's/option domain-name-servers ns1.example.org, ns2.example.org/option domain-name-servers 10.10.10.1/' /etc/dhcp/dhcpd.conf

# uncomment authoritative
sed -i 's/#authoritative/authoritative/' /etc/dhcp/dhcpd.conf

# dhcp range is 10.10.10.10 to 10.10.10.199
cat <<EOT >>  /etc/dhcp/dhcpd.conf

# dhcp range
subnet 10.10.10.0 netmask 255.255.255.0 {
range 10.10.10.10 10.10.10.199;
}
EOT

# restart the dhcp server
systemctl restart isc-dhcp-server.service

# status the dhcp server
systemctl status isc-dhcp-server.service
```

Now you can start the VMs and containers
and they will get IP addresses from the DHCP server.

We can also check for status on DHCP leases and other things:

```bash
# list the dhcp leases (should be no leases)
dhcp-lease-list

# check the status of iptables (should be no rules)
iptables -L -t nat -v -n  --line-numbers

# check ip address of the dhcp-server
ip address | grep inet

# ping test the dhcp-server (should be only 10.10.10.1)
ping 10.10.10.1
```

Source:
* [How I configure a DHCP server on my personal network](https://opensource.com/article/22/7/configure-dhcp-server)
* [How to: Create a VM Internal Only network with DHCP server on Proxmox VE (PVE) easily](https://dannyda.com/2020/06/06/how-to-create-a-vm-internal-only-network-with-dhcp-server-how-to-create-an-dhcp-server-on-proxmox-ve-pve-easily/)

#### Step X: Add NAT to the Private Network
## Proxmox VM Access the Internet Without a Public IP address
## Proxmox as a Hosting Provider and Single Public IP Address
You are likely to desire a Proxmox VM be able to ping/access Internet servers
without having to assign a public IP to your VM.
And of course, you want this to be as secure as possible.
How do I do this?

It is best practice to keep your VM/CT on a separate network from Proxmox (i.e. `vmbr0`).
Your going to want your VM/CT network to interface with the Internet,
so your going to need to access the WAN port (aka `enp1s0` interface).
You need to enable NAT networking to accomplish this.
To create a separate network, enable NAT networking mode,
edit the interfaces file `/etc/network/interfaces`
The interfaces file shows that `vmbr0` is the default bridge network for Proxmox,
as in the lines below:

```bash
auto lo
iface lo inet loopback

iface enp1s0 inet manual

iface enp2s0 inet manual

iface enp3s0 inet manual

iface enp4s0 inet manual

# bridge network interfacing (via enp1s0) with public network (aka internet)
auto vmbr0
iface vmbr0 inet static
    address 192.168.1.202/24
    gateway 192.168.1.1
    bridge-ports enp1s0
    bridge-stp off
    bridge-fd 0
```

Add the following content to the Proxmox file `/etc/network/interfaces`
to create the bridge network `vmbr1`:

```bash
# bridge network containing nat to public network
auto vmbr1
iface vmbr1 inet static
    address  10.10.10.1/24
    bridge_ports none
    bridge_stp off
    bridge_fd 0

    post-up echo 1 > /proc/sys/net/ipv4/ip_forward

    # change vmbr0 for your ethernet device which is displayed at the top of the interfaces
    post-up   iptables -t nat -A POSTROUTING -s '10.10.10.0/24' -o vmbr0 -j MASQUERADE
    post-down iptables -t nat -D POSTROUTING -s '10.10.10.0/24' -o vmbr0 -j MASQUERADE
```

Finally, restart the new interface with `ifdown vmbr1 && ifup vmbr1` in the Proxmox terminal.
Then check the status of the `iptables` and `vmbr1`:

```bash
# restart the interface
ifdown vmbr1 && ifup vmbr1

# check the status of iptables
iptables -L -t nat -v -n  --line-numbers

# check the status of the vmbr1 interface
ping 10.10.10.1
```

Next time you create a VM or CT,
`vmbr0` and `vmbr1` will be available for the bridge network option.
You should select `vmbr1` to keep the VM/CT on a separate network from Proxmox.
IP Masquerading adds some processing overhead
but this give you additional security & protection of Proxmox.

* vmbr0 : This is the interface that was already configured in your network file.
* vmbr1 : This is the bridge name for NAT.
* bridge_ports none : Bridge ports here is set to none, since we are not connecting to outside world directly.
* 192.168.1.0/24 : This will be the network we are going to use in our internal network, our usable ips in this network will be:
    * 192.168.1.2-192.168.1.254
    * If you plan to use different network, you can use this site to get help. - https://jodies.de/ipcalchttps://jodies.de/ipcalc

>**NOTE:** This is for my Protectli Vault / Proxmox settup,
>make sure to adjust the names `vmbr0`, etc. properly for your needs.

>**Note:** I did not use the same network for
>`vmbr0` (i.e. `192.168.1.0` and `vmbr1` (i.e. `10.10.10.0`).
>Do not assign two bridge interfaces IP addresses in the same network without anything like VLAN.
>If you do and we do an `arp` to get the MAC address,
>we will find out that both MAC addresses will send reply to that `arp`.
>If we set `vmbr0` tp `192.168.1.202/24` and `vmbr1` to `192.168.1.202/24`
>`arp` will get reply from both `vmbr0` and `vmbr1`,
>thus we should not set IP addresses in the same network/LAN for more than one bridge interface.

Checking status:

```bash
# check the status of iptables (should be no rules)
iptables -L -t nat -v -n  --line-numbers

# check ip address of the dhcp-server
# should be 10.10.10.10, the the first elagable IP for leasing from dhcp-server
ip address | grep inet

# ping test the this system & dhcp-server
ping 10.10.10.1
ping 10.10.10.10
```

If you happend to want to remove all the iptable rules,
do the following:

```bash
# dump all iptables rules onto screen
iptables-save

# purge all iptable rules and let everything in/out, no routing, no nat
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -t raw -F
iptables -t raw -X

# verify that firewall rules are flushed out
iptables -L -n -v -t nat
```

The `iptables` options mean the following:

* **-F**: Deleting (flushing) all the rules.
* **-P**: Set the default policy (such as DROP, REJECT, or ACCEPT).
* **-t table_name**: Select table (called nat or mangle) and delete/flush rules.
* **-X**: Delete chain.


* [How to setup Proxmox with Single Public IP and share with VMs](https://www.youtube.com/watch?v=Q5l7VH6b5r4)
* [How do I get my Proxmox VM to access the internet without a public IP address](https://serverfault.com/questions/440423/how-do-i-get-my-proxmox-vm-to-access-the-internet-without-a-public-ip-address)
* [Proxmox Wiki: Network Configuration](https://pve.proxmox.com/wiki/Network_Configuration)



-----


# Proxmox Server Hardening
Out of the box Proxmox does not have any Brute Force protection in the same way as some other virtualisation technologies do.
As such, for our proxmox servers we wanted to increase security on the two open ports: SSH port 80 & Web Portal port 8006 (The Proxmox Web Management Portal).

* [Proxmox: Potect your server with fail2ban](https://devopstales.github.io/linux/proxmox-fail2ban/)
* [Securing Proxmox and SSH using Fail2Ban](https://www.ukhost4u.com/securing-proxmox-and-ssh-using-fail2ban/)
* [Hardening Proxmox, some in one place](https://blog.samuel.domains/blog/security/hardening-proxmox-some-in-one-place)
* [proxmox Serverhardening: Part 1 – rpc](https://www.fu-solutions.de/en/2022/01/ulli/administration-en/proxmox-serverhardening-part-1-rpc/)
* [proxmox Serverhardening: Part 2 – fail2ban](https://www.fu-solutions.de/en/2022/04/ulli/administration-en/proxmox-serverhardening-part-2-fail2ban/)
* [How to Protect Your Server With Fail2Ban in Linux](https://www.maketecheasier.com/protect-ssh-server-with-fail2ban-ubuntu/)
* [How Fail2Ban Works to Protect Services on a Linux Server](https://www.digitalocean.com/community/tutorials/how-fail2ban-works-to-protect-services-on-a-linux-server)
* [Protect Web Servers from DDoS Attacks using Fail2ban](https://sysopstechnix.com/protect-web-servers-from-ddos-attacks-using-fail2ban/)

* [Fail2NetworkBan](https://github.com/modernham/Fail2NetworkBan)

* [Hardening Proxmox VE management interface with 2FA, reverse proxy and Let's Encrypt](https://loicpefferkorn.net/2020/11/hardening-proxmox-ve-management-interface-with-2fa-reverse-proxy-and-lets-encrypt/)


# Protecting the Web Server
Any web service endpoint exposed to the public Internet are particularly susceptible to many attacks by hackers.
In my case, the service is a website, where malicious users and bots
will attempt to break into the site, or shut it down,
by repeatedly sending requests, sometimes at with higher frequency.
I will attempt to mitigate these attacks using [Fail2ban][52]
and [Cloudflare Web Application Firewall (WAF)][53].
These security tools help shutdown malicious attacks on the website.

# Cloudflare Web Application Firewall (WAF)
Cloudflare runs one of the largest networks in the world
and one of their key services is [Distributed Denial-Of-Services (DDOS)][54] attack mitigation
Claudflare can handle most any DDOS attach automatically and without charge,
a policy which Cloudflare calls [Unmetered Mitigation][55].
They also provide a service called [Web Application Firewall (WAF)][56]

Cloudflare appears to provide some basic WAF protection automatically,
but you can provide some custom rules via the Cloudflare UI.
To do so, goto the Cloudflare main menu (left-side of the screen)
and select **Security** > **WAF**.
It is here you can provide some limited set of [custome WAF rules][57].

At this time, I have [addeded one custom rule][58]
(**NOTE:** this is the maximum number of rules for the free plan).
That rule will block IP addresses for 10 seconds that exceeding 150 requests within 10 seconds.
You can add rules via the main menu by selecting
**Security** > **WAF** and select from the tab **Rate limiting rules**.

# Fail2Ban
[Fail2ban][52] can also help protect a web server from brute force and Deny-Of-Services (DOS) attacks.
Instead of monitoring traffic like Cloudflare,
Fail2ban is configured to monitor the logs of a service.
It read the logs file and try to match suspsious patterns to actions to perform.
For example, Fail2ban analyzes the logs of the server and looks for several unsuccessful connection attempts.
It will put in place actions that you will block the IP address or send alert email

>**NOTE:**By default, action will be taken when 3 authentication failures have been detected in 10 minutes,
>and the default ban time is for 10 minutes.
>The default for number of authentication failures necessary to trigger a ban
>is overridden in the SSH portion of the default configuration file
>to allow for 6 failures before the ban takes place.
>This is entirely configurable by the administrator in the `jail.conf` file.

* [How Fail2Ban Works to Protect Services on a Linux Server](https://www.digitalocean.com/community/tutorials/how-fail2ban-works-to-protect-services-on-a-linux-server)
* [Protect Web Servers from DDoS Attacks using Fail2ban](https://sysopstechnix.com/protect-web-servers-from-ddos-attacks-using-fail2ban/)

```bash
# scan all ports (all 65536 ports) on router lan side
$ nmap -p- 192.168.1.1
Starting Nmap 7.80 ( https://nmap.org ) at 2023-03-22 15:16 EDT
Nmap scan report for pfSense.jeffskinnerbox.me (192.168.1.1)
Host is up (0.0032s latency).
Not shown: 65532 filtered ports
PORT    STATE SERVICE
53/tcp  open  domain
80/tcp  open  http
443/tcp open  https

Nmap done: 1 IP address (1 host up) scanned in 202.49 seconds

# get the router's extenal IP address
curl ipecho.net/plain ; echo ""
<ext_ip>

# scan all ports (all 65536 ports) on router - from the internet
$ nmap -p- <ext_ip>
Starting Nmap 7.80 ( https://nmap.org ) at 2023-03-22 15:29 EDT
Nmap scan report for pool-<ext_ip>.clppva.fios.verizon.net (<ext_ip>)
Host is up (0.0013s latency).
Not shown: 65532 filtered ports
PORT    STATE SERVICE
53/tcp  open  domain
80/tcp  open  http
443/tcp open  https

Nmap done: 1 IP address (1 host up) scanned in 197.74 seconds

# scan all ports (all 65536 ports) on cloudflare proxy wan side (aka internet)
$ nmap -Pn <cloudflare_ip>
Starting Nmap 7.80 ( https://nmap.org ) at 2023-03-22 15:45 EDT
Nmap scan report for pool-<cloudflare_ip>.clppva.fios.verizon.net (<cloudflare_ip>)
Host is up.
All 1000 scanned ports on pool-<cloudflare_ip>.clppva.fios.verizon.net (<cloudflare_ip>) are filtered

Nmap done: 1 IP address (1 host up) scanned in 201.45 seconds
```

From these set of IP scans, the only ports open are `53`, `80`, and `443` on the WAN side of my router.
Ports `80` & `433` are used for http/https web services (specifically the pfSense admin UI),
but since I'm using Cloudflare Tunnels for web services, I can close them.
As to port `53`, it must remain open to support DNS services





-----




# Proxmox Cluster
* [How do I create a cluster?](https://faq.myloc.de/?action=faq&cat=23&id=271&artlang=en)




-----



# Proxmox Template with Cloud Image and Cloud Init
Cloud Images are small images that are certified cloud ready that have Cloud Init preinstalled and ready to accept a Cloud Config

* **Cloud Images -
[Ubuntu Cloud Images](https://cloud-images.ubuntu.com/) pre-configured with Cloud Init
* **Cloud Templates -
* **Cloud Init - Cloud images are operating system templates and every instance starts out as an identical clone of every other instance. It is the user data that gives every cloud instance its personality and cloud-init is the tool that applies user data to your instances automatically.
You use cloud-init to configure:
(1) Setting a default locale, (2) Setting the hostname, (3) Generating and setting up SSH private keys, (4) Setting up ephemeral mount points

* [Use Proxmox Cloud-Init to Deploy Your Virtual Machines!](https://www.youtube.com/watch?v=Kv6-_--y5CM)
* [Perfect Proxmox Template with Cloud Image and Cloud Init](https://www.youtube.com/watch?v=shiIi38cJe4)
* [Setting up Cloud-INIT VM inside Proxmox | Proxmox Home Server Series | Proxmox Home Lab](https://www.youtube.com/watch?v=KweBabVHmYU)
* [Ubuntu Cloud-Init Technology](https://www.youtube.com/watch?v=-zL3BdbKyGY)



-----



# Proxmox Automation
Using VM Templates in Proxmox and Packer,
you can create custom machine images for Proxmox with provisioning shell scripts
and inject configuration settings via Cloud-Init.

* [Create VMs on Proxmox in Seconds!](https://www.youtube.com/watch?v=1nf3WOEFq1Y)



-----



# eMail Notification
* [Proxmox VE E-mail Notifications are Important](https://www.servethehome.com/proxmox-ve-e-mail-notifications-are-important/)


-----



# How to Rollback a Proxmox Kernel Update
* [How To Revert a Proxmox Kernel Update](https://engineerworkshop.com/blog/how-to-revert-a-proxmox-kernel-update/)


-----


# Move Proxmox Containers And VMs
* [How To Move Proxmox Containers And VMs To Different Disk](https://ostechnix.com/move-proxmox-containers-vms-to-different-disk/)


-----



# Virtual GPU/OpenGL Support
* [Virtual GPU Is Now Functional On Proxmox!](https://www.youtube.com/watch?v=gkzrAYQHtk4)




[01]:https://protectli.com/kb/bios-versions-for-the-vault/
[02]:https://www.servethehome.com/how-to-change-primary-proxmox-ve-ip-address/
[03]:https://protectli.com/kb/proxmox-ve-on-the-vault/
[04]:https://pve.proxmox.com/wiki/Network_Configuration
[05]:https://phoenixnap.com/kb/install-proxmox
[06]:https://pve.proxmox.com/pve-docs/pve-admin-guide.html#sysadmin_network_configuration
[07]:https://www.ventoy.net/en/index.html
[08]:https://www.ventoy.net/en/screenshot.html
[09]:https://www.ventoy.net/en/doc_start.html
[10]:https://www.proxmox.com/en/downloads
[11]:https://pve.proxmox.com/wiki/Prepare_Installation_Media
[12]:https://www.oreilly.com/library/view/linux-shell-scripting/9781785881985/8e6f4e56-ec36-4357-a47f-23241079fffd.xhtml
[13]:https://pve.proxmox.com/wiki/Package_Repositories#sysadmin_no_subscription_repo
[14]:https://www.youtube.com/watch?v=_u8qTN3cCnQ
[15]:https://unixcop.com/modify-proxmox-repositories/
[16]:https://www.youtube.com/watch?v=Fc6b7jchSWY
[17]:https://www.networksolutions.com/blog/establish/domains/what-is-a-fully-qualified-domain-name--fqdn--
[18]:https://johnscs.com/remove-proxmox51-subscription-notice/
[19]:https://linuxcontainers.org/
[20]:https://www.geeksforgeeks.org/chroot-command-in-linux-with-examples/
[21]:https://blog.aquasec.com/a-brief-history-of-containers-from-1970s-chroot-to-docker-2016
[22]:https://www.geeksforgeeks.org/difference-between-lxc-and-docker-containers/
[23]:https://www.educba.com/lxc-vs-docker/
[24]:https://protectli.com/coreboot/
[25]:http://www.electricmonk.org.uk/2020/11/12/aes-and-aes-ni/
[26]:https://www.coreboot.org/users.html
[27]:https://arstechnica.com/civis/viewtopic.php?t=1141632
[28]:https://study.com/academy/lesson/address-translation-definition-types-examples.html#:~:text=Address%20Translation%20(AT)%20refers%20to,Network%20Address%20Translations%20(NAT).
[29]:https://www.keycdn.com/support/what-is-cidr
[30]:https://gareth.com/index.php/2021/09/14/proxmox-7-installation/
[31]:https://pve.proxmox.com/pve-docs/chapter-pvecm.html#pvecm_edit_corosync_conf
[32]:https://linuxcontainers.org/lxc/introduction/
[33]:https://www.sumologic.com/blog/application-containers-vs-system-containers-understanding-difference/
[34]:https://www.turnkeylinux.org/
[35]:https://b3n.org/proxmox-vs-esxi/
[36]:https://getmethegeek.com/blog/2020-04-20-installing-docker-and-portainer-on-proxmox/
[37]:https://www.youtube.com/watch?v=79KiCBNbsbg
[38]:https://docs.docker.com/engine/install/debian/
[39]:https://www.thesmarthomebook.com/2021/09/21/home-server-installing-docker-portainer-home-assistant-on-proxmox/
[40]:https://radagast.ca/linux/nat_and_ip_masquerade.pdf
[41]:https://learn.g2.com/port-forwarding
[42]:https://www.portainer.io/
[43]:https://www.youtube.com/watch?v=n2DyeLOu3bA
[44]:https://www.rodsbooks.com/refind/
[45]:http://refit.sourceforge.net/
[46]:http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface
[47]:http://www.gnu.org/software/grub/
[48]:
[49]:
[50]:
[51]:
[52]:https://www.fail2ban.org/wiki/index.php/Main_Page
[53]:https://blog.cloudflare.com/waf-for-everyone/
[54]:https://www.akamai.com/our-thinking/ddos
[55]:https://blog.cloudflare.com/unmetered-mitigation/
[56]:https://blog.cloudflare.com/waf-for-everyone/
[57]:https://developers.cloudflare.com/waf/reference/migration-guides/firewall-rules-to-custom-rules/
[58]:https://developers.cloudflare.com/support/firewall/tools/configuring-cloudflare-rate-limiting/
[59]:
[60]:

