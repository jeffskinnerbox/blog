<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.1
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----


# What is Bottles?
Bottles is similar to [Wine][07] (a popular compatibility layer for Windows)
but offers some advanced options.
For one, Bottles allows you to install Windows software on Linux with ease.
If you are also interested in running any Windows software on Linux,
you should install Bottles on your machine,
Wine will be installed under Bottles.

Bottles is an open-source application that can simplify and manage Wine.
Wine imitates the Windows C drive
and includes all the necessary files to use Windows-based applications on Linux.
However, Wine require a few upgrades,
and Bottles was developed to provide this in a GUI.

In simple words, Bottles allows you to run different games and software in Linux
by imitating the C drive to provide the Windows environment in Linux.
You can also use Bottles GUI to tweaking options to change the system settings according to any specific program's requirements.

## How Do You Install Bottles?
You can install Bottles through different package formats such as [DEB, Flatpak, AppImage, Snap, etc][10].
However, there is a difference between Flatpak, AppImage, and Snap,
so choose the one according to your needs.
Ubuntu and other Debian-based distros use the `.deb` package format natively.
Native packages are fast as they are designed and compiled specifically for a system,
and they also share libraries, keeping apps smaller.
Distro independent packages like Snap, AppImage, and Flatpak
provide apps that can run on different machines.
They take away the dependency issues many Linux users face every day
and make life a lot easier for developers.
However, this also results in larger binaries.

* **DEB** - Ubuntu and other Debian-based distros use the `.deb` package format natively.
* **Snap** - A packaging system developed by Canonical and has significant corporate backing.
When you install the snap version of an app, it includes all the libraries and dependencies required to run that app.
This saves app maintainers the time needed to roll out different builds for different systems.
* **AppImage** - A great way to try out new apps without installing them on your machine.
The concept behind AppImage is fairly simple: one file per app.
This way, developers can ensure the portability of their apps,
and users get to try out new packages without installation.
A major advantage of AppImages is that they don't require sudo permissions in Linux.
* **Flatpak** - This is another distro agnostic packaging system that ships apps with required dependencies.
Users can find and install flatpaks from the distribution store of popular Linux systems or via the CLI.
Flatpak apps run in an environment separate from the host system's runtime.
The isolated nature of Flatpak packages makes them inherently secure,
and system changes can only occur if the user provides explicit permission.
However, Flatpak packages usually take up more space than Snaps or AppImages.
They are also slower compared to AppImages but faster than Snap packages.

For some opinions on what package format to use, check out these websites:

* [Snap vs. Flatpak vs. AppImage - In Depth Pros & Cons of Universal Packaging](https://www.youtube.com/watch?v=ywwTov7S9M0)
* [HUGE Speed Differences! Flatpak vs. Snap vs. AppImage](https://www.youtube.com/watch?v=OftD86RgAcc)
* [Flatpak vs Snaps vs Appimage vs Packages - Linux packaging formats compared](https://www.youtube.com/watch?v=9HuExVD56Bo)
* [Snap vs. AppImage vs. Flatpak: What Is the Difference and Which Is Best for You?](https://www.makeuseof.com/snap-vs-appimage-vs-flatpak/)
* [Run Windows Programs With Bottles in Linux](https://www.youtube.com/watch?v=o2HUNRPUDkU)

## I'll Use Flatpak
I'll use Flatpak to install Bottles on my Ubuntu desktop
(it's [Bottles recommended method][11]).
[Flatpak][01], formerly known as xdg-app,
is a utility for software deployment and package management for Linux.
[Flathub][04] is the home of hundreds of Flatpak packaged apps which can be
easily installed on any Linux distribution.
Flatpak is advertised as offering a sandbox environment in which
users can run application software in isolation
(like a [Linux Container][02], but strictly speaking it is not)
from the rest of the system.
Check out "[Frequently Asked Questions][03]" on the Flatpak website for more insights what it
is, and is not.

>**NOTE:** When comparing Docker vs Flatpak,
>most important reason people chose Flatpak is:
>You can install flatpak packages on any distro you want.
>
>Developers describe Docker as "Enterprise Container Platform for High-Velocity Innovation".
>Docker's focus is the enterprise server.
>On the other hand, Flatpak is discribed as "Build and distribute applications on Linux".
>It is a next-generation technology for building and distributing desktop applications on Linux.



------



# Setting Up Flatpak
Flatpak is a utility for software deployment and package management for Linux.
It is advertised as offering a sandbox environment in which
users can run application software in isolation from the rest of the system.
Another key feature of Flatpak is that it allows application developers
to directly provide updates to users without going through distributions,
and without having to package and test the application separately for each distribution

[Setting up Flatpak on any of the Linux distributions][04] is simple.
I'll do it here for Ubuntu.

Sources:

* [Flatpak Tutorial - Setting up Flatpak and installing Packages](https://www.youtube.com/watch?v=31WRiI1nk8Q)

#### Step 1: Install Flatpak - DONE
To install Flatpak on Ubuntu 18.10 or late,
and the Flathub application repository, simply run:

```bash
# install flatpak
sudo apt install flatpak

# this flatpak plugin makes it possible to install apps without needing the command line
sudo apt install gnome-software-plugin-flatpak

# add Flatpak application repository
$ flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

Note that the directories

'/var/lib/flatpak/exports/share'
'/home/jeff/.local/share/flatpak/exports/share'

are not in the search path set by the XDG_DATA_DIRS environment variable, so
applications installed by Flatpak may not appear on your desktop until the
session is restarted.

# reboot your system or restart your login session
sudo shutdown -r now
```

#### Step 2: Create Your First FlatPak Application - DONE
To install Flatpak applications, you just go to [Flathub's download site][05].
For my very first FlatPak application,
I'll install a ready built application called [Color Picker][12],
which helps you choose colors from the "picker" or from sampling the screen.
You can [find this package on FlatHub][12].

```bash
# list what flatpak package are already install (answer = none)
flatpak list

# install color picker via the commandline
flatpak install flathub nl.hjdskes.gcolor3

# list your flatpak package installed
flatpak list

# execute color picker
flatpak run nl.hjdskes.gcolor3
```

#### Step 3: Install the Bottles App - DONE
In this case, I'm going to install [Bottles][08] so I can execute MS Windows software.
Bottles is a [Wine installer for Linux][07].
It advoids the conflicts that can arise with Wine since Bottles create separate sandboxes for each Windows install.

To install Bottles, you could [search for it on Flathub][06],
or install it vid the command line:

```bash
# install bottles via the commandline
flatpak install flathub com.usebottles.bottles

# list what was installed
$ flatpak list
Name                                    Application ID                          Version   Branch         Installation
Bottles                                 com.usebottles.bottles                  50.2      stable         system
Color Picker                            nl.hjdskes.gcolor3                      2.4.0     stable         system
Freedesktop Platform                    org.freedesktop.Platform                22.08.5   22.08          system
Mesa                                    org.freedesktop.Platform.GL.default     22.3.2    22.08          system
Mesa (Extra)                            org.freedesktop.Platform.GL.default     22.3.2    22.08-extra    system
Mesa                                    org.freedesktop.Platform.GL32.default   22.3.2    22.08          system
Intel                                   org.freedesktop.Platform.VAAPI.Intel              22.08          system
ffmpeg-full                             org.freedesktop.Platform.ffmpeg-full              22.08          system
openh264                                org.freedesktop.Platform.openh264       2.1.0     2.2.0          system
GNOME Application Platform version 43   org.gnome.Platform                                43             system
i386                                    org.gnome.Platform.Compat.i386                    43             system
Yaru-sage-dark Gtk Theme                org.gtk.Gtk3theme.Yaru-sage-dark                  3.22           system
DXVK                                    org.winehq.Wine.DLLs.dxvk               1.10.3    stable-22.08   system
Gecko                                   org.winehq.Wine.gecko                             stable-22.08   system
Mono                                    org.winehq.Wine.mono                              stable-22.08   system
```

>**NOTE:** When you install a Flatpak, you are not prompted for root password,
>and are installed for the current user only.
>Flatpak's are not installed system wide, unless you use `sudo`.

To execute Bottles,
you can click the **Activities** button on the upper-left of the Ubuntu desktop
and search for it, or execute it on the commandline:

```bash
# execute bottles
flatpak run com.usebottles.bottles
```

Bottles window will pop-up and take you through an installation process.
This goes quickly and then you click the **Start using Bottle** button.
This gives you a Bottles environment with no bottles and no Libraries.
We'll create some bottles in the next sub-section below.

#### Step 4: List, Update, Search, Uninstall, etc. for Flatpak - DONE
Some additional commands well worth knowing are:

```bash
# install package on flathub via the commandline
flatpak install flathub <package>

# list your flatpak package installed
flatpak list

# execute package
flatpak run <package>

# search for a specific package
flatpak search <serach term>

# update flatpak
flatpak update

# remove a flatpak package
sudo flatpak uninstall <package>
```

If you wish to remove `flatpak` and all its packages,
do the following:

```bash
# uninstall flatpak, removing any leftover flatpak packages
flatpak uninstall --all
flatpak uninstall --unused --delete-data --force-remove
sudo apt purge --autoremove flatpak

# check that everything has been removed
ls /var/lib/flatpak/
ls ~/.local/share/flatpak/

# remove everything
rm -r -f /var/lib/flatpak/
rm -r -f ~/.local/share/flatpak/

# uninstall flatpak
sudo apt remove flatpak gnome-software-plugin-flatpak
```



------



# Install Some Bottles Apps
When everything is ready,
you will see [a screen telling you that there is no bottles yet][13].
To create your first bottle,
execute bottles via `latpak run com.usebottles.bottles`,
you will need to press the **Bottles** button (or the **+**) on the top left,
then the **Create a new Bottle...** button,
and proceed following the on-screen instructions.

* Give the bottle a name
* Select the **Application** button

To delete a bottle, select the bottle to be deleted,
goto the top right menu and select **Delete Bottle...**

Sources:

* [Bottles Installation](https://docs.usebottles.com/getting-started/installation)
* [How to install Windows software on Linux with Bottles](https://www.techrepublic.com/article/how-to-install-windows-software-on-linux-with-bottles/)
* [How to install Windows software on Linux with Bottles](https://www.youtube.com/watch?v=Fiiq4IkLvzM)
* [How to run Windows apps on Linux with Bottles](https://www.youtube.com/watch?v=VqDgrHCPWG8)
* [Easily Run Windows Apps On Linux With Bottles](https://www.youtube.com/watch?v=ttsGxu1o6pQ)

#### Step 1: Create Your First Bottle
Your first bottle will take a lengthy amount of time since many things will be
loaded into your environment with the first bottle,
In my case, my first application will be TurboTax.

To create this bottle,
execute bottles via `latpak run com.usebottles.bottles`,
you will need to press the **Bottles** button (or the **+**) on the top left,
then the **Create a new Bottle...** button,
and proceed following the on-screen instructions.

* Give the bottle a name, in my case "TurboTax"
* Select the **Application** button
* Install `ndp48-web.exe` from the [.NET Framework 4.8 download site][14].
I got a message that .NET Framework 4.8 is already installed.
* Installed `Windows_PC_TurboTax_Download.exe` from the TurboTax download site

If you need to mount the CD, see this [Mount an ISO image in Wine?](https://askubuntu.com/questions/278912/mount-an-iso-image-in-wine)





[01]:https://flatpak.org/
[02]:https://linuxcontainers.org/
[03]:https://flatpak.org/faq/
[04]:https://flatpak.org/setup
[05]:https://flathub.org/home
[06]:https://flathub.org/apps/details/com.usebottles.bottles
[07]:https://www.winehq.org/
[08]:https://usebottles.com/
[09]:https://www.autodesk.com/products/fusion-360/overview?term=1-YEAR&tab=subscription
[10]:https://www.makeuseof.com/snap-vs-appimage-vs-flatpak/
[11]:https://usebottles.com/download/
[12]:https://flathub.org/apps/details/nl.hjdskes.gcolor3
[13]:https://docs.usebottles.com/getting-started/first-run#your-first-bottle
[14]:https://dotnet.microsoft.com/en-us/download/dotnet-framework/thank-you/net48-web-installer
[15]:
[16]:
[17]:
[18]:
[19]:
[20]:

