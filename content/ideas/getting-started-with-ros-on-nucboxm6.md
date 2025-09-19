<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
    title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------


# Getting Started with Robot Operating System 2 (ROS 2)

The [Robot Operating System (ROS)][17] is not an operating system in the traditional sense,
but a "glue" or middleware that holds your robotic system together.
It enables different robot components, running as separate processes within multiple physical locations.
With ROS, these process can exchange information using using computer services like
communicating messages (e.g. current state), perform services (e.g. compute something for me),
or actions (e.g. (a goal is requested, perform the task, and give feedback as you execute).
ROS allows various parts of the robot system (sensors, actuators, decision-making units)
to work cooperatively to fulfill its mission.

## Robotics

What is a robot? What is robotics?

## Installing ROS2

## The Tech Stack

Robot
Robotics
Process
Middleware
Operating System (OS)
Open Source
Software Framework
Computer Vision (CV)
Neural Networks
Machine Learning (ML)
Artificial Intelligence (AI)
Generative AI
Large Language Models (LLMs)
Physics Engine - realistic interactions with physical properties such as momentum, inertia, and gravity
Modelling - refers to the process of creating a digital representation of a physical object

## Robot Modelling and Visualisation

A critical aspect of designing and simulating robots is the creation of
accurate and visually / dynamically representative models of the robot.
These models are blueprints for capturing the geometric properties and mechanical mobility of the robot.
They enabling you to analyze, simulate, and control robotic systems effectively.
A design document used by ROS2 for achieving this is the [Unified Robot Description Format (URDF)][15].
URDF is an XML-based file format widely used in the robotics community.
It was originally developed by [Willow Garage][16] and adopted as a standard for
robot modeling in the [Robot Operating System (ROS)][17].

Why is the visual & dynamic representation of the robot with URDF important?

* **Reduce Cycle-Time:** Creating a robot is an iterative process of ideation, design, build, test, re-plan, and repeat.
If you must build physical robot for each cycle, this becomes very expensive in both time & money.
So a virtual process (aka digital representation of what physical is happening) is highly desirable.
* **Visualization:** A visually realistic robot model aids in understanding how a robot will look and move in the real world,
making it easier to communicate design concepts and ideas.
* **Dynamic Simulation:** Before building a physical robot, you want to validate its behavior in a virtual environment.
Accurate visual representation allows for realistic simulations of task that need to be performed,
which can help in testing and fine-tuning control algorithms and robot behavior.
* **Sensory Simulation:** In robotics, sensor placement, and orientation are critical.
An accurate visual model assists in simulating and predicting how sensors (such as cameras or LIDAR)
interact with the environment and assist the robot in it mission.

### Components of a URDF Visual Model

The components that make up URDF Visual Model are intended to inform the robots internal controls
how the robot can configure itself in physical space.
When operated, or simulated, you want to know how the robot is positioned,
has a robot component (e.g. arm) reached it destination,
or will it collide with something.
In addition, for the robot to move from one physical position to a target position,
it must transform itself to reach its target
(essentially a mathematical operation performed to convert one coordinate system to another).

What are the components of the URDF model that captures the robots configuration?

* **Links:** In URDF, a robot is composed of individual links.
Links represent physical components of the robot, such as arms, wheels, or the base/body.
Each link can have visual and collision representations.
* **Visual Elements:** Within each link, you define visual elements to represent how it looks.
These visual elements include geometric shapes (like cylinders, spheres, and meshes)
and their associated properties, such as size, color, and texture.
* **Collision Elements:** While visual elements define how a robot looks,
collision elements define its shape for collision detection.
They may differ from the visual representation,
often simplifying the geometry for efficient computation.
* **Transforms:** URDF allows you to specify the relative pose of links and their visual/collision elements,
enabling you to accurately model complex robot structures.
* **Material Properties:** You can define material properties, such as color and transparency, for visual elements,
contributing to the realism of the model.

### Tools for Working with URDF

Creating and manipulating URDF files can be accomplished with various tools,
such as ROS packages like `urdfdom` for parsing URDF XML statements and `Rviz` for visualization,
or modeling software like Blender or CAD tools.

## Sources

* [Getting Started with Robot Operating System 2 (ROS 2)](https://medium.com/@thebinayak/getting-started-with-robot-operating-system-2-ros-2-ef56d2ac29f0)
* [An Introduction to Understanding Visual Robot Models with URDF](https://www.linkedin.com/pulse/introduction-understanding-visual-robot-models-urdf-kangal/)
* [Robot Modelling and Visualisation in ROS 2: A Practical Guide](https://medium.com/@thebinayak/robot-modelling-and-visualisation-in-ros-2-a-practical-guide-fa666160011d)




---------------


# Robot Operating System (ROS)

[Robot Operating System (ROS)][03] is a framework consisting of a huge number of libraries and tools specifically for developing robots.
It’s open source, supported by a large community,
and designed to support real-time performance and multi-robot systems.
ROS is primarily tested on Ubuntu, Mac OS X, and Windows but they also have a Docker version available.

Here is a [brief description][10] of the inter-workings of the ROS ecosystem,
but here is a summary of the major components:

* [Robot Operating System 2 (ROS 2)][03] framework as described above.
* [Gazebo][04] is a powerful open-source robotics simulator that allows developers to test
and validate robot designs in complex environments, offering realistic physics and sensor models.
* [RViz][05] is a 3D visualization tool for ROS that enables developers to
visualize sensor data, robot models, and environment maps, aiding in debugging and monitoring robot behavior.

The following tasks will be performed:

* Install Ubuntu Desktop OS
* Install Your User Environment
* Install Docker
* Install Robot Operating System (ROS)
* Enable ROS Screen Sharing
* Running ROS in Docker Container


---------------


# Install Ubuntu Desktop OS

[GMKTec M6][02]
Ryzen 6600H ARM processor
Dual NIC LAN 2.5G
AMD R5 6600H (6C/12T up to 4.50 GHz)
32G DDR5 RAM
1TB PCle SSD
WiFi 6E, USB 4.0, BT 5.2, HDMI

```bash
# show system host name and related information
$ hostnamectl status
 Static hostname: ros
       Icon name: computer-desktop
         Chassis: desktop 🖥️
      Machine ID: 83e0e557106c4f249ac84bd9c34f047b
         Boot ID: 2bd1130d9d704bd8bf0224ab787c8b72
Operating System: Ubuntu 24.04.2 LTS
          Kernel: Linux 6.11.0-24-generic
    Architecture: x86-64
 Hardware Vendor: GMKtec
  Hardware Model: NucBox M6
Firmware Version: 103
   Firmware Date: Fri 2024-05-24
    Firmware Age: 11month 6d
```

Sources:

* [How to Install Ubuntu 24.04 Desktop: Complete Beginner's Guide](https://www.youtube.com/watch?v=zE7OYNkuQ1w)
* [Install Ubuntu Desktop on the Intel NUC](https://ubuntu.com/download/intel-nuc-desktop)
* [Download Ubuntu Desktop](https://ubuntu.com/download/desktop)

#### Step 1: Download Ubuntu 24.04 - DONE

At this time, the latest long-term support version of Ubuntu,
for desktop PCs and laptops, is Ubuntu 24.04.2 LTS.
I download the [AMD 64-bit architecture version][01] to my hard drive.
The location of the download was `/home/jeff/Downloads/ubuntu-24.04.2-desktop-amd64.iso`


#### Step 2: Create Bootable USB Stick - DONE

First, identify what USB device your USB Stick is plugged into and then move the
Ubuntu ISO file onto the USB Stick.

```bash
# identify usb devices, identify current drives
$ lsblk | grep sd
sda           8:0    0 931.5G  0 disk
sdb           8:16   0 119.2G  0 disk
├─sdb1        8:17   0   476M  0 part
├─sdb2        8:18   0     1K  0 part
├─sdb3        8:19   0   513M  0 part
├─sdb5        8:21   0   7.8G  0 part
└─sdb6        8:22   0 110.4G  0 part  /old_computer
sdc           8:32   0 931.5G  0 disk
sdd           8:48   1     0B  0 disk

# install usb stick and rerun the above command
$ lsblk | grep sd
sda           8:0    0 931.5G  0 disk
sdb           8:16   0 119.2G  0 disk
├─sdb1        8:17   0   476M  0 part
├─sdb2        8:18   0     1K  0 part
├─sdb3        8:19   0   513M  0 part
├─sdb5        8:21   0   7.8G  0 part
└─sdb6        8:22   0 110.4G  0 part  /old_computer
sdc           8:32   0 931.5G  0 disk
sdd           8:48   1     0B  0 disk
sde           8:64   1  28.9G  0 disk
```

You have a new device, `/dev/sde`.  This is your USB Stick.
Now lets copy the ISO file just downloaded to this USB Stick.

```bash
# unmount the usb stick
sudo umount /dev/sde

# write the iso file to the usb stick
sudo dd if=/home/jeff/Downloads/ubuntu-24.04.2-desktop-amd64.iso of=/dev/sde bs=4M status=progress oflag=sync

# once dd finishes, flush any remaining operations
sync
```

You can now unplug your USB Stick.


#### Step 3: Booting the GMKTec M6 from the USB Stick - DONE

Start with this step with the GMKTec M6 in the powered-off state.
Wire up a monitor, keyboard, and ideally a mouse to the GMKTec M6.
Do the following steps:

1. Insert the USB Stick into the GMKTec M6.
2. Start the GMKTec M6 and push `Esc` key repeatedly until you enter the boot menu.
3. Select the USB Stick as your boot option.
4. The system will automatically execute the first stage of installation and prompt for an acknowledgement to complete the system install.

I gave GMKTec NucBox M6 the hostname of `NucBoxM6` and my login is `jeff` using my standard password.


#### Step 4: Install OpenSSH - DONE

Before I removed the monitor / keyboard / mouse, I did the following:

1. I checked to make sure `ssh` was working by via `ssh jeff@NucBoxM6.local` but this failed to find `NucBoxM6`.
2. I executed on my network the command `sudo netdiscover -c 3 -s 10 -L -N -r 192.168.1.0/24` and I found a new device with IP address of `192.168.1.154`.
3. The command `ssh jeff@92.168.1.154` did not work so I need to configure SSH via the Ubuntu environment just installed.

To fix this ssh problem, I did the following:

```bash
# update the systems repositories
sudo apt update
sudo apt upgrade

# install openssh server
sudo apt install ssh

# enable ssh services to start on boot
sudo systemctl enable ssh

# verify ssh service status
sudo systemctl status ssh

# configure firewall
sudo ufw allow ssh
sudo ufw enable
```

I rebooted `NucBoxM6` and redoing the command `ssh jeff@NucBoxM6.local` to validate that it now works.
I can now remove the  monitor / keyboard / mouse from the GMKTec M6
and put it on my network via an Ethernet cable.
Going forward, I'll use a terminal to log into my ROS environment
and all command-line and GUI / X-Windows program should work over this connection.


#### Step 5: Check if X Windows is Running - DONE

I want to run a X Window System (X11) application on my server (the GMKTec with Ubuntu 224.04)
but display its graphical output on a remote client (my `desktop` with Ubuntu) which is also running X Window.
To do this, you need to use [SSH with X11 forwarding][09].
You must have X11 forwarding enabled on both the client side and the server side.
Also, you have to enable X11 forwarding when connecting via SSH,
and specify the clients `DISPLAY` environment variable.
This should all default properly and just work, but lets check by doing the following:

```bash
# from the client, shh into the server using x forwarding
ssh -X jeff@NucBoxM6.local

# check if you can remotely execute a x windows application on the server and display on your client
xclock &
xeyes &

# check if your running display server xorg or wayland - good thing to know if you need to debug
ps aux | grep xorg
ps aux | grep Xwayland
```

There are alternative to X11 Forwarding.
You can also use a remote desktop protocol like RDP (using [`xrdp`][07]) or [VNC][08]
to display an entire desktop on a remote client.
These protocols provide a more complete remote desktop experience compared to X11 forwarding,
which focuses on forwarding individual applications.

Sources:

* [How to Use X11 Forwarding on Windows or Linux](https://www.youtube.com/watch?v=FlHVuA_98SA)
* [How to forward X over SSH to run graphics applications remotely?](https://unix.stackexchange.com/questions/12755/how-to-forward-x-over-ssh-to-run-graphics-applications-remotely)


#### 6: Using Microsoft Windows as X11 Client

If you want to use Microsoft Windows as your client,
see the following: [How to Use X11 Forwarding on Windows or Linux](https://www.youtube.com/watch?v=FlHVuA_98SA)


---------------


# Install Your User Environment

Here I will establish my login environment that I'm accustom to using.
I'm going to want to use all my familiar tools,
tools like Gnome Terminal, Curl, Chrome browser, NeoVim, Dotfiles, etc.
Lets get these installed.


#### Step 1: Install Packages for Frequently Used Linux Tools - DONE

```bash
# install packages for general use
sudo apt -y install trash-cli gnome gnome-session gnome-terminal git jq vim tmux wmctrl curl stow xclip

# install basic networking tools
sudo apt -y install net-tools nmap traceroute arp-scan netdiscover

# packages which let apt get packages over HTTPS
sudo apt -y install apt-transport-https ca-certificates curl software-properties-common

# install tools required by ansible
sudo apt -y install sshpass lookup acl

# install codecs for proprietary files with restricted copyright
sudo apt -y install ubuntu-restricted-extras

# install some tools used for my custom neovim configuration
sudo snap install alacritty --classic
sudo snap install nvim --classic
sudo apt install wl-clipboard     # if your using X Window's Wayland protocol (other wise install 'xset')
sudo apt install ripgrep          # ripgrep (executable is called `rg`) is need by for telescope

# update the packages on your system
sudo apt update && sudo apt upgrade
```


#### Step 2: Install Your `.dotfiles` - DONE

Within my GitHub, I maintain my `.dotfiles`` and the maintenance tool that I use is`stow`.
Let's pull down the latest`.dotfiles` repository and an install anything required:

```bash
# make sure you have install your version of the .dotfiles
cd $HOME
git clone https://github.com/jeffskinnerbox/.dotfiles.git

# put into you '.bashrc' file the environment variable for the path to `.config` directory
export XDG_CONFIG_HOME=$HOME/.config

# stow all your dotfile package - aka create your symlinks for your configuration files
stow --dir=$HOME/.dotfiles --target=$HOME --stow pkg-X
stow --dir=$HOME/.dotfiles --target=$HOME --stow pkg-vim
stow --dir=$HOME/.dotfiles --target=$HOME --stow pkg-tmux
stow --dir=$HOME/.dotfiles --target=$HOME --stow pkg-bash
stow --dir=$HOME/.dotfiles --target=$HOME --stow pkg-screen
stow --dir=$HOME/.dotfiles --target=$XDG_CONFIG_HOME --stow pkg-nvim
stow --dir=$HOME/.dotfiles --target=$XDG_CONFIG_HOME --stow pkg-yamllint
stow --dir=$HOME/.dotfiles --target=$XDG_CONFIG_HOME --stow pkg-alacritty
stow --dir=$HOME/.dotfiles --target=$XDG_CONFIG_HOME --stow pkg-ansible-lint
```


#### Step 3: Install Miniconda for Python and NVM Version of Node.js - DONE

[Python][67] is such a success in large part because of its very active community
in which people share their awesome solutions.
Unfortunately, there is a price.
[Python packages][68] you used get updated with a better way to solve their problem.
These changes can be breaking changes for the code you have written.

There are several ways to deal with this issue and I have chosen to manage it by using
[Miniconda][70], a much smaller base installation than [Anaconda][69],
but with the ability to scale up to the whole Anaconda distribution, if you chose to do so.
The Miniconda Python system requires ~400MB of disk space, where Anaconda requires ~3GB of disk space

The following steps install Miniconda.
Not only will Miniconda will be installed but your `bash` shell environment
(specifically the files `.bashrc` or `.bash_profile`)
will be updated to include Miniconda in the `$PATH`.
Also, if the environment variable `$PYTHONPATH` is set, you will get a warning like
"*please verify that your $PYTHONPATH only points to directories of packages that are compatible with the Python interpreter in Miniconda3*"

```bash
# create a directory to install miniconda in
mkdir -p ~/.miniconda3

# determine the processor architecture of your Linux system
$ uname -m
x86_64

# download latest miniconda version - https://repo.anaconda.com/miniconda/
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/.miniconda3/miniconda.sh

# run the install script
bash ~/.miniconda3/miniconda.sh -b -u -p ~/.miniconda3

# delete the install script
rm -rf ~/.miniconda3/miniconda.sh
```

Following the steps above, restart the terminal and Miniconda is ready to go.

```bash
# restart your terminal

# add a conda initialize to your bash   <-- DO NOT run `conda init bash` if you plan to use `~/.dotfile` since it already contains the changes needed for `~/.bashrc`
#~/.miniconda3/bin/conda init bash

# verify the installation by listing the contents of the install
conda list

# list the environments established (should only be 'base')
conda env list
```

There are at least two ways to install Node.js.
You could do it via a Ubuntu repository package,
but a superior way is to using [Node Version Manager (`nvm`)][48]
along with the [Node Package Manager (`npm`)][47].
Now let's install the [Long Term Support (LTS)][49] version of [Node.js][50].

```bash
```bash
# download and install node version manager (nvm) - https://nodejs.org/en/download
mkdir $HOME/.nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
\. "$HOME/.nvm/nvm.sh"      # in lieu of restarting the shell
nvm install 22              # download and install node.js LTS version 22

# verify the node.js version
$ node -v
v22.15.0

# verify the node version manager (nvm) version
$ nvm current
v22.15.0

# verify node package manager (npm version
$ npm -v
10.9.2
```


#### Step 3B: If You Wish to Uninstall Miniconda - DONE-NOT

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

* [How to Uninstall Miniconda on Linux: A Guide](https://saturncloud.io/blog/how-to-uninstall-miniconda-on-linux-a-guide/)
* [Install Miniconda on Linux from the command line in 5 steps](https://javedhassans.medium.com/install-miniconda-on-linux-from-the-command-line-in-5-steps-403912b3f378)


#### Step 4: Install Google Chrome - DONE

My go-to browser is Chrome and you can install it on Ubuntu from [here][50].

```bash
# determine the processor architecture of your Linux system
$ uname -m
x86_64

# download the latest Google Chrome .deb package
cd Downloads
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

# installing packages on Ubuntu
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

Installing Chrome will also add the repository to your package manager.
Use the following command to keep Chrome up to date on your system.

```bash
# to update chrome, use the following
sudo apt install google-chrome-stable

# test chrome
google-chrome &
```


#### Step 4B: Uninstall Google Chrome - DONE-NOT

If you decide that you’d like to remove Chrome from your system in the future,
use the following command to uninstall the web browser.

```bash
# use the following to remove chrome
sudo apt purge google-chrome-stable
```


#### Step 5: Install Nerd Fonts - DONE

Ubuntu bundled its own fonts,
and they are all Free Libre Open Source Software licensed (FLOSS).
The fonts included by default in Ubuntu are of course different to other operating systems.
On Ubuntu, fonts installation is located in two places:
User fonts - `~/.local/share/fonts/` and System fonts - `/usr/share/fonts/`.

The terminal version of NeoVim, we will use whatever font your terminal is using.
So to implement your preferred font,
you’ll need to change the font of your terminal emulator.
In my case, the terminal emulators I use are [`gnome-terminal`][51] and [`alacritty`][52].

Nerd Fonts is a project that patches developer-targeted fonts with many [glyphs][54] ([icons][55]).
It includes [programming ligatures][56] and is designed to enhance the appearance of source code.
Nerd Fonts also includes additional broad range of glyphs giving geeks more eye candy.

```bash
# list all the available fonts
fc-list

# check if any nerd fonts are already installed
fc-list | grep -i nerd
```

Now lets install the tool, [getNF (aka `getnf`)][58],
we'll use to load Nerd Fonts on our system:

```bash
# cloning the nerd fonts installation tool 'getnf'
mkdir ~/src
cd ~/src
git clone https://github.com/ronniedroid/getnf.git
cd getnf
./install.sh
```

To find a font that you find appealing,
check out [programmingfonts.org](https://www.programmingfonts.org/)
and [CodingFont](https://www.codingfont.com/).

Make sure that `~/.local/bin` is in your PATH so that `getnf` is executable.
Now to install the fonts,
we'll run `getnf` and select from the menu what fonts to install.
Choose one or more fonts (by index/number) to install
Hit Return/Enter to install the selected fonts.
Type the index/number corresponding to 'Quit' to cancel.

```bash
# you can load fonts from your home directory
cd $HOME

# read the getnf help information
getnf --help

# using `gitnf`, install the following fonts: JetBrainsMono
getnf

# check if the nerd fonts have been added
ls ~/.local/share/fonts
```

At this point, you'll need to restart your X Windows desktop manager so the `gnome-terminal`
application picks up the change.
With that, within a `gnome-terminal` window,
click the "hamburger" menu > **Preferences** > **Default** > select your Nerd Font.
I selected `JetBrainsMonoNL Nerd Font Mono` and font size `9`.
See "[Our favorite fonts for the Linux terminal][57]" for more information.

Once the font files are copied to these locations,
you need to refresh system wide font cache to complete the installation.
To do so, run the following command:

```bash
# refresh system wide font cache to complete the installation
sudo fc-cache -vf ~/.local/share/fonts
```

The fonts in `~/.local/share/fonts` are available for all apps now.

Using the command-line on the GTKtec M6 client,
execute `gnome-terminal` and `alacritty` to make sure they pop-up a window logged into the client:

```bash
# execute terminal sessions and make sure these new windows pop-up on your server but logged into you client
alacritty         # this worked nicely
gnome-terminal    # for some reason, this did not work ... it hung
```

Sources:

* [How to Install Nerd Fonts on Linux](https://bytexd.com/how-to-install-nerd-fonts-on-linux/)
* [How to Install Nerd Fonts on Linux](https://www.geekbits.io/how-to-install-nerd-fonts-on-linux/)
* [Nerd Fonts](https://www.nerdfonts.com/#home)
* [GitHub: ryanoasis/nerd-fonts](https://github.com/ryanoasis/nerd-fonts)
* [Add Icons to your Fonts with Nerd Fonts](https://www.youtube.com/watch?v=fR4ThXzhQYI)
* [Neovim 101 — Fonts](https://alpha2phi.medium.com/neovim-101-fonts-da575bd4eda9)
* [Installing system nerd-fonts with ansible](https://waylonwalker.com/ansible-install-fonts/)
  * [No More Missing Fonts | ansible-playbook](https://www.youtube.com/watch?v=2MEmsinxRK4)


#### Step 5B: Uninstall Nerd Fonts - DONE, NOT

To remove fonts installed on User directory:
Go to `~/.local/share/fonts/` and delete the files with `.ttf` or `.otf` extensions.
Repeat this step for each of the targeted fonts.


#### Step 6: Install Favorite Text Editor: NeoVim - DONE

There are several sources for [NeoVim][51],
but I have found that [Snap][54] has one of the most up to date versions.
I installed NeoVim via the [Snap Store][59] using this method:

```bash
# make sure python and node.js are installed as outline above (Step 3)

# neovim has nightly & stable version available on the snap store - https://snapcraft.io/install/nvim/ubuntu

# stable builds for neovim - latest/stable v0.11.0
sudo snap install nvim --classic

# install alacritty via snap to get the latest release
sudo snap install alacritty --classic

# to update snap package for neovim
sudo snap refresh nvim

# check the nvim version
$ nvim --version | grep NVIM
NVIM v0.11.0
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
#$ echo $XDG_SESSION_TYPE
#wayland

# if your using X Window's X11 protocol
sudo apt install xsel

# if your using X Window's Wayland protocol (other wise install 'xset')
sudo apt install wl-clipboard
```

To fix complaints about lack of Python, Node.js, `ripgrep` support,
you need to install Python, Node.js, and other tools.
This should be already established on the `/home` drive.
**Note** that I'm using Miniconda for my Python environment
you must activate the `base` environment, if not already done via your shell.

```bash
# if not already, activate your 'base' python environment
conda activate base

# neovim python support
pip install pynvim

# neovim node support
npm i -g neovim

# install yarn
npm install -g yarn

# ripgrep (executable is called `rg`) is need by for telescope
sudo apt install ripgrep

# ruby & gem are used by neovim and must be in your $PATH
sudo apt install ruby-full

# install a C compiler, specifically gcc (gnu compiler collection)
sudo apt install build-essential

# install luacheck for linting lua code
sudo apt install lua-check

# install perl scripting language
sudo apt install perl
```


---------------


# Enable Screen Sharing

At times, I want to remote desktop into NucBoxM6 so I can take full advantage of the desktop GUI menu system,
and not be relegated to a command-line interface you get from Secure Shell (SSH).
There are in fact [many remote desktop software packages][46] available to choose from,
but only small number seem to have a  significant following in the Linux world,
and [Virtual Network Computing (VNC)][45] is the de-facto remote desktop protocol for Linux.
But both `desktop` and `NucBoxM6` are Ubuntu/Gnome systems,
and there is an easy to configure Gnome specific screen sharing solution.

* Within the `docs` folder, see the document "install-vnc-on-linux-for-remote-access-and-screen-sharing.md".
* [How use Remote Desktop Address when desktop sharing on Ubuntu 22.04](https://askubuntu.com/questions/1501258/how-use-remote-desktop-address-when-desktop-sharing-on-ubuntu-22-04)
* [How to remote desktop into Ubuntu](https://www.itpro.com/mobile/remote-access/368102/how-to-remote-desktop-into-ubuntu)
* [Screen sharing (Remote Desktop) in Ubuntu 24.04.1 LTS?](https://www.reddit.com/r/Ubuntu/comments/1g42tyb/screen_sharing_remote_desktop_in_ubuntu_24041_lts/)

#### Step X: Install Some Screen Sharing Tool - DONE, NOT

--------------


# Install Docker

**Docker** is a popular application that simplifies the process of managing application processes in containers.
Containers let you run your applications in resource-isolated processes.
They’re similar to virtual machines, but containers are more portable,
more resource-friendly, and more dependent on the host operating system.

>**NOTE:** By default, the docker command can only be run the root user
>or by a user in the docker group, which is automatically created during Docker’s installation process.

Sources:

* [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)
* [Install the Compose Plugin](https://docs.docker.com/compose/install/linux/#install-using-the-repository)

## Docker Engine & Docker Compose

Ubuntu is my go-to Linux OS and installing on Ubuntu is fairly straight-forward.
I'll used the installation scripts below.
This involves adding a new package source,
adding the GPG key from Docker to ensure the downloads are valid,
and then install the Docker package.


#### Step 1: Install Docker - DONE

While not the absolute latest Docker version,
I’ll install Docker from the Dockers official Ubuntu repository,
instead of Docker's generic repository.

```bash
# before you can install docker engine, you need to uninstall any previous installed conflicting packages
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done

# clean up any existing docker related data
rm /var/lib/docker/*

# update your existing list of ubunutu packages
sudo apt update
```

Now let do the actual install of Docker:

```bash
# add Docker's official gpg key
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# add the repository to apt sources
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

From the above last command,
you'll see the installation will be from the Docker repository for what ever version of Ubuntu you are running.
Now lets install Docker:

```bash
# install the latest version of docker
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# docker should be running, but make sure
sudo service docker start
sudo service docker status

# verify that the docker engine installation is successful running
sudo docker run hello-world
```

Source:

* [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)

#### Step 2: Install Docker Compose - DONE

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

#### Step 4: Upgrade Docker & Docker Compose - DONE

Docker & Docker Compose will be automatically by Ubuntu from the official Ubuntu repository for Docker.


---------------


# Devices in Linux & Docker

* [Devices in Docker - Not so simple! (Docker for Robotics #4)](https://www.youtube.com/watch?v=uf4zOigzTFo)
* [Logitech F310 Gamepad Review On Linux](https://www.gamingonlinux.com/2015/05/logitech-f310-gamepad-review-on-linux/)

I purchased a [Logitech F310 Wired Gamepad Controller](https://www.logitechg.com/en-gb/products/gamepads/f310-gamepad.940-000138.html) on [Amazon](https://www.amazon.com/dp/B003VAHYQY) for $20.
The Logitech F310 Wired Gamepad Controller is generally supported out-of-the-box in Ubuntu.
It's a USB wired controller that typically works directly when plugged into a PC without requiring special drivers.
The F310 has both [D-Input (DirectInput) and X-Input (XInput) modes](https://www.howtogeek.com/792984/directinput-vs.-xinput-for-game-controllers-whats-the-difference/), which are widely supported by Linux games.

Some Linux programs for testing devices:

* The [`evtest`](https://manpages.ubuntu.com/manpages/noble/man1/evtest.1.html) tool in Linux is used to monitor and query events generated by input devices, such as keyboards, mice, joystick, and touchpad. It helps in debugging issues with input devices and understanding the events they generate.
You can use `evtest` to see what events are generated when you press a specific key on your keyboard or click a mouse button.
It allows users to monitor the raw data coming from keyboards, mice, touchscreens, joysticks, and other input peripherals.
* [`jstest-gtk`](https://manpages.ubuntu.com/manpages/jammy/man1/jstest-gtk.1.html) is  mainly a graphical interface to check that your joysticks and pads work properly. You can find precise information on each axis, you can optionally recalibrate it and also change the mapping.
If you run the program without parameters, you will get a window showing all the joystick devices in your system  (there  can  be more than one).
* Install these tools with `sudo apt install evtest jstest-gtk`

* Gemini Prompt: In linux, how do I configure a joystick or gamepad
* [How do I configure a joystick or gamepad?](https://askubuntu.com/questions/32031/how-do-i-configure-a-joystick-or-gamepad)


---------------


# Install Robot Operating System (ROS)

ROS is released as distributions, with more than one ROS distribution supported at a time.
Some releases come with long term support (LTS),
meaning they are more stable and have undergone extensive testing.
The latest LTS distribution is supported on Ubuntu 24.04 and called [ROS 2 Jazzy Jalisco][11].

There is also a [Docker version ROS 2 Jazzy Jalisco][12] for the install.
This could be a preferred installation approach and the one used
by the ["Robotics and ROS 2 Essentials" course][13].
I'm using this course as my guide for this "getting started with ROS" document.
I'll be following the courses setup and ROS exercises.

Beyond the courseware, I'll be using these sources:

* [ROS Package Documentation](https://docs.ros.org/): On this site you can find the core tutorials and documentation for the project as well as generated API documentation for individual packages.
* [Robotics Stack Exchange](https://robotics.stackexchange.com/): It is likely that the ROS developer community has posted questions similar to yours; if your question isn’t already asked, post a new one.
* [ROS Index](https://index.ros.org/): When you want to find out information about a specific package the index is the best place to start.


## Running ROS 2 Jazzy Jalisco on Ubuntu Linux

Sources:

* [Install ROS2 Jazzy and Ubuntu Linux on Raspberry Pi + Optimize the Performance -Everything Explained](https://www.youtube.com/watch?v=saoBiYCi3Uo)
* [How to install ROS2 Jazzy on Raspberry Pi 5 and Linux Ubuntu](https://aleksandarhaber.com/how-to-install-ros2-jazzy-on-raspberry-pi-5-and-linux-ubuntu/#google_vignette)
* [ROS 2 Documentation: Installation - Ubuntu (deb packages)](https://docs.ros.org/en/jazzy/Installation.html)

#### Step 1: Check Character Encoding Standard - DONE

Make sure you using the [UTF-8](https://en.wikipedia.org/wiki/UTF-8) [character encoding](https://en.wikipedia.org/wiki/Character_encoding) standard.
Most likely you are.

```bash
# check character encoding standard
$ echo $LANG
en_US.UTF-8
```

#### Step 2: Enable Required Repositories for ROS2 - DONE

```bash
# ensure that the ubuntu universe repository is installed
sudo apt install software-properties-common
sudo add-apt-repository universe

# add the ROS 2 GPG key with apt
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

# add the repository to your sources list
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

#### Step 3: Install ROS 2 - DONE

* `ros-dev-tools` are a suite of command-line tools and libraries used to manage, introspect,
and interact with the ROS 2 system.
These tools provide functionality for tasks like managing nodes, topics, services
and more, both for developers and users.
* `ros-jazzy-ros-base` provides the essential tools and libraries for developing ROS 2 applications
including build tools but no graphical user interface (GUI) components.
* `ros-jazzy-desktop`, on the other hand, builds upon `ros-jazzy-ros-base`
and includes all the necessary GUI tools for development
and running ROS 2 applications, such as RVIZ, Gazebo, and graphical editors.

>**NOTE:** The error "Could not get lock /var/lib/dpkg/lock" is a frequent Ubuntu error.
>It occurs when the system tries to execute several commands that need access to the same file,
>usually the `/var/lib/dpkg/lock` file.
> See [here](https://phoenixnap.com/kb/fix-could-not-get-lock-error-ubuntu) how to fix it.

```bash
# for building ROS packages or otherwise do development
sudo apt update && sudo apt install ros-dev-tools

# ROS 2 packages are built on frequently updated ubuntu systems
sudo apt upgrade

# ROS-base communication libraries, message packages, command line tools
sudo apt install ros-jazzy-ros-base

# desktop install of ROS, RViz, demos, tutorials
sudo apt install ros-jazzy-desktop
```

#### Step 4: Setup ROS Environment and Verify

With `ros-jazzy-ros-base` and `ros-jazzy-desktop` installed,
you can do a simple ROS2 implementation to verify things are working.

In one terminal, source the setup file and then run a C++ `talker`:

```bash
# set up your environment and then activate `talker`
source /opt/ros/jazzy/setup.bash
ros2 run demo_nodes_cpp talker
```

In another terminal source the setup file and then run a Python `listener`:

```bash
# set up your environment and then activate `listener`
source /opt/ros/jazzy/setup.bash
ros2 run demo_nodes_py listener
```

You should see the `talker` saying that it’s Publishing messages and the `listener` saying I heard those messages.
This verifies both the C++ and Python APIs are working properly.

#### Step 5: Uninstall ROS2 - DONE, NOT

If you need to uninstall ROS 2 or switch to a source-based install
once you have already installed from binaries, run the following command:

```bash
# remove ros repositories
sudo apt remove ~nros-jazzy-* && sudo apt autoremove

# you may also want to remove the repository
sudo rm /etc/apt/sources.list.d/ros2.list
sudo apt update
sudo apt autoremove
sudo apt upgrade            # consider upgrading for packages previously shadowed
```

#### Step 6: Install `turtlesim`

`turtlesim` is a ROS way of paying homage to the late 1960's educational programming language
[Logo](https://en.wikipedia.org/wiki/Logo_(programming_language)) and [Turtle graphics](https://en.wikipedia.org/wiki/Turtle_graphics)
created by Seymour Papert.
Children could use a [Logo turtle robot](https://runestone.academy/ns/books/published/apcsareview/TurtleGraphics/turtleBasics.html),
that they programmed, to draw geometric shapes on paper.
Here is a [modern version](https://www.niklasroy.com/robotfactory/)

```bash
# install turtlesim
sudo apt update
sudo apt install ros-jazzy-turtlesim

# check if the package is installed - return a list of turtlesim’s executables
$ ros2 pkg executables turtlesim
turtlesim draw_square
turtlesim mimic
turtlesim turtle_teleop_key
turtlesim turtlesim_node

# start turtlesim - this is node 1
ros2 run turtlesim turtlesim_node
```

Open a new terminal and source ROS 2 again.
Now you will run a new node to control the turtle in the first node:

```bash
# start another turtlesim node to control the turtle - this is node 2
ros2 run turtlesim turtle_teleop_key
```

You can now use the arrow keys on your keyboard to control the turtle.
It will move around the screen,
using its attached “pen” to draw the path it followed so far.

You can see the nodes, and their associated topics, services, and actions,
using the list subcommands of the respective commands:

```bash
# see the nodes, and their associated topics, services, and actions
ros2 node list
ros2 topic list
ros2 service list
ros2 action list
```

There is a friendly way to interact with nodes, and their associated topics, services, and actions.
In ROS 2, `rqt` is a graphical user interface (GUI) framework for
visualizing, controlling, and debugging ROS 2 systems.
It provides a way to interact with ROS 2 nodes, topics, services, and other components
through a user-friendly interface, according to the ROS 2 documentation.
`rqt` is built on top of the Qt framework, a tool for developing GUI-based applications.

```bash
# install rqt
sudo apt install '~nros-jazzy-rqt*'

# run rqt
# when running oqt for the first time, the window will be blank,
# just select Plugins > Services > Service Caller from the menu bar at the top
rqt
```


--------------


# Install ROS on Windows Subsystem for Linux (WSL)

* [Install ROS2 Jazzy on Windows Subsystem for Linux and Windows 11 and 10](https://www.youtube.com/watch?v=cLpVG51EImQ)


--------------


## Running ROS 2 Jazzy Jalisco in Docker Container

One of the ROS courses on the Web is ["Robotics and ROS 2 Essentials"][13],
which is a beginner-friendly introduction to robotics and ROS 2,
and it has a focus on learning by doing and experimenting through exercises.
The practical exercises that accompany the theoretical content are
based on a Gazebo simulation with the [simulated Andino robot from Ekumen][14].

One of the nice things about this course is that ROS doesn't need to be installed on your system.
Instead, the course uses Docker to provide all the course exercises in a containerized environment,
requiring no manual installation of ROS 2, simulation, packages, and dependencies.
All you need is an Ubuntu Operating System and Docker installed, and you are all set!

### Setup for Dockerized ROS

Despite it simplicity, there are some challenges to get it working within my configuration
where I wish to running a X Window System (X11) application on my server (the GMKTec with Ubuntu 24.04)
but display its graphical output on a remote client (my `desktop` with Ubuntu with X Window).
**This will not work for me.**
Appears the Docker container was built to support everything working on the server.
So that is documented below.

>**NOTE:** No preliminary ROS 2 installation is required.
>Instead, the course uses Docker to provide all the course exercises in a containerized environment,
>requiring no manual installation of ROS 2, simulation, packages, and dependencies

#### Step 0: Install ROS Docker Container

[Exercises 0 - Setup](https://github.com/henki-robotics/robotics_essentials_ros2/tree/main/0-setup)

```bash
# clone the repository containing ros2 and gazebo simulator
cd ~/src
git clone https://github.com/henki-robotics/robotics_essentials_ros2.git

# create a new workspace for your exercises, this will be automatically mounted and available from the docker container
mkdir -p $HOME/exercises_ws/src
```

Before bring up the Docker container, run the following command.
This will give permissions to your containers to send their display to the containers host system.

```bash
# give permissions to your containers to send their display to the containers host system.
xhost +

# use docker compose to build and run the Docker container
cd ~/src/robotics_essentials_ros2/docker/
sudo docker compose up
```

Now open a new terminal (e.g. via `CTRL+ALT+T` and run this command to start a new terminal inside the Docker container.
The `docker exec` command opens a new terminal inside this Docker container,
allowing you to interact with it.

```bash
# get terminal access to the inside of the docker container
sudo docker exec -it robotics_essentials_ros2 bash
```

Now while in the terminal inside the Docker container, we perform a test to make sure everything is working correctly:

```bash
# while inside the docker container
# perform a test to make sure everything is working correctly
ros2 launch andino_gz andino_gz.launch.py
```

Sources:

* [Robotics and ROS 2 Essentials: Exercises 0 - Setup](https://github.com/henki-robotics/robotics_essentials_ros2/tree/main/0-setup)
* [GUI apps within a Docker container](https://medium.com/@paliwalsamriddhi/gui-apps-within-a-docker-container-971681838fda)
* [X11 forwarding from a docker container in remote server](https://unix.stackexchange.com/questions/403424/x11-forwarding-from-a-docker-container-in-remote-server)

#### Step 1: Exercises 1 - ROS 2 Introduction

In this [Exercises 1 - ROS 2 Introduction](https://github.com/henki-robotics/robotics_essentials_ros2/tree/main/1-ros_2_introduction#basic-concepts),
**ROS 2 Topics** are the first to be explore.
ROS 2 Topics are a core communication mechanism in ROS 2 that enable
data exchange in a publish/subscribe model.
Publishers send messages to a named topic,
while subscribers listen to that topic to receive relevant data.

In another terminal, execute these commands:

```bash
# in another terminal, gain access to ros
sudo docker exec -it robotics_essentials_ros2 bash

# list all the available ROS 2 topics
$ ros2 topic list
/camera_info
/clicked_point
/clock
/cmd_vel
/goal_pose
/image_raw
/initialpose
/joint_states
/odom
/parameter_events
/robot_description
/rosout
/scan
/scan/points
/tf
/tf_static

# get more info about the /camera_info topic to learn the message type
$ ros2 topic info /camera_info
Type: sensor_msgs/msg/CameraInfo
Publisher count: 1
Subscription count: 0

# get more info about the /scan topic to learn the message type
$ ros2 topic info /scan
Type: sensor_msgs/msg/LaserScan
Publisher count: 1
Subscription count: 1

# read the sensor data from the laser scanner (press CTRL+C to stop)
ros2 topic echo /scan

# move the robot by publishing to /cmd_vel topic
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist "{linear: {x: 0.2}}"

# send zero velocity command to stop the robot
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist "{linear: {x: 0.0}}"

# rotate the robot with this command
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist "{angular: {z: 0.5}}"

# to stop the rotation, do the following
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist "{angular: {z: 0.0}}"
```

**RViz** is a useful visualization tool that allows us to display data from ROS 2 topics.
The robot is constantly publishing images from the simulated camera.
Let's see how those images look like!

In ROS 2, **Coordinate Transforms (TF)**
are used to describe the spatial relationships between different coordinate frames in a robotic system.
They sit at the center of the robot, at the center of sensors, at joints,
and there are so the "Map" and "Odometry" frames.

Commonly used coordinate frames are as follows:

* **map** - The map frame provides a global reference point for the robot's environment,
allowing it to understand its position within a larger context.
Typically, the coordinates in the map frame present the robot's coordinates on a 2D map.
* **odom** - The odom frame represents the robot's position based on its odometry data.
It tracks the robot's movement from its starting point, being subject to drift and inaccuracies.
* **base_footprint** - The base_footprint frame is a 2D representation of the robot's footprint on the ground,
typically used for planning and movement calculations without considering the robot's height.
* **base_link** - The base_link frame represents the robot's main body
and is used as a reference for other components, such as sensors and arms.
* **laser_link** - The laser_link frame denotes the position of a laser sensor on the robot.
It is essential for interpreting the data collected by the laser
for tasks like mapping and obstacle detection,
providing a reference for where the sensor is located in relation to other frames.

TF frames in RViz

* **fixed frame** - The fixed frame is used to determine from which frame's perspective you are visualizing the data.
This is an important feature to know about,
as sometimes the data you are looking to visualize might not be available if you are visualizing a wrong frame.

TFs allow you to convert positions and orientations from one frame to another,
and basically keep track of how each part of your robot moves in relation to the other parts of the robot.
This is crucial for tasks like navigation, sensor fusion, and manipulation.
By using transforms, robots can effectively understand their position in the world and how their sensors
and motors are located in relation to their body.

The relationship between these coordinate frames is determined with **tf-tree**.
It essentially tells, with a tree-like structure,
what is the child-frame's position in relation to the parent frame.

#### Step 2: Exercises 2 - SLAM and Navigation Demo

In this [Exercises 2 - SLAM and Navigation Demo](https://github.com/henki-robotics/robotics_essentials_ros2/blob/main/2-slam_and_navigation_demo/README.md),
we'll use the robot to build a new 2D map of the simulated environment and autonomously navigate on it.
The packages that will be used perform these tasks are:

* [Slam-toolbox](https://github.com/SteveMacenski/slam_toolbox/tree/ros2) is an advanced 2D SLAM (Simultaneous Localization and Mapping)
solution for ROS 2.
* [Nav2, aka Navigation2](https://github.com/ros-navigation/navigation2), is a framework for ROS 2 that enables robots to navigate autonomously.
* [AMCL](https://github.com/ros-navigation/navigation2/tree/main/nav2_amcl) (stands for [Adaptive Monte Carlo Localization](https://roboticsknowledgebase.com/wiki/state-estimation/adaptive-monte-carlo-localization/)) is a probabilistic localization system used in ROS 2, and is part of the Nav2 stack.
It enables robots to determine their position within a known map using particle filters.
AMCL uses sensor data, typically from a LiDAR, to refine the estimated pose of the robot as it navigates.

To get ROS2 up & running, execute these commands in a terminal:

```bash
# give permissions to your containers to send their display to the containers host system.
xhost +

# use docker compose to build and run the Docker container
cd ~/src/robotics_essentials_ros2/docker/
sudo docker compose up
```

In another terminal, gain access to ROS within the container
and run the simulator:

```bash
# in a terminal, gain access to ros
sudo docker exec -it robotics_essentials_ros2 bash
ros2 launch andino_gz andino_gz.launch.py

# run slam-toolbox
sudo docker exec -it robotics_essentials_ros2 bash
ros2 launch andino_gz slam_toolbox_online_async.launch.py
```

In RViz, subscribe to /map topic to view the map that is being built
Use Gazebo teleop to drive the robot around in the simulation and map the area.

Once you are satisfied with the map,
open a new terminal inside the Docker container and run this command to save it:

```bash
# in another terminal, gain access to ros
sudo docker exec -it robotics_essentials_ros2 bash

# launch the Andino simulation with Nav2
ros2 launch andino_gz andino_gz.launch.py nav2:=True
```

#### Step 3: Exercises 3 - Create Your First Ros 2 Package


In this [Exercises 3 - Create Your First Ros 2 Package](https://github.com/henki-robotics/robotics_essentials_ros2/tree/main/3-create_ros_2_package)

#### Step 4: Exercises 4 - Robot Odometry

In this [Exercises 4 - Robot Odometry](https://github.com/henki-robotics/robotics_essentials_ros2/tree/main/4-robot_odometry)

#### Step 5: Exercises 5 - Path Planning

In this [Exercises 5 - Path Planning](https://github.com/henki-robotics/robotics_essentials_ros2/tree/main/5-path_planning)

#### Step 6: Remove All Stopped Containers

To clean up all the Docker object created by this course,
execute the following:

```bash
# stop and remove all of parts of the 'robotics_essentials_ros2' container
sudo docker stop robotics_essentials_ros2
sudo docker rm robotics_essentials_ros2
sudo docker rmi --force robotics_essentials_ros2
```



[01]:https://ubuntu.com/download/desktop
[02]:https://blog.lon.tv/2024/08/18/gmktec-m6-review-the-mid-range-of-the-low-cost-mini-pc-market/
[03]:https://www.ros.org/
[04]:https://gazebosim.org/home
[05]:http://wiki.ros.org/rviz
[07]:https://www.digitalocean.com/community/tutorials/how-to-enable-remote-desktop-protocol-using-xrdp-on-ubuntu-22-04
[08]:https://www.tightvnc.com/
[09]:https://goteleport.com/blog/x11-forwarding/
[10]:https://hackaday.com/2018/05/31/modular-robotics-made-easier-with-ros/
[11]:https://docs.ros.org/en/jazzy/Installation.html
[12]:https://hub.docker.com/_/ros/
[13]:https://henkirobotics.com/robotics-and-ros-2-essentials-course-announcement/
[14]:https://github.com/Ekumen-OS/andino_gz/tree/humble
[15]:https://www.linkedin.com/pulse/introduction-understanding-visual-robot-models-urdf-kangal/
[16]:https://en.wikipedia.org/wiki/Willow_Garage
[17]:https://en.wikipedia.org/wiki/Robot_Operating_System

[45]:https://en.wikipedia.org/wiki/VNC
[46]:https://en.wikipedia.org/wiki/Framebuffer
[47]:https://www.npmjs.com/
[48]:https://www.freecodecamp.org/news/node-version-manager-nvm-install-guide/
[49]:https://nodejs.org/en/about/previous-releases
[50]:https://nodejs.org/en
[51]:https://help.gnome.org/users/gnome-terminal/stable/
[52]:https://alacritty.org/
[53]:https://www.nerdfonts.com/
[54]:https://ubuntu.com/core/services/guide/snaps-intro
[55]:https://www.amazon.com/dp/B09KKYS967
[56]:https://www.msi.com/Motherboard/PRO-Z690-A/support#manual
[57]:https://opensource.com/article/23/4/linux-terminal-fonts
[58]:https://help.ubuntu.com/community/CronHowto
[59]:https://snapcraft.io/install/nvim/ubuntu

[67]:https://www.python.org/
[68]:https://pypi.org/
[69]:https://www.anaconda.com/
[70]:https://www.anaconda.com/docs/getting-started/miniconda/main




