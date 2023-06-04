<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----



While experimenting with [Netdata][14] (an excellent server monitoring tool)
Netdata raised an alarm, stating:
_Number of devices in the down state for the md0 (raid1) array. The array is degraded. Some array devices are missing. To fix, bring them back online or replace the faulty ones. To find faulty devices use [mdadm --detail RAIDDEVICE]._
This was the first sign I got that my [RAID 1][15] disks has failed.

Described below are the steps I used to replace a mirror disk in a software RAID 1 array.
I'll be using `/dev/sda` as the known good disk
and `/dev/sdb` as the failed/failing disk.
Keep in mind the following:
I **do not** want to destroy the array and any data written to it and
I **do not** want to remove the RAID array (e.g. `sudo mdadm --remove /dev/md0`).

# Background
I quickly fond some good sources on how to replace the bad drive.
What proved more challenging was:

1. from a secondary source, confirmation information about the bad drive
2. how to physical recognize the bad drive
3. what type of drive was need as a replacement

In the subsections, I'll review some important things I learned.

## SMART (Self-Monitoring, Analysis, and Reporting Technology)
[SMART (Self-Monitoring, Analysis, and Reporting Technology)][01] data on modern hard disk and solid-state drives.
It allows you to inspect the drive's SMART data to determine its health, as well as run various tests on it.
`smartctl` is the primary tool for querying and controlling SMART.
It allows you to inspect the drive's SMART data to determine its health,
as well as run various tests on it.
But [SMART is not fool proof][04].
You can access the SMART information on the drive,
but since there is no standardization for SMART,
there is always a question about its reliability.

To access the SMART data,
you can install the [`smartmontools`][02] package.
For an alternative to the `smartctl` commandline tool, take a look at [GSmartControl][03].
It's a nice graphical frontend to `smartctl`.
It shows all SMART values, and highlights those that indicate old age or impending failure,
plus you can run tests on demand.
You can install both these tools via:

```bash
# install smartmontools and gsmartcontrol
sudo apt-get -y install smartmontools gsmartcontrol

# if you see Reallocated or Pending sectors, it is recommend to replace the drive ASAP
$ sudo smartctl -a /dev/sda | grep -E "Reallocated|Pending"
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0

# 5 smart attributes indicate imminent drive failure
# https://superuser.com/questions/1171760/how-to-determine-how-dead-a-hdd-is-from-smartctl-report
sudo smartctl -a /dev/sda | grep -E "Reallocated_Sector_Ct|Reported_Uncorrect|Command_Timeout|Current_Pending_Sector|Offline_Uncorrect"
```

The SMART tool set (`smartmontools`) has useful utilities beyond `smartctl`.
This include daemon to run SMART reports periodically
and a hook to take action like send an email, pop-up a UI notification, or something more intrusive.
You find more information [here][02].

Key sources include:

