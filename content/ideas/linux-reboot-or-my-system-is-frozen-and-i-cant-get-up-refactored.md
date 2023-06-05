<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----






# Display Server Freeze
[Gnome Shell, aka `gnome-shell`][25], (GNOME is acronym for GNU Network Object Model Environment)
provides core interface functions like switching windows,
launching applications, see your notifications, change the icon, themes, fonts, etc.
And if your running the GNOME desktop environment,
you can also use it to help recover from a frozen display server.
Gnome Shell has a built-in restart function that users can execute
to restart a frozen desktop while in use quickly.

>**NOTE:**
>But there is a catch for using `gnome-shell` ... it doesn’t work with the new Wayland display protocol
>so you need to be using Xorg for this to work.
>See [here][28] for Wayland fixes for frozen display server.

For this to work, you must first check if your running [Xorg protocol][26]
and **not** the [Wayland protocol][27]:

```bash
# check if you are running wayland or xorg display server protocols
# wayland is the default display server
$ env | grep -i XDG_SESSION_TYPE
XDG_SESSION_TYPE=x11
```

Get a terminal outside of your desktop environment so you can get commandline access.
You can do this via Pressing `Ctrl`+`Alt`+`F3`.
Then enter the [following command to restart][29] the Gnome desktop environment:

>**NOTE:** This will kill any runing applications, fully reloads the desktop environment,
>and you will have to log in again from scratch.

```bash
# restart the gnome desktop environment
#sudo gnome-shell --replace      # old method
sudo pkill -SIGQUIT gnome-shell

# if the above doesn't work, try restarting the display manager
sudo systemctl restart gdm
```

Press `Ctrl`+`Alt`+`F2` to move back to the desktop and,
after a short wait and if everything goes according to the plan,
a refreshed version of your desktop will started.



[25]:https://wiki.gnome.org/Projects/GnomeShell
[26]:https://www.x.org/wiki/
[27]:https://wayland.freedesktop.org/
[28]:https://www.addictivetips.com/ubuntu-linux-tips/fix-frozen-gnome-desktop-session/
[29]:https://askubuntu.com/questions/100226/how-to-restart-gnome-shell-from-command-line







<a href="/home/jeff/blogging/content/images/sysrq-key.jpg">
    <img class="img-rounded" style="margin: 0px 8px; float: left" alt="sysrq-key" src="/images/sysrq-key.jpg" width="300" height="199" />
</a>
While I was building the environment for my Linux box, I ran into some problems with Ubuntu.
I found myself with frozen screens or booted up into blank screens and other such things.
Seems that Ubuntu 13.04 is currently a bit unstable or I just screwed things up badly ... a little of both I suspect.
I managed to get through these problems, but too often I got desperate
and I hitting the on/off switch to get the box rebooted.
Doing this can result in corrupted files and other such nasty things.
So this motivated me to research the "correct" way to get out of these Linux near death experiences.

The golden nugget here is actually at the end of this posting, that is the Magic SysRq Key.
This gem can get you out of most any freeze but I provide more here since the alternatives might be less intrusive.

## Stopping a Running Process
While this post's focus is on how to reboot Linux,
keep in mind that sometimes the problem that your attempting to solve may be handled via a simpler approach.
Specifically, maybe you just need to kill a running process.

In the Bash shell, you can use job control:

* `Ctrl+C` – halts the current command
* `Ctrl+Z` – stops the current command, resume with fg in the foreground or bg in the background
* `Ctrl+D` – log out of current session, similar to exit

On a Desktop version of Linux, there are normally six text consoles sessions available and one graphics session.
You could leave a frozen GUI, and go to a console screen to kill an offending process:

* You can access the consoles by pressing `CTRL + ALT + Fx`
(where `Fx` is a function key on the keyboard from `F1` to `F6`).
* Once you enter one of the consoles, you will be prompted for user name and password.
Enter them and then you’ll reach a command prompt.
Now you can kill the offending process using the `kill` command.
* To switch back to the graphic session, just click `CTRL + ALT + F7`.

The process "killing" could be done via the recommended `kill -SIGTERM <pid>`
the more forceful `kill -SIGKILL <pid>`.
There are also versions of these tools, [`killall` and `pkill`][03],
that use the name of the process as an argument instead of the process ID.
`xkill` is a utility for forcing the X server to close connections to clients,
closing an X application that has become unresponsive, or misbehaving in general.
To use it, execute `xkill`, and once it's running,
you simply click on the window you wish to kill, and it performs a `kill -9`.

## When Kill -9 Does Not Work
You are supposed to be able to kill any process with `kill -9 pid`,
but you may come across a process that just will not die.
Usually this happens when you are trying to kill a
[zombie process or defunct process][04].
These are processes that are dead and have exited,
but they remain as [zombies in the process list][05].
The kernel keeps them in the process list until the parent process
retrieves the exit status code by calling the `wait()` system call.
This does not usually happen with daemon processes because
they detach themselves from their parent process
and are adopted by the `init` process (PID=1) which will
automatically call `wait()` to clear them out of the process list.

You may sometimes see the daemon defunct PID in the process list for a brief moment
before it gets cleaned up by the `init` process.
You don't have to worry about these.
You can also end up with an unkillable process if a process is stuck waiting for the kernel to finish something.
This usually happens when the kernel is waiting for I/O.
Where you see this most often is with network filesystems,
such as NFS and SaMBa, that have disconnected uncleanly.
This also happens when a drive fails or if someone unplugs a cable to a mounted drive.
If the device had a memmapped file or was used for swap then you may be really screwed.
Any kernel calls that flush IO may hang forever waiting for the device to respond.

You can be identify **zombie** processes in the output from the process status command
`ps` by the presence of a "Z" in the "STAT" column.
Zombies that exist for more than a short period of time typically indicate a bug in the parent program,
or just an uncommon decision to reap children.
An **orphan** process is not the same as a zombie process.
An orphan process is a process that is still executing, but whose parent has died.
They do not become zombie processes;
instead, they are adopted by `init` (process ID 1), which waits on its children.

## Standard Reboot Commands
The vast majority of your system shut downs or reboots will follow one of these two forms.
The first will halt the system so you can power it off and the second will reboot the system:

```bash
# power off system
shutdown -h now

# reboot the system
shutdown -r now
```

[`shutdown`][06] is the preferred and the safest ways to stop Linux.
Never the less, in the tradition of Unix,
Linux gives you more than one way to accomplish this task.
[`reboot`][07], `halt`, and `poweroff` are some additional commands
that Linux provides to stop the system.
These commands can be more "forceful" than `shutdown` but [similar to it][08].

The simplicity of these commands give the illusion that the system state of Linux is running or not running.
It isn't quite that simple.
Linux can operate in several states called runlevels.

## Linux Runlevels
[runlevel][09] is a preset operating state for the Linux operating system.
A system can be booted into  any of several runlevels,
each of which is represented by a single digit integer.
Each runlevel designates a different system configuration
and allows access to a different combination of processes and system resources.

Seven runlevels are supported in the standard Linux kernel. They are:

* **0 - System Halted:**  all system activity is stopped, the system can be safely powered down
* **1 - Single User:**  single superuser is the only active login and no daemons (services) are started.
It is mainly used for maintenance.
* **2 - Multiple Users:** multiple users allowed but network filesystem (HFS) is not.
* **3 - Multiple Users:**  multiple users are allowed command line (i.e., all-text mode);
the standard runlevel for most servers
* **4 - User-Definable**
* **5 - Multiple Users:** multiple users are allowed graphical user interface;
the standard runlevel for most desktop systems
* **6 - Reboot:** just like run level 0 except a reboot is issued, used when restarting the system

In the interests of completeness,
there is also a runlevel 'S' that the system uses on it's way to another runlevel.
Read the [man page for the `init` command][10] for more information,
but you can safely skip this for all practical purposes.

By default Linux boots either to runlevel 3 or to runlevel 5.
The former permits the system to run all services except for a GUI.
The latter allows all services including a GUI.

Booting into a different runlevel can help solve certain problems.
For example, if a change made in the X Window System configuration on a machine
that has been set up to boot into a GUI has rendered the system unusable,
it is possible to temporarily boot into a
console (i.e., all-text mode) runlevel (i.e., runlevels 3 or 1)
in order to repair the error and then reboot into the GUI.
Likewise, if a machine will not boot due to a damaged configuration file
or will not allow logging-in because of a corrupted `/etc/passwd` file
or because of a forgotten password,
the problem can solved by first booting into single-user mode (i.e. runlevel 1).

There are two commands for directly reading or manipulating the Linux rumlevels:

* **`runlevel`** - Use the `runlevel` command to tell you two things:
The last run level, and the current run level.
If the first character is 'N', it stands for none,
meaning there has been no run level change since powering up.
* **`telinit`** - The program responsible for altering the runlevel is `init`,
and it can be called using the `telinit` command.

The [topic of runlevels][11] is actually much richer than what is illustrated here.
It plays a key role in Linux background processes, called services or daemons.
For more, check out this [Managing Services in Ubuntu, Part I: An Introduction to Runlevels][12]
and [Part II][13].

## Getting a Login From a Frozen GUI Screen
A not so common problem is when a frozen,
full screen X application takes control over your mouse and keyboard
and it seems that the only way to regain access to the system is to force a shutdown.
The fact is, if you could get to a some form of terminal session,
you might be able to kill the offending process and get out of this frozen state.
This is where accessing a console screen by pressing `CTRL` + `ALT` + `Fx`
(where `Fx` is a function key on the keyboard from `F1` to `F6`;
and `F7` brings you back to the desktop) can be very handy.

The X Server can often be the source of these frozen screen situations,
so restarting the X Server may be the solution.
This can be done via the key combination `Ctrl`+`Alt`+`Backspace`.
Keep in mind that you will loses any unsaved data in applications.
Also, this capability is turned off by default on may Linux systems (including Ubuntu).
This was done to avoid confusion by  people accustom to MS Windows.
An alternative key combination is as follows:

* Press [`AltGR`][01] + [`SysRQ`][02] + `K`
instead (`AltGR` is the RIGHT `ALT` button and `SysRQ` is often labeled "Print Screen",
and remember to press and hold the keys in the in the right sequence,
e.g. starting with `ALtGR`, and ending with the `K`(ill) key).

You can turn back on the `Ctrl`+`Alt`+`Backspace` by following the instructions [here][14].

## Magic SysRq Key
If the system is completely locked up,
or [your filesystem fails][17], there are still alternatives.
The [magic SysRq key][15] provides a way to send commands directly to the kernel
through the [`/proc` filesystem][16].
It is enabled via a kernel compile time option, `CONFIG_MAGIC_SYSRQ`,
which seems to be standard on most distributions.
The magic SysRq key (or `PrintScrn` or `Print Screen` on some keyboards)
a key combination understood by the Linux kernel,
which allows the user to perform various low-level commands regardless of the system's state.
This is a surprising feature of the kernel
but is commonly used to perform a safe reboot of a locked-up Linux computer.
See this post for some [historical perspective of the SysReq key][18].

To check if the `CONFIG_MAGIC_SYSRQ` option is enable on your Linux kernel,
check the configuration file that installed to /boot partition.
Do this via:

```bash
# check if magic sysrq key is enabled
$ cat /boot/config-$(uname -r) | grep CONFIG_MAGIC_SYSRQ
CONFIG_MAGIC_SYSRQ=y
CONFIG_MAGIC_SYSRQ_DEFAULT_ENABLE=0x01b6
CONFIG_MAGIC_SYSRQ_SERIAL=y
CONFIG_MAGIC_SYSRQ_SERIAL_SEQUENCE=""
```

If your get `CONFIG_MAGIC_SYSRQ=y`, then Magic SysRq Key is enabled on your kernel.

When running a kernel with SysRq compiled in,
`/proc/sys/kernel/sysrq` controls the functions allowed to be invoked via the SysRq key.
If the file contains `1`,
that means that every possible SysRq request is allowed.
See [here][19] for more on the `/proc/sys/kernel/sysrq`.

To actually reboot the machine there is a well know key sequence to follow:
REISUB (or REISUO if you want to turn off the system instead of reboot).
Basically, if you keep pressed `AltGR` + `SysRq` + `R`
and then while you keep pressed `AltGR` + `SysRq` you press `E`, `I`, `S`, `U`, `B`
 about 1 second between each letter (do not type it fast).
Your system will reboot.
 is a safer alternative to just cold rebooting the computer.

Mnemonic for REISUB is **R**eboot **E**ven **I**f  **S**ystem **U**tterly **B**roken,
so while pressing `AltGR + SysRq`, press the following keys:

* **R** - Switch to [XLATE mode][20]
* **E** - Send [Terminate signal][21] to all processes except for `init`
* **I** - Send [Kill signal][22] to all processes except for `init`
* **S** - [Sync][23] all mounted filesystems
* **U** - Remount filesystems as read-only
* **B** - Reboot

The magic SysRq key supports more then just the REISUB keys.
To see the larger range of thing you can do via Magic SysRq Key's
direct communications with the kernel, [check out here][24].



[01]:http://en.wikipedia.org/wiki/AltGr_key
[02]:http://en.wikipedia.org/wiki/System_request
[03]:http://www.thegeekstuff.com/2009/12/4-ways-to-kill-a-process-kill-killall-pkill-xkill/
[04]:http://en.wikipedia.org/wiki/Zombie_process
[05]:http://www-cdf.fnal.gov/offline/UNIX_Concepts/concepts.zombies.txt
[06]:http://linux.die.net/man/8/shutdown
[07]:http://manpages.ubuntu.com/manpages/lucid/man8/reboot.8.html
[08]:http://askubuntu.com/questions/64995/what-is-the-difference-between-shutdown-and-poweroff-commands
[09]:http://en.wikipedia.org/wiki/Runlevel
[10]:http://linux.about.com/od/commands/l/blcmdl8_init.htm
[11]:http://www.debian-administration.org/articles/212
[12]:http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/
[13]:http://pthree.org/2008/02/27/managing-services-in-ubuntu-part-ii-managing-runlevels/
[14]:https://wiki.ubuntu.com/XorgCtrlAltBackspace
[15]:http://en.wikipedia.org/wiki/Magic_SysRq_key
[16]:http://www.linuxjournal.com/article/8381
[17]:http://www.linuxjournal.com/content/rebooting-magic-way
[18]:http://royal.pingdom.com/2012/06/26/sysadmin-needs-sysrq-magic/
[19]:http://lxr.linux.no/linux/Documentation/sysrq.txt
[20]:http://unix.stackexchange.com/questions/16530/what-does-raw-unraw-keyboard-mode-mean
[21]:http://www.gnu.org/software/libc/manual/html_node/Termination-Signals.html
[22]:http://meinit.nl/the-3-most-important-kill-signals-on-the-linux-unix-command-line
[23]:http://linux.die.net/man/1/sync
[24]:http://www.isotton.com/devel/docs/sysrq-cheatsheet/
