<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----


# Installing New Arduino-cli
* [Install Arduino CLI on Ubuntu 20.04](https://lindevs.com/install-arduino-cli-on-ubuntu)
* [Arduino CLI](https://arduino.github.io/arduino-cli/latest/installation)
* [Arduino CLI: Getting started](https://arduino.github.io/arduino-cli/latest/getting-started/)

* [Cheatsheet: Arduino Command Line ](https://www.woolseyworkshop.com/wp-content/uploads/WoolseyWorkshop_Cheatsheet_ArduinoCommandLine_v1.4.pdf)
* [Arduino-cli: compile, upload and manage libraries, cores, and boards](https://www.pcbway.com/blog/Activities/Arduino_cli__compile__upload_and_manage_libraries__cores__and_boards.html)

# Using Makefile
* [Arduino With Makefiles For Linux Command Line Programmers](https://blog.robertelder.org/arduino-make-file-command-line/)

# Creating Arduino Library
* [Create Your Own Arduino Library](https://roboticsbackend.com/arduino-create-library/)
* [How To Create Custom Arduino Library Using C++](https://www.geeksforgeeks.org/how-to-create-custom-arduino-library-using-c/)
* [All About Arduino Libraries](https://learn.adafruit.com/adafruit-all-about-arduino-libraries-install-use/arduino-libraries)








# Arduino On The Command Line
For someone like myself, who is at home with Linux as my OS and Vim as my editor,
using the [Arduino IDE][03] for Arduino coding is a step back into the stone age.
If you are used to doing these things yourself and controlling the organization of your code
then the Arduino IDE does some really arbitrary and annoying things.
For example, try sharing a common file between your sketch and modules (that is, Arduino libraries)
which you may or not use depending on what sketch you are compiling.
The Arduino will compile everything in the directory with the included file.
You have no say in what gets compiled and in what context.

I particulalry wanted command line support with ESP8266 addon for the Arduino IDE,
provided by the ESP8266 community ([lead by Ivan Grokhotkov of Espressif][22]).
Check out the [ESP8266 Arduino GitHub repository][32] for more information.
To see more detailed instructions on installing  ESP8266 support on your Arduino IDE,
see [SparkFun's ESP8266 Thing Hookup Guide][33].
[ESP8266 Arduino libraries documentation][34] can be found online.

I'm not the first to lament about the this topic, but more importantly,
some people have stepped forward and done something about it!
The folks at Arduino have given us [Installing Arduino on Linux][01], which gives us
a Arduino IDE, but more importantly, the foundation of this package are executables
and libraries that can be called executed outside of the IDE.
Others like [Martin Oldfield and Sudar Muthu][02] have given us the Linux package `arduino-mk`
which allows you to use the core tools that form the foundation for the Arduino IDE.
Those foundational tools are within the package `arduino-core`.
The actual Arduino IDE is in the package `arduino`.
But these Makefile tools don't easily support the ESP8266/ESP32 boards,
which prompted the creation of [Esp8266-Arduino-Makefile][17]
to get support for the ESP architecture but abandoned the Arduino boards.

I wanted to avoid all this confusion and get on a path that will remain compatible
with the future evolution of the Arduino IDE.
I discovered that [Arduino has released a command line interface (CLI)][13],
called `arduino-cli`,
that performs most of the features present in the Arduino IDE.
The Arduino CLI aims to replace the majority of features the Arduino IDE has without the graphical UI.
The CLI will allow you to Install new libraries, create new projects,
and compile projects directly from the command line.
And it appears the goal of the Arduino CLI in any kind of script for the command line.
So in principle, it should work in a standard Makefile too.

>**NOTE:** As of August 24, 2018, the Arduino team has made a formal
>alpha release [announcment of Arduino Command Line Interface (CLI)][13].
>See the [`arduino-cli` github site][14] for more information, where it says
>"This software is currently under active development:
>anything can change at any time,
>API and UI must be considered unstable until we release version 1.0.0."

One of the things that comes free with the Arduino IDE is a serial monitor.
Of course, this is an indispensable tool for both testing and debugging,
and I don't want to loss this capability.
We haven't abandoned this capability since there are Linux alternatives.
The post [Arduino and Linux TTY][04] provides a series of solutions.
(What is listed below isn't always functional for every need, so consult the posting for more ideas.)

Some of your best monitoring options are:

* Assuming the Arduino's USB is plugged into `/dev/ACM0` and the port speed is set to `57600`,
`cu -l /dev/ttyACM0 -s 57600` will get you simple connect.
For more commands, consult the [`cu` manual page][07].
* You can use [`screen`][08] to provide a more interactive serial monitor session with an Arduino.
The command `screen /dev/ttyACM0 57600` is similar to the above.
See [Linux Screen Tutorial and How To][05]
[Screen User's Manual][06] for more information about the power of `screen`.

What follows is how I installed the [Arduino IDE][03], the [Arduino CLI][14]
and used it with [GNU Make (aka Makefile)][15].
Doing this, I can create an all command line (or nearly all)
software development experance while still leveraging the popularity of the Arduino IDE platform.


-----


# Installing the Arduino IDE
[Arduino][11] is an open-source platform used for building electronics projects.
Arduino consists of both a physical programmable circuit board (often referred to as a microcontroller)
and a piece of software, or IDE (Integrated Development Environment) that runs on your computer,
used to write and upload computer code to the physical board.
There is [Linux build of the Arduino IDE][09],
as well as [alternatives to the standard Arduino IDE][10].

#### Step 1: Uninstall Old Arduino IDE - DONE
If you upgrading your Arduino IDE,
the first thing you want to do is uninstall the old version.
The Arduino IDE package comes with an uninstall script but it doesn't do a complete removal
of all the configuration files and modifications you have likely make over time.
You'll need to save and then reinstall those things you have added.
The procedure below should do the trick.

Copy any of your sketch and personal libraries you may wish to keep.
Don't worry about public libraries since they can be reinstalled from sources.

Sources
* [Uninstall Arduino IDE](https://support.arduino.cc/hc/en-us/articles/360021325733-Uninstall-Arduino-IDE)

```bash
# to find the path to the arduino ide
whereis arduino

# copy your executable
cp -r ~/bin/arduino ~/tmp/arduino
rm -r -f ~/bin/arduino

# remove the arduino ide confguration files
trash ~/.arduino15 ~/tmp/arduino
trash ~/Arduino

# remove your symbolic link to the arduino ide executable
rm ~/bin/arduino

# remove the entire arduino ide directory
cd ~
rm -r -f ~/src/arduino

# remove any appimage you have for arduino ide
rm -r -f ~/bin/arduino-ide*.AppImage
```

#### Step 2: Installing Arduino IDE - DONE
You could install the Arduino IDE via the Ubuntu Software Center and search for Arduino.
Alternatively, you can install via the command line by running the following:

Source:
* [Downloading and installing the Arduino IDE 2.0](https://docs.arduino.cc/software/ide-v2/tutorials/getting-started/ide-v2-downloading-and-installing)

```bash
# install arduino from software repositories (NOT RECOMMENDED)
sudo apt-get update && sudo apt-get install arduino arduino-core
```

The above installs a package from the Ubuntu software repositories,
which likely to be an older Arduino IDE version.
The newest version of the Arduino can be downloaded from the [Arduino download page][12].
(**NOTE:** Using this method Arduino software won't automatically be updated,
so you should check Arduino website every few months and download
a new version if one is available.)

```bash
# download the software - arduino-ide_2.0.3_Linux_64bit.zip
# from https://www.arduino.cc/en/software

# download the appimage file
cd ~/bin
wget https://downloads.arduino.cc/arduino-ide/arduino-ide_2.2.1_Linux_64bit.AppImage
```

Before we can launch the Arduino IDE,
we need to first make it an executable file.
This is done by:

* right-click the file,
* choose **Properties**,
* select **Permissions** tab,
* tick the **Allow executing file as program** box.

Now make it executable from your `bin`:

```bash
# make the appimage executable
chmod ug+x arduino-*.AppImage

# make it executable as 'arduino'
ln -s /home/jeff/bin/arduino-ide_2.2.1_Linux_64bit.AppImage /home/jeff/bin/arduino
```

#### Step 3: Quick Test - DONE
Lets do a quick check on the install:

```bash
# execute arduino ide
arduino

# or
arduino &>/dev/null &
```

This will also create the directories `$HOME/Arduino` to hold your sketchbook
and the directories `$HOME/.arduino15` and  `$HOME/.arduinoIDE`

When the Arduino Software IDE is properly installed you can execute
the IDE via the command `arduino &>/dev/null &` or the desktop icon.

>**NOTE:** It might happen that when you upload a sketch
>(after you have selected your board and serial port),
>you get an error Error opening serial port.
>If you get this error, you need to [set serial port permission][23].

#### Step 4: Setup Your Arduino IDE Preferences - DONE
Normally, running the `arduino` command starts the IDE,
optionally loading any `.ino` files specified on the commandline.
Also, it normally puts all your Arduino sketches and project libraries within
a common directory defaulting to `$HOME/Arduino`.
Lets change this location:

1. Create the directory `$HOME/src/arduino/sketchbooks`
2. Start the Arduino IDE, select the menu button **File** > **Preferences**
3. Change the "Sketchbook location" to `$HOME/src/arduino/sketchbooks`
(make sure you do this via the **Browse** button) and save it.
4. Restart the Arduino and the directory will be prepared automatically for you

>**NOTE:** Some preferences, but not all,
>can be controlled from the Preferences dialog within the Arduino environment (see [here][19]).
>More preferences can be edited directly in the file `$HOME/.arduino15/preferences.txt`
>but only edit when the Arduino IDE is **not** running.

#### Step 5: Remove Old Sketch Directory - DONE
When you create your fist sketch,
the new `sketchbook` directory create above will have a subdirectory `libraries`.
`$HOME/src/arduino/sketchbooks/libraries` is where all your libraries will go
(both downloads and personal ones you create).
Now that your sketches and libraries have a new location,
make sure to remove the default location created during the Arduino IDE install:

```bash
# remove the old sketchbook location
rm -r -f ~/Arduino
```

>**NOTE:** Improperly installing libraries can be a major source of confusion within the Arduino world.
>Check out Adafruit's "[All About Arduino Libraries][18]" for their proper care and feeding.

#### Step 6: Move Back Saved Sketches - DONE
If you you saved any sketch from a previous install,
you can simply copy them into the `$HOME/src/arduino/sketchbooks` directory.
For example:

```bash
# copy your old sketches into you new sketchbook
cp -r ~/tmp/sketchbooks ~/src/arduino
```


-----


# Installing the Arduino Commond Line Interface - `arduino-cli`
[Arduino has released a command line interface (CLI)][13], called `arduino-cli`,
that performs most of the features present in the Arduino IDE.
The CLI will allow you to Install new libraries, create new projects,
and compile projects directly from the command line.
The goal of the Arduino CLI is to be including it in Makefile
or in any kind of script for the command line.
The Arduino CLI aims to replace the majority of features
the Arduino IDE has without the graphical UI.

There isn't a great deal of documentation on `arduino-cli`
but the [`arduino-cli` github site][14] provides what you need for installation.
I also found these sites useful:

* [Install Arduino CLI on Ubuntu 20.04](https://lindevs.com/install-arduino-cli-on-ubuntu)
* [Arduino CLI](https://arduino.github.io/arduino-cli/latest/installation)
* [Arduino CLI: Getting started](https://arduino.github.io/arduino-cli/latest/getting-started/)

* [Arduino now has a command line interface (CLI)](https://hub.packtpub.com/arduino-now-has-a-command-line-interface-cli/)
* [Tutorial on the Arduino Command Line Interface (CLI)][21]
* [Using The Arduino Command Line](https://www.woolseyworkshop.com/2019/04/14/using-the-arduino-command-line/)
* [Arduino Command Line Interface](https://github.com/arduino/arduino-cli)
* [Arduino CLI Command Line Interface Getting Started (Mac and Windows)](https://www.youtube.com/watch?v=8LPSjucQoso)
* [Arduino Gets Command Line Interface Tools That Let You Skip the IDE](https://hackaday.com/2018/08/26/arduino-gets-command-line-interface-tools-that-let-you-skip-the-ide/)

>**NOTE:** As of August 24, 2018, the Arduino team has made a formal
>alpha release [announcment of Arduino Command Line Interface (CLI)][13].
>See the [`arduino-cli` github site][14] for more information, where it says
>"This software is currently under active development:
>anything can change at any time,
>API and UI must be considered unstable until we release version 1.0.0."

#### Step 0: Uninstall arduino-cli - DONE
You may have installed `arduino-cli` in the past and it will be wise to remove
any other version that may be in your `$PATH`.

```bash
# check the version of arduino-cli your using
$ arduino-cli version
arduino-cli  Version: 0.29.0 Commit: 76251df9 Date: 2022-11-17T09:21:40Z
A new release of Arduino CLI is available: 0.29.0 → 0.34.2
https://arduino.github.io/arduino-cli/latest/installation/#latest-packages

# remove executable in your PATH
sudo rm -rf ~/bin/arduino-cli /usr/bin/arduino-cli /usr/local/bin/arduino-cli
```

#### Step 1: Install arduino-cli - DONE
You can install `arduino-cli` via:

```bash
# install via snap container
sudo snap install arduino-cli
```

The easiest way to get the **latest version** of
`arduino-cli` is to use the supplied `install.sh` script:

```bash
# isntall arduino-cli in your local bin
$ curl -fsSL https://raw.githubusercontent.com/arduino/arduino-cli/master/install.sh | BINDIR=$HOME/bin sh
Installing in /home/jeff/bin
ARCH=64bit
OS=Linux
Using curl as download tool
Downloading https://downloads.arduino.cc/arduino-cli/arduino-cli_0.28.0_Linux_64bit.tar.gz
arduino-cli  Version: 0.28.0 Commit: 06fb1909 Date: 2022-10-20T08:42:19Z installed successfully in /home/jeff/bin

# check the the installation
$ arduino-cli version
arduino-cli  Version: 0.28.0 Commit: 06fb1909 Date: 2022-10-20T08:42:19Z

# list commandline options
$ arduino-cli help
Arduino Command Line Interface (arduino-cli).

Usage:
  arduino-cli [command]

Examples:
  arduino-cli <command> [flags...]

Available Commands:
  board           Arduino board commands.
  burn-bootloader Upload the bootloader.
  cache           Arduino cache commands.
  compile         Compiles Arduino sketches.
  completion      Generates completion scripts
  config          Arduino configuration commands.
  core            Arduino core operations.
  daemon          Run as a daemon on port: 50051
  debug           Debug Arduino sketches.
  help            Help about any command
  lib             Arduino commands about libraries.
  monitor         Open a communication port with a board.
  outdated        Lists cores and libraries that can be upgraded
  sketch          Arduino CLI sketch commands.
  update          Updates the index of cores and libraries
  upgrade         Upgrades installed cores and libraries.
  upload          Upload Arduino sketches.
  version         Shows version number of Arduino CLI.

Flags:
      --additional-urls strings   Comma-separated list of additional URLs for the Boards Manager.
      --config-file string        The custom config file (if not specified the default will be used).
      --format string             The output format for the logs, can be: text, json, jsonmini, yaml (default "text")
  -h, --help                      help for arduino-cli
      --log-file string           Path to the file where logs will be written.
      --log-format string         The output format for the logs, can be: text, json
      --log-level string          Messages with this level and above will be logged. Valid levels are: trace, debug, info, warn, error, fatal, panic
      --no-color                  Disable colored output.
  -v, --verbose                   Print the logs on the standard output.

Use "arduino-cli [command] --help" for more information about a command.
```

#### Step 2: List arduino-cli Board Support - DONE
If you are running a fresh install of the `arduino-cli`,
you probably need to update the platform indexes by running:

```bash
# update the local cache of available platforms and libraries
$ arduino-cli core update-index
Downloading index: package_index.tar.bz2 downloaded

# shows the list of installed platforms
$ arduino-cli core list
ID          Installed Latest Name
arduino:avr 1.8.6     1.8.6  Arduino AVR Boards
```

This shows that only the default Arduino board core is currently available.
Now list list all the available boards that are supported.

```bash
# list all known boards and their corresponding FQBN
$ arduino-cli board listall
Board Name                       FQBN
Adafruit Circuit Playground      arduino:avr:circuitplay32u4cat
Arduino BT                       arduino:avr:bt
Arduino Duemilanove or Diecimila arduino:avr:diecimila
Arduino Esplora                  arduino:avr:esplora
Arduino Ethernet                 arduino:avr:ethernet
Arduino Fio                      arduino:avr:fio
Arduino Gemma                    arduino:avr:gemma
Arduino Industrial 101           arduino:avr:chiwawa
Arduino Leonardo                 arduino:avr:leonardo
Arduino Leonardo ETH             arduino:avr:leonardoeth
Arduino Mega ADK                 arduino:avr:megaADK
Arduino Mega or Mega 2560        arduino:avr:mega
Arduino Micro                    arduino:avr:micro
Arduino Mini                     arduino:avr:mini
Arduino NG or older              arduino:avr:atmegang
Arduino Nano                     arduino:avr:nano
Arduino Pro or Pro Mini          arduino:avr:pro
Arduino Robot Control            arduino:avr:robotControl
Arduino Robot Motor              arduino:avr:robotMotor
Arduino Uno                      arduino:avr:uno
Arduino Uno Mini                 arduino:avr:unomini
Arduino Uno WiFi                 arduino:avr:unowifi
Arduino Yún                      arduino:avr:yun
Arduino Yún Mini                 arduino:avr:yunmini
LilyPad Arduino                  arduino:avr:lilypad
LilyPad Arduino USB              arduino:avr:LilyPadUSB
Linino One                       arduino:avr:one
```

#### Step 3: Install New Core's for arduino-cli - DONE
The list above only include Arduino microcontrollers.
What if you wanted support for [SAM D MCUs][16]
In this case, you would install the `arduino:samd`
platform core by running the following:

```bash
# install support for SAM D processors
$ arduino-cli core install arduino:samd
Downloading packages...
arduino:arm-none-eabi-gcc@7-2017q4 downloaded
arduino:bossac@1.7.0-arduino3 downloaded
arduino:openocd@0.10.0-arduino7 downloaded
arduino:CMSIS@4.5.0 downloaded
arduino:CMSIS-Atmel@1.2.0 downloaded
arduino:arduinoOTA@1.2.1 downloaded
arduino:samd@1.8.4 downloaded
Installing arduino:arm-none-eabi-gcc@7-2017q4...
arduino:arm-none-eabi-gcc@7-2017q4 installed
Installing arduino:bossac@1.7.0-arduino3...
arduino:bossac@1.7.0-arduino3 installed
Installing arduino:openocd@0.10.0-arduino7...
arduino:openocd@0.10.0-arduino7 installed
Installing arduino:CMSIS@4.5.0...
arduino:CMSIS@4.5.0 installed
Installing arduino:CMSIS-Atmel@1.2.0...
arduino:CMSIS-Atmel@1.2.0 installed
Installing arduino:arduinoOTA@1.2.1...
arduino:arduinoOTA@1.2.1 installed
Installing arduino:samd@1.8.4...
arduino:samd@1.8.4 installed
```

There’s an add-on for the Arduino IDE that allows you to program the [ESP32 MCUs][35]
using the Arduino IDE and its programming language.
To install the ESP32 & ESP8266 board,
you need to add some additional board manager URLs.

```bash
# update the cores
arduino-cli core update-index
```

Next, Follow these steps in your Arduino IDE:

* execute `arduino` on the commandline
* Goto **File** > **Preferences**
* Enter the following into the **Additional Board Manager URLs** field:
    * `https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json,
    http://arduino.esp8266.com/stable/package_esp8266com_index.json`
* Save your work
* Open the Boards Manager by going to **Tools** > **Board** > **Boards Manager…**
* Search for ESP8266 and click **Install**
* Search for ESP32 and click **Install**

Now lets see if support of the new boards is present:

```bash
# verify we have installed the core properly
$ arduino-cli core list
ID              Installed Latest Name
arduino:avr     1.8.6     1.8.6  Arduino AVR Boards
esp32:esp32     2.0.5     2.0.5  esp32
esp8266:esp8266 3.0.2     3.0.2  esp8266
```

Source:
* [ESP32: Using arduino-cli][35]
* [Getting Started with arduino-cli](https://create.arduino.cc/projecthub/B45i/getting-started-with-arduino-cli-7652a5)
* [Installing the ESP32 Board in Arduino IDE (Windows, Mac OS X, Linux)](https://randomnerdtutorials.com/installing-the-esp32-board-in-arduino-ide-windows-instructions/)

#### Step 4: Fix the `esptool`
I had to do a "fix" the [`esptool.py` tool][24] (ROM bootloader for ESP8266 & ESP32)
since its not within my $PATH
The fix is the following:

```bash
# remove any old symbolic link to esptool
rm -f -f ~/bin/esptool

# check the newly install esptool is executable
$ ls -l ~/.arduino15/packages/esp32/tools/esptool_py/4.5.1/esptool*
chmod ug+x ~/.arduino15/packages/esp32/tools/esptool_py/4.5.1/esptool.py

# create a symbolic link to the esptool executable
ln -s ~/.arduino15/packages/esp32/tools/esptool_py/4.5.1/esptool.py ~/bin/esptool

# test you can now reach it
$ esptool
usage: esptool [-h] [--chip {auto,esp8266,esp32}] [--port PORT] [--baud BAUD]
               [--before {default_reset,no_reset,no_reset_no_sync}]
               [--after {hard_reset,soft_reset,no_reset}] [--no-stub]
               [--trace] [--override-vddsdio [{1.8V,1.9V,OFF}]]
               {load_ram,dump_mem,read_mem,write_mem,write_flash,run,image_info,make_image,elf2image,read_mac,chip_id,flash_id,read_flash_status,write_flash_status,read_flash,verify_flash,erase_flash,erase_region,version}
               ...
esptool: error: too few arguments
```

-----


# Using the arduino-cli With ESP Processor
In this section,
I'll walkthrough how to make use of `arduino-cli` to build projects.
I'll be using examples from [ntp-clock.ino][20].

#### Step 1: Load Needed Libraries
The example I'm doing, the [ntp-clock.ino][20] sketch,
requires several additional libraries which are not
pre-installed in the Arduino IDE or the `arduino-cli`.
I show below how to do a library install via a`arduino-cli`,
and they will be place in `$HOME/src/arduino/sketechbooks/libraries`

>**NOTE:** You could have install this libary within the Arduino IDE, for example,
>via **Tools** > **Manage Libraries...** > enter "arduino-timer" and install.
>That will work with the Adruino IDE but would **not** have worked with `ardunio-cli`.
>You must use `arduino-cli lib install <library-name>`.

The `arduino-cli` command we will use to install libraries is `arduino-cli lib ...`:

```bash
# help message for arduino-cli lib
$ arduino-cli lib help
Arduino commands about libraries.

Usage:
  arduino-cli lib [command]

Examples:
  arduino-cli lib install AudioZero
  arduino-cli lib update-index

Available Commands:
  download     Downloads one or more libraries without installing them.
  install      Installs one of more specified libraries into the system.
  list         Shows a list of all installed libraries.
  search       Searchs for one or more libraries data.
  uninstall    Uninstalls one or more libraries.
  update-index Updates the libraries index.
  upgrade      Upgrades installed libraries.

Flags:
  -h, --help   help for lib

Global Flags:
      --config-file string   The custom config file (if not specified ./.cli-config.yml will be used).
      --debug                Enables debug output (super verbose, used to debug the CLI).
      --format string        The output format, can be [text|json]. (default "text")

Use "arduino-cli lib [command] --help" for more information about a command.
```

One of the libraries to be installed is `arduino-timer`.
You can see how this is done below:

```bash
# search for a library with 'arduino-timer' in its name
$ arduino-cli lib search arduino-timer
Name: "arduino-timer"
  Author: Michael Contreras
  Maintainer: Michael Contreras
  Sentence: Timer library for delaying function calls
  Paragraph: Simple non-blocking timer library for calling functions in / at / every specified units of time. Supports millis, micros, time rollover, and compile time configurable number of tasks.
  Website: https://github.com/contrem/arduino-timer
  Category: Timing
  Architecture: *
  Types: Contributed
  Versions: [0.0.1, 1.0.0, 1.0.1, 2.0.0, 2.0.3]
Name: "arduino-timer-api"
  Author: sadr0b0t
  Maintainer: sadr0b0t
  Sentence: Simple cross-platform API for multitasking on timer interrupt handlers
  Paragraph: Simple cross-platform API for multitasking on Arduino based on timer interrupt handlers. Works with AVR/Arduino, PIC32/ChipKIT platforms.
  Website: https://github.com/sadr0b0t/arduino-timer-api
  Category: Timing
  Architecture: *
  Types: Contributed
  Versions: [0.1.0]

# install the desired library
$ arduino-cli lib install "arduino-timer"
arduino-timer depends on arduino-timer@2.0.3
Downloading arduino-timer@2.0.3...
arduino-timer@2.0.3 downloaded
Installing arduino-timer@2.0.3...
Installed arduino-timer@2.0.3

# check if it installed
$ arduino-cli lib list
Name          Installed Available Location
arduino-timer 2.0.3     -         user
```

I'll use this non-trivial example sketch, [ntp-clock.ino][20],
which makes use of a ESP8266/NodeMCU + 7-segment LED display board.
Let's install the required libraries for the sketch `ntp-clock.ino`:

```bash
# install all your required libraries
arduino-cli lib install "arduino-timer"
arduino-cli lib install "Adafruit GFX Library"
arduino-cli lib install "Adafruit LED Backpack Library"@1.1.6
arduino-cli lib install "Time"
arduino-cli lib install "Timezone"

# or
arduino-cli lib install "arduino-timer" "Adafruit GFX Library" "Adafruit LED Backpack Library" "Time" "Timezone"

# to see what you have installed so far
$ arduino-cli lib list
Name                          Installed Available Location
arduino-timer                 2.0.1     -         user
Adafruit_ILI9341              1.5.4     -         user
Adafruit_LED_Backpack_Library 1.1.6     -         user
Adafruit_GFX_Library          1.7.5     -         user
Timezone                      1.2.4     -         user
Adafruit_TouchScreen          1.0.4     -         user
Adafruit_STMPE610             1.1.0     -         user
Time                          1.6       -         user
```

To remove all these libraries, just use the following command:
`arduino-cli lib uninstall Adafruit_GFX_Library Adafruit_LED_Backpack_Library arduino-timer Time Timezone`.

#### Step 2: Find the Board's FQBN (Fully Qualified Board Name)
First step is understand what type of board your dealing.
To do this, just connect your device to your PC via a USB,
in my case a ESP8266/NodeMCU board,
and run a command to sense the board:

```bash
# connect the board to PC via usb cable

# sense the board
$ arduino-cli board list
Port         Type              Board Name FQBN Core
/dev/ttyUSB0 Serial Port (USB) Unknown
```

This wasn't much help since `arduino-cli` couldn't detect the board type.
We know the board is some type of NodeMCU with a ESP8266.
Let's list available cores matching 'nodemcu':

```bash
# list all boards matching 'nodemcu'
$ arduino-cli board listall nodemcu
Board Name                  	FQBN
NodeMCU 0.9 (ESP-12 Module) 	esp8266:esp8266:nodemcu
NodeMCU 1.0 (ESP-12E Module)	esp8266:esp8266:nodemcuv2
NodeMCU-32S                 	esp32:esp32:nodemcu-32s
```

My board is the "NodeMCU 1.0 (ESP-12E Module)", and so,
we now have its coresponding Fully Qualified Board Name (FQBN)
of `esp8266:esp8266:nodemcuv2`.
This gives us the needed information to complile the sketch.

#### Step 3: Compiling the Sketch
The `arduino-cli` tool also supports compiling and loading of the sketch.
hear is more information on compiling:

```bash
# help message for arduino-cli compiler
$ arduino-cli help compile
Compiles Arduino sketches.

Usage:
  arduino-cli compile [flags]

Examples:
  arduino-cli compile -b arduino:avr:uno /home/user/Arduino/MySketch

Flags:
      --build-cache-path string    Builds of 'core.a' are saved into this path to be cached and reused.
      --build-path string          Path where to save compiled files. If omitted, a directory will be created in the default temporary path of your OS.
      --build-properties strings   List of custom build properties separated by commas. Or can be used multiple times for multiple properties.
  -b, --fqbn string                Fully Qualified Board Name, e.g.: arduino:avr:uno
  -h, --help                       help for compile
  -o, --output string              Filename of the compile output.
      --preprocess                 Print preprocessed code to stdout instead of compiling.
      --quiet                      Optional, supresses almost every output.
      --show-properties            Show all build properties used instead of compiling.
  -v, --verbose                    Optional, turns on verbose mode.
      --vid-pid string             When specified, VID/PID specific build properties are used, if boards supports them.
      --warnings string            Optional, can be "none", "default", "more" and "all". Defaults to "none". Used to tell gcc which warning level to use (-W flag). (default "none")

Global Flags:
      --config-file string   The custom config file (if not specified ./.cli-config.yml will be used).
      --debug                Enables debug output (super verbose, used to debug the CLI).
      --format string        The output format, can be [text|json]. (default "text")
```

To compile the sketch we have to run the compile command
with the proper board's FQBN (Fully Qualified Board Name) we just got in the previous command.
Now we are going to compile the [ntp-clock.ino][20] sketch.

```bash
# download net-clock.ino
mkdir ~/tmp/ntp-clock
cd ~/tmp/ntp-clock
wget https://gist.github.com/jeffskinnerbox/d74f518157c28dc2dac3297095417447/raw
mv raw ntp-clock.ino

# compile the sketch
$ arduino-cli compile --fqbn esp8266:esp8266:nodemcuv2 ~/tmp/ntp-clock
WARNING: library Timezone claims to run on avr architecture(s) and may be incompatible with your current board which runs on esp8266 architecture(s).
Sketch uses 279620 bytes (26%) of program storage space. Maximum is 1044464 bytes.
Global variables use 30268 bytes (36%) of dynamic memory, leaving 51652 bytes for local variables. Maximum is 81920 bytes.
```

This will create two file,
`ntp-clock.esp8266.esp8266.nodemcuv2.bin` and `ntp-clock.esp8266.esp8266.nodemcuv2.elf`,
within `~/src/ntp-clock`.
The `.bin` file is the firmware that will be uploaded into the microcontroller.
The `.elf` file is a executable and linkable format (elf)
formated file used when object file linking is required.

#### Step 4: UpLoad the Sketch
We can now upload the sketch to the ESP8266 board
and see the board in operation.

```bash
# help information concerning upload
$ arduino-cli help upload
Upload Arduino sketches.

Usage:
  arduino-cli upload [flags]

Examples:
  arduino-cli upload /home/user/Arduino/MySketch

Flags:
  -b, --fqbn string    Fully Qualified Board Name, e.g.: arduino:avr:uno
  -h, --help           help for upload
  -i, --input string   Input file to be uploaded.
  -p, --port string    Upload port, e.g.: COM10 or /dev/ttyACM0

  -t, --verify         Verify uploaded binary after the upload.

Global Flags:
      --config-file string   The custom config file (if not specified ./.cli-config.yml will be used).
      --debug                Enables debug output (super verbose, used to debug the CLI).
      --format string        The output format, can be [text|json]. (default "text")
```

As before, we need to provide the FQBN, but also specify the serial port used by the board:
We'll do this for the [ntp-clock.ino][20] sketch:

```bash
# upload the compile sketch
$ arduino-cli upload --fqbn esp8266:esp8266:nodemcuv2 --port /dev/ttyUSB0 ~/tmp/ntp-clock
No new serial port detected.
esptool.py v2.6
2.6
esptool.py v2.6
Serial port /dev/ttyUSB0
Connecting....
Chip is ESP8266EX
Features: WiFi
MAC: bc:dd:c2:24:f9:fb
Uploading stub...
Running stub...
Stub running...
Configuring flash size...
Auto-detected Flash size: 4MB
Compressed 283776 bytes to 205769...
Wrote 283776 bytes (205769 compressed) at 0x00000000 in 18.2 seconds (effective 124.9 kbit/s)...
Hash of data verified.

Leaving...
Hard resetting via RTS pin...
```

Your board should now be running the `ntp-clock.ino` sketch.
To validate, execute `screen /dev/ttyUSB0 9600,cs8` in a terminal and push the reset button on the NodeMCU.


----


# Using Makefile
You'll find Makefile template for the [Arduino board family][26],
the [Atmel (now Microchip) AVR family][25],
[Espressif Systems ESP family][17] ([there is more than one][27]), and others.
The harsh reality is that there isn't single Makefile template for all
the boards & processors leveraging the Arduino IDE or `arduino-cli`.
Ideally, I want to have a simple to understand Makefile for
the specific board/processor families I'm interested in.
There are several "best practices" you'll find them here:

* [Practical Makefiles, by example](http://nuclear.mutantstargoat.com/articles/make/)
* [Make: Building AVR And Arduino Firmware On The Command Line](https://flyingcarsandstuff.com/2017/11/make-building-avr-and-arduino-firmware-on-the-command-line/)
* [Makefiles, Best Practices](https://danyspin97.org/blog/makefiles-best-practices/)
* [ESP8266 - First Steps](http://smallbits.marshall-tribe.net/blog/2016/05/07/esp8266-first-steps)

To get what I needed,
I ended up settling on on [makeEspArduino][27] as the foundation of my Makefile.
While not as simple as I wished,
it does seem to be very functional and well supported.
It's major down side is its lack of good documentation.
Only materials I have found are:

* [makeEspArduino: README File](https://github.com/plerup/makeEspArduino/blob/master/README.md)
* [makeEspArduino: A makefile for ESP8266 and ESP32 Arduino projects](https://libraries.io/github/plerup/makeEspArduino)

#### Step 1: Create the Makefile - DONE
You'll find that the simple Makefile below
will support our example sketch [ntp-clock.ino][20] when using `arduino-cli`.
It is capable of supporting not only the `*.ino` file but additional C++ files (i.e. `*.cpp`).
Place the text below in a file called `Makefile`:

```bash
#-------------------------------------------------------------------------------
#
# Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
# Version:      0.9.5
#
# USAGE
#   To build the executable
#       make build                              # build the firmare but don't upload
#
#   To flash the device
#       make upload                             # upload firmware via usb port
#       make upload-ota                         # upload firmware via wifi over-the-air (ota)
#
#   To build the executable and flash the device
#       make                                    # build and upload the firmware via usb port
#       make all                                # build and upload the firmware via usb port
#
#   To monitor execution of the device
#       screen /dev/ttyUSB0 9600,cs8cls
#       to terminate Ctrl-a :quit
#
#       telnet ota.local
#       to terminate Ctrl-a quit
#
#   Makefile Syntax
#       =  set the variable
#       ?= set the variable only if it's not set/doesn't have a value
#       := set variable as the output an executed shell script
#       += is used for appending more text to variables
#       $$ if you want a dollar sign to appear in your recipe, you must double it (‘$$’)
#
# SOURCES
#   The Makefile was created with the help of this website:
#   https://learn.sparkfun.com/tutorials/efficient-arduino-programming-with-arduino-cli-and-visual-studio-code/all
#
# DOCUMENTATION
#   https://create.arduino.cc/projecthub/B45i/getting-started-with-arduino-cli-7652a5
#
#-------------------------------------------------------------------------------

# Use Bash shell instead of the default /bin/sh
SHELL := /bin/bash

# name of program being created
PROG = ntp-clock

# type of package, architecture, and board in use
PACKAGE = esp8266
ARCH =    esp8266
BOARD =   nodemcuv2

# serial port used by the board
PORT = /dev/ttyUSB0

#------------------------- names, tools, flags, paths --------------------------

# optional verbose compile/upload flag
#VERBOSE = -v

# fully qualified board name (FQBN)
FQBN = $(PACKAGE):$(ARCH):$(BOARD)

# location of the esptool used for usb flashing
ESPTOOL = /home/jeff/.arduino15/packages/esp32/tools/esptool_py/2.6.1/esptool.py

# string within names given to .bin and .elf files
VAR := $(shell echo $(FQBN) | tr ':' '.')

# path for temp-storage of binary, object, and core.a files
BUILD = /tmp/$(PROG)
BUILD_PATH = $(BUILD)/build

# paths to libraries and include files
LIBS = "/home/jeff/src/arduino/sketchbooks/libraries"

#---------------------------------- compiler -----------------------------------

# compiler and compiler flags
CC = arduino-cli compile
CC_FLAGS = $(VERBOSE) --fqbn $(FQBN) --build-path=$(BUILD_PATH) --build-cache-path=$(BUILD) --libraries $(LIBS)

#--------------------------------- usb upload ----------------------------------

# usb firmware flasher and flags
UPLOAD_USB = arduino-cli upload
UPLOAD_USB_FLAGS = $(VERBOSE) --fqbn $(FQBN) --port $(PORT) --input-dir $(BUILD_PATH)

#--------------------------------- ota upload ----------------------------------

# location of the espota.py used for ota flashing
ESPOTATOOL = /home/jeff/.arduino15/packages/esp8266/hardware/esp8266/2.5.2/tools/espota.py

# set ota password, ip address, and port for device
OTAHOSTNAME := $(shell grep OTAHOSTNAME secrets.h | cut -d" " -f3 | awk '{print substr($$0, 2, length($$0) - 2)}')
OTAPASS := $(shell grep OTAPASSWORD secrets.h | cut -d" " -f3 | awk '{print substr($$0, 2, length($$0) - 2)}')
OTAPORT := $(shell grep OTAPORT secrets.h | cut -d" " -f3)
OTAIP := $(shell ping -c1 $(OTAHOSTNAME).local | grep "bytes from" | cut -d " " -f5 | awk '{ print substr($$0, 2) }' | awk '{ print substr( $$0, 1, length($$0)-2 ) }')

# ota firmware flasher and flags
UPLOAD_OTA = python2 $(ESPOTATOOL)
UPLOAD_OTA_FLAGS = -d -i $(OTAIP) -p $(OTAPORT) -a $(OTAPASS) -f $(PROG).$(VAR).bin

#-------------------------------------------------------------------------------


# explicitly declare these target to be phony
.PHONY: help build upload upload-ota clean erase size

all: build upload                               # build and then upload via usb

all-ota: build upload-ota                       # build and then upload via ota

help:
	@echo ' '
	@echo 'Makefile for ntp-clock'
	@echo ' '
	@echo 'Usage:'
	@echo '   make              create all files and flash device via usb'
	@echo '   make all          create all files and flash device via usb'
	@echo '   make all-ota      create all files and flash device via ota'
	@echo '   make build        compile the code and create the *.elf file'
	@echo '   make upload       create the *.bin file and flash device via usb'
	@echo '   make upload-ota   create the *.bin file and flash device via ota'
	@echo '   make erase        erease the entire flash from the device and exit'
	@echo '   make size         print the flash size within the device and exit'
	@echo '   make clean        delete *.bin, *.elf, *.hex files'
	@echo '   make help         print this help message and exit'
	@echo ' '
	@echo 'Pass the option "--debug" to enable trace messaging (e.g. make --debug build)'
	@echo ' '

build:                                          # build the binary executable
	$(CC) $(CC_FLAGS) $(CURDIR)

upload:                                         # flash the binary executable via usb
	$(UPLOAD_USB) $(UPLOAD_USB_FLAGS) $(CURDIR)

upload-ota:                                     # flash the binary executable via ota
	@echo VAR = $(VAR)
	@echo OTAIP = $(OTAIP)
	@echo OTAPASS = $(OTAPASS)
	@echo OTAPORT = $(OTAPORT)
	@echo OTAHOSTNAME = $(OTAHOSTNAME)
	@echo UPLOAD_OTA_FLAGS = $(UPLOAD_OTA_FLAGS)
	$(CURDIR)/answerbot $(OTAIP) 23             # using telnet, reboot the device to do OTA
	sleep 10                                    # wait until device is ready for OTA start
	$(UPLOAD_OTA) $(UPLOAD_OTA_FLAGS)

erase:                                          # erase the entire flash
	$(ESPTOOL) erase_flash --port $(PORT)

size:                                           # determine the flash size
	$(ESPTOOL) flash_id --port $(PORT)

clean:                                          # delete all binaries and object files
	rm -r --force $(BUILD) *.bin *.elf *.hex
```

#### Step 2: Compile & Upload Sketch - DONE
With the Makefile encoding all the details of how to build your sketch,
you have a simple process to build and upload your firmware to the NodeMCU board:

```bash
# go to your test sketch
cd ~/tmp/ntp-clock

# create your Makefile using the block of code in Step 1

# compile the sketch
make build

# upload the sketch
make upload
```



[01]:http://playground.arduino.cc/Learning/Linux
[02]:http://www.mjoldfield.com/atelier/2009/02/arduino-cli.html
[03]:https://www.arduino.cc/en/main/software
[04]:http://playground.arduino.cc/Interfacing/LinuxTTY
[05]:http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/
[06]:http://www.gnu.org/software/screen/manual/screen.html#Overview
[07]:http://linux.die.net/man/1/cu
[08]:http://www.computerhope.com/unix/screen.htm
[09]:https://www.arduino.cc/en/Guide/Linux
[10]:https://www.intorobotics.com/alternatives-standard-arduino-ide-one-choose/
[11]:https://learn.sparkfun.com/tutorials/what-is-an-arduino
[12]:https://www.arduino.cc/en/Main/Software
[13]:https://blog.arduino.cc/2018/08/24/announcing-the-arduino-command-line-interface-cli/
[14]:https://github.com/arduino/arduino-cli
[15]:https://www.gnu.org/software/make/
[16]:https://www.microchip.com/design-centers/32-bit/sam-32-bit-mcus/sam-d-mcus
[17]:https://github.com/thunderace/Esp8266-Arduino-Makefile
[18]:https://learn.adafruit.com/adafruit-all-about-arduino-libraries-install-use/arduino-libraries
[19]:https://www.arduino.cc/en/hacking/preferences
[20]:https://gist.github.com/jeffskinnerbox/d74f518157c28dc2dac3297095417447
[21]:https://www.youtube.com/watch?v=TTiQR_4edXw
[22]:https://frightanic.com/iot/interview-ivan-grokhotkov-espressif/
[23]:https://www.arduino.cc/en/Guide/Linux
[24]:https://pypi.org/project/esptool/
[25]:https://flyingcarsandstuff.com/2017/11/make-building-avr-and-arduino-firmware-on-the-command-line/
[26]:https://hackaday.com/2015/10/01/arduino-development-theres-a-makefile-for-that/
[27]:https://github.com/plerup/makeEspArduino/blob/master/README.md
[28]:https://github.com/plerup/makeEspArduino
[29]:https://medium.com/rungo/everything-you-need-to-know-about-packages-in-go-b8bac62b74cc
[30]:https://medium.com/rungo/working-in-go-workspace-3b0576e0534a
[31]:https://golang.org/
[32]:https://github.com/esp8266/Arduino
[33]:https://learn.sparkfun.com/tutorials/esp8266-thing-hookup-guide/installing-the-esp8266-arduino-addon
[34]:https://arduino-esp8266.readthedocs.io/en/2.4.2/#
[35]:https://wellys.com/posts/esp32_cli/
[36]:
[37]:
[38]:
[39]:
[40]:

