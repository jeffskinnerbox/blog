<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------



# ESP32C3-Powered ePaper Dashboard / Display
Convert an IKEA RIBBA 5×7" picture frame into an ePaper dashboard for a Home Assistant smarthome.

* [Nerdiy's 3D-Printed Framework Turns an IKEA RIBBA Into a Seeed XIAO ESP32C3-Powered ePaper Dashboard](https://www.hackster.io/news/nerdiy-s-3d-printed-framework-turns-an-ikea-ribba-into-a-seeed-xiao-esp32c3-powered-epaper-dashboard-3d09f96f7936)
  * [Ikea Ribba eInk frame insert for 5″x7″ picture frames - 3D printable - STL files](https://nerdiy.de/en/product-2/eink-frame-insert-suitable-for-ikea-ribba-5x7-picture-frame-3d-printable-stl-files/)
  * [eInk Frame Insert suitable for Ikea Ribba 5″x7″ picture frame](https://github.com/Nerdiyde/ESPHomeSnippets/tree/main/Snippets/eInk_frame_insert_ribba_5inchX7inch)
  * [RIBBA Frame 5x7"](https://www.ikea.com/us/en/p/ribba-frame-black-50378448/)
  * [Americanflat 5x7 Picture Frame in Black](https://www.amazon.com/Americanflat-Picture-Frame-Black-Built/dp/B0CMC9232L/)



* [Displays We Love Hacking: SPI and I2C](https://hackaday.com/2023/12/21/displays-we-love-hacking-spi-and-i2c/)



# Display Types


# Power Consumption

* [How much current do OLED displays use?](How much current do OLED displays use?)


## LED Matrix
I choose one of the many versions of the [MAX7219 dot matrix module][08]
8x8 dot matrix common cathode LED display modules for my display.
I Choose this because of the because of its modest size
(Module size = length x width x height = 12.8 x 3.2 x 1.3 cm),
low working voltage (5V),
and you can chain 2 or more together to create a [scrolling display][10].
I specific used the MAX7219 Dot Matrix Module 4-in-1 Display
(at [Amazon][06] or much cheaper at [Banggood][07] and where I got mine).


## OLED Display
An organic light-emitting diode (OLED or Organic LED),
also known as an organic EL (organic electroluminescent) diode,
is a light-emitting diode (LED) containing an electroluminescent
film of organic compound that emits light in response to an electric current.
nk

OLEDs are used to create digital displays in devices such as television screens,
computer monitors, smartphones, etc.
OLEDs can be made flexible and transparent, with transparent displays being used in smartphones
with optical fingerprint scanners and flexible displays being used in foldable smartphones.

An OLED display works without a backlight because it emits visible light.
Thus, it can display deep black levels and can be thinner and lighter than a liquid crystal display (LCD).
In low ambient light conditions, an OLED screen can achieve a higher contrast ratio than an LCD.

* [0.96 Inch OLED Module 12864 128x64 Yellow Blue SSD1306 Driver I2C Serial Self-Luminous Display Board](https://www.amazon.com/gp/product/B072Q2X2LL/ref=ppx_od_dt_b_asin_title_s00)
* [UCTRONICS 0.96 Inch OLED Module 12864 128x64 Yellow Blue SSD1306 Driver I2C Serial Self-Luminous Display Board for Arduino Raspberry PI](https://www.uctronics.com/display/uctronics-0-96-inch-oled-module-12864-128x64-yellow-blue-ssd1306-driver-i2c-serial-self-luminous-display-board-for-arduino-raspberry-pi.html)
* [Interface OLED Graphic Display Module with ESP8266 NodeMCU](https://lastminuteengineers.com/oled-display-esp8266-tutorial/)

<https://www.waveshare.com/0.96inch-OLED-A.htm>
<https://www.waveshare.com/0.96inch-OLED-B.htm>


## OLED Display Emulator
Arduino OLED display emulator shows graphics and text on your computer screen.

* [OLED Display… on Your Monitor](https://www.hackster.io/news/oled-display-on-your-monitor-73abb411b4ed)


### HDMI

* [Making Your Own Technically-HDMI OLED Monitor](https://hackaday.com/2022/04/01/making-your-own-technically-hdmi-oled-monitor/)


### Volumetric OLED Display

* [Volumetric OLED Display Shows Bladerunner Vibe, Curious Screen Tech](https://hackaday.com/2021/03/04/volumetric-oled-display-shows-bladerunner-vibe-curious-screen-tech/)
* [OLED Display Kicks Knob Up Several Accurate Notches](https://hackaday.com/2022/04/19/oled-display-kicks-knob-up-several-accurate-notches/)


## E-Paper / E-Ink Display
Electronic paper, as that display tech is known (E Ink is a trademarked term owned by the company named E Ink, the tech's leading purveyor), has always been associated primarily with the Kindle and its ilk.

* [Raspberry Pi PaperPi App Offers Cool E-Ink Display Tools](https://www.tomshardware.com/news/raspberry-pi-paperpi-eink-tools)
* [How to Make a Name Badge with Tricolor E-Ink Display](https://www.hackster.io/Lover/how-to-make-a-name-badge-with-tricolor-e-ink-display-073acb)
* [DIY Air Quality Sensor](https://hackaday.com/2021/07/05/diy-air-quality-sensor/)
* [DESK OF LADYADA - Fast partial updates on an E-Ink - starring QT Py!](https://www.youtube.com/watch?v=3sYBws3-OoU)
* [Color E-Ink Display Photo Frame Pranks](https://hackaday.com/2020/10/30/color-e-ink-display-photo-frame-pranks-mom/)
* [Waveshare 2.9 Inch E-Paper Raw Display Panel 296x128 Resolution 3.3V E-Ink Electronic Paper Screen with Embedded Controller SPI Interface Support Partial Refresh](https://www.amazon.com/gp/product/B072J2LG8N/ref=ppx_od_dt_b_asin_title_s00)
* [$25 TTGO T5 4.7-inch e-Paper Display comes with ESP32 WiFi & Bluetooth SoC](https://www.cnx-software.com/2020/12/04/ttgo-t5-4-7-inch-e-paper-display-comes-with-esp32-wifi-bluetooth-soc/)
* [Low Power eInk Weather Gadget](https://developer.run/52)
* [The Slowest Video Player with 7-Colors!](https://hackaday.io/project/177197-the-slowest-video-player-with-7-colors)
* [This Large Raspberry Pi-Powered E Ink Calendar Ensures You'll Never Forget an Important Date Again](https://www.hackster.io/news/this-large-raspberry-pi-powered-e-ink-calendar-ensures-you-ll-never-forget-an-important-date-again-8745275164e6)

* [Inky wHAT (ePaper/eInk/EPD) – Red/Black/White](https://shop.pimoroni.com/products/inky-what?variant=13590497624147)
* [Inky Impression 5.7" (7 colour ePaper/eInk HAT)](https://shop.pimoroni.com/products/inky-impression-5-7)
* [Pimoroni's Inky Impression Is a 5.7" Seven-Color E Ink Display for the Raspberry Pi and Compatibles](https://www.hackster.io/news/pimoroni-s-inky-impression-is-a-5-7-seven-color-e-ink-display-for-the-raspberry-pi-and-compatibles-e20b7026a9d3)
* [Inky Frame 7.3" (Pico W Aboard)](https://shop.pimoroni.com/products/inky-frame-7-3)

* [A Handy Breakout Board For E-Paper Hacking](https://hackaday.com/2022/06/15/a-handy-breakout-board-for-e-paper-hacking/)


# InkPlate 6

* [InkPlate 6](https://www.crowdsupply.com/e-radionica/inkplate-6)
* [Review: Inkplate 6PLUS](https://hackaday.com/2021/06/21/review-inkplate-6plus/)
* [Inkplate Comes Full Circle, Becomes True Open Reader](https://hackaday.com/2021/08/20/inkplate-comes-full-circle-becomes-true-open-reader/)
* [E-Paper Picture That Changes for My Mom](https://www.youtube.com/watch?v=YawP9RjPcJA)

You can find technical information at the [Waveshape Wiki](https://www.waveshare.com/wiki/Main_Page)

* [Waveshare Universal e-Paper Raw Panel Driver Shield for Raspberry Pi](https://www.amazon.com/gp/product/B075R55WQT/ref=ppx_od_dt_b_asin_title_s00)
* [E-Paper Driver HAT](https://www.waveshare.com/wiki/E-Paper_Driver_HAT)
* [2.9inch e-Paper Module](https://www.waveshare.com/wiki/2.9inch_e-Paper_Module)
* [E-Paper ESP8266 Driver Board](https://www.waveshare.com/wiki/E-Paper_ESP8266_Driver_Board)
* [Collin's Lab: Eink, Think Ink - the full series!](https://www.youtube.com/watch?v=eipKg2pUQ_8)


### E-Paper Templates

* [Templateize Your Timetable With EPaper Templates](https://hackaday.com/2020/12/02/templateize-your-timetable-with-epaper-templates/)


## Wio Terminal
The [Wio Terminal](https://www.seeedstudio.com/Wio-Terminal-p-4509.html)
Compatible with Arduino and MicroPython, Wio Terminal is an ATSAMD51-based microcontroller with wireless connectivity supported by Realtek RTL8720DN. Its CPU speed runs at 120MHz (Boost up to 200MHz). Realtek RTL8720DN chip supports both Bluetooth and Wi-Fi providing the backbone for IoT projects. The Wio Terminal itself is equipped with a 2.4” LCD Screen, onboard IMU(LIS3DHTR), Microphone, Buzzer, microSD card slot, Light sensor, and Infrared Emitter(IR 940nm).

* [Why I'm Never Buying an Arduino Again: The Wio Terminal](https://www.youtube.com/watch?v=K4Irg3N7iLM)
* [Is The Wio Terminal Any Good? Getting Started + Bug Workaround](https://www.youtube.com/watch?v=pX_8mE53En4)

* [Wio Terminal Blog](https://www.seeedstudio.com/blog/tag/wio-terminal/)
* [Wio Terminal Classroom](https://www.youtube.com/playlist?list=PLpH_4mf13-A0MzOdPNITVfoVBMvf7Rg9g)
* [Wio Terminal Wiki](https://wiki.seeedstudio.com/Wio-Terminal-Getting-Started/)


# FontEdit

* [Give LEDs, LCDs, and ePaper Displays Custom Fonts with FontEdit](https://www.hackster.io/news/give-leds-lcds-and-epaper-displays-custom-fonts-with-fontedit-69709666f710)
* [FontEdit - a custom font editor for LCD, LED and E-Paper displays](https://kapusta.cc/2020/03/20/fontedit/)


# Using Raspberry Pi

* [3.5" SPI LCD experiments on Raspberry Pi Zero](https://medium.com/swlh/3-5-spi-lcd-experiments-on-raspberry-pi-zero-b09fa8adb5c)


# Using ESP8266 & ESP32


# Using MicroPython
OLED screen demo on ESP32 with MicroPython - <https://gist.github.com/laurivosandi/1dcc68aa1e665336f4867a4d81ce64b7>


# Round Displays

* [Exotic Round Displays and How to Use Them](https://www.youtube.com/watch?v=eJBDXjI5Zu4)



[01]:
[02]:
[03]:
[04]:
[05]:
[06]:https://www.amazon.com/WMYCONGCONG-MAX7219-Display-Arduino-Microcontroller/dp/B07FT6MZ7R/Dref=asc_df_B07FT6MZ7R/
[07]:https://www.banggood.com/3Pcs-MAX7219-Dot-Matrix-Module-4-in-1-Display-Screen-For-Arduino-p-1230975.html
[08]:https://www.openimpulse.com/blog/products-page/product-category/max7219-led-dot-matrix-module/
[09]:
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

