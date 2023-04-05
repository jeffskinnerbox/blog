!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----


# CI/CD for Website (aka my blog)
* [How to automatically deploy a Pelican blog with GitLab CI & Traefik](https://simonklug.de/ci-deploy-pelican)
* [How I do automated accessibility testing for my website](https://opensource.com/article/23/2/automated-accessibility-testing)
* [Example build pelican blogs with gitlab-ci](https://jugit.fz-juelich.de/docker-images/gitlabci-pelican)

A while ago, I broke my [Pelican][02] website via doing an update.
it was a routine Pelican update, but my website, like many others,
is full of add-on things that invite failure.
I shutdown the website, anticipating a quick fix, but now years have passed by.
It was just too painful to fix.
I explored other static website generators but the core problem is [dependency hell][01].
My website tools are using my global environment of my desktop Linux system.
Efforts to fix my website tools will compromise other things.
In addition, all the tools I'm using made the manual
build, validate, and deploy process complicated and error prone.

So I really need to remove the dependencies on my globally installed tools
and simplify/automate the build process.
I figured this would be a fun opportunity to play around with Docker and CI/CD.
Effectively, I wanted the Docker container to hold all the things that gave the website its personality,
and the CI/CD procedure to create/validate/deploy that website,
and I can focus exclusively on creating content using only Markdown as my authoring language.

I have used Docker containers widely but never built my own Docker container,
and this looks like just the right use case.
I don't want to compromise on my website's look & feel,
so just using someone else Docker container will not get me what I want.
I need to build my own container, but I can get some "hand holding"
from the many examples of Pelican Docker containers that others have built.
Sources of inspiration can be found below:

* [My Over-Engineered Blogging Setup](https://gdelgado.ca/my-over-engineered-blogging-setup.html#title)
* [Explorations with Pelican](https://jameslmart.in/pelican/)
* [Explorations with Pelican (part two)](https://jameslmart.in/pelican_part_two/)
* [gitlabci-pelican](https://jugit.fz-juelich.de/docker-images/gitlabci-pelican)
* [CircleCI for a Pelican static Github site](https://blog.john-pfeiffer.com/circleci-for-a-pelican-static-github-site/)
* [Running a Pelican Blog on Docker Cloud with Let's Encrypt](https://dtucker.co.uk/blog/docker-letsencrypt-pelican/)

Move to Hugo???

* [Migrating from Pelican to Hugo](https://dafyddcrosby.com/pelican-to-hugo/)
* [How I Migrate My Data Science Blog from Pelican to Hugo](https://wayofnumbers.com/p/how-i-migrate-my-data-science-blog-from-pelican-to-hugo/)
* [Moving from Pelican to Hugo for this blog](https://bulimov.me/post/2021/02/16/pelical-to-hugo/)
* [Migrating Blogs (Again) from Pelican to Hugo](https://arunrocks.com/moving-blogs-pelican-to-hugo/)
* [no migration tools for Pelican on Hugo website ... what does that tell you](https://gohugo.io/tools/migrations/)

## Rundeck
Rundeck is an open source software used to quickly automate manual tasks.
Use it to create workflows consisting of commands, scripts, and APIs.
These workflows might include software management, configurations, and scheduled events.
Rundeck logs these activities for transparency and troubleshooting.

* [Delegate common tasks with an open source automation tool](https://opensource.com/article/23/2/automate-common-tasks-rundeck)
* [Rundeck](https://www.rundeck.com/)
* [Rundeck: Running Docker Images](https://docs.rundeck.com/docs/administration/install/docker.html)



[01]:https://www.techtarget.com/searchitoperations/definition/dependency-hell
[02]:https://docs.getpelican.com/en/latest/#
[03]:
[04]:
[05]:
[06]:
[07]:
[08]:
[09]:
[10]:





-----






# CI/CD for Hardware (aka ESP8266 & ESP32)
* [Hardware-in-the-Loop and Continuous Integration - how do they fit together?](https://www.elektormagazine.com/news/hardware-in-the-loop-and-continuous-integration-how-do-they-fit-together)

# Earthly
Earthly is a CI/CD framework that allows you to develop pipelines locally and run them anywhere. Earthly leverages containers for the execution of pipelines. This makes them self-contained, repeatable, portable, and parallel.

* [Earthly](https://earthly.dev/)
* [Beyond Docker with Earthly](https://semaphoreci.com/blog/beyond-docker-with-earthly)
* []()
* []()

# Codefresh
https://codefresh.io/pricing/

# FlowForge
* [FlowForge](https://flowforge.com/)

# CircleCI
* [CircleCI](https://circleci.com/)

# GitOps
* [Source Code Management for GitOps and CI/CD](https://dzone.com/articles/source-code-management-for-gitops-and-cicd)
* [The Path to GitOps](/home/jeff/src/linux-tools/ci-cd/Path-to-GitOps-Red-Hat-Developer-e-book.pdf)






* [CI / CD pipeline for ESP32](https://rbklabs.in/ci-cd-pipeline-for-esp32/index.html)
* [Continuous Integration for ESP32](https://electric-toast.com/continuous-integration-for-esp32/)
* [An Automated CI/CD Pipeline to Build and Release your ESP32 Firmware with GitHub Actions](https://www.smartlab.at/an-automated-ci-cd-pipeline-to-build-and-release-your-esp32-firmware-with-github-actions/)
* [GitLab CI for ESP32 and Arduino](https://codeblog.dotsandbrackets.com/gitlab-ci-esp32-arduino/)
* See the "tags" at [Electric Toast](https://electric-toast.com/) website for more CI/CD ideas for ESP32 devices

* [IDF Docker Image](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-guides/tools/idf-docker-image.html)
* [Building ESP32 firmware with Espressif's IDF Docker image](https://koen.vervloesem.eu/blog/building-esp32-firmware-with-espressifs-idf-docker-image/)
* [ESP32 – Developing With ESP-IDF](https://www.studiopieters.nl/idf/)
* [Dockerized Arduino IDE for ESP32](https://github.com/vedantroy/arduino-docker-esp32)

# What is CI/CD?
Writing code is one thing.
Testing and deploying that code into production is another.
Continuous integration, delivery, and deployment are strategies designed to help increase the velocity of development and the release of well-tested, usable products. Continuous integration encourages development teams to test and integrate their changes to a shared codebase early to minimize integration conflicts. Continuous delivery builds off of this foundation by removing barriers on the way to deployment or release. Continuous deployment goes one step further by deploying every build that passes the test suite automatically.

Many tools exist to automate the workflow, from code commit to production release.

**CI or Continuous Integration** is a set of steps for the developer to follow to maintain the standard of the codebase. This is the barebone structure of the process -

* Check in code in frequently.
* Automate the build and test portion.
* Always test the code locally before checking it in.
* Never merge any failed branches to the main branch.
* Return its status back to successful if you’re the developer who causes the failed build or test.
* Make it your top priority to do so once the fail happens.

**CD or Continuous Delivery/Deployment** is more of continuation to CI. Generally the will be lot of work involved in order to deploy new application. Stop running processes, swap binaries, restart services in the required order and this is time consuming. The same applies even if its a on premise application, might be little simple, but still present. Create the right package - only the changes or the complete binaries, deploy on the CDS, notify user/application and handle the load.

So it is suitable to automate this CI/CD process and in most of the time it remains constant through out the lifecycle of the application. CD can usually have different kinds of triggers, run a CD on commit, run a CD at specific time interval or have a manual trigger.

# Setup My Own Pipeline

## Concourse CI/CD
[Concourse](https://concourse-ci.org/) is an open source automation system written in Go.
It is most commonly used for CI/CD, and is built to scale to any kind of automation pipeline,
from simple to complex.
Concourse is very opinionated about a few things:
idempotency, immutability, declarative config, stateless workers, and reproducible builds.

* [Concourse CI](https://www.youtube.com/watch?v=C9erh0ZnyOY)
* [Concourse CI: Documentation](https://concourse-ci.org/docs.html)
* [Concourse CI: Examples](https://concourse-ci.org/examples.html)
* [Concourse CI: Tutorials](https://concoursetutorial.com/)

## Install Concourse CI/CD
* https://concoursetutorial.com/
* [Quick Start: Docker Compose Concourse](https://concourse-ci.org/quick-start.html)
* [How to Install Concourse CI](https://vegastack.com/tutorials/how-to-install-concourse-ci/)
* [Getting Started with Concourse CI](https://tanzu.vmware.com/developer/guides/concourse-gs/)
* [Setting Up and Using Concourse CI on Ubuntu 16.04](https://www.digitalocean.com/community/tutorial_series/setting-up-and-using-concourse-ci-on-ubuntu-16-04)