* [Ubuntu Documentation: Smartmontools][02]
* [GSmartControl][03]
* [A Tool to Determine the Health and Test Hard Disks/SSDs on Linux (Windows/Mac)](https://www.youtube.com/watch?v=vxq8j7GUz40)
* [What happened to S.M.A.R.T. Drives?][04]
* [How to determine how dead a HDD is from SMARTCTL report](https://superuser.com/questions/1171760/how-to-determine-how-dead-a-hdd-is-from-smartctl-report)
* [Monitoring hard disk health with smartd under Linux or UNIX operating systems](https://www.cyberciti.biz/tips/monitoring-hard-disk-health-with-smartd-under-linux-or-unix-operating-systems.html)
* [Test If Linux Server SCSI / SATA / SSD Hard Disk Going Bad](https://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html)
* [Hard Drive SMART Stats](https://www.backblaze.com/blog/hard-drive-smart-stats/)
* [Diagnose and Replace a Defective Hard Drive (Linux Dedicated Server with Software RAID)](https://www.ionos.com/help/server-cloud-infrastructure/server-administration-dedicated-servers/diagnose-and-replace-a-defective-hard-drive-linux-dedicated-server-with-software-raid/)

## CMR vs SMR Hard Drives
When it comes to hard drives, its more than access speed and cost.
Another thing to consider is Shingled Magnetic Recording (SMR) or Conventional Magnetic Recording (CMR).
Because the different recording methods behave differently,
you should pick the recording technology based on you usage pattern.
For RAID arrays, there is a bigger consideration.
In some cases, a [RAID controller may refuse to repair the array of an SMR drive][09] if used instead of a CMR.
CMR hard disks are a good choice when data is to be stored at high transfer rates
or particularly large amounts of data.
This includes a large number of activities from music streaming and image processing to use for NAS servers.

Sources:
* [CMR vs SMR Hard Drives in Network Attached Storage (NAS)](https://www.buffalotech.com/blog/cmr-vs-smr-hard-drives-in-network-attached-storage-nas)
* [SMR? CMR? Which Hard Drive is best for which purpose?](https://www.reichelt.com/magazin/en/smr-cmr-which-hard-drive-is-best-for-which-purpose/)
* [WD Red SMR vs CMR Tested Avoid Red SMR](https://www.servethehome.com/wd-red-smr-vs-cmr-tested-avoid-red-smr/)


-----


# Repairing Damage RAID 1
There are many websites that write about RAID 1 repair but very few
give the level of detail deserving of this critical task.
The sites that I found most helpful, yet not completely to my satisfaction,
are listed below.

* [Introduction to RAID Concepts](https://www.tecmint.com/category/raid/)
* [How To Create RAID Arrays with mdadm on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04)
* [Replacing a Failed Mirror Disk in a Software RAID Array (mdadm)](https://www.thegeekdiary.com/replacing-a-failed-mirror-disk-in-a-software-raid-array-mdadm/)
* [mdadm: How to Remove a Drive From a RAID Array](https://delightlylinux.wordpress.com/2020/12/22/how-to-remove-a-drive-from-a-raid-array/)
* [Replacing A Failed Hard Drive In A Software RAID1 Array](https://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array)
* [How to wipe a signature from a disk device on Linux with wipefs command](https://www.cyberciti.biz/faq/howto-use-wipefs-to-wipe-a-signature-from-disk-on-linux/)

### Step 1: Evaluate the Good Disk Drives
Assess the overall health of of the non-RAID disk drive.
In my case, there are two:
One  is `/dev/sda` which happens to be a [SATA][12] [SSD][11]
and `/dev/sdb` which is a USB attached traditional hard drive (aka [HDD][13]):

```bash
# list all the drives
df -h

# quick, overall-health self-assessment test of /dev/sda
$ sudo smartctl -d ata -H /dev/sda
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-88-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

# quick, overall-health self-assessment test of /dev/sdb
$ sudo smartctl -d scsi -H /dev/sdb

# for more information
sudo smartctl --attributes --log=selftest /dev/sda
```

```bash
# long health test
sudo smartctl -d ata -t long /dev/sda

# after 15 minutes, check the report
sudo smartctl -l selftest /dev/sda
```

### Step 2: Validate There is a Failed Disk
[A hard drive can fail, or perform poorly, for many reasons][05].
In my case, one of my [RAID 1][06] drives failed completely, or was no longer communicating,
at least that was what Netdata appeared to be telling me.
My immediate problem was to validate what Netdata was telling me,
and I so I turned to SMART to get an answer (after doing simple things like `df -h`).
After a much experimenting with `smartctl` and `gsmartcontrol`,
it became clear that SMART can help you with disk drives that are communicating,
but it has nothing to offer you once the drive is dead.

>**NOTE:** I discovered later that Netdata gave further confirmation about the failed drive.
>I just had to check out the **MD arrays** > **health** entry on the right-hand side menu.

OK, so one of my RAID 1 drive may have completely fail
(or is "off-line" for some reason), but how do I validate this?
I know its must be one of my Seagate 1TB HDD (model ST1000DM003) but which one is it?
I conclude that I must look to the RAID management utility, [`mdadm`][10],
to give me a authoritative conclusion for the health of the RAID disk drive.
I'll use `smartctl` to get the serial number of the working drive
so I can isolate which drive is the bad one.

The commands below show that `mdadm` does sense a removed / failed drive in the RAID array.
I then use `smartctl` to get the serial number of the good RAID disk.

```bash
# information about the structure, component devices, and current state of the array
$ sudo mdadm --detail /dev/md0
/dev/md0:
           Version : 1.2
     Creation Time : Mon May 27 14:46:30 2013
        Raid Level : raid1
        Array Size : 976630336 (931.39 GiB 1000.07 GB)
     Used Dev Size : 976630336 (931.39 GiB 1000.07 GB)
      Raid Devices : 2
     Total Devices : 1
       Persistence : Superblock is persistent

       Update Time : Mon Oct 25 20:03:12 2021
             State : clean, degraded
    Active Devices : 1
   Working Devices : 1
    Failed Devices : 0
     Spare Devices : 0

Consistency Policy : resync

              Name : desktop:0  (local to host desktop)
              UUID : a2dd43af:38ddc058:ffd5ca35:0e09d37c
            Events : 160263995

    Number   Major   Minor   RaidDevice State
       -       0        0        0      removed
       1       8       49        1      active sync   /dev/sdd1
```

The report above states "State : clean, degraded" and one of the RAID disks is "removed".
The article "[RAID1 - State : clean, degraded][07]"
maybe there is nothing physically wrong with the drive,
and it is worthwhile to remove the drive from the array then re-add it.
This will cause the drive to re-sync with the array.
If the drive will not sync with the array, it is a good indication of hardware failure.

I can't find any evidence the drive is in fact failed,
just that it has been removed.
Could it be it just needs to be re-added to the RAID array?
You should try this before replacing
(via  something like `sudo mdadm --manage /dev/md0 --add /dev/sdd2`),
but in my case, there were no "candidate" drives.
All where accounted for.

### Step 3: Identify the Failed Disk and Get Its Serial Number
The above report shows that the RAID has an active drive with device file `/dev/sdd1`.
Let's use `smartctl` to find the identify of this drive:

```bash
# validate a drive has SMART capabilities
sudo smartctl -s on /dev/sdd1

# get the serial number of the good disk
$ sudo smartctl -i /dev/sdd1 | grep -E "Serial|Model"
Model Family:     Seagate Barracuda 7200.14 (AF)
Device Model:     ST1000DM003-1CH162
Serial Number:    Z1D3N7RY
```

The serial number is what I need.
I now can open my Linux computer, check the Seagate Barracuda drives,
and the fail disk is the one who serial number **is not** `Z1D3N7RY`.

Sources:

* Basic Linux Utilities
    * [how to list all hard disks in linux from command line](6 Different Ways to List Hard Drives in Linux)
    * [6 Different Ways to List Hard Drives in Linux](https://linuxhandbook.com/linux-list-disks/)
    * [How do I find out what hard disks are in the system?](https://unix.stackexchange.com/questions/4561/how-do-i-find-out-what-hard-disks-are-in-the-system)
* SMART and mdadm Utilities
    * [Hard Drive SMART Stats](https://www.backblaze.com/blog/hard-drive-smart-stats/)
    * [Diagnose and Replace a Defective Hard Drive (Linux Dedicated Server with Software RAID)](https://www.ionos.com/help/server-cloud-infrastructure/server-administration-dedicated-servers/diagnose-and-replace-a-defective-hard-drive-linux-dedicated-server-with-software-raid/)

### Step 4: Do a Backup
Before proceeding with a fix,
it is always a good idea to backup the original disk.
In my case, this will be done via:

```bash
# write any cashed data to disk (all mounted file systems)
sync

# backup the entire disk
su - backup_user
full-backup.sh

sudo /home/backup_user/bin/full-backup.sh

# to monitor the backup status
tail /home/backup_user/backup.log
```

Check for the completion of the backup via `ps aux | grep backup.sh`.
When the backup is complete, move to the next step.

### Step 5: Remove the Disk From RAID
With the disk completely backed up to another drive,
do another `sync` and mark your failed/failing drive as failed
(assuming its operational at all):

```bash
# write any cashed data to disk (all mounted file systems)
sync

# mark the failed disk (assuming its operational at all)
sudo mdadm --manage /dev/md0 --fail /dev/sdd2
```

To verify that the disk is marked as failed, `cat /proc/mdstat`.
Failed disk will be marked as “(F)”, assuming its operational at all.

If the disk has already failed, as in my case,
you can check it via the command below.

```bash
# information about the structure, component devices, and current state of the array
$ sudo mdadm --detail /dev/md0
/dev/md0:
           Version : 1.2
     Creation Time : Mon May 27 14:46:30 2013
        Raid Level : raid1
        Array Size : 976630336 (931.39 GiB 1000.07 GB)
     Used Dev Size : 976630336 (931.39 GiB 1000.07 GB)
      Raid Devices : 2
     Total Devices : 1
       Persistence : Superblock is persistent

       Update Time : Sun Oct 17 22:27:12 2021
             State : clean, degraded
    Active Devices : 1
   Working Devices : 1
    Failed Devices : 0
     Spare Devices : 0

Consistency Policy : resync

              Name : desktop:0  (local to host desktop)
              UUID : a2dd43af:38ddc058:ffd5ca35:0e09d37c
            Events : 159872523

    Number   Major   Minor   RaidDevice State
       -       0        0        0      removed
       1       8       49        1      active sync   /dev/sdd1
```

### Step 6: Replace the Disk
Now power down the computer but don't replace the disk drive yet.
First try re-seating the SCCI connection
(the disk drive that does **not** have the serial number `Z1D3N7RY`),
power back up the computer,
and check its status via `sudo mdadm --detail /dev/md0`.

If the above doesn't work, power down the computer so you can replace the disk
(the disk drive that does **not** have the serial number `Z1D3N7RY`).
Physically replace the drive and restart the computer.

### Step 7: Copy Partition Table to New Disk
First thing you need to do is find the new loaded disk,
which most likely will not mount (so `df -h` doesn't help you).
Your looking for something new, so use the disk partitioning tool `fdisk`:

```bash
# find the active raid drive
$ sudo mdadm --detail /dev/md0 | grep active
       1       8       33        1      active sync   /dev/sdc1

# list the partition tables for all the drives
$ sudo fdisk -l | grep "/dev/sd"
Disk /dev/sda: 119.25 GiB, 128035676160 bytes, 250069680 sectors
/dev/sda1  *         2048    976895    974848  476M 83 Linux
/dev/sda2       233635838 250068991  16433154  7.9G  5 Extended
/dev/sda3          976896 233633791 232656896  111G 83 Linux
/dev/sda5       233635840 250068991  16433152  7.9G 82 Linux swap / Solaris
Disk /dev/sdc: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
/dev/sdc1        2048 1953525167 1953523120 931.5G 83 Linux
Disk /dev/sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk /dev/sdd: 3.65 TiB, 4000787025920 bytes, 976754645 sectors
```

This tells me the new drive has device file `/dev/sdb`
and the active good drive is `/dev/sdc`.
You'll be using this information in the subsequent tasks below.

Copy the partition table to the new disk
( **Caution:** The `sfdisk` command will replace the entire partition table
on the target disk with that of the source disk
– use an alternative command if you need to preserve other partition information):

```bash
# list partition table of the good drive /dev/sdc
$ sudo fdisk -l /dev/sdc
Disk /dev/sdc: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-1CH1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xe9fd17be

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdc1        2048 1953525167 1953523120 931.5G 83 Linux

# get a root terminal session
sudo su root

# copy partition table to new disk
$ sfdisk -d /dev/sdc | sfdisk /dev/sdb
Checking that no-one is using this disk right now ... OK

Disk /dev/sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-1SB1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

>>> Script header accepted.
>>> Script header accepted.
>>> Script header accepted.
>>> Script header accepted.
>>> Created a new DOS disklabel with disk identifier 0xe9fd17be.
/dev/sdb1: Created a new partition 1 of type 'Linux' and of size 931.5 GiB.
/dev/sdb2: Done.

New situation:
Disklabel type: dos
Disk identifier: 0xe9fd17be

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1        2048 1953525167 1953523120 931.5G 83 Linux

The partition table has been altered.
Calling ioctl() to re-read partition table.
Syncing disks.

# drop out of root terminal
exit

# check if both hard drives have the same partitioning
sudo fdisk -l /dev/sdc /dev/sdb
```

### Step 8: Create New RAID and Verify
Next we add `/dev/sdb` to the `/dev/md0` RAID array.

```bash
# create the mirror of the disk
sudo mdadm --manage /dev/md0 --add /dev/sdb

# validate the setup
sudo mdadm --detail /dev/md0

# check if the raid is rebuilding the new disk
$ sudo mdadm --detail /dev/md0 | grep /dev/sdb
       2       8       16        0      spare rebuilding   /dev/sdb

# show the current progress of the recovery of the mirror disk
$ cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdb[2] sdc1[1]
      976630336 blocks super 1.2 [2/1] [_U]
      [>....................]  recovery =  1.7% (17492096/976630336) finish=100.5min speed=158905K/sec
```

When the synchronization is finished, the output will look like this:

```bash
# fully recovered mirroring looks like this
$ cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdb[2](S) sdc1[1]
      976630336 blocks super 1.2 [2/1] [_U]

unused devices: <none>

# initially, the recovering disks looks like this
$ sudo mdadm --detail /dev/md0
[sudo] password for jeff:
/dev/md0:
           Version : 1.2
     Creation Time : Mon May 27 14:46:30 2013
        Raid Level : raid1
        Array Size : 976630336 (931.39 GiB 1000.07 GB)
     Used Dev Size : 976630336 (931.39 GiB 1000.07 GB)
      Raid Devices : 2
     Total Devices : 2
       Persistence : Superblock is persistent

       Update Time : Tue Oct 26 00:15:47 2021
             State : clean, degraded
    Active Devices : 1
   Working Devices : 2
    Failed Devices : 0
     Spare Devices : 1

Consistency Policy : resync

              Name : desktop:0  (local to host desktop)
              UUID : a2dd43af:38ddc058:ffd5ca35:0e09d37c
            Events : 160271451

    Number   Major   Minor   RaidDevice State
       -       0        0        0      removed
       1       8       33        1      active sync   /dev/sdc1

       2       8       16        -      spare   /dev/sdb

# fully recovered mirroring looks like this
$ sudo mdadm --detail /dev/md0
[sudo] password for jeff:
/dev/md0:
           Version : 1.2
     Creation Time : Mon May 27 14:46:30 2013
        Raid Level : raid1
        Array Size : 976630336 (931.39 GiB 1000.07 GB)
     Used Dev Size : 976630336 (931.39 GiB 1000.07 GB)
      Raid Devices : 2
     Total Devices : 2
       Persistence : Superblock is persistent

       Update Time : Sat Nov 13 17:45:52 2021
             State : active
    Active Devices : 2
   Working Devices : 2
    Failed Devices : 0
     Spare Devices : 0

Consistency Policy : resync

              Name : desktop:0  (local to host desktop)
              UUID : a2dd43af:38ddc058:ffd5ca35:0e09d37c
            Events : 160891467

    Number   Major   Minor   RaidDevice State
       2       8       16        0      active sync   /dev/sdb
       1       8       33        1      active sync   /dev/sdc1
```

### Step 9: Assess General Health of the RAID Drives
I choose to replace failed drive with the exact same brand & model
as the good drive: 1TB Seagate Barracuda

>**NOTE:** I purchased the 1TB Seagate drive in May of 2013 for $71.
>I can replace it with the same model for $33 in October of 2021.

```bash
# identify the device drivers for the raid disks
$ sudo mdadm --detail /dev/md0 | grep "/dev/"
/dev/md0:
       2       8       16        0      active sync   /dev/sdb
       1       8       33        1      active sync   /dev/sdc1

# assess the health of the two drives
sudo smartctl -d ata -t long /dev/sdc
sudo smartctl -d ata -t long /dev/sdb
```

Given the original drive is now 8 years old,
I should expect it to will fail sometime in the near future.



[01]:https://www.youtube.com/watch?v=YNGUP1t8MYA
[02]:https://help.ubuntu.com/community/Smartmontools
[03]:https://gsmartcontrol.sourceforge.io/home/
[04]:https://www.youtube.com/watch?v=BDjxIHzSLPo
[05]:https://www.youtube.com/watch?v=hr57KHDgaFs
[06]:https://en.wikipedia.org/wiki/Standard_RAID_levels
[07]:https://www.howtoforge.com/community/threads/raid1-state-clean-degraded.66744/
[08]:https://www.ducea.com/2009/03/08/mdadm-cheat-sheet/
[09]:https://www.securedatarecovery.com/blog/choosing-cmr-smr-technology-hard-drives
[10]:https://raid.wiki.kernel.org/index.php/A_guide_to_mdadm
[11]:https://en.wikipedia.org/wiki/Solid-state_drive
[12]:https://en.wikipedia.org/wiki/Serial_ATA
[13]:https://en.wikipedia.org/wiki/Hard_disk_drive
[14]:https://www.netdata.cloud/get-netdata/
[15]:https://www.youtube.com/watch?v=U-OCdTeZLac
[16]:
[17]:
[18]:
[19]:
[20]:
