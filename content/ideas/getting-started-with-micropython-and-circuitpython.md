<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----



* [The Past, Present, and Future of CircuitPython](https://hackaday.com/2023/08/01/the-past-present-and-future-of-circuitpython/)
* [Getting Started with CircuitPython on XIAO RP2040](https://www.youtube.com/watch?v=KDb5SQzsGb0)





# First, Learn & Master Python
* [9 Things You Do That Shows You Are Not A Professional Python Developer](https://python.plainenglish.io/9-things-you-do-that-show-you-are-not-a-python-professional-b8e0681af9e3)
* [Python — Avoid “from module import *”](https://tonylixu.medium.com/python-avoid-from-module-import-d644e837ecf3)

* [Python 10 minutes a day](https://python-10-minutes-a-day.rocks/)
* [Real Python](https://realpython.com/)
* [The Python Tutorial](https://docs.python.org/3/tutorial/)
* [Introduction to Conda for (Data) Scientists](https://edcarp.github.io/introduction-to-conda-for-data-scientists/)

* [Adafruit CircuitPython API Reference](https://docs.circuitpython.org/en/latest/docs/)
* [Todbot's CircuitPython Tricks](https://learn.adafruit.com/todbot-circuitpython-tricks)
* [CircuitPython Essentials](https://learn.adafruit.com/circuitpython-essentials)
* [Module Support Matrix - Which Modules Are Available on Which Boards](https://docs.circuitpython.org/en/latest/shared-bindings/support_matrix.html)
* [Circuit Python Tutorials](https://www.youtube.com/watch?v=eU1e6xPvZEU&list=PL9VJ9OpT-IPSsQUWqQcNrVJqy4LhBjPX2&index=1)


# You Can Integrate with C
* [MicroPython and C Play Together Better](https://hackaday.com/2019/08/31/micropython-and-c-play-together-better/)
* [Micropython API to *any* C library!](https://blog.lvgl.io/2019-08-05/micropython-pure-display-driver#micropython-api-to-any-c-library)

#  Asymmetric Multiprocessing (AMP) / OpenAMP
With MicroPython v1.23, there is now support for Asymmetric Multiprocessing (AMP) on multi-core microcontrollers, based on the industry standard OpenAMP framework.
This enables Arduino users to run both an Arduino sketch and a MicroPython program simultaneously on multi-core modules and to communicate between the two

* [OpenAMP Runs MicroPython and Arduino Code on Same Dual-Core Microcontroller](https://www.hackster.io/news/openamp-runs-micropython-and-arduino-code-on-same-dual-core-microcontroller-f7a1806dec79)







* [OpenMV CAM RT1062 board for Machine Vision with MicroPython](https://linuxgizmos.com/openmv-cam-rt1062-board-for-machine-vision-with-python/)
* [OpenMV Cam H7 - Machine Vision w/ MicroPython](https://www.kickstarter.com/projects/1798207217/openmv-cam-h7-machine-vision-w-micropython)
* [OpenMV H7 Product Line](https://www.youtube.com/watch?v=E6SCejAeDSs)
* [MicroPython class for OV2640 Camera](https://github.com/namato/micropython-ov2640)
* [Grove - Vision AI Module with Himax HX6537-A processor, thumb-size AI-powered OV2640 camera sensor, support Yolo V5 and Edge Impulse, easy-to-use](https://www.seeedstudio.com/Grove-Vision-AI-Module-p-5457.html)

* [MicroPython Unveils New Pyboard D Series Board with STM32F7xx MCU](https://blog.hackster.io/micropython-unveils-new-pyboard-d-series-board-with-stm32f7xx-mcu-a7721bc09877)

* [Micropython and C Play Together Better](https://hackaday.com/2019/08/31/micropython-and-c-play-together-better/)

* [Simple Neural Network on MCUs](https://blog.hackster.io/simple-neural-network-on-mcus-a7cbd3dc108c)

* [Adafruit’s Feather nRF52840 Express Board and Developing with CircuitPython](https://blog.nordicsemi.com/getconnected/adafruits-feather-nrf52840-express-board-and-developing-with-circuitpython)

* [Micropython On Microcontrollers](https://hackaday.com/2020/11/14/micropython-on-microcontrollers/)
* [Raspberry Pi Pico vs ESPR32: Intro to Microcontrollers with MicroPython](https://www.techtimes.com/articles/256277/20210124/raspberry-pi-pico-vs-espr32-intro-microcontrollers-micropython.htm)

* [Your MicroPython Board Can Be Your Tinkering Peripheral](https://hackaday.com/2022/08/10/your-micropython-board-can-be-your-tinkering-peripheral/)

# MIP Package Manager for MicroPython
[mip](https://docs.micropython.org/en/latest/reference/packages.html),
the new, official lightweight package manager for MicroPython.

* [How To Manage MicroPython Modules With Mip on Raspberry Pi Pico](https://www.tomshardware.com/how-to/raspberry-pi-pico-micropython-mip)


# Hardware Options
## CircuitBrains
CircuitBrains Deluxe is the smallest soldererable ATSAMD51 module. Skip on all the tedious work of adding a 32-bit microcontroller to your next project. We’ve taken care of the tough work of pin mappings, power & decoupling layout, clock, flash, assembly, bootloader, and firmware. All you need to do is drop a footprint into your next PCB design project, connect your peripherals and USB connector, then solder it on and write your code.

* [CircuitBrains Deluxe](https://www.crowdsupply.com/null-byte-labs/circuitbrains-deluxe)
* https://kevinneubauer.com/





------



# CPython, MicroPython, or CircuitPython?
I want to expand my microprocessor/microcontroller skills beyond C/C++
and take advantage of MicroPython or CircuitPython.
But it’s not always clear what the differences are.
All these implementations use [REPL][09] and [GIL][25] (see below).

My interest and hope is that MicroPython/CircuitPython will give me ‘speed’
i.e. get something up and running beyond the embedded ‘hello world’ example.
While MicroPython/CircuitPython, like Python, is an interpreted, high-level,
general-purpose programming language (resulting in slower execution),
it is very expressive and comes with loads of libraries so you can create quickly.

## CPython
CPython is the widely used implementation of the Python programming language, written in C.
Usually, when people talk about Python, they are talking about Python running on CPython.
CPython interprets and executes Python code and provides the core functionality and features of Python.
CPython includes a built-in debugger module, [`pdb`][29], which supports breakpoints and single stepping.
CPython is designed for general purpose (desktops, servers, embedded systems, etc.).

If your working on with an desktop or server, CPython is what you should be using, hands down.

## MicroPython
MicroPython (aka μPython or uPython) is an implementation of Python,
specifically optimized for microcontrollers and embedded systems.
MicroPython thereby doesn’t require an operating system,
you can run it effectively as the operating system on a microcontroller.
Typically, in order to do that, people rely on an IDE like [Thonny][27] or the [Arduino IDE][28].
Unlike CPython, MicroPython doesn’t have built-in support for [`pdb`][29] as a debugging tool.
Instead, if you’re using MicroPython, you’re going to need to rely on other techniques like print statements.

MicroPython is all about providing a compact runtime for less powerful devices.
It uses less memory and really only provides specific modules and libraries for embedded systems.
MicroPython's extensive community and documentation cater to a global user base,
where CircuitPython is more focused on the AdaFruit community.

## CircuitPython
CircuitPython is a fork of MicroPython, developed & supported by [Adafruit](https://learn.adafruit.com/welcome-to-circuitpython/what-is-circuitpython)
with a design objective to be more beginner-friendly than MicroPython.
The differences between MicroPython and CircuitPython are extremely small.
One notable difference is that CircuitPython is designed to have files moved to the board
by appearing as an external disk (just as a USB would).
The idea there is that you don’t need to upload a file through an IDE like Thonny (although you still can).
To understand the difference between CircuitPython and MicroPython,
check out [Adafruit CircuitPython API Reference](https://docs.circuitpython.org/en/latest/docs/index.html).

CircuitPython has a more vibrant community than MicroPython with its broad ecosphere of boards and libraries for sensors and add-ons.
It appears that CircuitPython is more up-to-date and well maintained.
Learning CircuitPython won't detract your possibilities in quickly adopting MicroPython, if required.

Sources:
* [What’s the difference between CPython, MicroPython, & CircuitPython anyway?](https://picockpit.com/raspberry-pi/whats-the-difference-between-micropython-circuitpython-cpython-anyway/)
* [CircuitPython vs MicroPython | Orlando Python](https://www.youtube.com/watch?v=5eS3DUxRRqM)
* [Getting Started with MicroPython](https://python.plainenglish.io/getting-started-with-micropython-c09dd0bbe33c)
* [Getting Started with MicroPython on ESP32 – Hello World, GPIO, and WiFi](https://www.cnx-software.com/2017/10/16/esp32-micropython-tutorials/)

## CircuitPython and CircuitPython Libraries
There is an important difference between CircuitPython and CircuitPython Libraries:

* **CircuitPython** is a microprocessor specific implementation of Python written in C.
It includes chip-specific code that controls the hardware peripherals on the microcontroller,
including things like USB, I2C, SPI, GPIO pins,
and all the rest of the hardware features the chip provides.
This is something standard Python provides minimal or no support.
Here is the [main CircuitPython guide][48].
* **CircuitPython Libraries** is a sensor & breakout specific code written in Python,
using the CircuitPython hardware API,
using the modules provided by CircuitPython to control the
sensors and interact with various breakout boards.
Check out the [Adafruit CircuitPython Library Bundle][49].

## Python's Read-Eval-Print-Loop (REPL)
All these vesion of Python use the [read–eval–print loop (REPL)][09] paridigm,
also termed an interactive computer programming environment,
takes in a single user inputs (i.e., single expressions),
evaluates them, and returns the result to the user.
Classic examples of programming envirments that use REPL are
Lisp machines, PDP-11 Basic, and the Unix/Linux Shell.

Sources:
* [The Python REPL](https://python.land/introduction-to-python/the-repl)
* [WebREPL client for MicroPython](https://github.com/micropython/webrepl)

## Python's Global Interpreter Lock (GIL)
The [Python Global Interpreter Lock (GIL)][25],
is a lock that allows only one thread to hold the control of the Python interpreter.
This means that only one thread can be in a state of execution at any point in time.
The impact of the GIL isn’t visible to developers who execute single-threaded programs,
but it can be a performance bottleneck in CPU-bound and multi-threaded code.
Since we now live in a world of multi-core computer architectures,
where multiple threads can be execute d concerently in a multi-threaded architecture,
the GIL is a sometime hatted feature of Python.

>**NOTE:** The Python Steering Council plans to approve a proposal that will make GIL optional
>([PEP 703 - Making the Global Interpreter Lock Optional in CPython][26]).

Sources:
* [What Is the Python Global Interpreter Lock (GIL)?](https://realpython.com/python-gil/)
* [Getting to Know the Python Standard REPL](https://www.youtube.com/watch?v=pvxZMfrOxNQ)
* [Python moves to remove the GIL and boost concurrency](https://www.infoworld.com/article/3704248/python-moves-to-remove-the-gil-and-boost-concurrency.html)
* [Is Python's GIL the software world's biggest blunder?](https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/Is-Pythons-GIL-the-software-worlds-biggest-blunder)












-----



# Setting up Web Workflow for CircuitPython
[Workflows](https://docs.circuitpython.org/en/latest/docs/workflows.html) are the process used to
(1) manipulate files on the CircuitPython device and
(2) interact with the serial connection to CircuitPython.
CircuitPython supports workflows for USB, BLE, and Web connectivity.

Web workflow is enabled when a file named `settings.toml` is added to the
root folder of the CircuitPython file system.
This file contains local WiFi info and other settings.

* [Setting up Web Workflow](https://learn.adafruit.com/circuitpython-with-esp32-quick-start/setting-up-web-workflow)
* [MicroPython — OTA Updates and GitHub, a match made in heaven](https://medium.com/@ronald.dehuysser/micropython-ota-updates-and-github-a-match-made-in-heaven-45fde670d4eb)
    * [How to add Over-the-Air updates to your MicroPython projects](https://www.youtube.com/watch?v=f1widOJYQDc)
* [micropython-ota: Micropython library for upgrading code over-the-air (OTA)](https://pypi.org/project/micropython-ota/)
* [ESP32 MicroPython Tutorial with Raspberry Pi](https://www.youtube.com/watch?v=w15-EQASP_Y)
* [ESP32 / ESP8266 MicroPython: Running scripts from a computer](https://techtutorialsx.com/2017/06/03/esp32-esp8266-micropython-running-scripts-from-a-computer/)

#### Step X: CircuitPython Supported Bootloads
A bootloader is an application whose primary purpose is to allow the systems software
that has to be updated without using any specialized hardware such as a JTAG programmer.
The bootloader (1) manages the system's establishment of the new system image,
(2) receives new program information externally via some communication means
and writes that information to the program memory of the processor.

USB Flashing Format (UF2) Bootloader
Adafruit SAMD21 (M0) and SAMD51 (M4) boards feature an improved bootloader that makes it easier than ever to flash different code onto the microcontroller.
Instead of needing drivers or a separate program for flashing (e.g. `esptool.py`, `avrdude`), one can simply drag a file onto a removable drive.
The [format of the file](https://github.com/Microsoft/uf2) extra information to help the bootloader know where the data goes.

Direct Firmware Update (DFU) Bootloader
STM Bootloader

Sources:
* [Non-UF2 Installation](https://learn.adafruit.com/welcome-to-circuitpython/non-uf2-installation)
* [Installing CircuitPython on ESP32](https://learn.adafruit.com/circuitpython-with-esp32-quick-start/installing-circuitpython)
* [UF2 Bootloader Details](https://learn.adafruit.com/adafruit-feather-m0-express-designed-for-circuit-python-circuitpython/uf2-bootloader-details)

#### Step X: CircuitPython's Recommended Editors
For CircutiPython, we should consider adding additional tool,
the [Mu Editor][33] and/or [Thonny IDE][27].

##### Install Mu
Mu is a very simple editor create specifically for beginner Python programmers.

```bash
# download the AppImage
cd ~/Downloads
mkdir mu-editor
cd mu-editor
wget https://github.com/mu-editor/mu/releases/download/v1.2.0/MuEditor-Linux-1.2.0-x86_64.tar

# make sure you have the right permmisions ... you in the dialout group
$ groups jeff
jeff : jeff adm dialout cdrom sudo dip plugdev lpadmin lxd sambashare vboxusers

# untar the AppImage
tar -xf MuEditor-Linux-1.2.0-x86_64.tar

# install dependencies
sudo apt install libfuse2

# move the mu-editor executable to you bin and create symbolic links to it
cp Mu_Editor-1.2.0-x86_64.AppImage ~/bin
ln --symbolic ~/bin/Mu_Editor-1.2.0-x86_64.AppImage ~/bin/mu-editor
ln --symbolic ~/bin/Mu_Editor-1.2.0-x86_64.AppImage ~/bin/mu

# what version of mu-editor is loaded
# see mu-editor title bar
1.2.0
```

Now explore how to use Mu by following the following video:
* [CircuitPython Tutorial](https://www.youtube.com/watch?v=opes_7Uf49U)

##### Install Thonny
Thonny is a more porwerful than Mu in that its an IDE.

```bash
#install thonny
pip3 install thonny

# identify where thonny was installed
$ whereis thonny
thonny: /home/jeff/.local/bin/thonny

# what version of thonny is loaded
# see main menu > Help > About Thonny
4.1.4
```

Now explore how to use Thonny by following the following video:
* [Programming an ESP32 NodeMCU with MicroPython: Setup with Thonny](https://www.youtube.com/watch?v=BzAo48cFhS8)
* [Getting Started with Raspberry Pi Pico W and CircuitPython](https://www.youtube.com/watch?v=56N_8FI_WLU)

```bash
# erease the entire flash on the esp32
esptool.py --chip esp32 --port /dev/ttyUSB0 erase_flash

# flash the firmware starting at address 0x0 (different for micropython)
esptool.py --chip esp32 --port /dev/ttyUSB0 --baud 460800 write_flash -z 0x0 ~/Downloads/circuitpython/adafruit-circuitpython-doit_esp32_devkit_v1-en_US-8.2.9.bin
```

If it becomes necessary to uninstall Thonny,
use the following procedure:

```bash
# uninstall thonny
pip3 unisntall thonny
```

Sources:
* [Recommended Editor](https://learn.adafruit.com/welcome-to-circuitpython/recommended-editors)
* [How to Install and Use Thonny Python IDE on Linux](https://www.tecmint.com/thonny-python-ide/)
* [Programming an ESP32 NodeMCU with MicroPython: Setup with Thonny](https://www.youtube.com/watch?v=BzAo48cFhS8)
* [How to install Mu on Linux](https://codewith.mu/en/howto/1.2/install_linux)

#### Step X: CircuitPython's Use of Serial Console

Sources:
* [Connecting to the Serial Console](https://learn.adafruit.com/welcome-to-circuitpython/kattni-connecting-to-the-serial-console)

#### Step X: CircuitPython's Use of CIRCUITPY Drive
CIRCUITPY Drive - https://learn.adafruit.com/welcome-to-circuitpython/the-circuitpy-drive
It is important to remember that the ESP32 lacks native USB support and therefore no CIRCUITPY folder will show up. Loading CircuitPython firmware and getting wifi setup is done over a serial connection instead of a folder.
Because of this, the process for getting things setup on the ESP32 is different and more involved than other boards. So we're giving it some special attention.

For boards lacking native USB, like the ESP32 and ESP32-C3, no folder will show up after pressing reset. If CircuitPython firmware was loaded, the REPL can be accessed over a serial COM port.

For other boards, like ESP32-S2, -S3, etc., a BOOT folder should show up. A CircuitPython UF2 file can now be copied over to the BOOT folder, after which the CIRCUITPY folder should then show up.

## Step X: Setting up Web Workflow for CircuitPython
[Workflows](https://docs.circuitpython.org/en/latest/docs/workflows.html) are the process used to
(1) manipulate files on the CircuitPython device and
(2) interact with the serial connection to CircuitPython.
CircuitPython supports workflows for USB, BLE, and Web connectivity.

Web workflow is enabled when a file named `settings.toml` is added to the
root folder of the CircuitPython file system.
This file contains local WiFi info and other settings.

* [Setting up Web Workflow](https://learn.adafruit.com/circuitpython-with-esp32-quick-start/setting-up-web-workflow)

#### Step X: CircuitPython Supported Bootloads
A bootloader is an application whose primary purpose is to allow the systems software
that has to be updated without using any specialized hardware such as a JTAG programmer.
The bootloader (1) manages the system's establishment of the new system image,
(2) receives new program information externally via some communication means
and writes that information to the program memory of the processor.

USB Flashing Format (UF2) Bootloader
Adafruit SAMD21 (M0) and SAMD51 (M4) boards feature an improved bootloader that makes it easier than ever to flash different code onto the microcontroller.
Instead of needing drivers or a separate program for flashing (e.g. `esptool.py`, `avrdude`), one can simply drag a file onto a removable drive.
The [format of the file](https://github.com/Microsoft/uf2) extra information to help the bootloader know where the data goes.

Direct Firmware Update (DFU) Bootloader
STM Bootloader

Sources:
* [Non-UF2 Installation](https://learn.adafruit.com/welcome-to-circuitpython/non-uf2-installation)
* [Installing CircuitPython on ESP32](https://learn.adafruit.com/circuitpython-with-esp32-quick-start/installing-circuitpython)
* [UF2 Bootloader Details](https://learn.adafruit.com/adafruit-feather-m0-express-designed-for-circuit-python-circuitpython/uf2-bootloader-details)

#### Step X: CircuitPython's Recommended Editors
For CircutiPython, we should consider adding additional tool,
the [Mu Editor][33] and/or [Thonny IDE][27].

##### Install Mu
Mu is a vey simple editor create specifically for beginner Python programmers.

```bash
# download the AppImage
cd ~/Downloads
mkdir mu-editor
cd mu-editor
wget https://github.com/mu-editor/mu/releases/download/v1.2.0/MuEditor-Linux-1.2.0-x86_64.tar

# make sure you have the right permmisions ... you in the dialout group
$ groups jeff
jeff : jeff adm dialout cdrom sudo dip plugdev lpadmin lxd sambashare vboxusers

# untar the AppImage
tar -xf MuEditor-Linux-1.2.0-x86_64.tar

# install dependencies
sudo apt install libfuse2

# move the mu-editor executable to you bin and create symbolic links to it
cp Mu_Editor-1.2.0-x86_64.AppImage ~/bin
ln --symbolic ~/bin/Mu_Editor-1.2.0-x86_64.AppImage ~/bin/mu-editor
ln --symbolic ~/bin/Mu_Editor-1.2.0-x86_64.AppImage ~/bin/mu

# what version of mu-editor is loaded
# see mu-editor title bar
1.2.0
```

Now explore how to use Mu by following the following video:
* [CircuitPython Tutorial](https://www.youtube.com/watch?v=opes_7Uf49U)

##### Install Thonny
Thonny is a more porwerful than Mu in that its an IDE.

```bash
#install thonny
pip3 install thonny

# identify where thonny was installed
$ whereis thonny
thonny: /home/jeff/.local/bin/thonny

# what version of thonny is loaded
# see main menu > Help > About Thonny
4.1.4
```

Now explore how to use Thonny by following the following video:
* [Programming an ESP32 NodeMCU with MicroPython: Setup with Thonny](https://www.youtube.com/watch?v=BzAo48cFhS8)
* [Getting Started with Raspberry Pi Pico W and CircuitPython](https://www.youtube.com/watch?v=56N_8FI_WLU)

```bash
# erease the entire flash on the esp32
esptool.py --chip esp32 --port /dev/ttyUSB0 erase_flash

# flash the firmware starting at address 0x0 (different for micropython)
esptool.py --chip esp32 --port /dev/ttyUSB0 --baud 460800 write_flash -z 0x0 ~/Downloads/circuitpython/adafruit-circuitpython-doit_esp32_devkit_v1-en_US-8.2.9.bin
```

If it becomes necessary to uninstall Thonny,
use the following procedure:

```bash
# uninstall thonny
pip3 unisntall thonny
```

Sources:
* [Recommended Editor](https://learn.adafruit.com/welcome-to-circuitpython/recommended-editors)
* [How to Install and Use Thonny Python IDE on Linux](https://www.tecmint.com/thonny-python-ide/)
* [Programming an ESP32 NodeMCU with MicroPython: Setup with Thonny](https://www.youtube.com/watch?v=BzAo48cFhS8)
* [How to install Mu on Linux](https://codewith.mu/en/howto/1.2/install_linux)

#### Step X: CircuitPython's Use of Serial Console

Sources:
* [Connecting to the Serial Console](https://learn.adafruit.com/welcome-to-circuitpython/kattni-connecting-to-the-serial-console)

#### Step X: CircuitPython's Use of CIRCUITPY Drive
CIRCUITPY Drive - https://learn.adafruit.com/welcome-to-circuitpython/the-circuitpy-drive
It is important to remember that the ESP32 lacks native USB support and therefore no CIRCUITPY folder will show up. Loading CircuitPython firmware and getting wifi setup is done over a serial connection instead of a folder.
Because of this, the process for getting things setup on the ESP32 is different and more involved than other boards. So we're giving it some special attention.

For boards lacking native USB, like the ESP32 and ESP32-C3, no folder will show up after pressing reset. If CircuitPython firmware was loaded, the REPL can be accessed over a serial COM port.

For other boards, like ESP32-S2, -S3, etc., a BOOT folder should show up. A CircuitPython UF2 file can now be copied over to the BOOT folder, after which the CIRCUITPY folder should then show up.





-----



# Test Drive of MicroPython
[MicroPython][01] claims to be a lean and efficient implementation of the Python 3.
Its compact enough to fit and run within just 256k of code space and 16k of RAM.
MicroPython standard library includes a small subset of the Python standard library
plus additions for the embedded world,
and is optimized to run on microcontrollers and other constrained environments.
MicroPython's [pyboard][03] is just one example.
It give you the experince like a Python Operating System
(see this [video][23] for how this feels).
Many other type of MCUs are support, ash shown [here](https://micropython.org/download/).

MicroPython aims to be as compatible with normal Python, as much as possible,
and move code easily from the desktop to a microcontroller or embedded system.
A typical microcontroller programming session involves at least 5 steps:

1. **Write** your code, typically in some form of C/C++ using an IDE (Arduino etc.)
2. **Compile** your code for the specific microcontroller architecture
(with a specific tool-chain for a given architectures — AVR, Xtensa, ARM, etc.)
3. **Flash** you move binary, executable code to the board with some USB-to-serial adapter.
4. **Debug** you your code with an IDE and a lot of serial log/print statements.
5. **Repeat**by going back to step 1.

With MicroPython, the expectation is to strike out 2.5 of the 5.
The extra 0.5 from taking advantage of the large set of library.

To use MicroPython on any given MCU,
you'll need to download and install the the coresponding firmware for that MCU.
I'm going to focus on the ESP32.
There is a multitude of modules and boards from different sources which carry the ESP32 chip.
I'm going to focus on the ESP32 board, specifically the ESP-32S (aka ESP-WROOM-32).
MicroPython tries to provide a generic port which would run on as many boards/modules as possible,
but there may be limitations.

So MicroPython could make a generic ESP32 port and support as many boards as possible,
the following design and implementation decision were made:

* GPIO pin numbering is based on ESP32 chip numbering.
Have the manual/pin diagram of your board at hand to find correspondence between your board pins and actual ESP32 pins.
* All pins are supported by MicroPython but not all are usable on any given board.
For example pins that are connected to external SPI flash should not be used,
and a board may only expose a certain selection of pins.

## MicroPython Firmware Installation

#### Step 1: Download MicroPython Firmware - DONE
Flashing of firnware will vary from MCU board to MCU board.
For any given ESP board, there is only one firmware package to download
but there are many types to choose from.
MicroPython firmware source code is available on [Github][17],
so we could built the firmware from source,
but it is best to use the pre-built binary which you can
[download via MicroPython website (specifically for the ESP-WROOM-32)][18].

>**NOTE:** there is firmware for boards with and without external SPIRAM.
>Non-SPIRAM firmware will work on any board,
>whereas SPIRAM enabled firmware will only work on boards with 4MiB of external pSRAM.
>In my case, I'm using the standard & non-spiram firmware.
>Also other options are available, like OTA support, so choose wisely to conserve memory.

Here is what I did with **MicoPython**:

```bash
# make a directory for store firmware bin files
mkdir ~/Downloads/micropython
cd ~/Downloads/micropython

# micropython - get the esp32 firmware you wish to use, multiple possibilities listed here
wget https://micropython.org/resources/firmware/ESP32_GENERIC-20231005-v1.21.0.bin        # for HiLetgo ESP-WROOM32 - https://micropython.org/download/ESP32_GENERIC/
```

#### Step 2: Install Your MicroPython Flashing Tool - DONE
The binary files just downloaded need to be flashed to the ESP32.
Firmware flashing on the ESP32 (and for ESP8266) board is done using the [`esptool.py` program][20].

In my case, I choose to use my version of `esptool.py`
that I have been doing for all my C++ coding for the ESP processors found here:
`~/.arduino15/packages/esp32/tools/esptool_py/4.5.1/esptool.py`.
It wasn't necessary to use this version but just a convenience.

#### Step 3: Install Utility to Manipulate Files via USB - DONE
The MicroPython tool [`ampy`][08] is a simple command line tool to manipulate files
and run code on a MicroPython (or CircuitPython) board over its serial connection.
With `ampy` you can send files from your computer to the board's file system,
download files from a board to your computer,
and send a Python script to a board to be executed.

You can use `ampy` with either Python 2.7.x or 3.x:

```bash
# install ampy under python 3.x
pip3 install adafruit-ampy
```

Now lets see what `ampy` can do for us

```bash
# list ampy help
$ ampy --help
Usage: ampy [OPTIONS] COMMAND [ARGS]...

  ampy - Adafruit MicroPython Tool

  Ampy is a tool to control MicroPython boards over a serial connection.
  Using ampy you can manipulate files on the board's internal filesystem and
  even run scripts.

Options:
  -p, --port PORT    Name of serial port for connected board.  Can optionally
                     specify with AMPY_PORT environment variable.  [required]
  -b, --baud BAUD    Baud rate for the serial connection (default 115200).
                     Can optionally specify with AMPY_BAUD environment
                     variable.
  -d, --delay DELAY  Delay in seconds before entering RAW MODE (default 0).
                     Can optionally specify with AMPY_DELAY environment
                     variable.
  --version          Show the version and exit.
  --help             Show this message and exit.

Commands:
  get    Retrieve a file from the board.
  ls     List contents of a directory on the board.
  mkdir  Create a directory on the board.
  put    Put a file or folder and its contents on the board.
  reset  Perform soft reset/reboot of the board.
  rm     Remove a file from the board.
  rmdir  Forcefully remove a folder and all its children from the board.
  run    Run a script and print its output.
```

Each subcommand has its own help, for example to see help for the `ls` command run:

```bash
# help for ampy subcommand ls (NOTE: device must be pluggedinto usb)
$ ampy --port /dev/ttyUSB0 ls --help
Usage: ampy ls [OPTIONS] [DIRECTORY]

  List contents of a directory on the board.

  Can pass an optional argument which is the path to the directory.  The
  default is to list the contents of the root, /, path.

  For example to list the contents of the root run:

    ampy --port /board/serial/port ls

  Or to list the contents of the /foo/bar directory on the board run:

    ampy --port /board/serial/port ls /foo/bar

  Add the -l or --long_format flag to print the size of files (however note
  MicroPython does not calculate the size of folders and will show 0 bytes):

    ampy --port /board/serial/port ls -l /foo/bar

Options:
  -l, --long_format  Print long format info including size of files.  Note the
                     size of directories is not supported and will show 0
                     values.
  -r, --recursive    recursively list all files and (empty) directories.
  --help             Show this message and exit.
```

>**Note:** `ampy` by design is meant to be simple and does not support advanced interaction.
>If you want to use `shell` or a terminal to send input to a board,
>check out MicroPython tools like [`rshell`][19] or [`mpfshell`][24] for more advanced interaction with boards.

Sources:
* [Running code with ampy](https://learn.adafruit.com/sino-bit-micropython/running-code-with-ampy)

#### Step 4: Flash MicroPython Firmware to ESP32 - DONE
Now connect your Linux box with your ESP32.
For most ESP32 boards, the ESP32 board will be give device `/dev/ttyUSB0`.
You program your esp32 board using the [`esptool.py` program][20].
If you are putting MicroPython on your board for the first time,
then you should first erase the entire flash using the `esptool.py`:

```bash
# check type of board, flash size, etc.
$ esptool.py --port /dev/ttyUSB0 flash_id
esptool.py v4.5.1
Serial port /dev/ttyUSB0
Connecting.....
Detecting chip type... Unsupported detection protocol, switching and trying again...
Connecting.....
Detecting chip type... ESP32
Chip is ESP32-D0WDQ6 (revision v1.0)
Features: WiFi, BT, Dual Core, 240MHz, VRef calibration in efuse, Coding Scheme None
Crystal is 40MHz
MAC: 3c:71:bf:84:aa:f8
Uploading stub...
Running stub...
Stub running...
Manufacturer: ef
Device: 4016
Detected flash size: 4MB
Hard resetting via RTS pin...

# erease the entire flash on the esp32
esptool.py --chip esp32 --port /dev/ttyUSB0 erase_flash

# flash the firmware starting at address 0x1000 (different for circuitpython)
esptool.py --chip esp32 --port /dev/ttyUSB0 --baud 460800 write_flash -z 0x1000 ~/Downloads/micropython/ESP32_GENERIC-20231005-v1.21.0.bin
```

If these two step are successful, the output should be similar to below:

```bash
# erease the entire flash
$ esptool.py --chip esp32 --port /dev/ttyUSB0 erase_flash
esptool.py v4.5.1
Serial port /dev/ttyUSB0
Connecting............
Chip is ESP32-D0WDQ6 (revision v1.0)
Features: WiFi, BT, Dual Core, 240MHz, VRef calibration in efuse, Coding Scheme None
Crystal is 40MHz
MAC: 3c:71:bf:84:aa:f8
Uploading stub...
Running stub...
Stub running...
Erasing flash (this may take a while)...
Chip erase completed successfully in 6.0s
Hard resetting via RTS pin...

# flash the firmware starting at address 0x1000
$ esptool.py --chip esp32 --port /dev/ttyUSB0 --baud 460800 write_flash -z 0x1000 ~/Downloads/micropython/esp32-20210418-v1.15.bin
esptool.py v4.5.1
Serial port /dev/ttyUSB0
Connecting....
Chip is ESP32-D0WDQ6 (revision v1.0)
Features: WiFi, BT, Dual Core, 240MHz, VRef calibration in efuse, Coding Scheme None
Crystal is 40MHz
MAC: 3c:71:bf:84:aa:f8
Uploading stub...
Running stub...
Stub running...
Changing baud rate to 460800
Changed.
Configuring flash size...
Flash will be erased from 0x00001000 to 0x00196fff...
Compressed 1661872 bytes to 1104578...
Wrote 1661872 bytes (1104578 compressed) at 0x00001000 in 25.2 seconds (effective 526.9 kbit/s)...
Hash of data verified.

Leaving...
Hard resetting via RTS pin...
```

## Validation of the CircuitPython Installs

#### Step 1: Validate MicroPython Firmware is Working - DONE
Once you have the firmware installed,
you can access the REPL (aka Python prompt) over the ESP32 USB connection
(or over UART0 depending on your board) via a serial terminal.
The USB serial connection **default baudrate is 115200**.

Now make a terminal connection to the the ESP32 and use the `help()`
command to validate the firmware is working:

```bash
# serial terminal into the esp32
screen /dev/ttyUSB0 115200,cs8cls

# test out the python REPL
>>> help()
Welcome to MicroPython on the ESP32!

For online docs please visit http://docs.micropython.org/

For access to the hardware use the 'machine' module:

import machine
pin12 = machine.Pin(12, machine.Pin.OUT)
pin12.value(1)
pin13 = machine.Pin(13, machine.Pin.IN, machine.Pin.PULL_UP)
print(pin13.value())
i2c = machine.I2C(scl=machine.Pin(21), sda=machine.Pin(22))
i2c.scan()
i2c.writeto(addr, b'1234')
i2c.readfrom(addr, 4)

Basic WiFi configuration:

import network
sta_if = network.WLAN(network.STA_IF); sta_if.active(True)
sta_if.scan()                             # Scan for available access points
sta_if.connect("<AP_name>", "<password>") # Connect to an AP
sta_if.isconnected()                      # Check for successful connection

Control commands:
  CTRL-A        -- on a blank line, enter raw REPL mode
  CTRL-B        -- on a blank line, enter normal REPL mode
  CTRL-C        -- interrupt a running program
  CTRL-D        -- on a blank line, do a soft reset of the board
  CTRL-E        -- on a blank line, enter paste mode

For further help on a specific object, type help(obj)
For a list of available modules, type help('modules')
>>>

# list of available modules
>>> help('modules')
__main__          bluetooth         heapq             select
_asyncio          btree             inisetup          socket
_boot             builtins          io                ssl
_espnow           cmath             json              struct
_onewire          collections       machine           sys
_thread           cryptolib         math              time
_webrepl          deflate           micropython       uasyncio
aioespnow         dht               mip/__init__      uctypes
apa106            ds18x20           neopixel          umqtt/robust
array             errno             network           umqtt/simple
asyncio/__init__  esp               ntptime           upysh
asyncio/core      esp32             onewire           urequests
asyncio/event     espnow            os                webrepl
asyncio/funcs     flashbdev         platform          webrepl_setup
asyncio/lock      framebuf          random            websocket
asyncio/stream    gc                re
binascii          hashlib           requests/__init__
Plus any modules on the filesystem
>>>
```

#### Step 2: Validate MicroPython REPL Operation - DONE
After termination the above `screen` session (since we need the `/dev/ttyUSB0` device),
perfrm these operations:

```bash
# list the files on the esp32 recursively and in long format
$ ampy --port /dev/ttyUSB0 ls -r -l
/boot.py - 139 bytes

# lets load a junk file
ls > junk
ampy --port /dev/ttyUSB0 put junk

# now view what files we got
$ ampy --port /dev/ttyUSB0 ls -l
/boot.py - 139 bytes
/junk - 3213 bytes
```

Below is a useful function for connecting the ESP32 to your local WiFi network.
Using `screen /dev/ttyUSB0 115200,cs8cls` again,
type the Python script below into the REPL prompt:

```python
""" CircuitPython WiFi Startup Script: Scan for WiFi networks, prompt the user
    for SSID & password, initiate a WiFi connection to the device, and then
    do a ping test to google.com for validate you have a connection.

    Source: https://gist.github.com/todbot/7534740779cd64a2ce636d14ecb6e5af
            https://learn.adafruit.com/iot-led-sign/circuitpython-internet-test """

import wifi
import ipaddress

# scanning for wifi networks
print('\n\nScanning for available WiFi networks...')
print('{:^24s}{:^5s}{:^10s}{:^55s}'.format('SSID', 'RSSI', 'Channels', 'Autentication Mode'))
for ap in wifi.radio.start_scanning_networks():
    print('{:<24s}{:<5d}{:^10d}{:^55s}'.format(ap.ssid, ap.rssi, ap.channel, str(ap.authmode)))
wifi.radio.stop_scanning_networks()

# request wifi network you wish to join
ssid = input('\nWhat is your WiFi SSID: ')
password = input('What is your WiFi password: ')

# join your requested network
print("\nAttempting to join requested network...")
wifi.radio.connect(ssid, password)
print("IP address: ", wifi.radio.ipv4_address)

# check if you are connected by doing a ping
print('\nPerforming ping test...')
ping_ip = ipaddress.IPv4Address("8.8.8.8")
ping = wifi.radio.ping(ip = ping_ip)

# retry ping once more if it timed out
if ping is None:
    ping = wifi.radio.ping(ip = ping_ip)

if ping is None:
    print("Couldn't ping 'google.com' successfully")
else:
    # convert seconds to milliseconds
    print(f"Pinging 'google.com' took: {ping * 1000} ms")
```

You could also copy the above program into a file (`code.py`)
and upload it to the ESP32:

```bash
# contents of file system (assume you rebooted the ESP32)
$ ampy --port /dev/ttyUSB0 ls -l
/boot.py - 139 bytes

# upload file code.py
ampy --port /dev/ttyUSB0 put code.py

# upload but do not execute file code.py
ampy --port /dev/ttyUSB0 run --no-output code.py

# contents of file system after upload
$ ampy --port /dev/ttyUSB0 ls -l
/.Trashes - 0 bytes
/.fseventsd - 0 bytes
/.metadata_never_index - 0 bytes
/boot_out.txt - 121 bytes
/code.py - 1570 bytes
/lib - 0 bytes
/settings.toml - 0 bytes

# serial terminal into the esp32
screen /dev/ttyUSB0 115200,cs8cls

# execute the upload at the REPL prompt
do_connect()
```

Once the network is established,
the socket module can be used to create a TCP/UDP sockets
and the requests module for th HTTP requests.



-----



# Test Drive of CircuitPython
Adafruit has embraced MicroPython, extended it, and calls their version [CircuitPython][04].
So CircuitPython is a derivative of MicroPython,
but Adafruit's objective is to simplify things for the novice user,
so they changes a few things to make the language easier to learn and use.
Adafruit has also created its own MicroPython/CircuitPython compatible hardware.
The video's below help explain the differences
and Adafruit's [documentation][06] go into the details.

A nice feature of CircuitPython is its compatability with Linux.
AdaFruit provides a special library called [Adafruit-Blinka][31]
that supplies CircuitPython APIs for non-CircuitPython versions of Python, such as CPython, on Linux and MicroPython.
Adafruit-Blinka provide the layer that translates the CircuitPython hardware API
to whatever relivent library the Linux board provides, such as the Raspberry Pi Python [RPi.GPIO library][32].
The upshot is that any code we have for CircuitPython will be instantly
and easily runnable on Linux computers like Raspberry Pi, Ubuntu, etc.

Maybe the single most important difference might be
CircuitPython's support of SAMD microcontroller chip's on their boards.
This chip give you native USB connectivity,
so a serial connection to the board will give you access to a filesystem
with all the Python code on the chip.
This code is preserved between reboots,
eliminating accidental loss of your code while developing.

For many boards, when CircuitPython finishes installing,
or you plug a CircuitPython board into your computer with CircuitPython already installed,
the board shows up on your computer as a USB drive called `CIRCUITPY`.
This will happen with boards that natively support USB.
The `CIRCUITPY` drive is where your code and the necessary libraries and files will live
and you can treat it much like any USB drive.

But some boards, specifically the ones that don't support native USB,
cannot present a `CIRCUITPY` drive.
This includes boards using ESP32 or ESP32-C3 microcontrollers.
On these boards, there are alternative ways to transfer and edit files.
You can use the Thonny or Mu editor, or use the `ampy` tool.

Here's what you have to know about using CircuitPython **without native USB support**:

* No disk drive `CIRCUITPY` for drag-n-drop file moving, files must be moved via a special tool such as `ampy` that 'types' the file in for you via the REPL
* You only get a REPL connection! No HID keyboard/mouse or other USB interface

Sources:
* [CircuitPython vs MicroPython: Key Differences][05]
* [Time to Say Goodbye to Arduino and Go On to Micropython/ Adafruit Circuitpython?][07]
* [CircuitPython on ESP32 Quick Start](https://learn.adafruit.com/circuitpython-with-esp32-quick-start)
* [Drag And Drop Files On Select Arduino Boards ](https://hackaday.com/2019/05/29/drag-and-drop-files-on-select-arduino-boards/)
* [CircuitPython Libraries on Linux and Raspberry Pi](https://learn.adafruit.com/circuitpython-on-raspberrypi-linux/)
* [Experimenting with ESP32 & ESP8266 microcontrollers](https://medium.com/@makvoid/experimenting-with-esp32-esp8266-microcontrollers-1a6e27ef15ca)
* [The CIRCUITPY Drive](https://learn.adafruit.com/welcome-to-circuitpython/the-circuitpy-drive)

## CircuitPython Firmware Installation

#### Step 1: Download CircuitPython Firmware - DONE
The first thing you'll want to do is download the most recent version of CircuitPython.
Some boards from AdaFruit and others com pre-installed with CircuitPython,
so make sure you're running the latest version!
If you have code on the device, make sure to back it up before the install.

For any given ESP board, there is only one firmware package to download
but there are many types to choose from.
To find your firmware, go to CircuitPython's [Downloads page][21],
and select from the many boards listed there.
My board is the [DOIT ESP32 Development Board][30]
(which I belive is equivalent to the ESP-WROOM-32 I used in the MicroPhython section).

Here is what I did:

```bash
# make a directory for store firmware bin files
mkdir ~/Downloads/circuitpython
cd ~/Downloads/circuitpython

# find all the circuitpython libaries at https://circuitpython.org/downloads
# micropython - get the esp32 firmware you wish to use, multiple possibilities listed here
wget https://downloads.circuitpython.org/bin/doit_esp32_devkit_v1/en_US/adafruit-circuitpython-doit_esp32_devkit_v1-en_US-8.2.9.bin            # for DOIT ESP32 Development Board - https://circuitpython.org/board/doit_esp32_devkit_v1/
wget https://downloads.circuitpython.org/bin/seeed_xiao_esp32c3/en_US/adafruit-circuitpython-seeed_xiao_esp32c3-en_US-8.2.9.bin                # for Seeed Studio XIAO ESP32C3 - https://circuitpython.org/board/seeed_xiao_esp32c3/
wget https://downloads.circuitpython.org/bin/unexpectedmaker_tinys2/en_US/adafruit-circuitpython-unexpectedmaker_tinys2-en_US-8.2.9.bin        # for Unexpected Maker TinyS2 - https://circuitpython.org/board/unexpectedmaker_tinys2/
wget https://downloads.circuitpython.org/bin/unexpectedmaker_feathers3/en_US/adafruit-circuitpython-unexpectedmaker_feathers3-en_US-8.2.9.bin  # for Unexpected Maker FeatherS3 - https://circuitpython.org/board/unexpectedmaker_feathers3/
wget https://downloads.circuitpython.org/bin/adafruit_kb2040/en_US/adafruit-circuitpython-adafruit_kb2040-en_US-8.2.9.uf2                      # for Adafruit KB2040 - https://circuitpython.org/board/adafruit_kb2040/
wget https://downloads.circuitpython.org/bin/adafruit_kb2040/en_US/adafruit-circuitpython-qtpy_m0-en_US-8.2.9.uf2                              # for Adafruit QT PY - https://circuitpython.org/board/qtpy_m0/
```

I'm particularly interested in exploring the CircuitPython MCPs
[Adafruit KB2040][38], [Unexpected Maker FeatherS3][39], [Unexpected Maker TinyS2][40], and [Seeed Studio XIAO ESP32C3][42].
All have builtin audio modules that I hope to use in an audio project
(Adafruit KB2040 has `audiobusio`, `audiocore`, `audiomixer`, `audiomp3`, `audiopwmio`,
and Unexpected Maker FeatherS3 & Unexpected Maker TinyS2 have `audiobusio`, `audiocore`, `audiomixer`,
and Seeed Studio XIAO ESP32C3 having only `audiocore`, `audiomixer`).
My project also requires WiFi, and unfortunately, the most "audio-capable" MCP (Adafruit KB2040) doesn't have it.
The [Adafruit QT PY][44] is a "just for fun" tiny board.

Sources:
* [Installing CircuitPython](https://learn.adafruit.com/welcome-to-circuitpython/installing-circuitpython)

#### Step 2: Install Your CircuitPython Flashing Tool - DONE
The binary files just downloaded need to be flashed to the ESP32 or RP2040.
For the ESP32, this is done using the same tool as MicroPython, and document above,
the [`esptool.py` program][20].

In my case, I choose to load the latest version of `esptool.py`
into a [Miniconda environment][41] to be specifically used for CircuitPython work.
So first, I create a special environment for my CircuitPython coding:

```bash
# create an environment using conda
#    a single ‘=’ we tell conda to use the latest version in the Python 3 release tree, at the moment this is version 3.11.5
#    if you would like to use a specific version, use tow equal signs like '=='
conda create --name circuitpython python=3.11.5
```

Next, we acivate the Miniconda environment and install `esptool.py`:

```bash
# activate the new environment
conda activate circuitpython

# install the latest version of esptool.py
pip install esptool
```

>**NOTE:** The options used on the `esptool.py` commandline is different for CircuitPython.
>You flash the firmware starting at a different memory address.

#### Step 3: Install Utility to Manipulate Files via USB - DONE
For the ESP-WROOM-32, unlike other CircuitPython boards,
an extra drive called `CIRCUITPY` won’t appear attached to your device where you can easily drag and drop files.
For this feature to work, the MCU must have native USB connectivity,
something the ESP-WROOM-32 does not have.

Here again, we'll use the same tool used for MicroPython.
The MicroPython tool [`ampy`][08] is a simple command line tool to manipulate files
and run code on a MicroPython (or CircuitPython) board over its serial connection.
With `ampy` you can send files from your computer to the board's file system,
download files from a board to your computer,
and send a Python script to a board to be executed.
I'll install `adafruit-ampy` into the CircuitPython Conda environment:

```bash
# install ampy under python 3.x
pip install adafruit-ampy
```

#### Step 4: Flash CircuitPython Firmware to DOIT ESP32 Development Board - DONE
Now connect your Linux box with your ESP32.
For most ESP32 boards, the ESP32 board will be give device `/dev/ttyUSB0`.
You program your esp32 board using the [`esptool.py` program][20].
If you are putting MicroPython on your board for the first time,
then you should first erase the entire flash using the `esptool.py`.

For the ESP-WROOM-32, the process goes like this:

```bash
# check type of board, flash size, etc.
esptool.py --port /dev/ttyUSB0 flash_id

# erease the entire flash on the esp32
esptool.py --chip esp32 --port /dev/ttyUSB0 erase_flash

# flash the firmware starting at address 0x0 (different for micropython)
esptool.py --chip esp32 --port /dev/ttyUSB0 --baud 460800 write_flash -z 0x0 ~/Downloads/circuitpython/adafruit-circuitpython-doit_esp32_devkit_v1-en_US-8.2.9.bin     # for DOIT ESP32 Development Board - https://circuitpython.org/board/doit_esp32_devkit_v1/
```

Using `screen /dev/ttyUSB0 115200,cs8cls`, check out if you get the REPL.
If the steps above are successful, the output should be similar to the listing above for MicroPython.

#### Step 5: Flash CircuitPython Firmware to XIAO ESP32C3 Boards - DONE
For the Seeed Studio XIAO ESP32C3 board, we do the following:

```bash
# check type of board, flash size, etc.
esptool.py --port /dev/ttyACM0 flash_id

# erease the entire flash on the esp32
esptool.py --chip esp32-C3 --port /dev/ttyACM0 erase_flash

# flash the firmware starting at address 0x0 (different for micropython)
esptool.py --chip esp32-C3 --port /dev/ttyACM0 --baud 460800 write_flash -z 0x0 ~/Downloads/circuitpython/adafruit-circuitpython-seeed_xiao_esp32c3-en_US-8.2.9.bin       # for Seeed Studio XIAO ESP32C3 - https://circuitpython.org/board/seeed_xiao_esp32c3/
```

Using `screen /dev/ttyACM0 115200,cs8cls`, check out if you get the REPL.

#### Step 6: Flash CircuitPython Firmware to Unexpected Maker Boards - DONE
For the Unexpected Maker boards TinyS2 and FeatherS3,
you need to first put the board into bootloader mode
(document in the section titled "[Install, Repair, or Update UF2 Bootloader][40]" and [here][43]).
You do this via this method:

1. Plug board into a USB port on your computer using a data/sync cable
2. Press and hold down the BOOT or 0 button
3. Press and release the RESET or RST button
4. Release the BOOT button.

Then do the following steps:

```bash
# check type of board, flash size, etc.
esptool.py --port /dev/ttyACM0 flash_id                                        # works for both boards

# erease the entire flash on the esp32
esptool.py --chip esp32-S2 --port /dev/ttyACM0 erase_flash                     # for Unexpected Maker TinyS2 - https://circuitpython.org/board/unexpectedmaker_tinys2/
esptool.py --chip esp32-S3 --port /dev/ttyACM0 erase_flash                     # for Unexpected Maker FeatherS3 - https://circuitpython.org/board/unexpectedmaker_feathers3/


# flash the firmware starting at address 0x0 (different for micropython)
esptool.py --chip esp32-S2 --port /dev/ttyACM0 --baud 460800 write_flash -z 0x0 ~/Downloads/circuitpython/adafruit-circuitpython-unexpectedmaker_tinys2-en_US-8.2.9.bin     # for Unexpected Maker TinyS2 - https://circuitpython.org/board/unexpectedmaker_tinys2/
esptool.py --chip esp32-S3 --port /dev/ttyACM0 --baud 460800 write_flash -z 0x0 ~/Downloads/circuitpython/adafruit-circuitpython-unexpectedmaker_feathers3-en_US-8.2.9.bin  # for Unexpected Maker FeatherS3 - https://circuitpython.org/board/unexpectedmaker_feathers3/
```

>**NOTE:** The TinyS2 and FeatherS3 are designed with a LiPo battery charging circuit.
>The two LEDs near the USB-C port are for red 5V power indicator and the orange LED is the battery charge status.
>I suspect the rapid blinking of the orange LED indicates the battery is not charging or dead.

#### Step 7: Flash CircuitPython Firmware to Adafruit KB2040 Board - DONE
Unlike the cases above, this time we are going to make full use of the USB that device provides drive
(procedure taken from [here][46]).
(**NOTE:** We could have done this for the above Unexpected Maker boards,
but because they had ESP32 chips, we could make use of the `esptool.py` instead.)

Here are the steps to follow:

1. Plug board into a USB port on your computer using a data/sync cable
2. Press and hold down the BOOT or BOOTSEL button
3. Press and release the RESET or RST button
4. Continue to hold the BOOT/BOOTSEL button until the `RPI-RP2` drive appear. Rselease the BOOT button.
5. Drag the `adafruit-circuitpython-adafruit_kb2040-en_US-8.2.9.uf2` file to the `RPI-RP2` drive.

The file will be upload, the board will reboot, and the `CIRCUTPY` drive will appear ready to go!
**NOTE:** You may need to power cycle the board to get it operating properly.

#### Step 8: Flash CircuitPython Firmware to Adafruit QT PY Board - DONE
Flashing the QT PY board is similar to the KB2040, but this board has only one button for reset (RST),
and as a result, the procedure is a little different (procedure taken from [here][45]):

1. Plug board into a USB port on your computer using a data/sync cable
2. Double-click the small RST (reset) button, and you will see the NeoPixel RGB LED turn green.
4. You will see a new disk drive appear called `QTPY_BOOT`.
5. Drag the `adafruit-circuitpython-qtpy_m0-en_US-8.2.9.uf2` file to the `QTPY_BOOT` drive.

The file will be upload, the board will reboot, and the `CIRCUTPY` drive will appear ready to go!
**NOTE:** You may need to power cycle the board to get it operating properly.

## Validation of the CircuitPython Installs

#### Step 1: Validate CircuitPython `ampy` Tool
Before you connect with device via the USB connection using a serial terminal,
lets checkout the device with `ampy`:

```bash
# list the files on the esp32 recursively and in long format
ampy --port /dev/ttyACM0 ls -r -
```

#### Step 2: Validate CircuitPython Firmware is Working - DONE
Once you have the firmware installed,
you can access the REPL (aka Python prompt) over USB connection, via a serial terminal.
The USB serial connection **default baudrate is 115200**.
You can use `screen /dev/ttyACM0 115200,cs8cls`.

```bash
# serial terminal into the esp32
screen /dev/ttyACM0 115200,cs8cls
```

```python
# test out the python REPL
help()

# list of available modules
help('modules')

# find out more about a specific module
help('modules.audiocore')
```

#### Step 3: Validate CircuitPython REPL Operation - DONE
Below is a useful function for getting the mapping
of CircuitPython pin names to board physical pins ([source of script][36]).
Using a text editor, copy the code block below into a file called `pin-mapping.py`:

```python
# SPDX-FileCopyrightText: 2020 anecdata for Adafruit Industries
# SPDX-FileCopyrightText: 2021 Neradoc for Adafruit Industries
# SPDX-FileCopyrightText: 2021-2023 Kattni Rembor for Adafruit Industries
# SPDX-FileCopyrightText: 2023 Dan Halbert for Adafruit Industries
#
# SPDX-License-Identifier: MIT

""" CircuitPython Pin Map Script: This script will list the mapping of physical
    board pins to what those pins can be called in a CircuitPython script. """

import microcontroller
import board
try:
    import cyw43  # raspberrypi
except ImportError:
    cyw43 = None

board_pins = []
for pin in dir(microcontroller.pin):
    if (isinstance(getattr(microcontroller.pin, pin), microcontroller.Pin) or
        (cyw43 and isinstance(getattr(microcontroller.pin, pin), cyw43.CywPin))):
        pins = []
        for alias in dir(board):
            if getattr(board, alias) is getattr(microcontroller.pin, pin):
                pins.append(f"board.{alias}")
        # Add the original GPIO name, in parentheses.
        if pins:
            # Only include pins that are in board.
            pins.append(f"({str(pin)})")
            board_pins.append(" ".join(pins))

for pins in sorted(board_pins):
    print(pins)
```

Below is another useful function.
It can be used for connecting a WiFi capable device to your local WiFi network.
Using a text editor, copy the code block into `.../CIRCUITPY/code.py`.

```python
```

You execute these script remotely via the following command in your Linux machine:

```bash
# list the  circuitpython pin names to physical pin numbers
ampy --port /dev/ttyACM0 run pin-mapping.py

# initiate a wifi connect between the circuitpython device and you wifi access point
ampy --port /dev/ttyACM0 run start-wifi.py
```

Now drag this file into the `CIRCUTPY` drive
or upload via `ampy --port /dev/ttyACM0 put code.py`.

Using the serial terminal `screen /dev/ttyACM0 115200,cs8cls`
inspect the execute on the device.













-------



# Using CircuitPython Libraries
In order to use some common libraries that are not included in CircuitPython firmware you installed,
libraries like `datetime`, `requests`,
you’ll have to download the library bundle provided by CircuitPython.
You can get these libraries at [CircuitPython Libraries website][34]
CircuitPython libraries are written in Python and
they provide additional functionality and support external devices,
beyond what is in CircuitPython itself.
These libraries should be stored on your `CIRCUITPY` drive in a folder called `lib`.

Before you download the libraries, check what version CircuitPython is on your board:

```python
# query circuitpython for its version
>>> help()
Welcome to Adafruit CircuitPython 8.2.9!

Visit circuitpython.org for more information.

To list built-in modules type `help("modules")`.
>>>
```

I'm going to download the relevant libraries to my desktop Linux drive.
I'll pick from this what I need for my project.
The libraries are supplied as `.mpy` files,
which are compiled versions of Python source code.
The pre-compiled `.mpy` files take up less space and will load faster.

To make use of these libraries,
copy the individual library files you need to the `lib` folder on your `CIRCUITPY` drive.
For more details, checkout [Adafruit documentation][35].

First, download the Adafruit officially supported libraries:

```bash
# download supported circuitpython libraries
cd ~/Downloads/circuitpython/libraries
wget https://github.com/adafruit/Adafruit_CircuitPython_Bundle/releases/download/20231220/adafruit-circuitpython-bundle-8.x-mpy-20231220.zip
unzip adafruit-circuitpython-bundle-8.x-mpy-20231220.zip
rm adafruit-circuitpython-bundle-8.x-mpy-20231220.zip
```

Next, we will  download the community libraries contributed to the CircuitPython project:

```bash
# download community circuitpython libraries
cd ~/Downloads/circuitpython/libraries
wget https://github.com/adafruit/CircuitPython_Community_Bundle/releases/download/20231219/circuitpython-community-bundle-8.x-mpy-20231219.zip
unzip circuitpython-community-bundle-8.x-mpy-20231219.zip
rm circuitpython-community-bundle-8.x-mpy-20231219.zip
```

Sources:
* [Welcome To CircuitPython](https://learn.adafruit.com/welcome-to-circuitpython/overview)
* [CircuitPython Essentials](https://learn.adafruit.com/circuitpython-essentials/circuitpython-essentials)
* [CircuitPython Libraries (code)][34]
* [CircuitPython Libraries (doc)][35]

#### Step X: What CircuitPython Modules are Support on my Board?
Not every CircuitPython module is available for every board due to size constraints or hardware limitations.
So how do you find out what modules are available for your board?
There are two options for this.
You can check the [support matrix][37], and search for your board by name.
Or, you can use the REPL.
Plug in your board, connect to the serial console and enter the REPL.
Example below:

```python
# start a terminal session with your board
screen /dev/ttyUSB0 115200,cs8cls

# execuse a module listing
>>> help("modules")
__future__        canio             mdns              struct
__main__          collections       memorymap         supervisor
_asyncio          countio           microcontroller   synthio
_pixelmap         digitalio         micropython       sys
adafruit_bus_device                 displayio         msgpack           terminalio
adafruit_bus_device.i2c_device      dualbank          neopixel_write    time
adafruit_bus_device.spi_device      errno             nvm               touchio
adafruit_pixelbuf espidf            onewireio         traceback
aesio             espnow            os                ulab
alarm             espulp            ps2io             ulab.numpy
analogbufio       fontio            pulseio           ulab.numpy.fft
analogio          framebufferio     pwmio             ulab.numpy.linalg
array             frequencyio       rainbowio         ulab.scipy
atexit            gc                random            ulab.scipy.linalg
audiobusio        getpass           re                ulab.scipy.optimize
audiocore         hashlib           rotaryio          ulab.scipy.signal
audiomixer        i2cperipheral     rtc               ulab.scipy.special
binascii          i2ctarget         sdcardio          ulab.utils
bitbangio         io                select            uselect
bitmaptools       ipaddress         sharpdisplay      vectorio
board             json              socketpool        watchdog
builtins          keypad            ssl               wifi
busio             math              storage           zlib
Plus any modules on the filesystem
>>>

# to find out more about a specific module
>>> help("modules.wifi")
object modules.wifi is of type str
  encode -- <function>
  find -- <function>
  rfind -- <function>
  index -- <function>
  rindex -- <function>
  join -- <function>
  split -- <function>
  splitlines -- <function>
  rsplit -- <function>
  startswith -- <function>
  endswith -- <function>
  strip -- <function>
  lstrip -- <function>
  rstrip -- <function>
  format -- <function>
  replace -- <function>
  count -- <function>
  partition -- <function>
  rpartition -- <function>
  center -- <function>
  lower -- <function>
  upper -- <function>
  isspace -- <function>
  isalpha -- <function>
  isdigit -- <function>
  isupper -- <function>
  islower -- <function>
>>>
```

Of course, you could also get this information via `ampy` like this:

```bash
# execuse a module listing
echo "help('modules')" > junk ; ampy --port /dev/ttyUSB0 run junk

# to find out more about a specific module
echo "help('modules.wifi')" > junk ; ampy --port /dev/ttyUSB0 run junk
```

Sources:
* [CircuitPython Pins and Modules](https://learn.adafruit.com/circuitpython-essentials/circuitpython-pins-and-modules#circuitpython-built-in-modules-3082671)

#### Step X: CircuitPython Pin to Board Pin Mapping
This section will cover how to access your board's pins using CircuitPython,
We need a way to determine all available CircuitPython pin names mapping to board-specific pins.
This could be done via writen documentation but CircuitPython can provide some help.

When using any of you microcontroller board pins, n your code you will include `import board`.
The `board` module is used to provide access to a series of board-specific objects, including pins.
To see what CircuitPython knows about your board, execute the following:

```python
# circuitpython pin naming
>>> import board
>>> dir(board)
['__class__', '__name__', 'D1', 'D12', 'D13', 'D14', 'D15', 'D16', 'D17', 'D18', 'D19', 'D2', 'D21', 'D22', 'D23', 'D25'
, 'D26', 'D27', 'D3', 'D32', 'D33', 'D34', 'D35', 'D4', 'D5', 'I2C', 'LED', 'MISO', 'MOSI', 'RX', 'RX0', 'RX2', 'SCK', '
SCL', 'SDA', 'SPI', 'TX', 'TX0', 'TX2', 'UART', 'VN', 'VP', 'board_id']

# board pin naming
>>> import microcontroller
>>> dir(microcontroller.pin)
['__class__', 'GPIO0', 'GPIO1', 'GPIO10', 'GPIO11', 'GPIO12', 'GPIO13', 'GPIO14', 'GPIO15', 'GPIO16', 'GPIO17', 'GPIO18'
, 'GPIO19', 'GPIO2', 'GPIO20', 'GPIO21', 'GPIO22', 'GPIO23', 'GPIO25', 'GPIO26', 'GPIO27', 'GPIO3', 'GPIO32', 'GPIO33',
'GPIO34', 'GPIO35', 'GPIO36', 'GPIO37', 'GPIO38', 'GPIO39', 'GPIO4', 'GPIO5', 'GPIO6', 'GPIO7', 'GPIO8', 'GPIO9']
>>>
```

To get the CircuitPython to board pin mapping,
we will need to execute the script below ([source of script][36]):

```python
# SPDX-FileCopyrightText: 2020 anecdata for Adafruit Industries
# SPDX-FileCopyrightText: 2021 Neradoc for Adafruit Industries
# SPDX-FileCopyrightText: 2021-2023 Kattni Rembor for Adafruit Industries
# SPDX-FileCopyrightText: 2023 Dan Halbert for Adafruit Industries
#
# SPDX-License-Identifier: MIT

""" CircuitPython Pin Map Script: This script will list the mapping of physical board pins
    to what those pins can be called in a CircuitPython script. """

import microcontroller
import board
try:
    import cyw43  # raspberrypi
except ImportError:
    cyw43 = None

board_pins = []
for pin in dir(microcontroller.pin):
    if (isinstance(getattr(microcontroller.pin, pin), microcontroller.Pin) or
        (cyw43 and isinstance(getattr(microcontroller.pin, pin), cyw43.CywPin))):
        pins = []
        for alias in dir(board):
            if getattr(board, alias) is getattr(microcontroller.pin, pin):
                pins.append(f"board.{alias}")
        # Add the original GPIO name, in parentheses.
        if pins:
            # Only include pins that are in board.
            pins.append(f"({str(pin)})")
            board_pins.append(" ".join(pins))

for pins in sorted(board_pins):
    print(pins)
```

Place this script in the file `pin-mapping.py`, upload it to the ESP32 device,
and observer the pin mapping (**NOTE** that CircuitPython may have more than one name for a pin):

```bash
# check type of board, flash size, etc.
esptool.py --port /dev/ttyUSB0 flash_id

# upload and execute file pin-mapping.py
$ ampy --port /dev/ttyUSB0 run pin-mapping.py
board.D1 board.RX0 (GPIO1)
board.D12 (GPIO12)
board.D13 (GPIO13)
board.D14 (GPIO14)
board.D15 (GPIO15)
board.D16 board.RX board.RX2 (GPIO16)
board.D17 board.TX board.TX2 (GPIO17)
board.D18 board.SCK (GPIO18)
board.D19 board.MISO (GPIO19)
board.D2 board.LED (GPIO2)
board.D21 board.SDA (GPIO21)
board.D22 board.SCL (GPIO22)
board.D23 board.MOSI (GPIO23)
board.D25 (GPIO25)
board.D26 (GPIO26)
board.D27 (GPIO27)
board.D3 board.TX0 (GPIO3)
board.D32 (GPIO32)
board.D33 (GPIO33)
board.D34 (GPIO34)
board.D35 (GPIO35)
board.D4 (GPIO4)
board.D5 (GPIO5)
board.VN (GPIO39)
board.VP (GPIO36)
```

Each line represents a single physical pin.
Find the line containing the pin name that's labeled on the physical board (aka GPIO),
and you'll find the other names available, used by CircuitPython,for that pin.
For example, there is a GPIO pin numbered `18` (above shown as `(GPIO18)`).
het line is `board.D18 board.SCK (GPIO18)`.
This means that you can access GPIO pin numbered `18` in CircuitPython using both `board.D18` and `board.SCK`.

Sources:
* [CircuitPython Pins and Modules](https://learn.adafruit.com/circuitpython-essentials/circuitpython-pins-and-modules#circuitpython-pins-3082637)











------



#### Jupyter
* [MicroPython Jupyter notebook kernel with Tony D! @micropython @ProjectJupyter](https://www.youtube.com/watch?v=UFc0pR2ehiw&feature=youtu.be)
* [Micropython on ESP Using Jupyter](https://www.instructables.com/id/Micropython-on-ESP-Using-Jupyter/)
* [Programming an ESP using Jupyter Notebook](https://lemariva.com/blog/2019/01/micropython-programming-an-esp-using-jupyter-notebook)
* [MicroPython on ESP Using Jupyter Notebook](https://towardsdatascience.com/micropython-on-esp-using-jupyter-6f366ff5ed9)
* [Micropython on ESP Using Jupyter](https://www.instructables.com/id/Micropython-on-ESP-Using-Jupyter/)
* [Get on the Good Foot with MicroPython on the ESP32, Part 1 of 2](https://boneskull.com/micropython-on-esp32-part-1/)
* [Get on the Good Foot with MicroPython on the ESP32, Part 2 of 2](https://boneskull.com/micropython-on-esp32-part-2/)
* [A Jupyter based Micropython tutorial](https://github.com/hoihu/projects/blob/master/uPy/jupyter/uPy-tutorial1.ipynb)
* [Jupyter MicroPython Kernel](https://github.com/goatchurchprime/jupyter_micropython_kernel)
* [MicroPython Jupyter notebook kernel with Tony D! @micropython @ProjectJupyter](https://www.youtube.com/watch?v=UFc0pR2ehiw&feature=youtu.be)

 jupyter worksheet that explains things (how to install jupyter and the `mpy-repl-tool` package) and shows how to turn on a LED resp. the example disco flash effect from the official tutorials: https://github.com/hoihu/projects/blob/master/uPy/jupyter/uPy-tutorial1.ipynb

`mpy-repl-tool` is a package available on pypi with micropython tools
* [Welcome to mpy-REPL-Tool’s documentation!](https://mpy-repl-tool.readthedocs.io/en/latest/)

## Jupyter MicroPython Kernel
The Jupyter Notebook community have created a kernel to interact
with a MicroPython ESP8266 or ESP32 over its serial REPL.

* [MicroPython on ESP Using Jupyter Notebook](https://towardsdatascience.com/micropython-on-esp-using-jupyter-6f366ff5ed9)
* [Jupyter MicroPython Kernel](https://github.com/goatchurchprime/jupyter_micropython_kernel/)
* [CircuitPython Libraries and Jupyter Notebook on any Computer with MCP2221](https://learn.adafruit.com/jupyter-on-any-computer-with-circuitpython-libraries-and-mcp2221)




------












# Installing CircuitPython Libraries and Adafruit_Blinka
CircuitPython runs on microcontroller boards
using a variety of chips, such as the MicroChip SAMD21 SAMD51,
the Raspberry Pi RP2040, the Nordic nRF52840, and the Espressif ESP32-S2 and ESP32-S3.
They are all microcontrollers with hardware peripherals like SPI, I2C, ADCs etc.
But sometimes you want to do more than a microcontroller can do,
like HDMI video output, or camera capture, or serving up a website,
or just something that takes more memory and computing than a microcontroller.

To address this, Adafruit added a software layer where you can use
CircuitPython hardware control capabilities with CPython (aka "regular Python")
There is a special Python to CircuitPython Libraries interface layer called [adafruit_blinka][31]
that provides a layer that translates the CircuitPython hardware API to whatever library the Linux board provides.
CircuitPython firmware is **NOT** used when using Blinka.

![CircuitPython Libraries on Personal Computers](https://cdn-learn.adafruit.com/assets/assets/000/085/901/medium640/sensors_usb_to_mcp2221.png?1576619527)

The upshot is that most code we write for CircuitPython will be instantly
and easily runnable on Linux computers like Raspberry Pi.
You'll be able to use all of AdaFruit device drivers for
sensors, led controllers, motor drivers, HATs, bonnets, etc.
Nearly all of these use I2C or SPI!

* [Adafruit MCP2221A Breakout - General Purpose USB to GPIO ADC I2C](https://learn.adafruit.com/products/4471/guides)
* [Adafruit MCP2221A Breakout - General Purpose USB to GPIO ADC I2C - Stemma QT / Qwiic][51]
* [CircuitPython Libraries and Jupyter Notebook on any Computer with MCP2221](https://learn.adafruit.com/jupyter-on-any-computer-with-circuitpython-libraries-and-mcp2221)

Sources:
* [Adafruit-Blinka][31]
* [Installing Blinka on Raspberry Pi](https://learn.adafruit.com/circuitpython-on-raspberrypi-linux/installing-circuitpython-on-raspberry-pi)
* [CircuitPython Libraries on Linux and Raspberry Pi](https://learn.adafruit.com/circuitpython-on-raspberrypi-linux)

## Adafruit Blinka
Blinka is a software library that emulates the parts of CircuitPython that control hardware.
Blinka provides non-CircuitPython implementations for CircuitPython modules
like `board`, `busio`, `digitalio`, and other native CircuitPython modules.
This enables you to write Python code that looks like CircuitPython and uses CircuitPython libraries,
without having CircuitPython underneath.

There are [multiple ways to use Blinka][52]:

* Linux based Single Board Computers, for example a Raspberry Pi
* Desktop Computers (Windows, MacOS, Linux) + using specialized USB adapters (e.g. [Adafruit MCP2221][51])
* Boards running MicroPython

## USB to I2C/UART with MCP2221
If you are using a microcontroller that can run CircuitPython,
then you will most likely have the low level hardware interfaces needed to access
the many sensors and other breakout boards - I2C, SPI, and GPIO.
If you using a desktop type processor, your generally out-of-luck when it comes to electrically interfacing these board & sensors.

The [tiny microprocessor MCP2221][47] can be used to connect I²C sensors and breakout boards
to your desktop PC running Windows, Mac OSX, or Linux.
It give you a simple way to get I2C, GPIO, ADC, and DAC support on any PC with USB.
The MCP2221 is similar to a USB-to-serial converter chips but adds a GPIO and I2C interface as well.
The MCP2221 is a USB-to-UART/I2C serial converter
which enables USB connectivity in applications that have a UART and I²C interfaces.
The MCP2221 not only supports I2C communications,
but also allows for general purpose digital input/output (GPIO) for things like buttons and LEDs,
analog to digital conversion (ADC), and digital to analog (DAC).

>**NOTE:** Adafruit uses MCP2221 & MCP2221A chips,
>but the difference are not relevant for using Blinka or CircuitPython libraries
>and you can use either version of the chip!

>**NOTE:** The [Adafruit MCP2221][51] is very similar to the [Adafruit FT232H][50].
>The MCP2221 just makes different trade offs relative to the FT232H,
>the biggest being no hardware SPI support on the MCP2221.
>But you do gain ADC & DAC support and it's much cheaper than the FT232H.

## Installing CircuitPython Libraries
* https://learn.adafruit.com/circuitpython-libraries-on-any-computer-with-mcp2221/running-circuitpython-code-without-circuitpython#installing-circuitpython-libraries-3143514

### Linux Single-Board Computers (e.g. Raspberry Pi)

### Desktop Computers Using MCP2221
* Jupter Notebook with MCP2221 - [CircuitPython Libraries and Jupyter Notebook on any Computer with MCP2221](https://learn.adafruit.com/jupyter-on-any-computer-with-circuitpython-libraries-and-mcp2221)
* Google Docs Logging with MCP2221 - [Google Docs Sensor Logging From Your PC](https://learn.adafruit.com/gdocs-sensor-logging-from-your-pc)

### MicroPython



------



# Mix Both MicroPython & CircuitPython Code
* [Mix Both MicroPython & CircuitPython Code In The Same File On A Raspberry Pi Pico With Blinka](https://www.youtube.com/watch?v=l254lxm78I4)

# MicroPython & CircuitPython Coding Examples
An extensive list of great CircuitPython and MicroPython projects can be found here.
Great source for test projects and ideas.

* [Awesome MicroPython](https://awesome-micropython.com/)
    * [GitHub: mcauser/awesome-micropython](https://github.com/mcauser/awesome-micropython)
* [Awesome CircuitPython](https://circuitpython.org/awesome)
    * [GitHub: adafruit/awesome-circuitpython](https://github.com/adafruit/awesome-circuitpython)
* [CircuitPython Tricks](https://github.com/todbot/circuitpython-tricks/tree/main)











------









------








[01]:https://www.micropython.org/
[02]:http://www.arm.com/
[03]:https://store.micropython.org/
[04]:https://learn.adafruit.com/welcome-to-circuitpython/what-is-circuitpython
[05]:https://core-electronics.com.au/tutorials/circuitpython-vs-micropython-differences.html
[06]:https://circuitpython.readthedocs.io/en/2.x/#differences-from-micropython
[07]:https://www.youtube.com/watch?v=m1miwCJtxeM
[08]:https://learn.adafruit.com/sino-bit-micropython/running-code-with-ampy
[09]:https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop
[10]:https://learn.adafruit.com/building-and-running-micropython-on-the-esp8266/build-firmware
[11]:https://www.youtube.com/watch?v=qa2406iiSbI
[12]:https://github.com/adafruit/esp8266-micropython-vagrant/blob/master/Vagrantfile
[13]:https://www.vagrantup.com/
[14]:https://github.com/open-eio/esp32-micropython-vagrant/blob/master/Vagrantfile
[15]:https://docs.espressif.com/projects/esp-idf/en/latest/get-started/index.html#setup-toolchain
[16]:https://www.youtube.com/watch?v=jG7WBY_vmpE
[17]:https://github.com/micropython/micropython
[18]:https://micropython.org/download/ESP32_GENERIC/
[19]:https://github.com/dhylands/rshell
[20]:https://github.com/espressif/esptool
[21]:https://circuitpython.org/downloads
[22]:https://www.virtualbox.org/wiki/Downloads
[23]:https://www.youtube.com/watch?v=5LbgyDmRu9s&feature=youtu.be
[24]:https://github.com/wendlers/mpfshell
[25]:https://realpython.com/python-gil/
[26]:https://peps.python.org/pep-0703/
[27]:https://thonny.org/
[28]:https://hackaday.com/2022/11/14/arduino-brings-a-micropython-ide/
[29]:https://realpython.com/python-debugging-pdb/
[30]:https://circuitpython.org/board/doit_esp32_devkit_v1/
[31]:https://pypi.org/project/Adafruit-Blinka/
[32]:https://pypi.org/project/RPi.GPIO/
[33]:https://codewith.mu/
[34]:https://circuitpython.org/libraries
[35]:https://learn.adafruit.com/welcome-to-circuitpython/circuitpython-libraries
[36]:https://learn.adafruit.com/circuitpython-essentials/circuitpython-pins-and-modules#what-are-all-the-available-names-3082670
[37]:https://docs.circuitpython.org/en/latest/shared-bindings/support_matrix.html
[38]:https://circuitpython.org/board/adafruit_kb2040/
[39]:https://circuitpython.org/board/unexpectedmaker_feathers3/
[40]:https://circuitpython.org/board/unexpectedmaker_tinys2/
[41]:https://carpentries-incubator.github.io/introduction-to-conda-for-data-scientists/02-working-with-environments/index.html
[42]:https://circuitpython.org/board/seeed_xiao_esp32c3/
[43]:https://help.unexpectedmaker.com/index.php/knowledge-base/how-to-out-your-board-into-uf2-bootloader-mode/
[44]:https://circuitpython.org/board/qtpy_m0/
[45]:https://learn.adafruit.com/adafruit-qt-py/circuitpython
[46]:https://learn.adafruit.com/adafruit-kb2040/circuitpython
[47]:https://www.microchip.com/en-us/product/mcp2221
[48]:https://learn.adafruit.com/welcome-to-circuitpython
[49]:https://github.com/adafruit/Adafruit_CircuitPython_Bundle
[50]:https://www.adafruit.com/product/2264
[51]:https://www.adafruit.com/product/4471
[52]:https://learn.adafruit.com/circuitpython-libraries-on-any-computer-with-mcp2221/running-circuitpython-code-without-circuitpython#adafruit-blinka-a-circuitpython-compatibility-library-3149413
[53]:
[54]:
[55]:
[56]:
[57]:
[58]:
[59]:
[60]:

