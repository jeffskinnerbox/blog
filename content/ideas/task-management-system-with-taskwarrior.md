<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------


# TaskWorrior
I wanted a way to manage my project tasks within my NeoVim terminal.
I don't need a tight integration, just a way manage my project task with easy;
I'm thinking just a popup window.
The task management can be a stand allow commandline tool.

I considered using / building my own simple Python task management commandline tools.
I looked at the following candidates tools:

* [Build a Command-Line App with Python in 7 Easy Steps](https://www.kdnuggets.com/build-a-command-line-app-with-python-in-7-easy-steps)
* [A Simple Command-Line TO-DO List App](https://github.com/balapriyac/python-projects/tree/main/command-line-app)
* [Build a Command-Line To-Do App With Python and Typer](https://realpython.com/python-typer-cli/)
* [Manage Your To-Do Lists Using Python and Django](https://realpython.com/django-todo-lists/)

I almost pursued developing one of these tools but I decide to take a quick look at what might already in open source.
This is when I bumped into [Taskwarrior][01].
Taskwarrior is free and open source software that manages your TODO list from the command line.
It appears to be poppular, well supported, and has integrations with NeoVim.
It also appears to have excellent documentation as illustrated by the following:
[Taskwarrior FAQ List][04], [Taskwarrior Documentation][05],
[Taskwarrior Tools & Extensions][06], [Best Practices][07], and [Taskwarrior Commands][08].

Sources:

* [Using taskwarrior to manage my todos](https://www.markpitblado.me/blog/using-taskwarrior-to-manage-my-todos)
* [Taskwarrior is THE task management system you need](https://www.youtube.com/watch?v=rRTnF-EMey0)
* [To-Do Lists for Hackers! (Taskwarrior)](https://www.youtube.com/watch?v=5wmcn9-IQE4)
* [How To Use VIT The Curses Based Front End To Taskwarrior](https://www.youtube.com/watch?v=wY3DJVSWdeI)
* [A Dive into Taskwarrior Ecosystem with Tomas Babej](https://www.youtube.com/watch?v=tijnc65soEI)
* [Task Management](https://www.chiark.greenend.org.uk/~cjwatson/blog/task-management.html)
* [Reclaim Your Data Ownership: Leveraging Unix Philosophy for Modern Digital Workflows](https://itnext.io/reclaim-your-data-ownership-leveraging-unix-philosophy-for-modern-digital-workflows-25491f6da35d)


---------------


# Installation & Configuration of TaskWarrior
Ubuntu's version of Taskwarrior seem quite old ([dating back to October 2021][02]).
I checked the version via the code block below:

```bash
# install taskwarrior
sudo apt install taskwarrior

# check taskwarrior version
$ task --version
2.6.2

# remove this old version of taskwarrior
sudo apt remove taskwarrior
```

[Taskwarrior website][01] says the current stable version (as of 08/18/23) is 3.0.2.
Discovering this, I followed [Taskwarrior's download instructions][03]
to get the latest stable release.


#### Step 1: Download and Build Taskwarrior - DONE
Build the `task` program according to the directions in the `INSTALL` file

```bash
# goto installation directory
mkdir ~/src/taskwarrior
cd ~/src/taskwarrior

# download taskwarrior's tar file
wget https://github.com/GothenburgBitFactory/taskwarrior/releases/download/v3.0.2/task-3.0.2.tar.gz
wget https://github.com/GothenburgBitFactory/taskwarrior/releases/download/v3.0.2/task-3.0.2.tar.gz

# unpack the tarball file
tar xzvf task-3.0.2.tar.gz
trash task-3.0.2.tar.gz

# read the INSTALL and README.md files
pg task-3.0.2/INSTALL
pg task-3.0.2/README.md

# install some needed libraries (you'll get a failure message from cmake if needed)
sudo apt install uuid-dev rustc cargo

# build taskwarrior from source
cd ~/src/taskwarrior/task-3.0.2
cmake -DCMAKE_BUILD_TYPE=release .
make
sudo make install

# validated taskwarrior is operational
$ task --version
3.0.2
```


#### Step 2


#### Step 3


#### Step 4


---------------


# Simple Note Taking
`kiwi.nvim` is a stripped down VimWiki for Neovim.
Kiwi, the lean personal wiki for Neovim!

`kiwi.nvim` is a plugin for markdown note taking with linking notes, as in zettlecasten notes.

In short, this plugin is a lightweight replacement for VimWiki. It has the most important features provided by VimWiki and uses pure markdown to take notes.

kiwi.nvim is a new project which aims to be a minimal wiki plugin that doesn't
add features that many users will not use. If you want additional
functionality for your personal wiki, you can install other specialised
plugins to provide functions like syntax highlighting or autosave. You can
also create personal keymappings and personal functions to make your wiki
truly personal.

You can use a wiki in Neovim to:

* organize notes and ideas
* manage to-do lists
* write documentation
* write blog posts to publish using Hugo or Astro

Source:

* [kiwi.nvim - A simple markdown note taking plugin](https://serenevoid.github.io/blog/my-note-taking-plugin/)


---------------


# Mobile App

* [TaskWarrior Mobile](https://play.google.com/store/apps/details?id=com.ccextractor.taskwarriorflutter&hl=en_US)
* [WingTask](https://wingtask.com/)


# Integration With NeoVim

* [GitHub: ribelo/taskwarrior.nvim](https://github.com/ribelo/taskwarrior.nvim?tab=readme-ov-file#taskwarrior-command)
* [GitHub: huantrinh1802/m_taskwarrior_d.nvim]<https://github.com/huantrinh1802/m_taskwarrior_d.nvim()>


# Terminal Interface
There are several terminal user interface for taskwarrior.

* [taskwarrior-tui](https://kdheepak.com/taskwarrior-tui/)



[01]:https://taskwarrior.org/
[02]:https://taskwarrior.org/news/
[03]:https://taskwarrior.org/download/
[04]:https://taskwarrior.org/support/faq/
[05]:https://taskwarrior.org/docs/
[06]:https://taskwarrior.org/tools/
[07]:https://taskwarrior.org/docs/best-practices/
[08]:https://docs.wingtask.com/docs/taskwarrior_commands/
[09]:
[10]:
[11]:

