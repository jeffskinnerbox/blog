<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----




Water leak detection by measuring the flow of water in the house

* [Water Monitor Measures The Cost Of Your Shower Thinking Time](https://hackaday.com/2022/08/26/water-monitor-measures-the-cost-of-your-shower-thinking-time/)
* [How to Measure Flow with Magnets - (Magnetic Flow Meters)](https://www.youtube.com/watch?v=TR0baWuB6v4&feature=youtu.be)
* [FLUID Is A Smart Water Meter For Your Home][01]
* [Remote Water Consumption Display][02]
* [Measuring Water Consumption][03]
* [Water Hero][04]
* [vibration Sensor](http://www.phidgets.com/products.php?product_id=1104)
* [Water meter + Arduino = Aquameterduino](http://www.instructables.com/id/Water-meter-Arduino-Aquameterduino-/?ALLSTEPS)
* [Build a Wireless Water Meter for Your Home](http://spectrum.ieee.org/geek-life/hands-on/build-a-wireless-water-meter-for-your-home)
* [Flood Fault Circuit Interrupter Could Save Lives](https://hackaday.com/2018/05/16/flood-fault-circuit-interrupter-could-save-lives/)
* [Smart Water Meter](https://www.hackster.io/Pedro52/smart-water-meter-58d99d)
* [Wireless Water Meter Monitor Watches Waste](https://hackaday.com/2015/12/06/wireless-water-meter-monitor-watches-waste/)
* [Pipe Break Detector](https://www.hackster.io/jeffaddleman/pipe-break-detector-44e438)

* [Data Mining Home Water Usage; Your Water Meter Knows You A Bit Too Well](https://hackaday.com/2019/08/14/data-mining-home-water-usage-your-water-meter-knows-you-a-bit-too-well/)


* [An ESP Will Read Your Meter For You](https://hackaday.com/2021/02/07/an-esp-will-read-your-meter-for-you/)
* [Old Gas Meter Gets Smart With The ESP8266](https://hackaday.com/2021/01/31/old-gas-meter-gets-smart-with-the-esp8266/)

# Toilet Leak Monitoring
* [SI-Toilet Sensors](https://www.sensorindustries.com/toilet-sensor/)
* [Wireless Leak Detection by The Detection Group](https://lyncbywatts.com/the-detection-group)
* [LeakAlertor 6000 Product Review](https://www.youtube.com/watch?v=v86YXtAsd5Y)
* [Leak Alertor 6000 Installation: Basic](https://www.youtube.com/watch?v=5-jOwc5k7XU)
* [Leak Alertor 6000 Alerts](https://www.youtube.com/watch?v=TQRy27VDVYU)

## Leak Detection via Radar
* [Neural Network Helps With Radar Pipeline Diagnostics](https://hackaday.com/2023/05/31/neural-network-helps-with-radar-pipeline-diagnostics/)
* [AI-assisted Pipeline Diagnostics and Inspection W/ MmWave](https://www.instructables.com/AI-assisted-Pipeline-Diagnostics-and-Inspection-W-/)

# About Leesburg's Water Meters
* [Town of Leesburg: View Your Water Usage](https://www.leesburgva.gov/departments/utilities-water-sewer/customer-services/view-your-water-usage)
* [Using SDR to Read Your Smart Meter](https://hackaday.com/2014/02/25/using-sdr-to-read-your-smart-meter/)
* [Reading The Water Meter In A Literal Sense With an ESP8266](https://hackaday.com/2019/09/06/reading-the-water-meter-in-a-literal-sense-with-an-esp8266/)
* [Tracking down a water leak with rtlamr](https://irrational.net/2019/03/26/tracking-down-a-water-leak/)
* [Crossing AMR's Iron Curtain](https://www.wwdmag.com/meter-reading-services/crossing-amrs-iron-curtain)
* [RTLAMR - A word of caution when reading your water meter](https://www.reddit.com/r/RTLSDR/comments/3dh2ag/rtlamr_a_word_of_caution_when_reading_your_water/)
    - ERT
    - AMR
    - pit-mounted Itron encoder/receiver/transmitter (ERT) units
    - Badger Meter AMR

# Battery Free / Energy Harvesting
* [AquaSensing Leak Sensor 1.0](https://www.nordicsemi.com/News/2022/01/AquaSensings-Leak-Sensor-10-employs-nRF52832-SoC)

# Acoustic Water Leak Detection
* [AquaPing](https://www.crowdsupply.com/microphonon/aquaping)
    * [The Evolution of the AquaPing Design](https://www.crowdsupply.com/microphonon/aquaping/updates/the-evolution-of-the-aquaping-design)
    * [The AquaPing is not a flow meter: statistics and noise mitigation](https://www.crowdsupply.com/microphonon/aquaping/updates/the-aquaping-is-not-a-flow-meter-statistics-and-noise-mitigation)
* [MicroPhonon](https://microphonon.com/)

## Leak Sound Detection
* [DIY Hydrophone Listens In On The Deep For Cheap](https://hackaday.com/2022/02/19/diy-hydrophone-listens-in-on-the-deep-for-cheap/)
* [Cadmus - Microphone background noise cancellation and suppression for Linux!](https://www.youtube.com/watch?v=yYibLw3gsBw)
* [Listening to Bats As They Search For Food](https://hackaday.com/2023/07/14/listening-to-bats-as-they-search-for-food/)

## Microphone Types
Dynamic Microphone
ECM Microphone
MEMS Microphone
Ribbon Microphone

Digital microphones are available with two different output formats: PDM and I2S.
The output of a PDM (pulse density modulation) microphone is a 1-bit high sample rate data stream
that is the direct output of the Sigma-Delta modulator that's in the mic.
The sample rate of this PDM stream is typically between 1 and 3.25 MHz.
Before this PDM data can be further processed,
it needs to be decimated to a lower sample rate that other devices,
such as codecs and DSPs, can handle.
This decimation filter is implemented in the codec or DSP to which the PDM microphone is connected.
The output of this filter gives data at a lower sample rate, typically between 16 and 48 kHz.

* [How Accuracy is Achieved in MEMS Sensors](https://community.element14.com/learn/learning-center/the-tech-connection/w/documents/27395/how-accuracy-is-achieved-in-mems-sensors)

* [Comparing MEMS and Electret Condenser (ECM) Microphones](https://www.youtube.com/watch?v=CdfL7IaR7xQ)
* [Comparing MEMS and Electret Condenser (ECM) Microphones](https://www.cuidevices.com/blog/comparing-mems-and-electret-condenser-microphones)
* [Choosing the Right Microphone](https://www.puiaudio.com/audio-articles/show/choosing-microphones)
* [MEMS microphones, why is digital best?](https://www.cmlmicro.com/mems-microphones-why-is-digital-best/)

* [Condenser microphone pre-amp with bootstrapped op amp](https://www.by-rutgers.nl/ME6211-PRO37R.html)

* [Pressure Zone Microphone (PZM)](https://www.instructables.com/Build-a-PZM-or-Pressure-Zone-Microphone/)

* [Mico – A USB microphone based on Raspberry Pi RP2040 MCU](https://www.cnx-software.com/2021/12/31/mico-a-usb-microphone-based-on-raspberry-pi-rp2040-mcu/)
* [The Mico RP2040 Microphone Is Ideal for Machine Learning Applications](https://www.hackster.io/news/the-mico-rp2040-microphone-is-ideal-for-machine-learning-applications-add402fb884b)

### Dynamic Microphone
A dynamic microphone operates on the same basic electrical principles as a speaker, but in reverse. Sound waves strike the diaphragm, causing the attached voice coil to move through a magnetic gap creating current flow as the magnetic lines are broken.

### PDM Microphone
Pulse Density Modulation (PDM) Microphone,
sometimes called MEMS microphone since the are designed with Micro-Electro-Mechanical System (MEMS) components,

* [PDM Microphones and Sigma-Delta A/D Conversion](https://tomverbeure.github.io/2020/10/04/PDM-Microphones-and-Sigma-Delta-Conversion.html)
* [An Introduction to MEMS Microphone Arrays](https://www.cuidevices.com/blog/an-introduction-to-mems-microphone-arrays#overview)

* https://www.amazon.com/s?k=MEMS+Microphone+Breakout&i=electronics

### ECM Microphone
Electret Condenser Microphone (ECM microphone) apply the principle of capacitor charge/discharge for operation. The diaphragm acts as one plate of a capacitor, the vibration is generated due to the sound, then produce the changes of charge between the plates to make the signal transmission.

Electret Microphones: Adafruit [MAX4466](https://www.adafruit.com/product/1063) or [MAX9814](https://www.adafruit.com/product/1713)
MEMS Microphones: Adafruit [SPW2430](https://www.adafruit.com/product/2716) or [PDM MEMS](https://www.adafruit.com/product/3492) or [PDM MEMS with JST SH connector](https://www.adafruit.com/product/4346)
The MAX4466 is quite classical and has an integrated op-AMP and gain can change from 25x to 125x while the MAX9814 has an automatic gain control. However "max gain" can obviously me modified. Finally the SPW2430 is the smaller one and probably the best for audio detection while the two previous ones can be used for recording/sampling - but "the output peak-to-peak voltage has a 0.67V DC bias and about 100mVpp" - so it's the more likly to clip/sature on high-level sounds. So at this point we don't have any favorites !

* https://en.wikipedia.org/wiki/Electret
* https://en.wikipedia.org/wiki/Electret_microphone
* https://www.amazon.com/s?k=Electret+Microphone+Breakout&i=electronics

## Audio Source Seperation
* [How To Implement the Audio Source Separation Function](https://dzone.com/articles/how-to-implement-the-audio-source-separation-funct)

## Sound Classification
* [Simple Audio Recognition on a Raspberry Pi using Machine Learning (I2S, TensorFlow Lite)](https://electronut.in/audio-recongnition-ml/)

# What are some types of water leak detection systems?
* [Whole house water leak detection systems](https://www.statefarm.com/simple-insights/residence/water-leak-detection)
* [What is the best water leak detector?](https://www.consumeraffairs.com/homeowners/water-leak-detectors.html)

## Whole House Leak Detection
Flume uses patented technology to read the magnetic field directly from your water meter and detect usage down to the one-hundredth of a gallon
* [Flume](https://flumewater.com/product/)
* [A Water Leak Detector That Listens Carefully](https://hackaday.com/2022/06/24/a-water-leak-detector-that-listens-carefully/)




# Making Your Own Microphone
* [A Lab-Grade Measurement Microphone For Not A Lot](https://hackaday.com/2022/06/08/a-lab-grade-measurement-microphone-for-not-a-lot/)

# Microphone + Processor Boards
Seeed XIAO BLE nRF52840 Sense is a tiny Bluetooth LE development board designed for IoT and AI applications. It features an onboard antenna, 6 Dof IMU, microphone, all of which make it an ideal board to run AI using TinyML and TensorFlow Lite.

* [SparkFun Analog MEMS Microphone Breakout - SPH8878LR5H-1](https://www.sparkfun.com/products/19389)
* [Seeed Xiao BLE nRF52840 (Sense)](https://www.hackster.io/videos/1107)
* [Seeed XIAO BLE nRF52840 Sense - TinyML/TensorFlow Lite- IMU / Microphone - Bluetooth5](https://www.seeedstudio.com/Seeed-XIAO-BLE-Sense-nRF52840-p-5253.html)
* [XIAO BLE Sense Getting Started](https://wiki.seeedstudio.com/XIAO-BLE-Sense-Getting-Started/)

* [WioTerminal – Training an audio recognition module. Running the model on the Device](https://elbruno.com/2021/11/25/wioterminal-training-an-%f0%9f%97%a3%ef%b8%8f-audio-recognition-module-running-the-model-on-the-device-%e2%8f%af%ef%b8%8f/?ct=t()&mc_cid=2a79d36d65&mc_eid=376a45e4d9)
* [Building a quality USB-C microphone](https://www.youtube.com/watch?v=LoQu3XXIayc)
* [DIY USB MICROPHONE SEEMS OVERKILL; IS SURPRISINGLY IN-DEPTH](https://hackaday.com/2021/06/02/diy-usb-microphone-seems-overkill-is-surprisingly-in-depth/)
* [Flywoo AGC-MIC Automatic Gain Control VTX Microphone For FPV Camera](https://www.aliexpress.com/item/1005002064948892.html)




# Electret Microphone with Audio Amplifier
I purchased a [Electret Microphone with a audio amplifier][22];
the audio amplifer being the [MAX4466][21].
On the back there is a small trimmer pot to adjust the gain from 25x to 125x.
At the lowest gain, you at about 200mVpp (normal speaking volume about 6" away),
up to about 1Vpp at high gain (see [mic level vs line level][20]).
The output is [rail-to-rail][23] so if the sounds get loud, the output can go up to 5Vpp!

For use:
* **To power it,** you should connect GND to ground, VCC to 2.4-5VDC. Use the "quietest" supply available (3.3V or 5V microcontrol supply).
* **Output** for the audio waveform will come out of the OUT pin. The output will have a DC bias of VCC/2 so when it's perfectly quiet, the voltage will be a steady VCC/2 volt (it is DC couple - see [AC versus DC coupling][24]).
* **Audio applications** that require AC coupled audio,
place a 100uF capacitor between the OUT pin and the input of your device.
If you're connecting to an audio amplifier that has [differential inputs][25] or includes decoupling capacitors,
the 100uF cap is not required.
* **Drive speakers** or anything but the smallest in-ear headphones. you will need an audio amplifier
* (such as [3.7W stereo amp][26]) and connect the amp output directly to speakers.
* **Drive microcontroller** you don't need an amplifier or decoupling capacitor.
You can connect the OUT pin directly to the microcontroller ADC pin.



# ESP32 Audio Streamer
Use a Electret Microphone + Amplifier Board and ESP32 to stream audio over WiFi for futher digital signal processing.

* [ESP32 Voice Streamer](https://projects-raspberry.com/esp32-voice-streamer/)
    * https://www.hackster.io/julianso/esp32-voice-streamer-52bd7e

* [How to Use a Microphone with Arduino](https://www.teachmemicro.com/arduino-microphone/)
* [Tech Note 077 - ESP32 8-Octave Audio Spectrum Display](https://www.youtube.com/watch?v=OStljy_sUVg)
* [ESP32 Audio Input Using I2S and Internal ADC](https://www.youtube.com/watch?v=pPh3_ciEmzs)
* see the document "raspberry-pi-zero-walkie-talkies-via-mumble.md"



[01]:http://techcrunch.com/2015/09/15/fluid-is-a-smart-water-meter-for-your-home
[02]:https://hackaday.io/project/1460-remote-water-consumption-display
[03]:https://hackaday.io/project/4648-analogio-a-full-stack-iot-platform/log/23608-measuring-water-consumption
[04]:http://www.waterheroinc.com/
[05]:
[06]:
[07]:
[08]:
[09]:
[10]:
[11]:
[12]:
[13]:
[14]:
[15]:
[16]:
[17]:
[18]:
[19]:
[20]:https://www.shure.com/en-EU/performance-production/louder/differences-line-mic-level
[21]:https://www.maximintegrated.com/en/products/analog/audio/MAX4466.html
[22]:https://www.adafruit.com/product/1063
[23]:https://www.analogictips.com/amplifiers-rail-to-rail-single-supply-mean/
[24]:https://community.sw.siemens.com/s/article/ac-and-dc-coupling-what-s-the-difference
[25]:https://kb.mccdaq.com/KnowledgebaseArticle50277.aspx
[26]:https://www.adafruit.com/product/987
[27]:
[28]:
[29]:
[30]:
