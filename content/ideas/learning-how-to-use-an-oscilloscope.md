<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----




# Basics of Oscilloscopes
The modern oscilloscope is an invaluable tool.
[What is an oscilloscope?  What is it useful for?  How is it used?][06]
At its simplest level the oscilloscope allows users to visualize the behavior of a signal
by displaying its voltage over a time period.
But the setup, use, and interpretation of collected data can be overwhelming to many
and the wealth of new capabilities enabled by digital oscilloscopes are often unknown.
In this blog, I'll systematical review the use of an oscilloscope,
specifically the [Rigol DS1054Z][07] ([Rigol's site][08] and [Rigol DS1054Z User Guide][11]).


# History of the Oscilloscope

* [The Early History of the Oscilloscope: Amber and Frog Legs](https://www.allaboutcircuits.com/news/early-history-of-the-oscilloscope-amber-and-frog-legs/)
* [History of the Oscilloscope: Oersted’s Laws and Hand Drawn Waveforms](https://www.allaboutcircuits.com/news/history-of-the-oscilloscope-oersteds-laws-and-hand-drawn-waveforms/)
* [History of the Oscilloscope: Visualizing with Light, the CRT, to the Modern Oscilloscope](https://www.allaboutcircuits.com/news/history-of-the-oscilloscope-visualizing-with-light-crt-modern-oscilloscope/)
* [vintageTEK - Online Museum of TekTronix Oscilloscopes](https://vintagetek.org/exhibits/)
* [A Day for Oscilloscopes](https://www.sparkfun.com/news/5256)



-------



# Update Rigol DS1054Z Firmware - DONE
First thing to do is update you Rigol DS1054Z firmware.
[Here's a step-by-step video on how to perform the firmware (FW) upgrade][09].
The steps are as follows:


## Step 1: Format USB thumbdrive as Fat32 - DONE
show your USB drive among all storage partitions and volumes on your computer use
`dg -h` or `lsblk`.

```bash
# unmount the file system
sudo umount /dev/sdi1

#format drive with the FAT32 file system format and give it a name
sudo mkfs.vfat -F 32 -n 'THUMB-DRIVE' /dev/sdi1
```


## Step 2: Downloading the Firmware - DONE
Download the zip file to you PC drive first and then load to the thumb dirve:

```bash
# make a directory to story the zip file
mkdir ~/Downloads/DS1054Z-firmware
cd ~/Downloads/DS1054Z-firmware

# download file from https://www.rigolna.com/firmware/

# unzip the file and copy the appreciate file to the thumb drive
unzip DS1000ZUpdate.zip
cp DS1000ZUpdate.GEL /media/jeff/THUMB-DRIVE/
```


## Step 3: Do Firmware Upgrade - DONE
Now get your oscilloscopes firmware version
by select buttons **System** > **System Info**.

Eject the thumb drive and plug into the oscilloscope.
Select button **Ok**

The firmware update takes about 5 minutes.
When update complete, remove the thumb drive a restart the scope,
and recheck firmware version.

Now we must performing a self calibration, which takes about 15 minutes.
The scope should warm up for at least 30 minutes before calibration.
Select buttons **Utility** > **Menu Down Arrow** > **Self-Cal** > **Start**


# Expand Rigol DS1054Z Bandwidth to 100 MHz - DONE
There is a simple hack for the Rigol DS1054Z Digital Oscilloscope
in order to activate all the installed options, including its 100Mhz bandwidth.
You'll find that hack in the video
"[How to Hack a Rigol DS1054Z DIgital Oscilloscope - Quick Tips][10]".
Make sure the firmware is up to date before apply the activation key.

Model: DS1054Z
Serial No.: DS1ZA164859787
Software Version: 00.04.04.SP4
Board Version: 0.1.1

Options: DSER
Privatekey: 6F1106DDA994DA
Software Key: RDJ9JBB-N3SWWUS-RZ4ERVJ-K543RMA



--------



# Rigol DS1054Z Oscilloscope


## Introduction

* [EEVBlog #704 - Rigol DS1054Z Oscilloscope Features Review](https://www.youtube.com/watch?v=W2qdtQkBKhc&t=572s)
* [Oscilloscopes Made Easy #1 - Introduction to Oscilloscopes (Rigol DS1104Z)](https://www.youtube.com/watch?v=uU3FhH7_MWo)
* [Oscilloscopes Made Easy #2 - Simple Triggering (Rigol DS1104Z)](https://www.youtube.com/watch?v=5VyotIVwRiA&t=6s)


## Oscilloscope Definitions and Concepts


## Triggering

* [Tutorial: How to use an Oscilloscope #3 - How to capture a signal event / glitch / transient](https://www.youtube.com/watch?v=JsoZZM2Vc5Y)
* [Beyond The Basics: Exploring Exotic Scope Trigger Modes](https://hackaday.com/2023/12/20/beyond-the-basics-exploring-exotic-scope-trigger-modes/)


## Signal Integrity


## Advanced Analysis


## Connectivity and Data Management


### Making Your First Measurement

* [Making your first measurement](https://www.youtube.com/watch?v=-T--1IKV8lw)
* [Basics of Oscilloscopes](https://beyondmeasure.rigoltech.com/acton/fs/blocks/showLandingPage/a/1579/p/p-0032/t/page/fm/0)


# Decode I2C Serial Data

* [How to decode I2C serial data on the Rigol 1054Z oscilloscope](https://www.youtube.com/watch?v=VkbubgSxBnQ)
* [DS1000z I2C Decoding and Triggering (covers DS1054Z, DS1074Z, DS1100Z, MSO1074Z, MSO1104Z)](https://www.youtube.com/watch?v=HxpSYlnEDos)


# Decode SPI Serial Data

* [Decoding SPI with the Rigol DS1054z Oscilloscope](https://www.youtube.com/watch?v=O1mPIjh72gY)




--------



* [Building A Swiss Army Lab With Software Defined Instrumentation](https://hackaday.com/2022/04/29/building-a-swiss-army-lab-with-software-defined-instrumentation/)
  * [Liquid Insruments](https://www.liquidinstruments.com/)
  * [Moku:Go](https://www.liquidinstruments.com/products/hardware-platforms/mokugo/)


* [EEVblog Oscilloscope Tutorials](https://www.youtube.com/playlist?list=PLvOlSehNtuHsCTtj-T_vkpTTbBXW4sB51)
* [Mix - Eevblog oscilloscope](https://www.youtube.com/watch?v=xaELqAo4kkQ&list=RDQMgB8FTWZE6ak&start_radio=1)

* [The Pre-CRT Oscilloscope][01]
* [Cut Through The Noise, See Tiny Signals][02]
* [Bus Pirate Oscilloscope][03]
* [The Best Voltage And Current Reference This Side Of A Test Lab](https://hackaday.com/2020/03/10/the-best-voltage-and-current-reference-this-side-of-a-test-lab/)

* [Talk To Your ‘Scope, And It Will Obey](https://hackaday.com/2019/03/03/talk-to-your-scope-and-it-will-obey/)

* [How to Use Your Computer to Generate Complex Analog Waveforms](https://www.allaboutcircuits.com/technical-articles/how-to-use-your-computer-to-generate-complex-analog-waveforms/)

* [LEAP: Little Electronic and Arduino Projects](https://leap.tardate.com/)
* [How to Use an Oscilloscope](https://learn.sparkfun.com/tutorials/how-to-use-an-oscilloscope)
  * [How to Use an Oscilloscope: The Video](https://www.youtube.com/watch?v=u4zyptPLlJI&app=desktop)

* [Break Your Scope’s Bandwidth Barrier](https://hackaday.com/2019/01/24/break-your-scopes-bandwidth-barrier/)

* [Rigol MSO5000 Hacked, Features Unlocked](https://hackaday.com/2018/12/19/rigol-mso5000-hacked-features-unlocked/)

* [EEVblog #1226 - Get Better Accuracy On Your Oscilloscope](https://www.youtube.com/watch?v=8iE28oGtayQ&feature=em-uploademail)

* [Scope Review: Keysight 1000 X-Series](https://hackaday.com/2017/05/02/scope-review-keysight-1000-x-series/)



# Digital Oscilloscope Specs

* [Understanding Digital Oscilloscope Sample Rate and Analog Bandwidth Specs](https://www.allaboutcircuits.com/technical-articles/understanding-digital-oscilloscope-sample-rate-analog-bandwidth)

Oscilloscope Analog Bandwidth
Oscilloscope Sample Rate


-------



# Noise and EMI

* [Ferrite, chokes, and RFI](https://www.youtube.com/watch?v=LuMlM8zWQFk)
* [How do ferrite cores work?](https://www.youtube.com/watch?v=PhOVMgPMqWU)
* [How do EMI Filter Chokes Work?](https://www.youtube.com/watch?v=84aKURxohlg)
* [Visualizing EMI Filter Frequency Response with an Oscilloscope](https://www.youtube.com/watch?v=glNDcDklhRw)
* [Differential (Normal) Mode Noise and Common Mode Noise－Causes and Measures](https://techweb.rohm.com/knowledge/emc/s-emc/01-s-emc/6899)
* [How To Track Down Common Mode Noise](https://www.youtube.com/watch?v=BFLZm4LbzQU)
* [ferrite bead demo](https://www.youtube.com/watch?v=7w0Ec-HEPrA)
* [Basics of Ferrite Beads: Filters, EMI Suppression, Parasitic oscillation suppression / Tutorial](https://www.youtube.com/watch?v=81C4IfONt3o)
* [EEVblog #442 - Analog Vs Digital Oscilloscope Noise](https://www.youtube.com/watch?v=ImyUB3_n9fw)
* [EEVblog #601 - Why Digital Oscilloscopes Appear Noisy](https://www.youtube.com/watch?v=Znwp0pK8Tzk&feature=youtu.be)

* [Remoticon Video: Basics of RF Emissions Debugging Workshop](https://hackaday.com/2021/01/08/remoticon-video-basics-of-rf-emissions-debugging-workshop/)


# Making Better Measurements

* [How to make better measurements with your oscilloscope or digitizer](https://www.edn.com/how-to-make-better-measurements-with-your-oscilloscope-or-digitizer/)


# Premature Oscilloscope Triggering

* [EEVblog #1320 - Premature Oscilloscope Triggering](https://www.youtube.com/watch?v=GZHnrGIK9V8)


## The Art of Electronics
None of these tools will be a substitute for a mastering of the domain of electronics.
To that, you man not start here, but you should certainly finish here:
[The Truth is in There: The Art of Electronics, the x-Chapters](https://hackaday.com/2020/01/23/the-truth-is-in-there-the-art-of-electronics-the-x-chapters)


# Tutorials on Electronics

* [Ben Eater](https://www.youtube.com/channel/UCS0N5baNlQWJCUrhCEo8WlA)
* [Full 8-Bit Computer On Breadboards](https://hackaday.com/2020/11/23/full-8-bit-computer-on-breadboards/)
* [8-Bit Computer: UART Transceiver for breadboard computer](https://shepherdingelectrons.blogspot.com/2020/07/uart-transceiver-for-breadboard-computer.html)
* [A Well Documented BreadBoard Computer Shows Dedication](https://hackaday.com/2021/12/18/a-well-documented-breadboard-computer-shows-dedication/)


# Debugging Electronics

* [Daniel Samarin - Debugging Electronics: You Can’t Handle the Ground Truth!](https://www.youtube.com/watch?time_continue=10&v=oULeLtcv4n4&feature=emb_logo)
* [Voltage / Current Logger](https://hackaday.com/2019/11/23/if-you-need-a-measurement-tool-just-build-a-measurement-tool/)


# What Does a Workbench Need?

* [What Does An Electronics Tinkerer’s Workbench Need?](https://hackaday.com/2019/12/14/what-does-an-electronics-tinkerers-workbench-need/)


# Computer Control of the Oscilloscope

* [Controlling a Rigol oscilloscope using Linux and Python](http://www.cibomahto.com/2010/04/controlling-a-rigol-oscilloscope-using-linux-and-python/)
* [glScopeClient: A Permissively-Licensed Remote Oscilloscope Utility](https://hackaday.com/2019/05/30/glscopeclient-a-permissively-licensed-remote-oscilloscope-utility/)


# Tips & Tricks

* [Twelve tips for using the Rigol DS1052E Oscilloscope](http://www.righto.com/2013/07/tips-for-using-rigol-ds1052e.html)
* [EEVblog #1324 - Scope TRICK: 2 Probes 1 Hand](https://www.youtube.com/watch?v=v8sCyr5pZkc&feature=em-uploademail)


## FFT Mode
See 15:45 minutes into the video. Bottomline ... doesn't work well - [EEVblog #845 - Oscilloscope FFT Comparison](https://www.youtube.com/watch?v=07VkEUUd0eo&feature=youtu.be)


# Power Measurement

* [POWER MEASUREMENT OSCILLOSCOPE STYLE](https://hackaday.com/2019/04/24/power-measurement-oscilloscope-style/)


# Measure Current with an Oscilloscope

* [#855 Basics: Measure Current with an Oscilloscope](https://www.youtube.com/watch?v=JSBiIT3iljw)
* [Measuring and Observing Current using Oscilloscope and Shunt Resistor](https://www.youtube.com/watch?v=MwQzMxNOenI)


# Fun With Negative Resistance

* [Fun With Negative Resistance: Jellybean Transistors](https://hackaday.com/2019/05/08/fun-with-negative-resistance-jellybean-transistors/)


# Transistor Tester with Oscilloscope

* [Transistor Tester with Digital RIGOL Oscilloscope DS1054z 4K](https://www.youtube.com/watch?v=cd2rp9PhpgM)


# Vernier Controls
The concept is similar in use to [vernier calipers][04] which have a primary scale for gross measurements, and a secondary scale for fine measurements.

* [Get Better Accuracy On Your Oscilloscope](https://www.youtube.com/watch?v=8iE28oGtayQ)
* [Do Digital Scopes Have REAL Verniers?](https://www.youtube.com/watch?v=7v-P75MOZ5o&feature=em-uploademail)


# Spectrum Analyser

* [No Spectrum Analyser? No Problem!](https://hackaday.com/2015/12/20/no-spectrum-analyser-no-problem/)


# Spectrum Analyzer

* [#828 Using Oscilloscope as a Spectrum Analyzer (FFT)](https://www.youtube.com/watch?v=ZHYmUS7R6V4)
* [TinySA Is A $49 Spectrum Analyzer](https://hackaday.com/2020/09/01/tinysa-is-a-49-spectrum-analyzer/)
* [Product Review: The TinySA, A Shirt-Pocket Sized Spectrum Analyzer](https://hackaday.com/2020/11/09/product-review-the-tinysa-a-shirt-pocket-sized-spectrum-analyzer/)


# Example Uses

* [Measuring Cable Length - Fast Video Covers Coax Velocity Factor](https://hackaday.com/2019/10/11/fast-video-covers-coax-velocity-factor/)
* [Measure the Speed of Light](https://hackaday.com/2016/09/29/testing-the-speed-of-light-conspiracy/)
* [Back to Basics: Diodes - guide to operation, characteristics, types and specifications](https://www.youtube.com/watch?v=Pp5AAj2aIzc)


# Measuring Capacitor

* [#135: Measure Capacitor ESR with an Oscilloscope and Function Generator](https://www.youtube.com/watch?app=desktop&v=115erzCCxgE)


# Measuring RF Cable Impedance

* [Finding RF Cable Impedance](https://hackaday.com/2020/05/24/finding-rf-cable-impedance/)


# Transistor Curve Tracer

* [Simple Transistor Curve Tracer for Oscilloscopes.](https://www.youtube.com/watch?v=V5UJiaRwV88)
  * [Simple but effective Transistor Curve Tracer circuit](https://www.eddybergman.com/2017/06/simple-but-effective-transistor-curve.html#google_vignette)
  * [Transistor Curve Tracer](https://archive.org/details/ElektorMagazine/Elektor%5Bnonlinear.ir%5D%201980-09/page/n37/mode/2up)


# Oscilloscope Probes
An ideal oscilloscope probe would provide an exact copy of the signal you are probing. But in the real world, your probe becomes a part of the circuit under test because the probes and accessories attached to your device under test cause probe loading to the circuit.
Depending on the probe and the circuit, the probe loading may cause unwanted side effects such as overshooting, ringing, and DC offset problems in the time domain.

* [Demystifying RCRC and RC Probes](https://www.keysight.com/us/en/assets/7018-04792/application-notes/5992-0694.pdf)

* [Non Contact Scope Probe Costs Nearly Nothing](https://hackaday.com/2024/05/06/non-contact-scope-probe-costs-nearly-nothing/)

* [The Secret Life of Oscilloscope Probes](http://www.dfad.com.au/links/THE%20SECRET%20WORLD%20OF%20PROBES%20OCt09.pdf)
* [How an Oscilloscope Probe Works, and other Stories](https://hackaday.com/2017/03/15/how-an-oscilloscope-probe-works-and-other-stories/)
* [Oscilloscope Probes: What You Need to Know](https://www.youtube.com/watch?app=desktop&v=XQlPSFqhG08)
* [EEVblog #1367 - 5 Types of Oscilloscope Passive Probes COMPARED](https://www.youtube.com/watch?v=rzo4Ntxqu1E&feature=youtu.be)
* [Oscilloscope Current Probe for RF](https://www.elektormagazine.com/labs/oscilloscope-current-probe-for-rf)
* [MAKE YOUR OWN CURRENT CLAMP PROBE](https://hackaday.com/2018/01/27/make-your-own-current-clamp-probe/)
* [Little Bee: An affordable, high-performance current & magnetic field probe](https://www.crowdsupply.com/weston-braun/little-bee)
* [This Modular Differential Probe Shows Great Attention To Detail](https://hackaday.com/2021/08/25/this-modular-differential-probe-shows-great-attention-to-detail/)
* [Active Signal Tracer Probe Has AGC](https://hackaday.com/2022/06/24/active-signal-tracer-probe-has-agc/)
* [Near Field EMI Probes: Any Good?](https://hackaday.com/2023/01/03/near-field-emi-probes-any-good/)


## High Frequency Probe

* [A FET Oscilloscope Probe For Higher Frequencies](https://hackaday.com/2022/04/23/a-fet-oscilloscope-probe-for-higher-frequencies/)


## Passive Voltage Probe

* [EEVblog #453 - Mysteries of x1 Oscilloscope Probes Revealed](https://www.youtube.com/watch?app=desktop&v=OiAmER1OJh4)


## Active Voltage Probe

* [EEVblog #1368 - Active Oscilloscope Probes COMPARED (Part 2)](https://www.youtube.com/watch?v=WlSb8hdFtTY&feature=youtu.be)


## Current Probe

* [Understanding, Selecting, and Effectively Using Current Probes](https://www.digikey.com/en/articles/understanding-selecting-effectively-using-current-probes)
* [Micsig CP2100A Best Affordable Current Probe](https://www.youtube.com/watch?v=8zW4j0euN8A)


## High Voltage Probe


## High Current Probe

* [High Current Measurement Probe For Oscilloscopes](https://hackaday.com/2021/04/11/high-current-measurement-probe-for-oscilloscopes/)


## Single-Ended Probe


## Differential Probe

* [Differential Probe Clocks At 100MHz And $200](https://hackaday.com/2021/12/12/differential-probe-clocks-at-100mhz-and-200/)


# Probe Calibration

* [Calibrate probes on Rigol Oscilloscope](https://www.youtube.com/watch?v=vVt1xCKWkJY&feature=youtu.be)


# Probing Problems

* [I Only Probed the Board With a Scope - Why Did My Board Crash?](https://www.youtube.com/watch?v=MJpDFnRQw8s)
* [Probe Tips: Beware of capacitive loading of oscilloscope probes on your circuit operation](https://www.youtube.com/watch?v=sPSJnj7gVJA)


## Oscilloscope Probe to Wire Adapter

* [3D Printable Scope Probe Adapts To Your Needs](https://hackaday.com/2021/10/21/3d-printable-scope-probe-adapts-to-your-needs/)


## Electromagnetic Interference (EMI)

* [EMC debugging - Near field Electric field probes](https://www.youtube.com/watch?v=S27zk_Gj9nU)
* [EMC debugging - Near field Magnetic field probes](https://www.youtube.com/watch?v=l2YS1s6HxHU)
* [EMI](https://www.youtube.com/playlist?list=PLT84nve2j1g9_TabWCWUy1LrVnHN_EHvT)



--------



# Oscilloscope Safety

* [Everything you need to know when buying/using an Oscilloscope! EB#49](https://www.youtube.com/watch?v=d58GzhXKKG8)



--------



# Scope Fun


## Chaotic Circuits
A Chua's circuit (also known as a Chua circuit)
is a simple electronic circuit that exhibits classic chaotic behavior.
It's ease of construction and a real-world example of a chaotic system,
leading some to declare it ["a paradigm for chaos"][05].

* [Chua circuit](http://www.scholarpedia.org/article/Chua_circuit)
* [Building a Chaotic Oscillator from Common Components](https://cpldcpu.wordpress.com/2020/06/15/building-a-chaotic-oscillator/)
* [Chaos Theory in Practice: Chua’s Circuit](https://hackaday.com/2014/12/07/chaos-theory-in-practice-chuas-circuit/)
* [Generating Truly Random Sequences]()
* [Chua's circuit](https://en.wikipedia.org/wiki/Chua%27s_circuit)
* [Building Chua's Circuit](http://www.chuacircuits.com/howtobuild1.php)
* [Robust Op Amp Realization of Chua's Circuit](http://www.physics.smu.edu/scalise/chaoscircuit.pdf)

* [#1937 Chua's Circuit (part 1 of 2)](https://www.youtube.com/watch?v=Vgq6zHTigIg)
* [#1938 Chua's Circuit (part 2 of 2)](https://www.youtube.com/watch?v=x2lgAF5GsnI)


## Lorenz Attractor Circuits

* [#108 lorenz attractor](https://www.youtube.com/watch?v=z71iU72Klmg)
* [#1583 Lorenz Attractor: Analog and Digital Computers](https://www.youtube.com/watch?v=c14aXxlSxZk)
* [#1893 Lorenz Attractor PCB](https://www.youtube.com/watch?v=0wD2WbG7loU)


## Vector Display / X-Y Mode
Most dual channel oscilloscopes have an XY mode in which the timebase is replaced by the second channel, so instead of a constant sweep frequency the two inputs to be plotted relative to each other.

* [STM32 Draws on Scope: Rendering 3D Graphics On An Oscilloscope](https://hackaday.com/2024/03/10/stm32-draws-on-scope/)
  * [GetHub: Rendering 3D Graphics On An Oscilloscope](https://github.com/lowbyteproductions/3d-oscilloscope-renderer)

* turned his oscilloscope into a vector display - [WATCH VIDEO ON A OSCILLOSCOPE WITH AN ESP32](https://hackaday.com/2017/12/23/watch-video-on-a-oscilloscope-with-an-esp32/)
* [Scopetrex Is A Game Console… For Your Oscilloscope!](https://hackaday.com/2020/05/07/scopetrex-is-a-game-console-for-your-oscilloscope/)
* [Oscilloscope mushrooms on the Rigol DS1054Z](https://www.youtube.com/watch?v=NK5tK6SBO-c)
* [Vector display](https://trmm.net/Vector_display/)
* [Vector Display Introduction](https://www.nycresistor.com/2012/09/03/vector-display/)
* [Comparing XY Mode on Analog and Digital Oscilloscopes](https://www.youtube.com/watch?v=1tTeXPmbxW0)

* [Drawing Knots On An Oscilloscope Using Analog Means](https://hackaday.com/2023/02/22/drawing-knots-on-an-oscilloscope-using-analog-means/)

* [The Right Equipment Makes a Difference for Digital Oscilloscope Music](https://hackaday.com/2023/07/29/the-right-equipment-makes-a-difference-for-digital-oscilloscope-music/)



-------



# VISA (Virtual Instrument Software Architecture)

* [HOW TO CONTROL YOUR INSTRUMENTS FROM A COMPUTER: IT’S EASIER THAN YOU THINK](https://hackaday.com/2016/11/16/how-to-control-your-instruments-from-a-computer-its-easier-than-you-think/)
* [CONTROLLING YOUR INSTRUMENTS FROM A COMPUTER: DOING SOMETHING USEFUL](https://hackaday.com/2016/11/29/controlling-your-instruments-from-a-computer-doing-something-useful/)
* [Ollie: Voice control for oscilloscopes](https://github.com/jmwilson/ollie)
* [How To Talk To Your Scope](https://hackaday.com/2023/11/21/how-to-talk-to-your-scope/)


# LabView

* [What is LabVIEW?](https://www.youtube.com/watch?v=P8y3tKJQadEG)
* [LabVIEW in Linux](http://danielcentore.com/labview-in-linux/)
* [LabVIEW 2018 Additional Installation Information](https://intra.kth.se/polopoly_fs/1.338137.1555493593!/labview_lin_extrainfo.pdf)


# IEEE-488.1 / GPIB / SCPI

* [How to Program Test Tools with Python - Workbench Wednesdays](https://www.youtube.com/watch?v=1HQxnz3P9P4)
* [SCPI: On Teaching Your Devices The Lingua Franca Of Laboratories](https://hackaday.com/2021/11/17/scpi-on-teaching-your-devices-the-lingua-franca-of-laboratories/)
* [Save Money and Have Fun Using IEEE-488](https://hackaday.com/2022/01/31/save-money-and-have-fun-using-ieee-488/)
* [GPIB to USB, with a Python API](https://hackaday.com/2014/05/09/gpib-to-usb-with-a-python-api/)


# LAN eXtensIons (LXI)
LXI, or LAN eXtensions for Instrumentation is a modern control standard for connecting electronics instrumentation which supports ethernet. It replaces the older GPIB standard, giving much better performance and lower cost of implementation.

* [Open Source LXI Tools Free Us From Vendor Bloat](https://hackaday.com/2022/02/18/open-source-lxi-tools-free-us-from-vendor-bloat/)


# Computer Control a Rigol Oscilloscope

* [Controlling a Rigol DS1052E Oscilloscope from Ubuntu Linux](http://hccc.org.uk/usbtmc.html)
* [Rigol's PC software: Ultra-Sigma and beyond](https://core-electronics.com.au/tutorials/ultra-sigma-rigol-pc-software-tutorial.html)
* [Driverless Rigol DS1054Z screen capture over LAN](https://hackaday.io/project/5807-driverless-rigol-ds1054z-screen-capture-over-lan)
* [How To Control Your Instruments From A Computer](https://hackaday.com/2016/11/16/how-to-control-your-instruments-from-a-computer-its-easier-than-you-think/#more-228539)
* [GlScopeClient: A Permissively-Licensed Remote Oscilloscope Utility](https://hackaday.com/2019/05/30/glscopeclient-a-permissively-licensed-remote-oscilloscope-utility/)
* [alk to your scope, and it obey](https://hackaday.com/2019/03/03/talk-to-your-scope-and-it-will-obey/)


# Scope Test Board

* [A Scope Test Tool You Can Build With Just a Pico](https://hackaday.com/2024/05/31/a-scope-test-tool-you-can-build-with-just-a-pico/)



[01]:https://hackaday.com/2018/09/11/the-pre-crt-oscilloscope/
[02]:https://hackaday.com/2018/11/01/cut-through-the-noise-see-tiny-signals/
[03]:http://dangerousprototypes.com/2010/12/06/bus-pirate-piratescope/
[04]:https://en.wikipedia.org/wiki/Vernier_scale
[05]:https://www.worldscientific.com/worldscibooks/10.1142/1997
[06]:https://www.youtube.com/watch?v=Iq4QlfH-oqk
[07]:https://eleshop.eu/rigol-ds1054z.html
[08]:https://www.rigolna.com/products/digital-oscilloscopes/1000z/
[09]:https://www.youtube.com/watch?v=Xo9wLOAwW_o
[10]:https://www.youtube.com/watch?v=aNy6-CLS3BI
[11]:https://assets.testequity.com/te1/Documents/pdf/rigol/Rigol-DS1054Z-Manual.pdf
[12]:
[13]:
[14]:
[15]:
[16]:
[17]:
[18]:
[19]:
[20]:

