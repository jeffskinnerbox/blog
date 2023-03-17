<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


----


# Background
I first establish my Linux desktop environment in 2013 with Ubuntu 13.04.
I repeatedly upgraded desktop, generally twice a year, with the latest release.
It is now 2022 and Ubuntu 22.04 is available for another upgrade.
After these 8+ years, obtain a smooth / flawless upgrades is very unlikely.
I have to face the fact that my Ubuntu system is a bit messed up,
and despite trying numerous ways to fix it,
the easiest way out seems to be to reinstall Ubuntu.

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



-----



# Install Ubuntu 22.04
First, [download Ubuntu from its website][01].
Once you have got the ISO image, it’s time to [create a live USB][02] from it,
and [perform the install][03].

With version 22.04, Ubuntu switches to the Wayland display server by default once again.

* [Here are the New Features in Ubuntu 22.04 LTS Jammy Jellyfish](https://itsfoss.com/ubuntu-22-04-release-features/)



-----



# Add a Fail-Safe User Account
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

#### Create Fail-Safe Account - DONE
This fail-safe user account's home directory will reside on
the `/dev/sda` disk under the `/mnt` directory
and be in the same group as my user account.
The `/dev/sda` device is the safe place to reside because we'll be messing
with the other drives and they could get corrupted.

```bash
# add the user
sudo adduser --home /mnt/jeff-admin --ingroup jeff jeff-admin

# give the new account root privileges
sudo usermod -aG sudo jeff-admin
```

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

Source:
* [How to Add and Delete Users on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-add-and-delete-users-on-ubuntu-18-04)



-----



# Install Prerequisite Packages

#### Step 1: Supporting Packages - DONE
```bash
# install packages for general use
sudo apt-get -y install trash-cli gnome-terminal git jq

# install basic networking tools
apt-get -y install net-tools nmap traceroute arp-scan netdiscover

# packages which let apt get packages over HTTPS
apt -y install apt-transport-https ca-certificates curl software-properties-common

# install packages for for creation of raid
sudo apt-get -y install smartmontools mdadm
```

Next we will update the packages on your system
and install codecs for proprietary files with restricted copyright
(MP3, AVI, MPEG, Microsoft fonts) and Adobe Flash Player.

```bash
# update the packages on your system
sudo apt-get update && sudo apt-get dist-upgrade

# install codecs for proprietary files with restricted copyright
sudo apt-get install ubuntu-restricted-extras

# tools need for video card install
sudo apt install hwinfo

# install the spice client for use with proxmox
# NOTE: kvm conflicts with virtualbox
sudo apt-get install qemu-kvm virt-viewer
```

>**NOTE:** KVM and VitualBox **do not** play nice together.
>[VirtualBox will throw a Guru Meditation error][47] if KVM is installed.

You can't use Virtualbox alongside KVM,
choose one or the other, since they hypervisors fight over control.
you can temporally disable KVM or VirtualBox modules and then re-enable them when you want.

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

#### Step 2: Google Chrome
```bash
# download the latest Google Chrome .deb package
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

# installing packages on Ubuntu
sudo apt install ./google-chrome-stable_current_amd64.deb
```

In the Activities search bar type “Google Chrome” and click on the icon to launch the application.
Pin the icon to the favorites.

#### Step 3: Your Tools
```bash
# install required packages
sudo apt-get -y install wmctrl vim vim-gkt3 curl

# install bash and vim configuration files
https://github.com/jeffskinnerbox/.bash/blob/master/setup_dotbash.sh
https://github.com/jeffskinnerbox/.vim/blob/master/setup_dotvim.sh
```



-----



* [How To Manage RAID Arrays with mdadm on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-manage-raid-arrays-with-mdadm-on-ubuntu-16-04)
* [HOWTO: Repair a broken Ext4 Superblock in Ubuntu](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
# Mount RAID Drives
First, you'll need to find what disks you have install,
regardless if they are mounted or not.
You can do this with the `fdisk` command and via the `/etc/fstab` file.

#### Step 1: Gather Data - DONE
```bash
# list all the drives install on the computer
$ sudo fdisk -l | grep Disk | grep -v loop | grep -v dos
Disk /dev/sda: 119.24 GiB, 128035676160 bytes, 250069680 sectors
Disk model: Samsung SSD 840
Disk identifier: 0x0008f01d
Disk /dev/sdb: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-1SB1
Disk identifier: 0xe9fd17be
Disk /dev/sdc: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-1CH1
Disk identifier: 0xe9fd17be

# we are interested in sdb and sdc
$ sudo fdisk -l /dev/sdb /dev/sdc
Disk /dev/sdb: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-1SB1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xe9fd17be

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1        2048 1953525167 1953523120 931.5G 83 Linux


Disk /dev/sdc: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-1CH1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xe9fd17be

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdc1        2048 1953525167 1953523120 931.5G 83 Linux
```

We know that the multi-partitioned drive `/dev/sda` was used to load the Ubuntu OS.
Therefore, the drives `/dev/sdb` and `/dev/sdc` are the drives we are interested creating the RAID.
We also know the serial number of the oldest drive in the RAID is `Z1D3N7RY`
(see `solving-raid-disk-failure.md`).
Let's list the serial numbers on the drives:

```bash
# get the serial number of the sdb drive
$ sudo smartctl -i /dev/sdb1 | grep -E "Serial|Model"
Model Family:     Seagate Barracuda 7200.14 (AF)
Device Model:     ST1000DM003-1SB102
Serial Number:    W9ANL1XX

# get the serial number of the sdc drive
jeff@desktop: ~ $ sudo smartctl -i /dev/sdc1 | grep -E "Serial|Model"
Model Family:     Seagate Barracuda 7200.14 (AF)
Device Model:     ST1000DM003-1CH162
Serial Number:    Z1D3N7RY
```

#### Step 2: Create The Array - DONE
>**NOTE:** I was unable to successfully assemble the disks into a function RAID One array.
>As a result, I resorted to creating a fresh array and I will restore the files from my backups.

To create an empty RAID 1 array with `/dev/sdb` and `dev/sdc`

```bash
# create the raid one array
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb /dev/sdc
```

The mdadm tool will start to mirror the drives.
This can take some time to complete, but you can monitor the progress of the mirroring by checking the /proc/mdstat file:

```bash
# monitor the progress of the mirroring
$ cat /proc/mdstat
Personalities : [raid1]
md0 : active raid1 sdc[1] sdb[0]
      976630464 blocks super 1.2 [2/2] [UU]
      [=>...................]  resync =  9.4% (92582784/976630464) finish=90.4min speed=162962K/sec
      bitmap: 8/8 pages [32KB], 65536KB chunk

unused devices: <none>
```

>**NOTE:** To stop a RAID array, assuming its **not mount**, you `sudo mdadm --stop /dev/md0`.
>If mounted, then do `sudo umount /mnt/md0 && sudo mdadm --stop /dev/md0`.

Once this array creation process completes,
you can create a filesystem on the array:

```bash
# validate the setup
sudo mdadm --detail /dev/md0

# create a filesystem on the array
$ sudo mkfs.ext4 -F /dev/md0
mke2fs 1.46.5 (30-Dec-2021)
Creating filesystem with 244157616 4k blocks and 61046784 inodes
Filesystem UUID: 126e8dc9-e13c-440f-bb02-dc266378329f
Superblock backups stored on blocks:
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
	102400000, 214990848

Allocating group tables: done
Writing inode tables: done
Creating journal (262144 blocks): done
Writing superblocks and filesystem accounting information: done
```

#### Step 3: Mount The RAID Array - DONE
We want to mount the array as the `/home` directory for the Ubuntu OS.
This is where all the Ubuntu user accounts are located.
To do this, we'll need to move all the existing data out of `/home`.
That should only be the directory for the `jeff` account.

For Ubuntu, it seems it is also necessary to update the `/etc/mdadm/mdadm.conf` file.
If this is not done, the RAID device will not be mounted when you reboot the system.
The solution is to run the following command on your system,
once the RAID drive has been configured:

```bash
# check the final status of the raid array
sudo mdadm -D /dev/md0

# move data out of home directory
sudo mkdir /mnt/jeff-admin/tmp
sudo cp -R /home/* /mnt/jeff-admin/tmp

# clean out /home directory to prepare for the mounting of the raid array
sudo trash /home/jeff

# mount the raid array filesystem
sudo mount /dev/md0 /home
```

#### Step 4: Saving the Array Layout - DONE
To make sure that the array is reassembled automatically at boot:

1. update the `/etc/mdadm/mdadm.conf` file with the arrays configuration
2. update the `initramfs`, or initial RAM file system, so that the array will be available during the early boot process
3. add the new filesystem mount options to the /`etc/fstab` file for automatic mounting at boot

```bash
# automatically scan the active array and append
sudo cp /etc/mdadm/mdadm.conf /etc/mdadm/mdadm.conf_backup
sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf

# update initial RAM file system
$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-5.15.0-27-generic

# automatic mount array at boot
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
# / was on /dev/sda6 during installation
UUID=65e559c7-e595-4ab6-89a1-7b27d071bc3d /   ext4  errors=remount-ro  0  1
# /boot/efi was on /dev/sda3 during installation
UUID=CACF-2C59  /boot/efi       vfat    umask=0077                     0  1
/swapfile       none            swap    sw                             0  0
/dev/md0        /home           ext4    defaults,nofail,discard        0  0
```

Now test if the RAID array gets auto-mounted by doing a reboot.

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
```

#### Step 5: Load Backup to /home - DONE
* [Backup and Restore Your Linux System with rsync](https://averagelinuxuser.com/backup-and-restore-your-linux-system-with-rsync/)

Basically, these three options needed to preserve all the attributes of your files.
Owner attributes or permissions will not be modified during the backup process.

* `-a` - archive mode
* `-A` - preserve Access Control List
* `-X` - preserve extended attributes

* --delete - this option allows you to make an incremental backup. That means, if it is not your first backup, it will backup only the difference between your source and the destination. So, it will backup only new files and modified files and it will also delete all the files in the backup which were deleted on your system. Be careful with this option.
* --dry-run - This option simulates the backup. Useful to test its execution.

```bash
# do a dry-run test
sudo rsync --dry-run -aAXv --exclude="lost+found" /media/jeff-admin/c484e1d5-5e9d-4f95-bca9-de500fa3d44e/daily.0/desktop/home/ /home/

# do the restoration for real
sudo rsync -aAXv --exclude="lost+found" /media/jeff-admin/c484e1d5-5e9d-4f95-bca9-de500fa3d44e/daily.0/desktop/home/ /home/

# filesystem status
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           1.6G  2.1M  1.6G   1% /run
/dev/sda6       109G   14G   90G  14% /
tmpfs           7.8G  400M  7.4G   6% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
/dev/md0        916G  410G  460G  48% /home
/dev/sda3       512M  5.3M  507M   2% /boot/efi
tmpfs           1.6G  4.7M  1.6G   1% /run/user/1000
```

#### Step 6: Establish Additional Logins - DONE
With the loading of backup files to `/home`,
Some additional home directories have been established for the users:
`jennie` and `backup_user`.

```bash
# create the required logins: user login
sudo adduser --home /home/jennie jennie

# make a group id for the backup user
sudo groupadd -g 400 backup_user

# create the required logins: user without a login
sudo adduser --home /home/backup_user --disabled-login --disabled-password --uid 400 --gid 400 backup_user

# to check if all is well
cat /etc/passwd
```



-----




# Set-Up Networking
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

#### Step X: Check How is Your Network Being Managed - DONE
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

#### Step 1: Configuring Your Ethernet Connection - DONE
All of the above is a bit overwhelming.
I just want to do some basic configuration of my networks.
The install of Ubuntu defaulted to DHCP Ethernet connection with no WiFi.
I want to change this so the Ethernet is a static IP
and WiFi is also operational using DHCP.

You can make these updates with `Settings` app in the Ubuntu desktop toolbar.
I used the settings below:

```
# static ip address for ethernet connection
IP Address  192.168.1.200
Gateway     192.168.1.1
Net Mask    255.255.255.0
DNS         192.168.1.1, 1.1.1.1, 1.0.0.1
```

#### Step 2: Configuring Your WiFi Connection - DONE
Again using the `Settings` app in the Ubuntu desktop toolbar,
configure your WiFi for a DHCP connection.

#### Step X: Configure Your Network via Netpaln

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

#### Step X: Test and Apply Your Network Configuration
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


#### Step X: Restart the Network Service
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

#### Rename Interface
* [ubuntu 22.04 persistent network interface names](https://www.google.com/search?q=ubuntu+22.04+persistent+network+interface+names&sxsrf=ALiCzsYPpufekZV53gZk1KxELS1wlUxmRQ%3A1653143932949&ei=fPmIYu_KOYzWytMP2O-JwAQ&ved=0ahUKEwjv-IqH6fD3AhUMq3IEHdh3AkgQ4dUDCA4&uact=5&oq=ubuntu+22.04+persistent+network+interface+names&gs_lcp=Cgdnd3Mtd2l6EAM6BwgAEEcQsAM6BwgjELACECdKBAhBGABKBAhGGABQsQpYgh5g9iFoAnABeACAATyIAdoCkgEBN5gBAKABAcgBCMABAQ&sclient=gws-wiz)
* [How to rename a network interface in 20.04](https://askubuntu.com/questions/1317036/how-to-rename-a-network-interface-in-20-04)
* [A sysadmin's guide to network interface configuration files](https://opensource.com/article/22/8/network-configuration-files)



* [How to configure networking with Netplan on Ubuntu](https://vitux.com/how-to-configure-networking-with-netplan-on-ubuntu/)
* [Have a Plan for Netplan](https://www.linuxjournal.com/content/have-plan-netplan)
* [Ubuntu netplan gateway4 has been deprecated](https://tizutech.com/ubuntu-netplan-gateway4-has-been-deprecated/)
* [Netplan reference](https://netplan.io/reference/)
* [Netplan configuration examples](https://netplan.io/examples/)
* [How to Configure Netplan Network? – LAB Examples](https://getlabsdone.com/how-to-configure-netplan-network/)


-----



# Setup Dual Monitor
With this refresh of my Linux desktop computer,
I'm upgrading to a dual monitor configuration.
To do this, I'll need to

1. Purchase another monitor display equivalent to my existing display
([32" LG 32GN50T-B Monitor Ultragear FHD SYNC][28]) and a [dual monitor stand][29].
2. Purchase a video card ([MSI Geforce 210][26] / [N210-MD1G/D3][27]) to drive the second monitor screen.
3. Need to modify BIOS on [motherboard (Intel Desktop Board DZ77GA-70K)][25] to support dual monitor.
4. Within Ubuntu on the **Settings* > **Displays** app, I'll need to configure the two displays
5. Set the brightness, color setting, etc. on the two displays to be visually equivalent.

Alternatives ...
* [Raspberry Pi Adds Second Laptop Monitor](https://hackaday.com/2023/03/15/raspberry-pi-adds-second-laptop-monitor/#more-581185)

Sources:

* [How do dual monitors work?](https://www.youtube.com/watch?v=rjNCWK_MfZs)
* [How to Use Onboard Graphics for Second Monitor](https://www.youtube.com/watch?v=8iT1pgPo-1E)
* [How to Setup Dual Monitor | Windows | Linux | MAC](https://www.technowifi.com/how-to/how-to-setup-dual-monitor/)

#### Step 1: Wayland or X11 Display Manager - DONE
I read on the web that Wayland doesn't work well with a dual monitor setup, at least at this time.
To avoid this challenge, I choose to continue to use X11.

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

#### Step 2: Modify BIOS on Motherboard - DONE
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

#### Step 3: Install Monitors and Video Card - DONE
I followed the install procedures that came with the devices.
It was basically "plug & play".

I did not install any special driver for the video card.
You find may references on the web about installing [Linux Nvidia drivers][30],
and may stories about things going wrong.
Try using the video card without new drivers first;
its likely good enough unless your a gamer.

#### Step 4: Configure Ubuntu for Multiple Displays - DONE
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

#### Step 5: Get Screen Blanking Working
Should we go back to Wayland?

* [A Primer on Screen Blanking Under Xorg](https://shallowsky.com/linux/x-screen-blanking.html)
* [xscreensaver - extensible screen saver and screen locking framework](https://manpages.ubuntu.com/manpages/xenial/man1/xscreensaver.1.html)



-----



# MyMedia - Music Streaming to Echo - DONE
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



-----



# Apache Web Server - Infrastructure to Support WebPages
The Apache HTTP server is the most widely-used web server in the world.
There are a variety of reasons may choose to install the Apache Web Server.
You can use it for testing HTTP server for testing,
or host your own blog or wiki using static web pages, as I plan to do.

#### Step 1: Installing Apache - DONE
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

#### Step X: Adjust the Firewall - DONE
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

#### Step X: Setting Up Virtual Hosts
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



-----



# Fix Desktop Backup Tools

## Restart Synology Backup Processing
I'm using a Synology small office NAS to perfrom hourly backup of my Linux desktop system.
Its a 2-bay [DiskStation DS220+][38] and much of its operation is not impacted by my
refresh of the Ubuntu OS.
Never the less, there is some house keeping to be done.

#### Step X: Validate / Create Backup User - DONE
On the Linux desktop, you need to assure there is a `backup_user` login,
with a UID of less that 500,
which will run the rsync / rsnapshot utilities
and have `ssh` authentication keys.

>**NOTE:** I choose a UID of 400 so that the `backup_user`
>would not appear on the Ubuntu login screen list.
>To hide a user from the Ubuntu login screen list,
>you should be able to add the name to the hidden-users
>list in the file `/etc/lightdm/users.conf`, but there is a [problem][45].
>The is an alternative, and that is to choose a UID value less than 500
>(See the "minimum-uid" in `/etc/lightdm/users.conf`).

```bash
# validate that backup_user login exist with uid of 400
cat /etc/passwd | grep backup_user

# validate that backup_user has a home directory with required tools
$ lsa /home/backup_user/
bin/     .config/  .ssh/       .bash_history  .bashrc   rsync-exclude-desktop  rsync-exclude-windows  .viminfo
.cache/  .local/   backup.log  .bash_logout   .profile  rsync-exclude-RPi      .selected_editor
```

#### Step X: Add backup_user to sudo list - DONE
The `backup_user` is not root, and therefore, the utilities it uses for backups
(`rsync` and `rsnapshot`)
can't freely move through the whole directory system , write files, and such.
Again using the [`visudo`][43] command,
edit the [`/etc/sudoers`][44] file by adding the following
to the bottom of the file.

```bash
# start the edit process and do the edits below
sudo visudo /etc/sudoers

# allows this user to not need a password to sudo the specified command(s)
backup_user    ALL=NOPASSWD:    /usr/bin/rsync
backup_user    ALL=NOPASSWD:    /usr/bin/rsnapshot
```

Now check your work:

```bash
# check if your edits took hold
$ sudo cat /etc/sudoers | grep backup
backup_user    ALL=NOPASSWD:    /usr/bin/rsync
backup_user    ALL=NOPASSWD:    /usr/bin/rsnapshot
```

#### Step X: Increased Security of backup_user Account - DONE
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

#### Step X: Start Synology Backup Process - DONE
You should be able to now restart your Synology backup NAS device.
Check that backups are created.

#### Step X: Restart Rsnapshot Backup Processing - DONE
To get your backup work again,
you should read the document
`/home/jeff/blogging/content/articles/network-backups-via-rsync-and-rsnapshot.md`.
A large fraction of this work is done for you by reclaiming the `/home` directory
and using the scripts within `/home/bachup_user/bin`.
The steps you need to perform, using the documentation as your guide:

1. You'll need to to install `rsync` and related software.
2. Update the `/etc/fstab` file to mount the external drive.
3. Mount the drive and do your fist backup, as document, manually
(i.e. `sudo rsnapshot hourly`).
4. To get automated backups running, update the `crontab` file for the
user `backup_user` (if needed), and restart it.



-----



# Fix Desktop Environment

#### Step X: Re-Establish Desktop Layout - DONE
Install GNOME Extensions, GNOME Tweaks tool, and other such things using the following commands:

```bash
# gnome extension - gnome shell integration
# first, go to here - https://chrome.google.com/webstore/detail/gnome-shell-integration/gphhapmejobijbbhgpjhcjognlahblep
sudo apt-get install chrome-gnome-shell
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

#### Step X: Get Conky Working - DONE
Conky is a light-weight system monitor for X Window that displays any information on your desktop.
It is highly configurable as it is able to monitor literally any aspect of your system
from hard-drive temperature through number of users logged in to currently played music song.

```bash
# install conky
sudo apt-get -y install conky-all

# install your version of the .conkyrc file
git clone https://github.com/jeffskinnerbox/.conky.git

# to test, launch conky using your $HOME directory conky resource fil
conky

# launch conky using another resource file
conky -c /home/jeff/.conky/src/conky-test
```

By default, Conky monitors the `eth0` & `wlan0` network interface,
but there’s a good chance that your network interface uses a different name.
Obtain your network interface name and then replace the `eth0` & `wlan0` values.
You can get your network interface via this command:

```bash
# list network interfaces that are up & working
$ ip address | grep '^[0-9]' | grep 'state UP'
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
4: wlx94dbc95110ca: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
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


#### Step X: Downloading Video Files - DONE
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

To install it, do the following:

```bash
# download youtube-dl using curl and move it to the usr bin folder as a program
sudo curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl

# alter the permissions (read and execute)
sudo chmod a+rx /usr/local/bin/youtube-dl

# install the Python 3 pip package which is used to upgrade youtube-dl
sudo apt install python3-pip
pip3 install --upgrade youtube-dl

# youtube-dl sometimes makes use of ffmpeg
sudo apt install ffmpeg
```

When the time comes to upgrade Youtube-dl use:
`pip3 install --upgrade youtube-dl`.

>**NOTE:** `*.mp4` happens to be the default file output format for `youtube-dl`.

#### Step X: Install VLC Media Player - DONE
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



-----



# Development Tools: VirtualBox
I chose to installing VirtualBox from Oracle’s package repositories and
used the website "[How to Install VirtualBox on Ubuntu][22]" as my guide.

####################### REMOVE TEXT BETWEEN THESE LINES ########################
#### Step 1: Install VirtualBox
Often the default Ubuntu repositories do not have the latest versions of the software,
so instead, I chose to install from Oracle’s package repositories.
This process is more in-depth but installs the most recent version of VirtualBox.

```bash
# update the apt database
sudo apt-get update

# required packages for the install
sudo apt-get install software–properties–common

# download and install gpg keys for virtualbox repository
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -

# add the virtualbox repository
#echo "deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian $(lsb_release -cs) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
echo "deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian eoan contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list

# install virtualbox
sudo apt-get update
sudo apt-get install virtualbox–6.1
```

#### Step 2: Install VirtualBox Extension Pack
Now we'll install the VirtualBox Extension Pack.
It adds additional tools like USB 2.0 and 3.0, Remote Desktop, and encryption.
Make sure to use the latest version from the [Oracle website][23].

```bash
# download virtualbox extension pack
wget https://download.virtualbox.org/virtualbox/6.1.34/Oracle_VM_VirtualBox_Extension_Pack-6.1.34.vbox-extpack

# import virtualbox extension pack
sudo VBoxManage extpack install Oracle_VM_VirtualBox_Extension_Pack-6.1.34.vbox-extpack
```
####################### REMOVE TEXT BETWEEN THESE LINES ########################

#### Step 1: Install VirtualBox - DONE
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

#### Step 2: Install VirtualBox Extension Pack - DONE
Now we'll install the VirtualBox Extension Pack.
It adds additional tools like USB 2.0 and 3.0, Remote Desktop, and encryption.
Make sure to use the latest version from the [Oracle website][23].

```bash
# install the virtualbox extension pack
sudo apt-get install virtualbox-ext-pack
```


-----



# Development Tools: Vagrant

#### Step 1: Install Vagrant - DONE
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

#### Step 2: Installing Vagrant's VirtualBox Guest Addition - DONE
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


-----



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

#### Step 1: Installing Ansible - DONE
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

#### Step 2: Install Docker Extension - DONE
To manage Docker containers on remote machines,
you need to install the Docker Ansible-Galaxy extension for Ansible:

```bash
# install the docker extension for ansible
ansible-galaxy collection install community.docker

# check to see if it is installed
$ ls ~/.ansible/collections/ansible_collections/community
```

#### Step 3: Set Your Ansible Path - DONE
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

#### Step 4: Installing Vim Plugin for Ansible - DONE
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
#### Step 6: Create Your Remote Hosts - DONE
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

#### Step 6: Set Up SSH Keys - DONE
Ansible primarily communicates with client computers through SSH.
While it has the ability to handle password-based SSH authentication,
using SSH keys can help to keep things simple.
Check [here][39] if you need more information concerning SSH and its keys.

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




----



# Development Tools: Docker & Portainer
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
**[Portainer][61]** is a popular Docker UI that helps you visualise your
containers, images, volumes and networks.
Portainer helps you centrally configure, manage and secure containerized environments,
regardless of where they are hosted.
It helps you take control of the Docker resources on your machine, avoiding lengthy terminal commands.

>**NOTE:** By default, the docker command can only be run the root user
>or by a user in the docker group, which is automatically created during Docker’s installation process.

Sources:

* [How To Install and Use Docker on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04)
* [How To Install and Use Docker Compose on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-22-04)
* [Deploying Portainer CE in Docker](https://documentation.portainer.io/v2.0/deploy/ceinstalldocker/)
* [How to Install Portainer Docker UI Manager on Ubuntu 20.04 | 18.04 | 16.04](https://docs.fuga.cloud/how-to-install-portainer-docker-ui-manager-on-ubuntu-20.04-18.04-16.04)
* [How to Install Portainer 2.0 on your Docker](https://www.letscloud.io/community/how-to-install-portainer)

## Docker

#### Step X: Install Docker - DONE
To ensure we get the latest version,
we’ll install Docker from the official Docker repository.
To do that, we’ll add a new package source,
add the GPG key from Docker to ensure the downloads are valid,
and then install the package.

```bash
# update your existing list of packages
sudo apt update

# install a few prerequisite packages which let apt use packages over https
sudo apt install apt-transport-https ca-certificates curl software-properties-common

# add the GPG key for the official Docker repository
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# add docker repository to apt sources
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# update your list of packages
sudo apt update

# check to make sure you are about to install from
# the docker repo instead of the default Ubuntu repo
apt-cache policy docker-ce
```

From the above last command,
you'll see the installation will be from the Docker repository for Ubuntu 22.04 (jammy).
Now lets install Docker:

```bash
# install docker
sudo apt install docker-ce

# check to see if docker is running
sudo systemctl status docker
```

#### Step X: Upgrade Docker
Docker will be automatically by Ubuntu from the official Docker repository.

## Docker Compose

#### Step X: Install Docker Compose - DONE
To ensure we get the latest version,
we’ll install Docker Compose from the official Docker repository.
To do that, we’ll add a new package source,
add the GPG key from Docker to ensure the downloads are valid,
and then install the package.

First, we must confirm the latest version available for Docker Compose by check its [releases page][39].
At the time of this writing, the most **current stable version is 2.5.0**.

```bash
# download docker compose
mkdir -p ~/.docker/cli-plugins/
curl -SL https://github.com/docker/compose/releases/download/v2.5.0/docker-compose-linux-x86_64 -o ~/.docker/cli-plugins/docker-compose

# set the correct permissions
chmod +x ~/.docker/cli-plugins/docker-compose

# verify that the installation was successful
docker compose version
```

#### Step X: Upgrade Docker Compose
You'll need to upgrade Docker Compose from time-to-time via:

```bash
# download docker compose
mkdir -p ~/.docker/cli-plugins/
curl -SL https://github.com/docker/compose/releases/download/v2.5.0/docker-compose-linux-x86_64 -o ~/.docker/cli-plugins/docker-compose
```

## Portainer

#### Step X: Install Portainer - DONE
Use the following Docker commands to deploy the Portainer Server.

```bash
# create the volume for storing persistent data
sudo docker volume create portainer_data

# install the portainer container (ports 8000 is for agents and 9000 for web ui)
sudo docker run -d -p 8000:8000 -p 9000:9000 -p 9443:9443 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest

# check if portainer is running
sudo docker ps -a -s
```

Now using your browser, log into portainer via this URL: `localhost:9000`.

#### Step X: Upgrading Portainer
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
sudo docker run -d -p 8000:8000 -p 9000:9000 -p 9443:9443 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
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



----



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



------


# Setup Markdown to PDF / HTML Tools - DONE
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



------



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
[39]:https://github.com/docker/compose/releases
[40]:https://docs.portainer.io/v/ce-2.9/admin/upgrade/docker
[41]:https://en.wikipedia.org/wiki/Fail-safe
[42]:https://www.mymediaalexa.com/home/docker#download
[43]:http://www.sudo.ws/sudo/sudoers.man.html
[44]:http://www.sudo.ws/visudo.man.html
[45]:http://www.cyberciti.biz/faq/howto-change-rename-user-name-id/
[46]:https://www.amazon.com/bizmodeller-My-Media/dp/B06XPP135L
[47]:https://ostechnix.com/virtualbox-guru-meditation-critical-error-in-linux/
[48]:
[49]:
[50]:
