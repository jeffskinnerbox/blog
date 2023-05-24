<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----



# Check Out

* [How to Set Up Your Synology MailPlus Server](https://www.youtube.com/watch?v=tBLjJWn-WBk)

* [Backup in Linux Servers - Docker Volumes, and Databases](https://www.youtube.com/watch?v=JoA6Bezgk1c)
* [Get Docker organized for easier backups & replication. Trust me, an hour can save you days!](https://www.youtube.com/watch?v=sGtTvV0xbYg)
* [Backing up your Docker Configurations and Data](https://www.youtube.com/watch?v=wUXSLmGAtgQ)

* [Synology NAS Setup & Configuration Guide!](https://www.wundertech.net/synology-nas-initial-setup-ultimate-guide/)
* [Synology NAS Setup Guide 2022 – Part 1, Setup, Users, Updates, Remote Access And Security Settings](https://nascompares.com/guide/synology-nas-setup-guide-2022-part-1-setup-users-updates-remote-access-and-security-settings/)


# Proxmox Backup Server on Synology
* [Setting Up a Proxmox Backup Server](https://www.youtube.com/watch?v=n_JZ2aXMMmI)
* [How to Backup Proxmox to a Synology NAS](https://www.wundertech.net/how-to-backup-proxmox-to-a-synology-nas/)
* [ProxMox - Migration, Backup, and Restoration Tutorial](https://www.youtube.com/watch?v=BkVi2vRB75Q)



-------



# Backup Strategy
I need to implement the [3-2-1 backup rule][18]:
you should have 3 copies of your data,
you should be using at least 2 different medias,
and 1 copy should be offsite.

* [Backups: You're doing 'em wrong!](https://www.youtube.com/watch?v=S0KZ5iXTkzg)
* [Gickup](https://github.com/cooperspencer/gickup)
* [geerlingguy/my-backup-plan](https://github.com/geerlingguy/my-backup-plan)



-------



# Synology Cloud Sync
Cloud Sync enables you to connect your local Synology NAS to public cloud services or on-premise storage through Amazon S3 API, OpenStack Swift, or WebDAV protocols.
Connect your Synology NAS to public cloud services, such as BackBlaze B2, Dropbox, Google Cloud Storage, Microsoft Azure, OpenStack Swift, and more.

* [Cloud Sync](https://www.synology.com/en-us/dsm/feature/cloud_sync)



-------



# Syncthing (File Synchronization)
[Syncthing][10] is a continuous file synchronization program.
It synchronizes files between two or more computers in real time
Syncthing replaces proprietary sync and cloud services with something
open, trustworthy, and decentralized.
Your choose where it is stored,
if it is shared with some third party,
and how it’s transmitted over the Internet.

>**NOTE:** You might first think of Nextcloud when considering file synchronization
>but check out the video
>"[Why We Use Syncthing, The Open Source Private File Syncing Tool instead of NextCloud][11]"
>to see why you should consider Syncthing.

* [Adding 3rd Party Sources to your Synology Diskstation](https://www.youtube.com/watch?v=nlbM5q7FHpM)
* [Setup and Review of SyncThing, The Open Source File synchronization tool](https://www.youtube.com/watch?v=iFh27uPsYRw)
* [Open Source File Sync: Getting Started Tutorial With Syncthing on Windows & Linux](https://www.youtube.com/watch?v=O5O4ajGWZz8)
* [How to Install Syncthing on Your Synology NAS](https://mariushosting.com/how-to-install-syncthing-on-your-synology-nas/)
* [Syncthing Install and Set up on Synology! (2021)](https://www.youtube.com/watch?v=uhmi96PesXM)
* [Backing Up My Home Server Files - Setting Up Syncthing](https://www.youtube.com/watch?v=V4kWJ8JcdtM)
* [Configuring SyncThing Untrusted (Encrypted) Devices](https://www.youtube.com/watch?v=hT373XZHNvk)



-------



# How to Clone Your Linux Hard Drive
By cloning your Linux hard disk drive,
you create an exact disk image that can be restored later.
But how do you clone your Linux hard drive?
The webpage ["How to Clone Your Linux Hard Drive: 4 Methods"][38] can provide some insights.

# Clonezilla (Disk Cloning)
[Clonezilla][12] is a partition and disk imaging/cloning program
similar to [Acronis True Image][13] or [Norton Ghost][14].
It can be used to do system deployment or a bare metal backup / recovery.

There are several types of Clonezilla:

* **[Clonezilla Live][15] -** This is suitable for single machine backup and restore
It allows you to use the CD/DVD or USB flash drive to boot and run Clonezilla.
* **[Clonezilla Lite Server][16] -** Suitable for massive deployments.
It allows you to use Clonezilla live to do massive clonnning.
* **[Clonezilla SE (Server Edition)][17] -** Suitable for massive deployments

While it is less user friendly than other imaging tools that run in the native OS,
it is particularly robust and trustworthy,
given it’s one of the most widely used imaging tools for both Windows and Linux,
heavily used by IT administrators,
and offers powerful functionality to automate backup and restore across a network.
Some of its features are:

* Disk Imaging: You can create an ISO image of the current disk or partition
and restore the image to disk at any time.
* Disk Cloning: Allows you to clone directly between two disks
without creating a disk image.
* Disk Encryption: Image can be encrypted with `ecryptfs`, and saved-to or read-from
local disk, SSH server, Samba server, NFS server, WebDAV server or AWS S3 storage.
* It only saves & restores used blocks in the hard disk, therefore, increasing the clone efficiency.
* Supports lots of file systems like ext4, XFS, Btrfs, F2FS, FAT32, NTFS, HFS+, UFS.
* Supports MBR and GPT partition table.
* Supports BIOS and UEFI firmware.
* Clonezilla SE allows you to do massive system deployment over the network.
* Unattended Mode: You can avoid the data entry menu UI,
allowing almost all steps can be done via commands and options.

* [Bare metal backup and restore with Clonezilla](https://www.technorabilia.com/bare-metal-backup-and-restore-with-clonezilla/)
In my case,
I'm going to backup my desktop Linux system hard drive to my Synology NAS over SSH.
The NAS and the system from which you create the backup must be on the same network
or reachable from you network (e.g. in the cloud).
I'll need a directory within my NAS to store the backup image,
which I called `Clonezilla-images`,
where I will save all my various Clonezilla backups.
I'll also need to know my NAS IP address, a user with access rights, and that useres password.

* [Clonezilla](http://www.diskimagingreview.com/clonezilla/)
* [How to Use Clonezilla Live to Back Up Your Hard Drive](How to Use Clonezilla Live to Back Up Your Hard Drive)
* [Cloning/Imaging Hard Disks with Clonezilla Live](https://www.youtube.com/watch?v=EW4_tqBaczw)
* [How to save a Clonezilla full disk image to a server/NAS over SSH](https://danielrosehill.medium.com/how-to-save-a-clonezilla-full-disk-image-to-an-nas-over-ssh-771beb37f08b)
* [Using rsync to sync Clonezilla backup images to NAS (Synology DS920+)](https://www.youtube.com/watch?v=VpNlnkZRwT4)
* [Clonezilla LAN backup (over SSH): Linux host to Synology NAS](https://www.youtube.com/watch?v=cfMspUjk9ms)
* [Virtual Machine or Physical Machine Migration With Clonezilla](https://www.youtube.com/watch?v=wSTk9BLwF5k)

* [How to save a Clonezilla full disk image to a server/NAS over SSH](https://danielrosehill.medium.com/how-to-save-a-clonezilla-full-disk-image-to-an-nas-over-ssh-771beb37f08b)
* [How to back up hard drives for disaster recovery with Clonezilla]( https://www.xmodulo.com/how-to-back-up-hard-drives-for-disaster-recovery-with-clonezilla.html)

## Boot to Clonezilla via USB Drive
* [Bare metal backup and restore with Clonezilla](https://www.technorabilia.com/bare-metal-backup-and-restore-with-clonezilla/)

#### Step 1: Enable SFTP in Synology - DONE
You need to make sure that SFTP is enabled on Synology.
Within the Synology DMS, goto
**Control Planel** >  **File Services** > **FTP** tab > **SFTP** section.
Make sure to hit the **Apply** button at the bottom of the screen.

>**NOTE:** When SFTP is not enabled, you'll get an error within Clonezilla
>and it will not be clear what the root cause is.
>You'll get the message "Clonezilla connection reset by peer".
>See "[I can SSH into a remote host but get "Connection reset by peer" with SSHFS, what do I miss?][06]".

#### Step 2: Download Ventoy (Optional) - DONE
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
>Ventoy2Disk.sh will prompt you for update if the USB drive already installed with Ventoy.

* [How to Create a Multiboot USB with Ventoy Fast, Simple, and Easy Guide](https://www.youtube.com/watch?v=z1FyoCswwAc)
* [Ventoy: How to Create a Multiboot USB Drive with Multiple ISO Files](https://linuxiac.com/ventoy-create-bootable-usb/)

#### Step 3: Download Clonezilla Live to Flash Drive - DONE
[Download the Clonezilla Live][05] ISO image and place it on your USB flash drive.
In my case, I copied the ISO into the Ventoy USB drive I created earlier.

>**NOTE:** I found that my desktop computer didn't always sense the
>Ventoy bootable USB drive, and therefore, boot from it.
> I discovered that I had to completely power down my system by unpugging it from the main power.
> Only then could I assure the USB would boot.

#### Step 4: Boot Target System Using Flash Drive - DONE
Now put the flash drive into the target machine and boot the system.
The system will first boot into Ventoy where you will be given a list of images.
Select the Clonezilla ISO, Clonezilla will be loaded, and then executed.

Clonezilla will now ask you a lengthy series of questions.
My answer to those questions are as follow:

8KQT!x28imwqy94

* Clonezilla live (VGA with large font & RAM)
* Keep
* Start Clonezilla
* device-image
* ssh_server
* wired
* eth0
* dhcp
* 192.168.1.201 = synology ip address
* 22
* admin-jeff = synology user with root access rights
* /Clonezilla-images
* password = synology admin-jeff user
* 'Enter' to continue
* Beginner
* savedisk
* desktop-….img
* 'Space' to mark your selection of sda and sdc
* -zip
* -sfsck
* yes
* -senc
* -p choose

#### Step 5: Restoration

## Boot Directly into Clonezilla
You don't have to boot into Clonezilla from a USB drive.
You can boot into it from within your running running Linux system.

It’s also possible to automate the Clonezilla live setup to create or restore a disk image backup.
This will requires manually editing configuration files,
but one set-up, you'll be able to repeatedly run backup with minimal manual intervention.
It is the establishment of automated backup process is the main theme of this section.

There are two config files in the syslinux directory in Clonezilla live. If booting from a USB drive, one should edit syslinux/syslinux.cfg, and if booting from a CD/DVD, use syslinux/isolinux.cfg. This config file should be edited to add all the steps normally done manually from the Clonezilla GUI, as command line options.

Syslinux is a boot loader for the Linux operating system which operates off an MS- DOS/Windows FAT filesystem. It is intended to simplify first-time installation of Linux, and for creation of rescue and other special-purpose boot disks.

Check out
* http://www.diskimagingreview.com/clonezilla/

Sources:
* [How to install and use Clonezilla on Ubuntu 20.04](https://nextgentips.com/2021/12/06/how-to-install-and-use-clonezilla-on-ubuntu-20-04/)
* [How to Use Clonezilla Live to Back Up Your Hard Drive](https://www.linuxhowto.net/how-to-use-clonezilla-live-to-back-up-your-hard-drive/)
* [How to save a Clonezilla full disk image to a server/NAS over SSH](https://danielrosehill.medium.com/how-to-save-a-clonezilla-full-disk-image-to-an-nas-over-ssh-771beb37f08b)

#### Step X: Install Clonezilla
Update your package repositories in order to get the latest package information,
and then do the Clonezilla install:

```bash
# update your package repositories
sudo apt update && sudo apt -y upgrade

# do the clonezilla install
sudo apt -y install clonezilla
```

#### Step X:
You can launch Clonezilla from terminal by running clonezilla command:
`sudo clonezilla`.
Once launched, it will ask to select from
same screen menus you navigated when booting into Clonezilla via a USB drive
(documented above).

## Automated Clonezilla Backup/Restore
* [Preseed options to do job after booting](https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/05_Preseed_options_to_do_job_after_booting)

So far, all of the above are manual ISO backups using Clonezilla.
Doing this frequewntly can be quite cumbersome,
especially when you need to do backup frequently.
You might want ot automate the process and skip the manual setup.
You could then run unattended backup with Clonezilla.
This is possible, but not to be undertaken by the novice Linux user.

You can automate Clonezilla backup with the following:

* Place the Clonezilla ISO on your harddrive you wish to backup.
* have a second hard drive to recieve your backup (2nd drive could be internal, external, or network drive)
* Use the Grub bootloader (aka `grub-install`) to boot into Clonezilla
* Using crontab, schedule you backups.

#### Step X: Install Clonezilla ISO
Create a directory on the root of your drive called `isos`
and copy Clonezilla there from its [download site][37]
(in my case this was stable-3.0.0-26).

```bash
# create directory for clonezilla iso
sudo mkdir /isos

# place a copy of Clonezilla (iso file) into /isos
wget https://osdn.net/frs/redir.php?m=rwthaachen&f=clonezilla%2F77349%2Fclonezilla-live-3.0.0-26-amd64.iso
```

Sources
* [Preseed options to do job after booting](https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/05_Preseed_options_to_do_job_after_booting)
* [Create Automated Backup with Clonezilla or Easier Alternative](https://www.ubackup.com/backup-restore/clonezilla-automated-backup-1021.html)
* [AUTOMATED CLONEZILLA BACKUP/RESTORE](https://whatthefdidido.wordpress.com/2016/05/04/automated-clonezilla-backuprestore/)
* [How to create an automated and unattended Clonezilla Restore solution](https://stackoverflow.com/questions/65848953/how-to-create-an-automated-and-unattended-clonezilla-restore-solution)



-------



* [Synology NAS Setup & Configuration Guide!](https://www.wundertech.net/synology-nas-initial-setup-ultimate-guide/)

# Duplicati
Duplicati is a backup client that securely stores encrypted, incremental, compressed remote backups of local files on cloud storage services and remote file servers. Duplicati supports not only various online backup services like OneDrive, Amazon S3, Backblaze, Rackspace Cloud Files, Tahoe LAFS, and Google Drive, but also any servers that support SSH/SFTP, WebDAV, or FTP.
With Duplicati, you have backup software that not only can backup to a network drive,
but you can do this with mapping a network drive via WebDAV.

## WebDAV
Web Distributed Authoring and Versioning (WebDAV) is an extension of the Hypertext Transfer Protocol(HTTP)
that allows clients to perform remote Web content authoring operations.
For users who need to publish a lot of content,
WebDav reduces the dependency on CMS systems and makes uploading/downloading easier.

* [How to Map Synology NAS Drive Outside the Local Network (Over Internet)](https://www.wintips.org/how-to-map-synology-nas-drive-outside-the-local-network-over-internet/)

## Install Duplicati

* [Duplicati a Set it and Forget it backup tool for local and remote backups of your system!](https://www.youtube.com/watch?v=N1NRvg4KaDE)
* [Backup in Linux Servers - Docker Volumes, and Databases](https://www.youtube.com/watch?v=JoA6Bezgk1c&t=56s)
* [Setup Duplicati on Synology](https://www.youtube.com/watch?v=YVUvLZpKhQ0)
* [Backup Your Docker Server NOW! - Setup and Configure Duplicati](https://www.youtube.com/watch?v=--lYljZzrCQ)
* [Different ways to make a Duplicati backup](https://blog.files.fm/different-ways-to-make-a-duplicati-backup/)

#### Step X: Enable WebDAV on your Synology - DONE
We'll first setup WebDAV on the Synology.

* Go to **Package Center** search for "Web" and to install **WebDAV Server**.
* Launch **WebDAV Server** and tick the **Enable HTTPS** checkboxes and use the default port of `5006`.
* Also tick **Enable DavDepthInfinity** and **Enable WebDAV log**
* Save the settings by selecting **Apply**.

Now lets establish a user for the WebDAV feature:

* Go to **Contol Panel** > **Users & Groups** select "jeff" and **Edit**.
* Select the **Applications** tab and give the user access to WebDAV by ticking **Allow** and the hit **Save**.

#### Step X: Create Synology Folder for Backup - DONE
Now we need to create the folder where the backups will be stored.
I'm going to create a root folder for Duplicati
and subfolders for the computers that will be using Duplicati for backups.

* Go to **Contol Panel** > **Shared Folder** > **Create** tab > **Create Shared Folder** and name it "Duplicati".
* Disable **Enable Recycle Bin** and hit **Next**.
* Continue hiting **Next** until the **Configure user permissions** screen.
Here you give user "jeff" **Read/Write** access and hit **Apply**.
* Go to **File Station** > **Duplicati** > **Create** > **Create Folder** > name it **desktop**
for the computer the backup will be coming from.

#### Step X: Configure Duplicati
Assuming you have Duplicati installed on your source computer,
now we'll configure Duplicati to stream its backup to the Synology WebDAV agent.

* Select **Add backup** give it a name and discription but no need to encrypt since the data remains on your LAN.
* Click thru to **Backup destination** > **Storage Type** is WebDAV and enable **Use SSL**.
* **Server and port** is `192.168.1.201` and `5006`.
* **Path on server** is `/Duplicati/desktop` and when prompted with
"The folder /Duplicati/desktop does not exist. Create it now?", respond with **Yes**.
* Before you preform any test, click **Advance options** and select "accept-any-ssl-certificate".
After that, hit **Test connection**.
* Hit **Next** and come to "Source Data".  Check off "source", set the **Filters** and **Exclude** as you see fit.
* On the "Schedule" page, **don't** check "Automatically run backups" yet.
Run the backup manually until your confident that you have the setup right.

Sources:
* [How to Enable WebDav Service On Synology NAS?](https://www.multcloud.com/help/enable-webdav-service-on-synology-nas.html)
* [How do I access files on Synology NAS with WebDAV?](https://kb.synology.com/en-me/DSM/tutorial/How_to_access_files_on_Synology_NAS_with_WebDAV)


-------



## Linux Distro
* [Best Linux Distro for Server, my favorite ones](https://www.youtube.com/watch?v=E6Jyj6whge4)



# Network Attached Storage (NAS) Related Stuff
* [How to build your own Raspberry Pi NAS](https://www.techradar.com/how-to/computing/how-to-build-your-own-raspberry-pi-nas-1315968)
* [Create a hardened Raspberry Pi NAS](https://blog.alexellis.io/hardened-raspberry-pi-nas/)
* [OpenMediaVault](https://www.openmediavault.org/)
* [FreeNAS vs OpenMediaVault](http://www.freenas.org/freenas-vs-openmediavault/)
* [Video: Raspberry Pi 3 NAS 4TB - DIY Step by Step](https://www.youtube.com/watch?v=SUbaJ-Tjg5s)
* [Automating backups on a Raspberry Pi NAS](https://opensource.com/article/18/8/automate-backups-raspberry-pi)
* [How-To How to Turn a Raspberry Pi Into a NAS for Whole-Home File Sharing](https://www.pcmag.com/news/372164/how-to-turn-a-raspberry-pi-into-a-nas-for-whole-home-file-sh)
* [Sabrent USB 3.0 to SSD / 2.5-Inch SATA Hard Drive Adapter](https://www.amazon.com/Sabrent-2-5-Inch-Adapter-Optimized-EC-SSHD/dp/B011M8YACM)
* [PiNAS dual drive Raspberry Pi NAS](https://www.geeky-gadgets.com/raspberry-pi-nas-17-02-2020/)
* [5 cool things you can do with your router's USB port!](https://www.youtube.com/watch?app=desktop&v=xNyW0Agub-g)




# Network Attached Storage (NAS)

## NAS vs SAN
Network Attached Storage (NAS)
Storage Area Network (SAN)

* [NAS vs SAN - Network Attached Storage vs Storage Area Network](https://www.youtube.com/watch?v=3yZDDr0JKVc)

## Build or Buy?
* [Should you build your own NAS or buy one? Unraid vs. TrueNAS vs. Synology](https://9to5toys.com/2021/06/04/unraid-vs-synology-vs-truenas/)
* [Synology vs TrueNAS - What NAS is right for you?](https://www.youtube.com/watch?v=O0FIBbMYoM0)
* [What Synology Should You Buy? | Everything You Need To Know!](https://www.youtube.com/watch?v=-RbAiqWf-mQ)

* [Unraid](https://unraid.net/)
* [TrueNAS](https://www.truenas.com/)
* [Synology](https://www.synology.com/en-us)

## Synology DiskStation DS220+ vs. DS220j
Synology has a wide variety of options for a home or small office NAS.
Synology has a highly respected web-based operating system, DiskStation Manager.
In the 2-bay category, [DiskStation DS220+][01] is the most powerful option available,
but the [Diskstation DS220j][02] offers excellent value.
Both these NAS are excellent chooses for my needs,
but the DS220+ has better hardware, better backup tools, can support more cameras,
better ability to support applications.
Also, its appears to me that the DS220j is reaching its end-of-life and will be replace with the DS220+.

Sources:
* [Synology DS220+ vs DS220j NAS Comparison](https://www.youtube.com/watch?v=-5a58pxXqMQ)
* [Synology DiskStation DS220+ vs. DS220j: Which should you buy?](https://www.androidcentral.com/synology-diskstation-ds220-plus-vs-diskstation-ds220j)
* [Synology DiskStation DS220+ vs. DS220j: Which NAS is better?](https://www.windowscentral.com/synology-diskstation-ds220-vs-ds220j)
* [Synology DiskStation DS220j and DS220+ Review](https://simply.reviews/synology-diskstation-ds220j-and-ds220-review/)
* [Spec Comparison](https://www.synology.com/en-us/products/compare/DS218play/DS220+/DS220j/DS720+)

# Security Firewall and VPN Router
* $190 - [Synology 2 bay NAS DiskStation DS220j](https://www.amazon.com/dp/B0855LMP81)
* $300 - [Synology 2 Bay NAS DiskStation DS220+](https://www.amazon.com/Synology-Bay-DiskStation-DS220-Diskless/dp/B087ZCBWFH)

## Nextcloud vs Synology vs FreedomBox
All of them provide self-hosting your own cloud.
You can host Nextcloud on Synology, but you can't host Synology on Nextcloud.

Nextcloud is Self hosted and maintained by the open source community.
You are far more likely to find a client/solution for anything when looking at Nextcloud.
Nextcloud will probably be maintained a lot longer than the apps Synology/QNAP offer for your 2017 two bay SoHo NAS.

Some claim the Nextcloud file-syncing isn't reliable (calendar and contact sync never worked correctly).
People like their Synology NAS systems, not just because of the file sharing features
 but also for the reliable Calendar and Contacts sync, there’s also a feature to make it available from outside of your home network.

A Synology (or any NAS) is internal to your main network and is where your bulk data lives. It has special filesystems and other low level code for dealing with physical hard drives and data is shared with other local hosts over SMB or NFS.

While Synology provides Hardware Appliances, Nextcloud is a software solution.
Also the goal is different.
While Synology is a NAS with benefits,
Nextcloud wants to be an alternative to the cloud-solutions from Google/Microsoft/Dropbox.
A proper comparison for Synology is with one of the following:
[FreeNAS](https://www.freenas.org/)
[Unraid](https://unraid.net/)
[OpenMediaVault](https://www.openmediavault.org/)

They are not really comparable.
Only in that both provide different ways of storing files and provide access to them.

* [Nextcloud vs Synology](https://kevq.uk/install-nextcloud-on-synology/)
* [How To Install Nextcloud On A Synology NAS](https://kevq.uk/install-nextcloud-on-synology/)
* [How to Self-host the Password Manager Bitwarden on a Synology NAS!](https://www.wundertech.net/how-to-self-host-the-password-manager-bitwarden-on-a-synology-nas/)

# Synology NAS Encryption
Synology encryption is bad??
* [Synology NAS Encryption: Forensic Analysis of Synology NAS Devices](https://blog.elcomsoft.com/2019/11/synology-nas-encryption-forensic-analysis-of-synology-nas-devices/)




-----



# Selecting Disk Drives

## CMR vs SMR Hard Drives
When it comes to hard drives, its more than access speed and cost.
Another thing to consider is Shingled Magnetic Recording (SMR) or Conventional Magnetic Recording (CMR).
Because the different recording methods behave differently,
you should pick the recording technology based on you usage pattern.
For RAID arrays, there is a bigger consideration.
In some cases, a [RAID controller may refuse to repair the array of an SMR drive][19] is used instead of a CMR.
CMR hard disks are a good choice when data is to be stored at high transfer rates
or particularly large amounts of data.
This includes a large number of activities from music streaming and image processing to use for NAS servers.

Sources:
* [CMR vs SMR Hard Drives in Network Attached Storage (NAS)](https://www.buffalotech.com/blog/cmr-vs-smr-hard-drives-in-network-attached-storage-nas)
* [SMR? CMR? Which Hard Drive is best for which purpose?](https://www.reichelt.com/magazin/en/smr-cmr-which-hard-drive-is-best-for-which-purpose/)
* [WD Red SMR vs CMR Tested Avoid Red SMR](https://www.servethehome.com/wd-red-smr-vs-cmr-tested-avoid-red-smr/)




-----



# Selection
* [Synology DiskStation DS220+][01]

## DSM7

## Btrfs
 Btrfs, short for "B-Tree File System" (and frequently pronounced "butter" or "butter eff ess") is a computer storage format that combines a file system based on the copy-on-write (COW) principle with a logical volume manager (not to be confused with Linux's LVM), developed together.

Synology has implemented Btrfs on its NAS solutions.
[Btrf provides various benefits][03] from efficient drive storage, file self-healing,
high frequency data snapshots, self-service data recovery, etc.

* [Introduction to Btrfs Filesystem](https://linuxhint.com/btrfs-filesystem-beginner-guide/)
* [Examining btrfs, Linux’s perpetually half-finished filesystem](https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/)

## Raspberry Pi Backup to Synology
* [How do I back up a Linux device to my Synology NAS?](https://kb.synology.com/en-my/DSM/tutorial/How_to_back_up_Linux_computer_to_Synology_NAS)
* [Automatic backups for Raspberry Pis to a Synology NFS share](https://florianmuller.com/automatic-backups-for-raspberry-pis-to-a-synology-nfs-share)

## Apps to Install on Synology NAS
* [How to Install Netdata on Your Synology NAS](https://mariushosting.com/how-to-install-netdata-on-your-synology-nas/)

## Synology Surveillance Station
* [Synology Surveillance Station in 2021: (Still) the Best DIY Security Cam System](https://dongknows.com/synology-surveillance-station-review/)

## Synology NAS Security
* [How to Secure your Synology NAS](https://www.youtube.com/watch?v=qCULKjaLf08)
* [PROTECT YOUR FILES - How to Protect your Synology NAS from Ransomware / Crypto ATTACK](https://www.youtube.com/watch?v=uausl6HeFjg)
* [Ransomware Protection — Synology Webinar](https://www.youtube.com/watch?v=DUwUnyr9Om8)

# NAS Drives
* [Seagate IronWolf HDD Review - Happy Drives, Happy Life](https://www.youtube.com/watch?v=uKQhTgsYsM4)

# NAS Backup
* [Hyper Backup](https://www.synology.com/en-us/dsm/feature/hyper_backup)
* [YOU NEED TO BACKUP YOUR NAS - Backing up a Synology NAS for home users](https://www.youtube.com/watch?v=ETUwV4dS7Z8)
* [Backblaze](https://www.backblaze.com/cloud-backup.html)
* [Synology HyperBackup to External HardDrive](https://www.youtube.com/watch?v=42tG5lf-a_E&t=0s)
* [Backup Your Synology NAS to the BackBlaze Cloud with HyperBackup!](https://www.youtube.com/watch?v=apOX1rBu_Fg)

# Synology NAS Wake On LAN
Wake-on-LAN (WOL) is an Ethernet standard that allows a machine to be turned on by a network message. The idea is to send from a server of your network (for example, a Raspberry Pi) a magic message to the Synology NAS in order to wake it up.

* [How to Wake up a Synology NAS from an Ubuntu server](https://oastic.com/posts/how-to-wake-up-a-synology-nas-from-an-ubuntu-server/)
* [How To Turn On PC Remotely](https://www.technewstoday.com/turn-on-pc-remotely/)

# Synology Photos
* [I Switched To Synology Photos](https://www.youtube.com/watch?v=J9QuS_ePxAQ)
* [How to Setup the New Synology DSM7 Photos & Can it Replace Google Photos?](https://www.youtube.com/watch?v=5rQnQOJ3hLs)
* [How to setup Synology DSM7 photos for Sharing with Family](https://www.youtube.com/watch?v=o4ivCKrh_ik)

# VPN Server
* [Create VPN Server on Synology NAS](https://www.youtube.com/watch?v=1aaqqw3eQac)

# SMB



----



# DiskStation Manager (DSM) 7.0
* [DiskStation Manager (DSM) 7.0](https://www.synology.com/en-us/DSM70)

```bash
# web user interface for dms
google-chrome http://192.168.1.201:5000

google-chrome https://192.168.1.201:5001
```

# Setup of Synology NAS
* [How to Setup a Synology NAS for the first time in DSM 7 (Complete Guide for 2021+)][20]

* [Synology NAS Setup Guide 2022 #1 - DSM 7, RAID, VOLUMES, SHARES, MAPPED DRIVES](https://youtu.be/pRRcGoXhLLQ)
* [Synology NAS Setup Guide 2022 #2 - Snapshots, NAS to NAS/CLOUD/USB, SaaS Backups & Sync](https://youtu.be/-KIkwxJxL4w)
* [Synology NAS Setup Guide 2022 #3 - Photography, Indexing, Sharing & Moving from Google](https://youtu.be/0Jo_KwFvGVM)
* [Synology NAS Setup Guide 2022 #4 - Music Audio, Indexing, Sharing and Streaming over DLNA](https://youtu.be/kCnO-SeCqQ4)
* [Synology NAS Setup Guide 2022 #5 - Video Station, Stream to Fire TV, DLNA and Indexing TV/Films](https://youtu.be/O8rsO-wNvzY)
* [Synology NAS Setup Guide 2022 #6 - Setting Up Plex Media Server Right First Time](https://youtu.be/XUXJFu1LtJ4)
* [Synology NAS Setup Guide 2022 #7 - Setting Up Surveillance Station, Cameras, Control and Alert](https://youtu.be/glCr8c5yaTQ)
* [Synology NAS Setup Guide 2022 #8 - Setting Up an iSCSI Target and a Storage LUN](https://youtu.be/DampyCKp-Bc)

* [Synology NAS Setup Guide 2022 – Part 1, Setup, Users, Updates, Remote Access And Security Settings](https://nascompares.com/guide/synology-nas-setup-guide-2022-part-1-setup-users-updates-remote-access-and-security-settings/)

* [How to Use NFS to Mount Synology to Linux as a Storage Space?][21]
* [Top 8 Synology Features for Home Users (DSM7)](https://www.youtube.com/watch?v=apE6eyQzHdg)

## Setup of Synology NAS: Foundational
This covers setting up a Synology NAS for the very first time
[Synology's Diskstation Manager (DSM) Verizon 7](https://www.synology.com/en-us/DSM70).

#### Step 0: Power On/Off, Restart, etc.
Here are two ways you can restart and shutdown your Synology NAS:

1. From the web user interface (`http://192.168.1.201:5000`), click the "Options" icon at the top right.
2. Using the blue power button on the frount of the NAS, press-and-hold until you hear a beep.

The NAS will grasfully power down.
To start the NAS up again, simply press the power button once again.

* [How To Restart or Shutdown Your Synology NAS](https://www.youtube.com/watch?v=ICs8xnCMUM0)

#### Step 1: Assemble, Power-Up, and Initial DSM Install - DONE
I just followed the instruction that came in the box
([Hardware Installation Guide][39],
[Synology DS220+ NAS Setup: Synology Admin, Quick Connect and Creating Volume][40]) for the DS220+.
After a approximately a one minute boot-up, I got the following information:

* **Server Name:** SynologyNAS
* **IP Address:** 192.168.1.56
* **MAC Address:** 90:09:d0:00:4e:29
* **Serial Number:** 2170RLRB7J3SZ
* **DSM Version:** 6.2-25556
* **Model Name:** DS220+

For my intital / baseline setup of the NAS,
I closely followed [this video][20] but I choose to use a RAID 1 storage configuration
and I didn't setup any Snapshot Replication at this time.
Also, the video didn't show how to access the Synology NAS from a Linux computer
(the video references SMB which is generally used with Windows and MAC).
I will address this in a latter step.

Also during this step, I initiated my [Synology Account][04].
Your going to need it for some of the latter steps to follow.

>**NOTE:** I wouldn't do any of the following steps until the RAID setup process is complete.
>You'll have a visual clue that this process is active because the two disk drive lights
>will be constantly blinking.
>Also look within **Main Menu** > **Resource Monitor** > **Task Manager** > **RAID process**
>and you see "md2_repair" (or something concerning "repair"), then it is still processing the RAID setup.
>This process took about 8 hours for my 8 terabyte drives.

#### Step 2: Assign a Static IP Address to the NAS - DONE
The quick and easy way to get the NAS up and working is to allow the IP address to be assigned via DHCP
To deal with the changing IP address that could occur with DHCP,
Synology DMS software does have a [DDNS (Dynamic Domain Name System) feature][22].

While this works, it best practice to assign a static IPs to a server like a NAS.
This way you find the NAS the same address every time,
rather than a new address being set dynamically by [DHCP][23].
My home router is my DHCP server (`192.168.1.1`) and I have reserved the IP range 10 to 199
for dynamically allocated IP addresses.
This leaves IP range 200 to 255 for static IP addresses.
I'm using `192.168.1.201` for my NAS box.

I used the procedure outline in sources below to update the NAS IP address.

* [Synology NAS - Assign A Static IP Address To A Synology NAS](https://www.youtube.com/watch?v=lZJchA2YAHI)
* [Synology: How to Assign Static IP to Your NAS](https://mariushosting.com/synology-how-to-assign-static-ip-to-your-nas/)

#### Step 3: Eanble SSH Access to NAS - DONE
The Synology NAS will allow Telnet and SSH access if the login is within the administrators group.
Enable SSH terminal via **Control Panel** > **Terminal & SNMP** > **Eanble SSH service**.

Test it our via `ssh admin-jeff@192.168.1.201`
and use the password for `admin-jeff` entered during the NAS setup.

#### Step X: Enabling SMB to Access NAS Files
Linux (UNIX) machines can also browse and mount SMB shares. Note that this can be done whether the server is a Windows machine or a Samba server!

An SMB client program for UNIX machines is included with the Samba distribution. It provides an ftp-like interface on the command line. You can use this utility to transfer files between a Windows 'server' and a Linux client.

Most Linux distributions also now include the useful smbfs package, which allows one to mount and umount SMB shares.

```bash
sudo apt install smbclient
```


* [NAS Performance: NFS vs. SMB vs. SSHFS](https://blog.ja-ke.tech/2019/08/27/nas-performance-sshfs-nfs-smb.html)
* [SMB vs NFS vs AFP vs iSCSI - What are they and which should you use](https://www.youtube.com/watch?v=JXASmxGrHvY)

* [Mount Synology NAS with cifs-utils on Ubuntu](https://atlassc.net/2021/08/10/mount-synology-with-cifs-utils-on-ubuntu/)
* [Samba/CIFS to Synology NAS not working: no write access after upgrade from 16.04 to 20.04](https://askubuntu.com/questions/1287681/samba-cifs-to-synology-nas-not-working-no-write-access-after-upgrade-from-16-04)

#### Step 4: Enabling NFS to Access NAS Files
So far, the only way I can access files on my NAS is via the Sonology DSM browser.
I want to use my Linux desktop computer to access they NAS within my home local network.
I can do this via the [Network File System (NFS)][24] or SMB
(call [Samba][25] on Linux and is a free software re-implementation of the [SMB networking protocol][26]).
The article "[NFS vs SAMBA vs CIFS][27]" and "[NFS vs SMB – Which one to choose?][28]" pointed me to NFS

To get this working, I followed the procedures outlined [here][21].
On the NFS Server, which is the NAS, I enabled NFSv4
and within **Shared Folder** > **homes** > **Edit** > **NFS Permissions** > **Edit**
I set **Squash** to "".

The NFS Client is my Ubuntu desktop Linux box,
and I configured it with these commands:

```bash
# install the required nfs utilities
sudo apt install nfs-common

# make a mount point for the nas filesystem and set permissions
sudo mkdir /mnt/NAS
sudo chmod a+r u+w /mnt/NAS

# mount the nas filesystem on you desktop linux
sudo mount 192.168.1.201:/volume1/homes/jeff /mnt/NAS

# unmount the file system
sudo umount /mnt/NAS

# if the above doesn't work, unmount the file system via this
# also do a reboot to clean-up any mess from the '--force --lazy'
sudo umount --force --lazy /mnt/NAS
sudo reboot
```

Within the Nautilus file manager,
create a new bookmark on the left hand menu window for the NAS folder.

**NOTE:** See the following about doing the `mount` within `fstab` -
https://www.mjwebs.com/blog/configure-nfs-mount-with-synology-nas-on-ubuntu-18-04
https://maestropandy.wordpress.com/2019/07/17/how-to-set-up-an-nfs-mount-on-ubuntu-16-04/


----



## Setup of Synology NAS: Replications & Backups
Data **Backup** involves making a copy or copies of data
and storing them off-site, with assured safety, in case the original is lost or damaged.
It done in case of a major outage, it minimizes but doesn't prevent some data loss,
and typically requires a lengthy amount of time to restore.

Data **Replication** is the act of copying data and then moving data to a site
where it can be stored and restored rapidly,
at least much more rapid than a data Backup.
It is done in case of minor or isolated data loss,
it can be done in such a way that data loss is very small or none at all,
and restoration can be done within minutes.

At the heart of Synology backup & replication methodology is the concept of a **Snapshot**.
A snapshot leverages the DMS [Btrfs file system][03] to create point-in-time copies of files.

I'll be use [Active Backup for Business][30] for data replication.
I'll use [Hyperbackup][33] for data backup.

#### Step X: Backup Synology NAS Configuration - DONE
You can set up the system to automatically save NAS configuration files to your
[Synology Account][04] (latest backup, no versioning)
or manually export them to a local computer.
This allows you to save various settings on you NAS
(e.g. DNS users, groups, file service settings, etc.) and restore them at a later date.
I followed the video "[Backup Your Synology NAS System Configuration In DSM 7][32]"
to establish a regular backup of my NAS / DMS configuration for emergency restoration.

>**NOTE:** You may have already setup this backup routine in Step 1.
>I include here for completeness in this "Replications & Backups" section.

#### Step X: Install Active Backup for Business - DONE
Synology's [Active Backup for Business][30] does replication tasks for physical and virtual computer environments.
It a new feature in 2021, making [Synology's legacy backup methodologies][31] obsolte.
I followed the procedures outlined in the articles
"[How to Back Up a Linux PC to a Synology NAS using Active Backup for Business][29]"
and "[How to Use Synology to Back Up Your Linux Computer][34]".

To back up your Linux computer with Active Backup for Business,
you will have to log in to your Synology NAS.
For maximum control & security,
I create a dedicated user account on your Synology NAS for each Linux computer I will be backing up.
The user name took the form `backup-<host_name>`.

To install the Active Backup for Business client on my Linux desktop computer,
I used the following steps:

```bash
# unzip the downloaded file
unzip "Synology Active Backup for Business Agent-2.2.0-2074-x64-deb.zip"

# enter the directory and execute the installer
cd "Synology Active Backup for Business Agent-2.2.0-2074-x64-deb"
sudo ./install.run

# see all the commands that you can run using the client
sudo abb-cli -h

# connect your linux computer to synology nas to support active backup for business
sudo abb-cli -c
```

If you need to uninstall the client, you should do the following:

```bash
# uninstall the active backup for business client
sudo dpkg -r synology-active-backup-business-linux-service   # to uninstall the backup service
sudo dpkg -r synosnap                                        # to uninstall the driver
```

#### Step X: Do a Bare-Metal Backup - DONE
I created a task within Active Backup for Business using the type "Entire device".
I believe this is a [bare metal backup][35] but it appeared to fail
and completed with the status "Partially complete".
I did some poking around the web for what this meant but didn't find anything useful.
I then happen upon the comment from Martin Ehlert at the bottom of [this post][29].
He states that currently, not all system types are supported.

So it appears Synology has more work to do on Active Backup for Business!

#### Step X: Do a File Backup
PC and physical server backup tasks only support bare-metal and volume-based backup,
which does not allow the backup of only a specific file.

Active Backup for Business PC backup and Physical Server backup allow you to back up full devices (bare-metal backup) or full volumes.
If you do not wish to back up full devices or volumes (or you don't want to install the Active Backup for Business agent),
you can use the File Server backup functionality to perform agentless backups of folders
For detailed instructions on this process, see the article
"[How do I back up individual folders on Windows servers using Active Backup for Business][36]".

`backup_user` needs to have a password
I created this account via `sudo adduser backup_user --disabled-password -u 400`.
https://unix.stackexchange.com/questions/597946/how-to-add-password-to-an-account-that-was-created-using-disabled-password
password = ek3N9#4s94*

check this out "Enabling Rsync Accounts" - https://kb.synology.com/en-us/DSM/help/DSM/AdminCenter/file_rsync?version=6

`backup_user` must have read access to all files to do a complete backup.
Only root level access can read all files, so [`rsync` needs a passwordless `sudo`](https://askubuntu.com/questions/719439/using-rsync-with-sudo-on-the-destination-machine).

The logic goes like this:
* `rsync` should be run as `root` on the destination machine.
* You can't login as `root` via SSH, since that's disabled for security purposes.
* The user on the destination machine must use `sudo`
but the automation can't respond to the password prompt that is typical with the use of `sudo`.

The resolution:
* Edit the `/etc/sudoers` file via `sudo visudo` ([why visudo?](https://askubuntu.com/questions/625821/must-use-visudo))
* Then, on the source machine, specify that `sudo rsync` shall be used:
`rsync ... --rsync-path="sudo rsync" ...`.
This way, the destination machine `sudo` request will not prompt for a password.



* [How To Use Rsync to Sync Local and Remote Directories](https://www.digitalocean.com/community/tutorials/how-to-use-rsync-to-sync-local-and-remote-directories?utm_medium=email&utm_source=IaaN&utm_campaign=02102022&mkt_tok=MTEzLURUTi0yNjYAAAGCg8nuTcV6m2oY0eargA7nMEjXdhGLHQ_5AXNMLB5a-BH2HVxpkzqr-FMheSz3Yawm5_VVyh-sUaY7uyeEyRl4pW43Qn_STGOTfMFlQj-F)
* [How to Use rsync on Synology NAS](https://linuxhint.com/use-rsync-synology-nas/)
* [How to Use rsync Command to Copy Files on Ubuntu](https://linuxhint.com/rsync_copy_files_ubuntu/)
* [How to Use Rsync to Create a Backup on Ubuntu 20.04](https://serverspace.us/support/help/use-rsync-to-create-a-backup-on-ubuntu/)

#### Step X: Install Hyperbackup
[Synology Hyperbackup][33]

* [The Complete Hyper Backup Guide For Synology NAS (YOU NEED TO BACKUP YOUR NAS)](https://www.youtube.com/watch?v=7Retrqnr9eM)

#### Step X: Schedule Some Snapshot Replication
* [Never Lose Data Again! - Taking Snapshots with Synology DSM](https://www.youtube.com/watch?v=b4z1yH5pq80)
https://global.download.synology.com/download/Document/Software/WhitePaper/Firmware/DSM/All/enu/Synology_Data_Protection_White_Paper.pdf?_ga=2.168680097.1472444522.1635091279-406340359.1631583788



----



# Backup a Linux PC to a Synology NAS Using Rsync
* [How I configured my Synology NAS and Linux to use rsync for backups](https://obsolete29.com/posts/2022/04/30/how-i-configured-my-synology-nas-and-linux-to-use-rsync-for-backups/)
* [How do I back up data from a Linux device to my Synology NAS via rsync?](https://kb.synology.com/en-global/DSM/tutorial/How_to_back_up_Linux_computer_to_Synology_NAS)
* [Backup a Linux PC to a Synology NAS using Rsync!](https://www.wundertech.net/how-to-backup-a-linux-pc-to-a-synology-nas-using-rsync/)
* [How to Use rsync on Synology NAS](https://linuxhint.com/use-rsync-synology-nas/)
* [Backup and Restore Your Linux System with rsync](https://averagelinuxuser.com/backup-and-restore-your-linux-system-with-rsync/)



----



# Synology iPerf3 Speed Test
* [How to Run a Speed Test on a Synology NAS with iPerf3](https://www.wundertech.net/run-a-speed-test-on-a-synology-nas-with-iperf3/)


----



[01]:https://www.synology.com/en-us/products/DS220+
[02]:https://www.synology.com/en-us/products/DS220j
[03]:https://www.synology.com/en-global/dsm/Btrfs
[04]:https://account.synology.com/en-global/oauth2/login/home
[05]:https://clonezilla.org/downloads.php
[06]:https://askubuntu.com/questions/140197/i-can-ssh-into-a-remote-host-but-get-connection-reset-by-peer-with-sshfs-what
[07]:https://www.ventoy.net/en/index.html
[08]:https://www.ventoy.net/en/screenshot.html
[09]:https://www.ventoy.net/en/doc_start.html
[10]:https://syncthing.net/
[11]:https://www.youtube.com/watch?v=bNiiJe8NpEw
[12]:https://clonezilla.org/
[13]:https://www.acronis.com/en-us/products/true-image/
[14]:https://en.wikipedia.org/wiki/Ghost_(disk_utility)
[15]:https://clonezilla.org/clonezilla-live.php
[16]:https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/11_lite_server
[17]:https://clonezilla.org/clonezilla-SE/
[18]:https://www.youtube.com/watch?v=S0KZ5iXTkzg
[19]:https://www.securedatarecovery.com/blog/choosing-cmr-smr-technology-hard-drives
[20]:https://www.youtube.com/watch?v=oWujGFVATiI
[21]:https://linuxhint.com/nfs-mount-synology-linux/
[22]:https://kb.synology.com/en-us/DSM/help/DSM/AdminCenter/connection_ddns?version=7
[23]:https://www.efficientip.com/what-is-dhcp-and-why-is-it-important/
[24]:https://www.atera.com/blog/what-is-nfs-understanding-the-network-file-system/
[25]:https://en.wikipedia.org/wiki/Samba_(software)
[26]:https://en.wikipedia.org/wiki/Server_Message_Block
[27]:https://linuxconfig.org/nfs-vs-samba-vs-cifs
[28]:https://bobcares.com/blog/nfs-vs-smb/
[29]:https://www.wundertech.net/how-to-back-up-a-linux-pc-to-a-synology-nas/
[30]:https://www.synology.com/en-us/dsm/feature/active_backup_business
[31]:https://danielrosehill.medium.com/4-ways-to-backup-linux-workstations-onto-a-synology-nas-with-videos-487a54943702
[32]:https://www.youtube.com/watch?v=S0iKBichTPc
[33]:https://www.synology.com/en-us/dsm/feature/hyper_backup
[34]:https://linuxhint.com/use-synology-back-up-linux-computer/
[35]:https://www.baculasystems.com/glossary/bare-metal-backup-recovery/
[36]:https://kb.synology.com/en-ca/DSM/tutorial/How_to_use_Active_Backup_for_Business_to_backup_files_from_Windows_Server_VSS
[37]:https://clonezilla.org/downloads.php
[38]:https://www.makeuseof.com/tag/2-methods-to-clone-your-linux-hard-drive/
[39]:https://global.download.synology.com/download/Document/Hardware/HIG/DiskStation/20-year/DS220+/enu/Syno_HIG_DS220_Plus_enu.pdf
[40]:https://gizarena.com/synology-ds220-plus-setup/


