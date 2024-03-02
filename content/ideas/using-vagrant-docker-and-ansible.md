#
<
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----


* [i automated my home lab (and CLOUD) with Ansible](https://www.youtube.com/watch?v=6rpTjEpvUtc)
* [Automate your Docker deployments with Ansible](https://www.youtube.com/watch?v=CQk9AOPh5pw)



# Using Vagrant, Docker, and Ansible

# Some Prerequisites



# Ansible Semaphore
Ansible Semaphore is a web interface for running ansible playbooks.
you do not need to change your playbooks to start using it.
ansible semaphore designed for devops, has access controls to assure secure deployment and configuration.

* [This web UI for Ansible is so damn useful!](https://www.youtube.com/watch?v=NyOSoLn5T5U&t=180s)
* [ansible semaphore](https://www.ansible-semaphore.com/)
* [using ansible semaphore instead of ansible tower](https://medium.com/@farzadhabibii98/using-ansible-semaphore-instead-of-ansible-tower-e9d997b82041)
* [how to put a gui on ansible, using semaphore](https://thenewstack.io/how-to-put-a-gui-on-ansible-using-semaphore/)
* [this web ui for ansible is so damn useful!](https://www.youtube.com/watch?v=nyosoln5t5u)
* [setup ansible semaphore to run playbooks (ui for ansible - open source ansible tower alternative)](https://www.youtube.com/watch?v=l0ixfzkuto8)
* [simple ci/cd on ansible semaphore ui](https://dev.to/fiftin/simple-cicd-on-ansible-semaphore-4k17)


* [Ansible by Example](https://dzone.com/articles/ansible-boots-kubernetes)







------



# KVM
KVM (Kernel-based Virtual Machine) is a full virtualization solution for Linux on x86 hardware containing virtualization extensions (Intel VT or AMD-V).
KVM was added to the Linux Kernel (version 2.6.20) in February of 2007.

* [QEMU/KVM for absolute beginners](https://www.youtube.com/watch?v=BgZHbCDFODk)
* [Amazing Privacy Ideas with KVM Virtual Machines](https://www.youtube.com/watch?v=NIdu4haRWx0)

# QEMU
[QEMU (Quick EMUlator][A1] calls itself a generic and open source machine emulator and virtualizer.
A machine emulator that can run operating systems & programs for one machine on a different machine.
Mostly QEMU is not used as emulator but as virtualizer in collaboration with KVM kernel components.
In that case it utilizes the virtualization technology of the hardware to virtualize guests.

QEMU is a type 2 hypervisor that runs within user space and performs virtual hardware emulation, whereas KVM is a type 1 hypervisor that runs in kernel space, that allows a user space program access to the hardware virtualization features of various processors.

Proxmox VE vs Qemu: What are the differences? - https://stackshare.io/stackups/proxmox-ve-vs-qemu
Qemu/KVM Virtual Machines - https://pve.proxmox.com/wiki/Qemu/KVM_Virtual_Machines

* [QEMU: A proper guide!](https://www.youtube.com/watch?v=AAfFewePE7c)
* [Stop using Virtualbox, Here's how to use QEMU instead](https://www.youtube.com/watch?v=Kq849CpGd88)

[A1]:https://www.qemu.org/

## Virt-Manager
* [Virt-Manager Is The Better Way To Manage VMs](https://www.youtube.com/watch?v=p1d_b_91YlU)
* [Virtual Machine Manager: Virt-Manager](https://virt-manager.org/)




---



# Multipass
* [Launching Ubuntu instances with Multipass](https://www.youtube.com/watch?v=Z91l6ZdQjhI)
* [Linux Fu: Easy VMs](https://hackaday.com/2022/11/01/linux-fu-easy-vms/)

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



---



# VirtualBox
[VirtualBox][09] is a [full virtualization][07] x86 / AMD64 / Intel64 hardware architecture
(contrast this with [hardware-assisted virtualization][08]).
It creates a [virtual machine (VM)][06], aka an emulation of a computer system.
Virtual machines (VM) behave like a separate computer system,
complete with virtual hardware devices.
The VM runs as a process in a window on your current operating system.
You can boot an operating system installer disc (or live CD) inside the virtual machine,
and the operating system will be “tricked” into thinking it’s running on a real computer.
It will install and run just as it would on a real, physical machine.

## VBoxManage
[VBoxManage][53] is the command-line interface to Oracle VM VirtualBox.
With it, you can completely control Oracle VM VirtualBox from the command line of your host operating system.
It exposes all the features of the virtualization engine,
even those that cannot be accessed from the GUI.

```bash
# list vagrant boxes available
$ vagrant box list
ubuntu/bionic64 (virtualbox, 20190508.0.0)
ubuntu/disco64  (virtualbox, 20191204.0.0)
ubuntu/disco64  (virtualbox, 20191217.0.0)
ubuntu/trusty64 (virtualbox, 20180227.0.1)
ubuntu/xenial64 (virtualbox, 20180912.0.0)
windows10base   (virtualbox, 0)

# lists all virtual machines currently registered
$ VBoxManage list vms
"Windows 8" {13ac2827-612d-43cf-af2b-f578c1f4df9a}
"micropython_default_1550427608885_85428" {ee5c9ada-f0b8-45e8-9972-4d0efe77eb65}
"mosquitto_default_1556416097304_85598" {9a247aaa-571c-412a-8f1f-3f9732ce7a18}
"tensorflow_default_1576814704088_93718" {e9e714da-183b-42c6-981f-e5e547b52a89}
"tensorflow_default_1577381355317_77366" {dcb0ebdc-f906-4d21-ae77-0f11858819b7}
"rsyslog-test_default_1581097326775_97773" {5bf0edd8-8fde-48fa-9532-f9cfdae98ae0}
"windows-10_Windows10BaseBox_1581212590774_74597" {856f4ebb-3f51-4138-a51a-2091bf2ab296}

# lists the host DVD along with the name used to access them from within virtualbox
$ VBoxManage list hostdvds
UUID:         00445644-0000-0000-2f64-65762f737230
Name:         /dev/sr0

# shows information about a particular virtual machine
VBoxManage showvminfo windows-10_Windows10BaseBox_1581212590774_74597
```


```bash
# get the list of VMs that are running and their VM ID
$ VBoxManage list runningvms
"rsyslog-test_default_1581097326775_97773" {5bf0edd8-8fde-48fa-9532-f9cfdae98ae0}
"windows-10_Windows10BaseBox_1581212590774_74597" {856f4ebb-3f51-4138-a51a-2091bf2ab296}

# get the list of properties about the VM, so you can get the IDE controller name
$ VBoxManage showvminfo windows-10_Windows10BaseBox_1581212590774_74597 | grep "Controller Name"
Storage Controller Name (0):            IDE Controller

# add an empty optical drive
VBoxManage storageattach 856f4ebb-3f51-4138-a51a-2091bf2ab296 --storagectl "IDE Controller" --port 0 --device 1 --type dvddrive --medium emptydrive
```

```bash
# take snapshots so you can revert back to a known-good state rather than having to completely re-install
VBoxManage snapshot $VM take <name of snapshot>

# revert back to a particular snapshot
VBoxManage snapshot $VM restore <name of snapshot>
```

## Installing VirtualBox

### Step X: Installing VirtualBox
Along with the Vagrant install, it is essentially to installed and keep updated the Guest Addition package.
Keeping the tools update is problematic enough,
but then you realize not all boxes available from the official repository even have Guest Additions installed
Luckly, there is a plugin that can manage installing and updating the tools automatically.

```bash
# install guest addition plugin
vagrant plugin install vagrant-vbguest

# to update your plugins after a vagrant upgrade
vagrant plugin update vagrant-vbguest

# to repair your plugins if broken
vagrant plugin repair vagrant-vbguest
```

### Step X: Removing VirtualBox
I had problems where my version of VirtualBox and its Guest Additions where not at the same level.
Vagrant often doesn't like this and will result in things not working properly.
You can detect this inconsistency via the following commands:

```bash
# bring up a vagrant box
vagrant up

# run on host: check on the status of virtualbox guest additions
$ vagrant vbguest --status
Got different reports about installed GuestAdditions version:
Virtualbox on your host claims:   6.0.14
VBoxService inside the vm claims: 5.1.38
Going on, assuming VBoxService is correct...
[default] GuestAdditions versions on your host (6.0.14) and guest (5.1.38) do not match.
```

Another detection method is by looking at installed packages via `dpkg`:

```bash
# run on host: search for virtualbox-guest package
$ dpkg -l | grep virtualbox-guest
ii  virtualbox-guest-dkms                                       6.0.14-dfsg-1                                     all          x86 virtualization solution - guest addition module source for dkms
ii  virtualbox-guest-utils                                      6.0.14-dfsg-1                                     amd64        x86 virtualization solution - non-X11 guest utilities
ii  virtualbox-guest-x11                                        6.0.14-dfsg-1                                     amd64        x86 virtualization solution - X11 guest utilities

# run on guest: search for virtualbox-guest package
$ dpkg -l | grep virtualbox-guest
ii  virtualbox-guest-dkms                      5.1.38-dfsg-0ubuntu1.16.04.3                 all          x86 virtualization solution - guest addition module source for dkms
ii  virtualbox-guest-utils                     5.1.38-dfsg-0ubuntu1.16.04.3                 amd64        x86 virtualization solution - non-X11 guest utilities
ii  virtualbox-guest-x11                       5.1.38-dfsg-0ubuntu1.16.04.3                 amd64        x86 virtualization solution - X11 guest utilities
```

To fix this, bring the VirtualBox Guest Addition up to date with VirtualBox by doing this:

```bash
# update virtualbox guest addition
vagrant vbguest

# run on host: check on the status of virtualbox guest additions
$ vagrant vbguest --status
[default] GuestAdditions 6.0.14 running --- OK.
```


### Step X: Installing VirtualBox Guest Additions
VirtualBox Guest Additions are a collection of device drivers
and system applications designed to achieve closer integration
between the host and guest operating systems.
VirtualBox lets you download an image ISO file called “VBoxGuestAdditions.iso” containing Guest Additions.
This file is located on the host machine
and can be mounted on the guest system using the VirtualBox GUI manager.
Once mounted, the guest additions installer can be used to install the guest additions on the guest system.
The VirtualBox Guest Additions should be installed inside a virtual machine
after the guest operating system has been installed.
The article "[How to Install VirtualBox Guest Additions on Ubuntu 18.04][58]"
tells you how to do this install.

I'm not going to be using VitualBox directly,
but instead, I'll be using VirtualBox with Vagrant.

```bash
sudo apt-get install virtualbox-guest-additions-iso
```



----



# Vagrant
* [Vagrant Crash Course](https://www.youtube.com/watch?v=vBreXjkizgo)
* [Crash Course on Vagrant](https://sysadmincasts.com/episodes/42-crash-course-on-vagrant-revised)
* [Managing virtual environments with Vagrant](https://opensource.com/article/18/4/vagrant-guide-get-started)

[Vagrant][01] is a tool that offers a simple and easy to use
command-line client for managing virtual environments.
I started using it because it made it easier for me to
standup new software solutions for testing without disrupting my working system.

[Vagrant][01] is a tool for building and managing virtual machine environments in a single workflow.
Vagrant has an easy-to-use workflow, makes automation easy, and lowers development environment setup time.
Machines are provisioned on top of VirtualBox, VMware, AWS, or any other provider.
Then, industry-standard provisioning tools such as
shell scripts, Chef, or Puppet, can automatically install
and configure software on the virtual machine.

**For developers**, Vagrant will isolate dependencies and their configuration within a
single disposable, consistent environment, without sacrificing
any of the tools you are used to working with (editors, browsers, debuggers, etc.).
Once you or someone else creates a single [Vagrantfile][10],
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

Aside from reading [Vagrant's official documentation][05],
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

## Boxes
[Boxes][12] are the package format for Vagrant environments.
A box can be used by anyone on any platform that Vagrant supports
to bring up an identical working environment.
The `vagrant box` utility provides all the functionality for managing boxes.

Vagrant can ingest standard box templates, called base boxes,
to intialize your Vagrant VM.
The [Vagrant Cloud][13] and [Vagrantboex.es][11] websites
provide a list of base boxes organizations / people have made publicly available or can be purchased.

Vagrant boxes are all provider-specific. A box for VirtualBox is incompatible with the VMware Fusion provider, or any other provider. A box must be installed for each provider, and can share the same name as other boxes as long as the providers differ. So you can have both a VirtualBox and VMware Fusion "precise64" box.

## Defining Multiple Machines
* https://www.vagrantup.com/docs/multi-machine/

## What About Containers (e.g. Docker)
A container is a way to isolate a group of processes from the others on a running Linux system. By making use of existing functionality like the Linux kernel's new resource management and resource isolation features (Cgroups and name spaces), these processes can have their own private view of the operating system with its own process ID (PID) space, file system structure and network interfaces.

Containers share the same kernel with anything else that is running on it, but can be constrained to only use a defined amount of resources such as CPU, memory or I/O. By combining containers with other features like the Btrfs file system , it will be possible to quickly set up multiple lightweight isolated Linux instances on a single host. Therefore containers are better compared to Solaris zones or BSD jails.

Containerization is the process of distributing and deploying applications in a portable and predictable way. It accomplishes this by packaging components and their dependencies into standardized, isolated, lightweight process environments called containers.  Many organizations are now interested in designing applications and services that can be easily deployed to distributed systems, allowing the system to scale easily and survive machine and application failures.  Docker, a containerization platform developed to simplify and standardize deployment in various environments, was largely instrumental in spurring the adoption of this style of service design and management.  A large amount of software has been created to build on this ecosystem of distributed container management.

A container emulates the user space of an operating system.
You run a container engine to create isolated processes, memory, mount points, and networking.

* The **benefit** of this is that any container you run on top of the container engine
can only see its own user space, so it’s isolated from the host machine and other containers,
and will run exactly the same way in all environments.
Since the kernel and hardware are shared,
your containers can boot up in milliseconds and have virtually no CPU or memory overhead.
* The **drawback** is that all the containers running on a single server share
that server’s operating system kernel and hardware,
so the isolation is not as secure as with VMs.

Both docker and vagrant help create predictable and repeatable development environments. However, docker uses container technology while vagrant uses virtual machines to achieve this goal. Understanding the strengths and weaknesses of Docker and Vagrant will help developers mix and match these tools to achieve the desired results.

A Docker container is basically your complete application
and all of its dependencies wrapped up into one neat package.
Then you can run this image as a container on any machine running Docker.
You don’t need a new virtual machine for each container,
just one, as they are designed to run on top of a machine.
Then, you can run as many Docker containers as you like on that virtual machine,
as long as you have enough processing power and RAM.
If you can run Docker, you can run your application and it will work every time.

Vagrant is a tool focused on providing a consistent development environment workflow
across multiple operation systems.
Docker is a container management that can consistently run software
as long as a containerization system exists.

* [A sysadmin's guide to containers: What you need to know to understand how containers work](https://opensource.com/article/18/8/sysadmins-guide-containers)
* [Containers are Linux](https://www.redhat.com/en/blog/containers-are-linux)
* [Container Basics](https://www.sdxcentral.com/containers/definitions/containers-basics-update/)
* [6 container concepts you need to understand](https://opensource.com/article/20/12/containers-101)

* [How I build my personal website using containers with a Makefile](https://opensource.com/article/21/7/manage-containers-makefile)
* [3 steps to start running containers today](https://opensource.com/article/22/2/start-running-containers)

## Docker vs Vagrant
* [Docker Vs Vagrant](https://www.youtube.com/watch?v=9QGkJvbLpRA)
* [Docker – the Best Containerization Platform for an Efficient Software Development](https://www.cabotsolutions.com/2016/12/docker-best-containerization-platform-efficient-software-development/)
* [Docker vs Vagrant: Which is Better for Development?](https://www.devteam.space/blog/docker-vs-vagrant-which-is-better-for-development/)
* [Ansible and Docker: the Best Combination for an Efficient Software Product Management](https://medium.com/@cabot_solutions/ansible-and-docker-the-best-combination-for-an-efficient-software-product-management-28c86cfebe90)
* [Docker’s detached mode for beginners](https://www.freecodecamp.org/news/dockers-detached-mode-for-beginners-c53095193ee9/)

## Learning Vagrant
So Vagrant allows you to create portable work environments
which can be easily reproduced on any system.
It's useful for developers and system administrators
who want to mimic a server's configuration on their local machine.
Here are some materials to learn more about Vagrant:

* [Why Vagrant?](https://www.youtube.com/watch?v=N-8QuptIOvg)
* [Installing Vagrant and VirtualBox](https://www.youtube.com/watch?v=RhhF8Yh7OnE)

* [Tips for a better Vagrant-based development workflow](https://www.jeffgeerling.com/blogs/jeff-geerling/better-vagrant-development-workflow)
* [Vagrant: sudo access and the hostsupdater plugin](http://myrant.net/2016/05/07/vagrant-sudo-access-and-the-hostsupdater-plugin/)

* [Installing Vagrant and VirtualBox](https://www.youtube.com/watch?v=RhhF8Yh7OnE)
* [Crash Course on Vagrant](https://sysadmincasts.com/episodes/42-crash-course-on-vagrant-revised)

## Vagrant Plugins
Vagrant has many features that requires doing guest OS-specific actions,
such as mounting folders, configuring networks, etc.
Vagrant comes pre-configured to support many environments,
but sometimes you want to change the way Vagrant does something or add additional functionality to Vagrant.
This can be done via Vagrant plugins.
In fact, much of the core of Vagrant is [implemented using plugins][54].

```bash
# browse available plugins
$ gem list --remote vagrant-

*** REMOTE GEMS ***

capistrano-strategy-vagrant-copy-bundled (0.1.0)
chino-vagrant-hostmaster (0.8.1)
cjscp-vagrant-persistent-storage (0.0.27)
djo-vagrant-vsphere (1.6.3)
lh-vagrant-dns (0.0.6)
ll-vagrant-aws (0.0.1)
mojolingo-vagrant-librarian-puppet (0.7.1)
outoftime-vagrant-librarian-puppet (0.7.1.1416968000)
pleschev-vagrant-hostmaster (0.8.1)
realityforge-vagrant-windows (0.1.4)
  .
  .
  .

# available 'guest' plugins
$ gem list --remote vagrant- | grep guest
vagrant-guest-msys2 (0.0.6)
vagrant-guest-netbsd (0.0.2)
vagrant-guest-omnios (0.3.0)
vagrant-guest-openwrt (0.0.3)
vagrant-guest-qnx (0.0.1)
vagrant-guest_ansible (0.0.4)
vagrant-guestip (0.2)
vagrant-guests-clearlinux (1.2.4)
vagrant-guests-openbsd (0.0.3)
vagrant-guests-photon (1.0.5)
vagrant-guixsd-guest (0.1.1)
vagrant-nfs_guest (1.0.3)
vagrant-nfs_guest_vbfix (0.1.10)
vagrant-smartos-guest (0.0.1)
vagrant-vbguest (0.24.0)
vagrant-vbguest-centos (0.2.0)
vagrant-vbguest-redhat-kernel-update (0.2.3)
vagrant-windows-guest-nfs (0.2)

# list installed plugins
$ vagrant plugin list
vagrant-hostsupdater (1.1.1.160, global)
  - Version Constraint: > 0
vagrant-scp (0.5.7, global)
  - Version Constraint: > 0
vagrant-vbguest (0.24.0, global)
  - Version Constraint: > 0
```

## Installing Vagrant

### Step X: Check Verisons of Installed Vagrant and VirtualBox
```bash
# check vritualbox version
$ vboxmanage --version
6.1.10_Ubuntur138449

# check vagrant version
$ vagrant --version
Vagrant 2.2.6

# check if installed vagrant and virtualBox ara compatable
$ vagrant up --provider=virtualbox
The provider 'virtualbox' that was requested to back the machine
'default' is reporting that it is not usable on this system. The
reason is shown below:

Vagrant has detected that you have a version of VirtualBox installed
that is not supported by this version of Vagrant. Please install one of
the supported versions listed below to use Vagrant:

4.0, 4.1, 4.2, 4.3, 5.0, 5.1, 5.2, 6.  0

A Vagrant update may also be available that adds support for the version
you specified. Please check www.vagrantup.com/downloads.html to download
the latest version.
```

In my case, you see I have an incompatibility.
Unfortunately, this happens often when Virtualbox, Vagrant, or Ubuntu make updates.
In this case,
Oracle knew of the Vagrant 2.2.6 incompatibility with Virtualbox 6.1.x
and Oracle provided a fix.
See the article
["VirtualBox 6.1: No compatible version of Vagrant yet! (or is there?)"](https://oracle-base.com/blog/2020/01/01/virtualbox-6-1-no-compatible-version-of-vagrant-yet/).

### Step 1: Installing Vagrant and VirtualBox - DONE
Its best to install both VirtualBox and Vagrant via their respective download pages,
not your operating systems distribution package manager.
To often these packages are missing dependencies or include very outdated versions.
Go to [VirtualBox download][03] and [Vagrant download][02] pages for your software and install procedures.
Once you download the Vagrant deb file, click on it, and follow the instructions.

As a quick sanity check, make sure that we have the `vagrant` command in your path,
check the version number with `vagrant -v`
or `vagrant version` to check if your running the latest version.

### Step 2: Install Vagrant Hosts Updater Plugin - DONE
The [`vagrant-hostsupdater`][04] plugin adds an entry to your `/etc/hosts`
file on the host system.
With this, every time you start or shut down a VM with Vagrant,
the relevant hosts entries will be placed in your system's hosts file,
without requiring you to do anything manually.

Another nice plugin is [`vagrant-scp`][52].
It adds a `scp` command to vagrant,
so you can copy files to your VM like you would normally do with `scp`.

```bash
# list plugins currently installed
vagrant plugin list

# install host updater and other plugin
vagrant plugin install vagrant-hostsupdater
vagrant plugin install vagrant-scp

# uninstall the plugins
vagrant plugin uninstall vagrant-hostsupdater

# update the plugin
vagrant plugin update vagrant-hostsupdater
```

A downside to using the `vagrant-hostsupdater` plugin
is that you have to enter your `sudo` password when you build and destroy VMs.
You can avoid this by adding the following lines to your `/etc/sudoers` configuration

>**NOTE:** Make sure to use `sudo visudo` instead of just editing it in your favorite editor.
Then quit and restart your Terminal session so the new settings are picked up.

```bash
############################  Vagrant Configuration  ###########################
# NOTE: Make sure the 'admin' group is changed to whatever group your user account is in

# Allow Vagrant to manage NFS exports.
Cmnd_Alias VAGRANT_EXPORTS_ADD = /usr/bin/tee -a /etc/exports
Cmnd_Alias VAGRANT_NFSD = /sbin/nfsd restart
Cmnd_Alias VAGRANT_EXPORTS_REMOVE = /usr/bin/sed -E -e /*/ d -ibak /etc/exports

# Allow Vagant to manage hosts file.
Cmnd_Alias VAGRANT_HOSTS_ADD = /bin/sh -c echo "*" >> /etc/hosts
Cmnd_Alias VAGRANT_HOSTS_REMOVE = /usr/bin/sed -i -e /*/ d /etc/hosts
%admin ALL=(root) NOPASSWD: VAGRANT_EXPORTS_ADD, VAGRANT_NFSD, VAGRANT_EXPORTS_REMOVE, VAGRANT_HOSTS_ADD, VAGRANT_HOSTS_REMOVE
```

For more information,
checkout

### Step X: Install the vbguest Pluggin
`vagrant-vbguest` is a Vagrant plugin which automatically installs the
host's VirtualBox Guest Additions on the guest system.

The [VirtualBox Guest Additions][55] are a set of drivers and
applications to be deployed on a virtual machine to have better performance
and enable features such as folder sharing.
While it's possible to include the Guest Additions directly in the box,
not all the boxes you'll find have it, and even when they do, they can be outdated very quickly.

The [solution is to automatically deploy the VirtualBox Guest Additions on demand][56], through a plugin,
which [autoupdates VirtualBox Guest Additions with the `vagrant-vbguest` plugin][57].
The vbguest plugin (`vagrant-vbguest`) is a Vagrant plugin which automatically installs
and updates VirtualBox Guest Additions on the guest system.
This plugin is a prerequisite for some guest installations, and so good to have install.

>**NOTE:** If you find that one of these does not work for your operating system,
>then maybe the guest implementation is incomplete or incorrect.
>
>When we upgrade VirtualBox, we will get prompted to update the guest additions.
>That means that the installed version updates with the base version of VirtualBox itself.
>It does not automatically go back and retrofit the existing machines with the updated guest additions though.

```bash
# install the plugin
vagrant plugin install vagrant-vbguest

# uninstall the plugin
vagrant plugin uninstall vagrant-vbguest

# vbguest status check
$ vagrant vbguest --status
Got different reports about installed GuestAdditions version:
Virtualbox on your host claims:   5.0.18
VBoxService inside the vm claims: 5.1.38
Going on, assuming VBoxService is correct...
[default] A Virtualbox Guest Additions installation was found but no tools to rebuild or start them.
```

### Step X: Install the Cashier Pluggin
[speeds up Vagrant processing of packages](http://jeremybarthe.com/2015/02/02/speed-up-vagrant-environment-symfony2/)

```bash
vagrant plugin install vagrant-cachier
```

Also recommened to clear this problem - https://github.com/fgrehm/vagrant-cachier/issues/175

  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :machine

    config.cache.synced_folder_opts = {
      owner: "_apt",
      group: "_apt"
    }

* [`vagrant-cashier` plugin](http://fgrehm.viewdocs.io/vagrant-cachier/)
* [How To “Fix E: Could not open file /var/lib/dpkg/status”](https://www.unixmen.com/fix-e-open-file-varlibdpkgstatus/)

```bash
# this is how to fix
# "E: Could not open file /var/lib/dpkg/status”
# or "E: List directory /var/lib/apt/lists/partial is missing"

# if you get this
$ sudo apt-get update
Reading package lists... Error!
E: List directory /var/lib/apt/lists/partial is missing. - Acquire (2: No such file or directory)
E: flAbsPath on /var/lib/dpkg/status failed - realpath (2: No such file or directory)
E: Could not open file  - open (2: No such file or directory)
E: Problem opening
E: The package lists or status file could not be parsed or opened.

# then run this
sudo rm -r -f /var/lib/apt
sudo mkdir --parent /var/lib/apt/lists/partial
```

### Step X: Download a Vagrant Box and Build Virtual Machine
https://app.vagrantup.com/boxes/search?utf8=%E2%9C%93&sort=downloads&provider=&q=ubuntu+16.04

This puts wthe offical Ubuntu 16.04LTE (Xenia Xerus) daily build on your system.

```bash
# move to directory for vagrant vm
mkdir ~/tmp/vagrant-test
cd ~/tmp/vagrant-test

# create a base Vagrantfile (Ubuntu 16.04) and bring it up
vagrant init ubuntu/xenial64
vagrant up

# login to the machine
vagrant ssh
```

At a later time, you may want to update this box.
You can do this via:

```bash
# list the boxes you have installed
$ vagrant box list
ubuntu/trusty64 (virtualbox, 20180227.0.1)
ubuntu/xenial64 (virtualbox, 20180410.0.0)
ubuntu/xenial64 (virtualbox, 20180706.0.0)
```

To update the version of a box:

```bash
# check if there are updates available for all boxes
$ vagrant box outdated --global
* 'ubuntu/xenial64' for 'virtualbox' (v20180706.0.0) is up to date
* 'ubuntu/trusty64' for 'virtualbox' is outdated! Current: 20180227.0.1. Latest: 20180627.0.1

# updates a specified box
????

# updates the current vagrant environment if there are updates available
vagrant box update
```

To remove a box:

```bash
# list the boxes you have installed
$ vagrant box list
ubuntu/trusty64 (virtualbox, 20180227.0.1)
ubuntu/xenial64 (virtualbox, 20180410.0.0)
ubuntu/xenial64 (virtualbox, 20180706.0.0)

# remove the older ubuntu/xenial64 box
vagrant box remove ubuntu/xenial64 --box-version=20180410.0.0
```

### Step 3A: Setup SSH Keys on Linux
If you want to use your SSH credentials inside a Vagrant-powered VM,
you can turn on SSH agent forwarding on by adding the following line inside your Vagrantfile:

```
config.ssh.forward_agent = true
```

> **Note:** You usually don't have fowarding enabled if you are treating Vagrant VMs
strictly as sandboxed development environments.
If you are installing some software for testing inside the VM as the vagrant user,
you don't want it to be able to use your SSH credentials to do anything nefarious!
Generally that won't happen, but erring on the side of caution.

* https://www.cyberciti.biz/faq/how-to-set-up-ssh-keys-on-linux-unix/
* [Change Insecure Key To My Own Key On Vagrant](http://ermaker.github.io/blog/2015/11/18/change-insecure-key-to-my-own-key-on-vagrant.html)
* [Vagrant insecure by default?](https://stackoverflow.com/questions/14715678/vagrant-insecure-by-default)
* [security - Vagrant insecure by default?](https://code-examples.net/en/q/e08b1e)
* [Tips for a better Vagrant-based development workflow](https://www.jeffgeerling.com/blogs/jeff-geerling/better-vagrant-development-workflow)

### Step 3B: SSH Keys Inside Your VM - DONE
If you want to use your SSH credentials inside a Vagrant VM,
effectively re-use the key pair you have on the host machine,
you can turn on SSH agent forwarding on by adding
the following line inside your `vagrantfile` file:

```bash
# add this to the vagrantfile
config.ssh.forward_agent = true
```

>**NOTE:** If you're treating Vagrant VMs strictly as sandboxed development environments,
then usually you don't want to do this.
Doing so your could be mistakenly give your keys away to someone using the VM.

### Step X: Vagrantfile Setup
* [Vagrantfile Explained: Setting Up and Provisioning with Shell](https://www.sitepoint.com/vagrantfile-explained-setting-provisioning-shell/)

### Step X: Logging into Vagrant VM
```bash
# start your vagrant vm
$ vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Checking if box 'ubuntu/xenial64' is up to date...
==> default: Clearing any previously set forwarded ports...
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 (guest) => 2222 (host) (adapter 1)
==> default: Running 'pre-boot' VM customizations...
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
    default: The guest additions on this VM do not match the installed version of
    default: VirtualBox! In most cases this is fine, but in rare cases it can
    default: prevent things such as shared folders from working properly. If you see
    default: shared folder errors, please make sure the guest additions within the
    default: virtual machine match the version of VirtualBox you have installed on
    default: your host and reload your VM.
    default:
    default: Guest Additions Version: 5.1.34
    default: VirtualBox Version: 5.2
==> default: [vagrant-hostsupdater] Checking for host entries
==> default: Mounting shared folders...
    default: /vagrant => /home/jeff/src/test-env/mongodb
==> default: Machine already provisioned. Run `vagrant provision` or use the `--provision`
==> default: flag to force provisioning. Provisioners marked to run always will still run.

# login as the vagrant user
vagrant ssh
```

### Step X:
### Step X:
### Step X:

### Step X: Shutdown Vagrant Instance
To findout what machines Vagrant is managing, run the following command:

This command shuts down the running machine Vagrant is managing.

```bash
# gracefully turn down the running machine
vagrant halt
```

Vagrant will first attempt to gracefully shut down
the machine by running the guest OS shutdown mechanism.
If this fails, or if the `--force` flag is specified,
Vagrant will effectively just shut off power to the machine.

# Add Public Key to Vagrant
* [Add public key to Vagrant](https://medium.com/@Sohjiro/add-public-key-to-vagrant-4bd5424521bf)

# Upload Private SSH Key to Vagrant Box on "vagrant up"
Sometimes it is handy to have your own private SSH key on your vagrant box,
especially when you want to use git inside your box, rather then in you host OS.

Assuming you're using  Linux,
you can use shell provisioner to upload local file to remote box:

```bash
Vagrant.configure("2") do |config|
    config.vm.provision :shell, :inline => "echo -e '#{File.read("#{Dir.home}/.ssh/id_rsa")}' > '/home/vagrant/.ssh/id_rsa'"
end
```

```bash
Vagrant.configure("2") do |config|
    config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/rsa.pub"
end
```

You may want to upload you git configuration file `~/.gitconfig`:

```bash
Vagrant.configure("2") do |config|
    config.vm.provision :shell, :inline => "echo -e '#{File.read("#{Dir.home}/.gitconfig")}' > '/home/vagrant/.gitconfig'"
end
```

# Development Workflow With Vagrant
* [Managing virtual environments with Vagrant](https://opensource.com/article/18/4/vagrant-guide-get-started)
* [Development Workflow With Vagrant](https://paulund.co.uk/development-workflow-vagrant)
* [A gentle introduction to Vagrant, the automated Virtual Machine builder](https://chariotsolutions.com/blog/post/a-gentle-introduction-to-vagrant-the-automated-virtual-machine-builder/)
* [Building a Vagrant Box from Start to Finish](https://www.engineyard.com/blog/building-a-vagrant-box-from-start-to-finish)
* [How to Create a Vagrant Base Box from an Existing One](https://scotch.io/tutorials/how-to-create-a-vagrant-base-box-from-an-existing-one)
* [How to Create and Share a Vagrant Base Box](https://www.sitepoint.com/create-share-vagrant-base-box/)
* [How to create a Vagrant Virtual Machine](https://codewithintent.com/how-to-creat-a-vagrant-virtual-machine/)
* https://howtoprogram.xyz/2017/08/11/change-vagrant-virtual-machine-name/
* https://howtoprogram.xyz/2016/07/11/basic-vagrant-commands/

## Vagrant Command-Line Interface
To list all the `vagrant` commands available:

```bash
# list all the vagrant commands
$ vagrant list-commands
Below is a listing of all available Vagrant commands and a brief
description of what they do.

box             manages boxes: installation, removal, etc.
cap             checks and executes capability
destroy         stops and deletes all traces of the vagrant machine
docker-exec     attach to an already-running docker container
docker-logs     outputs the logs from the Docker container
docker-run      run a one-off command in the context of a container
global-status   outputs status Vagrant environments for this user
halt            stops the vagrant machine
help            shows the help for a subcommand
init            initializes a new Vagrant environment by creating a Vagrantfile
list-commands   outputs all available Vagrant subcommands, even non-primary ones
login           log in to HashiCorps Vagrant Cloud
package         packages a running vagrant environment into a box
plugin          manages plugins: install, uninstall, update, etc.
port            displays information about guest port mappings
powershell      connects to machine via powershell remoting
provider        show provider for this environment
provision       provisions the vagrant machine
push            deploys code in this environment to a configured destination
rdp             connects to machine via RDP
reload          restarts vagrant machine, loads new Vagrantfile configuration
resume          resume a suspended vagrant machine
rsync           syncs rsync synced folders to remote machine
rsync-auto      syncs rsync synced folders automatically when files change
snapshot        manages snapshots: saving, restoring, etc.
ssh             connects to machine via SSH
ssh-config      outputs OpenSSH valid configuration to connect to the machine
status          outputs status of the vagrant machine
suspend         suspends the machine
up              starts and provisions the vagrant environment
validate        validates the Vagrantfile
version         prints current and latest Vagrant version
```

Check out [Vagrant's online documention][14] for adition information concurning Vagrant CLI.

### Step 1:
Before you run any of the `vagrant` commands,
make sure that your located in the directory where
you want save your files that will be used in your application.

Next you must select a virtual machine that you will want to init your file with.
You can find a list of available virtual machines at the
[Vagrant Cloud][13] and [Vagrantboex.es][11] websites.
You could also [build a Vagrant Box from scratch][15].

```bash
# directory for my vagrant vm
mkdir ~/tmp/vagrant-test
cd ~/tmp/vagrant-test

# create a base Vagrantfile (Ubuntu 16.04) and bring it up
vagrant init ubuntu/xenial64
vagrant up
```

Now the machine is created and up, lets connect to it used over an SSH connection.

```bash
vagrant ssh

### Step X:
```bash
# get status of all vagrant machines on the host
vagrant global-status

# get status of all vagrant machines for this directories vagrantfile
vagrant status

# list all the boxes - just to know the names
vagrant box list

# stop the vagrant machine
vagrant halt
```

## Step X: Remove Old Boxes Plugin
After using Vagrant for some time,
you end up with way too many old boxes,
and the only way you can remove them is one-by-one
via an multi-step operation like:

```bash
# list the boxes you have installed
$ vagrant box list
ubuntu/bionic64 (virtualbox, 20180907.0.0)
ubuntu/bionic64 (virtualbox, 20180913.0.0)
ubuntu/trusty64 (virtualbox, 20180227.0.1)
ubuntu/xenial64 (virtualbox, 20180831.0.0)
ubuntu/xenial64 (virtualbox, 20180912.0.0)

# remove only the specified ubuntu/xenial64 box
vagrant box remove ubuntu/xenial64 --box-version=20180831.0.0
```

Luckily there is builtin feature `vagrant box prune` and
it will remove older boxes with a specific name and from a specific provider,
or it can remove all but the latest installed boxes.

```bash
$ vagrant box prune --help
Usage: vagrant box prune [options]

Options:

    -p, --provider PROVIDER          The specific provider type for the boxes to destroy.
    -n, --dry-run                    Only print the boxes that would be removed.
        --name NAME                  The specific box name to check for outdated versions.
    -f, --force                      Destroy without confirmation even when box is in use.
    -h, --help                       Print this help
```

Here is an example of `vagrant box prune` at work:

```bash
# list the boxes you have installed
$ vagrant box list
ubuntu/bionic64 (virtualbox, 20180907.0.0)
ubuntu/bionic64 (virtualbox, 20180913.0.0)
ubuntu/trusty64 (virtualbox, 20180227.0.1)
ubuntu/xenial64 (virtualbox, 20180831.0.0)
ubuntu/xenial64 (virtualbox, 20180912.0.0)

# do a dry run to see the impact
$ vagrant box prune --dry-run
The following boxes will be kept...
ubuntu/bionic64 (virtualbox, 20180913.0.0)
ubuntu/trusty64 (virtualbox, 20180227.0.1)
ubuntu/xenial64 (virtualbox, 20180912.0.0)

Checking for older boxes...
Would remove ubuntu/bionic64 virtualbox 20180907.0.0
Would remove ubuntu/xenial64 virtualbox 20180831.0.0

# make the pruning
$ vagrant box prune
The following boxes will be kept...
ubuntu/bionic64 (virtualbox, 20180913.0.0)
ubuntu/trusty64 (virtualbox, 20180227.0.1)
ubuntu/xenial64 (virtualbox, 20180912.0.0)

Checking for older boxes...
Box 'ubuntu/bionic64' (v20180907.0.0) with provider 'virtualbox' appears
to still be in use by at least one Vagrant environment. Removing
the box could corrupt the environment. We recommend destroying
these environments first:

default (ID: ce0a38ee8cf347e1a125ea0cad47d28f)

Are you sure you want to remove this box? [y/N] N
Removing box 'ubuntu/xenial64' (v20180831.0.0) with provider 'virtualbox'...

# now destroy the vm referenced above
vagrant destroy ce0a38ee8cf347e1a125ea0cad47d28f
```

## Vagrant Tools
Assuming you have only one box per provider,
this command will delete ALL Vagrant boxes you currently have on your system:

```bash
# outputs status of all vagrant machines
vagrant global-status

# delete all your vagrant boxes
vagrant box list | cut -f 1 -d ' ' | xargs -L 1 vagrant box remove -f

# packages a running virtualbox env in a reusable box
vagrant package
```

To remove a box:

```bash
# list the boxes you have installed
$ vagrant box list
ubuntu/trusty64 (virtualbox, 20180227.0.1)
ubuntu/xenial64 (virtualbox, 20180410.0.0)
ubuntu/xenial64 (virtualbox, 20180706.0.0)

# remove the older ubuntu/xenial64 box
vagrant box remove ubuntu/xenial64 --box-version=20180410.0.0
```

## Step X: Checking Status of Vagrant Boxes

```bash
#  lists all the boxes that are installed into Vagrant
vagrant box list

# check if box you are using in your current vagrant environment is outdated
vagrant box outdated

# check if every box if its outdated
vagrant box outdated --global

# state of all active vagrant environments on the system for the currently logged in user
vagrant global-status

# removes a box from vagrant that matches the given name
vagrant box remove NAME

# removes old versions of installed boxes; if in use confirm first.
vagrant box prune

# repackages the given box and puts it in the current directory
# name, provider, and version of the box can be retrieved using 'vagrant box list'
vagrant box update
```




###############################################################################
The private_network is a network that is only between your host and the guest vm. If you want to make the guest vm available to others systems on the same network as your host you need to use the "public_network" setup in vagrant. This will allow your guest to get/use an IP address on the network that your host is on.
###############################################################################

## Creating a Vagrant Base Box From an Existing One
* [Creating a Vagrant Base Box From an Existing One](https://scotch.io/tutorials/how-to-create-a-vagrant-base-box-from-an-existing-one)
* [Creating your own Vagrant base box](http://eudaimonia.io/2016/05/16/creating-your-own-vagrant-base-box.html)
* [Creating a Custom Box from Scratch](https://www.skoblenick.com/vagrant/creating-a-custom-box-from-scratch/)



----



## Vagrant Package: Custom Vagrant Boxes by Creating Your Own Base Box
* [Creating a Base Box](https://www.vagrantup.com/docs/virtualbox/boxes.html)
* [Creating Vagrant Base Box with Veewee](http://ruleoftech.com/2015/creating-vagrant-base-box-with-veewee)
* [Vagrant, Packer, Veewee.. what to use?](https://unscramblegk.tumblr.com/post/64993566557/vagrant-packer-veewee-what-to-use)
* [Repeatable Vagrant builds with Packer](https://techblog.covermymeds.com/infrastructure/repeatable-vagrant-builds-with-packer/)
* [Building VM images with Ansible and Packer](https://www.jeffgeerling.com/blog/server-vm-images-ansible-and-packer)
* [Using Packer and Vagrant to Build Virtual Machines](https://blog.codeship.com/packer-vagrant-tutorial/)
* [How to Install and use Packer on Ubuntu 18.04](https://computingforgeeks.com/how-to-install-and-use-packer/)
* [Packer Tutorial For Beginners – Automate AMI Creation](https://devopscube.com/packer-tutorial-for-beginners/)


# Packer
The creation of a Vagrant box starts with the creation of VM using virtualization tool like VirtualBox.
This is often a manual process, using a GUI or CLI,
and is very different for all the virtualization tools on the market (e.g. VitrualBox, VMWare, etc.).
Unfortunately, this doesn't fit the modern paradigm of [infrastructure as code][43].

To overcome this, the creates of Vagrant, [HasiCorp][44], offer a tool called [Packer][45].
[Why Use Packer][46]?
Packer embraces modern configuration management automates the creation of any type of machine image.
Packer is an open source tool for creating identical 'machine images'
for multiple virtualization tools from a single source configuration.
Packer runs on every major operating system, and creates machine images for multiple platforms in parallel.
Packer does not replace [configuration management][47] tools like Ansible, Chef, or Puppet.
In fact, when building images,
Packer is able to use configuration management tools to install software onto the image.
Packer lets you build Virtual Machine Images for different providers from one JSON file.
You can use the same file and commands to build an image on AWS, Digital Ocean VirtualBox and Vagrant.
This makes it possible to use exactly the same system for development which you then create in production.

>**NOTE:** A 'machine image' is a single static unit that contains a pre-configured operating system
>and installed software which is used to quickly create new running machines.
>Machine image formats change for each platform.
>Some examples include AMIs for an AWS EC2,VMDK/VMX files for VMware, OVF exports for VirtualBox, etc.

## Installing Packer
Packer may be installed from a precompiled binary or from source.
The easy and recommended method for all users is binary installation method.
Check the latest release of Packer on the [Downloads page][48].
Then download the recent version for your platform.
In my case:

```bash
# downlaod version 1.5.1  for ubuntu
cd ~/tmp
export VER="1.5.1"
wget https://releases.hashicorp.com/packer/${VER}/packer_${VER}_linux_amd64.zip

# uncompress the download file
unzip packer_${VER}_linux_amd64.zip

# move the packer binary into your path
sudo mv packer /usr/local/bin

# verify the install is working
$ packer --help
Usage: packer [--version] [--help] <command> [<args>]

Available commands are:
    build       build image(s) from template
    console     creates a console for testing variable interpolation
    fix         fixes templates from old versions of packer
    inspect     see components of a template
    validate    check that a template is valid
    version     Prints the Packer version
```

## How to Use Packer
Packer uses builders to generate images and create machines for various platforms from templates.
A template is a configuration file used to define what image is built and its format is JSON.
You can see a [full list of suppported builders and their templates][49].
A template has the following three main parts.

1. **variables** – Where you define custom variables.
2. **builders** – Where you mention all the required builder parameters.
3. **provisioners** – Where you can integrate a shell script,
ansible play or a chef cookbook for configuring a required application.

In my example, I will use [VirtualBox Builder][50] to create an
Ubuntu 19.04 VirtualBox Virtual Machine.
[This VirtualBox Packer builder][51] is able to create VirtualBox virtual machines
and export them in the OVF format,
starting from an existing OVF/OVA (exported virtual machine image).

>**NOTE:** When exporting from VirtualBox make sure to choose OVF Version 2,
>since Version 1 is not compatible and will generate errors.

The builder builds a virtual machine by importing an existing OVF or OVA file.
It then boots this image, runs provisioners on this new VM,
and exports that VM to create the image.
The imported machine is deleted prior to finishing the build.

### Step 1:
Here is a basic build template
https://computingforgeeks.com/how-to-install-and-use-packer/
https://devopscube.com/packer-tutorial-for-beginners/




----



**see "howto-use-docker-and-resin-on-the-raspberry-pi-and-openwrt.md" for more text**
* [Manage your Raspberry Pi fleet with Ansible](https://opensource.com/article/20/9/raspberry-pi-ansible)

# Docker

* [Docker Series](https://earthly.dev/blog/series/docker/)

* [Docker Commands You Should Know as a Beginner](https://dzone.com/articles/docker-commands-you-should-know-as-a-beginner)

* [How To Install and Use Docker on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04)
* [How To Install and Use Docker on Debian 10](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-debian-10)
* [How to build a smaller Docker image](https://medium.com/@gdiener/how-to-build-a-smaller-docker-image-76779e18d48a)
* [A Beginner-Friendly Introduction to Containers, VMs and Docker](https://medium.freecodecamp.org/a-beginner-friendly-introduction-to-containers-vms-and-docker-79a9e3e119b)
* [Running a Docker container as a non-root user](https://medium.com/redbubble/running-a-docker-container-as-a-non-root-user-7d2e00f8ee15)

* [The Docker Ecosystem: An Introduction to Common Components](https://www.digitalocean.com/community/tutorials/the-docker-ecosystem-an-introduction-to-common-components)
* [Docker Tutorial: Get Going From Scratch](https://stackify.com/docker-tutorial/)
* [A Practical Introduction to Container Terminology](https://developers.redhat.com/blog/2018/02/22/container-terminology-practical-introduction/)
* [A sysadmin's guide to containers](https://opensource.com/article/18/8/sysadmins-guide-containers)
* [Intro to Docker: Why and How to Use Containers on Any System](https://hackaday.com/2018/09/05/intro-to-docker-why-and-how-to-use-containers-on-any-system/)
* [Docker Tutorial: Play With Containers (Simple Examples)](https://dzone.com/articles/docker-tutorial-play-with-containers-simple-exampl)
* [Top Docker Commands Any Expert Should Know](https://dzone.com/articles/top-docker-commands-itsyndicate)
* [A Practical Introduction to Container Terminology](https://developers.redhat.com/blog/2018/02/22/container-terminology-practical-introduction/)
* [Docker – the Best Containerization Platform for an Efficient Software Development](https://www.cabotsolutions.com/2016/12/docker-best-containerization-platform-efficient-software-development/)
* [Why Kubernetes is The New Application Server](https://developers.redhat.com/blog/2018/06/28/why-kubernetes-is-the-new-application-server/)
* [Learning Docker Networking](https://hackernoon.com/learning-docker-networking-part-1-53b09fda9078)
* [How to Install and Use Docker on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04)
* [Removing Docker Images, Containers, and Volumes with Ease](https://medium.com/@jon.froiland/removing-docker-images-containers-and-volumes-with-ease-fdf16bebccec)
* [Docker’s detached mode for beginners](https://medium.freecodecamp.org/dockers-detached-mode-for-beginners-c53095193ee9)
* [Docker for App Dev](https://www.youtube.com/watch?v=tfOqLM9HjRg&list=PL6aLoEodmDP-SwkMXsLPnD2soWE7_2fwl)
* [Building container images with the ansible-bender tool](https://opensource.com/article/19/10/building-container-images-ansible)

## Docker Getting Started
* [A Beginner’s Guide to Understanding and Building Docker Images](https://jfrog.com/knowledge-base/a-beginners-guide-to-understanding-and-building-docker-images/)
* [Using Docker and Docker Compose for Local Development and Small Deployments](https://www.codementor.io/@jquacinella/docker-and-docker-compose-for-local-development-and-small-deployments-ph4p434gb)

## Docker Best Practices
* [Docker Best Practices and Anti-Patterns](https://medium.com/better-programming/docker-best-practices-and-anti-patterns-e7cbccba4f19)
* [Docker: Building Images for Multiple Architectures](https://admantium.medium.com/docker-building-images-for-multiple-architectures-4f142f6dda71)
* [Using Variables in Docker-Compose](https://medium.com/better-programming/using-variables-in-docker-compose-265a604c2006)
* [Create lean Docker images using the Builder Pattern](https://medium.com/@kaperys/create-lean-docker-images-using-the-builder-pattern-37fe2b5d97d4)
* [How To Update Docker Container automatically with nearly zero downtime](https://www.youtube.com/watch?v=5lP_pdjcVMo)
* [Why use Docker containers for machine learning development?](https://aws.amazon.com/blogs/opensource/why-use-docker-containers-for-machine-learning-development/)

* [Docker Networking Tutorial // ALL Network Types explained!](https://www.youtube.com/watch?v=5grbXvV_DSk)
* [Kubernetes explained simply, and why you should learn it!](https://www.youtube.com/watch?v=glFE28QT1HI)

* [Networking for Docker Containers (a Primer) Part I](https://d2iq.com/blog/networking-docker-containers)
* [Networking for Docker Containers Part II: Service Discovery for Traditional Apps and Microservices](https://d2iq.com/blog/networking-docker-containers-part-ii-service-discovery-traditional-apps-microservices)
* [Networking for Docker Containers Part III: Architectural Patterns for Service Registration, Service Discovery, and Load Balancing](https://d2iq.com/blog/networking-docker-containers-part-iii-architectural-patterns-service-registration-service-discovery-load-balancing)

## Docker Volumes
Files (and other data) stored within a Docker container does not persist if the container is deleted.
To overcome this, Docker volumes and bind mounts can be used.

* **Volumes** - Think of volumes as an external hard drive; if the internal hard drive is erased, the external hard drive still retain its own data. Volumes are stored on the host and independent of any container or image. They can be mounted to different containers as needed and, since volumes are separate from the image, they do not increase the image size.
* **Bind Mounts** - Instead of creating a new volume, you can also mount a directory from your host to a Docker container. This is accomplished through bind mounts and is helpful when you want to store and access your a container’s files directly from your system. Compared to volumes, bind mounts have limited functionality.

* [Understanding Docker Volumes](https://www.linode.com/docs/guides/understanding-docker-volumes/)

## Backup a Docker Container to Synology NAS
This process is the same for all Docker containers but will be demoed on a Synology NAS as I feel that’s one of the easiest ways to display what’s actually happening. Summing up the process as easily as I can, when you create a docker container, you mount specific volumes (which are basically folders inside of the container) to a local storage location. On a Synology NAS, that’s generally the docker folder (where you store all your data), however, on other devices, it could be a local storage location. This folder contains all the important information for the container and is ultimately what you want to back up.

In the event that you need to restore a docker container, you are NOT restoring a backup. You are restoring the folders that you backed up, recreating the container exactly as it was, then mounting the folder locations to ensure that the container reads your data.

* [How to Back Up a Docker Container](https://www.wundertech.net/how-to-back-up-a-docker-container/)

## Snap
Canonical has deployed Snappy Ubuntu Core,
a tiny Linux-based operating system for large-scale cloud container deployments,
IoT devices, mobile phones, and anything that needs transitional updates and tiny footprint.
Snappy Ubuntu Core works more or less like Google’s Chrome OS where
it offers transitional image based updates for the system and apps that can be rolled back,
along with confinement that is known in the container world.

But as the article "[Canonical’s Snap: The Good, the Bad and the Ugly](https://thenewstack.io/canonicals-snap-great-good-bad-ugly/)" nicely outlines, does the world need another containerizer on Linux?

* [How To Package and Publish a Snap Application on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-package-and-publish-a-snap-application-on-ubuntu-18-04?utm_source=DigitalOcean_Newsletter)




----



# Learning Ansible
Ansible 101 introduces Ansible for Linux server administration, based on the best-selling book, Ansible for DevOps.

* [Ansible 101 - with Jeff Geerling](https://www.youtube.com/playlist?list=PL2_OBreMn7FqZkvMYt6ATmgC0KAGGJNAN)
    * [Ansible for DevOps: Server and configuration management for humans](https://www.ansiblefordevops.com/)
        * [Ansible for DevOps: Errata and Changes](https://www.ansiblefordevops.com/errata)

* [Ansible Documentation](https://docs.ansible.com/)
* [Ansible GitHub](https://docs.ansible.com/ansible/latest/user_guide/sample_setup.html)



----




##################### REPLACE WITH ~/src/ansible/README.md #####################
# Ansible


Ansible has a great deal of terminology.
The Ansible documentation has glossary that could prove to be helpful.
* [Ansible Glossary](https://docs.ansible.com/ansible/latest/reference_appendices/glossary.html)

* [How to use Ansible to patch systems and install applications](https://opensource.com/article/18/3/ansible-patch-systems)
* [A sysadmin's guide to Ansible: How to simplify tasks](https://opensource.com/article/18/7/sysadmin-tasks-ansible)

* [Ansible Vagrant beginners guide](https://www.inpimation.com/ansible-vagrant-beginners-guide/)
* [Ansible round 2, the awesome stuff](https://www.inpimation.com/ansible-round-2-awesome-stuff/)

* [Reboot and wait for reboot to complete in Ansible playbook](https://www.jeffgeerling.com/blog/2018/reboot-and-wait-reboot-complete-ansible-playbook)
* [Ansible Tutorial for Beginners](https://linuxhint.com/ansible-tutorial-beginners/)
* [19 Minutes With Ansible (Part 1/4)](https://sysadmincasts.com/episodes/43-19-minutes-with-ansible-part-1-4)
* [An Ansible2 Tutorial](https://serversforhackers.com/c/an-ansible2-tutorial)
    * [Ansible: Using Vault](https://serversforhackers.com/c/ansible-using-vault)
    * [Ansible: Roles](https://serversforhackers.com/c/ansible-roles)
* [Vagrant Ansible Provision](https://deparkes.co.uk/2017/12/29/vagrant-ansible-provision/)
* [Getting Started: Writing Your First Playbook](https://www.ansible.com/blog/getting-started-writing-your-first-playbook)
* [Configuration Management 101: Writing Ansible Playbooks](https://www.digitalocean.com/community/tutorials/configuration-management-101-writing-ansible-playbooks)
* [How to use Ansible to patch systems and install applications](https://opensource.com/article/18/3/ansible-patch-systems)

You may have heard of using configuration management tools
like [Chef][17], [Puppet][18], [SaltStack][19], [Terraform][35], [CFEngine][41]
or simply using Bash scripts to provision servers or Vagrant Boxes.
The major difference between other configuration management tools and Anisble,
is that underneath Ansible is just SSH.
Chef and Puppet both have dependencies that must be installed
on the server before you can use them, Ansible does not.
[Ansible is agentless][20] — meaning there are no daemons or agents needed to run a particular action.
It runs on a machine apart from from your VMs
and uses SSH to connect to the servers and run the required commands.
Hence it is a push model, meaning no additional installs are not required at the end point VMs.

Why not just use Bash scripts, then?
Ansible has an edge over Bash scripts because
it features an goal-oriented resource model that
describes the desired state of computer systems and services,
not the paths to get them to this state.
No matter what state a system is in, Ansible understands how to transform it to the desired state.
Ansible is a simple to understand [configuration management approach][42].

Ansible just uses a list of tasks to run in YAML2 format.
Ansible also comes with [idempotency][16] out of the box.
That means you can run the same operation numerous times,
and the output will remain consistent
(i.e. it won't do something twice unless you ask it to).
You can write Bash scripts this way, but it requires quite a bit more overhead.

## Definitions
One important feature in Ansible is that a playbook describes a
desired state in a computer system,
so a playbook can be run multiple times against a server without impacting its state.
If a certain task has already been implemented (e.g., "user sysman already exists"),
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

These definitions and their relationships are depicted here:

[!ansible](https://opensource.com/sites/default/files/u128651/ansible-definitions.png)

* **Ansible Vault:**
* **Inventory:**
* **Modules:**
* **Handlers:**
* **Variables:**

### Tasks vs Roles vs Handlers
Creating and running tasks / playbooks /roles in Ansible can be done in different ways and this can be very confusing.
Knowing the differences in the beginning, and why you should use one or the other, can save hours of researching.
To summerize what Tasks, Roles, and Handlers are:

* **Tasks:** Clear overview of the Tasks to be executed, but could get difficult to understand with longer Playbooks.
* **Roles:** Reusable Tasks that can schedule other Tasks, but it's more difficult to figure out which Tasks are performed.
* **Handlers:** Simple Tasks to be performed at the end, but you can't give them a nice and descriptive name.

Source
* [Ansible: Tasks vs Roles vs Handlers](https://roelofjanelsinga.com/articles/ansible-difference-between-tasks-and-roles/)

### How Do Ansible Playbooks Work?
Ansible modules are executed within tasks. One or more Ansible tasks can be combined to make a play. Two or more plays can be combined to create an Ansible playbook. Ansible playbooks are lists of tasks that automatically execute against hosts. Groups of hosts form your Ansible inventory.

Each module within an Ansible playbook performs a specific task. Each module contains metadata that determines when and where a task is executed, as well as which user executes it.

#### Modules

#### Tasks
Tasks are a limited set of actions to accomplish a well defined task (e.g. install MySql).
They are found within a larger workflow, called a Playbook in Ansible, to accomplish a specific goal (e.g. standup LAMP stack)
These Tasks are specific to a Playbook and can't be shared with other Playbooks.
This is something you should use roles for.

The advantage of using Tasks rather than Roles or Handlers is that, generally,
Tasks are in the same file as the entire Playbook.
This is nice for smaller Playbooks, but gets tough to understand when the Playbook gets longer.
So you will see Tasks directories containing Task files,
but this is where Roles might offer a better way.

#### Roles
Roles are a collection of Tasks that are grouped within a file, under a common name.
Since the are in a separate file, they can be shared across Playbooks.
The advantage of using Roles rather than Tasks is that the Playbook stays small,
and you're also creating reusable workflows that can be added to multiple Playbooks.
The disadvantage is that you won't be able to see what the Playbook is actually running within the Playbook
and you may have to look through multiple directories to be able to figure out what is running at which point in time.

1. Role and Playbook both are the same in principle.
2. You can’t run a Role on its own, you need to include it inside a Playbook
along with the information about which hosts to run on.
3. When installing a Role, you can either install it globally on your machine or locally to a project.
You want it to be local to your project in case multiple projects need different versions of the same dependency.
4. Roles play prime function in Ansible. They keep playbooks clean and readable.
You can store the roles that you created in https://galaxy.ansible.com/, which is a public directory.

#### Playbooks
Playbooks are one of the core features of Ansible and tell Ansible what to execute.
They are like a to-do list for Ansible that contains a list of activates to perform (aka tasks).
A Playbook is simply a list of plays.
The highest level of a Playbook YAML is a list, and on that list only two things are accepted:
a play definition or the keyword import_playbook,
which imports a list of plays from another playbook file,
as if they were defined in that place of the calling file.
The Playbook is also the only thing that can be called directly from ansible-playbook.

1. Playbooks perform a superior role.
2. A Playbook is a big file, that contain all the infrastructure needed to run.
3. Playbooks and Roles are similar but different at the same time.
A Playbook is a standalone file that Ansible can run that contains all of the information
required to set a machine’s state to what you expect.
4. A Playbook can contain Variables, Tasks, Handlers, Roles, and even other Playbooks, all in the same file.
You don’t need any other files to accomplish your task.
5. So, the Playbook is a Master file, which is executable.
The Role file, you cannot execute on its own.

#### Handlers
Handlers are Tasks, but they're executed at the very end of the Playbook.
The advantages of Handlers is that you easily perform certain cleanup Tasks.
That way it's not something that'll get in the way of executing the workflow of Tasks,
but it's also not something you're going to forget.
A disadvantage is that you're not able to give the Handlers a descriptive name
like you can for the Roles and Tasks.

A handler functions for the most part just like a task. However, it is not executed by default, with the other tasks, during the playbook run. Instead, each individual handler will be executed only if notified by a task.

On a task definition, the keyword notify identifies the handlers the task wants to notify. If the task is executed and reports a changed state (not ok nor failed), then the handler will be marked for execution.

After all roles and tasks have run, each notified handler will be executed, in the order they appear in the file.

### Playbook vs Role vs Host
* https://stackoverflow.com/questions/32101001/ansible-playbooks-vs-roles

hosts is a single name for a group of hosts.
It allows you to reference multiple hosts by a single name.

Role is a set of tasks and additional files to configure host to serve for a certain role.

Playbook is a mapping between hosts and roles.

An example goes like this:

* Playbooks: `site.yml`, `webservers.yml`, `fooservers.yml` are playbooks.
* Roles: directories `roles/common/` and `roles/webservers/` contain definitions of common and webservers roles accordingly.

Inside a playbook (e.g. `webservers.yml`) you have something like:

```yaml
- hosts: webservers     <- this group of hosts defined in /etc/ansible/hosts, databases and mail_servers in example from your question
  roles:                <- this is list of roles to assign to these hosts
     - common
     - webservers
```

## Why Ansible?
Unlike Puppet, Chef, and Salt:

* Ansible operates only over SSH and requires no agent on the taget machine.
* It’s writen in Python, a very mature and powerful scripting language.
* It’s self-documenting with simple YAML files describing the playbooks and roles.
* It’s feature-rich; often called "batteries included" hundreds of modules provided out of the box, and new ones are pretty easy to write.

## So what about Terraform?
Both Ansible and Terraform are products for creating infrastructure as code
so you can deploy repeatable environments.
The differences involves the concepts of configuration management and orchestration.
Ansible is primarily a configuration management tool,
and Terraform is an orchestration tool.

Terraform is declarative tool where you define your environment,
and if that environment changes, it fixes it.
Asible is, at least partually, a procedural tool where you describe an application
with the exact steps to be laid out in the code.
Ansible is somewhat of a hybrid.
You can perform ad-hoc commands that allow for procedural-style configuration
or use most of the modules that perform declarative-style.

So Ansible is optimized for configuration management but it can perform orchestration tasks.
Ansible gives greater and far more popular than Terraform.

For more information on the merits of Ansible, check out these sources:
* [What is Ansible, how it works and how it works for me](https://www.linkedin.com/pulse/what-ansible-how-works-me-ivica-kolenka%C5%A1/)
* [Ansible vs. Terraform: Fight!](https://linuxacademy.com/blog/tips/ansible-vs-terraform-fight/)
* [Why use Terraform?](https://www.oreilly.com/learning/why-use-terraform)

## Ansible Roles
One of the satated advantages of Ansible is that it is easy to learn and straightforward to use.
Sounds good, doesn’t it?  It is, with one exception.
Getting up and running with a limited knowledge of the features and best practices
often means creating superficial and inflexible roles.
But to quote the Ansible documentation about roles:
“You absolutely should be using roles. Roles are great. Use roles.
Roles! Did we say that enough? Roles are great.”.

One of the reasons why roles are great is that they are **reusable**.
At least they are meant to be.
To creating reusable Ansible roles,
you need to follow best practices, and is not as easy as it sounds.

## Ansible Playbook
How do you tell Ansible what actions to take on the server?
You write a playbook.
An Ansible playbook is written in a simplified subset of YAML,
which is highly readable and easy to pick up. A sample playbook looks like this:

```yaml
```

You can declare variables in your playbook, run loops and use conditionals. Playbooks are divided into sections. For example, tasks are defined in a special “tasks” section, while variables are declared in a special “vars” section, and handlers are defined in a special “handlers” section.

The tasks section is a list of commands, to be run on the remote computers, or if specified as a local action, on the Ansible server. Handlers are special tasks that, if signaled with a notify statement, are run at the end of a play.

Every task runs a corresponding Ansible module. For example, I can run the push code from Github by calling the git module:

```yaml
```

This task invokes Ansible’s git module, grabs code from the specified git url and pushes it in the destination directory. The module cleans up after itself — Ansible does not leave any cruft from executing the module on your server.

When you install Ansible, it ships with over 500 modules, which more than covers most basic needs. There are preexisting modules that execute bash commands, push code and config files, deploy and manage Docker containers, install packages, and yes, specifically manage your Rackspace account. A complete list of modules is found on the Ansible docs website.

If you want to develop your own modules, you can — the modules can be written in any language; the only hard and fast requirement is that it must return a JSON object.

To run your playbook, use the command “sudo Ansible-playbook –i inventory.txt main.yml” and watch your playbook run.

## Creating A Role
When creating a new role,
the first step is to build its directory structure.
Since version 1.4.2, Ansible provides a tool to create the base directory structure.
The tool is called `ansible-galaxy` and below is an example on how to use it:

```bash
$ ansible-galaxy init levono.config
lenovo.config was created successfully
```

## Inventory
In order to be able to set up the connection to servers Ansible is configuring,
an [Inventory][31] file is needed.
This file can have any name, but the convention is to name it "hosts"
and by default this file is located at `/etc/ansible/hosts`.
(Don’t mix it up with `/etc/hosts` file because they are not the same.
The `hosts` inventory file is [structured like an `.ini` file][21],
with the example shown below:

```
[loadbalancers]
loadbalancer1
loadbalancer2

[webservers]
web1.ans
web2.ans

[all_servers:children]
loadbalancers
webservers
```

An inventory can have standalone servers, grouped servers, and groups can be added to other groups.
Group names are defined inside square brackets [ ].
The above example shows groups "loadbalancers" and "webservers" which have multiple hosts in them.
Also, there is a parent group named "all_servers"
which is composed of previously defined groups.
A server can exist in multiple groups without issue.
It is also possible to create a dynamic inventory.
This is extremely useful if you are working with virtual machines hosted on any public cloud services.
find more details on [official Ansible docs on dynamic inventory][22].
The Ansible host file can handle significantly more advanced functionality than what I am using.
For more information, see the [Inventory documentation][40].

## Modules
Inventory is what servers Ansible is connected to.
What Ansible does with them is defined by modules.
Modules are components installed with Ansible that do all the heavy lifting configuration tasks.

Modules can be classified as core and extra modules.

* Core modules come with Ansible and are built and maintained by Ansible Inc. and RedHat employees.
* Extra modules can be easily installed using your distribution’s package manager or directly from GitHub.

Ansible is an open-source tool
(meaning that everyone can contribute code to it but Ansible Inc.
but they have final say as to what changes to the code base will be accepted.
Some of the core modules are copy, user, npm, ping, setup, cron, hostname and many others.
Continuously growing list of modules is available at [official Ansible docs: All Modulep][23].

Majority of modules expect one or more arguments that tune the way a module works.
For example, the `copy` module has _src_ and _dest_ arguments
that tell the module what is the source and destination of the file or directory to be copied.
Running this module from command line can look similar to this:

```bash
ansible -m copy -a "src=my_app.zip dest=/var/www/html"
```

## Tasks
Ansible modules can be invoked directly from the command line,
but they are rarely used in this way, but generally executed as a task.
Tasks are atomic actions with defined by name and an accompanying module.
Here is an example:

```
- name: install mysql
  yum: name=mysql state=install
```

In the example, the _name_ of the task is “install mysql”,
module to be use is _yum_,
The module has two arguments, first being _name_ argument refereing
to the package which needs to be in the _state_ of “installed”.

AN Ansible task does not expect commands or functions that do something
Ansible tasks describe the desired state of the configured server.
If a package named “mysql” is installed, Ansible will not install it again.
This means that it is perfectly safe to run tasks several times
as they will not alter the system if its configuration is in the state described in those tasks.

A single task can only use one module.
If, for example, I wanted to install MySQL and start the mysqld service,
I would need two tasks to achieve that.
However, many modules support “with_items” construct which acts as a loop,
providing different value to the module on each iteration.
For example, yum and apt modules can be used in a following way:

```
- name: install common packages
  yum: name={{ item }} state=present
  with_items:
    - mysql
    - httpd
    - php
    - phpmyadmin
```

Ansible will internally loop over the items and create an array which will be used with the yum module.
In essence, the following command will be generated internally, and it will be executed only once:

```bash
yum -y install mysql httpd php phpmyadmin
```

## Playbooks
Example Playbooks -
* https://github.com/twobitcircus/rpi-build-and-boot
* https://www.ansible.com/blog/getting-started-writing-your-first-playbook
* https://gist.github.com/marktheunissen/2979474
* https://leucos.github.io/ansible-files-layout
* https://deliciousbrains.com/automating-server-setup-ansible/
* Run ansible on a single host - https://coderwall.com/p/tx91cw/run-ansible-on-a-single-host

Tasks for themselves have no real use case, so they are combine into playbooks.
Playbooks are collections of tasks that describe a state of the configured server
and are executed to configure it.
Playbooks are written in YAML.
An example playbook may look like this:

```yaml
- name: Common tasks
  hosts: webservers
  become: true
  tasks:
    - name: task 1
    .
    .
    .
  handlers:
  - name: handler 1
```

The first line starting with _name_ is the playbook name.
Next line tells Ansible on which hosts (from the `hosts`inventory file)
to apply the tasks from this playbook.
Third line contains _become_ which tells Ansible that it should
run the tasks with elevated privileges; e.g. as super user.
Next comes the list of tasks to perfrom.
Finally comes the definition of _handlers_ are defined.
More on handlers in the next section.

Tasks will be executed one by one in the order they are written in.
It is important to note that in the situation where Ansible executes a playbook on several servers,
tasks are running in parallel on all servers.

It is expected that sometimes a task or more tasks will fail for some reason.
In this case, Ansible will stop playbook execution and allow you to fix the error.
Running the same playbook again is completely safe.

* [Working With Playbooks](https://docs.ansible.com/ansible/latest/user_guide/playbooks.html#working-with-playbooks)
* [Ansible Playbook Structure](http://www.oznetnerd.com/ansible-playbook-structure/)

## Handlers
During the configuration process,
there is sometimes a need to conditionally execute a task.
Handlers are one of the conditional forms supported by Ansible.
A handler is similar to a task, but it runs only if it was notified by a task.
A task will fire the notification if Ansible recognizes that the task
has changed the state of the system.

An example situation where handlers are useful is when
a task modifies a configuration file of some service, MySQL for example.
In order for changes to take effect, the service needs to be restarted.

```yaml
- name: change mysq max_connections
  copy: src=edited_my.cnf dest=/etc/my.cnf
  notify:
    - restart_mysql
```

Notify keyword acts as a trigger for the handler named “restart_mysql”.
Handlers are tasks with a few differences:
(1) they must have an unique name,
(2) they will not run if not triggered by a task.

Several tasks may trigger the same handler and it will run only once.
This is a nice feature,
since handlers are most commonly used to restart services or reboot servers.

## Variables
Ansible is not a programming language
but it has certain features common to programming languages, such as variables.
Variables are really useful because they can be defined in several places:
in the playbook, in inventory file, in special files reserved for variables,
they can be set at runtime on CLI, or they can be automatically collected.
In order to use variables in playbooks, you need to surround them with curly braces:

```yaml
- name: Common tasks
  hosts: db_servers
  become: true
  vars:
    mysql_config_path: /etc/my.cnf
  tasks:
  - name: change mysql max_connection
    copy: src=edited_my.cnf dest="{{ mysql_config_path }}"
```

This code excerpt contains one difference from previous code,
which is the “vars” section.
This section is used for defining variables inside playbooks.
When the playbook is executed, name of the variable will be substituted with its value.
(**NOTE:** For security reasons, variable names have to be quoted to disable any malicious code in them.)

Variables can also be combined:

```yaml
vars:
  file_name: my_app.zip
  server_name: http://myhost.com
  file_location: {{ server_name }}/files/{{ file_name }}
```

Another great thing about variables is that they can be
created dynamically while a playbook is running.
This is achieved by using the “register” keyword in a task.
An example shown below will create a new variable named “logged_in_user“
from the output of “whoami” command:

```yaml
- name get current logged in user
  command: whoami
  register: logged_in_user
```

As a final note,
when Ansible connects to a server it runs one of the core modules named “setup”.
This module collects information such as operating system name,
operating system version, hardware and network configuration and so on.
This data is known as facts and they are cached for as long as the playbook is running
and can be used just as variables are, with curly braces.

## YAML
Ansible playbooks are written in [YAML][27]
because it is easier for humans to read & write than other common data formats like XML or JSON.
YAML is a [data serialisation language][26],
it’s a strict superset of JSON,
with the addition of syntactically significant newlines and indentation, like Python.
Unlike Python, however, YAML doesn’t allow literal tab characters for indentation.

* [YAML best practices for Ansible playbooks - tasks](https://www.jeffgeerling.com/blog/yaml-best-practices-ansible-playbooks-tasks)

### Lint Tools

* [Disabling checks for a specific line](https://yamllint.readthedocs.io/en/stable/disable_with_comments.html)
* [Disabling checks for all (or part of) the file](https://yamllint.readthedocs.io/en/stable/disable_with_comments.html#disabling-checks-for-all-or-part-of-the-file)

although not recommend, to disabled all rules for a specific line:

```yamllint
# yamllint disable-line
-  {    all : rules ,are disabled   for this line}

too long of a line .......  yamllint disable-line rule:line-length
```

**`yamllint`**
* A linter for YAML files - `sudo apt-get install yamllint`
* [A linter for YAML files](https://github.com/adrienverge/yamllint)
* [yamllint documentation](https://yamllint.readthedocs.io/en/stable/)

**`ansible-lint`**
* [Ansible Lint Documentation](https://ansible-lint.readthedocs.io/en/latest/)

```bash
# install lint tools
sudo apt-get install yamllint ansible-lint
```

```yaml
# place these linting rules in ~/.config/yamllint/config
---
extends: default

ignore: |
  *.template.yaml

rules:
  empty-lines: disable
  line-length:
    max: 200
    level: warning
```

## Key Ansible Files

### ansible.cfg File
The `ansible.cfg` file contains the locations of our inventory and roles:

```ymal
File: ansible.cfg
-----------------

[defaults]
hostfile = hosts
roles_path = galaxy:roles
```

### hosts File
The `hosts` file is our inventory.
This defines the list of hosts machines,
together with their group membership and login credentials.

```bash
File: hosts
-----------

[lemp]
xxx.xxx.xxx.xxx ansible_ssh_user=bencer
```

### modules Directory
If you need to download any 3rd party modules:

```bash
$ mkdir galaxy
$ ansible-galaxy install --roles-path=./modules/roles jdauphant.NGINX
$ ansible-galaxy install --roles-path=./modules/roles debops.php5
```

## Ansible Vault
A common method for using Ansible is to set up passwordless
SSH keys to facilitate ease of management.
For now, simply generate an SSH key with the following command:

```bash
# generating An SSH Key
ssh-keygen

# copy key to remote host
ssh-copy-id root@remote-host
```

* [Say YES to Password-free SSH Access!](https://medium.com/100-days-of-linux/say-yes-to-password-free-ssh-access-c7a7fa315cd7)
* [Ansible Vault: Maintaining Secure Secrets in Ansible | Jungle Disk](https://www.jungledisk.com/blog/2017/06/26/maintaining-secure-secrets-in-ansible/)
* [How Ansible Vault Works](https://serversforhackers.com/c/how-ansible-vault-works)
* [How To Use Vault to Protect Sensitive Ansible Data on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-use-vault-to-protect-sensitive-ansible-data-on-ubuntu-16-04)

## Ansible Galaxy Roles
[Ansible Galaxy][33], is a free site for finding, downloading, and sharing community developed roles.
It's analogous to Vagrant's XXX or Docker's XXX.
Use the Galaxy search page to find roles for your project,
you then download them onto your Ansible host using `ansible-galaxy`,
the command line tool that comes bundled with Ansible.

You can use Galaxy to jump-start your automation project via
packaged units of work known to Ansible as roles.
Roles can be dropped into Ansible PlayBooks and immediately put to work.
You’ll find roles for provisioning infrastructure,
deploying applications, and all of the tasks you do everyday.

Use [Galaxy’s Search page][29] to find roles for your project,
then download them onto your Ansible host using the command-line utility [`ansible-galaxy`][34].


* [How to Use Ansible Roles to Abstract your Infrastructure Environment](https://www.digitalocean.com/community/tutorials/how-to-use-ansible-roles-to-abstract-your-infrastructure-environment)
* [Excellent Galaxy Examples](https://galaxy.ansible.com/geerlingguy)


### Ansible Galaxy Useful Commands
Usage: ansible-galaxy [delete|import|info|init|install|list|login|remove|search|setup] [--help] [options] ...

If you want to directly install Ansible Galaxy role into your porjects `roles/` directory,
you'll need to append the `-p` flag,
and the path (relative or absolute) to your project's roles directory.
Otherwise they get installed in a global locations
`~/.ansible/roles` or `/usr/share/ansible/roles`.

So when you run `ansible-galaxy install -p ~/src/ansible-roles geerlingguy.dotfiles`
it gets installed at `~/src/ansible-roles`:

```bash
# install role to global directory

# install roles to your personal directory, not globally
$ ansible-galaxy install -p  ~/src/ansible-roles geerlingguy.dotfiles
- downloading role 'dotfiles', owned by geerlingguy
- downloading role from https://github.com/geerlingguy/ansible-role-dotfiles/archive/1.2.0.tar.gz
- extracting geerlingguy.dotfiles to /home/jeff/src/ansible-roles/geerlingguy.dotfiles
- geerlingguy.dotfiles (1.2.0) was installed successfully

# list the roles installed globally
$ ansible-galaxy list
- geerlingguy.git, 2.0.2
 [WARNING]: - the configured path /usr/share/ansible/roles does not exist.

# remove the role from the global directory
ansible-galaxy remove geerlingguy.git
```

In a way similar to the `pip freeze` command,
you can create a requirements file.
You can do this by running:

```bash
# create list for reimporting roles
ansible-galaxy list -p ~/src/ansible-roles >> galaxy-roles.txt
```

You then can reimport the whole bunch of useful roles with a single command:

```bash
ansible-galaxy install -r galaxy-roles.txt -p roles
```

Some other useful commands are:

```bash
# create a role in a format ready for submission to the Galaxy community
ansible-galaxy init my-new-role

# show currently installed roles
ansible-galaxy list

# removes a currently installed role
ansible-galaxy remove [role name]
```

### Getting Started and Best Practices with Ansible
* [A developer's shortcut to getting started with Ansible](https://www.redhat.com/en/blog/developers-shortcut-getting-started-ansible)
* [Ansible and Ansible Tower: best practices from the field](http://www.juliosblog.com/ansible-and-ansible-tower-best-practices-from-the-field/)

#### Running Ad-Hoc Ansible Commands
After you have copied your SSH keys to all the servers in your inventory,
you are ready to start using Ansible.
A basic Ansible function is the ability to run ad hoc commands.
The syntax is: `ansible -a "some command"`.

A useful ad hoc command would be the Ansible ping module,
which is used to verify that a server is ready to receive commands:

```bash
# ping all machines in the inventory
ansible -i inventory all -m ping
ansible -i 192.168.1.79, all --module-name ping --user pi --ask-pass
```

This will result in Ansible attempting to log in via SSH to all of the servers in your inventory.

Check this out
Ansible playbook "push_ssh_keys.yaml" - https://opensource.com/article/17/7/automate-sysadmin-ansible

#### Testing Ansible Roles
* [Testing Ansible roles with Molecule](https://opensource.com/article/18/12/testing-ansible-roles-molecule)

#### Ansible and Executing Remote Commands
Sometimes, all you need is to execute commands
directly on target hosts as you would on a bash shell.
Ansible shell module comes in handy to do this.
By default, the shell module uses the `/bin/sh` shell to run commands,
although you can configure it to use other shells.

>**NOTE:** Unlike the shell module,
>the command module is not affected the remote user’s shell environment.

>**NOTE: Since commands are not executed on the shell,
>the command module does not support environment variables,
>pipes and other operators such as `>` , `<` , `&`, `;` and `| |`.
>With shell module, piping, redirection and variables are fully supported.
>Thus, the shell module provides more flexibility.

```bash
# check if your targets are live on the network
ansible -i inventory all --module-name ping
ansible -i inventory all --module-name shell --args "ping"

# print condense output
$ ansible -i inventory all --module-name ping --one-line
test-pi | SUCCESS => {"changed": false,"ping": "pong"}

# check the uptime of all the target hosts
ansible -i 192.168.1.79, all --module-name shell --args "uptime -p" --user pi --ask-pass
ansible -i inventory test-pi --module-name shell --args "uptime -p"
```

Sources:
* [Getting Started With Ansible Ad Hoc Commands](https://ostechnix.com/ansible-ad-hoc-commands/)
* [How to Run Remote Commands with Ansible Shell Module](https://www.cherryservers.com/blog/how-to-run-remote-commands-with-ansible-shell-module)

#### Ansible and Gathering Facts
Ansible facts are data gathered about target nodes (host nodes to be configured) and returned back to controller nodes.
The information can be an IP address, operating system, filesystem and more.
This information gathering is taken care of by the "setup" module.

Ansible facts are stored in JSON format and are used to make important decisions about tasks based on their statistics.
Facts are in an `ansible_facts` variable, which is managed by Ansible Engine.
Ansible facts play a major role in syncing with hosts in accordance with real-time data.

```bash
# for remote server not managed by ansible
ansible -i 192.168.1.79, all --module-name setup --user pi --ask-pass

# filter the gathered facts
ansible -i 192.168.1.79, all --module-name setup --args "filter=ansible_all_ipv4_addresses,ansible_default_ipv4,ansible_distribution*" --user pi --ask-pass

# if you have an inventory established and ssh keys installed for ansible
ansible -i inventory test-pi --module-name setup
ansible -i inventory test-pi --module-name gather_facts

# writing the facts to a file
ansible -i inventory test-pi --module-name setup --tree /home/ansible/facts      # write permision problem
```

Sources:
* [Explaining Ansible Facts With Examples](https://ostechnix.com/ansible-facts/)
* [Ansible Facts](https://www.educba.com/ansible-facts/)
* [An introduction to Ansible facts](https://www.redhat.com/sysadmin/playing-ansible-facts)

## Install Ansible
One of the beauties of Ansible is that it will not add a database,
and there will be no daemons to start or keep running.
You only need to install it on one machine
and it can manage an entire fleet of remote machines from that central point.
It does not leave software installed or running on them,
so there’s no real question about how to upgrade Ansible when moving to a new version.

Below we will create Ansible Playbooks for:

* [Nginx][38] is a popular web server which can also be used as a reverse proxy,
load balancer, API gateway, mail proxy etc.
We'll create an Ansible role to setup and configure Nginx web server.

* [How to NGINX Reverse Proxy with Docker Compose](https://dzone.com/articles/how-to-nginx-reverse-proxy-with-docker-compose)

Some good videos for learning Ansible can be found [here][37].

### Step 1: Installing Ansible - DONE
There are multiple ways for you can install Ansible on your system.
You can install Ansible via a Linux PPA (Personal Package Archives)
or via a Pyhton's `pip` package management system.
I'm using the preferred method of Python Package Manager (`pip`) since its the most current:

```bash
# check if you have ansible installed and its version (you should have at least 2.10)
$ ansible --version
ansible 2.9.6
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/home/jeff/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  executable location = /usr/bin/ansible
  python version = 3.8.10 (default, Jun  2 2021, 10:49:15) [GCC 9.4.0]

# remove the old version of ansible
sudo apt remove ansible

# install ansible via pip
#python3 -m pip install ansible
pip install ansible

# test the ansible installation
$ ansible --version
ansible [core 2.11.5]
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/home/jeff/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /home/jeff/.local/lib/python3.8/site-packages/ansible
  ansible collection location = /home/jeff/.ansible/collections:/usr/share/ansible/collections
  executable location = /home/jeff/.local/bin/ansible
  python version = 3.8.10 (default, Jun  2 2021, 10:49:15) [GCC 9.4.0]
  jinja version = 2.10.1
  libyaml = True
```

If you wish to upgrade Ansible,
then you use this command:

```bash
# upgrade ansible to the latest version
#python3 -m pip install --upgrade ansible
pip install --upgrade ansible
```

To remove a `pip` installed Ansible, use this command:

```bash
# remove ansible
#python3 -m pip uninstall ansible
pip uninstall ansible
```

>**NOTE:** If you prefer PPA installation of Ansible on your system,
>run the following commands:
>
>```bash
># update and install prerequisites
>sudo apt-get update
>sudo apt-get upgrade
>sudo apt-get install software-properties-common
>
># add ansible official repository to your system’s software source and install ansible
>sudo apt-add-repository -y ppa:ansible/ansible
>sudo apt-get update
>sudo apt-get install -y ansible
>
># test the ansible installation
>$ ansible --version
>ansible 2.6.1
>  config file = /etc/ansible/ansible.cfg
>  configured module search path = [u'/home/jeff/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
>  ansible python module location = /usr/lib/python2.7/dist-packages/ansible
>  executable location = /usr/bin/ansible
>  python version = 2.7.14 (default, Sep 23 2017, 22:06:14) [GCC 7.2.0]
>```

### Step 2: Install Docker Extension - DONE
To manage Docker containers on remote machines,
you need to install the Docker Ansible-Galaxy extension for Ansible:

```bash
# install the docker extention for ansible
ansible-galaxy collection install community.docker

# check to see if it is installed
$ ls ~/.ansible/collections/ansible_collections/community/
docker/
```

####################### REMOVE TEXT BETWEEN THESE LINES ########################
### Step 2: Set Your Ansible Path
Now configure your environmental variable `ANSIBLE_ROLES_PATH`.
This path is where Ansible Galaxy will save every role you install
and where Ansible will look when resolving the imports from your playbook.
The default path is `/etc/ansible/roles` or `$HOME/.ansible`.
Make sure that the user installing the roles has write permissions on the directory.

I put put the following in my `.bashrc` file:

```bash
# setup for ansible environment
export ANSIBLE_ROLES_PATH="$HOME/src/ansible-roles"
```
####################### REMOVE TEXT BETWEEN THESE LINES ########################

### Step X: Installing Vim Plugin for Ansible
The Vim plugin, `ansible-vim` is a syntax plugin for Ansible 2.x,
it supports YAML playbooks, Jinja2 templates, and Ansible's hosts files.

### Step X: Clone Ansible Galaxy Roles
The `ansible-galaxy install ...` command clones the role repository found on Ansible Galaxy.
These repositories are an excellent starting point for roles you may be interested in creating.

```bash
# clone your desired ansible roles from galaxy to default directroy (~/.ansible/roles)
ansible-galaxy install geerlingguy.git

# clone your desired ansible roles from galaxy to current directory
ansible-galaxy install geerlingguy.dotfiles ---roles-path=./
```

### Step X: Create Your Remote Hosts - DONE
The Ansible host computers could exist anywhere as long as they are reachable via SSH.
For this exercise, I'm going to assume the host is on my Ansible server
as Vagrant instances.

So our next step will be to create our Vagrant file that will for our Nginx.

```bash
# list the boxes you have installed on your host
$ vagrant box list
ubuntu/trusty64 (virtualbox, 20180227.0.1)
ubuntu/xenial64 (virtualbox, 20180706.0.0)

# move to directory for vagrant vm
cd  ~/src/vagrant_machines
mkdir nginx
cd nginx

# create a base Vagrantfile (Ubuntu 16.04) and bring it up
vagrant init ubuntu/xenial64
vagrant up

# login to the machine to make sure its working
vagrant ssh
```

### Step X: Set Up SSH Keys
Ansible primarily communicates with client computers through SSH.
While it has the ability to handle password-based SSH authentication,
using SSH keys can help to keep things simple.
Check [here][39] if you need more information concerning SSH and its keys.

For our example here, where we are creating our Ansible hosts as Vagrant instances,
this setup and exchange of SSH keys isn't necessary.
It will be necessary if the Ansible host is remote.

#### Copying Public Key Using ssh-copy-id
A simpler method is to use the `ssh-copy-id` tool
included by default in many operating systems.
Launched from the Ansible server, the syntax is:
`ssh-copy-id username@remote_host`.

#### Copying Public Key Using SSH
If you do not have `ssh-copy-id` available,
but you have password-based SSH access to an account on your server,
you can upload your keys using a conventional SSH method:

```bash
# copying public key using ssh
cat ~/.ssh/id_rsa.pub | ssh username@remote_host "mkdir -p ~/.ssh && touch ~/.ssh/authorized_keys && chmod -R go= ~/.ssh && cat >> ~/.ssh/authorized_keys"
```

#### Copying Public Key Manually
Assuming SSH is already established on your Ansible server,
use the `cat` command to print the contents of your
non-root user’s SSH public key file to the terminal’s output:

```bash
# copy this public ssh key
cat ~/.ssh/id_rsa.pub
```

Copy the resulting output to your clipboard,
then open a new terminal and connect to one of your Ansible hosts using SSH,
and do the following:

1. Switch to the client machine’s root user.
1. As the root user, open the `authorized_keys` within the `~/.ssh` directory:
1. In the file, paste your Ansible server user’s SSH key, then save the file.

### Step X: Create Vagrantfile and Ansible Playbook
Next we create our Vagrant file that will be for our Nginx.

```bash
# list the boxes you have installed on your host
$ vagrant box list
ubuntu/trusty64 (virtualbox, 20180227.0.1)
ubuntu/xenial64 (virtualbox, 20180706.0.0)

# move to directory for vagrant vm
cd  ~/src/vagrant_machines
mkdir nginx
cd nginx

# create a base Vagrantfile (Ubuntu 16.04) and bring it up
vagrant init ubuntu/xenial64
vagrant up

# login to the machine
vagrant ssh
```

### Step X: Creating Ansible Nginx Role
Ansible Galaxy

### Step X: Creating Ansible Nginx Playbook
Next we create the Ansible Playbook that will be used within the Vagranfile.
Using a text editor, we create the following Playbook call `nginx.yml`:

```
 - hosts: web
   sudo: yes
   user: root

   tasks:
    - name: Add Nginx Repository
      apt_repository: repo='ppa:nginx/stable' state=present
      register: ppainstalled

    - name: Install Nginx
      apt: pkg=nginx state=latest update_cache=true
      when: ppainstalled|success
      notify:
       - Start Nginx

   handlers:
    - name: Start Nginx
      service: name=nginx state=started
```

So our Vagrantfile should now look like the following
to make use of the Ansible Playbook:

```bash
```

### Step X: Ansible Configuration Settings
Ansible supports several sources for configuring its behavior (see [here](https://docs.ansible.com/ansible/latest/reference_appendices/config.html))
The `ansible-config` utility allows users to see all the configuration settings available,
their defaults, how to set them and where their current value comes from.
See [`ansible-config` man page](https://docs.ansible.com/ansible/latest/cli/ansible-config.html#ansible-config) for more information.

The Ansible configuration file can be placed in multiple location but I recommend `$HOME`.
As a starting point for you own configuration file,
You can generate a fully commented-out example `$HOME/.ansible.cfg` file via the following:

```bash
# you can generate a fully commented-out file via the following
ansible-config init --disabled > $HOME/.ansible.cfg

# you can also have a more complete file that includes existing plugins
ansible-config init --disabled -t all > $HOME/.ansible.cfg

# set your environment in you shell configuration
export ANSIBLE_CONFIG=$HOME/.ansible.cfg

# for security
chmod go-rwx $HOME/.ansible.cfg
```

### Step X: Creating Hosts File
Ansible needs to know your remote server names or IP address.
This information is stored in a file called `hosts` and often referred to as your "inventory".
The default file is `/etc/ansible/hosts`.
You can edit this one or create a new one in your `$HOME` directory,
or better yet, place the `hosts` file in your projects directory reference it
on the command-line when running ansible.

### Step X: Update and Reboot
[Ansible reboot a Debian/Ubuntu Linux for kernel update and wait for it](https://www.cyberciti.biz/faq/ansible-reboot-debian-ubuntu-linux-for-kernel-update-waitforit/)

##################### REPLACE WITH ~/src/ansible/README.md #####################

# Ansible Molecule
Molecule project is designed to aid in the development and testing of Ansible roles.

* [Rapidly Build & Test Ansible Roles with Molecule + Docker](https://www.toptechskills.com/ansible-tutorials-courses/rapidly-build-test-ansible-roles-molecule-docker/)
* [How To Test Ansible Roles with Molecule on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-test-ansible-roles-with-molecule-on-ubuntu-18-04)



----



# Docker

* [How to install Docker and Hello World](https://www.youtube.com/playlist?list=PLRAV69dS1uWTJLvDP4Veld5F05rJAmOcp)

## Docker Hub

## Installing Docker

### Step 1: Installing Docker - DONE
To install Docker manually, go to the [Docker installation page][58].
There are multiple methods but I'm using the recommend method using [Docker’s repositories][60].

Source:
* [Docker explained simply](https://www.youtube.com/watch?v=_trJf3GbZXg&list=RDCMUCZNhwA1B5YqiY1nLzmM0ZRg&index=2)
* [How To Install and Use Docker on Ubuntu 20.04](https://phoenixnap.com/kb/install-docker-on-ubuntu-20-04)

```bash
# check the currently install verson of docker
docker --version

# uninstall any old version of docker (called docker, docker.io, or docker-engine)
sudo apt-get remove docker docker-engine docker.io containerd runc

# update the apt package index and install packages
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release

# add docker’s official gpg key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# set up the stable repository
 echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] \
    https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" \
    | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# install the latest version of docker engine
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io

# install a specific version of docker engine, list the available versions in the repo
$ apt-cache madison docker-ce
 docker-ce | 5:20.10.8~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:20.10.7~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:20.10.6~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:20.10.5~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:20.10.4~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:20.10.3~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:20.10.2~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:20.10.1~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:20.10.0~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:19.03.15~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:19.03.14~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:19.03.13~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:19.03.12~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:19.03.11~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:19.03.10~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
 docker-ce | 5:19.03.9~3-0~ubuntu-focal | https://download.docker.com/linux/ubuntu focal/stable amd64 Packages

# install a specific version using the version string from the second column
# sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io
sudo apt-get install docker-ce=5:20.10.8~3-0~ubuntu-focal docker-ce-cli=5:20.10.8~3-0~ubuntu-focal containerd.io

# check the currently install version of docker
$ docker --version
Docker version 20.10.8, build 3967b7d
```

### Step 2: Verify Docker Installation - DONE
Next we'll verify that Docker Engine is installed correctly by running the `hello-world` image.
This command downloads a test image and runs it in a container.
When the container runs, it prints a message and exits.

```bash
# verify that docker engine is installed correctly
$ sudo docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
b8dfde127a29: Pull complete
Digest: sha256:61bd3cb6014296e214ff4c6407a5a7e7092dfa8eefdbbec539e133e97f63e09f
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

To find out the status of Docker containers,
used these commands:

```bash
# list running docker containers
$ sudo docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

# list all containers, both running and stopped
$ sudo docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                      PORTS     NAMES
3536f50560bc   hello-world   "/hello"   12 minutes ago   Exited (0) 12 minutes ago             laughing_colden

# list the total file size of each container
$ sudo docker ps -a -s
CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                      PORTS     NAMES             SIZE
3536f50560bc   hello-world   "/hello"   14 minutes ago   Exited (0) 14 minutes ago             laughing_colden   0B (virtual 13.3kB)
```

### Step 3: Upgrade Docker Engine - DONE
To upgrade Docker Engine, first run `sudo apt-get update`,
then follow the installation instructions, choosing the new version you want to install:

```bash
sudo apt-get update
apt-cache madison docker-ce
sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io
```

### Step 4: Useful Docker Commands
* [What is Docker?](https://phoenixnap.com/kb/what-is-docker)
* [Docker vs. Kubernetes](https://phoenixnap.com/kb/docker-vs-kubernetes)
* [Kubernetes vs Docker Swarm: What are the Differences?](https://phoenixnap.com/blog/kubernetes-vs-docker-swarm)
* [How to List / Start / Stop Docker Containers](https://phoenixnap.com/kb/how-to-list-start-stop-docker-containers)
* [How to Use Docker Run Command with Examples](https://phoenixnap.com/kb/docker-run-command-with-examples)
* [How To Remove Docker Images, Containers, Networks & Volumes](https://phoenixnap.com/kb/remove-docker-images-containers-networks-volumes)
* [How to Set Up and Use Private Docker Registry](https://phoenixnap.com/kb/set-up-a-private-docker-registry)
* [How to Manage Docker Containers? Best Practices](https://phoenixnap.com/kb/docker-container-management)

```bash
# list installed images
sudo docker images
```

### Step 5: Uninstall Docker Engine

```bash
# uninstall the docker engine, the cli, and containerd packages
sudo apt-get purge docker-ce docker-ce-cli containerd.io

# delete all images, containers, and volumes
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd

# you must delete any edited configuration files manually
```

## Develop with Docker
* [Develop with Docker](https://docs.docker.com/develop/)
* [How to Deploy NGINX Reverse Proxy on Docker](https://phoenixnap.com/kb/docker-nginx-reverse-proxy)
* [How to Deploy and Manage MongoDB with Docker](https://phoenixnap.com/kb/docker-mongodb)
* [How to Containerize Legacy Applications](https://phoenixnap.com/kb/how-to-containerize-applications)
* [Docker Volumes: How to Create & Get Started](https://phoenixnap.com/kb/docker-volumes)
* [Docker and Running your self-hosted applications in a more secure way behind a reverse proxy.](https://www.youtube.com/watch?v=8T68pB_Fkm4)

## Install Docker Compose
[Docker Compose][62] is a tool for defining and running multi-container Docker applications.
With Compose, you use a YAML file to configure your application’s services.
Then, with a single command, you create and start all the services from your configuration.

* [Docker-compose tutorial](https://www.youtube.com/watch?v=qH4ZKfwbO8w)
* [Overview of Docker Compose](https://docs.docker.com/compose/)
* [Install Docker Compose](https://docs.docker.com/compose/install/)
* [How to Install Docker Compose on Ubuntu 20.04](https://phoenixnap.com/kb/install-docker-compose-on-ubuntu-20-04)
* [How to Install Docker and Docker Compose on Linux](https://www.cloudsavvyit.com/10623/how-to-install-docker-and-docker-compose-on-linux/)

### Step 1: Download the Latest Docker Compose Version
`docker-compose` is a separate binarya from Docker,
and it is best downloaded directly from the project’s GitHub releases.
Head to [Docker Compose’s releases page][63] and take note of the latest version number.
At the time of writing, it was `2.5.1`.

```bash
# download docker-compose binary
#sudo curl -L "https://github.com/docker/compose/releases/download/2.5.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo apt install docker-compose

# make the file executable
#sudo chmod +x /usr/local/bin/docker-compose

# check docker-compose status
docker-compose --version
```

### Step 2: Creating a Simple Docker-Compose File

### Step 3: Uninstall Docker Compose
Uninstalling Docker Compose from your Ubuntu system requires 3-step:

```bash
# delete the docker-compose if you installed binary (as done above)
sudo rm /usr/local/bin/docker-compose

# remove software package if you used apt
sudo apt remove docker-compose

# uninstall if you installed using pip
pip uninstall docker-compose
```

## Install Portainer
Adopting container orchestration platforms like Kubernetes can be hard.
[Portainer][61] is a popular Docker UI that helps you visualise your
containers, images, volumes and networks.
Portainer helps you centrally configure, manage and secure containerized environments,
regardless of where they are hosted.
It helps you take control of the Docker resources on your machine, avoiding lengthy terminal commands.

Portainer can be deployed to Docker, Docker Swarm, or Kubernetes environments
and comprised of two elements: the Portainer Server, and the Portainer Agent.
I going to deploy Portainer via Docker below.

Sources:

* [Deploying Portainer CE in Docker](https://documentation.portainer.io/v2.0/deploy/ceinstalldocker/)
* [How to Install Portainer Docker UI Manager on Ubuntu 20.04 | 18.04 | 16.04](https://docs.fuga.cloud/how-to-install-portainer-docker-ui-manager-on-ubuntu-20.04-18.04-16.04)
* [How to Install Portainer 2.0 on your Docker](https://www.letscloud.io/community/how-to-install-portainer)

* [How to Get Started With Portainer, a Web UI for Docker](https://www.cloudsavvyit.com/8911/how-to-get-started-with-portainer-a-web-ui-for-docker/)
* [Portainer Install Ubuntu tutorial - manage your docker containers](https://www.youtube.com/watch?v=ljDI5jykjE8)

* [How to Update Portainer](https://www.wundertech.net/how-to-update-portainer/)

### Step 1: Portainer Server Deployment - DONE
Use the following Docker commands to deploy the Portainer Server.

```bash
# create the volume for storing persistent data
sudo docker volume create portainer_data

# install the portainer container (ports 8000 is for agents and 9000 for web ui)
sudo docker run -d -p 8000:8000 -p 9000:9000 -p 9443:9443 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest

# check if portainer is running
sudo docker ps -a -s
```

Now using your browser, log into portainer via this URL: `localhost:9000`.

### Step 2: Manage Multiple Hosts in Portainer
* [How to manage multiple Hosts in Portainer?](https://www.youtube.com/watch?v=kKDoPohpiNk&list=RDCMUCZNhwA1B5YqiY1nLzmM0ZRg&index=4)
### Step 2: Portainer Agent Deployment
Use the following Docker commands to deploy the Portainer Agent.
Agents are installed on Docker nodes being managed remotely by Portainer.
The agent is not needed on standalone hosts,
however it does provide additional functionality if used:

```bash
# install the portainer container
sudo docker run -d -p 9001:9001 --name portainer_agent --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /var/lib/docker/volumes:/var/lib/docker/volumes portainer/agent:latest
```

# Install Some Containers
* [How to Install Nextcloud on Ubuntu, Move Data Directory, Setup Free DDNS Domain & SSL Certificate](https://www.youtube.com/watch?v=g1mYxrxdJXM&t=0s)
* [How to Install Nextcloud Hub 21 on Ubuntu 20.04 - Apache, MySQL, and PHP Configuration](https://www.youtube.com/watch?v=ZM1fL6ze4X8)
* [Fix Nextcloud Cron Job not Running on NC 21.0.3 - Nextcloud Redis Setup](https://www.youtube.com/watch?v=8JVhRtArovg)
* [How to Install Bitwarden on Ubuntu 20.04 - Self Hosting a Password Manager](https://www.youtube.com/watch?v=7bFuJCxWH6I)

### Step X: Upgrading Portainer
To [upgrade to the latest version of Portainer Server][64],
you must do it from the commandline.
Use the following commands to stop Portainer, then remove the old version,
and finally do a new install of Portainer.

```bash
# before stopping portainer, record the ip addresses of portainer-agents associated
# with this portainer instance so you can restore the connections later

# stop and remove the portainer container
sudo docker stop portainer
sudo docker rm portainer

# pull down the latest version of portainer
sudo docker pull portainer/portainer-ce:latest

# reinstall portainer
sudo docker run -d -p 8000:8000 -p 9000:9000 -p 9443:9443 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest

# check if portainer is running
sudo docker ps -a -s
```

You may want to also upgrade the Portainer Agent and this must be done separately:

```bash
# stop and remove the portainer agent container
sudo docker stop portainer-agent
sudo docker rm portainer-agent

# pull and start the updated version of the image
sudo docker pull portainer/agent:latest
sudo docker run -d -p 9001:9001 --name portainer-agent --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /var/lib/docker/volumes:/var/lib/docker/volumes portainer/agent:latest

# check if portainer is running
sudo docker ps -a -s
```

```yaml
# docker compose file for portainer agent

version: '3.8'

services:
  portainer-agent:
    image: portainer/agent:latest
    container_name: portainer-agent
    restart: unless-stopped
    ports:
      - '9001:9001'
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - /var/lib/docker/volumes:/var/lib/docker/volumes
```

>**NOTE:** Check out the video
>"[Pi-Hosted : Upgrading Portainer and Updating Containers Part 6][59]"
>for a script to do the above steps.

### Step X: Update Your Docker Container
You can update you Docker containers via the commandline,
but Portainer provides a intuitive browser UI to do the same.
Check out the videos below

* [Use Portainer to update your Docker Containers while they are running. No command line needed.](https://www.youtube.com/watch?v=Eme2TlR7Z7E)
* [How To Update Docker Container automatically with nearly zero downtime](https://www.youtube.com/watch?v=5lP_pdjcVMo)



--------




## Thoughts on Better Docker Volume Management
Volumes are a mechanism for storing data outside containers. All volumes are managed by Docker and stored in a dedicated directory on your host, usually /var/lib/docker/volumes for Linux systems.

I have been wondering if there is any kind of best practice for structuring the volumes for the containers
(more specifically, the config and data volumes).
At the moment I am using the home directory,
and just have a folder for each container, with each service's volumes.
For each docker stack or individual service, I'll also have a subdirectory and store there all volume data.
This allows for easy backups and is very organized.

I want to structured mine so that I'd be able to back up all containers easily
and also switch around containers in various compose stacks without having to change volume locations.
Something like this:

```
/opt/docker
  /stack1
    docker-compose.yml
  /stack2
    docker-compose.yml
  /volumes
    /container1
    /container2
```

But it might make more sense to include these volumes in something like this `/home/user/data/docker/volumes`.

* [Top Tips and Use Cases for Managing Your Volumes](https://www.docker.com/blog/top-tips-and-use-cases-for-managing-your-volumes/)
* [How to move Docker's data directory from /var/lib](https://www.dzombak.com/blog/2024/01/How-to-move-Docker-s-data-directory-from-var-lib.html)



## Install Watchtower
With [Watchtower][65] you can automate the updating of your running containerized apps.
Watchtower will pull down your new image,
gracefully shut down your existing container,
and restart it with the same options that were used when it was deployed initially.
These updates can be scheduled or done on demand.

Sources:
* [Watchtower Documentation][65]
* [How To Update Docker Container automatically with nearly zero downtime](https://www.youtube.com/watch?v=5lP_pdjcVMo)
    * [How To Update Docker Container automatically with nearly zero downtime](https://github.com/christianlempa/videos/tree/main/watchtower-tutorial)
* [Watchtower: The Docker Container That Automatically Updates Your Images](https://www.youtube.com/watch?v=DNfMuDLDq7k)
* [How to Update Docker Containers using Watchtower with Portainer](https://www.youtube.com/watch?v=mS0ylPhwQDU)

#### Step X: xxx
#### Step X: xxx
#### Step X: xxx

## Install HashiCorp Vault
Secure, store, and tightly control access to tokens, passwords, certificates, and encryption keys for protecting secrets and other sensitive data using a UI, CLI, or HTTP API.

Sources:
* [The 4 Primary Vault Use Cases](https://www.youtube.com/watch?v=XcDCQSkyhbA)
* [Introduction to HashiCorp Vault with Armon Dadgar](https://www.youtube.com/watch?v=VYfl-DpZ5wM&t=8s)
* [HashiCorp Vault](https://www.vaultproject.io/)
* [Integrate with Docker](https://developer.hashicorp.com/hcp/docs/vault-secrets/integrations/docker)

#### Step X: xxx
#### Step X: xxx
#### Step X: xxx
#### Step X: xxx



----



# Using Docker and Ansable



----



# Using Vagrant and Ansible
Vagrant has integrations with Ansible as a provisioner for Vagrant's virtual machines (VM)s.
The Vagrant Ansible provisioner allows you to provision the Vagrant VM
[using Ansible playbooks][24] by executing [`ansible-playbook`][25] from the Vagrant host.

The first step once you’ve installed Vagrant is to create a Vagrantfile
and customize it to suit your needs.
This is covered in detail in the Vagrant documentation,
but here is a quick example that includes a section to use the Ansible provisioner to manage a single machine:

```bash
# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version
Vagrant.configure(2) do |config|

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "ubuntu/xenial64"

  # Disable the new default behavior introduced in Vagrant 1.7, to
  # ensure that all Vagrant machines will use the same SSH key pair.
  # See https://github.com/mitchellh/vagrant/issues/5005
  config.ssh.insert_key = false

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "playbook.yml"
  end

end
```

Notice the `config.vm.provision` section that refers to an Ansible playbook
called `playbook.yml` in the same directory as the Vagrantfile.
Vagrant runs the provisioner once the virtual machine has booted and is ready for SSH access.

```bash
# start the virtual machine and run the provisioning playbook
vagrant up

# re-run a playbook on an existing virtual machine
vagrant provision
```

Sometimes you may want to run Ansible manually against the machines.  - https://docs.ansible.com/ansible/latest/scenario_guides/guide_vagrant.html#running-ansible-manually


* [Ansible tutorial part 1: Inventory files , vagrant and remote hosts](https://medium.com/@perwagnernielsen/ansible-tutorial-part-1-inventory-files-vagrant-and-remote-hosts-33a15b0185c0)
* [Ansible tutorial part 2: Installing packages](https://medium.com/@perwagnernielsen/ansible-tutorial-part-2-installing-packages-41d3ab28337d)

* [Ansible Vagrant beginners guide](https://www.inpimation.com/ansible-vagrant-beginners-guide/)
* [Ansible round 2, the awesome stuff](https://www.inpimation.com/ansible-round-2-awesome-stuff/)

* [19 Minutes With Ansible](https://sysadmincasts.com/episodes/43-19-minutes-with-ansible-part-1-4)
* [Using Ansible to Provision Vagrant Boxes](https://fedoramagazine.org/using-ansible-provision-vagrant-boxes/)
* [Using Vagrant and Ansible](https://docs.ansible.com/ansible/2.5/scenario_guides/guide_vagrant.html)
* [Developing in a VM with Vagrant and Ansible](https://blog.jetbrains.com/pycharm/2017/12/developing-in-a-vm-with-vagrant-and-ansible/)

## Using ansible-playbook
https://docs.ansible.com/ansible/latest/cli/ansible-playbook.html

## Ansible Playbook Structure
* [How to Manage Multistage Environments with Ansible](https://www.digitalocean.com/community/tutorials/how-to-manage-multistage-environments-with-ansible)
* [Creating a User in Ansible](https://serversforhackers.com/c/create-user-in-ansible)
* [Ansible Playbook Structure](http://www.oznetnerd.com/ansible-playbook-structure/)
* [The Anatomy of an Ansible Playbook](http://www.oznetnerd.com/anatomy-ansible-playbook/)

While Ansible is a powerful configuration management system,
you can get lost in a sea of options when it comes time to structure your Ansible Playbooks.
Ansible provides easy-to-read syntax, flexible workflows, and powerful tooling,
it can be challenging to structure your Playbooks when managing large numbers of hosts
that can vary by deployment environment and functionality.
For example, you can list your hosts and group variables in the `/etc/ansible/hosts` file,
or you can create your own inventory, hosts, and group files in your directory layout.
And there is a ridicules number of [different places your variables][30].

So which directory  structure method do you choose?
Ansible does provide a [Best Practices][32] page.
The approach demonstrated here relies on Ansible group variables and multiple inventories
and follows the ideas posted here:

* [How to Manage Multistage Environments with Ansible](https://www.digitalocean.com/community/tutorials/how-to-manage-multistage-environments-with-ansible)



To create a new project using this structure, you can do the following:

```bash
# create a new Ansible project
mkdir -p new_project
cd new_project

# create inventory and master playbook
touch production staging site.yml README.md

# folders
mkdir -p group_vars host_vars library filter_plugins

# create a role with all the folders (role is named common)
mkdir -p roles/common/{tasks,handlers,templates,files,vars,defaults,meta}
touch roles/common/{tasks,handlers,templates,files,vars,defaults,meta}/main.yml
```

Also see
* [How to design an Ansible directory structure](https://groups.google.com/forum/#!topic/ansible-project/OEYxzuNCwDE)
* [create-ansible-playbook-template.sh](https://gist.github.com/skamithi/11200462)
* [ansible-roles-oneliner](https://gist.github.com/mralexjuarez/c4cfae2f6f4f23af1d1b)

### Creating a User Playbook
You can't put a plaintext password into Ansible.
Instead you need to generate one!
The easiest way to do this is with the `mkpasswd` command.
This will prompt you for the plaintext password
and will give you a hashed password string you can paste into the task definition.
For password "password":

```bash
# generate for "password"
$ mkpasswd --method=sha-512
Password:
$6$j1kvmD5WQGrt8gv$/6ly6UjG0gGXfs0QtIPYWVcz31cUR1dRqFGZenlenuayf4KJF.Tgk4ZziygEZF1x1oKUPT6I38qCAau7bmBC40
```


```yaml
 - name: Create a login user
     user:
      name: jeff
      password: '$6$j1kvmD5WQGrt8gv$/6ly6UjG0gGXfs0QtIPYWVcz31cUR1dRqFGZenlenuayf4KJF.Tgk4ZziygEZF1x1oKUPT6I38qCAau7bmBC40'
      groups:                # Empty by default
       - docker
       - sudo
      state: present
      shell: /bin/bash       # Defaults to /bin/bash
      system: no             # Defaults to no
      createhome: yes        # Defaults to yes
      home: /home/jeff       # Defaults to /home/<username>
```

Check the [Ansible documentation][28] for more information,
such as creating an SSH key on the fly.

### Install Nginx
* [Deploying NGINX with Ansible](https://blog.serverdensity.com/deploying-nginx-with-ansible/)

We'll use the "apt" module to install Nginx across each server.
This let's us declaratively tell Ansible what we want the desired state to be.

```bash
# install nginx on all servers
ansible all -m apt -a "pkg=nginx state=latest update_cache=true" -u root --private-key=~/.ssh/id_ansible
```

This will install Nginx on each server!

* [How To Develop a Node.js TCP Server Application using PM2 and Nginx on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-develop-a-node-js-tcp-server-application-using-pm2-and-nginx-on-ubuntu-16-04)
* [DigitalOcean Tutorals](https://www.digitalocean.com/community/tutorials)

# Ansible Snippets
https://html5hive.org/ansible-quickies-useful-code-snippets/

# Ansible Callback Plugin
Callback plugins enable adding new behaviors to Ansible when responding to events.
Using the YAML callback plugin,
you can reformat Ansibles error message output to make it more readable.
To use it, edit your `ansible.cfg`and add the following lines under the `[defaults]` section:

```yaml
# use the YAML callback plugin, for documenation: `ansible-doc -t callback yaml`
stdout_callback = yaml

# use the stdout_callback when running ad-hoc commands
bin_ansible_callbacks = True
```

* [Use Ansible's YAML callback plugin for a better CLI experience](https://www.jeffgeerling.com/blog/2018/use-ansibles-yaml-callback-plugin-better-cli-experience)
* [Formatting stdout in a debug task of Ansible](https://stackoverflow.com/questions/50009505/formatting-stdout-in-a-debug-task-of-ansible)

# Testing Ansible Roles
* [Testing Ansible Roles with Travis CI on GitHub](https://www.jeffgeerling.com/blog/testing-ansible-roles-travis-ci-github)



[01]:https://www.vagrantup.com/
[02]:https://www.vagrantup.com/downloads.html
[03]:https://www.virtualbox.org/wiki/Downloads
[04]:https://github.com/cogitatio/vagrant-hostsupdater
[05]:https://www.vagrantup.com/docs/
[06]:https://en.wikipedia.org/wiki/Virtual_machine
[07]:https://www.virtualbox.org/wiki/Virtualization
[08]:https://en.wikipedia.org/wiki/Hardware-assisted_virtualization
[09]:https://www.virtualbox.org/
[10]:https://www.vagrantup.com/docs/vagrantfile/
[11]:http://www.vagrantbox.es/
[12]:https://www.vagrantup.com/docs/boxes.html
[13]:https://app.vagrantup.com/boxes/search
[14]:https://www.vagrantup.com/docs/cli/
[15]:https://www.youtube.com/watch?v=edoDx8bzU4M
[16]:https://stackoverflow.com/questions/1077412/what-is-an-idempotent-operation
[17]:https://www.chef.io/
[18]:https://puppet.com/
[19]:https://saltstack.com/
[20]:https://medium.com/@cabot_solutions/ansible-and-docker-the-best-combination-for-an-efficient-software-product-management-28c86cfebe90
[21]:https://en.wikipedia.org/wiki/INI_file
[22]:https://docs.ansible.com/ansible/latest/user_guide/intro_dynamic_inventory.html
[23]:https://docs.ansible.com/ansible/latest/modules/list_of_all_modules.html
[24]:https://docs.ansible.com/ansible/latest/scenario_guides/guide_vagrant.html
[25]:https://docs.ansible.com/ansible/latest/cli/ansible-playbook.html
[26]:https://en.wikipedia.org/wiki/Serialization
[27]:https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html#yaml-syntax
[28]:https://docs.ansible.com/ansible/latest/modules/user_module.html
[29]:https://galaxy.ansible.com/search
[30]:https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html#variable-precedence-where-should-i-put-a-variable
[31]:https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html
[32]:https://docs.ansible.com/ansible/latest/user_guide/playbooks_best_practices.html#directory-layout
[33]:https://galaxy.ansible.com/home
[34]:https://docs.ansible.com/ansible/latest/reference_appendices/galaxy.html#the-command-line-tool
[35]:https://www.terraform.io/
[36]:https://www.oreilly.com/learning/why-use-terraform
[37]:https://serversforhackers.com/c/ansible-installation-and-basics
[38]:https://www.nginx.com/
[39]:https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-1804
[40]:https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html
[41]:https://cfengine.com/
[42]:https://www.ansible.com/use-cases/configuration-management
[43]:https://en.wikipedia.org/wiki/Infrastructure_as_code
[44]:https://www.hashicorp.com/
[45]:https://www.packer.io/
[46]:https://www.packer.io/intro/why.html
[47]:https://www.ansible.com/use-cases/configuration-management
[48]:https://www.packer.io/downloads.html
[49]:https://www.packer.io/docs/builders/index.html
[50]:https://www.packer.io/docs/builders/virtualbox.html
[51]:https://www.packer.io/docs/builders/virtualbox-ovf.html
[52]:https://stackoverflow.com/questions/16704059/easiest-way-to-copy-a-single-file-from-host-to-vagrant-guest
[53]:https://docs.oracle.com/cd/E97728_01/E97727/html/vboxmanage-intro.html
[54]:https://github.com/hashicorp/vagrant/tree/master/plugins
[55]:https://geek-university.com/oracle-virtualbox/virtualbox-guest-additions/
[56]:https://subscription.packtpub.com/book/virtualization_and_cloud/9781786464910/1/ch01lvl1sec12/enabling-virtualbox-guest-additions-in-vagrant
[57]:https://discoposse.com/2016/05/23/autoupdating-virtualbox-guest-additions-with-vagrant-vbguest/
[58]:https://docs.docker.com/engine/install/
[59]:https://www.youtube.com/watch?v=q3wKqk8qVS8&list=PL846hFPMqg3jwkxcScD1xw2bKXrJVvarc&index=8
[60]:https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository
[61]:https://www.portainer.io/
[62]:https://docs.docker.com/compose/
[63]:https://github.com/docker/compose/releases
[64]:https://docs.portainer.io/v/ce-2.9/admin/upgrade/docker
[65]:https://containrrr.dev/watchtower/
[66]:
[67]:
[68]:
[69]:
[70]:
