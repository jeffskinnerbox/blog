<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----


# Remote Desktop
while away from my home LAN,
I want to remote desktop into Linux so I can take full advantage of the desktop GUI menu system,
and not be relegated to a commandline interface you get from Secure Shell (SSH).
There are in fact [many remote desktop software packages][42] available to choose from,
but only small number seem to have a  significant following in the Linux world,
and VNC is the de-facto remote desktop protocol for Linux.

[Virtual Network Computing (VNC)][49] uses the RFB (“remote framebuffer”) open protocol.
Because it works at the [framebuffer][42] level,
it is applicable to all windowing systems and applications,
including Microsoft Windows, MacOS, and the X Window System.
VNC can be quite a lifesaver for many who are not comfortable working
from the command-line and need to manage files,
install software, and configure settings on a remote server.

Linux X Window System has its own remote desktop tool, [Xephyr][43],
which allows you to nest X server within a X server (aka "X Nesting").
Cleaver but insecure, little used, an only available on X Window systems
(my experimentation with Xephyr can be found [here][44]).
There are other possibilities for accessing desktops remotely,
such as the [Remote Desktop Protocol (RDP)][52].
This is a proprietary protocol developed by Microsoft,
which provides a user with a graphical interface to
connect to another computer over a network connection.

Because of its popularity, VNC seems like the right choose of protocol.
The [VNC client/server model][48]
moves the whole video frame from the server to the VNCViewer on the client,
which give you a true representation of the remote desktop.
Contrast this with a popular alternative to VNC,
that being Windows Remote Desktop (WRD).
WRD does not transport frames, thereby reducing the bandwidth requirements (good),
but instead must create its own separate user session / rendering of the GUI experience (not so good).

There are [multiple instance of VNC implementation][47].
[RealVNC][45] appears to be [supported by Raspberry Pi Raspian OS][46],
on the other hand, [X11vnc][54] seems well tuned for X Windows,
and [TightVNC][49] comes installed within many Linux full distribution package.
But what is the [best VNC][50] ... could it be a useless question?
Just to keep it simple but functional,
I choose to explore [installing TigerVNC on my Ubuntu][51] desktop
(giving you remote access) along with X11vnc (giving you screen sharing).

>**NOTE:** TigerVNC is **not** the same as TightVNC but it is a fork of the TightVNC development
>which appears, from a development standpoint, to be dormant these days.
>See how TigerVNC compare to others [here][40] and [here][41].)

In my user scenario for VNC implemented below,
my Ubuntu desktop will be running the VNC Server so it can share its GUI user session with a VNC Viewer.
In this installation, I'm using Ubuntu 22.04 with the Gnome graphical desktop environment,
and the TigerVNC & X11vnc packages, both available from the official Ubuntu repository.
I followed mainly the following sources below:

Sources:
* TigerVNC
    * [How to Install and Configure VNC on Ubuntu 22.04][14]
    * [Install VNC Server with Gnome display on Ubuntu 18.04](https://www.teknotut.com/install-vnc-server-with-gnome-display-on-ubuntu-18-04/)
    * [How to install and configure VNC on Ubuntu](https://linuxhint.com/install-configure-vnc-ubuntu/)
    * [How To Install VNC Server on Ubuntu 22.04 LTS](https://idroot.us/install-vnc-server-ubuntu-22-04/)
* TightVNC
    * [How to Install & Configure VNC Server on Ubuntu 22.04|20.04](https://bytexd.com/how-to-install-configure-vnc-server-on-ubuntu/)
    * [How to Install and Configure VNC on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-22-04)
    * [Install and Configure VNC server on Ubuntu 22.04](https://itnixpro.com/install-and-configure-vnc-server-on-ubuntu-22-04/)
    * [Install and Configure VNC Server on Ubuntu 22.04|20.04|18.04](https://computingforgeeks.com/how-to-install-vnc-server-on-ubuntu/)
* X11vnc
    * [XXFCE: Remote Desktop via X11vnc Through an SSH Tunnel][56]
    * [How to install x11vnc vnc server as a service on Ubuntu 20.04, for remote access or screen sharing][64]
    * [How to Install and Run a VNC Server on Ubuntu Linux][67]

## Remote Access vs. Screen Sharing
You'll often find that the terms **Remote Access** and **Screen Sharing** are used interchangeably,
I'm going to consider them very different here.
My definitions are:

* **What is Screen Sharing? -**
Screen sharing, also known as desktop sharing,
is the practice of sharing the contents of the screen with another device
(or multiple devices) so all participants view, and possible, control the same screen.
Effectively all the participants are sharing the same login session and accessing the device simultaneously.
* **What is Remote Access? -**
Remote access is the ability of users to access a device or a network from any location.
With that access, users can login, creating an new user session,
and see a screen, manage files, etc. on the remote device.

So remote access, in it pure form, doesn't involve screen sharing with another user.
Remote access gives you a login for a user session
but you will not be sharing that user session with any other users.
For X Windows, this means the X [`$DISPLAY`][66] is different for each user session
(implying that the screens will have cosmetic differences).

On the other hand, screen sharing provide the same GUI experience for all user session,
and this user experience can be mutually shared in real-time.
In addition, that share user session could be alone (aka un-shared) or shared with many other users.
For X Windows, this means a single X `$DISPLAY` is being shared among users.

## Candidate Solutions
TigerVNC provides remote access by creating a new GUI session.
It creates another user session in addition to any other GUI sessions.
In fact, it doesn't have to be the same desktop experience that might be currently running elsewhere on the server.

So TigerVNC is not screen share where everyone sees the currently active local desktop session.
For that you need to use Ubuntu/Gnome built in vino (considered too slow) or X11vnc (much better).
X11vnc operate by "reading/replicating" the information for a user specified X display
(e.g. `:0` is your typical first GUI user display)
and streaming it out via the VNC protocol to a VNC Viewer.

* [How to connect to a remote computer using VNC in Linux][63]
* [Ubuntu: Access a remote desktop](https://ubuntu.com/tutorials/access-remote-desktop#1-overview)
* [Remmina: Remote access screen and file sharing to your desktop](https://www.remmina.org/)
* [How to use the screen share feature in Ubuntu][61]
* [Enable remote desktop in xubuntu](https://serverok.in/enable-remote-desktop-in-xubuntu)
* [How to enable Screen Sharing on Ubuntu 20.04 LTS](https://linuxhint.com/enable-screen-sharing-ubuntu/)
* [Enabling Remote Desktop Sharing in Xubuntu](https://softsolder.com/2011/12/18/enabling-remote-desktop-sharing-in-xubuntu/)
* [XXFCE: Remote Desktop via X11vnc Through an SSH Tunnel][56]
* [How to share your desktop in Linux using X11vnc](https://linuxconfig.org/how-to-share-your-desktop-in-linux-using-x11vnc)
* [Ubuntu: How to setup X11vnc to access with graphical login screen?](https://www.youtube.com/watch?v=sXIHAbXcz0Q)

## Screen Sharing on GNOME
I found that setting up a VNC server on Linux can be very tedious and time-consuming
(mainly because there is to many possibilities, inconsistent nomenclature, and incompatibilities).
Ubuntu agree, and as a result, have a “screen sharing” feature,
which can automatically configure and set up a VNC server to share your desktop’s screen.
[Vino][57] was a VNC server for the GNOME desktop environment, capable of screen sharing,
but the GNOME developers now recommend using [gnome-remote-desktop][58] instead.
On the GNOME desktop,
open **Settings**, select **Sharing**, and enable **Remote Desktop**
(see [here][63] for more details).
This should automatically enable the service and you should immediately
be able to connect via the [Remote Desktop Protocol (RDP)][59].
This is a GNOME-only solution intended for the enterprise market.
It appears you can [use other types of desktops][61],
but you must switch to GNOME for the screen sharing features to work.

GNOME also has a recommended solution for for remote access client software,
that being [Remmina][62].
This is also a modern browser implementation but isn't restricted to Ubuntu's screen sharing solution is.

## Screen Sharing via X11vnc & noVNC
[X11vnc][56] is a VNC Server program, but operates differently than most VNC servers.
It it captures the X Window session on the remote by continuously polling the X server's frame buffer for changes.
This approach  allows the user to control the remote X11 desktop (any ... KDE, GNOME, Xfce, etc.)
as if the user were sitting in front of it.
The `x11vnc` server also has built-in SSL/TLS encryption and 2048 bit RSA authentication,
including VeNCrypt support along with the UNIX account and password login system.

A downside of `x11vnc` is its conflict with `gdm3`.
Ubuntu Linux uses the GNOME Desktop Manager (GDM), specifically `gdm3`,
as the default display manager.
Unfortunately, GDM does not usually work very well with the `x11vnc` server.
To overcome this, you will have to install the Light Display Manager, or `lightdm`.

For maximum flexibility, I will use [noVNC][55] for the VNC Viewer.
`novnc` is an open Source VNC client using HTML5 (WebSockets, Canvas),
that runs well in any modern browser, including mobile browsers (iOS and Android).


-------


# X11vnc & noVNC

## Quick & Dirty Demonstration of X11vnc & noVNC
This is not a production ready installation but a quick test
demonstration of X11vnc and noVNC within you local LAN environment.
Manually starting the appropriate process terminals
doing this to validate the installation of the tools needed.

>**NOTE:** By default, ufw may also be setting IPv6 ports.
>To disable IPv6 ports, you must edit the `/etc/default/ufw` file.
>Set `IPV6` to `no` to no longer apply rules to support IPv6
>(`no` means only IPv6 on loopback accepted).
>You will need to `sudo ufw disable` and then `sudo ufw enable`
>for the firewall changes to take affect.
>See ["How to Set Up a Firewall with UFW on Ubuntu 18.04"][68]
>["UFW Essentials: Common Firewall Rules and Commands"][70] for more information.

#### Step 1: Install Software, Configure, and Start X11vnc - DONE
The web article ["XFCE: Remote Desktop via X11vnc Through an SSH Tunnel"][56]
shows how easy this can be done.
I tried it and it works!.
See below for how it was done:

>**NOTE:** Remote Server was my chromebook at IP address `192.168.1.19`
>and the Local Client was my `desktop` at IP address `192.168.1.200`.
>This is opposite to what would normally occur, where is the `desktop` would be the VNC Server.

```bash
# on the remote server, make sure your user (in my case 'jeff') has an running X session on display 0:
# execute the following within a terminal window on the gui
$ echo $DISPLAY
:0.0

# on the remote server, make sure ssh services is active and your local client
# has permission to use ssh access
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere

# on the remote server, install x11vnc
sudo apt install x11vnc

# ------------------------------------------------------------------------------

# on the local client, make sure ssh services is active
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere

# on the local client, install novnc
sudo snap install novnc

# on the local client, within a terminal, create a ssh tunnel to the remote server
# and then start the x11vnc process on the remote server
#ssh -v jeff@192.168.1.19 -L 5900:localhost:5900 "x11vnc -autoport 5900 -shared -display :0 -noxdamage -ncache 10 -ncache_cr -nopw"
ssh -v jeff@192.168.1.19 -L 5900:localhost:5900 "x11vnc -autoport 5900 -shared -display :0 -noxdamage -noncache -nopw"
```

The `x11vnc` [commandline option/parameters][60] used above are:

* **-autoport <n>**
Automatically probe for a free VNC port starting at <n>.
The default is to start probing at 5900.
* **-display <disp>**
X11 server display to connect to, usually :0.
The X server process must be running on same machine and support MIT-SHM.
* **-shared**
VNC display is shared, i.e. more than one viewer can connect at the same time (default off).
* **-forever**
Keep listening for more connections rather than exiting as soon as the first client(s) disconnect.
* **-noxdamage**
Do not use the X DAMAGE extension to detect framebuffer changes even if it is available.
Use -noxdamage if your default is to have it off.
x11vnc's use of the DAMAGE extension:
1) significantly reduces the load when the screen is not changing much,
and 2) detects changed areas (small ones by default) more quickly.
* **-nopw**
Disable the big warning message when you use x11vnc without some sort of password.
* **-passwd <password>**
used for authentication (USE AT YOUR RISK ... might see it via `ps`)
* **-passwdfile <filename>**
Specify the password via the first line of the file <filename>
(instead of via -passwd on the command line where others might see it via `ps`).
* **-noncache**
disable `-ncache` mode
* **-ncache <n>**
Client-side caching scheme for framebuffer memory <n> (an integer) times that of the
full display screen contents for rapid retrieval.
<n> = 10 is the default and use 0 to disable.
* **-ncache_cr**
In `-ncache` mode, try to do copyrect opaque window moves/drags
instead of wireframes (this can induce painting errors).
* **-auth guess**
x11vnc use its `-findauth` mechanism to try to guess the XAUTHORITY filename and use it.
* **-passwd <randompassword>**
* **-passwdfile <filename>**

Sources:

* [XFCE: Remote Desktop via X11vnc Through an SSH Tunnel][56]

#### Step 2: Start noVNC for Screen Sharing or Remote Server - DONE
Now on the local client, within a different terminal,
start the `novnc` VNC client
and go to your browser to see the VNC connection

```bash
# on the local client, check the ports being used by x11vnc
ss -antp | grep vnc

# on the local client, within a different terminal, start the novnc vnc client
$ novnc --listen 6080 --vnc 192.168.1.19:5900
Warning: could not find self.pem
Using installed websockify at /snap/novnc/77/bin/websockify
Starting webserver and WebSockets proxy on port 6080
WebSocket server settings:
  - Listen on :6080
  - Web server. Web root: /snap/novnc/77
  - No SSL/TLS support (no cert file)
  - proxying from :6080 to localhost:5900


Navigate to this URL:

    http://desktop:6080/vnc.html?host=desktop&port=6080

Press Ctrl-C to exit

# on the local client, bring up the screen sharing of the remote server
# via a browser using the url provide above
google-chrome http://desktop:6080/vnc.html?host=desktop&port=6080
```

**Important**:
When your done, make sure to kill the `x11vnc` process.
It is likely to continue to run once you kill the `ssh` tunnel created on the remote server.

```bash
# on the remote server, check if the x11vnc process is still running
$ ps uax | grep x11vnc
jeff        3365  0.4  0.4 139628 18708 ?        Ss   21:19   0:00 x11vnc -autoport 5900 -shared -display :0 -noxdamage -ncache 10 -ncache_cr -nopw
jeff        3435  0.0  0.0  19480  2224 pts/3    R+   21:20   0:00 grep --color=auto x11vnc

# kill the x11vnc process
kill 3365
```

------


## Production Ready Method for X11vnc & noVNC
Unlike the demonstration above,
this is intended to be a permanent installation so that my desktop Linux environment, `desktop`,
can act as a remote server.
The prerequisites for this method is:

* Remote Server - A machine (example is for Ubuntu) with a non-root user with `sudo` privileges.
Also need to use `lightdm` for its display manager (can't use the `gdm3`, GNOME display manager 3).
* Local Client - Any Linux machine having `vnc` client.

>**NOTE:** In my permanent installation done in this section,
>Remote Server = `desktop` and Local Client = `chromebook`.
>This is the direct opposite of the
>"Quick & Dirty Demonstration of X11vnc & noVNC" done above.

[Ubuntu: How to setup x11vnc to access with graphical login screen?](https://www.youtube.com/watch?v=sXIHAbXcz0Q)
[How can I set up x11vnc to start on boot, with lightdm?](https://unix.stackexchange.com/questions/653221/how-can-i-set-up-x11vnc-to-start-on-boot-with-lightdm)
[VNC Server with GDM login](https://unix.stackexchange.com/questions/644886/vnc-server-with-gdm-login)
[How to Setup x11vnc on Ubuntu 22.04](https://linuxopsys.com/topics/setup-x11vnc-on-ubuntu)

#### Step 1: Install Software and Configure X11vnc - DONE
First, we want to setup the firewall rules to support the VNC server.
In a typical installation, VNC service request will be coming into ports `5901` thru `5910`.

```bash
# on the remove server, make sure your user (in my case 'jeff') has an running X session on display 0:
# execute the following within a terminal window on the gui
$ echo $DISPLAY
:0.0

# check whether the ufw firewall running, and if not active, then enable it
sudo ufw status verbose
sudo ufw enable

# make sure to configure the default rules to deny all inbound and permit all outbound
sudo ufw default deny incoming
sudo ufw default allow outgoing

# need to open ports for incoming vnc connections
# if you plan to support only one connection then one port is enough, typically this is port 5900
#sudo ufw allow 5900:5910/tcp comment 'allow vnc in-coming connections on port 5900 thru 5910'
sudo ufw allow 5900/tcp comment 'allow in-coming vnc connections'

# on the remote server, make sure ssh services is active and your local client
# has permission to use ssh access, and vnc in-coming ports are open
$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
80/tcp (Apache)            ALLOW IN    Anywhere
52050                      ALLOW IN    Anywhere
52051                      ALLOW IN    Anywhere
3232/tcp                   ALLOW IN    Anywhere
22/tcp (OpenSSH)           ALLOW IN    Anywhere
5900/tcp                   ALLOW IN    Anywhere                   # allow in-coming vnc connections

# load any changes made to firewall
sudo ufw reload
sudo ufw status verbose
```

On the remote server, also need to change the display manager, typically `gdm3`, to `lightdm`,
since it conflicts with X11vnc.
Also, need to install the X11vnc package.

```bash
# on the remove server, find out what display manager are you using
$ cat /etc/X11/default-display-manager
/usr/sbin/gdm3

# if display manager is 'gdm3', change the display manager over to lightdm
sudo apt install lightdm

# on the remote server, install x11vnc
sudo apt install x11vnc

# reboot to get the display manager working
sudo reboot
```

>**NOTE:** By default, ufw may also be setting IPv6 ports.
>To disable IPv6 ports, you must edit the `/etc/default/ufw` file.
>Set `IPV6` to `no` to no longer apply rules to support IPv6
>(`no` means only IPv6 on loopback accepted).
>You will need to `sudo ufw disable` and then `sudo ufw enable`
>for the firewall changes to take affect.
>See ["How to Set Up a Firewall with UFW on Ubuntu 18.04"][68]
>["UFW Essentials: Common Firewall Rules and Commands"][70] for more information.

#### Step 2: Install noVNC Software - DONE
Now on the local client, install the noVNC software
you will use to access the remote server via VNC:

```bash
# on the local client, install novnc
sudo snap install novnc
```

#### Step 3: Test the Configuration Manually - DONE
Before we move to the next step,
lets manually test this configuration so far:

```bash
# on the remote server, execute this command in a terminal
#x11vnc -forever -shared -autoport 5900 -display :0 -auth guess -passwd randompassword -noxdamage -ncache 10 -ncache_cr -nopw
#x11vnc -forever -shared -autoport 5900 -display :0 -auth guess -noxdamage -ncache 10 -ncache_cr -nopw
x11vnc -forever -shared -autoport 5900 -display :0 -auth guess -noxdamage -noncache -nopw

# on the remote server, and in another terminal, check the ports being used by x11vnc
ss -antp | grep vnc

# on the local client, execute this command in a terminal
$ novnc --listen 6080 --vnc 192.168.1.200:5900
```

You should now be able to see the remote server GUI via
`google-chrome http://desktop:6080/vnc.html?host=desktop&port=6080`.

#### Step 4: Configure X11vnc Within systemd - DONE
We need to create the appropriate files so [`systemd`][71] can manage X11vnc.
To make this happen, on the remove server, create the file
`/lib/systemd/system/x11vnc.service` with the following content:

```
[Unit]
Description=x11vnc service
After=display-manager.service network.target syslog.target

[Service]
Type=simple
ExecStart=/usr/bin/x11vnc -forever -shared -autoport 5900 -display :0 -auth guess -noxdamage -noncache -nopw
ExecStop=/usr/bin/killall x11vnc
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

This configuration file instructing `systemd` to:

* start after some other services (system logging, network interfaces, and display manager) have been started
* no forking as the `x11vnc` creates a child process from the `-forever` clause.
* the `ExecStart` and `ExecStop` commands say what to do when starting and stopping
* we want it to be restarted on failure,
* we also want this service to be started before the process reaches the multi-user target.

We are now going to start up the VNC service

```bash
# tell the systemd system there is a change and to reload
sudo systemctl daemon-reload

# start the VNC service
sudo systemctl start x11vnc.service

# check the VNC status
sudo systemctl status x11vnc.service

# enable the VNC service so it starts automatically after the system reboot
sudo systemctl enable x11vnc.service
```

Now go to your local client and execute:

```bash
# on the local client, execute this command in a terminal
$ novnc --listen 6080 --vnc 192.168.1.200:5900
```

As a further test, `reboot` to make sure everything loads properly.

Below are a few more `systemctl` commands that could prove useful:

```bash
# check the vnc server status
systemctl status x11vnc.service

# to start vnc server now
sudo systemctl start x11vnc.service

# to start vnc server at next boot, and every subsequent boot
sudo systemctl enable x11vnc.service

# to stop vnc server
sudo systemctl stop x11vnc.service

# to prevent vnc server starting at boot
sudo systemctl disable x11vnc.service
```

Sources:

* [X11vnc Manual Page][60]
* [X11vnc](https://wiki.archlinux.org/title/x11vnc)
* [How to Setup x11vnc on Ubuntu 22.04](https://linuxopsys.com/topics/setup-x11vnc-on-ubuntu)
* [ArchLinux: X11vnc](https://wiki.archlinux.org/title/x11vnc)
* [How to Install and Run a VNC Server on Ubuntu Linux][67]
* [How to install x11vnc vnc server as a service on Ubuntu 20.04, for remote access or screen sharing][64]
    * [How to install x11vnc vnc server on ubuntu 20.04, for remote access or screen sharing](https://www.youtube.com/watch?v=bLGLwGToFCg)
    * [How to stop x11vnc vnc server on ubuntu 20.04 crashing, for remote access or screen sharing](https://www.youtube.com/watch?v=-jAiRyBLTPM)
* [Understanding Systemd Units and Unit Files](https://www.digitalocean.com/community/tutorials/understanding-systemd-units-and-unit-files)

#### Step 5: (Optional) Disable Suspend / Hibernation Modes - NOT DONE
If you are sure the remote computer is connected to the Internet but you see something like:
_VNC Server is not currently listening for Cloud connections_
... when attempting to connect,
then it may be that the remote VNC Server computer is suspended or hibernating.

>What's the difference between sleep, suspend, and hibernate?
>
>* **Sleep** (sometimes called "Standby" or “turn off display”) typically means that your computer
>and/or monitor are put into an idle, low power state.
>Depending on your operating system, sleep is sometimes used interchangeably with suspend,
>as is the case in Ubuntu based systems.
>* **Suspend** saves its current state to your RAM and puts the computer
>and all peripherals on a low power consumption mode.
>If the battery runs out or the computer turns off for some reason,
>the current session and unsaved changes will be lost.
>* **Hibernate** (sometimes called "suspend to disk"),
>it will save its current state to the hard disk and power down completely.
>When resuming, the saved state is restored to RAM.

When you suspend your Linux system,
the system is into sleep mode.
The screen goes off, but the computer remains very much powered on.
Getting back to using your system requires a simple mouse-click
or a tap on any keyboard button.
Sometimes, you may be required to press the power button.
But these actions may not work via VNC.

To prevent your Linux system from suspending or going into hibernation,
you need to disable the following [`systemd`][71] targets:

```bash
# check the status of sleep / hybrid-sleep / suspend features
sudo systemctl status sleep.target suspend.target hibernate.target hybrid-sleep.target

# prevent the system going into suspend / hibernate mode
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target

# apply the configuration changes
sudo systemctl daemon-reload
# OR maybe better
sudo reboot

# verify if the changes have been effected
sudo systemctl status sleep.target suspend.target hibernate.target hybrid-sleep.target
```

If you wish to test for what X11vnc will do when Ubuntu is in the suspend or hibernate state,
use these commandline tools: `systemctl suspend` and `systemctl hibernate`.

If you wish to re-enable the suspend / hibernation mode:

```bash
# re-enable the suspend / hibernation mode
sudo systemctl unmask sleep.target suspend.target hibernate.target hybrid-sleep.target

# apply the configuration changes and restart
sudo systemctl daemon-reload
sudo reboot
```

These changes do not prevent the system from going into suspend state upon closing a laptops lid,
nor prevents it from invoking the screen-saver.

Source:

* [Why is VNC Server not currently listening for Cloud connections?](https://help.realvnc.com/hc/en-us/articles/360003474692-Why-is-VNC-Server-not-currently-listening-for-Cloud-connections-)
* [How to Disable Suspend and Hibernation Modes In Linux](https://www.tecmint.com/disable-suspend-and-hibernation-in-linux/)
* [Linux Command: Put Laptop / Netbook In Hibernate / Suspend Mode](https://www.cyberciti.biz/faq/linux-command-to-suspend-hibernate-laptop-netbook-pc)

#### Step 6: Remove GNOME Screen Lock - DONE
There is a conflict with the GNOME screen lock, such that,
you will not be able to VNC after the screen locks.
You'll need to [turn-off the GNOME screen lock][64],
and [replace it with `xscreensaver`][65] (assuming you wish to continue screen locking).

We will now install the `xscreensaver` utility,
automatically enable it at startup,
and use it to set screen-savers on your system depending on your specific requirements.

```bash
# check out the version of gnome you are running
$ gnome-shell --version
GNOME Shell 42.5

# install xscreensaver packages
sudo apt install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra

# verify the installation
xscreensaver -help

# remove the default gnome screen-saver
sudo apt remove gnome-screensaver

# for gnome screen-saver to be removed completely, you need to restart your system
sudo reboot
```

#### Step 7: Setup the XScreensaver - DONE
Open the [Startup Applications][69] utility either by locating it in the Applications list
or simply by searching for it through the system Application Launcher
or executing `gnome-session-properties` in a terminal.

```bash
# enter startup application preferences
gnome-session-properties
```

In the **Add Startup Program** dialog,
enter the following information:
**Name:** `Screensaver`,
**Command:** `xscreensaver -nosplash`,
**Comment:** `start screensaver app at startup (GNOME screensaver disabled)`
Now click **Add**.

Every time you boot the system,
this startup program will start running the Xscreensaver utility
so that your screen-saver becomes active the way you have configured it.
The `nosplash` flag mean that the application would run without the UI being displayed.

#### Step 8: Configure the XScreensaver - DONE
In order to configure the screen-saver through the Xscreensaver utility,
open the application either through the Application Launcher
or via commandline:

```bash
# bring up xscreensave configuration menu
xscreensaver

# test xscreensave and it lock
xscreensaver-command --lock=
```

If for any reason, you want to remove the Xscreensaver utility
and switch back to the default Gnome screen-saver application:

```bash
# remove xscreensaver
sudo apt-get remove xscreensaver xscreensaver-gl-extra xscreensaver-data-extra

# re-install gnome screensaver
sudo apt install gnome-screensaver
```

The remove Xscreensaver app from your Startup Applications.
You do not need to add the Gnome Screen-saver to your system startup as the application
is meant to automatically run at all times.
You can verify this by running via the command `gnome-screensaver`.

Source:

* [How to replace Gnome Screensaver with Xscreensaver on Ubuntu](https://vitux.com/how-to-replace-gnome-screensaver-with-xscreensaver-on-ubuntu/)
* [How To Install Or Change Screensaver in Ubuntu?][65]
* [XScreenSaver](https://wiki.archlinux.org/title/XScreenSaver)
* [How to Install and Autostart XScreenSaver on Ubuntu 18.04, Ubuntu 19.04](https://www.linuxbabe.com/ubuntu/install-autostart-xscreensaver-ubuntu-18-04-19-04)

#### Step X: Turn Display Off
* [Keyboard Shortcut to Turn Display Off in Linux](https://www.putorius.net/keyboard-shortcut-turning-display-off-linux.html)
* [How to Turn Off Monitor Using Command-line in Ubuntu 20.04](https://brightwhiz.com/turn-off-monitor-ubuntu-20-04/)

```bash
# make the screen go to black, hit any key to restore
sleep 1 && sset -display :0.0 dpms force off
```


------


# Securing VNC Remote Access With Guacamole
**Issue:** Incorrect VNC sessions screen size - https://leo.leung.xyz/wiki/Guacamole

I encountered an issue with x11vnc where the screen size is about 10-15 times taller than it should be. The contents of the extraneous areas appear to be bits and pieces of other windows and overlays. The cause of this was that x11vnc was started with the ncache option which is used to expand the framebuffer for caching windows and window contents. This however requires a VNC client that supports this option which Guacamole's proxy (`guacd`) doesn't seem to support.

To fix this issue, re-run x11vnc with the `-noncache` option.

**But I could not get the above to work.**  I had to do the following

Review the documentation at https://guacamole.apache.org/doc/gug/using-guacamole.html.
`Alt` + `Ctrl` + `Shift` is used to bring up or hide the Guacamole menu sidebar.


------


# Set-up VNC on the Chromebook

#### Step 1: Install VNC Server Using Tasksel - DONE
The Ubuntu `apt` repositories contains TigerVNC server package (among others).
You can install it by just running the following command:

```bash
# install tigervnc
sudo apt install tigervnc-standalone-server tigervnc-common tigervnc-xorg-extension tigervnc-viewer
```

With TigerVNC installed,
you are required to set a VNC password to access your desktops.
Switch to the non-root user and set a VNC password.
In my case, the user is "jeff", my current login (no view-only password):

```bash
# create a vnc login
$ vncpasswd
You will require a password to access your desktops.
Password:<enter-your-password>
Verify: <re-enter-your-password>
Would you like to enter a view-only password (y/n)? n
```

Now lets start TigerVNC to validate it installation:

```bash
# start tigervnc
$ vncserver -localhost no
#OR
$ tigervncserver -localhost no

# verify if the tigervnc service is running
$ vncserver -list
```

Now the TigerVNC Server is running on the Chromebook providing a GUI login experience
to anyone with a VNC Viewer and the password.
We'll try this out in a following step via the command:
`xtigervncviewer -SecurityTypes VncAuth,TLSVnc -passwd /home/jeff/.vnc/passwd chromebook:1`.

So we can do further VNC configuration, we need to kill the VNC Server via:

```bash
# stop the tigervnc server running on display 1
$ vncserver -kill :1
Killing Xtigervnc process ID 1452... success!
```

Sources:

* [Install VNC on Ubuntu 20.04 using Tasksel/TigerVNC](https://lemehost.com/forum/topic/2460/install+vnc+on+ubuntu+20+04+using+taskseltigervnc)
* [How To Install and Configure VNC Server on Ubuntu 18.04](https://tecadmin.net/how-to-install-and-configure-vnc-on-ubuntu-18-04/)
* [Install and Configure TigerVNC VNC Server on Debian 11/10][35]

#### Step 2: Configure TigerVNC Server - DONE
While the VNC Server not running (terminate via `vncserver -kill :1`),
we are going to make some configuration changes to TigerVNC start script.

```bash
# make backup of vnc startup file
mv ~/.vnc/xstartup ~/.vnc/xstartup.bak
```

Now we are going to create a new `~/.vnc/xstartup` file for VNC.
The file should contain the following:

```bash
#!/bin/sh

## if using the gnome desktop environment
#xrdb $HOME/.Xresources
#vncconfig -iconic &
#dbus-launch --exit-with-session gnome-session &

# if using xfce4 desktop environment
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#xrdb $HOME/.Xresources
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
xsetroot -solid gray
exec startxfce4
exec xfwm4
```

>**NOTE:** Ubuntu 20.04 doesn't make use of the `/etc/vnc/xstartup` file.

Now Make the `~/.vnc/xstartup` file executable:

```bash
sudo chmod u+x  ~/.vnc/xstartup
sudo chmod 777 ~/.vnc/xstartup
```

#### Step 3: Connect to a VNC Server ... Securely - DONE
By default, VNC does not use secure protocols when connecting.
In my case, since I will be using VNC within [Guacamole][38],
a SSH tunnel will be provided by Guacamole.

At this time, I want to make a secure VNC connection without using Guacamole,
using [SSH Tunneling][39] as outline in the web articles below under "Sources".
I will test the VNC server locally on my LAN.
I will install a VNC client (aka VNC viewer) on another system
and use VNC to connect with my Chromebook.
I'll put the VNC client on my Linux desktop system using
(This is for the [TigerViewer][37].  Others are available, such as [RealVNC client][36]):

Strictly speaking, I really don't need to create the SSH Tunnel since all
my testing will be taking place within my private LAN.
Never the less, it is good practice and a absolute must for going outside my LAN.

First, you must install & configure for your SSH Tunnel on the Local Client (aka Linux desktop),
and then start the VNC server on the Remote Server (aka Chromebook).

##### Step 3A: On the Remote Server (aka Chromebook) - DONE
Now on the Remote Server, do the following:

```bash
# check if openssh-server is installed
sudo apt list --installed | grep openssh-server

# if the above test show it absent, install openssh-server
sudo apt install openssh-server

# so that vnc traffic isn't blocked, open ssh port for request from the vnc viewer machine
sudo ufw enable
sudo ufw allow from 192.168.1.200 to any port 22 proto tcp
sudo ufw reload
sudo ufw status

# get the IP address of the remote server machine (needed later)
$ ip route get 8.8.8.8 | awk '{print $7; exit}'
192.168.1.19

# start the vnc server on the remote server (i.e. chromebook)
vncserver :1 -localhost -geometry 1028x720 -depth 32
#OR
vncserver -localhost no

# verify if the tigervnc service is running
$ vncserver -list
```

>**NOTE:** To stop the `vncserver`, identify the display you wish to kill and
>execute the following command: `vncserver -kill :1` (where `:1` is the target display number).

##### Step 3B: Now on the Local Client (aka Linux desktop) - DONE
On the Local Client, install the viewer software, validate that SSH is working,
start a SSH Tunnel session, and then start the VNC Viewer:

```bash
# from local client, test you can reach the remote server machine via ssh
ssh jeff@192.168.1.19

# install tigervnc viewer (aka tigervnc client)
sudo apt install tigervnc-viewer
```

Still on the Local Client,
we'll need an SSH tunnel between the Local Client and the Remote Server.
This tunnel must connect the VNC session on port `5901` using display `:1`
(rule is display <#> is on port 5900 + <#>. In our case `:1` is on port 5900 + 1 = `5901`.)

>**NOTE:** 5901 is what you would use if your VNC session number was 1.
>If your session number is 12, you would use 5912 instead.
>`jeff` should be replaced by your username,
>and `192.168.1.19` should be replaced by your server name (or IP address) where you wish to VNC into.
>You should not need a password.
>Once you are logged in, you should see a command prompt. **Leave this window open.**
>As long as it is open, you should have an active SSH tunnel.

Lets create the SSH Tunnel initiated on Local Client (aka Linux desktop)
and terminated on the Remote Server (aka Chromebook):


```bash
# create ssh tunnel between local client and remote server
# format:  ssh -L <port>:<Local Client>:<port> <User Name>@<Remote Server>
ssh -L 5901:localhost:5901 jeff@192.168.1.19
# OR
ssh -N -T -C -L 5901:localhost:5901 -l jeff 192.168.1.19
```

The following options are used to create a tunnel:

* **-N -** specifies to only forward ports, not execute the command
* **-T -** disables pseudo-tty allocation
* **-C -** This flag enables compression which can help minimize resource consumption and speed things up
* **-L -** forwarding information from local port 5901 (first port is a local port) to remote port 5901 via SSH tunnel
* **-l -** specify the user you want to log in as once you connect to the server

With the tunnel running on one terminal window on the Local Client,
open another terminal window in the Local Client and enter the following:

```bash
# launch the vnc viewer
vncviewer                # you must manually supply a password
# OR
vncviewer localhost:1    # you must manually supply a password
# OR
vncviewer -SecurityTypes VncAuth,TLSVnc -passwd /home/jeff/.vnc/passwd localhost:1
# OR
xtigervncviewer -SecurityTypes VncAuth,TLSVnc -passwd /home/jeff/.vnc/passwd localhost:1
# OR
vncviewer -via jeff@192.168.1.19 localhost:1
```

At this point,
you should see the VNC session of the Remote Server running in a window on the Local Client.
Within that window you will, see a full GUI session (desktop and window manager),
just like you would see sitting at the physical screen.

Sources:
* [Install and Configure TigerVNC VNC Server on Debian 11/10][35]
* [Remote Desktop (VNC) with SSH Tunnel](https://sscf.ucsd.edu/self-help-guides/tutorials/linux/vnc-with-ssh-tunnel)
* [Connecting to a remote GUI using VNC over an SSH tunnel](http://www.allgoodbits.org/articles/view/58)
* [How to Install and Configure VNC on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04)

#### Step 4: Configure VNC to Start at Boot Time
The VNC server software we are using does not have a `systemctl` compatible service,
so we will need to write our own.
To create our service file,
create the file `/etc/systemd/system/vncserver@.service` with the following contents:

```
[Unit]
Description=TigerVNC Remote Desktop Server
After=syslog.target network.target

[Service]
Type=simple
User=user1
PAMName=login
PIDFile=/home/%u/.vnc/%H%i.pid
ExecStartPre=/usr/bin/vncserver -kill :%i > /dev/null 2>&1 || :
ExecStart=/usr/bin/vncserver :%i -localhost no -geometry 1028x720
ExecStop=/usr/bin/vncserver -kill :%i

[Install]
WantedBy=multi-user.target
```

These lines tell the service manager how to handle the VNC server

* start the VNC server software after the network has become available.
* VNC server available at the location, /`usr/bin/vncserver`.
* use the `:1` virtual display
* to shutting down, use the `-kill` argument to stop the virtual desktop.

We are now going to start up the VNC service, specifically for display `:1`
(that is why you see the reference to `@1` in `vncserver@1.service`):

```bash
# apply the configuration changes
systemctl daemon-reload

#start the VNC service
systemctl start vncserver@1.service

# enable the VNC service so it starts automatically after the system reboot
systemctl enable vncserver@1.service

# check the VNC status
systemctl status vncserver@1.service
```

We can now test to see if our new VNC service is working by running the following command to start it.

```bash
# to start vnc server now
sudo systemctl start vncserver@1.service

# check the vnc server status
systemctl status vncserver@1.service

# to start vnc server at next boot, and every subsequent boot
sudo systemctl enable vncserver@1.service

# to stop vnc server
sudo systemctl stop vncserver@1.service

# to prevent vnc server starting at boot
sudo systemctl disable vncserver@1.service
```

Sources
* [How to Enable Remote Desktop Ubuntu using VNC (Step by Step Tutorial)](https://cloudinfrastructureservices.co.uk/how-to-enable-remote-desktop-ubuntu-using-vnc-step-by-step-tutorial/)
* [Running VNC on Ubuntu 20.04 with default window manager](https://www.nodinrogers.com/post/2021-11-15-connecting-to-ubuntu-via-vnc-default-wm/)
* [Setting Up VNC Session](https://docs.uabgrid.uab.edu/wiki/Setting_Up_VNC_Session)
* [How to Install and Configure VNC Server on Ubuntu](https://www.tecmint.com/install-and-configure-vnc-server-on-ubuntu/)
* [How To Install and Configure VNC Server on Ubuntu 18.04](https://tecadmin.net/how-to-install-and-configure-vnc-on-ubuntu-18-04/)


-------


#### Step X: How Switch GUI Boot Target
Sources:

* [How to switch boot target to text or GUI in systemd Linux](https://www.cyberciti.biz/faq/switch-boot-target-to-text-gui-in-systemd-linux/)
* [Installing and Using Tasksel on Ubuntu 20.04](https://support.shells.net/hc/en-us/articles/1500003387442-Installing-and-Using-Tasksel-on-Ubuntu-20-04)






**Select a Display Manager**
When installing Display Manager, the system is going to ask for a default display manager because only one can run at a time, although you can have several installed.

```bash
# make sure your system is running with the latest packages
sudo apt update && sudo apt upgrade

# install display manager
sudo apt-get install lightdm

# start the display manager and load the GUI
sudo service lightdm start

# verify the default display manager
$ cat /etc/X11/default-display-manager
/usr/bin/lightdm
```

## How to Switch Boot Target
* [How to switch boot target to text or GUI in systemd Linux](https://www.cyberciti.biz/faq/switch-boot-target-to-text-gui-in-systemd-linux/)
* [Tasksel – Easily and Quickly Install Group Softwares in Debian and Ubuntu](https://www.tecmint.com/tasksel-install-group-software-lamp-mail-dns-in-debian-ubuntu/)

**Switching boot target to text**
The procedure is as follows to change into a text mode runlevel under `systemd`:

Open the terminal application.
For remote Linux servers, use the ssh command.
Find which target unit is used by default:
systemctl get-default

To change boot target to the text mode:
sudo systemctl set-default multi-user.target

Check the boot target
systemctl get-default

Reboot the system using the reboot command:
sudo systemctl reboot

**switch boot target to GUI**
Want to revert change boot to GUI instead of console/text mode? Try:

Open the Linux terminal application.
Again, for remote Linux servers, use the ssh command.
Find which target unit is used by default:
systemctl get-default

To change boot target to the GUI mode:
sudo systemctl set-default graphical.target

Check the boot target
systemctl get-default

Make sure you reboot the Linux box using the reboot command:
sudo reboot

**How to boot in to rescue mode**
Run the following systemctl command
sudo systemctl rescue

We can change to a different systemd target unit in the current log in session using the CLI as follows:
sudo systemctl isolate multi-user.target
# OR #
sudo systemctl isolate graphical.target

## Add Your Tools
```bash
# copy repositories for
.vim, .bash, .X, ...

# install needed tools
apt install vim vim-gtk3
```

## To Remove GUI from Ubuntu Server
If you realize that the desktop environment is taking too much computing resources, you may remove the packages you installed previously.
Please keep in mind that it may cause dependency issues in some cases so please make a backup of your important data or create a system snapshot.

```bash
# if you want to shutdown the GUI open a terminal window
sudo service ubuntu-desktop stop
sudo apt remove ubuntu-desktop
sudo apt remove lightdm
sudo apt autoremove
sudo service lightdm stop

# removing orphaned or unnecessary dependencies
sudo apt autoremove
```


## Start GUI from command line
sudo systemctl isolate graphical

## Connecting to Raspberry Pi via VNC
Appears the Raspberry Pi community has settled on RealVNC as their goto platform for VNC Server.

* [Connecting to your Raspberry Pi via VNC](https://raspberrypi-guide.github.io/networking/connecting-via-VNC)
* [VNC Connect and Raspberry Pi](https://help.realvnc.com/hc/en-us/articles/360002249917-VNC-Connect-and-Raspberry-Pi)
* [Setting up a VNC Server on the Raspberry Pi](https://pimylifeup.com/raspberry-pi-vnc-server/)
* [How to Use Remote Desktop on the Raspberry Pi with VNC](https://learn.sparkfun.com/tutorials/how-to-use-remote-desktop-on-the-raspberry-pi-with-vnc/enable-vnc)
* [Adafruit's Raspberry Pi Lesson 7. Remote Control with VNC](https://learn.adafruit.com/adafruit-raspberry-pi-lesson-7-remote-control-with-vnc)



[35]:https://computingforgeeks.com/install-and-configure-tigervnc-vnc-server-on-debian/
[36]:https://www.realvnc.com/en/connect/download/viewer/linux/
[37]:https://zoomadmin.com/HowToInstall/UbuntuPackage/tigervnc-viewer
[38]:https://guacamole.apache.org/
[39]:https://www.ssh.com/academy/ssh/tunneling
[40]:https://www.lifewire.com/vnc-free-software-downloads-818116
[41]:https://fixthephoto.com/best-vnc-software.html
[42]:https://en.wikipedia.org/wiki/Framebuffer
[43]:https://nims11.wordpress.com/2012/06/24/nested-x-servers-with-xephyr/
[44]:http://jeffskinnerbox.me/posts/2014/Apr/29/howto-using-xephyr-to-create-a-new-display-in-a-window/
[45]:https://www.realvnc.com/en/
[46]:https://www.raspberrypi.org/documentation/remote-access/vnc/
[47]:https://www.lifewire.com/vnc-free-software-downloads-818116
[48]:https://www.lifewire.com/vnc-virtual-network-computing-818104
[49]:https://www.tightvnc.com/
[50]:https://www.techradar.com/news/5-of-the-best-linux-remote-desktop-clients
[51]:https://tigervnc.org/
[52]:https://en.wikipedia.org/wiki/Remote_Desktop_Protocol
[53]:https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units
[54]:http://www.karlrunge.com/x11vnc/
[55]:https://novnc.com/info.html
[56]:https://en.wikipedia.org/wiki/X11vnc
[56]:https://softsolder.com/2022/01/03/xfce-remote-desktop-via-x11vnc-through-an-ssh-tunnel/
[57]:https://wiki.gnome.org/Projects/Vino
[58]:https://wiki.gnome.org/Projects/Mutter/RemoteDesktop
[59]:https://en.wikipedia.org/wiki/Remote_Desktop_Protocol
[60]:https://manpages.ubuntu.com/manpages/kinetic/man1/x11vnc.1.html
[61]:https://www.addictivetips.com/ubuntu-linux-tips/use-screen-share-in-ubuntu/
[62]:https://ubuntu.com/tutorials/access-remote-desktop#1-overview
[63]:https://www.redhat.com/sysadmin/vnc-screen-sharing-linux
[64]:https://www.crazy-logic.co.uk/projects/computing/how-to-install-x11vnc-vnc-server-as-a-service-on-ubuntu-20-04-for-remote-access-or-screen-sharing
[65]:(https://wethegeek.com/how-to-install-or-change-screensaver-in-ubuntu/)
[66]:https://askubuntu.com/questions/432255/what-is-the-display-environment-variable
[67]:https://www.makeuseof.com/install-ubuntu-vnc-server-linux/
[68]:https://www.letscloud.io/community/how-to-set-up-a-firewall-with-ufw-on-ubuntu-1804
[69]:https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en
[70]:https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands
[71]:https://opensource.com/downloads/pragmatic-guide-systemd-linux

