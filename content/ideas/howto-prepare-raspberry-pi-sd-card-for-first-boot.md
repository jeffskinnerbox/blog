<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----



You may think installing Ansible for Raspberry Pi is overkill,
but you will find it worthwhile if you need to manage more than two or three RPi.
Using Ansible also gives you a more hygienic network.
Your inventory is audited and listed in its host file,
software installations are documented through its playbooks,
and data and configurations are kept away from their devices,
so they are easier to back up regularly.

# Raspberry Pi Setup
I have set up nearly all my Raspberry Pi's as [headless devices][01];
not monitor, keyboard, or mouse attached to the device.
For one thing, I can run any X-Window application from my Linux desktop using its X Server.
I will be SSH'ing into my devices so I don't want or need a monitor/keyboard.
The real trick on going headless is doing the initial setup of the device
without any HDMI monitor or a keyboard / mouse,
required by the [typical RPi setup][28].
Using just a SD Card reader/writer, a Ethernet connection
(or optionally via USB WiFi adapter or the native RPi WiFi),
and a Linux machine, I can do the whole setup.

If you determined to have WiFi for your RPi Zero
(the one without WiFi, like the Zero W has), it can be done.
It's easy to just use a [Micro USB OTG Adapter][26] and a [WiFi USB Adapter][27].
With this in place, you just need to provision the RPi Zero
like any Raspberry Pi for WiFi connectivity.

