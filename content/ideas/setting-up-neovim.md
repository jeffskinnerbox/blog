<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.1
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


------



* [Build A Portable Development Environment With Nix Package Manager](https://www.youtube.com/watch?v=70YMTHAZyy4)




The majority of my inspiration came from the following sources:

* The Cult of Vim (or Vi)
    * [Vim from the ground up](https://thevaluable.dev/vim-commands-beginner/)
    * [Vim Best Practices For IDE Users](https://betterprogramming.pub/50-vim-mode-tips-for-ide-users-f7b525a794b3)
* General Guidance - How to structure you files, etc.
    * [Better Neovim plugin setup! Use Packer, break your init.lua into modules, look like a hero!](https://www.youtube.com/watch?v=NkfMBI1tVwY)
    * [How to Set up Neovim for Windows and Linux with Lua and Packer](https://dev.to/slydragonn/how-to-set-up-neovim-for-windows-and-linux-with-lua-and-packer-2391)
    * [Getting Started with Neovim](https://bryankegley.me/posts/nvim-getting-started/)
* Themes & Color Schemes
    * [The BEST Neovim color themes; some with support for Terminals and the latest Lua plugins](https://www.youtube.com/watch?v=_evGrg4l3CY)
* As an IDE
    * [Learn How To Use NeoVim As an IDE](https://programmingpercy.tech/blog/learn-how-to-use-neovim-as-ide/)
    * [Configure Mason Nvim - Portable Package Manager For Neovim](https://www.youtube.com/watch?v=2iczAXDdgTE&list=PLIHtvvGZ1O3jBXdp9Id02vRuOEOWIGB_w&index=9)
    * [Configuring Language Server Protocol in Neovim](https://blog.codeminer42.com/configuring-language-server-protocol-in-neovim/)
* NeoVim Tutorials - Comprehensive source of tutorials and ideas
    * Alpha2Phi
        * [Learn Neovim The Practical Way](https://alpha2phi.medium.com/learn-neovim-the-practical-way-8818fcf4830f)
        * https://github.com/alpha2phi
        * [Learn Neovim The Practical Way: All articles on how to configure and program Neovim](https://alpha2phi.medium.com/learn-neovim-the-practical-way-8818fcf4830f)
        * [Neovim Tips for a Better Coding Experience](https://alpha2phi.medium.com/neovim-tips-for-a-better-coding-experience-3d0f782f034e)
    * Christian Chiarulli (aka Chris@Machine)
        * [Christian Chiarulli](https://www.chrisatmachine.com/) Creator and lead maintainer of 🌙 LunarVim
            * [Configuring Neovim](https://www.youtube.com/watch?v=qb6fPgZMRF4&list=PLIHtvvGZ1O3jBXdp9Id02vRuOEOWIGB_w)
            * [Neovim Configuration](https://www.youtube.com/playlist?list=PLsz00TDipIffxsNXSkskknolKShdbcALR)
            * [Neovim from Scratch](https://www.youtube.com/playlist?list=PLhoH5vyxr6Qq41NFL4GvhFp-WLd5xzIzZ)
                * [Neovim from scratch](https://github.com/LunarVim/Neovim-from-scratch)
                * [LunarVim](https://www.lunarvim.org/)
* Example Configurations
    * [Neovim from scratch](https://github.com/LunarVim/Neovim-from-scratch)
    * [A Basic Stable IDE config for Neovim](https://github.com/LunarVim/nvim-basic-ide)

Sources:

* Vim vs. NeoVim
    * [Compare NeoVim vs Vim: Which Editor is Best for You?](https://www.sysprobs.com/compare-neovim-vs-vim-best-editor)
    * [7 Reasons Why Developers Prefer NeoVim Over Vim](https://linuxhandbook.com/neovim-vs-vim/)
    * [Why Neovim is so much better than Vim now... (Neovim vs Vim)](https://www.youtube.com/watch?v=qQvFC0wRiRE)
* NeoVim
    * [Meet Neovim](http://vimcasts.org/episodes/meet-neovim/)
    * [Neovim][04]
    * [How to Install Neovim on Ubuntu 22.04][05]
    * [How I Setup Neovim On My Mac To Make It Amazing - Complete Guide](https://www.youtube.com/watch?v=vdn_pKJUda8)
    * [Everything you need to know to configure neovim using lua](https://vonheikemen.github.io/devlog/tools/configuring-neovim-using-lua/)
    * [Configuring Neovim With Lua (It's Easy!)](https://www.youtube.com/watch?v=m62UCkdQ8Ck)
    * [Build your first Neovim configuration in lua](https://vonheikemen.github.io/devlog/tools/build-your-first-lua-config-for-neovim/)
* Vim-plug
    * [How to Install Plugins in Neovim](https://linuxopsys.com/topics/install-plugins-in-neovim)
    * [Vim-plug: A Minimalist Vim Plugin Manager](https://www.ostechnix.com/vim-plug-a-minimalist-vim-plugin-manager/)
    * [VIM Plug – The easy way to install plugins in VIM](https://www.linuxfordevices.com/tutorials/linux/vim-plug-install-plugins)
* NeoVim and Lua Referance Docs
    * [Nvim Documentation](https://neovim.io/doc/)
    * [Nvim Documentation: Lua](https://neovim.io/doc/user/lua.html)
    * [Nvim Documentation: Options](https://neovim.io/doc/user/options.html)
    * [Lua][16]
* NeoVim Plugins
    * [Awesome Neovim](https://github.com/rockerBOO/awesome-neovim)
    * [neovimcraft](https://neovimcraft.com/)













# Project Structure
If you want to load Lua files on demand, you can place them in the `lua`
directory in your [`runtimepath`](https://neovim.io/doc/user/options.html#'runtimepath')
default is `~/.config/nvim/lua`)
and load them with a `require` statement.

* [How I Setup Neovim Plugins With Lua](https://www.youtube.com/watch?v=jREkuPTResw)
* [Lua User Guide: Lua modules](https://neovim.io/doc/user/lua-guide.html#lua-guide)

This is where your nvim configuration lives: - https://www.chrisatmachine.com/posts/01-ide-crash-course
namespace

~/.config/nvim/
├── init.lua                           - entry point for `nvim` to access your configuration files
├── lua                                - in your runtime path
│   ├── active                         - my namespace directory for the currently 'active' nvim configuration
│   │   ├── auto.lua
│   │   ├── key-mapping.lua
│   │   ├── options.lua
│   │   ├── plugins.lua
│   │   └── configs
│   │       ├── comment.lua
│   │       ├── indent-blankline.lua
│   │       ├── lightline.lua
│   │       ├── nightfox.lua
│   │       ├── nvim-tree.lua
│   │       └── toggleterm.lua
├── plugin
│   └── packer_compiled.lua
├── swap
└── undo

The configuration structure is relatively simple:

* `init.lua`: the entry point for `nvim` to access your configuration files
* `lua/`: the directory where all the `nvim` lua code and plugin config goes
* `lua/active`: a namespace to avoid collisions with other plugins and lua modules
* `lua/active/core`:
* `lua/active/configs`:
* `lua/active/lsp`: lsp is complicated enough to warrant it’s own separate directory
* `lua/active/lsp/settings`: specific settings for your Language Server, to find more settings for your language server read more [here](https://github.com/neovim/nvim-lspconfig/blob/master/doc/server_configurations.md)

You will find plugins here under `~/.local/share/nvim/site/pack/packer`.
You will also find other useful plugin data

cache: `~/.cache` You can find logs here

state: `~/.local/state` You can find state about Neovim as well as other plugins here







* [Our favorite fonts for the Linux terminal](https://opensource.com/article/23/4/linux-terminal-fonts)





I started my professional career using the [line editor Ed][01] as my goto terminal-based fle editor
This is when I was using a [TI Silent 700][21] on my office desk, and at home,
using it acoustic coupler on a phone line conditioned for 1200 BPS data.
In time, I moved up to a [VT100][22] terminal and the [visual editor Vi][02],
which had many backward compatible commands with Ed,
but gave a full screen to navigate & display instead of just a single text line.
When the enhancement support for Vi became somewhat iffy,
[Vim (aka Vi Improved)][03] was created to improve and extend the existing Vi editor.
Similarly, [NeoVim (aka New Vim][04] was created to refactor and improve the existing Vim editor
but outwardly NeoVim is just like Vim.
You can find a little ed & vi history [here][24] and [here][25].

Vim & NeoVim offers a wide range of editing options and commands
but out-of-the-box, they lacks some of the features of a modern text editor.
This is because Vim is a minimal program and is minimalist by design.
It is meant to run on machines with low computing and storage.
But this does not mean we cannot have extra features in Vim & NeoVim.
There is a vast community of Vim / NeoVim users with many plugins
that can help us customize Vim / NeoVim and its functionalities to your liking.

Vim & NeoVim now have a native plug manager call [Vim-Plug][09],
and even better one ([Packer][18]) targetting NeoVim,
giving me a strong incentive to move off of my current plug manager, [Pathogen][07].
Truth be told, you do not need a plugin manager to install plugins in Vim.
There is a well-known way to install vim without any plugin manager.
But the Vim-Plug & Packer plugin managers can do more than just download packages.
It can control versions of your packages, install / update / rollback packages if required,
and create shallow clones to minimize disk space usage and download time.

## Compare NeoVim vs Vim
Vim and NeoVim are both powerful text editing tools excelling in different ways.
When people come to Linux for the first time, they get confused about which one to get.
For me, these are the compelling things that drive me towards NeoVim:

* NeoVim performs better than Vim out of the box due to a better configuration system, robust API, and plugin architecture.
* Vim uses Vimscript as the default for writing scripts. In NeoVim, you also have Lua natively.
Vimscript is much slower than Lua and lets you use a new class of plugins like Telescope and Treesitter on NeoVim.
* NeoVim benefits from the libuv library that ensures a small codebase. It enables asynchronous I/O operations, meaning the main thread won’t be blocked when performing multiple operations.
* One of the main goals of NeoVim developers was to make it much more extensible than the original Vim.
* Unlike Vim, NeoVim doesn’t need to support lots of widget toolkits for GUI interfaces. Instead, it implements GUI through external clients thanks to msgpack-rpc API.

### Convert Vimscript to Lua
* [Configuring Neovim With Lua (It's Easy!)](https://www.youtube.com/watch?v=m62UCkdQ8Ck)

### Vim as an IDE
Visual Studio Code (commonly referred to as VS Code)
is a source-code editor made by Microsoft with the Electron Framework, for Windows, Linux and macOS.
Features include support for debugging, syntax highlighting, intelligent code completion,
snippets, code refactoring, and embedded Git.

* [Debugging In Neovim (ft BashBunni)](https://www.youtube.com/watch?v=0moS8UHupGc)
* [Vim: Vim as an IDE (VimConf 2020 Talk)](https://www.youtube.com/watch?v=Gs1VDYnS-Ac)
* [3 Reasons Why I Switched to Neovim from VSCode](https://www.youtube.com/watch?v=5zR--Fj56Ho)

## Scripting: Vimscript vs Lua
When it comes to customizing my Vim user experience,
one of my goals is to retire my use of the obscure [Vimscript][15], as used in Vim,
and replace it with the well established [Lua][16] scripting within NeoVim.
Another goal is to improve my use of packages within Vim.
My current Vim configuration is fragile with some hidden conflicts among the packages.
NeoVim promises to provide better package management.

## NeoVim Plugins

### plugins for plugin package management
[Packer][57] GitHub repository [wbthomason/packer.nvim][18]

* [The Lazy Way in Neovim: From Packer to Lazy.nvim](https://www.youtube.com/watch?v=2ahI8lYUYgw)
* [Migrating from Packer.nvim to Lazy.nvim](https://www.youtube.com/watch?v=aqlxqpHs-aQ)
* [Zero to IDE with LazyVim](https://www.youtube.com/watch?v=N93cTbtLCIM)
* [GitHub: LazyVim / LazyVim](https://github.com/LazyVim/LazyVim)

### plugins for icons & eye-candy
* XXX DaikyXendo/nvim-material-icon
* XXX nvim-tree/nvim-web-devicons

### plugins for theme & color scheme
### plugins for useful tools
### plugins for quick edit of comments
### plugins for popup help
#### Key Mappings and WhichKey
* [WhichKey](https://alpha2phi.medium.com/neovim-for-beginners-key-mappings-and-whichkey-31dbf58f9f87) [folke/which-key.nvim](https://github.com/folke/which-key.nvim) - WhichKey is a lua plugin for Neovim 0.5 that displays a popup with possible keybindings of the command you started typing.
* [Neovim for Beginners — Key Mappings and WhichKey](https://alpha2phi.medium.com/neovim-for-beginners-key-mappings-and-whichkey-31dbf58f9f87)
### other plugins
* [Boost Your Neovim Experience with These Essential Plugins](https://livecode247.com/boost-your-neovim-experience-with-these-essential-plugins#heading-additional-resources)
* [Neovim and Tree-sitter: An Overview with Examples](https://thevaluable.dev/tree-sitter-neovim-overview/)
packer.nvim
telescope.nvim
nvim-treesitter
nvim-lspconfig
nvim-cmp
null-ls
LuaSnip
nvim-tree
Bufferline [akinsho/bufferline.nvim](https://github.com/akinsho/bufferline.nvim)
Lualine


# Learning the Basics
[How to Install and Set Up Neovim for Code Editing](https://mattermost.com/blog/how-to-install-and-set-up-neovim-for-code-editing/)
If you’ve never used Vim, Neovim, or Lua before,
then you might want to check out the following guides:

* **[Learn Vim in Y Minutes][12] -** This tutorial will quickly walk you through the basics of using Vim (and therefore Neovim).
* **[Learn Lua in Y Minutes][13] -** This tutorial will introduce the syntax for the Lua programming language.
* **[Understand NeoVim Modes][14] -** This tutorial show you how to navigate the Normal, Insert, Visual, and Command-Line modes.

Many tutorials that have been written are geared towards users who are
new to Neovim but have used Vim in the past.
These tutorials show how to transition one’s configuration from the Vimscript file init.vim to the Neovim file init.lua.



-----



# NeoVim and Tree-sitter
[Tree-sitter][AA] is a general parser generator tool and an incremental parsing library.
It enables you to generate concrete syntax tree from any language it supports.
You can use it to build a concrete syntax tree for a source file
and efficiently update the syntax tree as the source file is edited.
The official site has a [full list of the supported languages and parsers][BB].

The GitHub site [nvim-treesitter/nvim-treesitter][CC] contains the NeoVim plugin
for the `nvim` text editor.

[AA]:https://tree-sitter.github.io/tree-sitter/
[BB]:https://tree-sitter.github.io/tree-sitter/#language-bindings
[CC]:https://github.com/nvim-treesitter/nvim-treesitter

Sources:

* [Introductory To Treesitter](https://teknologiumum.com/posts/introductory-to-treesitter)
* [GitHub: tree-sitter/tree-sitter](https://github.com/tree-sitter/tree-sitter)
* [Neovim and Tree-sitter: An Overview with Examples](https://thevaluable.dev/tree-sitter-neovim-overview/)
* [Neovim 101 — Tree-sitter](https://alpha2phi.medium.com/neovim-101-tree-sitter-d8c5a714cb03)


-----



# Setup Test Environment

## VirtualBox
[VirtualBox][30] is a [full virtualization][31] x86 / AMD64 / Intel64 hardware architecture
(contrast this with [hardware-assisted virtualization][32]).
It creates a [virtual machine (VM)][33], aka an emulation of a computer system.
Virtual machines (VM) behave like a separate computer system,
complete with virtual hardware devices.
The VM runs as a process in a window on your current operating system.
You can boot an operating system installer disc (or live CD) inside the virtual machine,
and the operating system will be “tricked” into thinking it’s running on a real computer.
It will install and run just as it would on a real, physical machine.

## VBoxManage
[VBoxManage][34] is the command-line interface to Oracle VM VirtualBox.
With it, you can completely control Oracle VM VirtualBox from the command line of your host operating system.
It exposes all the features of the virtualization engine,
even those that cannot be accessed from the GUI.

## Vagrant
[Vagrant][35] is a tool that offers a simple and easy to use
command-line client for managing virtual environments.
It effective provides a single common management UI for many of the popular virtualization platforms, including VirtualBox.
I started using it because it made it easier for me to
standup new software solutions for testing without disrupting my working system.

Vagrant is a tool for building and managing virtual machine environments in a single workflow.
Vagrant has an easy-to-use workflow, makes automation easy, and lowers development environment setup time.
Machines are provisioned on top of VirtualBox, VMware, AWS, or any other provider.
Then, industry-standard provisioning tools such as
shell scripts, Chef, or Puppet, can automatically install
and configure software on the virtual machine.

**For developers**, Vagrant will isolate dependencies and their configuration within a
single disposable, consistent environment, without sacrificing
any of the tools you are used to working with (editors, browsers, debuggers, etc.).
Once you or someone else creates a single [Vagrantfile][36],
you just need to `vagrant up` and everything is installed and configured for you to work.

**For DevOps**, Vagrant gives you a disposable environment
and consistent workflow for developing and testing infrastructure management scripts.
You can quickly test things like shell scripts, Chef cookbooks, Puppet modules,
and more using local virtualization such as VirtualBox or VMware.
Then, with the same configuration, you can test these scripts
on remote clouds such as AWS or RackSpace with the same workflow.

So the high level difference between these two is VirtualBox is the creator of virtual machines
and Vagrant is a manager of the virtual machines environment.
Also, Vagrant and Docker suport different types of virtualisation.
Vagrant is related to virtual machines and Docker is a virtual environment tool.

Aside from reading [Vagrant's official documentation][37],
it also helps to know some of the basic terminology used by Vagrant:

* **Vagrant Box:**
A box is basically a package containing a representation of a virtual machine running a specific operating system.
To be more simple, it is a base image of any Operating System or Kernel. It may be for a specific Provider.
* **Providers:**
The Provider is the piece of software responsible for creating and managing the virtual machines used by Vagrant.
The main providers are Virtualbox and VMware, but the default one is VirtualBox, since it's free and open source.
* **Provisioners:**
Provisioner will do some task(s) using the vm instance already provided.
The provisioners are used to set up the virtual server, installing all necessary software and executing different tasks. The most used provisioners are: Puppet, Chef and Ansible.
Shell Script is also a very common option. You can find more information about vagrant provisioners here.
* **The Vagrantfile:**
The basic vagrant configuration is based in one file, the Vagrantfile. It shall be placed in your repository root.
In this file you will define which base box you want - a box is, basically,
a package with an operational system to be run in your virtual machine.

## Ansible
You may have heard of using configuration management tools
like [Chef][38], [Puppet][39], [SaltStack][40], [Terraform][41], [CFEngine][42]
or simply using Bash scripts to provision servers or Vagrant Boxes.
The major difference between other configuration management tools and Anisble,
is that underneath Ansible is just SSH.
Chef and Puppet both have dependencies that must be installed
on the server before you can use them, Ansible does not.
[Ansible is agentless][43] — meaning there are no daemons or agents needed to run a particular action.
It runs on a machine apart from from your VMs
and uses SSH to connect to the servers and run the required commands.
Hence it is a push model, meaning no additional installs are not required at the end point VMs.

Why not just use Bash scripts, then?
Ansible has an edge over Bash scripts because
it features an goal-oriented resource model that
describes the desired state of computer systems and services,
not the paths to get them to this state.
No matter what state a system is in, Ansible understands how to transform it to the desired state.
Ansible is a simple to understand [configuration management approach][44].

Ansible just uses a list of tasks to run in YAML2 format.
Ansible also comes with [idempotency][45] out of the box.
That means you can run the same operation numerous times,
and the output will remain consistent
(i.e. it won't do something twice unless you ask it to).
You can write Bash scripts this way, but it requires quite a bit more overhead.

One important feature in Ansible is that a playbook describes a
desired state in a computer system,
so a playbook can be run multiple times against a server without impacting its state.
If a certain task has already been implemented (e.g., "user system already exists"),
then Ansible simply ignores it and moves on.

* **Tasks:** A task is the smallest unit of work.
It can be an action like "Install a database," "Install a web server,"
"Create a firewall rule," or "Copy this configuration file to that server."
* **Plays:** A play is made up of tasks. For example, the play
"Prepare a database to be used by a web server" is made up of tasks
(1) Install the database package,
(2) Set a password for the database administrator,
(3) Create a database; and 4) Set access to the database.
* **Playbook:** A playbook is made up of plays.
A playbook could be "Prepare my website with a database backend" and the plays would be
(1) Set up the database server,
(2) Set up the web server.
* **Roles:** Roles are used to save and organize playbooks and allow sharing and reuse of playbooks.
Following the previous examples, if you need to fully configure a web server,
you can use a role that others have written and shared to do just that.
Since roles are highly configurable (if written correctly),
they can be easily reused to suit any given deployment requirements.
* **Ansible Galaxy:** Ansible Galaxy is an online repository where roles are uploaded so they can be shared with others. It is integrated with GitHub, so roles can be organized into Git repositories and then shared via Ansible Galaxy.

#### Step X: Create Your Directory Structure - DONE
I not only want to create a virtual machine with Vagrant to perform my NeoVim experimentation,
but also setup a directory where I can keep all my documentation and tools permanently.

```bash
# create your working directory
mkdir -p ~/src/test-env/nvim
cd ~/src/test-env/nvim

# create a directory for ansible playbooks
mkdir -p ~/src/test-env/nvim/playbooks
```

#### Step X: Create Your Vagrant Test Environment - DONE
Now create your Vagrantfile within `~/src/test-env/nvim/Vagrantfile`.
That file is listed below:

```
<---- Vagrantfile
```

While in `~/src/test-env/nvim`,
you create your virtual machine for NeoVim testing by executing `vagrant up`.
Once this process completes, you can validate your virtual machine is ready by
`vagrant ssh` which should log you into the machine.

OMake sure to update the static IP addresss in the `Vagrantfile`.
This virtual machine is configured with a static IP address (`192.168.1.250`)
since this is required for smooth operation of Ansible.
You'll also notice that the `Vagrantfile` also supplies a SSH key which will be
used by Ansible to gain access to perfrom its provisioning task.

#### Step X: Establish the Ansible Playbooks
Create the following files to support Ansible:

##### Inventory File - DONE
Establish the `inventory` file which will be used by all the Ansible Playbooks:

```
<---- Inventory File
```

##### Ping & Query Playbooks - DONE
Create a `ping.yml` playbook so you can easily valiate the virtual machine is up
and the SSH keys are working:

```
<---- Ping Playbook
```

```
<---- Query Playbook
```

```bash
# run the playbooks
ansible-playbook -i inventory ping.yml
ansible-playbook -i inventory query.yml
```



-----


# Install Baseline NeoVim
# Enhance NeoVim with Basic Capabilities
# Enhance NeoVim with IDE Packages




#### Step 0: Uninstalling nvim for Clean Start - DONE
If you are installing NeoVim for the first time,
you can skip this step, but if your reinstalling or rebuilding NeoVim,
this is an important step.
What is done below is to backup your current `~/.config/nvim`,
but equally important, you have to back (or delete)
your `~/.local/share/nvim` and `~/.local/state/nvim`.

Doing this might become necessary after a package upgrade
or some major editing of NeoVim's configuration files.

```bash
# make a backup of your current nvim folder
mv ~/.config/nvim ~/.config/nvim_bak

# clean neovim folders - optional but recommended
mv ~/.local/state/nvim ~/.local/state/nvim.bak
mv ~/.local/share/nvim ~/.local/share/nvim.bak
mv ~/.cache/nvim ~/.cache/nvim.bak

# a full clean-up, requiring a re-install of everything
trash ~/.cache/nvim ~/.local/state/nvim ~/.local/share/nvim ~/.config/nvim/undo ~/.config/nvim/site ~/.config/nvim/swap ~/.config/nvim/plugin

# edit all files
nvim -p ~/.config/nvim/init.lua ~/.config/nvim/lua/active/* ~/.config/nvim/lua/active/configs/*

# browse neovim logs
```

#### Step X: Install NeoVim on Ubuntu - DONE
The Neovim version available on your operating system repository
(see "[How to Install Neovim on Ubuntu 22.04][05]")
is not always the latest available version.
To install the absolute latest stable version of Neovim,
you must [download it from Github][06] and then install it manually
As of April 2023, this NeoVim version was at 0.9.0.
For Ubuntu, this version is avalible only as an [AppImage][23] or source code.

To install a potential more stable, but less current, version on NeoVim,
you can use Canonical [Snap Store's][19] version (install method documented [here][20]).
To install NeoVim via the Snap Store:

```bash
# neovim nightly & stable are available on the snap store

# stable builds
sudo snap install --beta nvim --classic

# nightly builds
sudo snap install --edge nvim --classic

# to update snap package for neovim
sudo snap refresh nvim

# to uninstall neovim
sudo snap remove nvim
```

>**NOTE:** The `snapd` daemon handles all the updates for snaps installed on a Linux system.
>Once a snap is installed, `snapd` daemon will automatically keep it up to date.
>This is done by regularly checking for updates from the snap store and installing any available updates.
>`sudo snap refresh --time` will give you the time of the last update.

A not so current as the Snap Store, but stable version can be obtained
via a Personal Package Archive (PPA) installation.
Neovim is available on PPA and you can install Neovim using the `apt` package manager.
PPA has both stable and unstable versions that Neovim support.
The following links list the currently available stable versions of Neovim:
`https://launchpad.net/~neovim-ppa/+archive/ubuntu/stable`.

To install NeoVim via PPA, do the following:

```bash
# install the software-properties-common package to enable the use of the add-apt-repository function
sudo apt install software-properties-common

# add the ppa repository on your Ubuntu computer
sudo add-apt-repository ppa:neovim-ppa/stable

# update the ppa repository to get a list of the most recent versions
sudo apt update

# install the latest available stable version of neovim
sudo apt install neovim

# check the version number of neovim
$ nvim --version
NVIM v0.8.3
```

**If you need to uninstall NeoVim**,
use the following procedure:

```bash
# uninstall neovim and all its dependent files
sudo apt -y autoremove neovim

# remove all the configurations and data of neovim
sudo apt -y purge neovim
```

#### Step X: Create a NeoVim Test Environment - DONE
I want to test NeoVim versions and plugins,
but I know that there will be issues where I'll need to start over from scratch.
To make this journey easier, I'm choosing a directory structure and file conventions
that takes its into consideration.

The directory structure used by NeoVim always starts within `$HOME/.config`.
The key controlling file for NeoVim execution is `$HOME/.config/nvim/init.lua`
and the contents of `$HOME/.config/nvim/lua/active`.
There may be other sub-directories within `$HOME/.config/nvim/lua`
but `init.lua` references only the `active` sub-directory.
Any other sub-directories (if they are present) are alternative configuration for NeoVim
that can be made 'active' but changing their directory name.
All the other sub-directories of `$HOME/.config/nvim` will be created by NeoVim itself
or its package manager (in my case Packer).

I can make use of this 'active' convention by changing references to 'active'
in the `init.lua` file, effectively changing the configuration of NeoVim
with very little effort.

The target directory structure is illustrated below:

```
$HOME/.config/
└── nvim
    ├── init.lua
    └── lua
        └── active
            ├── key-mapping.lua
            ├── options.lua
            ├── plugins.lua
            └── vars.lua
```

I can create this initial directory structure via:

```bash
# remove any existing neovim configuration directory
trash ~/.config/nvim

# create a new neovim configuration directory
mkdir -p ~/.config/nvim/lua/active

# create the initial neovim files (all void at this time)
touch ~/.config/nvim/init.lua
cd ~/.config/nvim/lua/active
touch key-mapping.lua options.lua plugins.lua vars.lua
```

#### Step X: Configure NeoVim
Now that I got Neovim running,
it’s time to start customizing your config files.
Many tutorials are geared towards users who are new to Neovim but have used Vim in the past.
In other words, a lot of tutorials show how to transition one’s configuration from the Vimscript file `init.vim`
to the Neovim file `init.lua`.
I'm going to take advantage of Lua’s position as a first-class language inside Neovim
and build config files using this language from the start.

MORE MORE MORE

Sources:

* REMOVE [Neovim Configuration for Beginners](https://builtin.com/software-engineering-perspectives/neovim-configuration)
* [How to Install and Set Up Neovim for Code Editing](https://mattermost.com/blog/how-to-install-and-set-up-neovim-for-code-editing/)
* [Turning Neovim into a Full-Fledged Code Editor with Lua](https://mattermost.com/blog/turning-neovim-into-a-full-fledged-code-editor-with-lua/)

##### Setup Initialization File
Create your `~/.config/nvim/init.lua` file in your Neovim configuration directory.

```bash
# create a very basic init.lua file
mkdir -p ~/.config/nvim/basic/lua

# create the files for a very basic nvim experience
nvim -p ~/.config/nvim/init.lua ~/.config/nvim/lua/basic/auto.lua ~/.config/nvim/lua/basic/key-mapping.lua ~/.config/nvim/lua/basic/options.lua ~/.config/nvim/lua/basic/plugins.lua
```

Now enter the following in the `~/.config/nvim/init.lua` file:

```lua
```

ETC, ETC, ETC

#### Step X: Install Vim-plug / Packer Plugin Managers
A plugin is a way to extend `vim` functionality and
this is where the combination of Neovim + Lua really shines.
The first thing you’ll need is a plugin manager (e.g. [Vim-plug][17] and [Packer][18]).
While it’s possible to manually install these plugins yourself,
it’s much simpler to use a tool that can take care of installing, updating, and removing packages on your behalf.

`vim` categorizes plugins into "global" plugins (which load and operate unconditionally)
and "filetype" plugins (which only load and operate for specific file types).
`vim` looks for plugins in specific locations,
in your home directory at `~/.vim/plugin`,
assuming you have not altered the runtime path.
You can change this location manually or via plugins like [Pathogen][07] or [Vundle][08].

To install plugins, you must first declare them in Vim / NeoVim configuration file.
The configuration file for ordinary Vim is `~/.vimrc`
and the config file for NeoVim is `~/.config/nvim/init.vim`.



You can install tons of plugins for your `vim`,
but choosing the plugins you want from the plugin directory is the essential step.
For Vim, there is a website called [Awesome Vim][10] that provides a gist of all these plugins in a single place.
For NeoVim, xxxxxx
It is generally a good option to check if the plugin is maintained properly
and has no key binding conflict with other installed plugins.

##### Step X: Install Packer Plugin Mananger

```bash
# pre requisites for vim plug
sudo apt install git

# install the packer plug manager - for neovim - https://github.com/wbthomason/packer.nvim
git clone --depth 1 https://github.com/wbthomason/packer.nvim \
    ~/.config/nvim/site/pack/packer/start/packer.nvim
```

This should create a new folder `~/.config/nvim/site` in your Neovim configuration directory.
You can take a look at all of the new files and folders created in this directory with `tree ~/.config`.
This is where Packer will install and configure any plugins you specify.

Now you’ll need to tell NeoVim that it should use the Packer plugin for plugin management.
In your `~/.config/nvim/lua` subdirectory,
open a new file in NeoVim called `plug.lua` and add the following lines of code:

```lua
-- [[ plug.lua ]]

return require('packer').startup(function(use)
  -- [[ Plugins Go Here ]]
end,
config = {
  package_root = vim.fn.stdpath('config') .. '/site/pack'
})
```

>**NOTE:** The double dots, i.e., `..`, is the Lua syntax for string concatenation.

This code block says to load the Packer module each time NeoVim is started.
It also sets the `package_root` to the location where you cloned the Packer repository.

Next, uncomment the line that imports your plugins module in your `~/config/nvim/init.lua`
file so it looks like this:

```lua
--[[ init.lua ]]

-- LEADER
-- These keybindings need to be defined before the first /
-- is called; otherwise, it will default to "\"
vim.g.mapleader = ","
vim.g.localleader = "\\"

-- IMPORTS
require('vars')      -- Set Variables
require('opts')      -- Set Options
require('keys')      -- Key Mappings
require('plug')      -- Plugins
```

#### PackerCommands
https://github.com/wbthomason/packer.nvim
packer provides the following commands after you've run and configured packer with require('packer').startup(...):

```lua
-- You must run this or `PackerSync` whenever you make changes to your plugin configuration
-- Regenerate compiled loader file
:PackerCompile

-- Remove any disabled or unused plugins
:PackerClean

-- Clean, then install missing plugins
:PackerInstall

-- Clean, then update and install plugins
-- supports the `--preview` flag as an optional first argument to preview updates
:PackerUpdate

-- Perform `PackerUpdate` and then `PackerCompile`
-- supports the `--preview` flag as an optional first argument to preview updates
:PackerSync

-- Show list of installed plugins
:PackerStatus

-- Loads opt plugin immediately
:PackerLoad completion-nvim ale
```


#### Step X: Install Your First Plugins
To install plugins,
you must first declare them in Vim or NeoVim configuration file as shown below.
The configuration file for ordinary Vim is `~/.vimrc`
and the configuration file for Neovim is `~/.config/nvim/init.vim`.
Also, when declaring the plugins in the configuration file,
the list should start with `call plug#begin(<PLUGIN_DIRECTORY>)` and end with `call plug#end()`.

To get started, let us install [`lightline.vim`][11] plugin.
To do so, add the following lines on top of your `~/.config/nvim/init.vim` file.

```lua
-- lightline.vim - https://github.com/itchyny/lightline.vim
call plug#begin('~/.config/nvim/plugins')
Plug 'itchyny/lightline.vim'                -- light & configurable statusline/tabline plugin for vim
call plug#end()
```

After adding the above lines in NeoVim configuration file,
perform the following on the NeoVim command line:

```bash
# reload the configuration file
#:source ~/.vimrc
:source ~/.config/nvim/init.vim

# check the plugin status
:PlugStatus

# install the plugins that you have declared in the config file earlier
:PlugInstall

# to update plugins, run
:PlugUpdate
```

#### Step X: Review / Remove / Rollback Plugins
Some times, the updated plugins may have new bugs or no longer work correctly.
To fix this, you can simply rollback the problematic plugins.

```bash
# to review the changes from the last :PlugUpdate
:PlugDiff

#  roll each plugin back to the previous state, before the update, by pressing X on each paragraph
```

To remove a plugin delete or comment out the plug commands
that you have added earlier in your NeoVim configuration file.
Then do the following:

```bash
# reload the configuration file
# OR restart Vim editor
#:source ~/.vimrc
:source ~/.config/nvim/init.vim

# run the following command to uninstall the plugins
:PlugClean
```

To upgrade the vim-plug itself, type:

```bash
# upgrade the vim plugins
:PlugUpgrade
```


------


# Do Health Checkgg
execute `:checkhealth` and fix an problems found

* [CheckHealth in Neovim](http://vimcasts.org/episodes/neovim-checkhealth/)



------



# Nvimtree (aka Nvim-Tree)
Nvimtree is a Neovim plugin to browse the file system and other tree like structures in whatever style suits you, including sidebars, floating windows, split style, file icons or all of them at once!

replace `:netrw`

* [Neovim for Beginners — File Explorer](https://alpha2phi.medium.com/neovim-for-beginners-file-explorer-a0b2e5cf6c57)
* [Neovim - NvimTree File Explorer Written In Lua](https://www.youtube.com/watch?v=SpexCBrZ1pQ)
* [GitHug: nvim-tree/nvim-tree.lua](https://github.com/nvim-tree/nvim-tree.lua)
* [GetHub: nvim-tree/nvim-web-devicons](https://github.com/nvim-tree/nvim-web-devicons)
* [GetHub: nvim-tree/nvim-tree](https://github.com/nvim-tree/nvim-tree.lua)

Alternative is [nvim-neo-tree/neo-tree.nvim](https://github.com/nvim-neo-tree/neo-tree.nvim)
[How to Set up Neovim for Windows and Linux with Lua and Packer](https://dev.to/slydragonn/how-to-set-up-neovim-for-windows-and-linux-with-lua-and-packer-2391)



------



# Adding Packages
* [numToStr / FTerm.nvim](https://github.com/numToStr/FTerm.nvim)
* A File Explorer For Neovim Written In Lua - [nvim-tree / nvim-tree.lua](https://github.com/nvim-tree/nvim-tree.lua)
* [folke / which-key.nvim](https://github.com/folke/which-key.nvim)
* [sainnhe / everforest](https://neovimcraft.com/plugin/sainnhe/everforest/index.html)
* [iamcco / markdown-preview.nvim](https://github.com/iamcco/markdown-preview.nvim)
* [ibhagwan / fzf-lua](https://github.com/ibhagwan/fzf-lua)

ToggleTerm
* [akinsho / toggleterm.nvim](https://github.com/akinsho/toggleterm.nvim)
* [Example Setup: toggleterm.lua](https://github.com/ChristianChiarulli/nvim/blob/master/lua/user/toggleterm.lua)
* [Neovim - Toggleterm | Open terminal programs in Neovim](https://www.youtube.com/watch?v=5OD-7h7gzxU)

Cheatsheet and Coding Assistant
* [toggleterm.nvim](https://github.com/akinsho/toggleterm.nvim)
* [Neovim for Beginners — Cheatsheet and Coding Assistant](https://alpha2phi.medium.com/neovim-for-beginners-cheatsheet-and-coding-assistant-137d5a15c934)
* [Neovim for Beginners — 3rd Party Tools](https://alpha2phi.medium.com/neovim-for-beginners-3rd-party-tools-c4a5148e501c)
* [Neovim 101 — Coding Assistant](https://alpha2phi.medium.com/neovim-101-coding-assistant-1df31c63913e)

Indent Blankline
* [lukas-reineke / indent-blankline.nvim](https://github.com/lukas-reineke/indent-blankline.nvim)

* Tree Sitter
* [tree-sitter / tree-sitter](https://github.com/tree-sitter/tree-sitter)
* [nvim-treesitter / nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter)



------



# Install Mason.nvim

* [Configuring Language Server Protocol in Neovim](https://blog.codeminer42.com/configuring-language-server-protocol-in-neovim/)
* [Learn How To Use NeoVim As an IDE](https://programmingpercy.tech/blog/learn-how-to-use-neovim-as-ide/)
    * [Configure Mason Nvim - Portable Package Manager For Neovim](https://www.youtube.com/watch?v=2iczAXDdgTE&list=PLIHtvvGZ1O3jBXdp9Id02vRuOEOWIGB_w&index=9)

[Mason.nvim][26] is a replacement for [nvim-lsp-installer][27] since it is no longer maintained.
Mason adds the ability to install and manage LSP servers, DAP servers, linters, and formatters.
It builds on top of the very same foundation as `nvim-lsp-installer` and writen in Lua,
but with a majority of internals refactored to improve extensibility and testability.

## Language Server Protocol (LSP)
The [Language Server Protocol (LSP)][28] is an open, JSON-RPC-based protocol for use
between source code editors or integrated development environments (IDEs)
and servers that provide programming language-specific features like code completion, syntax highlighting
and marking of warnings and errors, as well as refactoring routines.
The goal of the protocol is to allow programming language support to be implemented
and distributed independently of any given editor or IDE.

[williamboman/mason.nvim][26]           -- installer & manager of server LSP servers, DAP servers, linters, and formatters
[williamboman/mason-lspconfig.nvim][46] -- extension to mason.nvim that makes it easier to use lspconfig with mason.nvim
[neovim/nvim-lspconfig][29]             -- quickstart configs for nvim LSP
[jose-elias-alvarez/null-ls.nvim][47]   -- use neovim as a language server to inject LSP diagnostics, code actions, and more via Lua
[hrsh7th/nvim-cmp][48]                  -- completion engine plugin for neovim
[hrsh7th/cmp-nvim-lsp][49]              -- nvim-cmp source for neovim's built-in language server client

* [Neovim Tips for a Better Coding Experience](https://alpha2phi.medium.com/neovim-tips-for-a-better-coding-experience-3d0f782f034e)
* [Neovim LSP and DAP using Lua](https://alpha2phi.medium.com/neovim-lsp-and-dap-using-lua-3fb24610ac9f)
* [Basic Neovim LSP Setup - Treesitter + LSP + Completion](https://www.youtube.com/watch?v=Ku-m7eEbWas)
* [Neovim - Telescope: a highly extendable fuzzy finder](https://www.youtube.com/watch?v=OhnLevLpGB4)
    * [5 Terrific Neovim Telescope Extensions for 2022](https://www.youtube.com/watch?v=indguFY7wJ0)



------



# Install Glow
[Glow][52] is a terminal based markdown reader that renders markdown on the CLI.

```bash
# install glow on debian/ubuntu

# add the app key to the keyring
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://repo.charm.sh/apt/gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/charm.gpg

# install referances to the glow repository
echo "deb [signed-by=/etc/apt/keyrings/charm.gpg] https://repo.charm.sh/apt/ * *" | sudo tee /etc/apt/sources.list.d/charm.list

# install glow
sudo apt update && sudo apt install glow
```

There is also a Glow NeoVim plugin,
at Github repository [ellisonleao/glow.nvim][53],
that allow you to preview markdown code directly in your NeoVim terminal.



------



# NeoVim and Fonts
So you want to increase or decrease the font size, or change the font used, or what ever?
Maybe as easily as pressing `Ctrl +` or `Ctrl -` like in every other GUI application out there?
Not so!

Most Vim users still run `vim` (or `nvim`) from the command line, with a terminal emulator.
That is what I'm doing in this document.
But if you are running Vim inside of a terminal emulator,
the font isn’t controlled by Vim or NeoVim,
it is controlled by the terminal emulator, so look up the documentation for that.

For example, I am using GNOME Terminal.
In GNOME you can adjust the font size with `Ctrl Shift +` and `Ctrl -` and it just works.
(In other terminal emulators you can often hold Ctrl and scroll the mouse wheel to adjust font size).
See ["How to adjust the GUI font size in Vim or Neovim"][] if your using GUI Vim (aka `gvim`)
or one of the many graphical Neovim frontends.

## Types of Fonts
First, some font basics.
In general, fonts are divided into three classes namely Serif, Sans, and Mono.

 * **Serif** family fonts look "sharp" with its pointy "thorns" on every character (in Latin, serif).
Examples of Serif fonts are Times New Roman, Liberation Serif, and Apple Garamond.
 * **Sans** family fonts look "dull" without "thorns" (hence they're called sans-serif or no-thorns).
Example of Sans fonts are Arial, Liberation Sans, and Helvetica.
 * **Mono** family fonts look "square-y" also known as "typewriter" machine style.
Examples of Mono fonts are Courier New, Liberation Mono, and Monaco.

Furthermore, fonts also divided into two forms namely Bold and Italic (aka a "thick" and "slanted" writings).
As a result, you will find combinations in every single font,
divided into several files with each one serving a specific writing purpose.

Ubuntu bundled its own fonts,
and they are all Free Libre Open Source Software licensed (FLOSS).
The fonts included by default in Ubuntu are of course different to other operating systems.
On Ubuntu, fonts installation is located in two places:
User fonts - `~/.local/share/fonts/` and System fonts - `/usr/share/fonts/`.

## Install Nerd Fonts
The terminal version of NeoVim will use what ever your font your terminal is using.
So to implement your prefered font,
you’ll need to change the font of your terminal emulator.
In my case, this is gnome-terminal.

Nerd Fonts is a project that patches developer-targeted fonts with many [glyphs][54] ([icons][55]).
It includes [programming ligatures][56] and is designed to enhance the appearance of source code.
Nerd Fonts also includes additional broad range of glyphs giving geeks more eye candy.

```bash
# list all the available fonts
fc-list
```

```bash
# cloning the nerd fonts installation tool 'getnf'
cd ~/src
git clone https://github.com/ronniedroid/getnf.git
cd ~/getnf
./install.sh

# navigate into the nerd-font directory and install via provided installer script
cd ~/src/nerd-fonts
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
# using `gitnf`, install the following fonts:
# DejaVuSansMono, DroidSansMono, FiraCode, Inconsolata, Noto,
# RobotoMono, SourceCodePro, SpaceMono, Ubuntu, UbuntuMono, JetBrainsMono
FiraCode

# navigate to the directory containing the nerd fonts
```

* [Our favorite fonts for the Linux terminal](https://opensource.com/article/23/4/linux-terminal-fonts)

Once the font files are copied to these locations, you need to refresh system wide font cache to complete the installation. To do so, run the following command: `sudo fc-cache -vf ~/.local/share/fonts`.
The fonts in `~/.local/share/fonts` are available for all apps now.


To remove fonts installed on User directory:
Go to `~/.local/share/fonts/` and delete the files with `.ttf` or `.otf` extensions.
Repeat this step for each of the targetted fonts.

Sources

* [How to Install Nerd Fonts on Linux](https://bytexd.com/how-to-install-nerd-fonts-on-linux/)
* [How to Install Nerd Fonts on Linux](https://www.geekbits.io/how-to-install-nerd-fonts-on-linux/)
* [Nerd Fonts](https://www.nerdfonts.com/#home)
* [GitHub: ryanoasis/nerd-fonts](https://github.com/ryanoasis/nerd-fonts)
* [Add Icons to your Fonts with Nerd Fonts](https://www.youtube.com/watch?v=fR4ThXzhQYI)
* [Neovim 101 — Fonts](https://alpha2phi.medium.com/neovim-101-fonts-da575bd4eda9)
* [Installing system nerd-fonts with ansible](https://waylonwalker.com/ansible-install-fonts/)
    * [No More Missing Fonts | ansible-playbook](https://www.youtube.com/watch?v=2MEmsinxRK4)



------



# Using AstroNvim with NeoVim

Sources:

* [Neovim With AstroNvim | Your New Advanced Development Editor](https://www.youtube.com/watch?v=GEHPiZ10gOk)
* [Astro Vim - All in one Nvim config!!](https://www.youtube.com/watch?v=JQLZ7NJRTEo)
* [AstroNvim](https://astronvim.com/)

#### Step X: Backup NeoVim Files
```bash
# make a backup of your current nvim folder
mv ~/.config/nvim ~/.config/nvim.bak

# clean neovim folders - optional but recommended
mv ~/.local/share/nvim ~/.local/share/nvim.bak
mv ~/.local/state/nvim ~/.local/state/nvim.bak
mv ~/.cache/nvim ~/.cache/nvim.bak
```

#### Step X: Install and Confgure AstroNvim
```bash
# clone the astronvim repository
git clone --depth 1 https://github.com/AstroNvim/AstroNvim ~/.config/nvim
```


------


# Using Buffers, Windows, and Tabs Efficiently in Vim
* [Using buffers, windows, and tabs efficiently in Vim](https://dev.to/iggredible/using-buffers-windows-and-tabs-efficiently-in-vim-56jc#tabs)
* [Why do Vim experts prefer buffers over tabs?](https://stackoverflow.com/questions/26708822/why-do-vim-experts-prefer-buffers-over-tabs/26745051#26745051)

```bash
# create 3 buffers, one for each only one tab/window
vim file1 file2 file3

# create 3 buffers and each file in there own tab
vim -p file1 file2 file3
```

```vim
" turn buffers into tab page in neovim
:tab ball
```

# NeoVim Copy & Paste
Vi, Vim, and NeoVim have there own clipboard system meaning if you copy (aka 'yank' in `nvim`) something,
you won’t be able to just paste it in other apps because the clipboard is only available inside the editor.
There are many times when you want to copy & paste `nvim` to/from another application.
To do this, you must have access to your OS clipboard.

in Linux, you would think this is straight-forward, but it's not.
It depends on the window system that is being used: [Wayland][50] or [X11][51].

```bash
# environment variables & applications that provide information about your system's graphics environment

# check whether Wayland or Xorg is in use
echo $XDG_SESSION_TYPE

# check desktop envirnment
echo $XDG_CURRENT_DESKTOP

# displays the OS name, kernel version, hostname, display resolution, shell name
sudo apt install neofetch
neofetch
```

In my case, I'm running with X11.
For X11 window system, you need to install `xclip`
on both your source & target systems for the copy & paste.
you also need to set the 'clipboard' option as shown below:

```bash
# install `xclip` on both source & target systems
sudo apt install xclip
```

```lua
-- in the neovim `options.lua` file add
vim.o.clipboard = "unnamedplus"
```

With this, you should be able to copy & paste to/from non-NeoVim applications and `nvim`.
For me, the clipboard copy & paste keys are:
`"+y` (copy) and `"+p` (paste).

Also note there also appears to be an

```vim
" paste into vim by gnome-terminal's shortcut for paste.
<Ctrl>+<Shift>+v
```

https://stackoverflow.com/questions/67598285/cannot-paste-from-clipboard-in-neovim-nightly
Neovim doesn't have any code to access OS clipboard directly (or to process X Window events). Instead it delegates to external utilities/plugins. You're expected to execute :checkhealth command to see the current state. If you don't have any supported tool on your PATH then you'll not be able to access the clipboard.

As a shameless plug, I wrote [plugin](https://github.com/matveyt/neoclip) that consists of dynamic library providing direct access to clipboard. This is to avoid extra process creation for every copy/paste operation (btw. setting clipboard=unnamed[plus] is bad for more than just this single reason). However, the library must be built from source before use.

As of Wayland, its IPC mechanism is clearly different from X but at least in GNOME or KDE you may expect both selections being synchronized transparently. Otherwise you need specific utils to access Wayland clipboard, such as wl-copy/wl-paste.

Sources:

* [How to Check if You are Using Wayland or Xorg?](https://itsfoss.com/check-wayland-or-xorg/)
* [How to access OS clipboard in neovim](https://ramezanpour.net/post/2022/07/24/access-os-clipboard-in-neovim)
* [WSL NeoVim Copy & Paste](https://lloydrochester.com/post/vim/wsl-neovim-copy-paste/)



[01]:https://www.redhat.com/sysadmin/introduction-ed-editor
[02]:https://www.redhat.com/sysadmin/introduction-vi-editor
[03]:https://www.redhat.com/sysadmin/beginners-guide-vim
[04]:https://neovim.io/
[05]:https://linuxopsys.com/topics/install-neovim-ubuntu-and-plugins
[06]:https://github.com/neovim/neovim/releases/tag/stable
[07]:https://gist.github.com/romainl/9970697
[08]:https://linuxhint.com/installing_vim_vundle_plugin_ubuntu/
[09]:https://www.linuxfordevices.com/tutorials/linux/vim-plug-install-plugins
[10]:https://vimawesome.com/
[11]:https://github.com/itchyny/lightline.vim
[12]:https://learnxinyminutes.com/docs/vim/
[13]:https://learnxinyminutes.com/docs/lua/
[14]:https://hackernoon.com/understand-neovim-modes-once-and-navigate-them-like-a-pro-heres-how
[15]:https://learnvimscriptthehardway.stevelosh.com/
[16]:https://www.lua.org/docs.html
[17]:https://github.com/junegunn/vim-plug
[18]:https://github.com/wbthomason/packer.nvim
[19]:https://snapcraft.io/nvim
[20]:https://github.com/neovim/neovim/wiki/Installing-Neovim#snap
[21]:https://en.wikipedia.org/wiki/Silent_700
[22]:https://en.wikipedia.org/wiki/VT100
[23]:https://appimage.org/
[24]:https://en.wikipedia.org/wiki/Ed_(text_editor)
[25]:https://begriffs.com/posts/2019-07-19-history-use-vim.html#third-party-plugins
[26]:https://github.com/williamboman/mason.nvim
[27]:https://github.com/williamboman/nvim-lsp-installer
[28]:https://microsoft.github.io/language-server-protocol/
[29]:https://github.com/williamboman/mason-lspconfig.nvim
[30]:https://www.virtualbox.org/
[31]:https://www.virtualbox.org/wiki/Virtualization
[32]:https://en.wikipedia.org/wiki/Hardware-assisted_virtualization
[33]:https://en.wikipedia.org/wiki/Virtual_machine
[34]:https://docs.oracle.com/cd/E97728_01/E97727/html/vboxmanage-intro.html
[35]:https://www.vagrantup.com/
[36]:https://www.vagrantup.com/docs/vagrantfile/
[37]:https://www.vagrantup.com/docs/
[38]:https://www.chef.io/
[39]:https://puppet.com/
[40]:https://saltstack.com/
[41]:https://www.terraform.io/
[42]:https://cfengine.com/
[43]:https://medium.com/@cabot_solutions/ansible-and-docker-the-best-combination-for-an-efficient-software-product-management-28c86cfebe90
[44]:https://www.ansible.com/use-cases/configuration-management
[45]:https://stackoverflow.com/questions/1077412/what-is-an-idempotent-operation
[46]:https://github.com/williamboman/mason-lspconfig.nvim
[47]:https://github.com/jose-elias-alvarez/null-ls.nvim
[48]:https://github.com/hrsh7th/nvim-cmp
[49]:https://github.com/hrsh7th/cmp-nvim-lsp
[50]:https://wayland.freedesktop.org/
[51]:https://www.x.org/wiki/
[52]:https://github.com/charmbracelet/glow
[53]:https://github.com/ellisonleao/glow.nvim/tree/main
[54]:https://en.wikipedia.org/wiki/Glyph
[55]:https://en.wikipedia.org/wiki/Icon_(computing)
[56]:https://practicaltypography.com/ligatures-in-programming-fonts-hell-no.html
[57]:https://www.youtube.com/watch?v=NkfMBI1tVwY
[58]:
[59]:
[60]:


