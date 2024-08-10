<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----




# Coaxial Cable

* [UHF SO-239](https://www.amazon.com/Female-Chassis-Flange-Solder-Connector/dp/B007Q8JH4Y)
* [RF Coax Cable Connectors](http://www.fmuser.net/content/?852.html)
* [RF CONNECTORS, ATTENUATORS AND LOADS, TOGETHER WITH THEIR USES](http://www.harc.org.uk/?page=technical&sub=connectors)
* [The Modular Connector and How It Got That Way](https://hackaday.com/2018/10/02/the-modular-connector-and-how-it-got-that-way/#more-326628)
* [The BNC Connector and How It Got That Way](https://hackaday.com/2018/10/19/the-bnc-connector-and-how-it-got-that-way/)
* [Ham radio - the UHF connector and PL259 installation -Ria's Shack](https://www.youtube.com/watch?v=6A_OrkKj8Q0)
* [Ham Radio - N connectors for coaxial cable](https://www.youtube.com/watch?v=nef7BZTdu8s&list=PLaKDdkKwLCRilHQOC7lfyNfJA0PxBkkdN&index=7)

Essentials of Connector Technology

* [element14 Essentials: Connectors I](https://www.element14.com/community/docs/DOC-81482?CMP=EMC-NEWSLETTER-APR16-ESSENTIALS-CONNECTORS-1)
* [Co-Exist With Your Coax: Choose The Right Connector For The Job](http://hackaday.com/2016/03/31/co-exist-with-your-coax-choose-the-right-connector-for-the-job/)


## Coaxial Cable Types
[Coaxial cable][02] (aka "coax") is a common type of shielded data transmission cable,
which is made up of two conductors that are coaxially oriented,
but separated by a layer of dielectric insulation.
Coaxial cable is a [waveguide][01] (see this [video][14]),
designed to carry high-frequency signals,
and to protect those signals against electromagnetic interference from external sources
and to keep the signal from radiating to the outside world.

Coax is often typed (but not always) with the following convention: RG-#.
The "RG" is short for "Radio Guide," a term that dates back to obsolete World War II era standards.
The RG naming convention specify different grades of coax and their applications.
The most common RG designations seen these days are RG-6, RG-8, RG-11, RG-58, and RG-59.
RG-6 and RG-59 cables are widely used in residential settings.
RG-59 best suited to low-frequency transmissions and short cable runs,
and RG-6 the ideal choice to carry high frequency signals over long distances.

Coax comes in a bewildering number of varieties.
Below is some of the typical cables you'll come across.

| Cable Type | Outer Diameter | Center Conductor | Impedance | Typical Application | [Jonard Stripper][03] |
|:----------:|:--------------:|:----------------:|:---------:|:-------------------:|:---------------------:|
     RG-6    |  0.270 inches  |      18 AWG      |   75 Ω    | CATV/DBS/CCTV/HDTV  |      UST-500
     RG-7    |  0.320 inches  |      18 AWG      |   75 Ω    | CATV/DBS/CCTV/HDTV  |      UST-500
     RG-8    |  0.405 inches  |      13 AWG      |   50 Ω    |          AR         |
     RG-11   |  0.412 inches  |      14 AWG      |   75 Ω    | CATV/DBS/CCTV/HDTV  |      UST-500
     RG-58   |  0.195 inches  |      20 AWG      |   50 Ω    |          AR         |
     RG-59   |  0.242 inches  |      20 AWG      |   75 Ω    | CATV/DBS/CCTV/HDTV  |      UST-500
     RG-174  |  0.100 inches  |      26 AWG      |   50 Ω    |      pig tails      |      UST-175

* CATV - Cable Television
* DBS - Direct Broadcast Satellite
* CCTV - Closed-Circuit Television
* HDTV - High Definition Television
* SDI - Serial Digital Interface
* AR - Amateur Radio
* AWG - American Wire Gauge


## Coaxial Cable Connectors
Many [coaxial connector types][11] are available in the audio, video, digital, RF,
and microwave industries.
Each where designed for a specific purpose and application but their use has deversified.
Some of the widely used connector types are:

* [RCA][04] - RCA connector, sometimes called a phono connector or cinch connector, are commonly used to carry audio and video signals.
* [SMA][05] - SubMiniature version A connectors are semi-precision coaxial RF connectors for coaxial cable, with a screw type coupling mechanism. The connector has a 50 Ω impedance. It is designed for use from DC to 18 GHz.
* [SMB][10] - SubMiniature version B connectors are coaxial RF connectors that are smaller than SMA connectors.  They feature a snap-on coupling and are available in either 50 Ω or 75 Ω impedance. They designed to performance from DC to 4 GHz.
* [MCX][06] - Micro Coaxial connectors are coaxial RF connectors  th a snap-on interface and usually have a 50 Ω impedance (occasionally 75 Ω also) . They offer broadband capability from DC to 6 GHz.
* [BNC][07] - The BNC (Bayonet Neil-Conselman) connector is a miniature quick connect/disconnect RF connector used for coaxial cable and ideally suited for cable termination for miniature-to-subminiature coaxial cable (e.g., RG-58, RG-59). They are used with radio, television, and other radio-frequency electronic equipment, and test instruments. BNC connectors are made to match the characteristic impedance of cable at either 50 Ω or 75 Ω and frequencies below 4 GHz.
* [PL259][08] - Also goes by UHF connector, or Amphenol coaxial connector, it is a threaded RF connector design, from an era when UHF referred to frequencies over 30 MHz. The UHF connector is the most common connector in amateur radio applications up to 150 MHz.
* [F-Type][09] - The F connector is a coaxial RF connector commonly used for "over the air" terrestrial television, cable television, satellite television, and cable modems. It is usually connected to RG-6/U coax cable or with RG-59/U cable.
* U.FL -???
* N Connector -  handles frequencies up to 11 GHz.


## Why 50 and 75 Ohms
There is a prevalence of 50 ohm coax.
Sure, you sometimes see 75 ohm coax, but overwhelmingly, RF circuits work at 50 ohms.
Apparently in the 1930s,
radio transmitters were pushing towards higher power levels.
You generally think that thicker wires have less loss.
For coax cable carrying RF though, it’s a bit more complicated.
The impedance is a function of the dielectric material,
the diameter of the center conductor,
and RF signals exhibit the skin effect (they don’t travel in the center of the conductor)

When you put all this together,
you learn that the loss of the cable is minimized at 77 ohms for a cable with air dielectric.
Of course, that’s not 50 ohms but closer to the 75 ohms used to carry weak antenna signals in TV systems.
According to [Microwaves 101][12], choice of 50 ohms is a compromise between power handling capability
and signal loss per unit length, for air dielectric.
For cheaper commercial cables, such as those that bring CATV to your home,
an impedance 75 ohms probably was a compromise between low loss and cable flexibility.

* [Why is Coax 50 Ohms?](https://www.youtube.com/watch?app=desktop&v=I-OnQZJv35I)


## U.fl Connector

* [Three Quick Tips About Using U.FL](https://learn.sparkfun.com/tutorials/three-quick-tips-about-using-ufl)
* [How to Achieve Maximum U.fl RF Connector Reliability](https://www.youtube.com/watch?v=naJvFB52Etc)


## Sources

* [Coaxial Cable FAQs](http://www.cableorganizer.com/articles/coaxial-cable-faqs.html)
* [Coaxial Cable Solutions Guide](http://www.digikey.com/Web%20Export/Supplier%20Content/GenCable_42/PDF/GenCable_CoaxialCable.pdf?redirected=1)
* [Coaxial cable](http://en.wikipedia.org/wiki/Coaxial_cable)
* [Common Coaxial Connectors](http://ecee.colorado.edu/~kuester/Coax/connchart.htm)


# Measuring RF Cable Impedance

* [Finding RF Cable Impedance](https://hackaday.com/2020/05/24/finding-rf-cable-impedance/)


# Measuring Cable Length
Time-Domain Reflectometry (TDR) is a way to measure the time between
injecting a pulse into a cable and receiving its echo,
either from the other end of the cable or from some fault or defect along the way.

* [#323: Measure length of coax, etc. with your scope, a battery and a resistor - simple TDR](https://www.youtube.com/watch?v=z6UJPqQYzNc)



----


<div align="center">
<img src="https://imgs.xkcd.com/comics/usb_cables.png" title="From xkcd.com - Law of USB Cables: You will never have more than one which has no problems, no matter how many you get." align="center">

</div>


# USB Cables
USB cables are used to transfer data, power devices, and often both.
Sometimes, when selecting a random USB cable our devices do not work, charging is too slow, etc.
Your not sure if a crappy USB cable is the reason.

Since its introduction in 1996, USB has evolved in multiple ways
(some may say it [changed too much][22], maybe we should go back our [serial days][23]).
As a result, not all USB ports look and behave the same way
and there are some differences between them that are easy to miss.
For example, you might have noticed that your phone charges faster
when you connect it to a certain USB port on your computer.
Or you might discover that just one of your ports will allow
you to charge your phone while the computer is turned off or move data faster.

* [A Guide to Computer Ports and Adapters](https://www.laptopmag.com/articles/port-and-adapter-guide)
* [Avoid Surprises: How good are USB cables and how can you test yours?](https://www.youtube.com/watch?v=n70N_sBYepQ)
* [Is it me or is it USB?](https://www.tindie.com/products/nerfhammer/is-it-me-or-is-it-usb/)
* [Smart & Secure Fast-Charge USB Cable and Adapter](https://www.kickstarter.com/projects/andyfei/smart-and-secure-fast-charge-usb-cable-and-adapter)
* [Powering Up With USB: Untangling The USB Power Delivery Standards](https://hackaday.com/2021/09/16/powering-up-with-usb-untangling-the-usb-power-delivery-standards/)

What is a smart charging USB port? What's the difference between a smart one and a 1 or 2.1 a charger? - <https://www.quora.com/What-is-a-smart-charging-USB-port-Whats-the-difference-between-a-smart-one-and-a-1-or-2-1-a-charger>


## USB Cable Types
Your next phone or laptop will have a USB Type-C port for charging.
Type-C cables will subject to greater loads, and therefore,
will require higher levels of manufacturing tolerances.

* **USB Type-C** will not just give you data speeds which are 20 times more than USB 2.0,
but it also draws more power, A LOT more of it.
A regular Type-C cable is able to deliver 3A of current, while higher spec ones go up to 5A.
USB 2.0 can only support anywhere from 500mA up to 2A.


## Measuring USB Cable Resistance

* [Measuring USB cable resistance using USB testers](https://www.youtube.com/watch?v=9IG9wSS3F9w)


### USB-C
It’s 2019 and USB-C is still a mess - <https://www.androidauthority.com/state-of-usb-c-870996/>
[It's 2021 and USB-C is still a mess](https://www.androidauthority.com/state-of-usb-c-870996/)
The Problem With Micro-USB Cables - <https://tekbotic.com/blogs/tekblog/how-to-fix-loose-micro-usb-cable>

* [USB-C Is Taking Over… When, Exactly?](https://hackaday.com/2020/06/23/usb-c-is-taking-over-when-exactly/)
* [The Wonderful World Of USB Type-C](https://hackaday.com/2018/08/17/the-wonderful-world-of-usb-type-c/)
* [Here is why USB Type-C is AWESOME and how you can use Power Delivery for your electronics!](https://www.youtube.com/watch?v=OwAZqJ4wpJg)

* [USB-C: INTRODUCTION FOR HACKERS](https://hackaday.com/2022/12/06/usb-c-introduction-for-hackers/)
* [All About USB-C: Cable Types](https://hackaday.com/2022/12/13/usb-c-cable-types/)
* [All About USB-C: Connector Mechanics](https://hackaday.com/2022/12/20/all-about-usb-c-connector-mechanics/)
* [All About USB-C: Resistors And Emarkers](https://hackaday.com/2023/01/04/all-about-usb-c-resistors-and-emarkers/)
* [All About USB-C: Power Delivery](https://hackaday.com/2023/01/09/all-about-usb-c-power-delivery/)
* [All About USB-C: High-Speed Interfaces](https://hackaday.com/2023/01/17/all-about-usb-c-high-speed-interfaces/)
* [All About USB-C: Pinecil Soldering Iron](https://hackaday.com/2023/01/31/all-about-usb-c-pinecil-soldering-iron/)
* [All About USB-C: Manufacturer Sins](https://hackaday.com/2023/02/07/all-about-usb-c-manufacturer-sins/)
* [All About USB-C: Talking Low-Level PD](https://hackaday.com/2023/02/14/all-about-usb-c-talking-low-level-pd/)
* [All About USB-C: Replying Low-Level PD](https://hackaday.com/2023/02/22/all-about-usb-c-replying-low-level-pd/)
* [All About USB-C: Example Circuits](https://hackaday.com/2023/08/07/all-about-usb-c-example-circuits/)

* [USB-C For Hackers: Build Your Own PSU](https://hackaday.com/2023/10/12/usb-c-for-hackers-build-your-own-psu/)
* [USB-C For Hackers: Program Your Own PSU](https://hackaday.com/2023/12/04/usb-c-for-hackers-program-your-own-psu/)



-----



# USB-C Power Delivery
USB Power Delivery (PD)
USB PD Trigger
USB PD Trigger Module
Programmable Power Supply (PPS) mode

* [What is Programmable Power Supply (PPS) Fast Charging?](https://www.belkin.com/support-article/?articleNum=318878)

* [PPS For All: Directly charging lithium-ion batteries with a USB-C PD tester](https://ripitapart.com/2022/12/31/directly-charging-li-ion-batteries-with-a-usb-c-pd-tester/)

* [USB Power Delivery and Type-C](https://www.st.com/content/ccc/resource/sales_and_marketing/presentation/product_presentation/group0/5a/b1/8e/6c/2b/0d/46/3c/Apec/files/APEC_2016_USB_Power.pdf/_jcr_content/translations/en.APEC_2016_USB_Power.pdf)
* [Difference between Fast Charging, Quick Charge (QC) and USB Power Delivery (USB-PD)](https://avlab.com.tw/blog/view/41)
* [What the Tech? USB-C and Power Delivery Explained - Goal Zero](https://www.goalzero.com/blog/what-tech-usb-c-and-power-delivery/)
* [Here is why USB Type-C is AWESOME and how you can use Power Delivery for your electronics!](https://www.youtube.com/watch?v=OwAZqJ4wpJg)
* [What's the difference between PD and iQ3](https://www.bestbuy.com/site/questions/anker-powerport-pd-100w-usb-c-pd-and-usb-c-to-c-cable-6ft-white/6377818/question/3d38de72-a6e1-331b-a261-be861ec7b923)
* [Powering your projects using USB-C Power Delivery](https://www.youtube.com/watch?v=iumAnPiQSj8&t=638s)
* [USB Charger Cable Review - The Good, the Bad...and the Ugly!](https://www.youtube.com/watch?v=doMHmGatyYc&list=RDCMUCOTPsWDzNAosVd6vc3pCPHQ&start_radio=1)
* [Avoid Surprises: How good are USB cables and how can you test yours?](https://www.youtube.com/watch?v=n70N_sBYepQ)

* [Mike Rankin Wants to Make USB-C PD as Easy as 1-2-3, with His ESP32-Based USB-C PD Trigger Board!](https://www.hackster.io/news/mike-rankin-wants-to-make-usb-c-pd-as-easy-as-1-2-3-with-his-esp32-based-usb-c-pd-trigger-board-39be1086d8b1)


## Programmable Power Supply (PPS)
Programmable Power Supply (PPS) is a standard that refers to the advanced charging technology for USB-C® devices.  It can modify in real time the voltage and current by feeding maximum power based on a device's charging status.
The USB Implementers Forum (USB-IF), a nonprofit group that supports the marketing and promotion of the Universal Serial Bus (USB), added PPS Fast Charging to the USB PD 3.0 standard in 2017.  This allows data to be exchanged every 10 seconds, making a dynamic adjustment to the output voltage and current based on the condition of the receiving device's specifications
PPS' main advantage over other standards is its capability to lower conversion loss during charging.  This means that less heat is generated, which lengthens the device battery's lifespan.


## USB-C Power Delivery (PD)
USB-C Power Delivery (PD) is a fast charging technology, supported by certain iOS/Apple® and Android™/Google™/Samsung® devices, that delivers much higher levels of power than standard charging.  With up to 100W of power available, USB-C PD can even charge larger devices, like tablets and laptops.  All you need is the right wall charger and USB-C cable – and leave those heavy laptop power cables at home.
PPS and PD protocols work together where the former can renegotiate non-standard currents and voltages between the device and the charger.

* [USB Power Delivery explained: What you need to know about ubiquitous charging](https://www.androidauthority.com/usb-power-delivery-806266/)


# USB-C PD Sniffer
USB-C cables need to actively tell both ends what their capabilities are, which turns an otherwise passive device into a hidden chip in a passive looking cable.
This device "sniffs out" what are the power delivery (PD) capabilities of the USB-C cable.

* [Freshening Up Google’s USB-C PD Sniffer](https://hackaday.com/2023/11/22/freshening-up-googles-usb-c-pd-sniffer/)


## Quick Charge (QC)
This technology powers your devices faster than conventional charging, allowing you to spend less time connected to outlets.  As one of the most widely used of the fast charging technologies, Quick Charge is already in many of your favorite smartphones.  If your smartphone is Quick Charge 3.0-compatible, you can charge up to 80% in just 35 minutes.
Quick Charge 4+ is expected to work with USB Power Delivery, enabling Quick Charge accessories to fast charge a wider array of devices.  On the other hand, Quick Charge 5 is the latest in Quick Charge standards and can recharge smartphones up to 50% in just 5 minutes.


## USB PD 2.0 vs. USB PD 3.0
USB-C Power Delivery 3.0 (PD3.0) introduces a new Programmable Power Supply (PPS) mode, which allows a device to negotiate any supply of 3.3-21 V in 20 mV steps, and up to 5 A of current in 50 mA steps.

* [What's the Difference: USB PD 2.0 vs. USB PD 3.0](https://satechi.net/blogs/news/whats-the-difference-usb-pd-2-0-vs-usb-pd-3-0)


## What's the difference between PD and QC?
[USB Power Delivery (PD) vs USB Quick Charge (QC) – What’s the Difference?][13]
QC is a proprietary battery charging protocol developed by Qualcomm, used for managing power delivered over USB, mainly by communicating to the power supply and negotiating a voltage.
PD is a fast charging technology that was developed by the USB Implementers Forum. Because it’s an official part of USB technology, it can be supported by any manufacturer.

PD and QC are two different fast charging standards.
Both PD 3.0 and QC 3.0 will charge your battery faster than traditional USB. At the same time, there are important differences between the two. Depending on your phone, one or the other can be a significantly better choice.
You can’t really choose between them since devices often use one or the other.
Apple devices typically use PD, but most Android use QC.
If you live in a world of mixed devies, you’ll probably want a device that does both.

* [PD 3.0 vs QC 3.0 – What’s the Difference?](https://nerdtechy.com/pd-3-qc-3-difference)


## USB Cable Differeances

* [This is the difference between a $5 USB-C cable and a $129 USB-C cable](https://www.androidauthority.com/usb-c-cable-difference-between-cheap-expensive-3378193/)
* [Understanding different types of USB cables](https://www.androidauthority.com/different-types-of-usb-cables-804432/)
* [How long can a USB cable be?](https://www.androidauthority.com/how-long-can-a-usb-cable-be-3244520/)



------



# My Chargers
[Amazon Basics 30W One-Port USB-C Wall Charger](https://www.amazon.com/dp/B087MFL8DM?th=1)
with Power Delivery PD for Tablets & Phones (iPhone 15/14/13/12/11/X, iPad, Samsung, and more)
is **not** a PPS.
Its a PD 3.0 with a power deliver of up to 30W (5V @ 3A, 9V @ 3A, 15V @ 2A, 20V @ 1.5A)


## Instructions for Use of ZY12PDN

* <https://www.amazon.com/AITRIP-Charging-Trigger-Detector-Terminal/dp/B098WPSMV9>
* [Notes on USB PD Triggers (And ZY12PDN Instructions)](https://www.alexwhittemore.com/notes-on-usb-pd-triggers-and-zy12pdn-instructions/)
* [Open-Source Firmware for ZY12PDN USB-PD](https://github.com/manuelbl/zy12pdn-oss)
* [DIY USB Type-C Power Delivery Trigger Board](https://www.instructables.com/DIY-USB-Type-C-Power-Delivery-Trigger-Board/)
* [How to power ANYTHING using USB-C Power Delivery and the ZY12PDN PD Trigger Board](https://www.youtube.com/watch?v=aIHj3qMRqqE)
* [Power Delivery Board - USB-C (Qwiic) Hookup Guide](https://learn.sparkfun.com/tutorials/power-delivery-board---usb-c-qwiic-hookup-guide/all)

To enter ZY12PDN programming mode:

1. With the device unplugged, press and hold the button while plugging in.
When you do this, the LED will rapidly flash colors to indicate that you’re in programming mode.
2. Once you let go, the LED will go Red, and 5V will be present on the output.
3. Click the button to pick your preferred fixed mode.
While you select, output will remain at 5V.
Click repeatedly to select mode:
    * Red: Selectable mode, 5V present
    * Yellow: 9V
    * Green: 12V
    * Ice/Teal: 15V
    * Blue: 20V
    * Purple: Highest available. In this mode, the trigger will pick the highest power profile the charger advertises
    * White: Auto-cycle. In this mode, the trigger will cycle through available profiles.
    It’s just as if you plugged the trigger in in selectable mode, and clicked the button once a second indefinitely.
    Useful for testing I suppose.

The ZY12PDN always outputs 5V first, then it sets whatever voltage it’s fixed too or negotiated.


## The Annoyances of USB Charging
Most computers' USB ports can only charge smartphones slowly -- at 0.5 Amp max. Charge current, measured in Amp, indicates how fast it charges; e.g., 1.0 Amp means charging twice as fast as 0.5 Amp.

Worse yet, most computers' USB ports can't charge iPad or other tablets because they require higher charge current (1.0 Amp or higher). Some can still be charged, but very slowly.

Compatibility issues: USB chargers from different vendors often don't play nice with each other. A few examples: (1) the official iPad charger can't charge Samsung Galaxy tablets and some other tablets; (2) the official Samsung Galaxy tablet charger can't charge iPad; (3) some after-market chargers can charge one type of devices (iPad or Android tablet) at high speed (2 Amp or higher) but they charge the other type of devices at much reduced speed.

Many after-market chargers don't charge your phone or iPad/tablet as fast as they claim: many may claim they can charge at 1 Amp for phones and 2 Amp for iPad and other tablets, but the actual charging speed may be just half of that. That include some the so-called Smart or Universal chargers that are supposed to be cable to charge both iPad and other tablets at 2 Amp or higher.

Hacker attack! If you use a regular USB cable to connect your smartphones to a computer that has been compromised by a hacker, it is possible for the hacker to steal data off your phone; or worse, compromise your phone. It has been found that, it is even possible to hide a hacking device inside a normal-looking charger that is capable of stealing data from your phone or compromising it. Be careful when connecting your phone/tablet to a public computer or charger.
Introducing Smart & Secure Fast-Ch

They stop fitting snug in your device. They get loose, they fall out and stop charging or transferring data


# Cable Types


## Standard USB
Standard USB uses a master/slave architecture;
a host acts as the master device (aka host) for the entire bus, and a USB device acts as a slave (aka peripheral).
If implementing standard USB cable,
you must have one devices assume one the slave role, with computers generally set up as the hosts.


## USB On-The-Go (OTG)
How usb OTG works(master/slave) - <https://stackoverflow.com/questions/11338076/how-usb-otg-worksmaster-slave>

[USB On-The-Go][20] (USB OTG or just OTG) is a specification that allows USB devices,
such as tablets or smartphones, to act as a host (when they normally don't),
allowing other USB devices, such as USB flash drives, digital cameras, mice or keyboards, to be attached to them.
Use of USB OTG allows those devices to switch back and forth between the roles of host and slave device.

In the absence of USB OTG, cell phones often implemented slave functionality
to allow easy transfer of data to and from computers.
Such phones, as slaves, could not readily be connected to printers as they also implemented the slave role.
USB OTG directly addresses this issue.

A typical (but not only) USB OTG cable has a OTG A-device with a Type-A USB connector
and OTG B-device with a Type-Mini-B USB connector.
The OTG A-device is a power supplier (master/host), and an OTG B-device is a power consumer (slave/peripheral).
The host and peripheral modes may be exchanged later by using Host Negotiation Protocol (HNP).

OTG adds a fifth pin to the standard USB connector, called the ID-pin.
The micro-A plug has the ID pin grounded,
while the ID in the micro-B plug is floating.
A device with a micro-A plug inserted becomes an OTG A-device,
and a device with a micro-B plug inserted becomes a B-device.
The type of plug inserted is detected by the state of the pin ID.
(see diagram [here][21]).

An important evolution is taking place now, and that is USB Dual Role.
[USB Dual Role is to replaces USB On-The-Go][24].


## SuperSpeed USB (aka USB 3.X)
USB 3.0 was also marketed as SuperSpeed USB.
Most manufacturers use the SuperSpeed USB logo to let you know that you’re dealing with a USB 3.0 port.
If you see the "SS" prefix in front the regular USB logo, you successfully identified the USB 3.0 port.

* [So what's all this USB 3.0, 3.1, 3.2, SuperSpeed and SuperSpeedPlus?](http://xillybus.com/tutorials/usb-superspeed)



[01]:http://en.wikipedia.org/wiki/Waveguide_(electromagnetism)
[02]:http://en.wikipedia.org/wiki/Coaxial_cable
[03]:http://www.jonard.com/jonard-ecommerce/control/category/~category_id=WIRE_STRIPPERS
[04]:http://en.wikipedia.org/wiki/RCA_connector
[05]:http://en.wikipedia.org/wiki/Sma_connector
[06]:http://en.wikipedia.org/wiki/MCX_connector
[07]:http://en.wikipedia.org/wiki/Bnc_connector
[08]:http://en.wikipedia.org/wiki/PL259
[09]:http://en.wikipedia.org/wiki/F_connector
[10]:http://en.wikipedia.org/wiki/SMB_connector
[11]:http://ecee.colorado.edu/~kuester/Coax/connchart.htm
[12]:http://www.microwaves101.com/encyclopedias/why-fifty-ohms
[13]:https://nerdtechy.com/pd-3-qc-3-difference
[14]:https://www.youtube.com/watch?v=H09w5YSnpGI
[15]:
[16]:
[17]:
[18]:
[19]:
[20]:https://en.wikipedia.org/wiki/USB_On-The-Go
[21]:https://www.quora.com/How-different-is-a-normal-usb-cable-from-OTG-usb-cable
[22]:https://www.youtube.com/watch?v=36CKsP9YQ1E
[23]:https://www.youtube.com/watch?v=4mi0kLLLAOs
[24]:https://blogs.synopsys.com/tousbornottousb/2018/05/03/usb-dual-role-replaces-usb-on-the-go/
[25]:
[26]:
[27]:
[28]:
[29]:
[30]:
