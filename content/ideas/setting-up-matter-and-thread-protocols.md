<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>



* [Matter Devices You Can Buy Right Now](https://hometechhacker.com/matter-devices-you-can-buy-right-now/)
* [My Early Experiences With Matter Devices](https://hometechhacker.com/my-early-experiences-with-the-matter-protocol/)
* [Canonical's Nathan Hart Wants to Get You Started with Matter on a Raspberry Pi Running Ubuntu](https://www.hackster.io/news/canonical-s-nathan-hart-wants-to-get-you-started-with-matter-on-a-raspberry-pi-running-ubuntu-0acbd9433003)





[Matter is a new standard for smart homes][02],
created by Project Connected Home Over IP (aka Project Chip) in 2019
now call the [Connectivity Standards Alliance (CSA)][01].
The objective of Matter is to solve many of the pain points
created by proprietary software / hardware while bringing all our IoT devices together.

The [core problem Matter addresses][03] is to
makes the [device setup / commissioning][04] process easier, facilitate device interoperability,
and keep all device interactions local to your LAN without a cloud controller
via Matter's own application level protocol.
Put simply, Matter is an agreement between device manufacturer to support an interoperable application layer command set.

Thread is the wireless network layer protocol used by Matter.
Thread is a low-powered mesh-based wireless protocol,
creating a low-latency offline environment that instantly sends and receives data across devices.
As such, your Matter-certified devices continue working together even if you lose connection to the Internet or even your LAN.
Another possibility is for the device provider have the option to use WiFi or Bluetooth in place of Thread.
So to put this all cynically, Matter + Thread is a replacement for Zigbee.

But this is not complete yet,
since Matter uses the Bluetooth Low Energy (BLE) protocol to provide
a secure means to do device commissioning.
Matter used a Mobile phone, for scanning QR-codes & data entry, plus BLE for secure device communications.
[BLE is widely used to do device & application commissioning][05].
Put differently, Matter wisely choose not to re-invent the wheel for commissioning.

You are going to need at least one Matter Controller.

Sources:

* [The Way To Prepare For Matter (In Your Own Smart Home)](https://www.youtube.com/watch?v=HTOYHn5NUn0)
* [Matter: The Future of the Smart Home?](https://hometechhacker.com/matter-the-future-of-the-smart-home/)
* [You Should(n't) Care About Matter For Your Smart Home](https://www.youtube.com/watch?v=y-HpTIP46sY)
* [Matter explained: What is the next-gen smart home protocol](https://www.androidpolice.com/matter-smart-home-standard-explained/)
* [Thread and Matter Are NOT The Same: Key Differences Explained](https://www.youtube.com/watch?v=4_7yC0B21oY)
* [The Way To Prepare For Matter (In Your Own Smart Home)]()
* [Thread](https://www.youtube.com/playlist?list=PLoKOKJqgqHs9AK8cMkH3Nqyybzfv0q23D)

# What About My Home Devices?
Matter Controller - it can control any Matter certified device
Matter Bridges - it allows non-Matter devices to be controlled by a Matter Controller

Potential Matter Bridges
    Phillips Hue Bridge
    SwitchBot Hub 2
    Echo Plus (2nd Gen) ... purchased Dec 2018 ... only plug switches and bulbs over WiFi, not Thread, only on Andriod
    Samsung Hub V3 ... under consideration
    Aqara ... v2 hub will be both a Matter Controller and Matter Bridge

* [Here's How Your Old Smart Products Get Matter!](https://www.youtube.com/watch?v=azEwUi3SBJA)
* [Here's When Matter Will ACTUALLY Help Your Smart Home](https://www.youtube.com/watch?v=Rv38Gf8Io7Q)
* []()

# Build a Matter Device
* [Build a Smart Home Matter Device in 10 mins on ESP32](https://www.youtube.com/watch?v=nO45szofvOM)



[01]:https://csa-iot.org/all-solutions/matter/
[02]:https://csa-iot.org/newsroom/matter-making-the-smart-home-more-connected/
[03]:https://www.youtube.com/watch?v=8NcPWJv0nfo
[04]:https://www.youtube.com/watch?v=OSJpG2YWTGE
[05]:https://community.silabs.com/s/share/a5U1M000000ko4IUAQ/how-to-use-bluetooth-lowenergy-for-wifi-commissioning?language=en_US
[06]:
[07]:
[08]:
[09]:
[10]:
