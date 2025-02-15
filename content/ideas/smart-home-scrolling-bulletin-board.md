<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>

---------------

# Recorded Sound for Announcements

Dfrobot Voice Prompt Module with Integrated MP3 Player and Speaker

* [Dfrobot Voice Prompt Module](https://www.dfrobot.com/product-2862.html)
  * [Module Makes Noisy Projects Easy](https://hackaday.com/2024/10/16/module-makes-noisy-projects-easy/)

[LED Matrix Displays](https://www.amazon.com/s?k=Matrix+LED)
<https://hackaday.io/project/164444-very-large-led-display>
<https://pucktronics.com/build-a-monster-32-by-16-feet-led-matrix-wall-for-low-cost-part-1/>

################################ CHECK THIS OUT ################################

Pipe data to display via   echo -n "24,116" | nc -b -w 0 -u 192.168.1.196 1337
example code for ESP8266 - <https://cdn.hackaday.io/files/1705007294672000/esp8266_display.ino>

[Configure RSS Feed in Homer Dashboard with Node Red](https://smarthomepursuits.com/configure-rss-feed-in-homer-dashboard-with-node-red/)

################################ CHECK THIS OUT ################################

I'm in search of a simple scheme to collect data from a device,
typically to be stored for later analysis
but occasionally to trigger some action.
Less commonly, I’ll need a device to change its behavior
based on instructions received via the Internet.
I also want a simple why for these devices to inform me
of some critical state they my have detected
(e.g. such as water under the kitchen sink).

My first thought is to use IoT frameworks like [Adafruit IO][01],
[Thingsboard][02], [Ubidots][03], [openHAB][04], [Home Assistant][05], and the list goes on.
They have the advantage of being easy to use, and have rich features.
They can even react to data and send instruction back to devices.
But these environments are purposed built platforms, at leas to some extent.
I want the flexibility to modify a type of data for storage,
or to apply processing to the data,
or I need a device to request data that is private or that no one is presently offering.
At these times it’s useful to be able to build simple,
short-lived services that fill in these gaps during prototyping.
Far from being a secure or consumer-ready product,
I just need something we can try out to see if an idea is worth developing further.

* [WebtoPy](https://hackaday.com/2019/02/21/building-a-simple-python-api-for-internet-of-things-gadgets/)
* Node Red
* Mosquitto MQTT

Then there is the topic of a dashboard and notifications to provide status to me.

* Scrolling Dashboard
  * Make it a device connected with Home Assistant - /home/jeff/blogging/content/ideas/getting-started-with-home-assistant.md
* Alexa / Google
  * Include a speaker and Google Assistant - /home/jeff/blogging/content/ideas/google-aiy-projects.md
* Telegram
* Speaker
  * Use a speaker, send it text-to-speach - /home/jeff/blogging/content/articles/speech-synthesis-on-the-raspberry-pi.md
  * Use IBM's [Watson to turn speech to text](https://www.ibm.com/cloud/watson-speech-to-text)
  * [Offline Speech-to-Text on Raspberry Pi 5](https://www.crowdsupply.com/anavi-technology/anavi-dev-mic/updates/video-tutorial-offline-speech-to-text-on-raspberry-pi-5-with-anavi-dev-mic)
    * [Offline Speech-to-Text on Raspberry Pi 5 with Python3 and OpenAI Whisper ASR](https://www.youtube.com/watch?v=XzCWIGtRq4g)
  * [Build Your Own Smart Home Speaker With ESPHome!](https://www.youtube.com/watch?v=4DQ9iyV3G20)
  * Clone a voice pattern to use with speaker - /home/jeff/blogging/content/ideas/voice-cloning.md
  * Make the speaker into an intercom via Mumble - /home/jeff/blogging/content/ideas/raspberry-pi-zero-walkie-talkies-via-mumble.m

Native Informational Features

* Accurate Clock refresh off Internet Time Servers
* Local Weather and conditions (refreshed every 10 - 30 minutes)
* News Headlines from all the major sources

# Node Red MQTT on the Raspberry Pi

* [Node Red MQTT on the Raspberry Pi](https://www.youtube.com/watch?v=WxUTYzxIDns&feature=youtu.be)
* [#125 MQTT meets SONOFF: QoS, Last Will, Keep-Alive, etc. explained and shown](https://www.youtube.com/watch?v=fwb5YAPzPGk&t=19s)
* [#126 Cheap MQTT Broker on Raspberry Zero W / DietPi / MQTT Message Logger SQlite / PHPliteAdmin](https://www.youtube.com/watch?v=bpg6RSHS4Zc&feature=youtu.be)
* [#127 Home Automation without coding: Sonoff , MQTT,Alexa, Nod-Red](https://www.youtube.com/watch?v=QU24kMqpFdY&feature=youtu.be)
* [#128 Node-Red Tricks for Home Automation (JS, Audio, SQlite, Alexa, Mosq...](https://www.youtube.com/watch?v=YahFRqf-rFA&feature=youtu.be)

# Give it a Voice

## Give it a Voice via Amazon Polly

* [Amazon Polly Tutorial | How to convert Text to Speech using AWS Polly](https://www.youtube.com/watch?v=ywpPZE6Gd80)
* [The No Voice Assistant: You Can Now Text Alexa](https://www.makeuseof.com/you-can-now-text-alexa/)

## Give it a Voice via Serial Speech Synthesizer SAM

* [Classic 80s Text-To-Speech On Classic 80s Hardware](https://hackaday.com/2021/10/26/classic-80s-text-to-speech-on-classic-80s-hardware/)
* [SSSSAM](https://github.com/JanDerogee/SerialSpeechSynthesizerSAM)
* [ESP8266SAM](https://github.com/earlephilhower/ESP8266SAM)
* [Retro Speech Synthesis. Part : 12 IoT, Home Automation](https://www.instructables.com/Retro-Speech-Synthesis-Part-12-IoT-Home-Automation/)
* [EMIC 2 Text-to-Speech Module](https://duino4projects.com/emic-2-text-speech-module/)
* [DECtalk](https://en.wikipedia.org/wiki/DECtalk)
* [80speak](https://github.com/connornishijima/80speak)
* ["Perfect Paul" is Stephen Hawking's voice](https://www.wired.com/2015/01/intel-gave-stephen-hawking-voice/)
* [eSpeak](https://en.wikipedia.org/wiki/ESpeak) is a compact open source software speech synthesizer for Linux, Windows, and other platforms

* [Text-to-Speech Model Can Do Music, Background Noises, and Sound Effects](https://hackaday.com/2023/07/24/text-to-speech-model-can-do-music-background-noises-and-sound-effects/)

## Other Options

* [RPi Python Library Has Retro Chiptunes And Speech Covered](https://hackaday.com/2021/09/09/rpi-python-library-has-retro-chiptunes-and-speech-covered/)
* Check out your document - /home/jeff/blogging/content/articles/speech-synthesis-on-the-raspberry-pi.md

---------------

# Alternative Physical Design of Display

* [AI-Powered Bumper Sticker Provides Context-Sensitive Urban Camouflage](https://hackaday.com/2024/02/14/ai-powered-bumper-sticker-provides-context-sensitive-urban-camouflage/)
* [GitHub: PegorK/smahtSticker](https://github.com/PegorK/smahtSticker/tree/main)

---------------

# Physical Design of Display

Thing to watchout for:

* Watch the wire lengths. Long wires are fine when testing one of two modules on a protoboard, but when chaining more than 10 of these MAX7219 modules, the noise/distorsion introduced by the wires is enough to corrupt the data arriving at the last modules.
* Using “common rails” for CLK and CS worked better than daisy-chaining the signals from the output of one module to the input of the next.
* Estimate the power consumption beforehand.
* Triple check the wiring before applying power. I burned two MAX7219 along the course of the project.
* When possible, use HW-supported SPI communication instead of SW bit-banged SPI, for (much) faster communication.
* Adding Bluetooth communication to an Arduino project is quite straightforward, and not that expensive.

* [Long chain of MAX7219 Matrix displays Fail](https://forum.allaboutcircuits.com/threads/long-chain-of-max7219-matrix-displays-fail.151773/)
* [LED Matrix Strip](http://jheyman.github.io/blog/pages/LEDMatrixStrip/)
* [MAX7219 LED Matrix 4 in 1 module (8x32) - how many can daisy-chain?](https://forum.arduino.cc/index.php?topic=565612.0)
* [MAX7219 and 8x8 LED matrix modules - Measured current used](https://forum.arduino.cc/index.php?topic=301955.0)

## SPI Communication

Lift text from here - <http://jheyman.github.io/blog/pages/LEDMatrixStrip/>

## Power

Lift text from here - <http://jheyman.github.io/blog/pages/LEDMatrixStrip/>

---------------

# Software Design of Display

I choose one of the many versions of the [MAX7219 dot matrix module][08]
8x8 dot matrix common cathode LED display modules for my display.
I Choose this because of the because of its modest size
(Module size = length x width x height = 12.8 x 3.2 x 1.3 cm),
low working voltage (5V),
and you can chain 2 or more together to create a [scrolling display][10].
I specific used the MAX7219 Dot Matrix Module 4-in-1 Display
(at [Amazon][06] or much cheaper at [Banggood][07] and where I got mine).

## Library for Scrolling LED Matrix Displays

The key library to be installed is the [Marco Colli's MajicDesigns MD_Parola][09] library.
You can see how this is done below:

```bash
# update package index of cores
$ arduino-cli core update-index
Updating index: package_index.json downloaded

# example search for a library
$ arduino-cli lib search parola

Name: "MD_Parola"
  Author:  majicDesigns
  Maintainer:  marco_c <8136821@gmail.com>
  Sentence:  LED matrix text display special effects
  Paragraph:  Implemented using the MD_MAX72xx library for hardware control. Provides functions to simplify the implementation of text special effects on the LED matrix.
  Website:  https://github.com/MajicDesigns/MD_Parola
  Category:  Display
  Architecture:  *
  Types:  Contributed
  Versions:  [2.2.0, 2.5.0, 2.6.1, 2.6.2, 2.6.4, 2.6.5, 2.6.6, 2.7.0, 2.7.1, 2.7.2, 2.7.3, 2.7.4, 3.0.0, 3.0.1, 3.0.2]

# install the desired library
$ arduino-cli lib install MD_Parola@3.0.2 MD_MAX72XX@3.0.2
MD_Parola@3.0.2 downloaded
Installed MD_Parola@3.0.2
```

# Step X: XXX

* [Parola_Scrolling_ESP8266.ino](https://github.com/MajicDesigns/MD_Parola/blob/master/examples/Parola_Scrolling_ESP8266/Parola_Scrolling_ESP8266.ino)

# Parola Library Documentation

[Parola for Arduino  3.0: Text effects for LED Matrix modular hardware](https://majicdesigns.github.io/MD_Parola/)

* [Parola A to Z – Text Animation](https://arduinoplusplus.wordpress.com/2017/02/10/parola-a-to-z-text-animation/)
* [Parola A to Z – Double Height Displays](https://arduinoplusplus.wordpress.com/2017/03/15/parola-a-to-z-double-height-displays/)
* [Parola A to Z – Adapting for Different Hardware](https://arduinoplusplus.wordpress.com/2017/04/14/parola-a-to-z-adapting-for-different-hardware/)
* [Parola A to Z – Multi Zone Displays](https://arduinoplusplus.wordpress.com/2017/04/18/parola-a-to-z-multi-zone-displays/)
* [Parola A to Z – Vertical Displays](https://arduinoplusplus.wordpress.com/2017/07/22/parola-a-to-z-vertical-displays/)
* [Parola A to Z – RAM Requirements](https://arduinoplusplus.wordpress.com/2017/08/27/parola-a-to-z-ram-requirements/)

* [Parola A to Z – Optimizing Flash Memory](https://arduinoplusplus.wordpress.com/2018/09/23/parola-a-to-z-optimizing-flash-memory/#more-9486)
* [Parola A to Z – Sprite Text Effects](https://arduinoplusplus.wordpress.com/2018/04/19/parola-a-to-z-sprite-text-effects/)
* [Parola A to Z – Defining Fonts](https://arduinoplusplus.wordpress.com/2016/11/08/parola-fonts-a-to-z-defining-fonts/)
* [Parola A to Z – Mixing Text and Graphics](https://arduinoplusplus.wordpress.com/2018/03/29/parola-a-to-z-mixing-text-and-graphics/)

Text sprites Examples

* [Parola for Arduino 2.0 - LED Matrix with MAX7219 controller](https://www.youtube.com/watch?v=u1iELyROjW8)
* [Parola Sprites](https://www.youtube.com/watch?v=tfwAHx0MTxU)
* <https://www.makerguides.com/max7219-led-dot-matrix-display-arduino-tutorial/>
* <https://www.teachmemicro.com/max7219-cascaded-dot-matrix-module/>
* Library for modular scrolling LED matrix text displays - <https://github.com/MajicDesigns/MD_Parola>

## Test Code - Scrolling Text

* [Library for modular scrolling LED matrix text displays](https://github.com/MajicDesigns/MD_Parola)

## Rotary Encoder Control

* [ESP8266 Peripherals: KY-040 Rotary Encoder](https://blog.squix.org/2016/05/esp8266-peripherals-ky-040-rotary-encoder.html)
* [ESPRotary](https://github.com/LennartHennigs/ESPRotary)

* [A Tiny Knob Keeps You In Control](https://hackaday.com/2024/08/11/a-tiny-knob-keeps-you-in-control/)
  * [ATtiny85 TinyKnob](https://hackaday.io/project/171754-attiny85-tinyknob)
  * [CH32X033 USB Knob:Rotary Encoder with USB Interface and NeoPixels](https://hackaday.io/project/195160-ch32x033-usb-knob)
  * [CH32V003 USB Joystick: Simple Joystick with USB Interface](https://hackaday.io/project/196635-ch32v003-usb-joystick)

## Voltage Supervisor

Frequently, when I power on the scrolling display,
the display initializes such that some of the LED matrices are lite
or individual LEDs are randomly lite.
This is most likely caused at power up as the voltage rises and passes through the
low voltage range of the ESP8266 MCU, where it is unstable.
To avoid this instability, you need to keep the resent pin to 0V
until a stable 3.3Vcc voltage is reached.

This problem can be solved with a [voltage supervisor](https://training.ti.com/what-voltage-supervisor).

* [How to use Voltage Supervisors to protect ESP32, Raspberry Pi, and Batteries](https://www.youtube.com/watch?v=cKDv0aN67BY)

---------------

# Properly Powering the Display

I was having problems getting my scrolling display working properly and I had strong a strong feeling that the current I was attempting to pull from the USB powered ESP8266  was excessive

0.5A current draw from the ESP8266

Most computer USB 2.0 ports supply 5V of electricity with a maximum current of 0.5A. This amount of current is standard across the majority of computers and means the overall power output will be 2.5 Watts at best. USB 3.0 stamdard bring that current up to 0.9A. ([source](https://www.cmd-ltd.com/advice-centre/usb-chargers-and-power-modules/usb-and-power-module-product-help/usb-charger-faqs/))

The [MAX7219 datasheet](https://www.sparkfun.com/datasheets/Components/General/COM-09622-MAX7219-MAX7221.pdf) states that: Operating Supply Current: TYP 330 mA
Some have measure better values (200 mA) - <https://forum.arduino.cc/index.php?topic=301955.msg2100717#msg2100717>

* [MAX7219 and LED matrix power requirements](https://arduinoplusplus.wordpress.com/2015/09/12/max7219-and-led-matrix-power-requirements/)

* [LED Matrix Strip](http://jheyman.github.io/blog/pages/LEDMatrixStrip/)

[MAX7219 LED Matrix 4 in 1 module (8x32) - how many can daisy-chain?](https://forum.arduino.cc/index.php?topic=565612.15)

[How to properly power the ESP8266 modules](https://www.youtube.com/watch?v=wf_msvWv1jk)
[Nodemcu ESP8266: Nodemcu Power Supply, Nodemcu 12v Power supply, ESP8266 power supply](https://www.youtube.com/watch?v=3TlzoF0YpH8)

---------------

# Scrolling Sign

Example builds

* [Marquee Scroller (Clock, Weather, News, and More)](https://github.com/Qrome/marquee-scroller)
* [WMYCONGCONG MAX7219 Dot Matrix Module 4 in 1 Display Module for Arduino Microcontroller with 5 Pin Line](https://www.amazon.com/WMYCONGCONG-MAX7219-Display-Arduino-Microcontroller/dp/B07FT6MZ7R/ref=asc_df_B07FT6MZ7R/)
* [WS2812b Pixel Matrix，CHINLY 8x32 256 Pixels WS2812B Digital Flexible LED Panel Programmed Individually addressable Full Dream color lighting DC5V](https://www.amazon.com/Matrix%EF%BC%8CCHINLY-Flexible-Programmed-Individually-addressable/dp/B07418XNJ2/ref=asc_df_B07418XNJ2/)
* Connecting a 16x32 RGB LED Matrix Panel to a Raspberry Pi [Part 1](https://learn.adafruit.com/connecting-a-16x32-rgb-led-matrix-panel-to-a-raspberry-pi/overview) and [Part 2](https://learn.adafruit.com/16x32-rgb-display-with-raspberry-pi-part-2)
* [Morphing Digital Clock](https://www.instructables.com/id/Morphing-Digital-Clock/)
* [The Ultimate Bitcoin Tracker](https://hackaday.io/project/163647-the-ultimate-bitcoin-tracker)
  * [Arduino Tutorial #21 - MAX7219 LED Matrix Display Walkthrough & Test Code - Scrolling Text Code](https://www.youtube.com/watch?v=hH-m0LL_ZAs&feature=youtu.be)
* [Arduino Scrolling Text Bar Tutorial](https://www.youtube.com/watch?v=_SC4VdLBVHY)

* [Build a giant scrolling LED text display for about $15 per foot](https://www.youtube.com/watch?v=k-SYMPO8-f8)
  * [Bigger is better: Build an Arduino-powered monster scrolling LED sign for about $15 a foot](https://wp.josh.com/2016/05/20/huge-scrolling-arduino-led-sign/)
  * [Parallel Processing Arduino Style – Make Massive NeoPixel Displays With Nanoscale Concurrent Computing](https://wp.josh.com/2016/05/04/parallel-processing-arduino-style-make-massive-neopixel-displays-with-nanoscale-concurrent-computing/)
  * [Build a giant scrolling LED text display for about $15 per foot](https://www.youtube.com/watch?v=k-SYMPO8-f8&t=3s)
  * [ALITOVE 12V WS2812B Individually Addressable RGB LED Strip Light, 5m 300 LEDs AL2815 Programmable LED Pixels Light Strip, Signal Break-Point Continuous Transmission, Not Waterproof White PCB](https://www.amazon.com/ALITOVE-Individually-Addressable-Programmable-Transmission/dp/B07D48W1J7/ref=pd_day0_hl_201_6)

* [Samsung’s Family Hub refrigerator](https://news.samsung.com/global/the-new-family-hub-is-the-heart-of-the-connected-home)

# Telegram Bot with ESP8266

* [Telegram Bot with ESP8266](https://www.hackster.io/ShebinJoseJacob/telegram-bot-with-esp8266-dbada8)
* [Talking Telegram with the ESP8266](https://hackaday.com/2019/02/21/talking-telegram-with-the-esp8266/)
* [Using a Telegram Bot and a Demo Board to experiment with home automation](https://www.open-electronics.org/using-a-telegram-bot-and-a-demo-board-to-experiment-with-home-automation/)
* [ESP8266 and Telegram Bot: Home Automation](https://dzone.com/articles/esp8266-and-telegram-bot-home-automation)
* [Telegram: ESP32 Motion Detection with Notifications (Arduino IDE)](https://randomnerdtutorials.com/telegram-esp32-motion-detection-arduino)

# Telegram Bot with Alexa/Echo

* [Alexa skill that connects Amazon Echo with Telegram Messenger](https://devpost.com/software/my-telegrams)
  * [My Telegrams Explained](https://www.youtube.com/watch?v=1j1FhkBDjSo&feature=youtu.be)
* [My Telegrams](https://www.amazon.com/dp/B07GR5LD6M)
* [Talking Telegram with the ESP8266](https://hackaday.com/2019/02/21/talking-telegram-with-the-esp8266/)
* [Quick And Dirty: Operate An Intercom Via Telegram](https://hackaday.com/2019/12/02/quick-and-dirty-operate-an-intercom-via-telegram/)
* [Set Up Telegram Bot on Raspberry Pi](https://www.instructables.com/id/Set-up-Telegram-Bot-on-Raspberry-Pi/)
* [home surveillance monitored via telegram](https://ginolhac.github.io/posts/diy-raspberry-monitored-via-telegram/#communication-with-motion-via-telegram)
* [Creating a Telegram bot with Micronaut](https://dzone.com/articles/creating-a-telegram-bot-with-micronaut)

# Telegram Bot with Google DialogFlow

* [DialogFlow Integration with Telegram](https://medium.com/@hemantjain1999/dialogflow-integration-with-telegram-4048e16397fc)
* [Dialogflow](https://cloud.google.com/dialogflow/)

# Posting Messages via Alexa, Slack, etc

Could we post messages to your message board from anywhere
(e.g. connected devices, web services, Alexa)
and have Alexa read the messages to you?

* [Alexa Message Board (now with Slack!)](https://www.hackster.io/josep-valls/alexa-message-board-now-with-slack-324b84)

# Chirp + Alexa Toolkit

[Chirp](https://chirp.io/) lets your applications send and receive data using sound,
using a device's existing speaker and mic.

* [Chirp + Alexa Toolkit](https://www.hackster.io/ChirpDevs/chirp-alexa-toolkit-818ed9)

# Speaker

* [Thin Speaker - 0.5W](https://www.sparkfun.com/products/15350)

# Debuging Tools

* [RemoteDebug for ESP Platforms](https://hackaday.com/2019/03/07/remotedebug-for-esp-platforms/)

# UI Example to Emulate

* [ESP RFID - Access Control with ESP8266, RC522 PN532 Wiegand RDM6300](https://github.com/esprfid/esp-rfid#esp-rfid---access-control-with-esp8266-rc522-pn532-wiegand-rdm6300)
* [What the Heck is a Progressive Web App (PWA) Anyway?](https://it.toolbox.com/blogs/dennisstevenson/what-the-heck-is-a-progressive-web-app-pwa-anyway-102919)
* [How you can make a progressive web app in an hour](https://medium.freecodecamp.org/how-you-can-make-a-progressive-web-app-in-an-hour-7e36d560610e)
* [Developing Progressive Web Apps (PWAs) Course](https://codelabs.developers.google.com/dev-pwa-training/)

# News and Weather

* Display the day's top headlines using the [New York Times API](https://developer.nytimes.com/)
* [Marquee Scroller (Clock, Weather, News, and More)](https://github.com/Qrome/marquee-scroller)

# Authorization & Configuration Web GUI

* [Marquee Scroller (Clock, Weather, News, and More)](https://github.com/Qrome/marquee-scroller)

# Include Voice Announcements

* [Real-Time-Voice-Cloning](https://github.com/CorentinJ/Real-Time-Voice-Cloning)
* [Resemblyzer](https://github.com/resemble-ai/Resemblyzer)
* [Resemble](https://www.resemble.ai/)

# Send Linux Notifications

* [Send desktop notifications and reminders from Linux terminal](https://opensource.com/article/22/1/linux-desktop-notifications)

# Display Server Attacks

* [Displaying Incoming Server Attacks By Giving Server Logs A Scoreboard](https://hackaday.com/2020/09/23/displaying-incoming-server-attacks/)

---------------

# Controller for the Scroller

* [Knobby](https://github.com/quadule/knobby)
* [Small Spotify Remote Broadens Musical Horizons](https://hackaday.com/2020/10/21/small-spotify-remote-broadens-musical-horizons/)
* [PiAlert – V1](https://nick-web.co.uk/raspberrypi/posts/2020-09-21/pialert)

[01]:https://io.adafruit.com/
[02]:https://thingsboard.io/
[03]:https://ubidots.com/
[04]:https://www.openhab.org/
[05]:https://www.home-assistant.io/
[06]:https://www.amazon.com/WMYCONGCONG-MAX7219-Display-Arduino-Microcontroller/dp/B07FT6MZ7R/Dref=asc_df_B07FT6MZ7R/
[07]:https://www.banggood.com/3Pcs-MAX7219-Dot-Matrix-Module-4-in-1-Display-Screen-For-Arduino-p-1230975.html
[08]:https://www.openimpulse.com/blog/products-page/product-category/max7219-led-dot-matrix-module/
[09]:https://github.com/MajicDesigns/MD_Parola
[10]:https://www.youtube.com/watch?v=i_8tvPwT6OE
[11]:
[12]:
[13]:
[14]:
[15]:
[16]:
[17]:
[18]:
[19]:
[20]:
