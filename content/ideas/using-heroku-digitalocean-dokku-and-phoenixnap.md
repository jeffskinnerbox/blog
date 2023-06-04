<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----




Software as a service (or SaaS) is a way of delivering applications over the Internet—as a service. Instead of installing and maintaining software, you simply access it via the Internet, freeing yourself from complex software and hardware management.
SaaS is also known as "on-demand software" and Web-based/Web-hosted software.

Platform as a service (PaaS) or application platform as a service (aPaaS) or platform-based service is a category of cloud computing services that allows customers to provision, instantiate, run, and manage a modular bundle comprising a computing platform and one or more applications, without the complexity of building and maintaining the infrastructure typically associated with developing and launching the application(s); and to allow developers to create, develop, and package such software bundles.

Function as a service (FaaS) is a category of cloud computing services that provides a platform allowing customers to develop, run, and manage application functionalities without the complexity of building and maintaining the infrastructure typically associated with developing and launching an app.[1] Building an application following this model is one way of achieving a "serverless" architecture, and is typically used when building microservices applications.

Infrastructure as a service (IaaS) are online services that provide high-level APIs used to dereference various low-level details of underlying network infrastructure like physical computing resources, location, data partitioning, scaling, security, backup etc. A hypervisor, such as Xen, Oracle VirtualBox, Oracle VM, KVM, VMware ESX/ESXi, or Hyper-V runs the virtual machines as guests. Pools of hypervisors within the cloud operational system can support large numbers of virtual machines and the ability to scale services up and down according to customers' varying requirements.



----




# Why Heroku & DigitalOcean
Why Heroku or DigitalOcean? Maybe a better question is why not AWS or Azure or Google?
Heroku is a PaaS, letting you run apps on their platform the Heroku way.
Digital Ocean is an IaaS, which gives you raw servers to compose as you want to run your app.
The differences are mainly around pricing and control vs effort.
Heroku / DigitalOcean are container-base cloud platform
whereas AWS is a secure cloud services platform providing IaaS, PaaS and SaaS.

* [Azure vs. AWS: What is the Difference Between AWS and Azure](https://www.guru99.com/azure-vs-aws.html)
* [Google Cloud vs AWS: Difference Between AWS and GCP](https://www.guru99.com/google-cloud-vs-aws.html)
* [Heroku vs AWS: What is the Difference?](https://www.guru99.com/heroku-vs-aws.html)
* [DigitalOcean vs. AWS: Comparing Offers and Choosing the Better Option](https://soshace.com/digitalocean-vs-aws-comparing-offers-and-choosing-the-better-option/)
* [DigitalOcean vs Heroku | Which is better?](https://blog.back4app.com/digitalocean-vs-heroku/)
* [DigitalOcean vs Heroku: The Battle of ‘Cloud’ Guardians for Your Business](https://envzone.com/digitalocean-vs-heroku-the-battle-of-cloud-guardians-for-your-business/)



----



# Heroku
[Heroku positions itself as a Platform as a Service (PaaS)][01]
based on a managed container system, with integrated data services and a powerful ecosystem, for deploying and running modern apps. The Heroku developer experience is an app-centric approach for software delivery, integrated with today’s most popular developer tools and workflows.

* [Introduction to Heroku & Deep Dive](https://www.youtube.com/watch?v=lz-E7AGa37M)



----



# DigitalOcean
DigitalOcean doesn’t boast a huge market share, and instead,
the company focuses on smaller companies, startups, and individuals, allowing itself to fine-tune its product.
DigitalOcean calls its virtual private servers “droplets”
and you can manage these servers either utilize DigitalOcean’s web interface or a command-line interface.

With Dokku, you can push Heroku-compatible applications to it via Git.
They'll build using Heroku buildpacks and then run in isolated containers.
The end result is your own, single-host version of Heroku.

* [Full DigitalOcean Crash Course - Get started with cloud computing today](https://www.youtube.com/watch?v=9ZUHSW1tTiU)



----



# Dokku
Dokku can can assist the DigitalOcean IaaS platform with PaaS with "Heroku-like" features.
You can think of Dokku as a private Heroku that you manage.
Dokku refers to itself as a “Docker powered mini-Heroku.”

* [Dokku](https://dokku.com/)
* [DigitalOcean Droplet Installation Notes](https://dokku.com/docs/getting-started/install/digitalocean/)
* [Using Dokku On DigitalOcean](https://www.papertrail.com/blog/using-dokku-on-digitalocean/)



----



# phoenixNAP

A bare-metal server is a physical server dedicated to a single tenant/customer. Each server offered for rental is a distinct physical piece of hardware that is a functional server on its own.
Despite being often used interchangeably, the terms 'bare metal server' and 'dedicated server' refer to different types of servers. As such, it's worth asking yourself: "[bare-metal vs dedicated servers: which is the better hosting option?][02]" before making a decision.

phoenixNAP provides bare metal cloud computing infrastructure
with pricing as pay-as-you-go, monthly, and yearly reservation options.

* [Bare Metal Cloud - How to Deploy a Server Tutorial](https://www.youtube.com/watch?v=8TLsqgLDMN4&t=7s)
* [Building a 5-node Proxmox VE Cluster in 20 Minutes for a Dollar](https://www.servethehome.com/building-5-node-proxmox-ve-cluster-20-minutes-dollar-phoenixnap-intel-supermicro/)



[01]:https://www.heroku.com/platform
[02]:https://www.techradar.com/news/bare-metal-vs-dedicated-servers-which-is-the-better-hosting-option
[03]:
[04]:
[05]:
[06]:
[07]:
[08]:
[09]:
[10]:
