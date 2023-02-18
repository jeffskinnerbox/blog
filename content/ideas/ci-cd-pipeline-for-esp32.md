!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="http://www.foxbyrd.com/wp-content/uploads/2018/02/file-4.jpg" title="These materials require additional work and are not ready for general use." align="center">
</div>


-----


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
[Concourse][01] is an open source automation system written in Go.
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



[01]:https://concourse-ci.org/
[02]:
[03]:
[04]:
[05]:
[06]:
[07]:
[08]:
[09]:
[10]:
