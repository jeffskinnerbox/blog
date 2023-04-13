<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----




# Starter Projects
* [How to get started with ESPHome and Sonoff](https://www.youtube.com/watch?v=soKuma8DJWQ)

## Room Thermometer/Hygrometer
* [Super easy! Add your ESP32 Board to Home Assistant with ESPHome](https://www.youtube.com/watch?v=Be5zWukjV9I)
* [Use this CHEAP Xiaomi thermometer with an ESP32 and Home Assistant](https://www.youtube.com/watch?v=l5ea7lQWpMk)
    * [Xiaomi LYWSD03MMC Bluetooth BLE Thermometer Hygrometer](https://www.amazon.com/gp/product/B083Y1D8WB/ref=ox_sc_act_title_1)
    * [NEW! ESP Web Tools. Program ESP boards from your browser with ESPHome Add-on in Home Assistant](https://www.youtube.com/watch?v=mj-24SZLQKk)
    * [CUSTOM FIRMWARE FOR CHEAP BLUETOOTH THERMOMETERS](https://hackaday.com/2020/11/17/custom-firmware-for-cheap-bluetooth-thermometers/)
* [A Simple Web Configured BLE To GPIO Bridge](https://hackaday.com/2022/09/06/a-simple-web-configured-ble-to-gpio-bridge/)
* [Telink Flasher for Xiaomi Mii Thermometer](https://pvvx.github.io/ATC_MiThermometer/TelinkMiFlasher.html)

## Home Assistant Bluetooth Proxies
* [EASY Bluetooth Proxies in Home Assistant! Increase the range of your passive Bluetooth devices!](https://www.youtube.com/watch?v=CjpPdwK_ttg)
* [Home Assistant Bluetooth Proxy - How To](https://digiblur.com/2022/09/07/home-assistant-esphome-bluetooth-proxy-how-to/)

## Lightning Sensor
* [AMS AS3935 Franklin Lightning Sensor](https://esphome.io/components/sensor/as3935.html)

## Physical Presense Sensor
Black or lock comperter display if person isn't present

```bash
# black screen
gnome-screensaver-command -a

# black and lock screen
gnome-screensaver-command -l
```




# ESPHome
Tasmota or ESPHome, together with Home Assistant are often seen together for home automation.
Most of the focus is on flashing and integrating readily available devices and sensors.
But which framework is better also for our do-it-yourself sensors and ESP32 boards.

* [Tasmota vs ESPhome: Who wins?](https://www.youtube.com/watch?v=nHaFM0tKOvY&feature=youtu.be)

Esphome shows a lot of promise.
It has over-the-air updates, it automatically compiles based on some yaml and uploads it! If it cant upload it (like the initial flash) I would simply set up the yaml, compile it, SCP it locally and flash it with https://github.com/espressif/esptool. If this worked, it would now support OTA updates.

Because its a bunch of yaml I can source control it too!

It uses passwords for both API integrations (home-assistant) and for OTA updates (same or different password) which makes me feel good.

Also: the server runs as a container, so its running on my Server network on nomad. I can simply go to http://esphome.service.consul and click “Upload” to update my IoT.

* [ESPHome](https://esphome.io/)
* [ESPHome Device Configuration Repository](https://www.esphome-devices.com/)
* [This is SO Much Better! Getting Started with ESPHome 2021](https://www.youtube.com/watch?v=iufph4dF3YU)

* [Home Automation With Home Assistant and ESPHome - First Steps](https://www.youtube.com/watch?v=xDbH-xPQtXU)
* [Home Automation with ESPHome & Home Assistant](https://www.youtube.com/playlist?list=PL2a34OA-WuyYvDbSaIthEk5dCs1BB2fB-)
* [Getting Started with ESPHome and Home Assistant](https://esphome.io/guides/getting_started_hassio.html)
* [Roll Your Own Automation With ESPHome](https://hackaday.com/2020/04/20/roll-your-own-automation-with-esphome/)
* [My Secure Smart Home](https://marcyoung.us/post/smart-home/)

## Installing ESPHome via Home Assistant
* [Home Assistant: A Fingerprint Scanner for Your Garage](https://hometechhacker.com/home-assistant-a-fingerprint-scanner-for-your-garage/)


