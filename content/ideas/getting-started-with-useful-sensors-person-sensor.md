<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----

* [Sense All the Things with a Synthetic Sensor](http://hackaday.com/2017/05/19/sense-all-the-things-with-a-synthetic-sensor/)
* [Into The Belly Of The Beast With Placemon](https://hackaday.com/2020/09/17/into-the-belly-of-the-beast-with-placemon/)
* [Synthetic Sensors: Towards General-Purpose Sensing](http://www.gierad.com/assets/supersensor/supersensor.pdf)
* [Synthetic Sensors (Gierad Laput - ACM CHI 2017)](https://www.youtube.com/watch?v=hpxUrvTltJI)
* [Vibrosight Hears When You are Sleeping. It Knows When You’re Awake.](https://hackaday.com/2018/10/22/vibrosight-hears-when-you-are-sleeping-it-knows-when-youre-awake/)
* [Enhancing my ordinary IP security cameras with AI](https://harizanov.com/2018/03/enhancing-my-ordinary-security-cameras-with-ai/)
* [mmWave Human Detection Sensor](https://www.seeedstudio.com/mmWave-Human-Detection-Sensor-Kit-p-5773.html)

* [Useful Sensors' Tiny Code Reader Is a Privacy-Centric Low-Cost Scanner for 2D QR Codes](https://www.hackster.io/news/useful-sensors-tiny-code-reader-is-a-privacy-centric-low-cost-scanner-for-2d-qr-codes-104d9229e8c7)
    * [Tiny Code Reader from Useful Sensors](https://www.adafruit.com/product/5744)
    * [Useful Sensors Tiny Code Reader](https://www.sparkfun.com/products/23352)




I have been intrigued by the possibilities within the concept of a "synthetic sensor".
I define a synthetic sensor as a device that doesn't simple sense the physical phenomena in its environment,
but inference about one or more physical phenomena to conclude that something is happening in the environment.
I thought that an ML/CV enabled camera would be a very good example,
but to truly think of it as a sensor,
it needs to be inexpensive (a few dollars) and work out-of-the-box (plug it in and it provide the inference information).
While I didn't create this concept (See ["Synthetic Sensors: Towards General-Purpose Sensing"][04]
and ["Machine Learning Sensors"][05]), its not unique and now appears to becoming a reality.

For $10, I purchased a [Person Sensor][01] by [Useful Sensors Inc.][02]
from [SparkFun (aka product code SEN-21231)][03]
in October of 2022 and finally got around to messing with it in March of 2023.
The Person Sensor includes a camera module pre-programmed with algorithms that can detect human faces,
and return information over a [Qwiic I2C interface][06].
It is designed to be used as true sensor that inputs to a larger system which will process the information.
This makes it easy to build projects that
wake up when people approach,
count the number of faces present,
where they are relative to the sensor,
follow their faces,
mute a microphone when nobody is present,
and even recognize different people to personalize their experiences.

#### Step X: Wiring the Person Sensor to a ESP32
Before you start trying to read information from the sensor,
a good first step is to power it up and make sure it seems to be working correctly.
To do this, at a minimum you need to connect the GND and 3.3V lines from your microcontroller (MCU) to the sensor.
 It is best to do this by:

 1. wiring the Qwiic socket on the MCU to the sensors Qwiic socket.
 1. breaking out to individual pins on the MCU and connect with the sensors Qwiic socket via the [Qwiic - Breadboard cable][07].

With the sensor powered, try moving it around so the camera is pointed at your face.
You should see the LED light up green.

#### Step x: Read Data From the Person Sensor
With the person sensor connected, you can start reading information from it.
The code needed will depend on the platform you’re using for the main controller device,
but [here is some example code][08].
I choose to use Circuit Python / MicroPython / C++ on Linux.

>**NOTE:** The 7-bit peripheral address for the sensor is 0x62.
> Please note that some systems include the read/write bit in the address,
> >making the 8-bit peripheral address 0xC4.

#### Step x: xxx
#### Step x: xxx
#### Step x: xxx
#### Step x: xxx
#### Step x: xxx



[01]:https://usefulsensors.com/person-sensor/
[02]:https://usefulsensors.com/
[03]:https://www.sparkfun.com/products/21231
[04]:https://www.gierad.com/projects/supersensor/
[05]:https://arxiv.org/pdf/2206.03266.pdf
[06]:https://www.sparkfun.com/qwiic
[07]:https://www.digikey.com/en/products/detail/sparkfun-electronics/PRT-17912/13998112
[08]:https://github.com/usefulsensors
[09]:
[10]:
