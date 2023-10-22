<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----



# M5Stack
M5Stack, with an eye on IoT solutions, provides flexible, quick & easy development components and tools.
They offer stackable hardware modules and friendly programming platform, to multiple markets like
industrial IoT, smart agriculture, smart retail, STEM education.
To help their user community
they ahve developed a guide on how to program the ESP32 using the Arduino IDE.
The guide offers a detailed walkthrough on programming the ESP32
(using M5Stack Basic as an example) with the Arduino IDE.
Key steps include:

* **Setting Up the Arduino IDE:** Users are directed to the official Arduino website for the appropriate software download.
* **Configuring the IDE:** Detailed instructions on adding board manager URLs specific to ESP32 and M5Stack are provided.
* **Board Installation:** A clear guide on installing the ESP32 board and M5Stack's Basic Core within the Arduino IDE is presented.
* **Programming the ESP32:** With the setup complete, users can now program their devices using the Arduino IDE, unlocking a world of possibilities.

* [M5Stack Announces Comprehensive Guide on Integrating ESP32 with Arduino IDE](https://www.digitaljournal.com/pr/news/getnews/m5stack-announces-comprehensive-guide-on-integrating-esp32-with-arduino-ide)
* [M5Stack's Official Website](https://shop.m5stack.com/)
* [M5Stack's Product Documentation](https://docs.m5stack.com/en/products)
* [Step-by-Step Guide: How to Program ESP32 with Arduino IDE?](https://shop.m5stack.com/blogs/news/step-by-step-guide-how-to-program-esp32-with-arduino-ide)

# M5Stack Atom Echo
* [ATOM Echo Smart Speaker Development Kit](https://shop.m5stack.com/products/atom-echo-smart-speaker-dev-kit)
* [ATOM Echo Documentation](https://docs.m5stack.com/en/atom/atomecho)

# Home Assistant Integration
* [LOCAL VOICE CONTROL of Home Assistant with the M5Stack Atom Echo](https://www.youtube.com/watch?v=U2rykdQlSgA)
* [I turned my ATOM Echo into a Private Voice Assistant for Home Assistant](https://peyanski.com/atom-echo-as-private-voice-assistant/)
    * [ATOM Echo as Voice Assistant for Smart Home](https://www.youtube.com/watch?v=H12dX5oTBGg)
* FLASHING THE ATOM ECHO - [$13 voice remote for Home Assistant](https://www.home-assistant.io/voice_control/thirteen-usd-voice-remote/)
* [LOCAL Voice and Hearing for your Home Assistant Assist!!!](https://www.youtube.com/watch?v=MOJQU5zyoIY)
* [Hands-Free Control with Wake Words](https://www.mostlychris.com/hands-free-control-with-wake-words/)

# Battern Version of "ATOM Echo"
* Adafruit Feather v2 ESP32 board
* 3.7V / 500mA/hr battery
* I2S Microphone - [Adafruit SPH0645LM4H][01] I2S MEMS Microphone Breakout (potential alternative is [DAOKI INMP441][02])
* Audio Amplifier - [Adafruit MAX98357A][03] (or [this][04] form factor) 3W Class D Amplifier takes standard I2S digital audio input, decodes it into analog, and amplifies to support a speaker (alternative is the [MakerHawk MAX98357][05])
* 20x14x3mm speaker button

* [Home Assistant Voice Remote](https://www.youtube.com/watch?v=EeUG3Si9fZk)
* [ESP32 Battery Life Tips](https://www.youtube.com/watch?v=4EZYYPmQnJY)
* [ESP32 Deep Sleep, RTC Memory, "Secret" LoLin Pins](https://www.youtube.com/watch?v=r75MrWIVIw4)


---------


#### Step 1: Quick Testing
The [factory default firmware][10] (compiled on the ESP-IDF platform) on the Atom Echo is a Bluetooth speaker,
which uses the A2DP protocol to transmit audio data（call reception is not supported).
After power on, the red LED is displayed.
When the connection with a Bluetooth device is established,
the LED turns green and sounds can be output from the M5Stack ATOM Echo.
The LED turns red when the device disconnects.

1. Power the Atom Echo via the USB-C port
2. Using a smart phone Bluetooth, pair with "M5_SPEAKER_T1"
3. Go to Amazon Music play some free pod cast or Music
4. Increase the phones volume controls to hear the Amazon audio

If this doesn't work, it might be beacuse the M5Aton Echo needs factory firmware.

Sources:
* [M5Atom Echo - Unboxing & Testing](https://www.youtube.com/watch?v=ZMFTXzuPBqQ)

#### Step 2: xxx
Now lets test the Atom Echo with some example files provided by M5Stack.
We'll get these example programs when we load into our development envirnment
the Atom Echo libraries.

```bash
# search for a library with 'M5atom' in its name
$ arduino-cli lib search M5atom

# install all your required libraries
$ arduino-cli lib install "M5Atom"
Error installing M5Atom: No valid dependencies solution found: dependency 'ATOM-ECHO' is not available

# because of the error, I updated the arduino envirnment using the arduino IDE

# find the eample files here
```


[01]:https://www.adafruit.com/product/3421
[02]:https://www.amazon.com/gp/product/B0821521CV
[03]:https://www.adafruit.com/product/3006
[04]:https://www.adafruit.com/product/5770
[05]:https://www.amazon.com/gp/product/B07PS653CD

[10]:https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Core/Atom/AtomEcho


