<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------



# Teensy 3.2
The [Teensy 3.2][06] is a microcontroller development system,
using the ARM Cortex processors,
where all programming is done via a USB port.
Its compatible with Arduino software & libraries and has
free software development tools including Teensy Loader application
(works with Mac OS X, Linux & Windows).


# Teensy 3.X

* [Teensy 3.5](https://www.sparkfun.com/products/14055?utm_campaign=September+15%2C+2016&utm_source=hs_email&utm_medium=email&utm_content=35839602&_hsenc=p2ANqtz-_u6ZjfDLKRGNuGXIM27xBEjiiruIq3OthnasBlr6PeUld5krSOu7tNKhFFek4XVSRWauD1rvX2vXL29tLTjelNMOj0rg&_hsmi=35839568)
* [Teensy 3.6](https://www.sparkfun.com/products/14057?utm_campaign=September+15%2C+2016&utm_source=hs_email&utm_medium=email&utm_content=35839602&_hsenc=p2ANqtz--YLeNo8yN27XQdXKoYvoc5GLCvJFvVW_Uqy5vjQKlFNHwp5_ETiq7y3BJmyU914Fxa_Jh7cRHpwq__Gw0l-Ci0QGsEjA&_hsmi=35839568)


# Teensy 4.0

* [Teensy 4.0](https://blog.hackster.io/teensy-4-0-brings-600-mhz-cortex-m7-to-the-arduino-world-13d451477918) brings 600 MHz Cortex-M7 offers the best performance per dollar available.
* [New Teensy 4.0 Blows Away Benchmarks, Implements Self-Recovery, Returns To Smaller Form](https://hackaday.com/2019/08/07/new-teensy-4-0-blows-away-benchmarks-implements-self-recovery-returns-to-smaller-form/)
* [CircuitPython Now Working On Teensy 4.0](https://hackaday.com/2020/01/14/circuitpython-now-working-on-teensy-4-0/)
* [Teensy 4 Pushed To The Limit With 1 GHz Overclock](https://hackaday.com/2022/01/02/teensy-4-pushed-to-the-limit-with-1-ghz-overclock/)


# Teensy 4.1

* [Teensy 4.1 Development Board](https://www.pjrc.com/store/teensy41.html)
* [New Teensy 4.1 Arrives with 100 Mbps Ethernet, High-Speed USB, 8 MB Flash](https://hackaday.com/2020/05/11/new-teensy-4-1-arrives-with-100-mbps-ethernet-high-speed-usb-8-mb-flash/)
* [Teensy 4.1 Is the First Arduino-Compatible Board with 100 Mbit Ethernet](https://www.hackster.io/news/teensy-4-1-is-the-first-arduino-compatible-board-with-100-mbit-ethernet-2f4ff34384b6)
* [Teensy 4.1 without Ethernet](https://www.sparkfun.com/products/20359)


## ARM Cortex-M4
The ARM Cortex-M is a group of [32-bit RISC ARM][03] processor cores licensed by [ARM Holdings][02].
The cores are intended for microcontroller use, and consist of
the [ultra-low-power Cortex-M0+ to the top-of-the-range, high-performance Cortex-M7][05].
The [Cortex-M4][04] has been specifically developed for high-performance low-cost devices
for a broad range of Digital Signal Processing (DSP) and embedded controller market.


## Additional Features
The Teensy 3.2 is a step up from previous version of the Teensy family:

* 64K of RAM, 256K of flash memory, and 2K EEPROM
* Teensy 3.2 has a powerful 3.3 volt regulator,
with the ability to directly power ESP8266 Wifi,
WIZ820io Ethernet and other power-hungry 3.3V add-on boards.
* All digital pins are 5 volt tolerant on Teensy 3.2. However,
the analog-only pins (A10-A14), AREF, Program and Reset are 3.3V only.
* 12 Bit DAC analog output and two analog to digital converters inputs


# Getting Started

* [Getting Started](http://www.pjrc.com/teensy/first_use.html)
* [How-To Tips](http://www.pjrc.com/teensy/pins.html)
* [Code Library](http://www.pjrc.com/teensy/usb_debug_only.html)
* [Teensyduino](http://www.pjrc.com/teensy/teensyduino.html)
* [Arduino Libraries](http://www.pjrc.com/teensy/td_libs.html)


# Loading MicroPython Firmware
[MicroPython][01]
[What is MicroPython][02]

<https://learn.adafruit.com/micropython-basics-how-to-load-micropython-on-a-board/overview>


# Picking The Right RTOS

* [Real-Time OS Basics: Picking The Right RTOS When You Need One](https://hackaday.com/2021/02/24/real-time-os-basics-picking-the-right-rtos-when-you-need-one/)
* [Making Sense Of Real-Time Operating Systems In 2024](https://hackaday.com/2024/11/13/making-sense-of-real-time-operating-systems-in-2024/)


# Loading FreeRTOS Firware

* [FreeRTOS on Teensy 3.1](http://rishifranklin.blogspot.com/2014/03/freertos-on-teensy-31.html)
* [FreeRTOS](mavweb.mnsu.edu/hen/lec/FreeRTOS-TaskManagement_p1.pptx)
* [Running the RTOS on a ARM Cortex-M Core](http://www.freertos.org/RTOS-Cortex-M3-M4.html)
* [Using FreeRTOS multi-tasking in Arduino](https://www.hackster.io/feilipu/using-freertos-multi-tasking-in-arduino-ebc3cc)
* [NuttX Real-Time Operating System](http://www.nuttx.org/)
* [What is the NuttX RTOS and why should you care?](https://www.embedded.com/electronics-blogs/say-what-/4458729/What-is-the-NuttX-RTOS-and-why-should-you-care-)
* [New Verizon Developer Toolkit Makes IoT Projects Easy for Amazon Web Services Users](https://iotbusinessnews.com/2018/11/30/27014-new-verizon-developer-toolkit-makes-iot-projects-easy-for-amazon-web-services-users/)

* [Shawn Hymel Presents: Introduction to RTOS](https://www.youtube.com/playlist?list=PLEBQazB0HUyQ4hAPU1cJED6t3DU0h34bz)

* [Zephyr is an open source real-time operating system (RTOS)](https://hackaday.com/2018/04/11/zephyr-adds-features-platforms-and-windows/)
* [The Zephyr Project Welcomes Adafruit Industries to its Open Source Ecosystem](https://blog.adafruit.com/2020/03/02/the-zephyr-project-welcomes-adafruit-industries-to-its-open-source-ecosystem-zephyriot-zephyriot-linuxfoundation-linux-adafruit/)
* [Zephyr 3.4: An RTOS of a Different Stripe](https://www.electronicdesign.com/technologies/embedded/software/article/21273429/electronic-design-zephyr-34-an-rtos-of-a-different-stripe)


# OTA

* [Over the Air Updates for Your Arduino](https://hackaday.com/2018/01/18/over-the-air-updates-for-your-arduino/)



[01]:https://www.micropython.org/
[02]:http://www.arm.com/
[03]:https://en.wikipedia.org/wiki/ARM_architecture
[04]:https://www.arm.com/products/processors/cortex-m/cortex-m4-processor.php
[05]:http://ambiqmicro.com/news/why-choose-arm-cortex-m4-over-m0-wearables-and-iot
[06]:http://www.pjrc.com/teensy/index.html
[08]:
[09]:
[10]:
