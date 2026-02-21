<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
    title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>

---------------

Projects to Follow
[ROS Robotics](https://robots.ros.org/)
* Robot Vision Pipeline
  * [Document - Robot Vision: ROSifying a YOLO Pipeline](https://soulhackerslabs.com/robot-vision-rosifying-a-yolo-pipeline-898fcefa9061)
  * [Videos - Robot Vision: ROSifying a YOLO Pipeline](https://www.youtube.com/playlist?list=PLhevfbQANJR1mqTFFRAtj70Q31pA2cwnk)
  * [GitHub - Robot Vision: ROSifying a YOLO Pipeline](https://github.com/carlos-argueta/rse-yolo-perception-pipeline)
* TurtleBot3
  * [Correctly Install TurtleBot3 Robot in ROS and Simulate Movement in Gazebo 3D Worlds - ROS Tutorial](https://www.youtube.com/watch?v=_RBZ-9_rz9Y)
  * [Rototis TurtleBot3](https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/)
  * [GitHub: ROBOTIS-GIT/turtlebot3](https://github.com/ROBOTIS-GIT/turtlebot3)
* LGDXRobot2
  * [LGDXRobot2](https://robots.ros.org/lgdxrobot2/)

ROS 2 Docker Images
* [Open Source Robotics Foundation ROS2 Docker Images - osrf/ros](https://hub.docker.com/r/osrf/ros/)
* [S1S2 Robotics Academy]()

MyDevContainer
* [GetHub: ros-tooling/setup-ros-docker](https://github.com/ros-tooling/setup-ros-docker)
* [Docker for Robotics](https://articulatedrobotics.xyz/category/docker-for-robotics)
* [ROS Development Inside Docker](https://ruhyadi.medium.com/ros-development-inside-docker-7c2e411badf6)
* [The Complete Beginner’s Guide to Using Docker for ROS 2 Deployment (2025 Edition)](https://blog.robotair.io/the-complete-beginners-guide-to-using-docker-for-ros-2-deployment-2025-edition-0f259ca8b378)
* [The Complete Guide to Docker for ROS 2 Jazzy Projects](https://automaticaddison.com/the-complete-guide-to-docker-for-ros-2-jazzy-projects/)
* [An Updated Guide to Docker and ROS 2](https://roboticseabass.com/2023/07/09/updated-guide-docker-and-ros2/)
* [ROS 2 with Docker - Part 1](https://divyanshu-raj.medium.com/ros-2-with-docker-part-1-9060f3095811)
* [The Complete Beginner’s Guide to Using Docker for ROS 2 Deployment (2025 Edition)](https://blog.robotair.io/the-complete-beginners-guide-to-using-docker-for-ros-2-deployment-2025-edition-0f259ca8b378)
* [ROS2 in Docker From Scratch! - Learn to Write, Install, and Run ROS2 Packages in Docker From Scratch](https://www.youtube.com/watch?v=oix-Qs75O08)
* [An Updated Guide to Docker and ROS 2](https://roboticseabass.com/2023/07/09/updated-guide-docker-and-ros2/)
* [Running ROS Noetic in Docker: A Practical Guide for Simulation and Teleoperation](https://discourse.openrobotics.org/t/running-ros-noetic-in-docker-a-practical-guide-for-simulation-and-teleoperation/42572)
* [Using ROS in a Docker Container](https://medium.com/@vikramsetty169/using-ros-in-a-docker-container-862bcbd9d4bf)
* [How to Create a ROS 2 Docker Image for Running GUI Tools — Part 1](https://medium.com/@kaitungyu/how-to-create-a-ros-2-docker-image-for-running-gui-tools-part-1-95c2c886c6fd)
* [How to Create a ROS 2 Docker Image for Running GUI Tools — Part 2](https://medium.com/@kaitungyu/how-to-create-a-ros-2-docker-image-for-running-gui-tools-part-2-5bdcec79c81c)
* [How to Create a ROS 2 Docker Image for Running GUI Tools — Part 3](https://medium.com/@kaitungyu/how-to-create-a-ros-2-docker-image-for-running-gui-tools-part-3-69ddf6a21b7f)

* [ROS 2 Best Practices](https://henkirobotics.com/ros-2-best-practices/)


---------------


# Using Docker for ROS 2 Deployment
[Robot Operating System (ROS)][03] is a framework consisting of a huge number of libraries and tools specifically for developing robots.
It’s open source, supported by a large community,
and designed to support real-time performance and multi-robot systems.
ROS is primarily tested on Ubuntu, Mac OS X, and Windows but they also have a Docker version available.

Here is a [brief description][10] of the inter-workings of the ROS ecosystem,
but here is a summary of the major components:

* [Robot Operating System 2 (ROS 2)][03] framework as described above.
* [Gazebo][04] is a powerful open-source robotics simulator that allows developers to test
  and validate robot designs in complex environments, offering realistic physics and sensor models.
* [RViz][05] is a 3D visualization tool for ROS that enables developers to
  visualize sensor data, robot models, and environment maps, aiding in debugging and monitoring robot behavior.

The following tasks will be performed:
* Install Docker
* Running ROS in Docker Container
* Create Working Docker Containers for [Bumper-Bot][18] and [TurtleBot3][17]

## Create Base DevContainer (Jazzy)


### prerequisites

```bash
# first you should have the GitHub CLI (gh)
sudo apt update
sudo apt -y install curl wget gh

# install the GitHub CLI GPG key and repository
sudo mkdir -p -m 755 /etc/apt/keyrings
wget -qO- https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null
sudo chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null

# the gh command won't work until you link it to your GitHub account
gh auth login
```

### What is a DevContainer?
A development container (dev container or DevContainer for short)
allows you to use a container as a full-featured development environment.
You can configure the dev container for GitHub (aka GitHub Codespace) so that repository gives you a tailored development environment,
complete with all the tools and runtimes you need to work on a specific project, including running in GitHub's cloud (but not necessary).
There are specifications for DevContainer (see [Development Containers][01] and [Codespaces: Introduction to dev containers][02]).

This is how you can [develop inside a container][06], with Visual Studio Code (VS Code) following the DevContainer specifications:

* **Key Features & Benefits:**
  * **Cloud-Based:** Runs in GitHub's cloud, accessible from anywhere with an internet connection, reducing reliance on local machine power.
  * **Consistent Environments:** Ensures everyone working on a project gets the exact same setup, defined in the repository's configuration.
  * **Fast Setup:** Spin up a complete, ready-to-code environment in seconds, perfect for new contributors or switching projects.
  * **Customizable:** Configure the OS, tools, runtimes, and extensions using configuration files (`.devcontainer.json`).
  * **Integrated Editor:** Works seamlessly with Visual Studio Code (VS Code) and a browser-based editor, providing a familiar interface.
  * **Cost-Effective:** Offers free hours monthly, with pausing after inactivity to save costs.
* **How it Works:**
  1. You select a repository and launch a Codespace.
  1. GitHub spins up a virtual machine and a Docker container.
  1. It clones your repository and installs project dependencies based on your configuration.
  1. You connect via your browser or VS Code, accessing a full development environment with terminal, debugger, and editor.

I will not be using the full breath of the DevContainer specifications,
since I plan to work locally and I want to use my own development tools.
Never the less, following the DevContainer paradigm is very helpful.

### DevContainer ROS2 Images
The easiest and quickest way to get started is to pull the base ROS2 Jazzy image from Docker Hub:
If we don’t need to make any modifications to the base image, there’s no need to create a Dockerfile.

The primary tags to use for the [official ROS2 images][25] (desktop version [here][27]) are:
* **`ros:jazzy-ros-base`:** This image includes the ROS 2 base packages (communication libraries, message definitions, and core functionality)
  but no desktop tools or simulation environments. This is a common choice for deployment or building specific components.
* **`ros:jazzy`:** This is an alias for `ros:jazzy-ros-base` and points to the latest Jazzy base image.
* **`ros:jazzy-ros-core`:** This is an even more minimal image, containing only the ROS graph and communication libraries (ROS Core).
* **`osrf/ros:jazzy-desktop`:** This image includes a more complete installation of ROS 2,
  including the `ros-base` packages plus tools like `rviz` and `gazebo` integration for development purposes.
* **`osrf/ros:jazzy-desktop-full`:** A complete, full installation of all ROS 2 desktop tools, demos, and tutorials

Since I'm following the [RCLPY From Zero to Hero][07] book as my guide on how to build and manage my ROS2 development,
I will be using the DevContainer images  repository created by the author for the book.
This repository provides a ready-to-use ROS 2 development environment using Visual Studio Code's DevContainer feature
(use of Visual Studio is optional).
It allows you to quickly set up a Docker-based containerized workspace for
ROS 2 development without manually configuring dependencies.
The `ros:jazzy-ros-base` and `osrf/ros:jazzy-desktop-full` versions
can be found as [packages on the Robotics Contents Lab GitHub site][09].
You can either create a new repository from this template via the GitHub CLI or directly through GitHub's interface
([documentation for this process][11]):

```bash
# change to the directory where you want to do your ros2 development
cd ~/tmp/ros2_ws

# clone the Robotics-Content-Lab/ros2_devcontainer repository into your github
#   gh repo create    tells the GitHub CLI to create a brand new repository under your account
#   test-project      your new repository is named test-project
#   --template ...    uses Robotics-Content-Lab/ros2_devcontainer as a blueprint, copy all the starter files, configurations, and Docker settings from that source
#   --private         ensures the new repository is hidden from the public. Only you can see it.
#   --clone           Once the repo is created on GitHub's servers, this immediately downloads (clones) a copy to your local computer.
gh repo create test-project --template Robotics-Content-Lab/ros2_devcontainer --private --clone

# create directory where the base devcontainer will be stored on your computer and clone robot content lab's devcontainer
git clone https://github.com/Robotics-Content-Lab/rclpy-from-zero-to-hero-container.git ~/ros2_ws/test-project
```

Why use this specific template `--template Robotics-Content-Lab/ros2_devcontainer`?
The template you're using (`Robotics-Content-Lab/ros2_devcontainer`) is designed for DevContainers.
When you open this cloned folder in VS Code,
it will likely prompt you to "Reopen in Container."
If you do, it will build a specific Docker environment pre-loaded with:

* Ubuntu (the correct version for your ROS 2 distro)
* ROS 2 (Humble, Iron, or Jazzy)
* Development tools like `colcon`, `rosdep`, and C++/Python extensions.

This saves you from the "it works on my machine" headache by
making sure your environment is identical to the template's configuration.

### My DevContainer Conventions
I'm basically following the DevContainer conventions established in the [RCLPY From Zero to Hero][07] book.
The specific ROS 2 DevContainer cloned and modified for my needs is managed by the [Robotics Content Lab](https://www.roboticscontentlab.com/)
in GitHub repository [Robotics-Content-Lab/ros2_devcontainer](https://github.com/Robotics-Content-Lab/ros2_devcontainer).
This repository provides a ready-to-use ROS 2 development environment using Visual Studio Code's devcontainer feature.
It allows you to quickly set up a Docker-based containerized workspace for ROS 2 development without manually configuring dependencies.

Follow the steps below to set up and start working with these ROS 2 devcontainer environment:

It has two prerequisites:
* **[Docker](https://www.docker.com/get-started):** Ensure that Docker is installed and running on your machine.
* **[Visual Studio Code](https://code.visualstudio.com/):** The **optional** development environment,
  and the [Remote - Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers),
  required for running DevContainers in VS Code.

Follow the steps below to set up and start working with the ROS 2 DevContainer environment:

1. **Clone the DevContainer Repository from GitHub** -
This will create a local repository, with pre-install scripts, to further configure your development environment.

```bash
# create a new local repository this template Robotics-Content-Lab/rclpy-from-zero-to-hero-container
git clone https://github.com/Robotics-Content-Lab/rclpy-from-zero-to-hero-container.git ~/tmp/test-project

# delete the git metadata for fresh start
rm -rf ~/tmp/test-project/.git

# reinitialize the local git repository
git -C ~/tmp/test-project init
git -C ~/tmp/test-project add --all
git -C ~/tmp/test-project commit -m "first commit"

# push your initial local git repository to github
gh repo create --source=/home/jeff/tmp/test-project --private --push
```

1. **Clone the GitHub Repository to Local Machine** -

```bash
# change directory to your codespace and clone the template you created
cd ~/ros2_ws/src
gh repo clone jeffskinnerbox/test-project
```

1. **Start Your Container and Tmux UI** -
Via a script, you can specify options like ROS distribution, base image, UI, and graphics platform.

```bash
# build your DevContainer
cd ~/tmp/test-project
sudo bash scripts/run_docker.sh -d jazzy -p base -t terminal -g standard
#bash ./scripts/run_docker.sh -d jazzy -p desktop -t vnc -g nvidia

# check the status of the DevContainer - list all images for containers
sudo docker image ls

# check the status of the DevContainer - list all containers (running, stopped, etc.)
sudo docker ps -a
```

1. Attach a Terminal to the Running DevContainer** -

```bash
sudo bash ./scripts/attach_terminal.sh
```

1. **Add Your ROS 2 Packages** -
Once you've cloned the repository, add your ROS 2 `colcon` packages to the `src` directory,
and build your new ROS 2 packages within the DevContainer:


1. Open in Visual Studio Code - After adding your packages:
* Open the repository folder in Visual Studio Code.
* When prompted, click on **Reopen in Container**.
    This will automatically build the DevContainer environment.


# see ROS 2 Devcontainer Setup for documentation - <https://github.com/Robotics-Content-Lab/ros2_devcontainer/pkgs/container/jazzy>
# to install the ROS2 container
# ghcr.io is the URL for the GitHub Container Registry (GHCR), GitHub's service for hosting, storing, and managing container images (like Docker images) directly within your GitHub account or organization, integrated with repositories and Actions for seamless CI/CD. It functions similarly to Docker Hub but offers tighter integration with the GitHub ecosystem, allowing you to manage image permissions separately from repository permissions and use Personal Access Tokens (PATs) or GITHUB_TOKEN for authentication


docker pull ghcr.io/robotics-content-lab/rclpy-from-zero-to-hero:jazzy-base-terminal-standard
# List all containers (running, stopped, etc.)
docker ps -a
# list all images for containere
docker image ls
                                                            i Info →   U  In Use
IMAGE                           ID             DISK USAGE   CONTENT SIZE   EXTRA
ghcr.io/robotics-content-lab/rclpy-from-zero-to-hero:jazzy-base-terminal-standard
                                c48c4ae8c25f       11.8GB         4.18GB

# start the container & bring up Tmux UI
cd ~/rclpy-from-zero-to-hero-container/
bash scripts/run_docker.sh -d jazzy -p base -t terminal -g standard

# Tmux split horizontial & vertical
vertical split         Ctrl + b then %
horizontial split    Ctrl + b then "
sudo apt install ros-jazzy-turtlebot3-gazebo
Correctly Install TurtleBot3 Robot in ROS and Simulate Movement in Gazebo 3D Worlds - ROS Tutorial -
<https://www.youtube.com/watch?v=_RBZ-9_rz9Y>
<https://emanual.robotis.com/docs/en/platform/turtlebot3/simulation/>

```bash
# create directory where the base devcontainer will be stored and clone robot content lab's devcontainer
git clone https://github.com/Robotics-Content-Lab/rclpy-from-zero-to-hero-container.git ~/ros2_ws/devcontainer

cd ~/ros2_ws/devcontainer
```

## Create DevContainer for TurtleBot3 Robot in ROS2 and Simulate Movement in Gazebo 3D Worlds

* [Correctly Install TurtleBot3 Robot in ROS and Simulate Movement in Gazebo 3D Worlds - ROS Tutorial](https://www.youtube.com/watch?v=_RBZ-9_rz9Y)
* [Learning ROS Through Simulation with TurtleBot3 and Gazebo - Part 1](https://www.youtube.com/watch?v=cOMtzShsGug)







---------------











## Install Docker
**Docker** is a popular application that simplifies the process of managing application processes in containers.
Containers let you run your applications in resource-isolated processes.
They’re similar to virtual machines, but containers are more portable,
more resource-friendly, and more dependent on the host operating system.

>**NOTE:** By default, the docker command can only be run the root user
>or by a user in the docker group, which is automatically created during Docker’s installation process.

Sources:
* [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)
* [Install the Compose Plugin](https://docs.docker.com/compose/install/linux/#install-using-the-repository)

### Docker Engine & Docker Compose
Ubuntu is my go-to Linux OS and installing on Ubuntu is fairly straight-forward.
I'll used the installation scripts below.
This involves adding a new package source,
adding the GPG key from Docker to ensure the downloads are valid,
and then install the Docker package.

#### Step 1: Install Docker - DONE
While not the absolute latest Docker version,
I’ll install Docker from the Dockers official Ubuntu repository,
instead of Docker's generic repository.

```bash
# before you can install docker engine, you need to uninstall any previous installed conflicting packages
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done

# clean up any existing docker related data
rm /var/lib/docker/*

# update your existing list of ubunutu packages
sudo apt update
```

Now let do the actual install of Docker:

```bash
# add Docker's official gpg key
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# add the repository to apt sources
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

From the above last command,
you'll see the installation will be from the Docker repository for what ever version of Ubuntu you are running.
Now lets install Docker:

```bash
# install the latest version of docker
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# docker should be running, but make sure
sudo service docker start
sudo service docker status

# verify that the docker engine installation is successful running
sudo docker run hello-world
```

Source:
* [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)

#### Step 2: Install Docker Compose - DONE

To ensure we get the latest version,
we’ll install Docker Compose from the official Docker repository.
To do that, we’ll add a new package source,
add the GPG key from Docker to ensure the downloads are valid,
and then install the package.

```bash
# download docker compose
sudo apt update
sudo apt install docker-compose-plugin

# verify that the installation of docker compose was successful
docker compose version
```

#### Step 4: Upgrade Docker & Docker Compose - DONE

Docker & Docker Compose will be automatically by Ubuntu from the official Ubuntu repository for Docker.


---------------


## Devices in Linux & Docker

* [Devices in Docker - Not so simple! (Docker for Robotics #4)](https://www.youtube.com/watch?v=uf4zOigzTFo)
* [Logitech F310 Gamepad Review On Linux](https://www.gamingonlinux.com/2015/05/logitech-f310-gamepad-review-on-linux/)

I purchased a [Logitech F310 Wired Gamepad Controller](https://www.logitechg.com/en-gb/products/gamepads/f310-gamepad.940-000138.html) on [Amazon](https://www.amazon.com/dp/B003VAHYQY) for $20.
The Logitech F310 Wired Gamepad Controller is generally supported out-of-the-box in Ubuntu.
It's a USB wired controller that typically works directly when plugged into a PC without requiring special drivers.
The F310 has both [D-Input (DirectInput) and X-Input (XInput) modes](https://www.howtogeek.com/792984/directinput-vs.-xinput-for-game-controllers-whats-the-difference/), which are widely supported by Linux games.

Some Linux programs for testing devices:

* The [`evtest`](https://manpages.ubuntu.com/manpages/noble/man1/evtest.1.html) tool in Linux is used to monitor and query events generated by input devices, such as keyboards, mice, joystick, and touchpad. It helps in debugging issues with input devices and understanding the events they generate.
You can use `evtest` to see what events are generated when you press a specific key on your keyboard or click a mouse button.
It allows users to monitor the raw data coming from keyboards, mice, touchscreens, joysticks, and other input peripherals.
* [`jstest-gtk`](https://manpages.ubuntu.com/manpages/jammy/man1/jstest-gtk.1.html) is  mainly a graphical interface to check that your joysticks and pads work properly. You can find precise information on each axis, you can optionally recalibrate it and also change the mapping.
If you run the program without parameters, you will get a window showing all the joystick devices in your system  (there  can  be more than one).
* Install these tools with `sudo apt install evtest jstest-gtk`

* Gemini Prompt: In linux, how do I configure a joystick or gamepad
* [How do I configure a joystick or gamepad?](https://askubuntu.com/questions/32031/how-do-i-configure-a-joystick-or-gamepad)


---------------


## Docker for ROS Robotics
When developing robotics software, setting up your environment can be frustrating—installing ROS 2,
managing dependencies, and making sure everything works the same on different computers.
Docker is a tool that helps you define and build an environment in which your application can run,
encapsulating everything it needs, including the runtime, system tools, libraries, and settings.
This ensures that applications behave consistently across different platforms, solving the [“it works on my machine” problem][22].
Because everything is bundled together,
Docker containers make sure your project runs the same way, whether on your laptop, a robot, or a cloud server.
No more “it works on my machine” issues!

Docker ensures this consistency by maintaining the same environment across different deployments.
Docker isn’t just a tool — it’s a foundational part of DevOps.
For robotics, it means faster testing, less time debugging setup issues,
and smoother deployments to field robots or simulation environments.
And if you wish to run your robotics application in the cloud,
Docker streamlines the process of setting up the cloud environment to run your robotics applications.

Sources:
* [ROS2 in Docker — Why and How?](https://medium.com/@oelmofty/ros2-in-docker-why-and-how-b72b3880dc97)
* [Setup ROS2 in a Docker Container](https://devanshdhrafani.com/posts/2021-04-15-dockerros2/)
* [RCLPY From Zero to Hero][07]
* [The Complete Beginner’s Guide to Using Docker for ROS 2 Deployment (2025 Edition)](https://blog.robotair.io/the-complete-beginners-guide-to-using-docker-for-ros-2-deployment-2025-edition-0f259ca8b378)
* [The Complete Guide to Docker for ROS 2 Jazzy Projects](https://automaticaddison.com/the-complete-guide-to-docker-for-ros-2-jazzy-projects/)
* [Docker for Robotics](https://www.youtube.com/playlist?list=PLunhqkrRNRhaqt0UfFxxC_oj7jscss2qe)
* [The Complete Guide to Deploying ROS Applications in Production](https://blog.robotair.io/the-complete-guide-to-deploying-ros-applications-in-production-07a652a2e2f8)

### Containerized Robots - TurtleBot3
* [What is TurtleBot?][17]
* [TurtleBot3](https://wiki.ros.org/turtlebot3)
* [Robotis Turtle3](https://emanual.robotis.com/docs/en/platform/turtlebot3/docker_container_setup/)
* [ROS 2 docker image using the Gazebo simulation](https://github.com/brean/ros2-turtlebot3-gazebo-docker)
* [TurtleBot Behavior Demos](https://github.com/sea-bass/turtlebot3_behavior_demos/tree/main)

Various community-maintained Docker images are available for running TurtleBot3 with ROS 2,
as there are no official Docker images provided by ROBOTIS directly through Docker Hub.
These images often include the necessary dependencies for simulation (Gazebo)
or real hardware operation across different ROS 2 distributions (Humble, Jazzy, etc.).

#### Where to Find TurtleBot3 ROS 2 Docker Images
Most images are hosted on Docker Hub or the source `Dockerfile` is provided in GitHub repositories for building yourself.

* **For Simulation:** Repositories such as `apresland/ros2-turtlebot3-sim` offer
  images for running the TurtleBot3 in a Gazebo simulation environment.
  The image `andrewpresland/ros2-turtlebot3-sim:latest` is readily available for pulling.
* **For Specific ROS 2 Distributions:**
  * **For ROS 2 Humble**, you can explore images like `ubeike/ros2-humble-turtlebot3`
    or review the humble branches in repositories such as `arshadlab/tb3_multi_robot`.
  * **For ROS 2 Jazzy**, repositories like `sea-bass/turtlebot3_behavior_demos`
    provide examples of Docker workflows for the latest ROS 2 release.
* **For Real Hardware / Remote PC:** Projects like `brean/ros2-turtlebot3-remote-pc-docker` offer configurations
  for connecting to a real TurtleBot3, often requiring `host` networking mode in Docker.
* **Official Documentation Examples:** The ROBOTIS e-Manual provides a guide on setting up a Docker container,
  generally for running the `turtlebot3_bringup` and other core packages on the single board computer (SBC) of the robot itself.

#### Official & Popular Docker Images
* **ROBOTIS e-Manual Images:** Official configurations are typically provided via
  specialized scripts in the TurtleBot3 GitHub repository that build or pull images for specific ROS 2 distros (Foxy, Humble, and Jazzy).
* **Humble Simulation (brean/ros2-turtlebot3):** A widely used community image for ROS 2 Humble and Gazebo simulation.
  It includes pre-installed packages for navigation and RViz2.
* **Jazzy Support:** New for 2025/2026, repositories like `arshadlab/tb3_multi_robot` provide images for ROS 2 Jazzy and Gazebo Harmonic, supporting multi-robot simulations.
* **Standard Base (osrf/ros):** Many developers build custom images using `osrf/ros:humble-desktop-full`
  or `osrf/ros:jazzy-desktop` as the base to include specific dependencies like `nav2`.

#### Key Considerations
* **Host OS and GPU Support:** For simulations using Gazebo, you may need a specific Docker version
  (e.g., `docker-nvidia2` for NVIDIA graphics cards) to enable GPU acceleration.
* **Network Configuration:** When working with real hardware or communication between multiple containers,
  you might need to configure the network mode (e.g., `network_mode: host`) and set the appropriate `ROS_DOMAIN_ID`.
* **Building vs. Pulling:** While pulling pre-built images is faster,
  building the image from a `Dockerfile` yourself allows for greater customization
  and ensures compatibility with your specific system and project requirements

#### Key Setup Requirements
To run these images successfully, you must configure specific environment variables and hardware passthroughs:
* **TURTLEBOT3_MODEL:** Set this to `burger`, `waffle`, or `waffle_pi` (e.g., `export TURTLEBOT3_MODEL=burger`).
* **GUI Display:** Pass the host's display to the container using `-e DISPLAY=$DISPLAY`
  and mounting the X11 socket (`-v /tmp/.X11-unix:/tmp/.X11-unix`) to see Gazebo or RViz.
* **Hardware Acceleration:** For NVIDIA users, use the `--gpus all` flag or `nvidia-docker2`
  to ensure smooth 3D simulation performance.

### ROS2 Using Docker - ROS2 DevContainer
* [How to Install and Launch ROS2 Using Docker](https://automaticaddison.com/how-to-install-and-launch-ros2-using-docker/)


**Basic ROS2 Image**
The basic ROS2 image only includes core components of ROS and does not contain development tools

```bash
# pull ros base image from docker hub
docker image pull ros:jazzy-ros-base

# if we don’t need to make any modifications, simply run a container from the base image
# the argument -it allows an interactive shell to be opened in the container
docker run -it --name base_ros2_container ros:jazzy-ros-base

# if you want to open another terminal within that same container
docker exec -it base_ros2_container /bin/bash
```

**Full Desktop ROS2 Image**
This is a complete, full installation of all ROS 2 desktop tools, demos, and tutorials

```bash
# pull ros desktop image from docker hub
docker image pull osrf/ros:jazzy-desktop-full

# run a container from the ros desktop image
# the -v option allows Docker to mount a volume to the container, enabling the container to access directories on the host machine’s filesystem, such as the X server
# the -e DISPLAY=$DISPLAY argument passes the DISPLAY environment variable from the host to the container
docker run -it -v /tmp/.X11-unix/:/tmp/.X11-unix/:rw --env=DISPLAY --name ros2_container osrf/ros:jazzy-desktop-full
```

**Crafting your Dockerfile**
If you want to modify the base image of ROS2, you’ll need to create your own Dockerfile.
Let’s walk through an example,
such as by installing the [Nav2 stack][23] along with [TurtleBot3 packages][24] in your container.

Here is the Dockerfile:

```docker
# extend the ROS2 distro
FROM osrf/ros:jazzy-desktop-full

# install the required packages
RUN apt-get update \
 && apt-get install -y \
 ros-jazzy-navigation2 \
 ros-jazzy-nav2-bringup \
 ros-jazzy-turtlebot3* \
 && rm -rf /var/lib/apt/lists/*

# Set the environment variable required to run TurtleBot3
ENV TURTLEBOT3_MODEL=burger
```

We can then build the Docker image using the following command

```bash
# build the docker image (executed in dockerfile directory)
sudo docker build -t turtlebot3_image .

# create the container
# automatically open interactive shell in the container
sudo docker run -it -v /tmp/.X11-unix/:/tmp/.X11-unix/:rw --env=DISPLAY --name turtlebot3_container turtlebot3_image

# inside the container, you can now boot up the turtlebot3 simulation
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py

# if you want to open another terminal within that same container
sudo docker exec -it turtlebot3_container /bin/bash
```


---------------


## Running ROS 2 Jazzy Jalisco in Docker Container ("Robotics and ROS 2 Essentials" version)

One of the ROS courses on the Web is ["Robotics and ROS 2 Essentials"][13],
which is a beginner-friendly introduction to robotics and ROS 2,
and it has a focus on learning by doing and experimenting through exercises.
The practical exercises that accompany the theoretical content are
based on a Gazebo simulation with the [simulated Andino robot from Ekumen][14].

One of the nice things about this course is that ROS doesn't need to be installed on your system.
Instead, the course uses Docker to provide all the course exercises in a containerized environment,
requiring no manual installation of ROS 2, simulation, packages, and dependencies.
All you need is an Ubuntu Operating System and Docker installed, and you are all set!

### Setup for Dockerized ROS

Despite it simplicity, there are some challenges to get it working within my configuration
where I wish to running a X Window System (X11) application on my server (the GMKTec with Ubuntu 24.04)
but display its graphical output on a remote client (my `desktop` with Ubuntu with X Window).
**This will not work for me.**
Appears the Docker container was built to support everything working on the server.
So that is documented below.

>**NOTE:** No preliminary ROS 2 installation is required.
>Instead, the course uses Docker to provide all the course exercises in a containerized environment,
>requiring no manual installation of ROS 2, simulation, packages, and dependencies

#### Step 0: Install ROS Docker Container

[Exercises 0 - Setup](https://github.com/henki-robotics/robotics_essentials_ros2/tree/main/0-setup)

```bash
# clone the repository containing ros2 and gazebo simulator
cd ~/src
git clone https://github.com/henki-robotics/robotics_essentials_ros2.git

# create a new workspace for your exercises, this will be automatically mounted and available from the docker container
mkdir -p $HOME/exercises_ws/src
```

Before bring up the Docker container, run the following command.
This will give permissions to your containers to send their display to the containers host system.

```bash
# give permissions to your containers to send their display to the containers host system.
xhost +

# use docker compose to build and run the Docker container
cd ~/src/robotics_essentials_ros2/docker/
sudo docker compose up
```

Now open a new terminal (e.g. via `CTRL+ALT+T` and run this command to start a new terminal inside the Docker container.
The `docker exec` command opens a new terminal inside this Docker container,
allowing you to interact with it.

```bash
# get terminal access to the inside of the docker container
sudo docker exec -it robotics_essentials_ros2 bash
```

Now while in the terminal inside the Docker container, we perform a test to make sure everything is working correctly:

```bash
# while inside the docker container
# perform a test to make sure everything is working correctly
ros2 launch andino_gz andino_gz.launch.py
```

Sources:

* [Robotics and ROS 2 Essentials: Exercises 0 - Setup](https://github.com/henki-robotics/robotics_essentials_ros2/tree/main/0-setup)
* [GUI apps within a Docker container](https://medium.com/@paliwalsamriddhi/gui-apps-within-a-docker-container-971681838fda)
* [X11 forwarding from a docker container in remote server](https://unix.stackexchange.com/questions/403424/x11-forwarding-from-a-docker-container-in-remote-server)

#### Step 1: Exercises 1 - ROS 2 Introduction

In this [Exercises 1 - ROS 2 Introduction](https://github.com/henki-robotics/robotics_essentials_ros2/tree/main/1-ros_2_introduction#basic-concepts),
**ROS 2 Topics** are the first to be explore.
ROS 2 Topics are a core communication mechanism in ROS 2 that enable
data exchange in a publish/subscribe model.
Publishers send messages to a named topic,
while subscribers listen to that topic to receive relevant data.

In another terminal, execute these commands:

```bash
# in another terminal, gain access to ros
sudo docker exec -it robotics_essentials_ros2 bash

# list all the available ROS 2 topics
$ ros2 topic list
/camera_info
/clicked_point
/clock
/cmd_vel
/goal_pose
/image_raw
/initialpose
/joint_states
/odom
/parameter_events
/robot_description
/rosout
/scan
/scan/points
/tf
/tf_static

# get more info about the /camera_info topic to learn the message type
$ ros2 topic info /camera_info
Type: sensor_msgs/msg/CameraInfo
Publisher count: 1
Subscription count: 0

# get more info about the /scan topic to learn the message type
$ ros2 topic info /scan
Type: sensor_msgs/msg/LaserScan
Publisher count: 1
Subscription count: 1

# read the sensor data from the laser scanner (press CTRL+C to stop)
ros2 topic echo /scan

# move the robot by publishing to /cmd_vel topic
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist "{linear: {x: 0.2}}"

# send zero velocity command to stop the robot
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist "{linear: {x: 0.0}}"

# rotate the robot with this command
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist "{angular: {z: 0.5}}"

# to stop the rotation, do the following
ros2 topic pub /cmd_vel geometry_msgs/msg/Twist "{angular: {z: 0.0}}"
```

**RViz** is a useful visualization tool that allows us to display data from ROS 2 topics.
The robot is constantly publishing images from the simulated camera.
Let's see how those images look like!

In ROS 2, **Coordinate Transforms (TF)**
are used to describe the spatial relationships between different coordinate frames in a robotic system.
They sit at the center of the robot, at the center of sensors, at joints,
and there are so the "Map" and "Odometry" frames.

Commonly used coordinate frames are as follows:

* **map** - The map frame provides a global reference point for the robot's environment,
allowing it to understand its position within a larger context.
Typically, the coordinates in the map frame present the robot's coordinates on a 2D map.
* **odom** - The odom frame represents the robot's position based on its odometry data.
It tracks the robot's movement from its starting point, being subject to drift and inaccuracies.
* **base_footprint** - The base_footprint frame is a 2D representation of the robot's footprint on the ground,
typically used for planning and movement calculations without considering the robot's height.
* **base_link** - The base_link frame represents the robot's main body
and is used as a reference for other components, such as sensors and arms.
* **laser_link** - The laser_link frame denotes the position of a laser sensor on the robot.
It is essential for interpreting the data collected by the laser
for tasks like mapping and obstacle detection,
providing a reference for where the sensor is located in relation to other frames.

TF frames in RViz

* **fixed frame** - The fixed frame is used to determine from which frame's perspective you are visualizing the data.
This is an important feature to know about,
as sometimes the data you are looking to visualize might not be available if you are visualizing a wrong frame.

TFs allow you to convert positions and orientations from one frame to another,
and basically keep track of how each part of your robot moves in relation to the other parts of the robot.
This is crucial for tasks like navigation, sensor fusion, and manipulation.
By using transforms, robots can effectively understand their position in the world and how their sensors
and motors are located in relation to their body.

The relationship between these coordinate frames is determined with **tf-tree**.
It essentially tells, with a tree-like structure,
what is the child-frame's position in relation to the parent frame.

#### Step 2: Exercises 2 - SLAM and Navigation Demo

In this [Exercises 2 - SLAM and Navigation Demo](https://github.com/henki-robotics/robotics_essentials_ros2/blob/main/2-slam_and_navigation_demo/README.md),
we'll use the robot to build a new 2D map of the simulated environment and autonomously navigate on it.
The packages that will be used perform these tasks are:

* [Slam-toolbox](https://github.com/SteveMacenski/slam_toolbox/tree/ros2) is an advanced 2D SLAM (Simultaneous Localization and Mapping)
solution for ROS 2.
* [Nav2, aka Navigation2](https://github.com/ros-navigation/navigation2), is a framework for ROS 2 that enables robots to navigate autonomously.
* [AMCL](https://github.com/ros-navigation/navigation2/tree/main/nav2_amcl) (stands for [Adaptive Monte Carlo Localization](https://roboticsknowledgebase.com/wiki/state-estimation/adaptive-monte-carlo-localization/)) is a probabilistic localization system used in ROS 2, and is part of the Nav2 stack.
It enables robots to determine their position within a known map using particle filters.
AMCL uses sensor data, typically from a LiDAR, to refine the estimated pose of the robot as it navigates.

To get ROS2 up & running, execute these commands in a terminal:

```bash
# give permissions to your containers to send their display to the containers host system.
xhost +

# use docker compose to build and run the Docker container
cd ~/src/robotics_essentials_ros2/docker/
sudo docker compose up
```

In another terminal, gain access to ROS within the container
and run the simulator:

```bash
# in a terminal, gain access to ros
sudo docker exec -it robotics_essentials_ros2 bash
ros2 launch andino_gz andino_gz.launch.py

# run slam-toolbox
sudo docker exec -it robotics_essentials_ros2 bash
ros2 launch andino_gz slam_toolbox_online_async.launch.py
```

In RViz, subscribe to /map topic to view the map that is being built
Use Gazebo teleop to drive the robot around in the simulation and map the area.

Once you are satisfied with the map,
open a new terminal inside the Docker container and run this command to save it:

```bash
# in another terminal, gain access to ros
sudo docker exec -it robotics_essentials_ros2 bash

# launch the Andino simulation with Nav2
ros2 launch andino_gz andino_gz.launch.py nav2:=True
```

#### Step 3: Exercises 3 - Create Your First Ros 2 Package


In this [Exercises 3 - Create Your First Ros 2 Package](https://github.com/henki-robotics/robotics_essentials_ros2/tree/main/3-create_ros_2_package)

#### Step 4: Exercises 4 - Robot Odometry

In this [Exercises 4 - Robot Odometry](https://github.com/henki-robotics/robotics_essentials_ros2/tree/main/4-robot_odometry)

#### Step 5: Exercises 5 - Path Planning

In this [Exercises 5 - Path Planning](https://github.com/henki-robotics/robotics_essentials_ros2/tree/main/5-path_planning)

#### Step 6: Remove All Stopped Containers

To clean up all the Docker object created by this course,
execute the following:

```bash
# stop and remove all of parts of the 'robotics_essentials_ros2' container
sudo docker stop robotics_essentials_ros2
sudo docker rm robotics_essentials_ros2
sudo docker rmi --force robotics_essentials_ros2
```


---------------


## Running ROS 2 Jazzy Jalisco in Docker Container ("[RCLPY From Zero to Hero][07]" version)
DevContainers provide a way to develop in a containerized environment.
the convenience script for Unix based systems that will start the docker container. The scripts will automatically pull the latest version of the docker container from the docker hub and start it.

The `run_docker` scripts provide a flexible setup for ROS 2 environments. You can specify
ROS distribution, base profile, UI type, and graphics platform, allowing tailored configurations

* **Automatic GPU Detection:** Determines GPU type (NVIDIA or AMD) for graphics platform settings.
* **WSL Support:** Adapts configurations for Windows Subsystem for Linux (WSL), ensuring seamless Docker integration.
* **Workspace Mounting:** Mounts your local ROS 2 workspace (`ros2_src`) to `/home/ros_user/ros2_ws/` inside the container.
* **UI Selection:** Choose between terminal interaction or VNC for GUI-based applications.
* **Error Handling:** Provides detailed help messages and error diagnostics for troubleshooting.

Taken from "[RCLPY From Zero to Hero][07]" (page 18), authored by [Georg Adrian Novotny][08].

```bash
# make sure docker is running
sudo systemctl start docker

# download the container image
ghcr.io/robotics-content-lab/rclpy-from-zero-to-hero:jazzy-base-terminal-standard

# start the container & bring up Tmux UI
cd ~/ros2_ws/rclpy-from-zero-to-hero-container/
bash scripts/run_docker.sh -d jazzy -p base -t terminal -g standard
```



[01]:https://containers.dev/
[02]:https://docs.github.com/en/codespaces/setting-up-your-project-for-codespaces/adding-a-dev-container-configuration/introduction-to-dev-containers
[03]:https://www.ros.org/
[04]:https://gazebosim.org/home
[05]:http://wiki.ros.org/rviz
[06]:https://code.visualstudio.com/docs/devcontainers/containers
[07]:https://www.roboticscontentlab.com/product/ros2-rclpy-from-zero-to-hero/
[08]:https://novog93.github.io/
[09]:https://github.com/orgs/Robotics-Content-Lab/packages
[10]:https://hackaday.com/2018/05/31/modular-robotics-made-easier-with-ros/
[11]:https://github.com/Robotics-Content-Lab/ros2_devcontainer/pkgs/container/jazzy

[13]:https://henkirobotics.com/robotics-and-ros-2-essentials-course-announcement/
[14]:https://github.com/Ekumen-OS/andino_gz/tree/humble

[17]:https://www.turtlebot.com/turtlebot3/
[18]:https://github.com/AntoBrandi/Bumper-Bot/

[22]:https://www.reddit.com/r/ProgrammerHumor/comments/4te2z5/it_works_on_my_computer/
[23]:https://github.com/ros-navigation/navigation2
[24]:https://github.com/ROBOTIS-GIT/turtlebot3
[25]:https://hub.docker.com/_/ros/
[27]:https://hub.docker.com/layers/osrf/ros/jazzy-desktop-full/images/sha256-b706aba86d1be07e9dc2834bf54c9acf1be87c2bad1aea83cd2f49ff738b6f5e
