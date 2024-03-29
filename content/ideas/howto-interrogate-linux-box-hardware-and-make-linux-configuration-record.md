<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----



for CSI, you can get the NEID in the file `/home/csiadmin/coolerCache/neid`.

`inxi` is a command line system information tool that provides a wealth of
information about your Linux computer, whether it's a laptop, desktop, or server.
* [3 ways to use the Linux inxi command](https://opensource.com/article/22/9/linux-inxi-command)

* Check out Ansible an its `ansible localhost -m setup` command.

* [9 things to do in your first 10 minutes on a Linux server](https://opensource.com/article/20/12/linux-server)
* [How To Check If A Linux System Is Physical Or Virtual Machine](https://ostechnix.com/check-linux-system-physical-virtual-machine/)

# Tools
* [What's in the Box? Interrogate Your Linux Machine's Hardware](http://www.linuxjournal.com/content/whats-box-interrogate-your-linux-machines-hardware)
* [Linux commands to display your hardware information](https://opensource.com/article/19/9/linux-commands-hardware-information)
[Get Linux System and Hardware Details on the Command Line](https://vitux.com/get-linux-system-and-hardware-details-on-the-command-line/)
* [How to check Wireless network card and WiFi information from Linux Command Line](https://www.2daygeek.com/linux-find-out-wireless-network-wifi-speed-signal-strength-quality/)
* [Linux Find Wireless Wifi Driver Chipset Information](https://www.cyberciti.biz/faq/linux-find-wireless-driver-chipset/)
* [Unix Toolbox - a collection of Unix/Linux/BSD commands for advanced users](http://cb.vu/unixtoolbox.xhtml)
* [Query your Linux operating system like a database](https://opensource.com/article/21/6/osquery-linux)

* [How To Check If A Linux System Is Physical Or Virtual Machine](https://ostechnix.com/check-linux-system-physical-virtual-machine/)

* [Use lspci on Linux to see your hardware](https://opensource.com/article/21/9/lspci-linux-hardware)

* [Recognize more devices on Linux with this USB ID Repository](https://opensource.com/article/20/8/usb-id-repository)

# HDMI
* [Automatically detect when HDMI is plugged in](https://stackoverflow.com/questions/47960344/automatically-detect-when-hdmi-is-plugged-in/47964800)
* [Detecting HDMI cable whether it's plugged in or not](https://bbs.archlinux.org/viewtopic.php?id=133921)

# JSON
* [Converting CSV to JSON in bash](https://stackoverflow.com/questions/44780761/converting-csv-to-json-in-bash)
* [Transform plain data into json file](https://unix.stackexchange.com/questions/370032/transform-plain-data-into-json-file)
* [7 Command-Line Tools for Data Science](https://www.datascienceworkshops.com/blog/seven-command-line-tools-for-data-science/)






# Hardware Configuration Data

```bash
# facter is a command line utility to collect and display a system's information
facter

# if your using ansible to reach a remote system (appears to run facter)
ansible localhost -m setup
# or
ansible cluster-node-1 -i inventory -m setup

# check the DMI table
sudo dmidecode

# machine ID of the local system that is set during installation or boot
cat /etc/machine-id

# hardware architecture of the system
uname -a

# hardware information such as memory, CPU, disks, etc.
sudo lshw -json

# displays information about all the basic storage devices
lsblk --json

# lists information about all the USB controllers and the devices connected
lsusb

# detailed CPU information
lscpu

# wireless / wifi chipset
lspci | egrep -i 'wifi|wireless|intel|broadcom|realtek'

# block storage device uuid
blkid

# device uuid by mountpoint
lsblk -f | grep -v loop
```

# Firmware Configuration Data
```bash
# list of all drivers (modules) loaded in the Linux Kernel
lsmod
```

# Software Configuration Data
```bash
```

# More Linux Configuration Commands
* [GET BIOS, FIRMWARE, HARDWARE AND DRIVERS DETAILS IN LINUX/UNIX](https://www.linuxnix.com/how-to-get-bios-firmware-and-installed-drivers-details/)
* [How to check HP iLO Firmware version from Linux command line](https://www.2daygeek.com/how-to-check-hp-ilo-firmware-version-from-linux-command-line/)
* [How to get the Network Interface Card (NIC) firmware version on Linux system](https://www.dell.com/support/article/en-us/how11978/how-to-get-the-network-interface-card-nic-firmware-version-on-linux-system?lang=en)
* [New App Makes Linux Firmware Management MUCH Easier (Updated)](https://www.omgubuntu.co.uk/2019/08/new-gnome-firmware-updater-app-will-make-linux-firmware-management-easier)
* [Obtain hard-drive firmware information using Linux and smartctl](https://linuxconfig.org/obtain-hard-drive-firmware-information-using-linux-and-smartctl)
* [LVFS makes Linux firmware updates easier](https://opensource.com/article/17/11/firmware-updates-and-lvfs)

#Configuration Comparison
[Using jq or alternative command line tools to compare JSON files](https://stackoverflow.com/questions/31930041/using-jq-or-alternative-command-line-tools-to-compare-json-files)

```bash
jq --argfile a a.json --argfile b b.json -n '($a | (.. | arrays) |= sort) as $a | ($b | (.. | arrays) |= sort) as $b | $a == $b'

jq --argfile a a.json --argfile b b.json -n 'def post_recurse(f): def r: (f | select(. != null) | r), .; r; def post_recurse: post_recurse(.[]?); ($a | (post_recurse | arrays) |= sort) as $a | ($b | (post_recurse | arrays) |= sort) as $b | $a == $b'
```

