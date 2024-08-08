<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>

---

A Joule Thief is a simple circuit that takes advantage of the inductive kickback produced by an inductive element (a wound toroid in this case) to step up the voltage.

The joule thief can operate with very low voltages, this means it can work with batteries which would normally be considered "dead", taking energy from them in a seemingly impossible way, hence it's name.

The Joule Thief Circuit is a voltage booster circuit which converts a constant low voltage input into a periodic output of a higher voltage.

A joule thief is nothing but a primitive switching regulator. There is nothing about it's design that restricts it to a single 1.5V cell. Most use a 1.5V cell for size reasons. And because a single 1.5V cell, at 1V, can easily be boosted to 3+ volts to power a white or other 3+ Vf leds.
I've used a joule thief self osscilating circuit with 2 AA to power an LED for months without issues, with a random ferrite ring and Telco wire. Nothing optimized.
If the cell is full, the oscillating circuit gets saturated faster and less energy is needed to boost it to saturation. It will simply last longer.
[Joule thief - Why only single celled?](https://electronics.stackexchange.com/questions/319797/joule-thief-why-only-single-celled)

[two versions of the joule thief](https://blog.zakkemble.net/joule-thief/)
[How to Build a Joule Thief & Steal Battery Power](https://www.arrow.com/en/research-and-events/articles/how-to-build-a-joule-thief-and-steal-battery-power)

- [Easy Joule Thief Circuit](https://www.instructables.com/Easy-Joule-Thief-Circuit/)
- [Easy Joule Thief Soldering Project](https://www.instructables.com/Easy-Joule-Thief-Soldering-Project-1/)
- [19 Projects tagged with "Joule thief"](https://hackaday.io/projects?tag=Joule%20thief)

- [Joule Thief PCB: Power from "dead" batteries!](https://www.hackster.io/glowascii/joule-thief-pcb-power-from-dead-batteries-651d67)
- [Joule Thief LED Tea Light Adapter](https://www.hackster.io/glowascii/joule-thief-led-tea-light-adapter-c7c11c)
- [1.5 to 9V Converter Uses Supercharged Joule Thief PCB](https://rustybolt.info/wordpress/?p=7643)

- [A Joule Thief Circuit](https://electronut.in/a-joule-thief-circuit/)
- [Multi-Videos for Joule Thief](https://www.youtube.com/user/RimstarOrg/search?query=joule%20thief)
- [Joule Thief Cat Kit: Live Assembly // Tech Highlight](https://www.hackster.io/videos/1208)

- <https://en.wikipedia.org/wiki/Joule_thief>
- [Joule Thief Information Page](http://cs.yrex.com/ke3fl/htm/JouleThief/JouleThief.htm)
- [Itty Bitty Joule Thief](https://www.instructables.com/id/Itty-Bitty-Joule-Thief/)

- [3 Best Joule Thief Circuits](https://www.homemade-circuits.com/1-watt-led-driver-using-joule-thief/)
- [Optimized Joule Thief Circuit](https://devopedia.org/joule-thief-circuit)

- [Making a Simple Joule Thief (made Easy)](https://www.instructables.com/id/Making-A-Simple-Joule-Thief-made-easy/)

- [Thief of Joules](http://cachivacheselectronicos.blogspot.com/2015/04/test-ladron-de-jouls-primer-proyecto-en.html)


# Transistor Selection

- [All About PNP Transistors](https://hackaday.com/2024/07/21/all-about-pnp-transistors/)
- [Biasing That Transistor: The Common Emitter Aamplifier]

Any small generic NPN transistors should work as long as you bias it right.
However, an NPN will work best as you are performing switching work, rather than amplifying work to get the 'HV' pulse out of the transformer. The more turns you put into the transformer the bigger the power spike you'll get out of it, but the longer it will take to charge. Also, I'd guess that technically there will be both a minimum # and maximum # of turns you could use before the thing pretty much wouldn't work right due to timing/frequency issues.
2N3904, BC547B, 2SC2500, BC337, 2N2222, 2N4401 or other NPN. Vceo= 30 V, P= 0.625 W.

- [How To Find a Transistor Replacement](https://www.youtube.com/watch?v=jtcgoWtwK6E)


# High Voltage Joule Thief

- [HV Joule Thief](https://hackaday.io/project/10477-hv-joule-thief)


# Super Joule Thief

- [Make a SUPER Joule Thief Light!](https://www.instructables.com/id/Make-a-SUPER-Joule-Thief-Light/)
- [Powering Neon With a Joule Thief](https://hackaday.com/2020/03/14/powering-neon-with-a-joule-thief/)
- [Playing with Neons (NE2 and MTX90)](https://www.youtube.com/watch?v=M6P-adLrXBI)


# Othe Battery Options

- [Water Powered Calculator (Original)](https://www.instructables.com/id/Water-Powered-Calculator/)


# No Toroid Coil

- [Make a Joule Thief Coil Without a Ferrite Toroid - Instructables](https://www.instructables.com/Make-A-Joule-Thief-Coil-Without-A-Ferrite-Toroid/)
- [Make a Joule Thief Coil Without a Ferrite Toroid](https://trybotics.com/project/Make-A-Joule-Thief-Coil-Without-A-Ferrite-Toroid-25967)
- [Joule Thief, No Toroid Coil - How to Build](https://www.youtube.com/watch?v=g2jMrNFV4nQ)


# Toroid Design Considerations

- [How Toroids Work](https://www.youtube.com/watch?v=Lx2g-fVe8Ds)
- [Toroid Design Considerations](https://www.magneticsgroup.com/wp-content/uploads/2019/08/DESIGN-TOROIDS.pdf)
- [About Toroid inductors and magnetic field containment](https://www.youtube.com/watch?v=c8YYLla2I8U)


# Wireless LED

- [Wireless LEDs - BUILD or BUY?](https://www.youtube.com/watch?v=jdc_0r5pJPc)
- [Wireless LEDs Aren’t Really Magic](https://hackaday.com/2021/11/29/wireless-leds-arent-really-magic/)


# Circuit Sculpture

- [Cumin Lander](https://www.hackster.io/mohit/cumin-lander-9d9784)
- [Test Your Capacity for Circuit Sculpture with Flashing Lights](https://hackaday.com/2022/12/30/test-your-capacity-for-circuit-sculpture-with-flashing-lights/)
- [Kinetic Sculpture Achieves Balance Through Machine Learning](https://hackaday.com/2018/10/26/kinetic-sculpture-achieves-balance-through-machine-learning/)
- [The Eerie Sounds Of Ioalieia: An ESP32/Valve/Analog Hybrid Circuit Sculpture](https://hackaday.com/2022/01/15/the-eerie-sounds-of-ioalieia-an-esp32-valve-analog-hybrid-circuit-sculpture/)
- [Mohit Bhoite's Sculptures](https://www.bhoite.com/sculptures/)
  - [Mohit Bhoite's KT-15 Circuit Sculpture Is Ready for a Kitchen Landing with Its 4-Bit Timer](https://www.bhoite.com/sculptures/kt-15/)
- [TWELVE CIRCUIT SCULPTURES WE CAN’T STOP LOOKING AT](https://hackaday.com/2019/01/15/twelve-circuit-sculptures-we-cant-stop-looking-at/)
- [A little CSK satellite for a bright workstation](https://hackaday.io/project/190199-a-little-csk-satellite-for-a-bright-workstation)


# RF Detector Circuits

- [3 Simple RF Detector Circuits / Radio Signal Field Detector](https://www.youtube.com/watch?v=kJge1pN6hL8)


# Sound

- [Big Noise From A 555 And A Little Embroidery](https://hackaday.com/2022/09/14/big-noise-from-a-555-and-a-little-embroidery/)


# Touch Switch

- [TTP223 Brings Simple Touch Controls To A LED Lamp](https://hackaday.com/2022/10/04/ttp223-brings-simple-touch-controls-to-a-led-lamp/)


# Switch Mode Power Supply

- [What is a Switch Mode Power Supply?](https://www.jameco.com/Jameco/Blog/what-is-switch-mode-power-supply.html)
