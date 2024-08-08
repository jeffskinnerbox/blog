<!--
Maintainer: jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version: 0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>

---

- [Wanna build a Raspberry Pi 5 cluster?](https://www.raspberrypi.com/news/wanna-build-a-raspberry-pi-5-cluster/)


## What is a Cluster

Computer clusters are an architectural component of [High Performance Computing (HPC)][05],
but not exclusively.
Years ago, machines used for high performance computing were known as "supercomputers".
They were big standalone machines with specialized hardware
and worked very different from what you would find in home and office computers you see today.
Nowadays, however, the majority of supercomputers are instead computer clusters (or just "clusters" for short).
Cluster computers are collections of relatively low-cost standalone computers that are networked together.
These inter-connected computers are endowed with software to coordinate programs on (or across) those computers,
and they can therefore work together to perform computationally intensive tasks.

Each computer in the cluster is called a node,
and we commonly talk about two types of nodes: head node and compute nodes.

- **Node -** This is the name usually used for one unit (usually one computer) in a computer cluster.
  Generally, this computer will have one or two CPUs, each normally with more than one core.
  The memory is always shared between cores on the same CPU, but generally not between the CPUs.
  This means programs using only multi-threaded, shared memory programming interfaces,
  like OpenMP, is not generally suited for clusters, unless there are many cores per CPU and much memory per CPU.
- **Head Node -** The head node is the computer where we land when we log in to the cluster.
  This is where we edit scripts, compile code, and submit jobs to the scheduler.
  The head nodes are shared with other users and jobs should not be run on the head nodes themselves.
- **Compute Node -** The compute nodes are the computers where jobs should be run.
  In order to run jobs on the compute nodes we must go through the job scheduler.
  By submitting jobs to the job scheduler,
  the jobs will automatically be run on the compute nodes once the requested resources are available.

Clusters computers are what you turn to when your standard computer resource can no longer handle the computations you need to get done.
Some concrete advantages of using clusters are:

- Lots of processing capacity, ability to do parallel computing (e.g., you could use many CPU-cores for a single job)
- Lots of memory (e.g. each nodes have modest GB of memory but can be "added-up" to create very large RAM space)
- Ability to work with large datasets
- Lots of software is available and already configured (e.g., MPI, compilers, commercial software)
- Keep your laptop free to use by running your work on the clusters

HPC has [many practical uses][09] and
refers to the practice of aggregating computing power in a way that delivers
much higher performance than one could get out of a typical desktop computer or workstation
in order to solve large problems in science, engineering, or business.
Computer clusters, and references to HPC, are also used in [cloud computing][04].

- [Clusters vs Supercomputers](https://www.networkcomputing.com/network-infrastructure/clusters-vs-supercomputers)
- [Beginner's Guide to clusters](https://www.hpc2n.umu.se/documentation/guides/beginner-guide)
- [What is High-performance computing (HPC)?](https://ubuntu.com/blog/what-is-high-performance-computing-hpc-part-1)
- [Introduction to Parallel Computing Tutorial](https://hpc.llnl.gov/documentation/tutorials/introduction-parallel-computing-tutorial)


## Clustered Operating System

Cluster operating systems are a combination of software and hardware clusters.
Hardware clusters aid in the sharing of high-performance disks among all computer systems,
while software clusters give a better environment for all systems to operate.
The cluster software is installed on each node in the clustered system,
and it monitors the cluster system and ensures that it is operating properly.
Cluster components are generally linked via fast area networks,
and each node executing its instance of an operating system.
In most cases, all nodes share the same hardware and operating system.

There are mainly three types of the clustered operating system:

- In **Asymmetric Clustering System**, one node out of all nodes is in hot standby mode,
  while the remaining nodes run the essential applications.
  Hot standby mode is completely fail-safe and also a component of the cluster system.
  The node monitors all server functions; the hot standby node swaps this position if it comes to a halt.
- In a **Symmetric Clustering System**, the multiple nodes help run all applications in this system,
  and it monitors all nodes simultaneously.
  ecause it uses all hardware resources, this cluster system is more reliable than asymmetric cluster systems.
- A **Parallel Cluster System** allows several users to access similar data on the same shared storage system.
  The system is made possible by a particular software version and other apps.


# Parallel Programming Language

- [Chapel: Making parallel computing as easy as Py(thon), from laptops to supercomputers](https://www.youtube.com/watch?app=desktop&v=7Qk8T7_bevo)

A [computer cluster][01] is a set of computers that work together so that they can be viewed as a single system.
The components of a cluster are usually connected to each other through fast local area networks.
Each computer used as a server (typically called a node) running its own instance of an operating system.
In most circumstances, all of the nodes use the same hardware and the same operating system.

So a computer cluster consists of a set of loosely (or tightly) connected computers
that work together so that, in many respects, they can be viewed as a single system.
This is unlike grid computers where the individual computers work on separate tasks
that are part of a large problem.
They are usually more different from one another and geographically further apart than cluster computers are.

A [Beowulf cluster][02] is a computer cluster
(typically identical, commodity-grade computers)
networked together and running some kind of parallel processing software
that allows each node in the cluster to share data and computation for a common task.
Typically, the parallel programming communications software is Message Passing Interface (MPI).
MPI utilizes TCP/IP, along with some libraries,
to allow programmers to create parallel programs that can split a task
into parts suitable to run on multiple machines simultaneously.
MPI provides an API that enables both asynchronous and synchronous process interaction.
For more information:

- [Beowulf Project Overview](https://beowulf.org/overview/faq.html)
- [Linux High Performance Computing Cluster -- Beowulf Cluster](https://www.programmersought.com/article/7646863911/).
- [Building a Beowulf Cluster in just 13 steps](https://www.linux.com/training-tutorials/building-beowulf-cluster-just-13-steps/)
- [Creating a Raspberry Pi-Based Beowulf Cluster](http://kau.diva-portal.org/smash/get/diva2:1110319/FULLTEXT02.pdf)
- [Creating a Raspberry Pi-Based Beowulf Cluster](http://coen.boisestate.edu/ece/files/2013/05/Creating.a.Raspberry.Pi-Based.Beowulf.Cluster_v2.pdf)

- [DIY mini supercomputer with several Raspberry Pi 4? Bad idea?](https://www.reddit.com/r/DataHoarder/comments/d1d7wy/diy_mini_supercomputer_with_several_raspberry_pi/)
- [Build a DIY Supercomputer: Part 2!](https://medium.com/@leerbardon/build-a-diy-supercomputer-part-2-8a40a484c0e2)
- [How to Build a Supercomputer](https://www.wikihow.com/Build-a-Supercomputer)
- [BYOC: Build Your Own Cluster](https://www.webmo.net/support/pdf/byoc.pdf)
- [How to build a Raspberry Pi cluster](https://www.raspberrypi.com/tutorials/cluster-raspberry-pi-tutorial/)
- [Build a Raspberry Pi cluster computer](https://magpi.raspberrypi.com/articles/build-a-raspberry-pi-cluster-computer)
- [Setting up a home cluster](https://www.blasbenito.com/post/01_home_cluster/)
- [Why build a Raspberry Pi Cluster?](https://www.jeffgeerling.com/blog/2021/why-build-raspberry-pi-cluster)

A [Apache Hadoop cluster][06] is a Java developed framework primarily used for
running applications on clusters of industry-standard commodity hardware.
Hadoop can be viewed as two segments:
data storage functions, [Hadoop Distributed File System (HDFS)][07],
and data processing function, [MapReduce][08].

Some studies (particle physics problems) show that Beowulf cluster with MPI can significantly out performed
Hadoop with HDFS in terms of processing speed and provides more consistent performance.
However, Hadoop shows better data management infrastructure
and dealing with node failure and data replication.


## Which Linux Distribution

Building a RPi cluster using Raspbian (based on Debian) has several advantages but its down side it its weight.
Raspbian supports many features and so there is a large amount of daemons running all the time.
As such, boot time is much longer than it has to be,
more memory / CPU is used,
and you have many packages installed you'll never need.

A better choose maybe [Arch Linux][03], which provides a minimalist instance.
The image is tiny at ~150MB and boots in around 10 seconds.
The install image has nothing extra included.
The default installation provides a bare bones, minimal environment,
that boots to a command line interface (CLI) with network support.
The downside is you have to be willing to learn the different (but elegant) approach to Linux.


## Raspberry Pi Cluster

I chose Raspbian Lite


# Proxmox on Raspberry Pi Hardware

In this section, the objective is to install Proxmox (a Type 1 Hypervisvor) on the Raspberry Pi hardware.
Within Proxmox, we'll create an Turnkey Core LXC container,
and nested in this will be Docker & Docker Compose so we can use Docker containers.
Then using Docker container, we can install Home Assistant, Node Red,
and may of the other utilities used for home automation.


## Install Proxmox on Raspberry Pi

Pimox is a port of Proxmox to the Raspberry Pi allowing you to run a
Type 1 Hypervisor on the Raspberry Pi hardward.
The required steps to install Proxmox on a Raspberry Pi are:

- Use a Raspberry Pi 4, with at least 4G of RAM, 8G is better ([method][AA] to check RAM)
- Install a 64-bit version of Raspberry Pi OS.
- Download the Pimox script and edit it.
- Run the Pimox installation script.

[AA]: https://www.canadarobotix.com/blogs/how-to/how-to-tell-which-raspberry-pi-4-ram-size-do-i-have

Once these steps are done,
a Proxmox web interface will be available to configure everything else.

Sources:

- [Installing Proxmox 7 on Raspberry Pi 4 with PiMox](https://raspberrypiprojects.com/installing-proxmox-7-on-raspberry-pi-4-with-pimox/)
- [Installing Proxmox 8.1 virtualization platform on a Raspberry Pi 5](https://www.geeky-gadgets.com/installing-proxmox-8-raspberry-pi-5/)
- [How to run PVE 7 on a Raspberry Pi](https://forum.proxmox.com/threads/how-to-run-pve-7-on-a-raspberry-pi.95658/)
- [RASPBERRY PI: INSTALLING PROXMOX VE 7 ON THE PI 4](https://pycvala.de/blog/raspberry-pi/raspberry-pi-installing-proxmox-ve-7-on-the-pi-4/)
- [Is the Raspberry Pi5 the better Proxmox Server?](https://www.youtube.com/watch?v=Qit-3upR6iA)


# Proxmox Cluster

- [More POWER for my HomeLab! // Proxmox Cluster](https://www.youtube.com/watch?v=IhEE_QlI1MU)
- [Install Proxmox 8 on Raspberry Pi OS](https://www.youtube.com/watch?v=VILBY-xZD8E)
- [Create VMs on Proxmox in Seconds!](https://www.youtube.com/watch?v=1nf3WOEFq1Y)
- [Proxmox virtual machine _automation_ in Terraform](https://www.youtube.com/watch?v=dvyeoDBUtsU)
- [Now running Proxmox on a Raspberry Pi 4 cluster](https://www.reddit.com/r/Proxmox/comments/n4d7ev/now_running_proxmox_on_a_raspberry_pi_4_cluster/)
- [Installing Proxmox 8.1 virtualization platform on a Raspberry Pi 5](https://www.geeky-gadgets.com/installing-proxmox-8-raspberry-pi-5/)
- [RASPBERRY PI: INSTALLING PROXMOX VE 7 ON THE PI 4](https://pycvala.de/blog/raspberry-pi/raspberry-pi-installing-proxmox-ve-7-on-the-pi-4/)
- [Virtual Machines on the Raspberry Pi!: VMWare ESXi on Raspberry Pi 4](https://medium.com/@arsalan.sahab/virtual-machines-on-the-raspberry-pi-3292ce60acdb)

- [Home Server PC build with Proxmox - cheap, quiet, powerful](https://www.youtube.com/watch?v=nwlircveTHU)
- [Now running Proxmox on a Raspberry Pi 4 cluster](https://www.reddit.com/r/Proxmox/comments/n4d7ev/now_running_proxmox_on_a_raspberry_pi_4_cluster/)
- [Install Proxmox 7 on Raspberry Pi 4](https://www.youtube.com/watch?v=bkub3_KbBVo)
- [Working VM on Raspberry Pi running Proxmox 7 (Pimox)](https://www.youtube.com/watch?v=ULboyaR_8EU)
- [Running LXD Container on Raspberry Pi 4 Proxmox 7](https://www.youtube.com/watch?v=7lkUu_OMKrY)
- [Installing Proxmox 8.1 virtualization platform on a Raspberry Pi 5](https://www.geeky-gadgets.com/installing-proxmox-8-raspberry-pi-5/)


# Project to Test the Cluster: Enigma Machine Brute Force Decryption

- [The Ultimate Hack: Using a Raspberry Pi 5 Cluster to Break the Enigma Code](https://www.youtube.com/watch?v=cIq2AEbYotA)
  - [py-enigma 0.1](https://pypi.org/project/py-enigma/)
  - [PyEnigma Documentation](https://py-enigma.readthedocs.io/en/latest/reference.html)
  - [OctaPi: brute-force Enigma](https://projects.raspberrypi.org/en/projects/octapi-brute-force-enigma/6)
  - [Breaking the Enigma Code in Python with MCMC (Marvel themed)](https://towardsdatascience.com/breaking-the-enigma-code-in-python-with-mcmc-marvel-themed-9ceb358dd8ae)
- [Parallel Examples](https://hpc.llnl.gov/documentation/tutorials/introduction-parallel-computing-tutorial##Examples)


# Raspberry Pi Docker Swarm Cluster

- [Docker Swarm](https://www.kevsrobots.com/blog/docker-swarm.html)
- [DOCKER SWARM ON RASPBERRY PI 5](https://www.kevsrobots.com/learn/docker_swarm/)
- [Creating a Supercomputer with a Raspberry Pi 5 Cluster and Docker Swarm!](https://www.youtube.com/watch?v=tDENgLiJSh0)

- [7 Raspberry Pi Cluster Projects You Should Try](https://www.makeuseof.com/raspberry-pi-cluster-projects-you-should-try/)

- [My Custom (Automated) LiM Kubernetes Cluster](https://rpi.loonix.ca/lim-cluster-set-up/)

- [Ansible 101](https://www.youtube.com/playlist?list=PL2_OBreMn7FplshFCWYlaN2uS8et9RjNG)
- [Kubernetes 101](https://www.youtube.com/playlist?list=PL2_OBreMn7FoYmfx27iSwocotjiikS5BD)
- [Kubernetes explained simply, and why you should learn it!](https://www.youtube.com/watch?v=glFE28QT1HI)

- [Build a Kubernetes cluster using K3s via Ansible](https://github.com/k3s-io/k3s-ansible/tree/master)


## Learning Hadoop

- [How to get started with Hadoop](http://bigdatastudio.com/tag/best-way-to-learn-hadoop)
- [How can I learn Hadoop?](http://bigdatastudio.com/hadoop)
- [Hadoop Tutorials: Real Life Use Cases in the Sandbox](http://hortonworks.com/blog/hadoop-tutorials-real-life-use-cases-in-the-sandbox)


## Using AWS

- [Build a Hadoop Cluster in AWS in Minutes](https://dzone.com/articles/automate-building-hadoop-cluster-in-aws?edition=244486&utm_source=DailyDigest&utm_medium=email&utm_campaign=dd2016-11-30)
- [How Do I Get Started with the AWS Free Usage Tier?](http://docs.aws.amazon.com/gettingstarted/latest/awsgsg-intro/gsg-aws-free-tier.html)
- [Installing aws-cli, the New AWS Command Line Tool](http://alestic.com/2013/08/awscli)


# Using Google Kubernetes

- [Ansible for Kubernetes Examples](https://github.com/geerlingguy/ansible-for-kubernetes)
- [Self-hosting Kubernetes on your Raspberry Pi](https://blog.alexellis.io/self-hosting-kubernetes-on-your-raspberry-pi/)
- [Cluster computing on the Raspberry Pi with Kubernetes](https://opensource.com/life/16/2/build-a-kubernetes-cloud-with-raspberry-pi)


## Using Raspberry Pi for Hadoop Cluster

- [Cluster Deck Packs Four Pis Into One Portable Package](https://hackaday.com/2020/10/22/cluster-deck-packs-four-pis-into-one-portable-package/)
- [Raspberry Pi Cluster Shows You The Ropes](https://hackaday.com/2020/04/24/raspberry-pi-cluster-shows-you-the-ropes/)
- [Five years of Raspberry Pi clusters](https://medium.com/@alexellisuk/five-years-of-raspberry-pi-clusters-77e56e547875)
- [Raspberry Pi Supercomputer Cluster](https://www.youtube.com/watch?v=VzcarXuVUvU)
- [Creating a Raspberry Pi-Based Beowulf Cluster](http://coen.boisestate.edu/ece/files/2013/05/Creating.a.Raspberry.Pi-Based.Beowulf.Cluster_v2.pdf)
- [Build a Raspberry Pi cluster computer](https://www.blogdot.tv/build-a-raspberry-pi-cluster-computer/)
- [Tiny Titan is a sub-$1,000 classroom supercomputer](http://tinytitan.github.io/)
- [GCHQ Builds A Raspberry Pi Cluster](http://www.i-programmer.info/news/91-hardware/8385-gchq-builds-a-raspberry-pi-cluster.html)
- [Raspberry Pi Zero Cluster Packs a Punch](https://hackaday.com/2016/01/25/raspberry-pi-zero-cluster-packs-a-punch/#more-187972)
- [Drupal 8 on a Cluster of Raspberry Pis](http://www.pidramble.com/)
- [Raspberry Pi Dramble](https://github.com/geerlingguy/raspberry-pi-dramble)
- [Raspberry Pi Cluster](http://likemagicappears.com/projects/raspberry-pi-cluster/)
- [Designing a High Performance Parallel Personal Cluster](http://hackaday.com/2016/05/09/designing-a-high-performance-parallel-personal-cluster/)

- [Everyone can have a Cray-1 supercomputer with this Raspberry Pi DIY guide](https://www.datacenterdynamics.com/en/news/everyone-can-have-a-cray-1-supercomputer-with-this-raspberry-pi-diy-guide/)


# What Version of RPi DO I Have?

- [Raspberry Pi OS "Bullseye" Launches, Brings Speed Boost to the Latest Raspberry Pi 4 Models](https://www.hackster.io/news/raspberry-pi-os-bullseye-launches-brings-speed-boost-to-the-latest-raspberry-pi-4-models-b86becec3ae6)
- [How to know which Raspberry do you have](https://oastic.com/posts/how-to-know-which-raspberry-do-you-have/)
  - [Which Pi Do I Have? Includes Pi 4](https://support.pishop.us/article/69-which-pi-do-i-have-includes-pi-4)
  - [Raspberry Pi 4 Model B - Board Revisions](https://core-electronics.com.au/tutorials/Versions-Raspberry-Pi.html)


## Using Raspberry Pi Zero for Hadoop Cluster

- [The Turing Pi Cluster](https://www.youtube.com/playlist?list=PL2_OBreMn7Frk57NLmLheAaSSpJLLL90G)
- [Cluster HAT v2.0](https://shop.pimoroni.com/products/cluster-hat)
- Raspberry Pi Zero Cluster "Supercomputer" [Part 1](https://youtu.be/HsIFWk_QHoc) and [Part 2](https://youtu.be/ddrTDCdlYDE)
- [EEVblog #934 - Raspberry Pi Supercomputer Cluster PART 1](https://www.youtube.com/watch?v=KI7YLXhovb8&feature=em-uploademail)


## ESP32 Cluster

- [Build Your Own Supercomputer With ESP32s](https://hackaday.com/2018/04/17/build-your-own-supercomputer-with-esp32s/)


## Spark

- [Spark Or Hadoop: Which Is The Best Big Data Framework?](https://www.linkedin.com/pulse/spark-hadoop-which-best-big-data-framework-chaaranpall-lambba?trk=eml-b2_content_ecosystem_digest-recommended_articles-103-null&midToken=AQFNblHgIt9-6A&fromEmail=fromEmail&ut=0pSjPikaB8JD81)


## Distributed Processing Tools

- [Jubatus is a distributed processing framework and streaming machine learning library](http://jubat.us/en/)


## Other Tools

- [FoundationDB - The best Key-Value Store in the world](https://foundationdb.com/)
- [FoundationDB: Using Python with a Distributed Key-Value Store](https://www.youtube.com/watch?v=G293P7UGnAY&feature=youtu.be)
- [Backup, Restore, Customize and Clone your Raspberry Pi SD Cards (tutorial)](http://sysmatt.blogspot.com/2014/08/backup-restore-customize-and-clone-your.html)
- [distributed server with RPi](https://hackaday.io/project/1002-distributed-server-with-rpi)


# Virtual Clusters (vcluster)

- [vcluster](https://www.vcluster.com/)


# Infrastructure as Code

In the not-so-distant past
(prior to the rise of DevOps),
if you wanted to build a software company,
you also had to manage a lot of hardware.
You would set up cabinets and racks, load them up with servers, hook up wiring,
install cooling, build redundant power systems, and so on.
The idea behind infrastructure as code (IAC)
is that you write and execute code to define, deploy, and update your infrastructure.
The article "[Why use Terraform?][36]" give a excellent description
and motivation for the multiple infrastructure tools.

The complexity of application stacks keeps going up


## HomeLab

Maybe you want to experiment with different technologies,
create development environments, or have your own private cloud.


# Background

After watching several videos about Home Labs, [Pi Cluster](https://www.youtube.com/watch?v=8zXG4ySy1m8)
Jeff Geerling

The CRAY-1 was rated at 160 MIPS and weighted 5.5 tons ran at 80MHz 115KW of power. The stock (no overclocking) Raspberry Pi C 2040 MIPS (Linpack) and weights 42 grams

- <https://www.tomshardware.com/reviews/raspberry-pi-4-overclock-2-ghz,6254.html>

Hands on learning about private clouds, clusters, Linux networking, Docker, Kubernetes, Helm, load balancer, OpenFaaS
parallel programming with python MPI

But what about virtual machines, virtual networking, ansible?

You can make a computer cluster with nearly anything that has a CPU and a network interface,
and it can handle a range of applications that lend easily to loosely-coupled parallel tasks.
For learning about parallel computing and the problems involved, the Raspberry Pi is vary suitable,
and you always have the RPi to re-used afterwards, if you choose to do so.
But for real world applications, the Raspberry Pi is a cheap, but not the best for MIPS/dollar.

Sources of inspiration:

- [5 reasons to run Kubernetes on your Raspberry Pi homelab](https://opensource.com/article/20/8/kubernetes-raspberry-pi)
- [Building a Raspberry Pi Kubernetes Cluster and running .NET Core - Alex Ellis & Scott Hanselman](https://www.youtube.com/watch?v=ZyTLMnzehyU&t=231s)
- [i built a Raspberry Pi SUPER COMPUTER!! // ft. Kubernetes (k3s cluster w/ Rancher)](https://www.youtube.com/watch?v=X9fSMGkjtug)

- [Why containers and Kubernetes have the potential to run almost anything](https://opensource.com/article/19/6/kubernetes-potential-run-anything)
- [Kubernetes basics: Learn how to drive first](https://opensource.com/article/19/6/kubernetes-basics)
- [Kubernetes is a dump truck: Here's why](https://opensource.com/article/19/6/kubernetes-dump-truck)
- [How to navigate the Kubernetes learning curve](https://opensource.com/article/19/6/kubernetes-learning-curve)
- [Build a Kubernetes cluster with the Raspberry Pi](https://opensource.com/article/20/6/kubernetes-raspberry-pi)
- [Manage your Kubernetes cluster with Lens](https://opensource.com/article/20/6/kubernetes-lens)


# Kubernetes


## Kubernetes and MPI

- [Kubernetes and MPI](https://stackoverflow.com/questions/38093438/kubernetes-and-mpi)
- [Scaling Kubernetes to 7,500 Nodes](https://openai.com/blog/scaling-kubernetes-to-7500-nodes/)
- See how to install MPI - [Building a Beowulf Cluster in just 13 steps](https://www.linux.com/training-tutorials/building-beowulf-cluster-just-13-steps/)


# MPI for Python

- [Installing MPI for Python on a Raspberry Pi Cluster](https://thenewstack.io/installing-mpi-python-raspberry-pi-cluster-runs-docker/)
- [Parallel programming in Python: mpi4py (part 1)](https://www.kth.se/blogs/pdc/2019/08/parallel-programming-in-python-mpi4py-part-1/)
- [MPI for Python: Tutorial](https://mpi4py.readthedocs.io/en/stable/tutorial.html)
- [Easy Parallel Computing with IPython](https://andrewmellor.co.uk/blog/articles/2015/04/30/easy-parallel/)


# K8S, K3S, Microk8s


# Setting Up the Cluster

- [Ansible 101 - on a Cluster of Raspberry Pi 2s](https://www.jeffgeerling.com/blog/ansible-101-cluster-raspberry-pi-2s)
- [A Raspberry Pi based ‘Bramble’ Cluster for Docker Swarm](https://glasstty.com/a-raspberry-pi-based-bramble-cluster-for-docker-swarm/)

  - [A Raspberry Pi based Cluster for use with ipyparallel and MPI](https://glasstty.com/a-raspberry-pi-based-cluster-for-use-with-ipyparallel-and-mpi/)

- [Building a Raspberry Pi cluster with MicroK8s](https://ubuntu.com/blog/building-a-raspberry-pi-cluster-with-microk8s)
- [How to build a Raspberry Pi Kubernetes cluster using MicroK8s](https://ubuntu.com/tutorials/how-to-kubernetes-cluster-on-raspberry-pi#1-overview)

- [K8s Cluster with Ansible](https://dzone.com/articles/ansible-boots-kubernetes)
- [Provisioning your Raspberry Pi-4 Cluster with Ansible](https://shantanoo-desai.github.io/posts/technology/edge_cluster_provisioning_ansible/)
- [Ansible - Raspberry Pi Kubernetes Cluster](https://everythingshouldbevirtual.com/automation/containers/ansible-raspberry-pi-kubernetes-cluster/)
- [Raspberry Pi Cluster Part 1: Provisioning with Ansible and temperature monitoring using Prometheus and Grafana](https://www.dinofizzotti.com/blog/2020-04-10-raspberry-pi-cluster-part-1-provisioning-with-ansible-and-temperature-monitoring-using-prometheus-and-grafana/)
- [Raspberry Pi Cluster Part 2: ToDo API running on Kubernetes with k3s](https://www.dinofizzotti.com/blog/2020-05-09-raspberry-pi-cluster-part-2-todo-api-running-on-kubernetes-with-k3s/)
- [Raspberry Pi Cluster Part 3: Running Load Tests with Kubernetes and Locust](https://www.dinofizzotti.com/blog/2020-07-04-raspberry-pi-cluster-part-3-running-load-tests-with-kubernetes-and-locust/)

- [Raspberry Pi 4 Personal Datacentre Part 1: Ansible, Docker and Nextcloud](https://www.rs-online.com/designspark/raspberry-pi-4-personal-datacentre-part-1-ansible-docker-and-nextcloud)
- [Raspberry Pi 4 Personal Datacentre Part 2: Home Assistant](https://www.rs-online.com/designspark/raspberry-pi-4-personal-datacentre-part-2-home-assistant)
- [Raspberry Pi 4 Personal Datacentre Part 3: A Self-hosted IoT Data Platform](https://www.rs-online.com/designspark/raspberry-pi-4-personal-datacentre-part-3-a-self-hosted-iot-data-platform)

- [Ansible Role: Docker for ARM](https://github.com/geerlingguy/ansible-role-docker_arm)

---


# My Cluster


## Cluster Hardware Configuration

Quantity Unit Cost Item
1 $40 [C4Labs Zebra Bramble Cluster Case](https://www.c4labs.com/product/bramble-case-raspberry-pi-3-b-color-and-stack-options/)
6 $75 [Raspberry Pi 4 Model B - 8GB DDR4](https://www.microcenter.com/product/622539/pi4modelB8gb?src=raspberrypi)
1 $25 [NETGEAR 8-Port Gigabit Ethernet Plus Switch (GS308E)](https://www.amazon.com/NETGEAR-8-Port-Gigabit-Ethernet-Managed/dp/B07PLFCQVK)
1 $20 [6-Port USB Charging Station 60W 12](https://www.amazon.com/gp/product/B098B6YY59)
6 $ 2 [6 inch Cat6 Ethernet Network Patch Cable RJ45](https://www.amazon.com/iMBAPrice-Ethernet-Network-Patch-Cable/dp/B00A1UPGY4/ref=sr_1_4)
6 $ 2 [6 inch USB-C to USB-A Charging Cable](https://www.amazon.com/Durable-Charging-Station-Compatible-Samsung/dp/B08PYJ1N9L/ref=sr_1_1_sspa)
Total $559


## Cluster Software Configuration


### Step 1: Physical Design


### Step X: Raspberry Pi OS Image


### Step X: Find the Devices

How you approach this will entirely depend on how your network is configured,
and what tools is available to you.
I would advise listening to the episode by operat0r called hpr3090 :: Locating Computers on a Enterprise Network for some great tips on how to do this.


### Step X: Turn Off Swap

From [How to build your own Raspberry Pi Kubernetes Cluster](https://www.youtube.com/watch?v=B2wAJ5FLOYw)

Check if swap is allocated via `free -m`

```bash
# turn off swap
dphys-swapfile swapoff

# uninstall swap so it can't be turned on
dphys-swapfile uninstall

# remove the package so it can be installed without a download
update-rc.d -f dphys-swapfile remove
```


### Step X: Install Docker

From [How to build your own Raspberry Pi Kubernetes Cluster](https://www.youtube.com/watch?v=B2wAJ5FLOYw)
at about 18 minutes

- [Setting up a Raspberry Pi Kubernetes Cluster with Ubuntu 20.04](https://www.youtube.com/watch?v=qv3_gLvjITk)
- [Build a Kubernetes cluster with the Raspberry Pi](https://opensource.com/article/20/6/kubernetes-raspberry-pi)


### Step X: Installing Kubernetes

From [How to build your own Raspberry Pi Kubernetes Cluster](https://www.youtube.com/watch?v=B2wAJ5FLOYw)
at about 21 minutes

- [Setting up a Raspberry Pi Kubernetes Cluster with Ubuntu 20.04](https://www.youtube.com/watch?v=qv3_gLvjITk)
- [Build a Kubernetes cluster with the Raspberry Pi](https://opensource.com/article/20/6/kubernetes-raspberry-pi)

- [i built a Raspberry Pi SUPER COMPUTER!! // ft. Kubernetes (k3s cluster w/ Rancher)](https://www.youtube.com/watch?v=X9fSMGkjtug)


### Step X: Install Lens

- [Manage your Kubernetes cluster with Lens](https://opensource.com/article/20/6/kubernetes-lens)
- [Speed up administration of Kubernetes clusters with k9s](https://opensource.com/article/20/5/kubernetes-administration)
- [Basic kubectl and Helm commands for beginners](https://opensource.com/article/20/2/kubectl-helm-commands)
- [The definitive pronunciation guide for kubectl](https://opensource.com/article/18/12/kubectl-definitive-pronunciation-guide)
- [Kubernetes namespaces for beginners](https://opensource.com/article/19/12/kubernetes-namespaces)


### Step X: Install Monitoring

Internet Monitoring: Installs Prometheus and Grafana, along with a few Docker containers to monitor your Internet connection with Speedtest.net speedtests and HTTP tests so you can see uptime, ping stats, and speedtest results over time.

- [Monitor your Internet with a Raspberry Pi](https://www.jeffgeerling.com/blog/2021/monitor-your-internet-raspberry-pi)
- [Setting up a Pi for remote Internet connection monitoring](https://www.jeffgeerling.com/blog/2021/setting-pi-remote-internet-connection-monitoring)


#### Munin

Munin is a set of tools that allows you to monitor computers, applications, and devices in a networked environment.
One of the advantages of Munin is its vast plugin eco-system. There are several hundred plugins available, which make it a powerful monitoring system. Munin itself uses RRDTool, which is written in Perl, whereas plugins could be written in any language.
Once data is collected from nodes, it is processed by the master and various graphs are made available on the dashboard. One of the components is – Munin-limits – which monitors the values between configured “ok”, “warn” and “crit” levels and can create a notification for the administrators.

- [Munin](https://munin-monitoring.org/)
  - [So, what is Munin?](https://subscription.packtpub.com/book/networking_and_servers/9781849696746/1/ch01lvl1sec03/so-what-is-munin)
  - [Live Demo](http://demo.munin-monitoring.org/)
- [Ansible Role: Munin](https://github.com/geerlingguy/ansible-role-munin)
- [Ansible Role: Munin Node](https://github.com/geerlingguy/ansible-role-munin-node)


#### Nagios

- [Nagios](https://www.nagios.org/downloads/)


# DMZ

- [Is the DMZ Dead? Not Quite](https://www.pcmag.com/news/is-the-dmz-dead-not-quite)
- [4 DMZ Best Practices to Shield You From Attackers](https://securityboulevard.com/2019/11/4-dmz-best-practices-to-shield-you-from-attackers-2/)


## Port Forwarding or DMZ

We need to have an incoming web server request, from the Internet,
hit port 80 or 433 on the home router and get sent (aka [port forwarded][85])
to the Vagrant VM contain the Nginx Proxy Manager which is then redirects it onto Bitwarden,
running on that same VM.

You might tempted to putting the proxy manger / Bitwarden combination on your home router's DMZ,
which seems easier moving through all these network ports, and may appear equivalent.
After all, isn't this what they do in corporate networks?

Not so fast, since a "DMZ host" isn't really a "[true DMZ][55]".
Specifically, some home routers refer to a DMZ host within there configuration options.
A home router DMZ host is a single IP address on the LAN network
that has all traffic sent to it which is not otherwise forwarded to other LAN hosts.
By definition, this is not a true DMZ, since the router alone does not separate
the host from your internal LAN network.

In the context of the "DMZ host" feature on home routers:

- Generally you should always port forward and be very specific about what you let through the gateway device.
  This means only a limited number of ports are exposed and all of them as in the DMZ case.
- The exception to this rule is when your ISP requires you to use a certain hardware device for the gateway,
  and you want to run your own NAT device behind it without having to double-NAT every service you run.
  In this case you would set your internal router as the DMZ host, then do all port forwarding on your device.

Sources:

- [Difference Between DMZ and Port Forwarding](http://www.differencebetween.net/technology/internet/difference-between-dmz-and-port-forwarding/)
- [The Ultimate Guide to Forwarding Ports in Your Router][85]
- [When And How To Setup DMZ Host For Home Use](https://routerguide.net/when-and-how-to-setup-dmz-host-for-home-use/)
- [Hosting my website from home](https://superuser.com/questions/902770/hosting-my-website-from-home)
- [Difference between Firewall and Proxy Server](https://www.geeksforgeeks.org/difference-between-firewall-and-proxy-server/)

[01]: https://en.wikipedia.org/wiki/Computer_cluster
[02]: https://en.wikipedia.org/wiki/Beowulf_cluster
[03]: https://www.prl.res.in/prl-eng/hpc/knowledge_base
[04]: https://www.youtube.com/watch?v=nIBu1EFYmBU
[05]: https://insidehpc.com/hpc-basic-training/what-is-hpc/
[06]: https://hadoop.apache.org/docs/r1.2.1/index.html
[07]: https://hadoop.apache.org/docs/r1.2.1/hdfs_design.html
[08]: https://hadoop.apache.org/docs/r1.2.1/mapred_tutorial.html
[09]: https://www.ibm.com/topics/hpc

[10]:

[55]: https://en.wikipedia.org/wiki/DMZ_(computing)
[85]: https://portforward.com/how-to-port-forward/
