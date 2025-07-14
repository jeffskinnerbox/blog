<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
        title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------



* [What is the Windows Subsystem for Linux?](https://learn.microsoft.com/en-us/windows/wsl/about)
* [How to install Linux on Windows with WSL](https://learn.microsoft.com/en-us/windows/wsl/install)
* [How to Install the Windows Subsystem for Linux on Windows 11](https://www.howtogeek.com/744328/how-to-install-the-windows-subsystem-for-linux-on-windows-11/)
* [How to Access Your Linux (WSL) Files in Windows 10 and Windows 11](https://www.howtogeek.com/426749/how-to-access-your-linux-wsl-files-in-windows-10/)
* [An introduction to Linux through Windows Subsystem for Linux](https://theshepord.github.io/intro-to-WSL/)
* [Setting Up WSL with Graphics and Audio](https://research.wmz.ninja/articles/2017/11/setting-up-wsl-with-graphics-and-audio.html)


* [How to Install the Windows Subsystem for Linux on Windows 11](https://www.howtogeek.com/744328/how-to-install-the-windows-subsystem-for-linux-on-windows-11/)
* [Enable Linux Subsystem and Install Ubuntu in Windows 10](https://www.ssl.com/how-to/enable-linux-subsystem-install-ubuntu-windows-10/)






# Important

* [Windows Subsystem for Linux (WSL): what can't I do with the Ubuntu application for Microsoft Windows?](https://askubuntu.com/questions/1051525/windows-subsystem-for-linux-wsl-what-cant-i-do-with-the-ubuntu-application-f)


---------------


# Install Windows Subsystem for Linux (WSL)

Enabling WSL (Windows Subsystem for Linux) allows you to run an Ubuntu instance on top of Windows OS.
You will install the necessary development tools into the Ubuntu WSL environment and do your development there.

Sources:

* [How to install Linux on Windows with WSL](https://learn.microsoft.com/en-us/windows/wsl/install)
* [Manual installation steps for older versions of WSL](https://learn.microsoft.com/en-us/windows/wsl/install-manual)
* [Basic commands for WSL](https://learn.microsoft.com/en-us/windows/wsl/basic-commands)
* [Installing WSL (Windows Sybsystem for Linux) and Ubuntu on Windows-10](https://www.youtube.com/watch?v=bT-aCtjd-qs)
* [Install Windows Subsystem for Linux (WSL)](https://www.youtube.com/watch?v=gTf32sX9ci0)

#### Step 1: Check Windows Version

You must be running Windows 10 version 2004 and higher (Build 19041 and higher)
or Windows 11 to use the commands below.
If you are on earlier versions please see the [manual install page](https://learn.microsoft.com/en-us/windows/wsl/install-manual).

#### Step 2: Enable WSL Windows Feature

1. Type **features** into the start bar and open the Control panel to **Turn Windows features on or off**.
2. In the panel, find the checkbox **Windows Subsystem for Linux**.
Check the box, and click **OK**.
Wait for it to complete the requested changes and then restart your computer when prompted.

#### Step 3: Install Ubuntu 24.04

Open PowerShell or Windows Command Prompt and enter the commands below:

```bash
wsl --set-default-version 1
wsl --install -d Ubuntu-24.04
```

1. The ubuntu application is now launched and opens a new WSL terminal window. The terminal prints the message "Installing, this may take a few minutes…", be patient while it works.
2. After it completes, it may prompt you to create a username and password and if so, follow its instructions.

Bring the Ubuntu packages up to date by running the commands below in your WSL terminal window:

```bash
sudo dpkg-divert --rename --add /usr/bin/systemd-sysusers
sudo ln -sf /usr/bin/true /usr/bin/systemd-sysusers
sudo apt update && sudo apt upgrade
```

Use the commands below to confirm the correct versions of WSL and ubuntu.

```bash
lsb_release -a
powershell.exe "wsl --list --verbose"
```

#### Step 4: Accessing WSL files from Windows

It is important to recognize that WSL hosts its own file system.
The files you access within the WSL terminal are separate from your regular Windows file system.
You can access the WSL files in the Windows File Explorer by changing to a particular directory in the WSL terminal and run the command below:

```bash
explorer.exe .
```

This command opens a window in File Explorer that shows the files in the current WSL directory (whose shortname name is dot).
Windows applications can now access these files,
such as to edit a WSL text file using your favorite Windows text editor.


---------------



# Multipass - NOT COMPETED OR TESTED

[Multipass][12] is a tool for creating and managing Ubuntu virtual machines (VMs) on Linux, macOS, and Windows.
Multipass is designed to create and manage Ubuntu-based Linux virtual machines,
meaning it only readily supports launching Ubuntu images by default;
you cannot use it to run a Windows operating system directly within a Multipass VM.

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



[12]:https://canonical.com/multipass