# What Version of RPi DO I Have?
* [Raspberry Pi OS "Bullseye" Launches, Brings Speed Boost to the Latest Raspberry Pi 4 Models](https://www.hackster.io/news/raspberry-pi-os-bullseye-launches-brings-speed-boost-to-the-latest-raspberry-pi-4-models-b86becec3ae6)
* [How to know which Raspberry do you have](https://oastic.com/posts/how-to-know-which-raspberry-do-you-have/)
    * [Which Pi Do I Have? Includes Pi 4](https://support.pishop.us/article/69-which-pi-do-i-have-includes-pi-4)
    * [Raspberry Pi 4 Model B - Board Revisions](https://core-electronics.com.au/tutorials/Versions-Raspberry-Pi.html)




---------



# Preparing the Raspberry Pi Image

## Choose Your OS
* [Raspberry Pi OS][31]
* [How to install Ubuntu Desktop on Raspberry Pi 4](https://ubuntu.com/tutorials/how-to-install-ubuntu-desktop-on-raspberry-pi-4#1-overview)
* [How to install Ubuntu Server on your Raspberry Pi](https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#1-overview)
* [EdgeX on Raspberry Pi 4B](https://docs.edgexfoundry.org/2.0/examples/Ch-ExamplesRP4/)
* [Installing CentOS on a Raspberry Pi](https://medium.com/@rockprofile/installing-centos-on-a-raspberry-pi-2112e9ee68fc)
* [How to Install Arch Linux on a Raspberry Pi 4](https://itsfoss.com/install-arch-raspberry-pi/)

### Step 1: Download Raspberry Pi Image - DONE
Before you can load a copy of the latest Raspberry Pi image onto your micro SD Card,
you must first download the official [Raspberry Pi 4][30] operating system, [Raspberry Pi OS][31]
I'll download and install the Raspberry Pi OS Lite version.
The download site also lists a check sum for the download file.
(In my case, I down loaded the Raspberry 4 OS file to `/home/jeff/Downloads/RPi-OS`.)
Check whether the file has been changed from its original state
by checking its digital signature (SHA1 hash value).

```bash
# change director to temp storage
cd ~/Downloads/RPi-OS

# download raspberry pi os (Raspberry Pi OS Lite - no desktop)
# method below or via this page - https://www.raspberrypi.org/software/operating-systems/
wget https://downloads.raspberrypi.org/raspios_lite_armhf/images/raspios_lite_armhf-2021-05-28/2021-05-07-raspios-buster-armhf-lite.zip

# validate file is not corrupted via check of digital signature
# at https://www.raspberrypi.org/software/operating-systems/
$ sha256sum /home/jeff/Downloads/RPi-OS/2021-05-07-raspios-buster-armhf-lite.zip
c5dad159a2775c687e9281b1a0e586f7471690ae28f2f2282c90e7d59f64273c  /home/jeff/Downloads/RPi-OS/2021-05-07-raspios-buster-armhf-lite.zip
```

Next you need to unzip the file to retrieve the Linux image file:

```bash
# move to the directory with the download
cd /home/jeff/Downloads/RPi-OS

# unzip the raspberry pi os
unzip 2021-05-07-raspios-buster-armhf-lite.zip

# check the size of the image
$ ls -l
total 2287912
-rw-r--r-- 1 jeff jeff 1874853888 May  7 11:00  2021-05-07-raspios-buster-armhf-lite.img
-rw-rw-r-- 1 jeff jeff  465662909 May  7 11:02  2021-05-07-raspios-buster-armhf-lite.zip


# remove the zip file
rm 2021-05-07-raspios-buster-armhf-full.zip
```

### Step 2: Write Raspberry Pi Image to SD Card - DONE
Next using Linux, you have to copied the Raspberry OS image onto the SD card mounted to your system.
I'll be using the [Rocketek 11-in-1 4 Slots USB 3.0 Memory Card Reader][32] to create my SD Card.
Make sure to [choose a reputable SD Card][33] from [here][34], don't go cheap.

>>**NOTE:** Additionally important, for some project,
>>is to **use a 16G or 32G SD Card** if your doing a full image with desktop.

When using your card reader,
you'll need to know the device name of the reader.
The easiest way to find this is just unplug your card reader from the USB port,
run `df -h`, then plug it back in, and run `df -h` again.

```bash
# with the SD card reader unplugged
df -h

# with the SD card reader plugged in USB
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
 .
 .
 .
/dev/sdf2        15G  5.1G  8.4G  38% /media/jeff/e6e7f776-11a4-4cd7-b4fd-c44ecdbfcf90
/dev/sdf1        60M   21M   39M  36% /media/jeff/boot
```

Note that in my example above, the new device is `/dev/sdj1`.
The last part (the number 1) is the partition number
but we want to write to the whole SD card, not just one partition.
Therefore you need to remove that part when creating the image.
With this information, and know the location of the Raspbian image and
where we need to write the Raspberry OS image to the SD Card.

```bash
# go to directory with the RPi image
cd /home/jeff/Downloads/RPi-OS

# unmount the sd card reader
sudo umount /dev/sdf1
sudo umount /dev/sdf2

# write the image to the sd card reader
$ sudo dd bs=4M if=2021-05-07-raspios-buster-armhf-lite.img of=/dev/sdf status=progress
1870659584 bytes (1.9 GB, 1.7 GiB) copied, 150 s, 12.5 MB/s
447+0 records in
447+0 records out
1874853888 bytes (1.9 GB, 1.7 GiB) copied, 150.45 s, 12.5 MB/s

# ensure the write cache is flushed
sudo sync

# (optional) make a copy of the image from the sd-card
sudo dd bs=4M if=/dev/sdf of=copy-from-sd-card.img
sudo truncate --reference 2021-05-07-raspios-buster-armhf-lite.img copy-from-sd-card.img

# (optional) check the integrity of the sd card image
$ diff -s 2021-05-07-raspios-buster-armhf-lite.img copy-from-sd-card.img
Files 2021-05-07-raspios-buster-armhf-lite.img and copy-from-sd-card.img are identical

# remove the copied image
rm ~/Downloads/RPi-OS/copy-from-sd-card.img
```

### Step 3: Enable SSH on SD Card - DONE
SSH can be enabled on first boot by placing a file named `ssh` (without any extension),
onto the root directory of the boot partition on the SD-Card:

```bash
# mount the SD card reader by plug it in USB again

# check the mount point
$ df -h | grep media
/dev/sdf2       1.5G  1.1G  281M  80% /media/jeff/rootfs
/dev/sdf1       253M   48M  205M  19% /media/jeff/boot


# enable ssh on first boot
sudo touch /media/jeff/boot/ssh
```

As shown above,
while the SD Card maybe something like 16GB or 32GB in capacity,
the image makes it think its about 8GB.
This will need to be fixed in a later step where we reclaim this abandoned storage space.

>**NOTE:** (Optional) To securely wipe data from the SD-Card,
>you should wipe out all the data on the SD-Card by overwriting the entire drive with random data.
>This ensures that the data cannot be recovered by any data recovery tool.
>You need to completely wipe the data only if the device is going to be given away.
>Otherwise, you can skip this step.
>
>```bash
># erase data on the cd-card
>sudo dd if=/dev/zero of=/dev/<drive> bs=4096 status=progress
>```
>
>Depending of the size of the drive, the process will take some time to complete.
>Once the disk is erased, the `dd `command will print “No space left on device”.

### Step 4: Set a Static IP Address - DONE
If you’re using your Raspberry Pi as a server
often need to access it remotely from another device,
or provission it with with tools like Ansible,
setting a [static IP address][41] for it is a very good idea.
This way you find the Raspberry Pi at the same address every time,
rather than a new address being set dynamically by [DHCP][40].

My home router is my DHCP server (`192.168.1.1`) and I have reserved the IP range 2 to 199
for dynamically allocated IP addresses.
This leaves IP range 200 to 255 for static IP addresses.
I'm using `192.168.1.200` for my desktop Linux box,
so I'll pick my Raspberry Pi IP address from the remaining numbers that are unassigned.

Use the script below to update the DHCP configuration file `/etc/dhcpcd.conf`,
telling it that the device not to use DHCP, but instead, assign a static address.

```bash
# use this script to identify what ip addresses are being used, including any static ip
sudo arp-scan 192.168.1.0/24

# use this script to assign the ip address to the rpi
echo "
# using static address
interface eth0
static ip_address=192.168.1.201/24
static routers=192.168.1.1
static domain_name_servers=192.168.1.1" | sudo tee --append /media/jeff/rootfs/etc/dhcpcd.conf > /dev/null

# unmount the sd card
sudo umount /dev/sdj1 /dev/sdj2
```

Source:
* [How Do I Set a Static IP Address on Raspberry Pi?](https://www.makeuseof.com/raspberry-pi-set-static-ip/)

### Step 5: Install Ansible SSH Key
A common method for using Ansible is to set up passwordless
SSH keys to facilitate ease of management and automation of multiple nodes from a single controller.
My Ansible controller is my Linux desktop server
and Ansible SSH key is located `~/.ssh/ansible.pub`.

```bash
# use this script to install the ansible ssh key
??check first?? sudo cat ~/.ssh/ansible.pub >> /media/jeff/rootfs/home/pi/.ssh/authorized_keys
??check first?? sudo cat ~/.ssh/ansible.pub >> /media/jeff/rootfs/root/.ssh/authorized_keys
```

Sources:

* [Say YES to Password-free SSH Access!](https://medium.com/100-days-of-linux/say-yes-to-password-free-ssh-access-c7a7fa315cd7)

### Step X: Booting From the SD-Card
Install the SD Card created earlier and apply power.
Once the RPi boots up,
you can [find your Raspberry P on your network][35] using [`arp-scan`][36].
This tool will list the MAC Address of the devices on your network
and you can search for Rasperry Pi or the WiFi USB dongle it is using:

```bash
# scan the network for all live hosts
sudo arp-scan 192.168.1.0/24

# or scan the network of a certain type of live hosts
# https://udger.com/resources/mac-address-vendor-detail?name=raspberry_pi_foundation
# https://udger.com/resources/mac-address-vendor-detail?name=edimax_technology_co-ltd

# scan for a raspberry pi
$ sudo arp-scan 192.168.1.0/24 | grep -e dc:a6:32 -e b8:27:eb -e e4:5f:01
192.168.1.69	dc:a6:32:a7:fe:98	Raspberry Pi Trading Ltd

# scan for a edimax wifi usb dongle
$ sudo arp-scan 192.168.1.0/24 | grep -e 00:00:b4 -e 00:0e:2e -e 00:1f:1f -e 00:50:fc -e 08:be:ac -e 74:da:38 -e 80:1f:02
192.168.1.26	74:da:38:70:1c:08	Edimax Technology Co. Ltd.
```

Now using the IP address you found for the RPi,
SSH login (`ssh pi@192.168.1.69`)
and run the following commands to update your RPi to the latest software:

```bash
# login into the raspberry pi
# you might want to generate a new key via: sudo ssh-keygen -R 192.168.1.69
ssh pi@192.168.1.69

# set the time zone for your raspberry pi device
sudo timedatectl set-timezone America/New_York

# update the raspberry pi os
sudo apt-get update && sudo apt-get -y upgrade

# clean up any packages no longer needed
sudo apt-get -y autoremove
```

Run the following commands to update your RPi to the latest firmware:

```bash
# do firmware update and reboot
sudo rpi-update

# expand partition to use 100% of remaining space
#sudo raspi-config nonint do_expand_rootfs

# check if you got secured the remaining space on sd card
#df -h

# reboot needed the above to take effect
sudo reboot
```

Sources:

* [How could one automate the raspbian raspi-config setup?](https://raspberrypi.stackexchange.com/questions/28907/how-could-one-automate-the-raspbian-raspi-config-setup)



--------



# Post First Boot

### Ansible `apt update` All Packages
You can update the base Raspberry Pi OS image using the
`apt update && apt full-upgrade` equivalent apt module.
The playbook would be:

```yaml
---
- hosts: servers
  become: true
  become_user: root
  tasks:
    - name: Update apt repo and cache on all Debian/Ubuntu boxes
      apt: update_cache=yes force_apt_get=yes cache_valid_time=3600

    - name: Upgrade all packages on servers
      apt: upgrade=dist force_apt_get=yes

    - name: Check if a reboot is needed on all servers
      register: reboot_required_file
      stat: path=/var/run/reboot-required get_md5=no

    - name: Reboot the box if kernel updated
      reboot:
        msg: "Reboot initiated by Ansible for kernel updates"
        connect_timeout: 5
        reboot_timeout: 300
        pre_reboot_delay: 0
        post_reboot_delay: 30
        test_command: uptime
      when: reboot_required_file.stat.exists
```

Source
* [Ansible apt update all packages on Ubuntu / Debian Linux](https://www.cyberciti.biz/faq/ansible-apt-update-all-packages-on-ubuntu-debian-linux/)

### Ansible Install Docker
* [How to install Docker with Ansible for Raspberry Pi server?](https://www.reddit.com/r/selfhosted/comments/jqiwvo/how_to_install_docker_with_ansible_for_raspberry/)
* [How to install docker and docker-compose on your Raspberry Pi with Ansible](https://iotechonline.com/how-to-install-docker-and-docker-compose-on-your-raspberry-pi-with-ansible/)

```yaml
```

Sourcs:
* [How To Install and Use Docker on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04)
* [How to Use Ansible to Install and Set Up Docker on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-use-ansible-to-install-and-set-up-docker-on-ubuntu-18-04)



[01]:http://internetofthingsagenda.techtarget.com/definition/headless-system

[26]:https://www.amazon.com/gp/product/B015GZOHKW
[27]:https://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY
[28]:https://www.raspberrypi.org/help/noobs-setup/


[30]:https://www.raspberrypi.org/products/raspberry-pi-4-model-b/?resellerType=home
[31]:https://www.raspberrypi.org/software/

[32]:http://www.amazon.com/gp/product/B00GVRHON2?psc=1&redirect=true&ref_=oh_aui_detailpage_o00_s01
[33]:http://www.wirelesshack.org/best-micro-sd-card-for-the-raspberry-pi-model-2.html
[34]:http://www.jeffgeerling.com/blogs/jeff-geerling/raspberry-pi-microsd-card

[35]:https://www.youtube.com/watch?v=hx7DB7Iqslk
[36]:https://www.linux-magazine.com/Online/Features/Using-ARP-for-Network-Recon

[40]:https://www.efficientip.com/what-is-dhcp-and-why-is-it-important/
[41]:https://www.avast.com/c-static-vs-dynamic-ip-addresses
[42]:
[43]:
[44]:
[45]:
[46]:
[47]:
[48]:
[49]:
[50]:













