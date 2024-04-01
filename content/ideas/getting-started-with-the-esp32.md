<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----



# Choosing an ESP32
* [ESP32 Guide 2024 | Choosing and Using an ESP32 Board](https://www.youtube.com/watch?v=u5unB24lhC4)



# IMPORTANT - ESP32 Bluetooth Vulnerability
* [Bluetooth Vulnerability: Arbitrary Code Execution On The ESP32, Among Others](https://hackaday.com/2021/09/23/bluetooth-vulnerability-arbitrary-code-execution-on-the-esp32-among-others/)






* [9 New ESP32 Boards: Comparison and Tests](https://www.youtube.com/watch?v=mnoZYlyebBc)

* [How to use ESP32 Dual Core with Arduino IDE](https://randomnerdtutorials.com/esp32-dual-core-arduino-ide/)

* [RP2040 vs STM32 vs ESP32 vs ESP8266](https://socialcompare.com/en/comparison/rp2040-vs-stm32-vs-esp32-vs-esp8266)
* [ESP8266 vs ESP32 vs ESP32-S2 vs ESP32-C3](https://socialcompare.com/en/comparison/esp8266-vs-esp32-vs-esp32-s2)


* [Eric N. Shows How OpenCV Can Squeeze Onto an Espressif ESP32, Using Joachim Burket's Shrunken Fork](https://www.hackster.io/news/eric-n-shows-how-opencv-can-squeeze-onto-an-espressif-esp32-using-joachim-burket-s-shrunken-fork-8c73520a6b81)




# ESP-ZeroCode
The first ESP-ZeroCode modules will be offered with either ESP32-C3 (aka ESP8685) or ESP32-C2 (aka ESP8684) WiFi & BLE RISC-V SoCs, or ESP32-H2 802.15.4 & BLE RISC-V microcontroller, and ships with a Matter compatible firmware that enables “near-zero investment in development”. Not it’s not entirely clear whether those are zero-code or just “little-code” (better known as low code) programming devices

The Matter protocol is intended to solve the problem of interoperability for smart home devices. It securely and robustly connects various smart devices with each other across ecosystems, regardless of the manufacturer.

Matter is an application layer protocol that abstracts the underlying connectivity technologies such as Wi-Fi, Thread and Bluetooth LE.

By using a common software stack, device manufacturers who build with Matter will be able to support various smart home ecosystems and voice services. Smart home users will be able to buy any Matter-certified device regardless of their platform of choice.

* [Matter compatible ESP-ZeroCode modules enable plug-and-play automation solutions](https://www.cnx-software.com/2022/11/15/matter-compatible-esp-zerocode-modules-enable-plug-and-play-automation-solutions/)
* [Announcing ESP-ZeroCode Modules for Building Matter-Compatible, Smart-Home Devices with Ease](https://www.espressif.com/en/news/ESP-ZeroCode_Modules)
* [ESP RainMaker Eases Cloud Integration & Mobile App Development for ESP32-S2 SoC](https://www.cnx-software.com/2020/04/19/esp-rainmaker-eases-cloud-integration-mobile-app-development-for-esp32-s2-soc/)
* [Espressif’s Solution for Matter](https://www.espressif.com/en/solutions/device-connectivity/esp-matter-solution)
* [What is ESP RainMaker®?](https://rainmaker.espressif.com/)

# ESP32Console
* [ESP32Console](https://github.com/jbtronics/ESP32Console)

# ESP-EYE
ESP-EYE is a development board for image recognition and audio processing

# ESP32-H2
The ESP32-H2 is a single-core 96MHz RISC-V with built-in IEEE 802.15.4
to support ZigBee 3.x and Thread 1.x.

* [New Part Day: An ESP With ZigBee](https://hackaday.com/2021/08/04/new-part-day-an-esp-with-zigbee/)

# TinyPICO

# ESP32-S2
ESP32-S2 only has a single 32-bit Xtensa core, reduced RAM and ROM,
and WiFi only (no Bluetooth) — compared to the traditional ESP32.
These tradeoffs mean the S2 draws significantly less power consumption, especially while active.

* [#339 The new ESP32-S2: How relevant is it for the Makers? First tests](https://www.youtube.com/watch?v=L6IoSVdKwNM)
* [EYE on NPI - Espressif ESP32-S2 SoC](https://www.youtube.com/watch?v=4F25y-P8krM)
* [ESP32-S2 Processor Datasheet Released, Development Boards Unveiled](https://www.cnx-software.com/2019/09/03/esp32-s2-processor-datasheet-released-development-boards-unveiled/)
* [FeatherS2 Board Brings ESP32-S2 to Adafruit Feather Form Factor](https://www.cnx-software.com/2020/10/05/feathers2-board-brings-esp32-s2-to-adafruit-feather-form-factor/)
* [ESP32-S2 board targets battery-powered applications with 30uA deep sleep power consumption](https://www.cnx-software.com/2020/10/28/esp32-s2-board-targets-battery-powered-applications-with-30ua-deep-sleep-power-consumption/)
* [Test of Battery operated ESP32 Boards (Olimex, TinyPICO, EzSBC, TTGO)](https://www.youtube.com/watch?v=ajt7vtgKNNM)
* [ESP32-S2 New Arduino USB Functionality: Cool Combination with WiFi](https://www.youtube.com/watch?v=XnqDEV21BSA)

# ESP32-S3
The dual-core ESP32-S3 with a clock of 240 MHz is similar to the original and, unlike the S2, has Bluetooth 5 (LE) support. In addition, it has instructions specific to neural networks and signal processing which is helpful in edge machine learning applications.
Other key differences between ESP32-S3 and ESP32 include support for larger capacity and higher-speed SPI flash and PSRAM chips, a few more I/O pints, more security features, a lack of Ethernet MAC, and support for Bluetooth LE 5.0 connectivity with long-range and 2Mbps transfer support.

* [ESP32-S3](https://esp32s3.com/)
* [Unexpected Maker](https://unexpectedmaker.com/esp32s2)
* [Announcing ESP32-S3 for AIoT Applications](https://www.espressif.com/en/news/ESP32_S3)
* [Espressif's New ESP32-S3 Adds AI Features for IoT Devices](https://www.hackster.io/news/espressif-s-new-esp32-s3-adds-ai-features-for-iot-devices-b42b902abdf5)
* [New Part Day: Espressif ESP32-S3](https://hackaday.com/2021/01/09/new-part-day-espressif-esp32-s3/)

## LILYGO T-Camera S3 / ESP32-S3
The T-CAMERA S3 is a compact embedded module based on the low power ESP32-S3 SoC
supporting dual-band WiFi and Bluetooth 5.2.
The device is equipped with an OV2640 camera module,
a 0.96” OLED display, microphone, a PIR sensor,
and a few JST connectors for additional devices.

* ESP32-S3FN16R8 — Dual Core 32-bit LX7 MCU (up to 240MHz); 8MB PSRAM, 16MB Flash; 2.4/5.0GHz WiFi/Bluetooth 5.2
* OLED Display - SSD1306 0.96” OLED display with 128 x 64 resolution, which communicates via I2C protocol.
* OV2640 Camera Module - 3.3V OV2640 module with 1622 x 1200 UXGA resolution (2 Megapixel)
* PIR Sensor - AS312
* USB - one USB type-C for power and serial communications
* Buttons - 1x Power button, 1x Boot button, 1x Reset button
* I/O Interfaces - 1x JST-PH connector 1x JST-GH connector, 1x Microphone, 1x PIR sensor
* Power - AXP2101 PMU for managing the charging of single cell Li-battery

* [LILYGO T-Camera S3: New developer board arrives with ESP32-S3 microcontroller](https://www.notebookcheck.net/LILYGO-T-Camera-S3-New-developer-board-arrives-with-ESP32-S3-microcontroller.676101.0.html)
* [LILYGO T-CAMERA S3 includes display and PIR sensor](https://linuxgizmos.com/lilygo-t-camera-s3-includes-display-and-pir-sensor/)
* [LILYGO T-CAMERA S3 ESP32-S3 PINOUT](https://www.aliexpress.us/item/3256804873501569.html)

* Start Here - [LilyGO Camera S3](https://github.com/Xinyuan-LilyGO/LilyGo-Cam-ESP32S3)
* [Face Detection and Recognition with T-Camera](https://github.com/Xinyuan-LilyGo/esp32-face-recognition)
* [T-Display-S3](https://github.com/Xinyuan-LilyGO/T-Display-S3)
* [LilyGo Camera Series](https://github.com/Xinyuan-LilyGO/LilyGo-Camera-Series)
* [Grove - Vision AI Module with Himax HX6537-A processor, thumb-size AI-powered OV2640 camera sensor, support Yolo V5 and Edge Impulse, easy-to-use](https://www.seeedstudio.com/Grove-Vision-AI-Module-p-5457.html)

# ESP32-C3
When Esspresif introduced the ESP32-C3, it was their first SOM based entirely on the RISC-V architecture. It is a low-cost, single-core SOM with WiFi and Bluetooth support.

The new “C3” variant has a single 160 MHz RISC-V core that out-performs the ESP8266, and at the same time includes most of the peripheral set of an ESP32. While RAM often ends up scarce on an ESP8266 with around 40 kB or so, the ESP32-C3 sports 400 kB of RAM, and manages to keep it all running while burning less power. Like the ESP32, it has Bluetooth LE 5.0 in addition to WiFi.

ESP32-C3 is a single-core WiFi and Bluetooth 5 (LE) microcontroller SoC, based on the open-source RISC-V architecture for secure IoT applications. It strikes the right balance of power, I/O capabilities and security, thus offering the optimal cost-effective solution for connected devices.

* [HANDS-ON: THE RISC-V ESP32-C3 WILL BE YOUR NEW ESP8266](https://hackaday.com/2021/02/08/hands-on-the-risc-v-esp32-c3-will-be-your-new-esp8266/)
* [Getting Started with Seeed Studio XIAO ESP32C3](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/)
* [Seeed Unveils the Compact Matter-Ready XIAO ESP32C6 Dev Board](https://www.hackster.io/news/seeed-unveils-the-compact-matter-ready-xiao-esp32c6-dev-board-a43f5912dd2c)

### Seeeduino XIAO
* [Seeeduino Xiao: Specs, Price, Release & Reviews](https://all3dp.com/2/seeeduino-xiao-review-specs/)
* [Meet the Seeeduino XIAO](https://dronebotworkshop.com/seeeduino-xiao-intro/)
* [Seeed Studio XIAO Series: System-on-Modules (SoM) User Manual](https://files.seeedstudio.com/wiki/XIAO/Seeed-Studio-XIAO-Series-SOM-Datasheet.pdf)
* [IO Expander for XIAO - 16 extra IO, 2 power output, 1 Grove IIC bus port, solder-friendly, configurable IIC address, allowed dual expansion boards working simultaneously](https://www.seeedstudio.com/GPIO-Expander-for-XIAO-p-5795.html)

* [he SMALLEST ESP32 Board 🔥🔥 | Getting Started with XIAO ESP32 C3 | ESP32 Projects](https://www.youtube.com/watch?v=PZZYTYN8hjc)
* [Seeed Studio Launches Compact RISC-V XIAO ESP32-C3 for Battery-Powered Wearable and IoT Projects](https://www.hackster.io/news/seeed-studio-launches-compact-risc-v-xiao-esp32-c3-for-battery-powered-wearable-and-iot-projects-932ba7de4fe9)
* [RISC-V based XIAO ESP32C3 is enabled with Wi-Fi and BLE](https://linuxgizmos.com/risc-v-based-xiao-esp32c3-is-enabled-with-wi-fi-and-ble/)
* [RISC-V: How much is open source? Featuring the new ESP32-C3](https://www.youtube.com/watch?v=VdPsJW6AHqc)
* [XIAO ESP32C3](https://www.cnx-software.com/2022/07/08/seeed-studio-5-xiao-esp32c3-board-wifi-and-ble-battery/)

* [Seeed Studio Teases the Ultra-Compact Edge AI TinyML XIAO ESP32S3 Sense Smart Camera Dev Board](https://www.hackster.io/news/seeed-studio-teases-the-ultra-compact-edge-ai-tinyml-xiao-esp32s3-sense-smart-camera-dev-board-f31af68d5094)




* [ESP32 Videos](https://www.youtube.com/playlist?list=PL3XBzmAj53RnZPeWe799F-uoXERBldhn9)

* [ESP8266 Tips & Tricks](https://www.youtube.com/channel/UCqk4hT4XpzUVVUfsIDNzvPw)
* [My ESP32 videos](https://www.youtube.com/channel/UCu7_D0o48KbfhpEohoP7YSQ)

* [RemoteDebug for ESP Platforms](https://hackaday.com/2019/03/07/remotedebug-for-esp-platforms/)

* [#328 ESP32 Secrets: Interrupts, and Deep-Sleep under the Hood](https://www.youtube.com/watch?v=CJhWlfkf-5M)
* [Unknown ESP32 saving modes: Light Sleep, Clock Reduction, Modem Sleep, Hibernation, and a few tricks](https://www.youtube.com/watch?v=JFDiqPHw3Vc)


* [Using the ESP8266 to build the Internet of Things](https://www.youtube.com/watch?v=CjeDkmm0w_w&app=desktop)
* [The Internet of Things with ESP32](http://esp32.net/)
* [Installing the ESP32 Arduino Core](https://learn.sparkfun.com/tutorials/esp32-thing-hookup-guide#installing-the-esp32-arduino-core)
* [Over-the-air updating an ESP32](https://blog.classycode.com/over-the-air-updating-an-esp32-29f83ebbcca2)
* [Secure over-the-air updates for ESP32](https://blog.classycode.com/secure-over-the-air-updates-for-esp32-ec25ae00db43)
* [ESP32 AT Instruction Set and Examples - Espressif Systems](https://espressif.com/sites/default/files/documentation/esp32_at_instruction_set_and_examples_en.pdf)
* [ESP32, We Have Ways to Make You Talk](https://hackaday.com/2018/02/06/esp32-we-have-ways-to-make-you-talk/)
* [ESP32 Boards With Displays: An Overview](https://hackaday.com/2018/05/23/esp32-boards-with-displays-an-overview/)

* [Face Detection and Recognition on the ESP32](https://blog.hackster.io/face-detection-and-recognition-on-the-esp32-3b4b9a35c765)
* [Espressif IoT Development Framework (ESP-IDF)](https://docs.espressif.com/projects/esp-idf/en/latest/get-started/index.html)
    * [Secure Boot](https://docs.espressif.com/projects/esp-idf/en/latest/security/secure-boot.html)
    * [Flash Encryption](https://docs.espressif.com/projects/esp-idf/en/latest/security/flash-encryption.html)

# ESP32-C5
ESP32-C5 = dual-band WiFi 6 + BLE
* [ESP32-C5 RISC-V IoT MCU supports dual-band WiFi 6, Bluetooth 5.0 LE](https://www.cnx-software.com/2022/06/22/esp32-c5-risc-v-iot-mcu-dual-band-wifi-6-bluetooth-le/)

# ESP32-C6
ESP32-C6 = WiFi 6 + Bluetooth 5 LE
* [Is the new Espressif ESP32-C6 a game changer?](https://www.youtube.com/watch?v=d0dkTFxa3io)
* [ESP32-C6 WiFI 6 and Bluetooth 5 LE RISC-V SoC for IoT devices coming soon](https://www.cnx-software.com/2021/04/11/esp32-c6-wifi-6-and-bluetooth-le-risc-v-soc-for-iot-devices/)
* [ Espressif ESP32-C6 Includes WiFi 6 And A RISC-V Core](https://hackaday.com/2021/04/11/new-part-day-espressif-esp32-c6/)

# ESP32-D

# ESP32-E
ESP32-E, specially designed for IoT, is an ESP-WROOM-32E-based main controller board with dual-core chips.

# ESP32-NOW
https://www.dfrobot.com/blog-1473.html?tracking=60adc151185b6

# ESP32-WROOM
* [SparkFun Thing Plus - ESP32 WROOM](https://www.sparkfun.com/products/15663)
* [SparkFun Thing Plus - ESP32-S2 WROOM](https://www.sparkfun.com/products/17743)

# ESP32-WROOM-DA
The [ESP32-WROOM-DA](https://www.espressif.com/en/news/ESP32-WROOM-DA)
resemblance to the ESP32-WROOM but can deliver better WiFi connectivity.
The clever WiFi trick comes in the form of a pair of antennas at 90 degrees to each other,
allowing it to select whichever antenna gives the best signal at any one time.

* [New Part Day: ESP32-WROOM-DA](https://hackaday.com/2021/05/21/new-part-day-esp32-wroom-da/)

# ESP32-P4
On board are dual-core 400 MHz and a single-core low power 40 MHz RISC-V processors, and an impressive array of hardware peripherals including display and camera interfaces and a hardware JPEG codec alongside the ones you’d expect from an ESP32 part. It’s got a whopping 768 KB of on-chip SRAM as well as 8 K of very fast cache RAM for intensive operations.

* [Espressif Reveals ESP32-P4: A High-Performance MCU with Numerous IO-Connectivity and Security Features](https://www.espressif.com/en/news/ESP32-P4)





# Background
The ESP32 is a low cost, low power microcontroller with integrated 2.4 GHz WiFi (up to 150Mbps)
and dual-mode Bluetooth (classic and BLE),
which employs a dual-core Tensilica Xtensa LX6 microprocessor.
The ESP32 is a successor to the ESP8266 microcontroller,
and like the ESP8266, the ESP32 is created and developed by Espressif Systems,
a Shanghai-based Chinese company.
This chip includes almost everything you’ll need to begin programming the WiFi/Bluetooth SoC
and to create IoT applications.

* ESP32 Key Features
    * 240 MHz dual-core Tensilica LX6 microcontroller with performing at up to 600 DMIPS
    * integrated 520 KB SRAM
    * integrated 802.11/b/g/n HT40 WiFi transceiver,  baseband,  stack and LWIP
    * integrated dual mode Bluetooth (classic and BLE)
    * 16 MB Flash
    * 2.2V to 3.6V operating voltage
    * -40°C to +125°C operating temperature
    * on-board PCB antenna / IPEX connector for external antenna
    * supports sniffer, station, SoftAP and WiFi direct modes
* ESP32 Peripheral Interfaces
    * 12-bit ADC up to 18 channels
    * 2x 8-bit DACs
    * 10x capacitive touch interface
    * Temperature sensor
    * 3x SPI
    * 2x I²S
    * 2x I²C
    * 3x UARTs, including hardware flow control
    * SD/SDIO/MMC host
    * SDIO master/slave 50 MHz
    * Ethernet MAC interface with dedicated DMA and IEEE 1588 support
    * CAN bus 2.0
    * IR (TX/RX)
    * PWM/timer input/output available on every GPIO pin
    * Hall effect sensor
    * Ultra low power and low noise analog amplifier
* ESP32 Security
    * WEP, WPA/WPA2 PSK/Enterprise
    * Hardware accelerated encryption: AES / SHA2 / Elliptical Curve Cryptography / RSA-4096
* ESP32 Performance
    * Max data rate of 150 Mbps@11n HT40, 72 Mbps@11n HT20, 54 Mbps@11g, and 11 Mbps@11b
    * Maximum transmit power of 19.5 dBm@11b, 16.5 dBm@11g, 15.5 dBm@11n
    * Minimum receiver sensitivity of -98 dBm
    * 135 Mbps UDP sustained throughput
    * 2.5 μA deep sleep current
* Resources
    * [ESP32 Datasheet (PDF)](https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_en.pdf)
    * [ESP32 Technical Reference Manual](https://espressif.com/sites/default/files/documentation/esp32_technical_reference_manual_en.pdf)
    * [ESP32 Pinout v1.0]()
    * [ESP32 Pin List]()
    * [ESP32 Hardware Design Guidelines](https://espressif.com/sites/default/files/documentation/esp32_hardware_design_guidelines_en.pdf)
    * [ESP32 RTOS SDK API Reference](https://github.com/espressif/ESP31_RTOS_SDK/tree/master/documents)
    * [ESP32 Other Resources (Espressif/Documentation)](https://espressif.com/en/products/hardware/esp32/resources)
    * [ESP32 Other Resources (esp32.net)](http://esp32.net/)
    * [ESP32 Used As Wireless CAN Bus Reader](https://hackaday.com/2023/11/22/esp32-used-as-wireless-can-bus-reader/)

# Toolchain
The Espressif Internet Development Framework (ESP-IDF) is core development tool-chain for the ESP32 chip. It includes the compiler, programming tools and various software components that enable software development on the chip.

* [How to Get Started with the ESP32](http://hackaday.com/2016/10/04/how-to-get-started-with-the-esp32/)
* [ESP32 Toolchain Setup on Ubuntu](http://iot-bits.com/esp32/esp32-toolchain-setup/)
* [ESP32 – building the toolchain for Linux (Ubuntu)](http://blog.podkalicki.com/esp32-building-the-toolchain-for-linux-ubuntu/)

# Over-The-Air Update (OTA)
* [Library Makes ESP Over the Air Updates Easy](https://hackaday.com/2019/03/21/library-makes-esp-over-the-air-updates-easy/)
* [ESP32 OTA tutorial with tricks (incl. OTA debugging)](https://www.youtube.com/watch?v=1pwqS_NUG7Q)
* [ESP8266 - Pushing OTA Upgrades](http://smallbits.marshall-tribe.net/blog/2016/05/29/esp8266-pushing-ota-upgrades)
* https://www.youtube.com/watch?v=o05sBDfaFO8&index=9&list=PLNOffh-6mSoRfxD4wTvRziUDUiSLSyJKE

# AWS IoT with ESP32 and Mongoose OS
See - https://madcow-public.s3.amazonaws.com/iot_loft_guide.pdf
and - https://www.slideshare.net/AmazonWebServices/rapid-prototyping-with-aws-iot-and-mongoose-os-on-esp8266-esp32-and-cc3200-platforms

Prerequisites
* AWS CLI configured with valid credentials in the AWS account that you intend to use
    * http://docs.aws.amazon.com/cli/latest/userguide/installing.html
* ESP32 Dev board
    * A (good!) USB cable to connect the ESP32 board to your computer
    * mos – The Mongoose OS flashing tool. Download at http://www.mongoose-os.com
* git clone of the Mongoose OS repository from GitHub:
    * git clone https://github.com/

# ESP Security
* [Don’t Toss That Bulb, It Knows Your Password](https://hackaday.com/2019/01/29/dont-toss-that-bulb-it-knows-your-password/)
* [ESP32 Vulnerability Affects Older Chips](https://hackaday.com/2020/09/24/esp32-vulnerability-affects-older-chips/)

# Watchdog Time
* [BASICS OF REMOTE CELLULAR ACCESS: WATCHDOGS](https://hackaday.com/2021/10/14/basics-of-remote-cellular-access-watchdogs/)
* [Preventing Embedded Fails with Watchdogs](https://hackaday.com/2019/01/12/preventing-embedded-fails-with-watchdogs/)
* [ESP32 Technical Tutorials: Watchdog Processing](https://www.youtube.com/watch?v=C2xF3O6qkbg)
* [ESP32 Tutorial - Watchdog Timer](https://www.youtube.com/watch?v=7kLy2iwIvy8)
* [Watchdog Timers in Microcontrollers](https://www.allaboutcircuits.com/technical-articles/watchdog-timers-microcontroller-timers)

# Using Both ESP32 Cores
The ESP32 comes with 2 Xtensa 32-bit LX6 microprocessors: core 0 and core 1.
So, it is dual core.
When we run code on Arduino IDE, by default, it runs on core 1.
What if I wanted to keep everything WiFi related to core0,
while updating the displays was handled by core1,
and make your ESP32 multitasking?

* [How to use ESP32 Dual Core with Arduino IDE](https://randomnerdtutorials.com/esp32-dual-core-arduino-ide/)

# Swagger UI
* [ESP8266 Tutorial: Adding Swagger UI to REST AP](https://everythingesp.com/esp8266-tutorial-adding-swagger-ui-to-rest-api/)

# ESP32 Long-Range
* [External antennas and ESP32 Long-Range mode](https://www.youtube.com/watch?v=2rujjTOPIRU&app=desktop)
* [Wi-Fi Antennas with Gain and ESP32 Long-Range Mode (part2)](https://www.youtube.com/watch?v=PUppoaePi3A)
