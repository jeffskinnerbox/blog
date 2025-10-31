<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
    title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------

<h1 style="text-align: center;">SUMMARY</h1>

```bash
# Sources:
#   Python Virtual Environments: A Primer - https://realpython.com/python-virtual-environments-a-primer/
#   Managing Multiple Python Versions With pyenv - https://realpython.com/intro-to-pyenv/
#   Managing Python Projects With uv: An All-in-One Solution - https://realpython.com/python-uv/
#   Python and TOML: New Best Friends - https://realpython.com/python-toml/
#   How to Manage Python Projects With pyproject.toml - https://realpython.com/python-pyproject-toml/


# --------------------------- typical installation when using uv / pyenv --------------------------

# supply all needed dependencies
sudo apt update
sudo apt install make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev \
     curl git libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev

# install uv on your system using the recommended installer
curl -LsSf https://astral.sh/uv/install.sh | sh

# install pyenv on your system using the recommended installer
curl -fsSL https://pyenv.run | bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init - bash)"' >> ~/.bashrc
exec "$SHELL"     # reload your shell or alternatively you can restart your terminal


# ---------------------- create your development environment with uv / pyenv -----------------------

# determine the python version you want for your development
pyenv install --list | grep -E ' 3\.([1-9][0-9]+)'

# create your virtual environment for python development
cd <project-directory>
pyenv install 3.13.7                 # released on August 14, 2025
pyenv local 3.13.7
uv init
uv run main.py
source .venv/bin/activate

# install you standard development tools
uv pip install flask ruff

# install the stubs for circuitpython libraries (this installs stubs for ALL boards)
uv pip install circuitpython-stubs

# -OR- if your reproducing an existing project
uv pip install -r requirements.txt


# ---------------------- typical development workflow when using uv / pyenv -----------------------

# supply all needed dependencies (vim & nvim not included)
sudo apt install tio
sudo usermod -a -G dialout <your-username>

# load vim or nvim with your program on your pc and make your edits
vim <path-to-file>/code.py

# within vim or nvim, save your edits to your pc at the same file location
:w

# within vim or nvim, copy you program to the microprocessor's copy.py file
:!cp % /media/jeff/CIRCUITPY/code.py

# find the path to your device
tio -L

# open a terminal outside of vim or nvim and control & monitor python REPL
tio /dev/ttyACM0

# press `Ctrl+C` then `Ctrl+D` in the terminal window to restart your board
# enter `Ctrl-t q` to exit serial terminal `tio`


# ----------------------- typical close-out workflow when using uv / pyenv ------------------------

# to save your project for later use
pip freeze > requirements.txt
```


---------------


* [Python 3.14 and the End of the GIL](https://towardsdatascience.com/python-3-14-and-the-end-of-the-gil/)

# Next-gen Python Tooling
Over the years, legacy Python has created multiple tools & procedures to manage the Python interpreter,
the software project using Python code, the modules/libraries used by Python,
and the command-line tool used to format/lint/validate/build/document/publish Python code.
Not all these tools work well together and they also over lap in their functional role.
This can cause even an experience Python developer confusion & difficulties.
This challenge has stimulated the effort to create a more unified tool, called `uv`, to address this problem.

[`uv`][01] is a single tool who's mission is to replace
[`pip`][02], [`pipx`][03], [`pip-tools`][04], [`poetry`][05], [`pyenv`][06], [`twine`][07], [`virtualenv`][08], and more.
[`ruff`][09] can be used to replace [Flake8][10] (plus dozens of plugins), [Black][11], [`isort`][12], [`pydocstyle`][13], [`pyupgrade`][14], [`autoflake`][15], and more,
all while executing tens or hundreds of times faster than any individual tool.

**Question:**
* I'm using existing Python environments and I'm pleased with what I can do.
  So, the questions becomes: Does the value provided by `uv` justify having another tool installed on my system?
  Why not just stick with Python tooling and accept `pip` or `venv` will be slightly slower?
  What am I missing here?

**Answer:**
* Do you build images regularly? `uv` is phenomenal in that context.
* Do you try and share you code with other people, who have different computers than you? Again, `uv` shines.
* Do you want global access to python-based tools across different projects,
  without the headache of managing tool-specific virtual environments? `uv` is for you.
* `uv` actually resolves your python version.
  We often get devs who last interacted with a service 1+ minor versions of python ago.
  A lot of libraries and `stdlib` stuff doesn't work right with pinned packages on an older version.
  The troubleshooting can take some time and is an easy solve, but is annoying.
  The fact that `uv` resolves the python versioning via [`uv sync`][18] is miles ahead of pip tools.

This last point cannot be overstated.
The fact that `uv` can, on the fly, download the correct version of Python modules,
compatible with the target OS and architecture,
is a game changer and takes it from a handy tool to indispensable.
Sure, that could be managed in different ways,
but the simplicity of setting up your entire environment from scratch with `uv sync` is just marvelous.

## Python Version vs Python Project Management
Your going to be using two primary tools:

* [`pyenv`][06] manages your Python versions
* [`uv`][01] manages your project's virtual environment and packages

`uv` cannot perform the same core tasks as `pyenv`.
They don't conflict; they complement each other.
`uv` will use the Python version that `pyenv` has made active for your project.
Think of it like this: `pyenv` manages the workshop (i.e. manages Python versions),
and `uv` manages the project on the workbench (i.e. manages virtual environments & project packages).

Here is the standard workflow that shows how `uv` and `pyenv` interact seamlessly.

1. Create Your Project Directory -
In an effort to organize and isolate your project,
you need to create a project directory, initialized properly via `pyenv` and `uv`.

```bash
# create your new project directory called "my-project"
uv init my-project
```

2. Select Your Python Version with `pyenv` -
First, you tell `pyenv` which version of Python you want to use for your project.
This is usually done on a per-project basis.

```bash
# navigate to your project directory
cd my-project

# tell pyenv to use Python 3.11.8 for this directory specifically
pyenv local 3.11.8

# check that you python version has been update
cat .python-version
# or
pyenv version
```

3. Activate and Use Your Environment -
Now you can activate the environment and use `uv` to install packages and build your project

```bash
# run the project’s entry-point script
uv run main.py

# activate the environment
cd my-project
source .venv/bin/activate

# use uv to install packages into the active environment
uv pip install flask ruff
```

Sources:
* [Next-gen Python Tooling](https://docs.astral.sh/)
* [uv Official Documentation](https://docs.astral.sh/uv/getting-started/installation/)
* [UV and Ruff: Next-gen Python Tooling](https://www.youtube.com/watch?v=ifj-izwXKRA)
* [Python, pip, pyenv, uv. Why do we need them?](https://www.youtube.com/watch?v=IYcTaZfjODg)
* [Managing Python Projects With uv: An All-in-One Solution](https://realpython.com/python-uv/)
* [Python Tutorial: UV - A Faster, All-in-One Package Manager to Replace Pip and Venv](https://www.youtube.com/watch?v=AMdG7IjgSPM)

---------------

## Complete Python Project Development Workflow
With `uv`, you can install and manage multiple Python versions, create virtual environments,
efficiently handle project dependencies, reproduce working environments, and even build and publish a project.
These capabilities make `uv` an all-in-one tool for Python project management.

* `uv` is a Python package and project manager that integrates multiple functionalities into one tool,
  offering a comprehensive solution for managing Python projects.
* `uv` is used for fast dependency installation, virtual environment management, Python version management,
  and project initialization, enhancing productivity and efficiency.
* `uv` can build and publish Python packages to package repositories like PyPI,
  supporting a streamlined process from development to distribution.
* `uv` automatically handles virtual environments, creating and managing them as needed to ensure clean
  and isolated project dependencies.

### Installing / Updating / Uninstalling `uv` & `pyenv`

#### Step 1: Install uv & pyenv
`uv` provides a standalone installer to download and install `uv`.
This places `uv` files in your `~/.local` directory:

```bash
# install uv & pyenv on your system using the recommended installer
curl -LsSf https://astral.sh/uv/install.sh | sh
curl -L https://raw.githubusercontent.com/pyenv/pyenv-installer/master/bin/pyenv-installer | bash

# check your uv install
$ whereis uv
uv: /usr/include/uv /home/jeff/.local/bin/uv

$ uv --version
uv 0.8.18

# check your pyenv install
$ whereis pyenv
pyenv: /home/jeff/.pyenv/bin/pyenv

$ pyenv --version
pyenv 2.6.8
```

#### Step 2: Upgrading to the Latest uv Version
The `uv` project is currently under active development, which means that new versions are released regularly.
If you’ve installed `uv` using the standalone installer (as we did here)
and would like to be up to date with the latest version, then you can run the following command:

```bash
# upgrade uv
uv self update

# upgrade pyenv
pyenv update
```

#### Step 3: Uninstall uv & pyenv
If you wish to uninstall `uv`, not that the
`uv` installer script (`curl -LsSf https://astral.sh/uv/install.sh | sh`)
puts `uv` into your home directory under `~/.local/bin/uv`.
So to uninstall uv, you can simply delete the binary and any cached files:

```bash
# remove the binary uv & pyenv
rm -f ~/.local/bin/uv
rm -rf $(pyenv root)

# remove uv cache, config, data
rm -rf ~/.cache/uv
rm -rf ~/.local/share/uv
rm -rf ~/.config/uv
```

### Creating Python Project

#### Step 1: Create Python Project
To create and initialize a Python project with `uv`,
navigate to the directory where you want to store the project.
Once there, you can run the following command to create and initialize the project:

```bash
# create your project directory and initialize it as project "my-project"
uv init my-project

# if you have already created a project directory for your new project called "my-project"
cd my-project
uv init

# the resulting project structure created
$ tree -a --filesfirst $HOME/..../my-project/

$HOME/..../my-project/
├── .gitignore
├── main.py
├── pyproject.toml
├── .python-version
├── README.md
└── .git
```

>**NOTE:** If you want to start managing an existing project with `uv`,
>then navigate to the project directory and run the following command: `uv init`.
>This command will create the `uv` project structure for you.
>It won’t overwrite the `main.py` file if you have one, but it’ll create the file if it’s missing.
>It neither modifies your Git repository nor your `README.md` file.
>
>However, this command won’t work if you already have a `pyproject.toml` file in place.
>If that’s the case, then you can move the file to another location and run the `uv init` command.
>Finally, you can update the new file with any relevant configuration from your old `pyproject.toml`.

#### Step 2: Run the Project’s Entry-Point Script
Once you’ve created the project, you can use `uv` to run the entry-point script,
which is the `main.py` file by default.
This action will automatically create for you a virtual environment via a `.venv` directory.
To run the script, go ahead and execute the following command:

```bash
# run the project’s entry-point script
$ uv run main.py
Using CPython 3.12.3 interpreter at: /usr/bin/python3.12
Creating virtual environment at: .venv
Hello from my-project!
```

>**Note:** You can change the entry-point script’s name and location at any time.
>Naming it `main.py` isn’t mandatory.

#### Step 3: Install Desired Python Version
Before Step 2 (aka before creating the `.venv`), or now,
you are free to change the version of Python you will be operating under.
If you want to change to Python version 3.13.7, do this as follows:

```bash
# change you python version to 3.13.7 in you virtual environment
pyenv local 3.13.7

# check that you python version has been update
cat .python-version
# or
pyenv version
```






### Syncing Your Environment
The `uv sync` command is designed to keep your virtual environment aligned with your project's dependency requirements.
When you run `vu sync`, `uv` compares the current state of your environment against the
dependencies specified in your `requirements.txt` or `pyproject.toml` files.

So if you have a `venv`, `pyproject.toml` and `uv.lock` managed project,
the `uv sync` command installs / updates all dependencies specified in the `pyproject.toml` and `uv.lock` files.
It performs the following actions:

* **Installation**: Installs any missing dependencies that are listed in your requirements but not yet present in your environment.
* **Upgrades/Downgrades**: Adjusts the versions of existing packages to match the versions specified in your requirements.
  This ensures that your environment is using the exact versions you’ve defined,
  which is crucial for avoiding unexpected behavior due to version mismatches.
* **Uninstallation**: Removes any packages that are installed in the environment but not listed in your requirements,
  keeping the environment clean and free from unnecessary bloat.








Use these sources to finish text below:
* [uv: Towards a unified vision for Python tooling](https://thedataquarry.com/blog/towards-a-unified-python-toolchain/)
* [Managing Multiple Python Versions With pyenv](https://realpython.com/intro-to-pyenv/)
* [uv vs pip: Managing Python Packages and Dependencies](https://realpython.com/uv-vs-pip/)
* [Managing Python Projects With uv: An All-in-One Solution](https://realpython.com/python-uv/)
* [A Comprehensive Guide to Python Project Management and Packaging: Concepts Illustrated with uv – Part I](https://reinforcedknowledge.com/a-comprehensive-guide-to-python-project-management-and-packaging-concepts-illustrated-with-uv-part-i/)
* [A Comprehensive Guide to Python Project Management and Packaging: Concepts Illustrated with uv – Part II](https://reinforcedknowledge.com/a-comprehensive-guide-to-python-project-management-and-packaging-concepts-illustrated-with-uv-part-2/)
* [Python UV: The Ultimate Guide to the Fastest Python Package Manager](https://www.datacamp.com/tutorial/python-uv)
* [uv Package Manager for Python](https://medium.com/@nimritakoul01/uv-package-manager-for-python-f92c5a760a1c)
* [Mastering Python Project Management with uv](https://dev.to/thomas_bury_b1a50c1156cbf)


### Running Your Project

### Python Dependency Management
`uv` give you a cleaner workflow for project dependencies.
This workflow allows you to lock your project’s dependencies so that other developers can reproduce your environment exactly
and contribute to your code without much setup effort.

#### Step X: Adding Dependencies With `uv`
#### Step X: Removing Dependencies With `uv`


### Python Version Management with `pyenv`

### Installing Packages: Pip, Pipx, Pip-Tools - no longer needed
[`pip`][02]
[`pipx`][03]
[`pip-tools`][04]
* [pip-tools: introduction](https://calmcode.io/course/pip-tools/introduction)
* [Using Python's pip to Manage Your Projects' Dependencies](https://realpython.com/what-is-pip/)
* [uv vs pip: Managing Python Packages and Dependencies](https://realpython.com/uv-vs-pip/)

## Managing Python Build Environments
### Building Packages With `uv`
### Creating Packageable Apps With `uv`
### Uploading Packages With `uv`
* [`twine`][07]
* [How to Publish an Open-Source Python Package to PyPI](https://realpython.com/pypi-publish-python-package/)

## Managing Python Packages and Dependencies
### Python Package Dependency Management
* [`poetry`][05]
* [Simplifying Python Dependency Management with Poetry](https://medium.com/@jdgb.projects/simplifying-python-dependency-management-with-poetry-e996738778bc)
* [Poetry - Python dependency management and packaging made easy](https://python-poetry.org/)
* [How to Use Poetry in Python to avoid Dependency Hell](https://www.youtube.com/watch?v=V5rKVrVhEh8)
* [Stop Wasting Hours - Every Python Dev NEEDS to Master Poetry](https://www.youtube.com/watch?v=nrm8Lre-x_8)

## Managing Python Version
## Managing Python Version Changes
* `uv sync`
### Managing Python Version
* [`pyenv`][06]
* [`pyupgrade`][14]
* [Managing Multiple Python Versions With pyenv](https://realpython.com/intro-to-pyenv/)

### Python Virtual Environments
[`virtualenv`][08]
[`venv`][16]
* [Python Virtual Environments: A Primer](https://realpython.com/python-virtual-environments-a-primer/)
* [virtualenv: intro](https://calmcode.io/course/virtualenv/intro)
* [How to Create a Python Virtual Environment(Step-by-Step Guide)](https://www.geeksforgeeks.org/python/create-virtual-environment-using-venv-python/)

### Python Code Formatting & Linting
* [`ruff`][09]
* [Flake8][10]
* [Black][11]
* [`autoflake`][15]
* [`isort`][12]
* [`pydocstyle`][13]
* [Ruff: A Modern Python Linter for Error-Free and Maintainable Code](https://realpython.com/preview/ruff-python/)
* [A Guide to Popular Python Static Analysis Tools](https://blog.codacy.com/python-static-analysis-tools)
* [How to Write Beautiful Python Code With PEP 8](https://realpython.com/python-pep8/)
* [Python Linter Comparison 2022: Pylint vs Pyflakes vs Flake8 vs autopep8 vs Bandit vs Prospector vs Pylama vs Pyroma vs Black vs Mypy vs Radon vs mccabe](https://inventwithpython.com/blog/2022/11/19/python-linter-comparison-2022-pylint-vs-pyflakes-vs-flake8-vs-autopep8-vs-bandit-vs-prospector-vs-pylama-vs-pyroma-vs-black-vs-mypy-vs-radon-vs-mccabe/)
* [Why Pylint is both useful and unusable, and how you can use it](https://pythonspeed.com/articles/pylint/)
* [Goodbye to Flake8 and PyLint: faster linting with Ruff](https://pythonspeed.com/articles/pylint-flake8-ruff/)

### Python Command-line Utilities
* [Python's many command-line utilities](https://www.pythonmorsels.com/cli-tools/)

### Python Code Documentation
* [`pydoc`][17]
* Sphinx
* [How to Write Docstrings in Python](https://realpython.com/how-to-write-docstrings-in-python/)
* [Quick Tip: Documenting CircuitPython Programs On Your Computer](https://www.woolseyworkshop.com/2023/04/19/quick-tip-documenting-circuitpython-programs-on-your-computer/)
Build your documentation with [Sphinx](https://www.sphinx-doc.org/en/master/) using a [theme](https://github.com/readthedocs/sphinx_rtd_theme) provided by [Read the Docs](https://about.readthedocs.com/)

## Managing Python Testing
### Python Testing

## Managing Python Debugging
### Python Debugging











# Python Static Analysis Tools

As projects grow in complexity, ensuring code quality and security becomes paramount.
There are many Python static analysis tools to choose from, but these are most helpful:

* [`black`](https://pypi.org/project/black/) uncompromising Python code formatter.
  It saves you from the minutiae of hand-formatting and freedom from nagging about formatting.
  Install `black` with `pip install black`.
  (**NOTE:** If you want to format Jupyter Notebooks, install with `pip install "black[jupyter]"`.)
* [`mypy`](https://mypy-lang.org/) is a static type checking tool.
  You can freely mix static and dynamic typing within a program,
  within a module or within an expression.
  No need to give up dynamic typing — use static typing when it makes sense.
  Install `mypy` with `pip install mypy`.
* [`ty`](https://realpython.com/python-ty/) is a static type checking tool.
  This new tool delivers a lightning-fast static type-checking experience in Python
  At the time of writing, `ty` is available as an early preview release.
  If you’d like to get familiar with a new, robust, and promising type checker in your personal projects, then by all means give ty a try!
* [`flake8`](https://pypi.org/project/flake8/) is a bundle of
  [`pyflakes`](https://pypi.org/project/pyflakes/), [`pycodestyle`](https://pypi.org/project/pycodestyle/),
  and [`mccabe`](https://pypi.org/project/mccabe/).
  It is faster than Pylint largely because Flake8 only examines the syntax tree of each file individually.
  Install `flake8` with `pip install flake8`.
* [`pylint`](https://www.pylint.org/) is a static code analyzer for Python 2 or 3.
  Pylint analyses your code without actually running it.
  It checks for errors, enforces a coding standard, looks for [code smells](https://en.wikipedia.org/wiki/Code_smell),
  and can make suggestions about how the code could be refactored.
  Its follows the [PEP 8 style guide for Python code](https://peps.python.org/pep-0008/)
  Install `pylint` with `pip install pylint`.
* [`ruff`](https://docs.astral.sh/ruff/) aims to be orders of magnitude faster than
  alternative tools while integrating more functionality behind a single, common interface.
  Its objective is to replace `black`, `flake8`, `pylint`, and more.
  Install `ruff` with `pip install ruff`.































---------------


* [Python 3 Cheat Sheet](https://scouv.lisn.upsaclay.fr/python-memento/memento-python3-en-latest.pdf)

* [Master the Art of Python Debugging With These Tips](https://thenewstack.io/master-the-art-of-python-debugging-with-these-tips/)
* [7 Python Debugging Techniques Every Beginner Should Know](https://www.kdnuggets.com/7-python-debugging-techniques-every-beginner-should-know)
* [How to Debug Common Python Errors](https://realpython.com/debug-python-errors/)

* [Python 10 minutes a day](https://python-10-minutes-a-day.rocks/)
* [Real Python Learning Paths](https://realpython.com/learning-paths/)
* [Python Engineer](https://www.python-engineer.com/posts/)
* [mCoding](https://www.youtube.com/@mCoding)

* [Creating Great README Files for Your Python Projects](https://realpython.com/readme-python-project/)



* [The Case for Makefiles in Python Projects (And How to Get Started)](https://www.kdnuggets.com/the-case-for-makefiles-in-python-projects-and-how-to-get-started)





# Python IDLE

Python IDLE is the default integrated development environment (IDE comes bundled with every Python installation,
helping you to start coding right out of the box.

* [Getting Started With Python IDLE](https://realpython.com/python-idle/)


# Python Development Environment / Dev Containerized Environment

If you have more than one Python project,
your going to want to setup separate development environments.
The very act of setting up these environments and maintaining them can be laborious,
even with the aid of Python's virtual environment tools.
And if your sharing a project with teammates,
you have to coordinate the environments across space & time.
A good remedy for this can be containerization of your Python development environment.

* [How to Manage Python Projects With pyproject.toml](https://realpython.com/python-pyproject-toml/)

* [Python Virtual Environments: A Primer](https://realpython.com/python-virtual-environments-a-primer/)

* [Don’t Manage Your Python Environments, Just Use Docker Containers](https://www.kdnuggets.com/manage-python-environments-docker-containers)
* [Setting Up a Great Python Dev Environment with Docker](https://dev.to/njoguu/setting-up-a-great-python-dev-environment-with-docker-2b01)
  * [GitHub: jamestthompson3/nvim-remote-containers](https://github.com/jamestthompson3/nvim-remote-containers)
* [How to Create a Great Local Python Development Environment with Docker](https://www.youtube.com/watch?v=6OxqiEeCvMI)
* [How To Use Docker To Make Local Development A Breeze](https://www.youtube.com/watch?v=zkMRWDQV4Tg)
* [Setting A Dockerized Python Environment — The Elegant Way](https://towardsdatascience.com/setting-a-dockerized-python-environment-the-elegant-way-f716ef85571d)
* [Learn the fundamentals of Docker packaging—in just one afternoon](https://pythonspeed.com/products/justenoughdockerpackaging/)

* [Containerized Python Development – Part 1](https://www.docker.com/blog/containerized-python-development-part-1/)
* [Containerized Python Development – Part 2](https://www.docker.com/blog/containerized-python-development-part-2/)
* [Containerized Python Development – Part 3](https://www.docker.com/blog/containerized-python-development-part-3/)

* [Development Containers](https://containers.dev/)
  * [Dev Containers for shareable dev environments](https://www.youtube.com/watch?v=jTNP0UUMmfs)
  * [Dev Containers Overview](https://www.youtube.com/playlist?list=PLj6YeMhvp2S7FFvNDj7ks7ndm0u69Ufrs)


# Nvim & Dev Container

* [Using Devcontainers to set up your development environment](https://dev.to/caduribeiro/using-devcontainers-to-set-up-your-development-environment-5fbp)
  * [Running Neovim with Devcontainers](https://dev.to/caduribeiro/running-neovim-with-devcontainers-2imn)
* [Devcontainer for Software Development (with NeoVim)](https://www.youtube.com/watch?v=FzINeQ92g3w)
* [Devcontainer support for Neovim](https://www.ensarsarajcic.com/blog/nvim-dev-container-intro/)
  * [Codeberg: esensar/nvim-dev-container](https://codeberg.org/esensar/nvim-dev-container)
* [GitHub: jamestthompson3/nvim-remote-containers](https://github.com/jamestthompson3/nvim-remote-containers)

---------------

# Python's -> Notation
In short, the "->" notation indicates a function’s return type in Python.

* [What Does -> Mean in Python Function Definitions?](https://realpython.com/what-does-arrow-mean-in-python/)

---------------


## The `.__doc__` Attribute
## The `help()` Function
## The `pydoc` Tool

---------------

# Learning Python

* [What Can I Do With Python?](https://realpython.com/what-can-i-do-with-python/)
* [How to Use Python: Your First Steps](https://realpython.com/python-first-steps/)
* [The Ultimate List of Python YouTube Channels](https://realpython.com/python-youtube-channels/)
* [Python Morsels](https://www.pythonmorsels.com/)
* [Python Tutorials 2025](https://www.youtube.com/playlist?list=PL4KX3oEgJcfd7I5KmEnUF7cTVqrvCPRDj)
* [Python Tutorials 2024](https://www.youtube.com/playlist?list=PL4KX3oEgJcfeKzc-v2nD-KzTSELlNyafC)


# Sometimes the Problem is Your Environment

* [Linux Crisis Tools](https://www.brendangregg.com/blog/2024-03-24/linux-crisis-tools.html)

# Python Continuous Integration

* [Python Continuous Integration and Deployment Using GitHub Actions](https://realpython.com/courses/cicd-github-actions/)

# Debugging Tools & Techniques

[Debugging](https://en.wikipedia.org/wiki/Debugging) is the process of looking for the root causes of defects (aka bugs) in software after they’ve been discovered,
as well as taking steps to fix them.

* [Debugging Vs Printing](https://hackaday.com/2025/09/11/debugging-vs-printing/)
* [Stepping Up Your Python Printf Debugging Game](https://hackaday.com/2018/02/12/stepping-up-your-python-printf-debugging-game/)
* [30 Must-Know Tools for Python Development](https://www.kdnuggets.com/2025/02/nettresults/30-must-know-tools-for-python-development)

* [breakpoint: debugging in Python](https://www.pythonmorsels.com/debugging-with-breakpoint/)
* [Syntax Error #11: Debugging Python](https://www.syntaxerror.tech/syntax-error-11-debugging-python/)
* [Debugging 101: Replace print() with icecream ic()](https://www.youtube.com/watch?v=JJ9zZ8cyaEk)
* [Debug Your Python Code Efficiently with IceCream Package: 10 Advanced Examples to Replace Print Statements](https://medium.com/@danielwume/debug-your-python-code-efficiently-with-icecream-package-10-advanced-examples-to-replace-print-820fef801cb0)
* [Debugging with ice cream in Python](https://www.geeksforgeeks.org/python/debugging-with-ice-cream-in-python/)
* [Your Guide to the Python print() Function](https://realpython.com/python-print/)

* [Understanding the Python Mock Object Library](https://realpython.com/python-mock-library/)

* [Testing with Python (part 1): the basics](https://www.bitecode.dev/p/testing-with-python-part-1-the-basics)
* [Testing with Python (part 2): moving to pytest](https://www.bitecode.dev/p/testing-with-python-part-2-moving)
* [Testing with Python (part 3): pytest setup](https://www.bitecode.dev/p/testing-with-python-part-3-pytest)
* [Testing with Python (part 4): why and what to test?](https://www.bitecode.dev/p/testing-with-python-part-4-why-and)
* [Testing with Python (part 5): the different types of tests](https://www.bitecode.dev/p/testing-with-python-part-5-the-different)
* [Testing with Python (part 6): Fake it...](https://www.bitecode.dev/p/testing-with-python-part-6-fake-it)
* [Testing with Python (part 7): ...until you make it](https://www.bitecode.dev/p/testing-with-python-part-7-until)


# Python's Built-in Debugger pdb

* [Python Debugging With pdb: Overview](https://realpython.com/lessons/python-debugging-pdb-overview/)
* [Python Debugging With pdb](https://realpython.com/courses/python-debugging-pdb/)


# ViperIDE

* An Innovative MicroPython / CircuitPython IDE for Web and Mobile - [GitHub: vshymanskyy/ViperIDE](https://github.com/vshymanskyy/ViperIDE)

* [How to write code for your Raspberry Pi Pico in your web browser with ViperIDE](https://www.tomshardware.com/raspberry-pi/raspberry-pi-pico/how-to-write-code-for-your-raspberry-pi-pico-in-your-web-browser-with-viperide)


# Error / Exception Handling
* [Python Exceptions: An Introduction](https://realpython.com/python-exceptions/)
* [Python's raise: Effectively Raising Exceptions in Your Code](https://realpython.com/python-exceptions/)
* [Handling or Preventing Errors in Python: LBYL vs EAFP](https://realpython.com/courses/handling-preventing-errors-lbyl-eafp/)


# IPython & Jupyter & JupyterLab

[IPython](https://ipython.org/) is an alternative interactive interpreter to the standard Python interpreter that ships with the language.
The standard interpreter is useful for testing out small snippets of code and learning the language, but its functionality is basic. IPython adds a lot of features that are useful if you make much more extensive use of interactive Python.

IPython enhances Python's interactive mode with syntax highlighting and magic commands.
It offers built-in help, tab completion, and the ability to run system commands within Python.
You can log sessions for review, further enhancing IPython's functionality.

One of IPython's spinoffs is the popular notebook interface [Jupyter](https://jupyter.org/), which is popular in scientific computing.
Jupyter is available in two flavors: the standard Jupyter Notebook and JupyterLab. The latter is intended to be a fuller-featured version, similar to an IDE. The Jupyter project even deprecated the older Jupyter and put it into maintenance mode, but eventually pulled the original Jupyter out of mothballs and maintains both simultaneously due to its continuing popularity.

* [Why IPython is Better Than the Standard Python Interpreter](https://www.howtogeek.com/why-ipython-is-better-than-the-standard-python-interpreter/)
* [How to Get Started Creating Interactive Notebooks in Jupyter](https://www.howtogeek.com/how-to-get-started-creating-interactive-notebooks-in-jupyter/)
* [JupyterLab Documentation](https://jupyterlab.readthedocs.io/en/latest/#)


# DIY Python Debugger

* [Roll Your Own Python Debugger](https://hackaday.com/2023/11/11/roll-your-own-python-debugger/)

* [Let’s create a Python Debugger together: Part 1](https://mostlynerdless.de/blog/2023/09/20/lets-create-a-python-debugger-together-part-1/)
* [Let’s create a Python Debugger together: Part 2](https://mostlynerdless.de/blog/2023/10/06/lets-create-a-python-debugger-together-part-2/)
* [Let’s create a Python Debugger together: Part 3 (Refactoring)](https://mostlynerdless.de/blog/2023/11/06/lets-create-a-python-debugger-together-part-3-refactoring/)
* [Let’s create a Python Debugger together: Part 4 (Python 3.12 edition)](https://mostlynerdless.de/blog/2023/11/10/lets-create-a-python-debugger-together-part-4-python-3-12-edition/)
* [Let’s create a Python Debugger together: Tiny Addendum (exec and **name**)](https://mostlynerdless.de/blog/2023/11/14/lets-create-a-python-debugger-together-tiny-addendum-exec-and-__name__/)
* [Let’s create a Python Debugger together: PyData Talk](https://mostlynerdless.de/blog/2023/11/17/lets-create-a-python-debugger-together-pydata-talk/)


# Mutable & Immutable Types

* [Differences Between Python's Mutable and Immutable Types](https://realpython.com/courses/differences-mutable-immutable-types/)


# Manhole

Manhole is in-process service that will accept unix domain socket connections and present the stacktraces for all threads and an interactive prompt. It can either work as a python daemon thread waiting for connections at all times or a signal handler (stopping your application and waiting for a connection).

* [Manhole](https://pypi.org/project/manhole/)
* [Manhole Documentation](https://python-manhole.readthedocs.io/en/stable/)
* [A Python prompt into a running process: debugging with Manhole](https://pythonspeed.com/articles/live-debugging-python/)


# Testing Strategies & Tools

* [Python unittest Module](https://realpython.com/ref/stdlib/unittest/)
* [Debugging](https://realpython.com/lessons/debugging/)
* [Jupyter Notebook Debugging](https://realpython.com/lessons/jupyter-debugging/)
* [Simpler Debugging With F-Strings](https://realpython.com/lessons/simpler-debugging-f-strings/)
* [Python's assert: Debug and Test Your Code Like a Pro](https://realpython.com/python-assert-statement/)
* [4 Techniques for Testing Python Command-Line (CLI) Apps](https://realpython.com/python-cli-testing/)
* [Debugging Code With Decorators](https://realpython.com/lessons/debugging-code-decorators/)
* [pytest tricks: parametrize twice](https://calmcode.io/course/pytest-tricks/parametrize-twice)
* [Welcome to pytest-benchmark’s documentation!](https://pytest-benchmark.readthedocs.io/en/latest/)

# Benchmarking
* [Benchmarking MicroPython](https://blog.miguelgrinberg.com/post/benchmarking-micropython)


---------------


# Python C Extensions

* [Building a Python C Extension Module](https://realpython.com/build-python-c-extension-module/)
* [When C extensions crash: easier debugging for your Python application](https://pythonspeed.com/articles/python-c-extension-crashes/)
* [Production-ready Docker packaging for Python developers](https://pythonspeed.com/docker/)
* [Multi-stage builds #1: Smaller images for compiled code](https://pythonspeed.com/articles/smaller-python-docker-images/)
* [Multi-stage builds #2: Python specifics](https://pythonspeed.com/articles/multi-stage-docker-python/)
* [Multi-stage builds #3: Speeding up your builds](https://pythonspeed.com/articles/faster-multi-stage-builds/)


---------------


# Regular Expressions Using Python

A regex is a special sequence of characters that is used to extract part of a string, or detect a particular string pattern.
Regular expressions have become an integral part of natural language processing (NLP) and are very useful in the fields of text processing, information extraction and more.

There are some special characters in the field of regular expressions,
which help us perform different tasks.
These are:

```text
\ - drop special meaning of char
[] - represents a character class/set of characters
^ - Beginning of an expression
$ - Ending of an expression
. - Any character except the new line character (‘\n’)
| - Means OR - Matches with characters that are separated by it
? - Matches zero or One occurrence (Verifies whether the given character is there or not)
* - If the given character occurred zero or more times
+ - If the given character occurred one or more times
{}- The number occurrences of a preceding regex needed to match
()- Used to enclose a group of Regex
\ - To remove the special values of these characters
```

* [Working with Regular Expressions Using Python](https://www.opensourceforu.com/2025/01/working-with-regular-expressions-using-python/)
* [Python RegEx](https://www.w3schools.com/python/python_regex.asp)
* [Python RegEx](https://www.geeksforgeeks.org/regular-expression-python-examples/)
* [10 Python Regular Expression Tricks You Need to Master](https://levelup.gitconnected.com/10-python-regular-expression-tricks-you-need-to-master-7ba83104cf1c)
* [How to Replace a String in Python](https://realpython.com/replace-string-python/)


---------------


# Python Concurrency

* [Python's asyncio: A Hands-On Walkthrough](https://realpython.com/async-io-python/)
* [Deep Dive into Multithreading, Multiprocessing, and Asyncio](https://towardsdatascience.com/deep-dive-into-multithreading-multiprocessing-and-asyncio-94fdbe0c91f0)
* [Python Concurrency: Threads, Processes, and asyncio Explained](https://newvick.com/python-concurrency/)


---------------


# How Python Works

* [How Python Works](https://www.youtube.com/playlist?list=PLJ_usHaf3fgNFfY4CN6-A3zYplVVqnbv2)


## How to Write Pythonic Code

Pythonic describes code that doesn’t just get the syntax right but uses the language in the way it’s intended to be used. Here’s how to optimize your Python code.

* [How to Write Pythonic Code](https://builtin.com/data-science/pythonic)
* [Python for Loops: The Pythonic Way](https://realpython.com/python-for-loop/)
* [Python Oddities That Might Surprise You](https://www.kdnuggets.com/python-oddities-might-surprise-you)

## What is Python's .**dict** For?
* [Working With Python's .**dict** Attribute](https://realpython.com/courses/working-dict-attributes/)

## What Is Python's `__slot__` For?
What if there is a way to make your Python code faster?
`__slots__` in Python can improve the performance of your code while reducing the memory usage.

* [What Does Python’s **slots** Actually Do?](https://www.kdnuggets.com/what-does-pythons-__slots__-actually-do)

## What Is Python's `__init__.py` For?
* [What Is Python's **init**.py For?](https://realpython.com/python-init-py/)

## What Is Python's `__repr__.py` For?
Weekly Python tip: always implement `__repr__` in your classes
* [Python's 2 different string representations](https://www.pythonmorsels.com/pythons-two-different-string-representations/)

## Making a Main Function

In Python, there's a way to ask, are we being run from the command-line or being imported as a module?
Or put another way, is our current Python module the entry point to our Python process?
This question can be asked using the statements like this:

```python
def main():
    .
    .
    .

if __name__ == "__main__"
    main()
```

If you need to make a single Python file that can both be **used as a module** (i.e. is being imported)
and can be **run as a Python script** to do something,
you can check the variable `__name__` in your module to see whether it's equal to the string `"__main__"`.

When ever we run a file, Python automatically creates `__name__`, `__main__`, `__file__`, `__doc__`, etc.
These special variables are called "Dunders", which is short for double underscore.

* [Defining a main function in Python](https://www.pythonmorsels.com/making-main-function-python/)
* [Python if **name** == '**main**': Visually Explained](https://www.youtube.com/watch?v=KZpYtNtGxSU)


## Python's Built-in Functions

Python has many built-in functions that you can use directly without importing anything.
These functions cover a wide variety of common programming tasks that include performing math operations,
working with built-in data types, processing iterables of data, handling input and output in your programs, working with scopes, and more.

* [Python's Built-in Functions: A Complete Exploration](https://realpython.com/preview/python-built-in-functio/)


## Building Your Own Functions

* [Defining Your Own Python Function](https://realpython.com/defining-your-own-python-function/)
* [Using Python Optional Arguments When Defining Functions](https://realpython.com/python-optional-arguments/)


## Python Idioms (Idiomatic Python)

* Being Pythonic
  * [Python Name-Main Idiom Quiz](https://realpython.com/quizzes/python-name-main-idiom/)
  * [5 Good Python Habits](https://www.youtube.com/watch?v=I72uD8ED73U)
  * [A forbidden Python technique to put ANYTHING in a dict or set](https://www.youtube.com/watch?v=NpdNDTncxwA)
  * [**new** vs **init** in Python](https://www.youtube.com/watch?v=-zsV0_QrfTw)
* Python Keywords
  * [Python Keywords: An Introduction](https://realpython.com/python-keywords/)
* Newbe Bad Habits
  * [25 nooby Python habits you need to ditch](https://www.youtube.com/watch?v=qUeud6DvOWI)
  * [21 MORE nooby Python habits](https://www.youtube.com/watch?v=E8NijUYfyus)


## Python Scope

In programming, the scope of a name defines the region of a program where you can unambiguously access that name, which could identify a variable, constant, function, class, or any other object.
Nearly all programming languages use the concept of scope to avoid name collisions and unpredictable behavior.
Python resolves names using what’s known as the **LEGB rule**, which defines the order in which the interpreter searches through distinct scopes. The letters in this acronym stand for Local, Enclosing, Global, and Built-in.

* [Python Scope and the LEGB Rule: Resolving Names in Your Code](https://realpython.com/python-scope-legb-rule/)

## Python Objects

* Magic Methods
  * [Please Master This MAGIC Python Feature...](https://www.youtube.com/watch?v=qqp6QN20CpE&t=23s)
  * [Magic Methods - Making Python builtins work with your classes](https://www.youtube.com/watch?v=Zl-Vb1OIhCk)
  * [Python's Magic Methods in Classes](https://realpython.com/courses/magic-methods-classes/)
  * [Magic Methods: The Secret to Elegant Python Code](https://thenewstack.io/magic-methods-the-secret-to-elegant-python-code/)
  * [Understanding Python’s Iteration and Membership: A Guide to **contains** and **iter** Magic Methods](https://www.kdnuggets.com/understanding-pythons-iteration-and-membership-a-guide-to-__contains__-and-__iter__-magic-methods)
  * [Efficient Iterations With Python Iterators and Iterables](https://realpython.com/courses/efficient-iterations-iterators-iterables/)
  * [Asynchronous Iterators and Iterables in Python](https://realpython.com/python-async-iterators/)
  * [Using Python's .**dict** to Work With Attributes](https://realpython.com/python-dict-attribute/)
* Classes
  * [Python's Instance, Class, and Static Methods Demystified](https://realpython.com/instance-class-and-static-methods-demystified/)
  * [Metaclasses in Python](https://www.youtube.com/watch?v=yWzMiaqnpkI)
  * [Python dataclasses will save you HOURS, also featuring attrs](https://www.youtube.com/watch?v=vBH6GRJ1REM)
  * [Which Python @dataclass is best? Feat. Pydantic, NamedTuple, attrs...](https://www.youtube.com/watch?v=vCLetdhswMg)
  * [What Are Mixin Classes in Python?](https://realpython.com/python-mixin/)
  * [Lists vs Tuples in Python](https://realpython.com/python-lists-tuples/)
  * [Exploring Python's tuple Data Type With Examples](https://realpython.com/courses/exploring-tuple-data-type-examples/)
  * [How to Remove Items From Lists in Python](https://realpython.com/remove-item-from-list-python/)
* Descriptors
  * [8 things in Python you didn't realize are descriptors](https://www.youtube.com/watch?v=mMbVs17Vmo4)
* Generators
  * [Python Generators](https://youtu.be/tmeKsb2Fras?si=h7bXVCyo8zEcs1jU)
* Sets
  * [Using Sets in Python](https://realpython.com/courses/sets-python/)
* Decorators
* Enumerations
  * [Building Enumerations With Python's enum](https://realpython.com/courses/python-enum/)
* Pointers
  * [unique_ptr: C++'s simplest smart pointer](https://www.youtube.com/watch?v=AmjoK55h68Y)
* Strings
  * [Python f-strings can do more than you thought. f'{val=}', f'{val!r}', f'{dt:%Y-%m-%d}'](https://www.youtube.com/watch?v=BxUxX1Ku1EQ)
  * [str vs bytes in Python](https://www.youtube.com/watch?v=EimoZHDcQMA)
  * [String Interpolation in Python: Exploring Available Tools](https://realpython.com/python-string-interpolation/)
  * [Python 3.14 Preview: Template Strings (T-Strings)](https://realpython.com/python-t-strings/)
* Structural Pattern Matching
  * [Using Structural Pattern Matching in Python](https://realpython.com/courses/structural-pattern-matching/)
* Copying of Python Objects
  * [Shallow vs Deep Copying of Python Objects](https://realpython.com/python-copy/)


# Python Type Checking

* [Python Type Checking (Guide)](https://realpython.com/python-type-checking/)


## Duck Typing

Python makes extensive use of a type system known as duck typing.
The system is based on objects’ behaviors and interfaces.
Many built-in classes and tools support this type system,
which makes them pretty flexible and decoupled.

* [Getting Started With Duck Typing (Overview)](https://realpython.com/videos/duck-typing-python-overview/)


## Python Best Practices

* Speedup
  * [Unlocking your CPU cores in Python (multiprocessing)](https://www.youtube.com/watch?v=X7vBbelRXn0)
  * [The Fastest Way to Loop in Python - An Unfortunate Truth](https://www.youtube.com/watch?v=Qgevy75co8c)
  * [The Python Global Interpreter Lock - Explained](https://www.youtube.com/watch?v=XVcRQ6T9RHo)
  * [Understanding Python's Global Interpreter Lock (GIL)](https://realpython.com/courses/understanding-global-interpreter-lock-gil/)
  * [Intro to async Python | Writing a Web Crawler](https://www.youtube.com/watch?v=ftmdDlwMwwQ)
* Parallel Iteration
  * [Using the Python zip() Function for Parallel Iteration](https://realpython.com/python-zip-function/)
* Performance Profiling
  * [Diagnose slow Python code. (Feat. async/await)](https://www.youtube.com/watch?v=m_a0fN48Alw)
* Logging
  * [Logging in Python](https://realpython.com/python-logging/)
  * [How to Use Loguru for Simpler Python Logging](https://realpython.com/python-loguru/)
  * [Modern Python logging](https://www.youtube.com/watch?v=9L77QExPmI0)
  * [Logging in Python: A Developer’s Guide](https://blog.sentry.io/logging-in-python-a-developers-guide/)
  * [Eliot: Logging that tells you why it happened](https://eliot.readthedocs.io/en/stable/)
* Unit Testing
  * [unittest: Python’s Built-In Safety Net for Developers](https://thenewstack.io/unittest-pythons-built-in-safety-net-for-developers/)
  * [Python's unittest: Writing Unit Tests for Your Code](https://realpython.com/python-unittest/)
  * [pytest Framework](https://docs.pytest.org/)
* Infrastructure Testing
  * [Infrastructure testing with Testinfra](https://philpep.org/blog/infrastructure-testing-with-testinfra/)
  * [Using Testinfra with Ansible to verify server state](https://opensource.com/article/19/5/using-testinfra-ansible-verify-server-state)
  * [testinfra/pytest delights](https://medium.com/@george.shuklin/testinfra-pytest-delights-3e0a7d5c84d2)
  * [Choosing between testinfra and Ansible for tests](https://medium.com/opsops/choosing-between-testinfra-and-ansible-for-tests-e52a9329b3ec)
  * [Testinfra](https://testinfra.readthedocs.io/en/latest/)
* Automated Testing
  * [Automated Testing in Python with pytest, tox, and GitHub Actions](https://www.youtube.com/watch?v=DhUpxWjOhME)
* Code Quality
  * [Python Code Quality: Best Practices and Tools](https://realpython.com/python-code-quality/)


## Asterisks in Python

* [Asterisks in Python: what they are and how to use them](https://treyhunner.com/2018/10/asterisks-in-python-what-they-are-and-how-to-use-them/)


## List & Dictionary Comprehension in Python

List  & dictionary comprehension is a way to create these object using a concise syntax.
It allows us to generate a new list/dictionaries by applying an expression to each item in an existing iterable (such as a list or range).
This helps us to write cleaner, more readable code compared to traditional looping techniques.

* [List Comprehension in Python](https://www.geeksforgeeks.org/python-list-comprehension/)
* [Python Dictionary Comprehension](https://www.geeksforgeeks.org/python-dictionary-comprehension/)
* [Building Dictionary Comprehensions in Python](https://realpython.com/courses/building-dictionary-comprehensions/)


---------------


# Profiling / Timing Code

* [Python Timer Functions: Three Ways to Monitor Your Code](https://realpython.com/python-timer/)


---------------



# Bitwise Operators in Python
* [Bitwise Operators in Python](https://realpython.com/python-bitwise-operators/)



---------------

# Python's Walrus Operator

* [The Walrus Operator: Python's Assignment Expressions](https://realpython.com/python-walrus-operator/)


# Python's Import Statement

The Python `import` statement lets you read (aka copy) a module into your code.
A module, sometimes called packages, is any file that contains
classes, functions, and values that you can reference from your program.
In short, Python modules are `.py` files that contain Python code.

We could import the Python `time` module and make use of the `sleep()` function via the following code:

```python
import time

time.sleep(3)
```

The above `import` statement allows you to import all the functions from a module into your code.
Often, though, you’ll only want to import a few functions, or just one.
that can be done via:

```python
from random import choice

fruits = ["Apple", "Pear", "Banana"]
print(choice(fruits))
```

The default name given to modules in your code is the name of the module.
However, you can override the default module name using the `as` keyword.

```python
import tkinter as tk

window = tk.Tk()
```


# What Is the **pycache** Folder?

* [What Is the **pycache** Folder in Python?](https://realpython.com/python-pycache/)


---------------

# Python Modules

* Itertools - Itertools is a module in python, it is used to iterate over data structures that can be stepped over using a for-loop. Such data structures are also known as iterables. This module incorporates functions that utilize computational resources efficiently.
  * [itertools — Functions creating iterators for efficient looping](https://docs.python.org/3/library/itertools.html)
  * [What are itertools in Python?](https://www.educative.io/answers/what-are-itertools-in-python)
  * [Python Itertools](https://www.geeksforgeeks.org/python-itertools/)
  * [The FULL Guide To Itertools For Python Developers](https://www.youtube.com/watch?v=baZpqVmR488)
  * [Looping in Python](https://www.pythonmorsels.com/screencasts/looping/)
  * [The Iterator Protocol](https://www.pythonmorsels.com/iterator-protocol/)
  * [Lazy Looping: The Next Iteration](https://treyhunner.com/lazy-looping/resources.html)

* pathlib - Use for nearly all file-related code in Python, especially when you need to construct or deconstruct file paths or ask questions of file paths.
  * [Python's pathlib Module: Taming the File System](https://realpython.com/python-pathlib/)
  * [Python's pathlib module](https://www.pythonmorsels.com/pathlib-module/)


# Role of Underscore

* [Role of Underscore(\_) in Python Tutorial](https://www.datacamp.com/tutorial/role-underscore-python)
* [Single and Double Underscore Naming Conventions in Python](https://realpython.com/courses/single-double-underscore-naming-conventions/)


---------------

# TOML Files
TOML stands for Tom's Obvious, Minimal Language.
Its human-readable syntax makes TOML convenient to parse into data structures across various programming languages.
In Python, you can use the built-in `tomllib` module to work with TOML files.
TOML plays an essential role in the Python ecosystem.

## pyproject.toml
`pyproject.toml` is crucial for package configuration and specifies the build system and dependencies. Modern Python projects use pyproject.toml files to describe a project's metadata, dependencies, and other valuable attributes.

## settings.toml
`settings.toml` file serves as a dedicated location for storing configuration variables and sensitive information, particularly for network-connected devices. This method **does not** make them secure. It only separates them from the code.

* [Python and TOML: New Best Friends](https://realpython.com/python-toml/)
* [How to Manage Python Projects With pyproject.toml](https://realpython.com/python-pyproject-toml/)
* [Adafruit CircuitPython: Environment Variables](https://docs.circuitpython.org/en/latest/docs/environment.html)
* [TOML: A config file format for humans](https://toml.io/en/)

---------------


# Python Versioning



---------------


---------------


# Build a Python Command-Line App

Example programs that make heavy use of Python's commandline utilities.

* [Build a Command-Line App with Python in 7 Easy Steps](https://www.kdnuggets.com/build-a-command-line-app-with-python-in-7-easy-steps)
* [A Simple Command-Line TO-DO List App](https://github.com/balapriyac/python-projects/tree/main/command-line-app)
* [Build a Command-Line To-Do App With Python and Typer](https://realpython.com/python-typer-cli/)
* [Manage Your To-Do Lists Using Python and Django](https://realpython.com/django-todo-lists/)


---------------


# Basic Input / Output

* [Basic Input and Output in Python](https://realpython.com/python-input-output/)


---------------


# Python Graphical User Interfaces (GUI)
* [Python GUI's With TKinter](https://www.youtube.com/playlist?list=PLCC34OHNcOtoC6GglhF3ncJ5rLwQrLGnV)
* [Building a Python GUI Application With Tkinter](https://realpython.com/courses/building-gui-application-tkinter/)
* [Modern Tkinter Design With CustomTkinter](https://www.youtube.com/playlist?list=PLfZw_tZWahjxJl81b1S-vYQwHs_9ZT77f)
* [My Example](https://github.com/jeffskinnerbox/ll-tracker/blob/master/tkrdecoder.py)


# Gradio
Gradio is an open-source Python library that simplifies the creation of
user-friendly web interfaces for machine learning models, APIs, or any Python function.

* [Introduction to Gradio for Building Interactive Applications](https://pyimagesearch.com/2025/02/03/introduction-to-gradio-for-building-interactive-applications/)

# Textual
The lean application framework for Python. Build sophisticated user interfaces with a simple Python API. Run your apps in the terminal and a web browser.

* [Textual](https://www.textualize.io/)
  * [GitHub: Textualize/textual](https://github.com/Textualize/textual)



---------------


# Pickle Module

In Python, the `pickle` module lets you serialize and deserialize data.
Essentially, this means that you can convert a Python object into a stream of bytes
and then reconstruct it (including the object’s internal structure)
later in a different process or environment by loading that stream of bytes.

* [Exploiting Python pickles](https://davidhamann.de/2020/04/05/exploiting-python-pickle/)


# Python Text Formatting
Rich is a Python library for rich text and beautiful formatting in the terminal.
The Rich API makes it easy to add color and style to terminal output.
Rich can also render pretty tables, progress bars, markdown, syntax highlighted source code, tracebacks, and more — out of the box.

* [Rich’s documentation](https://rich.readthedocs.io/en/latest/#)
  * [pip install rich](https://pypi.org/project/rich/)
  * [GitHub: Textualize/rich](https://github.com/Textualize/rich)
  * [Pretty terminal output with Python and Rich](https://calmcode.io/course/rich/introduction)
  * [The Python Rich Package: Unleash the Power of Console Text](https://realpython.com/python-rich-package/)


---------------


# Web Scraping With Scrapy and MongoDB

* [Web Scraping With Scrapy and MongoDB](https://realpython.com/web-scraping-with-scrapy-and-mongodb/)


---------------


# Check for Issues with Dependencies

[`deptry`](https://deptry.com/) is a command line tool to check for issues with dependencies in a Python project, such as unused or missing dependencies.
It supports the following types of projects:

* Projects that use [Poetry](https://python-poetry.org/) and a corresponding pyproject.toml file
* Projects that use [PDM](https://pdm-project.org/latest/) and a corresponding pyproject.toml file
* Projects that use any package manager that strictly follows [PEP 621](https://peps.python.org/pep-0621/) dependency specification
* Projects that use a `requirements.txt` file according to the [pip](https://pip.pypa.io/en/stable/user_guide/) standards

* [Make a 2D Side-Scroller Game With PyGame](https://realpython.com/courses/pygame-primer/)
* [Build Conway's Game of Life With Python](https://realpython.com/conway-game-of-life-python/)
* [Build a Python Turtle Game: Space Invaders Clone](https://realpython.com/preview/build-python-turtle-game-space-invaders-clone/)


---------------


# Build a Python Script

* [How Can You Structure Your Python Script?](https://realpython.com/python-script-structure/)
* [Executing commands safely from Python](https://supakeen.com/weblog/executing-commands-safely-from-python/)
* [You should put this in all your Python scripts | if **name** == '**main**': ...](https://www.youtube.com/watch?v=g_wlZ9IhbTs)
* [Execute Your Python Scripts With a Shebang](https://realpython.com/courses/execute-python-scripts-with-shebang/)


---------------



[01]:https://realpython.com/python-uv/
[02]:https://realpython.com/what-is-pip/
[03]:https://realpython.com/python-pipx/
[04]:https://pypi.org/project/pip-tools/2.0.1/
[05]:https://realpython.com/dependency-management-python-poetry/
[06]:https://realpython.com/intro-to-pyenv/
[07]:https://realpython.com/pypi-publish-python-package/
[08]:https://realpython.com/python-virtual-environments-a-primer/
[09]:https://realpython.com/ruff-python/
[10]:https://realpython.com/python-pep8/
[11]:https://black.readthedocs.io/en/stable/
[12]:https://trunk.io/formatters/python/isort
[13]:https://www.pydocstyle.org/en/stable/
[14]:https://medium.com/top-python-libraries/pyupgrade-easily-upgrade-your-code-to-the-latest-python-syntax-0b42fdf8122f
[15]:https://www.packetcoders.io/production-pimping-your-python-code-with-autoflake/
[16]:https://www.freecodecamp.org/news/how-to-setup-virtual-environments-in-python/
[17]:https://dennisokeeffe.medium.com/how-pydoc-helps-your-python-development-df0b186ad96e
[18]:https://realpython.com/python-uv/#locking-and-syncing-the-environment

