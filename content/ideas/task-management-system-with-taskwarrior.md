<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------


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

Sources:

* [Using taskwarrior to manage my todos](https://www.markpitblado.me/blog/using-taskwarrior-to-manage-my-todos)
* [Taskwarrior is THE task management system you need](https://www.youtube.com/watch?v=rRTnF-EMey0)
* [To-Do Lists for Hackers! (Taskwarrior)](https://www.youtube.com/watch?v=5wmcn9-IQE4)
* [How To Use VIT The Curses Based Front End To Taskwarrior](https://www.youtube.com/watch?v=wY3DJVSWdeI)
* [A Dive into Taskwarrior Ecosystem with Tomas Babej](https://www.youtube.com/watch?v=tijnc65soEI)
* [Task Management](https://www.chiark.greenend.org.uk/~cjwatson/blog/task-management.html)



[Taskwarrior][01] is free and open source software that manages your TODO list from the command line.

[Taskwarrior FAQ List](https://taskwarrior.org/support/faq/)
[Taskwarrior Documentation](https://taskwarrior.org/docs/)
[Taskwarrior Tools & Extensions](https://taskwarrior.org/tools/)
[Taskwarrior Commands](https://docs.wingtask.com/docs/taskwarrior_commands/)


---------------


# Installation of TaskWarrior
Ubuntu's version of Taskwarrior seem quite old ([dating back to October 2021][02]):

```bash
# install taskwarrior
sudo apt install taskwarrior

# check taskwarrior version
$ task --version
2.6.2


# remove this old version of taskwarrior
sudo apt remove taskwarrior
```


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
[03]:
[04]:
[05]:
[06]:
[07]:
[08]:
[09]:
[10]:
[11]:

