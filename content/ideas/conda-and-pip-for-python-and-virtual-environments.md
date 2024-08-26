<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------



**Add information about Conda-Lock.  See README.md in the root directory.**

* [Conda Cheat Sheet](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf)


# What is pipx?

* [Why You Should Install Python Apps With pipx (and How to Get Started)](https://www.howtogeek.com/install-python-apps-with-pipx/)


# What About Pip?

* [Python Basics Exercises: Installing Packages With pip](https://realpython.com/courses/basics-exercises-install-packages-with-pip/)


# What is the Difference Between Miniconda and Anaconda?
The main difference between Anaconda and Miniconda lies in their size and the number of pre-installed packages. Anaconda is larger and comes with a vast array of pre-installed packages, while Miniconda is smaller and only includes Conda and Python.

Anaconda is a free and open-source distribution of Python and R programming languages. It’s widely used in scientific computing, data science, machine learning, and related fields. Anaconda simplifies package management and deployment, making it easier for you to manage your Python environment.
Anaconda comes with over 1,500 pre-installed packages, including popular ones like NumPy, Pandas, and Matplotlib. It also includes Conda, a powerful package manager and environment manager.
While Python is a versatile programming language that can be used for a wide range of applications, Anaconda provides a more specialized environment for machine learning and data science, with pre-installed packages and a package manager that make it easier to manage dependencies and resolve conflicts between packages.

Miniconda is a smaller, “minimal” version of Anaconda. It includes only Conda and Python, without any additional packages pre-installed.
Miniconda is lightweight and quick to install, making it a great choice if you’re working with limited disk space or only need specific packages.

* [Anaconda vs. Miniconda: A Guide for Data Scientists](https://saturncloud.io/blog/anaconda-vs-miniconda-a-guide-for-data-scientists/)

* [Anaconda](https://www.anaconda.com/distribution/)
* [Anaconda Python Tutorial: Everything You Need to Know](https://dzone.com/articles/python-anaconda-tutorial-everything-you-need-to-kn)
* [Getting started with Anaconda Python for data science](https://opensource.com/article/18/4/getting-started-anaconda-python)
* [How To Install the Anaconda Python Distribution on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-install-the-anaconda-python-distribution-on-ubuntu-16-04)
    * [How to Install Anaconda on Ubuntu 18.04 17.04 16.04](https://www.youtube.com/watch?v=UbzZtzLxxo0)

* [Conda: Myths and Misconceptions](https://jakevdp.github.io/blog/2016/08/25/conda-myths-and-misconceptions/)
* [Installing anaconda over existing python system?](https://stackoverflow.com/questions/34906338/installing-anaconda-over-existing-python-system)
* [Jupyter Standalone Might Just Be Better Than Anaconda](https://towardsdatascience.com/jupyter-standalone-might-just-be-better-than-anaconda-53104da05eee)


# What About Anaconda and Raspberry Pi?

* [Installing Anaconda Python Distribution on Raspberry Pi](https://www.youtube.com/watch?v=fYPr43YhTMM&t=185s)


# Ephemeral Environments
Ephemeral - something that lasts for a very short time
An ephemeral environment is an environment meant to last for a limited amount of time
ephemeral environments are supposed to be created, used for a limited period, and then discarded. Because of this, they’re also known as ‘on-demand environments’, ‘dynamic environments’, ‘temporary environments’, ‘sandbox environments’, or ‘short-lived environments’.
For example, they could be as short as the lifecycle of a CI/CD pipeline, or they could last for a few weeks (the length of a sprint).

* [What Are Ephemeral Environments? + How to Deploy and Use Them Efficiently](https://www.bunnyshell.com/blog/what-are-ephemeral-environment/)
* [Nix Shell](https://nixos.org/)
    * [Say Goodbye to Containers - Ephemeral Environments with Nix Shell](https://www.youtube.com/watch?v=0ulldVwZiKA)
    * [How Nix-Shell Saved Our Team’s Sanity](https://medium.com/att-israel/how-nix-shell-saved-our-teams-sanity-a22fe6668d0e)






Although Python applications can be made of a single file,
usually they consist of a series of functions, objects (classes), handy tools and of course,
variables spread across multiple file(s), placed inside modules.
These modules together make up what is referred as a package.

A Virtual Environment, oftern refered to as virtualenv,
is an isolated working copy of Python which allows you to work on a specific project
without worry of affecting other projects.
It enables multiple side-by-side installations of Python, one for each project.
It doesn’t actually install separate copies of Python, but it does provide a
clever way to keep different project environments isolated.

When you’re beginning,
it’s pretty easy to setup your Python environment on Linux.
But in time, things can get messy due to multiple versions, interpreters, utilities and projects.
The traditional way of installing a package involves first spotting it and then downloading.
It sounds simple and feels right since its like many things in Python,
but this can lead to problems down the road.
Packages can conflict with each other and be dependent on specific version of Python interpreters.

**The Goal** - Create isolated development environments that target different python interpreters and require different dependencies.

**The Problem** - When using python to develop a project, it is very easy to accidentally install packages that can be found by your system python. This is a problem because it makes it difficult to isolate dependencies on a per project basis. A better approach is to create isolated environments in which dependencies can be installed.

**The Solution** - Virtual environments (and a few other tools) can rescue us from this situation.
From the [official documents][05]:
"A virtual environment (also called a venv) is a Python environment such that the Python interpreter, libraries and scripts installed into it are isolated from those installed in other virtual environments, and (by default) any libraries installed in a “system” Python, i.e. one which is installed as part of your operating system."


## What is an Environment
In the world of Python, an environment is a folder (directory) which contains everything that a Python project (application) needs in order to run in an organised, isolated fashion. When it is initiated, it automatically comes with its own Python interpreter - a copy of the one used to create it - alongside its very own pip.


## Virtual Environments
Python has its own way of downloading, storing, and resolving packages (or modules).
Python makes decisions made about package storage and resolution,
which can lead to some problems on which packages are are pulled into your code.

At its core, the main purpose of Python virtual environments
is to create an isolated environment for Python projects.
This means that each project can have its own dependencies,
regardless of what dependencies every other project has.

Using the `virtualenv` tool consists of getting it to create a folder,
containing the Python interpreter and a copy of pip.
Afterwards, in order to work with it, we need to either specify the location of that interpreter
or us its `activate` command.


## Virtualenv and Shebang
It is important to use [shebang][11] `#!/usr/bin/env python` within Python executable scripts.
It runs `env`, which will look for the default python for that environment.
Therefore, your script will use the right path to you Python modules
and **not** `$PYTHONPATH` set for you login.

* [How to activate a Python virtual environment from a script file](https://www.a2hosting.com/kb/developer-corner/python/activating-a-python-virtual-environment-from-a-script-file)


## Leave Your Native Python Alone
Linux has many Python programs as part of it suite of tools.
I like them to be available in all sessions without activate any virtualenv.
And I don't want to mess with the global Python installation to avoid library conflict issues.
Another thing that I don’t like is installing big packages like
Jupyter/iPython, OpenCV, etc. on each of my projects’ virtualenvs.









[Python][01] is such a success in large part because of its very active community
in which people share their awesome solutions.
Unfortunately, there is a price.
[Python packages][02] you used get updated with a better way to solve their problem.
These changes can be breaking changes for the code you have written.
Popular packages, such as [Numpy][03] or [Matplotlib][04] are very reliable,
and chances that you get breaking changes are slim.
However, using packages that are not so popular cause problems.

The Python community has learned to cope with this problem via [virtual environments (`venv`)][05].
Python virtual enticements are isolated instances of Python with their own set of packages.
It is good practice to have a unique environment for each project you are doing.
A very popular tool to mange an instance of Python, and its companion packages,
within a virtual environment is the [Conda][06].
Conda gives you access practically all Python versions, its corresponding packages,
and it includes a easy system to manage virtual environments.

Conda give you two options for the Python distribution installation, that is,

* [Anaconda][07] a large full-fledged distribution, including many packages, tools & a GUI, ~7500 packages, ~3GB of disk space
* [Miniconda][08] another distribution which is much smaller base installation with a Python system, Pip, Conda, tools (no GUI), ~400MB of disk space

While Conda can be used to install packages,
you might want to only use it for virtual environments and Python versions.
Conda has a feature called dependency checking, which works quite well,
but sometimes can be a bit slow.
[Pip][09] might be preferred for some packages since its packages are sometime more up-to-date.
Another possibility is [Mamba][10] which is an implementation of Conda in C++ and runs significantly quicker.
Mixing them will probably work but it is probably better to use a single tool paradigm.

My preference is to do my installation with Miniconda,
use Conda for Python version management and virtual environment management,
and use Pip for package version management.

Sources:

* [Environments, Conda, Pip, aaaaah!: Managing Python environments without a headache](https://towardsdatascience.com/environments-conda-pip-aaaaah-d2503877884c)


# Installation of Your Python Environment - DONE
The following steps install Miniconda.
Not only will Miniconda will be installed but your `bash` shell environment
(specifically the files `.bashrc` or `.bash_profile`)
will be updated to include Miniconda in the `$PATH`.
Also, if the environment variable $PYTHONPATH is set, you will get a warning like
"_please verify that your $PYTHONPATH only points to directories of packages that are compatible with the Python interpreter in Miniconda3_"

```bash
# create a directory to install miniconda in
mkdir -p ~/.miniconda3

# download latest miniconda version
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/.miniconda3/miniconda.sh

# run the install script
bash ~/.miniconda3/miniconda.sh -b -u -p ~/.miniconda3

# delete the install script
rm -rf ~/.miniconda3/miniconda.sh

# add a conda initialize to your bash   <-- DO NOT run `conda init bash` if you plan to use `~/.dotfile` since it already contains the changes needed for `~/.bashrc`
#~/.miniconda3/bin/conda init bash

# verify the installation by listing the contents of the install
$ conda env list
# conda environments:
#
base                  *  /home/jeff/.miniconda3
circuitpython            /home/jeff/.miniconda3/envs/circuitpython

# list the envirnments established (should only be 'base')
conda env list
```

Following the steps above, restart the terminal and Miniconda is ready to go.

To uninstall Miniconda, you follow these steps:

```bash
# backup any important data and python environments
conda env list
conda env export --name base > environment_base.yml
conda env export --name circuitpython > environment_circuitpython.yml

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

* [Install Miniconda on Linux from the command line in 5 steps](https://javedhassans.medium.com/install-miniconda-on-linux-from-the-command-line-in-5-steps-403912b3f378)
* [How to Uninstall Miniconda on Linux: A Guide](https://saturncloud.io/blog/how-to-uninstall-miniconda-on-linux-a-guide/)


# Typical Workflow


#### Step 1: Create and Activate Environment
The typical workflow for a Python project is to create an environment for each project or task,
just to keep things separate.
You create an environment using `conda`:

```bash
# create an environment using conda
#    a single ‘=’ we tell conda to use the latest version in the Python 3 release tree, at the moment this is version 3.11.5
#    if you would like to use a specific version, use tow equal signs like '=='
conda create --name test python=3.8

# activate the new environment
conda activate test

# list the conda environment
conda info --envs
# or
conda env list

# check you python version used:way
$ python --version
Python 3.8.18
```

Use the `conda` in an activated environment to update all the packages to their latest versions.
This ensures that you have the latest features and bug fixes.

```bash
# activate environment before update
conda activate test

# update all the packages to their latest versions
conda update --all
```

To deactivate an active environment, do the following

```bash
# deactivate an active environment
conda deactivate
```


#### Step X: Install Desired Packages

```bash
# pip should already be installed but lets make sure
conda install pip
```


#### Step X: Transfer a Conda Environment to Another Device
Transferring a Conda environment to another device involves
exporting the environment on the source device, then importing it on the target device.

```bash
# export the environment by activate it first
conda activate test
conda env export > environment.yml

# import the environment on the target device
conda env create -f environment.yml
```

pyder
This will create a new environment with the same name and packages as the original.


#### Step X: Remove/Delete Conda Environment
The command used to remove a Conda environment is `conda env remove --name <env_name>`,
where `<env_name>` is the name of the environment you want to remove.
This command will delete the specified environment,
along with all its associated packages and dependencies.


```bash
# you must deactivate you environments first
conda deactivate

# now remove the environment
conda env remove --name test
```

What is deleted is in the directory `~/.miniconda3/envs/<env_name>`
It does not delete any of the Python development you have done.

In some cases, you may encounter a corrupted Conda environment where the above command doesn't work.
In such cases, you can manually delete the environment by removing its directory from the `envs` folder in your Conda installation.

Sources:

* [How to Remove Conda Environment: Best Practices & Commands](https://docs.kanaries.net/topics/Python/conda-remove-environment)





[01]:https://www.python.org/
[02]:https://pypi.org/
[03]:https://pypi.org/search/?q=numpy
[04]:https://pypi.org/search/?q=Matplotlib&o=
[05]:https://docs.python.org/3/library/venv.html
[06]:https://docs.conda.io/en/latest/
[07]:https://www.anaconda.com/download
[08]:https://docs.conda.io/projects/miniconda/en/latest/
[09]:https://pypi.org/project/pip/
[10]:https://mamba.readthedocs.io/en/latest/
[11]:https://bash.cyberciti.biz/guide/Shebang

