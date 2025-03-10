<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------





* [Antenna Basics: Radiation Patterns, Permittivity, Directivity, and Gain](http://www.allaboutcircuits.com/technical-articles/antenna-basics-field-radiation-patterns-permittivity-directivity-gain/)
* [Radio Antenna Mismatching: VSWR Explained](https://hackaday.com/2018/08/17/radio-antenna-mismatching-vswr-explained/)

* [Antennas](https://www.youtube.com/watch?v=rokAuaL2E74)
* [The Physics Behind an Antennas](https://hackaday.com/2019/07/11/the-physics-behind-antennas/)
* [Start Your Path to Becoming an Antenna Guru](https://hackaday.com/2016/11/27/start-your-path-to-becoming-an-antenna-guru/)
* [KiwiSDR Vs RaspberrySDR — A Tale Of Two SDRs](https://hackaday.com/2020/09/30/kiwisdr-vs-raspberrysdr-a-tale-of-two-sdrs/)

* [Improving Cheap SDR Antennas](https://hackaday.com/2021/07/19/improving-cheap-sdr-antennas/)

* [Spy Radio: Antenna Considerations](https://www.youtube.com/watch?v=UPwdYnxku6E)




# RTL-SDR on Mac OS
Nice starter project.
This project talks though the signal processing behind the GNU Radio flowgraph for receiving and demodulating FM radio broadcast signals.

* [RTL-SDR on Mac OS Part 1: Install & Setup](https://www.hackster.io/whitney-knitter/rtl-sdr-on-mac-os-part-1-install-setup-4d23da)
* [RTL-SDR on Mac OS Part 2: FM Radio Receiver DSP](https://www.hackster.io/whitney-knitter/rtl-sdr-on-mac-os-part-2-fm-radio-receiver-dsp-1b7385)


# Satellite Weather Images

* [Get Your Weather Images Straight From The Satellite](https://hackaday.com/2020/03/14/get-your-weather-images-straight-from-the-satellite/)
* [R2Cloud Project](https://github.com/dernasherbrezon/r2cloud)
* [How To Get Live Satellite Images Directly From Space](https://www.youtube.com/watch?v=icADyjm3PBE)


# Satellite Antenna

* [Mini Satellite-Antenna Rotator](https://www.sarcnet.org/rotator-mk1.html)






Need a SMA Panel Jack connector

* [Antenna Basics](http://www.rohde-schwarz-usa.com/rs/rohdeschwarz/images/8GE01_Antenna_Basics.pdf)
* [Understanding Antenna Specifications and Operation](http://www.digikey.com/en/articles/techzone/2011/mar/understanding-antenna-specifications-and-operation)
* [understanding antennas](http://www.antenna-theory.com/)
* [The Electromagnetic Spectrum](http://cnx.org/content/m42444/latest/?collection=col11406/1.7)
* [antennavis - Antenna Visualization Toolkit](http://manpages.ubuntu.com/manpages/trusty/man1/antennavis.1.html)
* [Understanding and Using Antenna Radiation Patterns](http://www.astronwireless.com/topic-archives-antenna-radiation-patterns.asp)

* [Radio Antenna Fundamentals Part 1 1947](https://www.youtube.com/watch?v=JHSPRcRgmOw&t=226s)
* [Radio Antenna Fundamentals - Part 2 1947](https://www.youtube.com/watch?v=EtEBxY8TvuE&t=8s)

The white paper [Antenna Basics][63] instructs you in the functionality of antennas
starting with Hertz’s Antenna Model and review the fundamentals of wave propagation.
It introduces the definitions of antenna characteristics
and the principle parameters of antenna specifications.
There are also example characteristics of several popular antennas shown
with a discussion on the trade-offs and benefits of each design.








---------------



Like all radio devices, to make optimal use of the RTL-SDR, a good antenna is need.
The 145mm [monopole antenna][41] that comes with my [NooElec R820T SDR & DVB-T][40] dongle
is not at all appropriate for the wide range of things I wish to do with this device.
A [discone antenna][42] is a good general antenna for the RTL-SDR as they are extremely wideband,
and can be engineered to be useful over most of RTL-SDR's tuneable range.
There are several good sources for designing a discone antenna, some of better are listed below:

* [Home Made Coat Hanger Discone](http://www.rtl-sdr.com/home-made-coat-hanger-discone/)
* [VE3SQB ANTENNA DESIGN PROGRAMS](http://www.ve3sqb.com/)
* [Discone Antenna Calculator](http://www.changpuak.ch/electronics/calc_11.php)
* [PRACTICAL ANTENNA DESIGN: 140-150 MHZ VHF TRANSCEIVERS](http://files.radioscanner.ru/files/download/file311/practical_antenna_design.pdf)
* [White Paper: Discone Antenna Design](http://www.hipoint.ca/whitepapers/WhitePaper_DisconeAntenna.pdf)
* [Notes on HF Discone Antennas](http://w4rnl.net46.net/download/discone.pdf)

* [Review: Nooelec Nano 3](http://www.radioforeveryone.com/2017/10/review-nooelec-nano-3_17.html)

With the exception of "Notes on HF Discone Antennas",
these sources lack any rigorous analysis of what performance can be expected from the discone antenna
and how it might compare to the simple antenna that comes with the RTL-SDR.
For example, I couldn't find basic things like a [radiation patttern][43] for the discone antenna.
In this posting I set out to perform this analysis on my DIY discone antenna.
In doing this, I start out with a short, high-level tutorial on the core electromagnetic principles
related to antenna design and build up to the analysis and my antennas final physical specifications.


# The Electromagnetic Spectrum
[Radio frequency (RF)][01] or [radio spectrum][02] refers to the part of the [electromagnetic spectrum][03] frequencies lower than around 300 GHz (or, equivalently, wavelengths longer than about 1 mm).
Electromagnetic waves in this frequency range, called [radio waves][04], can travel through the earths atmosphere with ease and are used for [radio communication][05] and various other technologies.
Above 300 GHz, the absorption of electromagnetic radiation by Earth's atmosphere is so great that the atmosphere is effectively opaque, until it becomes transparent again in the near-infrared and optical window frequency ranges.

![em opacity](img/posts/jekyll-posts/atmospheric_electromagnetic_opacity.png, "Electromagnetic transmittance, or opacity, of the Earth's atmosphere")

The Earth's atmosphere stops most types of electromagnetic radiation from space from reaching Earth's surface. This illustration shows how far into the atmosphere different parts of the EM spectrum can go before being absorbed. Only portions of radio and visible light reach the surface.

![em absorption](img/posts/jekyll-posts/em_absorption.jpg, "Electromagnetic absorption by the Earth's atmosphere")

Electromagnetic Spectrum

| Name | Wavelength | Frequency (Hz) | Photon Energy (eV) |
|:----:|:----------:|:--------------:|:------------------:|
| Gamma Ray | less than 0.01 nm | more than 30 EHz | 124 keV – 300+ GeV |
| X-Ray | 0.01 nm – 10 nm | 30 EHz – 30 PHz | 124 eV – 124 keV |
| Ultraviolet | 10 nm – 380 nm | 30 PHz – 790 THz | 3.3 eV – 124 eV |
| Visible | 380 nm – 700 nm | 790 THz – 430 THz | 1.7 eV – 3.3 eV |
| Infrared | 700 nm – 1 mm | 430 THz – 300 GHz | 1.24 meV – 1.7 eV |
| Microwave | 1 mm – 1 meter | 300 GHz – 300 MHz | 1.24 µeV – 1.24 meV |
| Radio | 1 mm – 100,000 km | 300 GHz – 3 Hz | 12.4 feV – 1.24 meV |

>Note: frequency x wavelength = 299,792,458 m/s (speed of light in vacuum).
1 eV (electron volt) is a unit of energy equal amount of energy gained (or lost) by the charge of a single electron moved across an electric potential difference of one volt.
[For comparisons][39], one trillion electronvolts  (1 Tev) about the kinetic energy of a flying mosquito and
6.24×10^20 eV is consumed by a single 100-watt light bulb in one second.

![Electromagnetic Spectrum](img/posts/jekyll-posts/electromagnetic-spectrum.jpg, "xxx")


## The Radio Spectrum
It is within the Radio and Microwave sections of the electromagnetic spectrum,
where the absorption by the atmosphere is minimal,
mankind has discoved how it can be uses for [radio or wireless][05] transmission of signals.
Naturally occurring radio waves are also made by lightning, or by astronomical objects.
Man-made radio waves are used for fixed and mobile radio communication, broadcasting,
radar, navigation systems, communications satellites, computer networks, and innumerable other applications.
Different frequencies of radio waves have different propagation characteristics in the Earth's atmosphere:

* long waves may cover a part of the Earth very consistently
* shorter waves can reflect off the ionosphere and travel around the world
* much shorter wavelengths bend or reflect very little and travel on a line of sight.

To prevent [interference][08] between different users, the artificial generation and use of radio waves is strictly regulated by law,
and coordinated by an international body called the [International Telecommunications Union (ITU)][09]
and the [Federal Communications Commission (FCC)][10] within the United States.
World wide, the radio spectrum is divided into a number of [radio bands][02] on the basis of frequency, allocated to different broad uses.
Within a region of the world, further regulation is applied to the spectrum.
For example, within the United States, the FCC is responsible for the [allocation of radio spectrum][11] for specific uses, power levels, area of usage, etc.
This process is sometimes called [spectrum management][12],
where a bands or small section of the spectrum of radio communication frequencies are set aside for the same purpose.
Each of these bands has a basic [bandplan][07] which dictates how it is to be used and shared, to avoid interference and to set protocol for the compatibility of transmitters and receivers.

| Band Name | Abbreviation | ITU Band | Frequency / Wavelength | Example Uses |
|:---------:|:------------:|:--------:|:----------------------:|:------------:|
| Tremendously low frequency | TLF | NA | less than 3 Hz / greater than 100,000 km | Natural and artificial electromagnetic noise |
| Extremely low frequency | ELF | NA | 3–30 Hz / 100,000 km – 10,000 km | Communication with submarines |
| Super low frequency | SLF | NA | 30–300 Hz / 10,000 km – 1000 km | Communication with submarines |
| Ultra low frequency | ULF | NA | 300–3000 Hz / 1000 km – 100 km | Submarine communication, Communication within mines |
| Very low frequency | VLF | 4 | 3–30 kHz / 100 km – 10 km | Navigation, time signals, submarine communication, wireless heart rate monitors, geophysics |
| Low frequency | LF | 5 | 30–300 kHz / 10 km – 1 km | Navigation, time signals, AM longwave broadcasting (Europe and parts of Asia), RFID, amateur radio |
| Medium frequency | MF | 6 | 300–3000 kHz / 1 km – 100 m | AM (medium-wave) broadcasts, amateur radio, avalanche beacons |
| High frequency | HF | 7 | 3–30 MHz / 100 m – 10 m | Shortwave broadcasts, citizens' band radio, amateur radio and over-the-horizon aviation communications, RFID, Over-the-horizon radar, Automatic link establishment (ALE) / Near Vertical Incidence Skywave (NVIS) radio communications, Marine and mobile radio telephony |
| Very high frequency | VHF | 8 | 30–300 MHz / 10 m – 1 m | FM, television broadcasts and line-of-sight ground-to-aircraft and aircraft-to-aircraft communications. Land Mobile and Maritime Mobile communications, amateur radio, weather radio |
| Ultra high frequency | UHF | 9 | 300–3000 MHz / 1 m – 100 mm | Television broadcasts, microwave ovens, microwave devices/communications, radio astronomy, mobile phones, wireless LAN, Bluetooth, ZigBee, GPS and two-way radios such as Land Mobile, FRS and GMRS radios, amateur radio |
| Super high frequency | SHF | 10 | 3–30 GHz / 100 mm – 10 mm | Radio astronomy, microwave devices/communications, wireless LAN, most modern radars, communications satellites, satellite television broadcasting, DBS, amateur radio |
| Extremely high frequency | EHF | 11 | 30–300 GHz / 10 mm – 1 mm | Radio astronomy, high-frequency microwave radio relay, microwave remote sensing, amateur radio, directed-energy weapon, millimeter wave scanner |
| Terahertz or Tremendously high frequency | THz or THF | 12 | 300–3,000 GHz / 1 mm – 100 μm | Terahertz imaging – a potential replacement for X-rays in some medical applications, ultrafast molecular dynamics, condensed-matter physics, terahertz time-domain spectroscopy, terahertz computing/communications, sub-mm remote sensing, amateur radio |

![US Frequency Plan](img/posts/jekyll-posts/US_Frequency_Allocations_Radio_Spectrum.jpg, "xxx")

Common radio frequency bands and their use include the following:

* **AM radio:** 535 kilohertz to 1.7 megahertz
* **Short wave radio:** bands from 5.9 megahertz to 26.1 megahertz
* **Citizens band (CB) radio:** 26.96 megahertz to 27.41 megahertz
* **Television stations:** 54 to 88 megahertz for channels 2 through 6
* **FM radio:** 88 megahertz to 108 megahertz
* **Television stations:** 174 to 220 megahertz for channels 7 through 13
* **Garage door openers, alarm systems, etc.:** Around 40 megahertz
* **Standard cordless phones:** Bands from 40 to 50 megahertz
* **Baby monitors:** 49 megahertz
* **Radio controlled airplanes:** Around 72 megahertz, which is different from...
* **Radio controlled cars:** Around 75 megahertz
* **Wildlife tracking collars:** 215 to 220 megahertz
* **MIR space station:** 145 megahertz and 437 megahertz
* **Cell phones:** 824 to 849 megahertz
* **New 900-MHz cordless phones:** Obviously around 900 megahertz!
* **Air traffic control radar:** 960 to 1,215 megahertz
* **Global Positioning System:** 1,227 and 1,575 megahertz
* **Deep space radio communications:** 2290 megahertz to 2300 megahertz

The very specific frequency bands and their usage can be refined further.
Governance agencies like the [Federal Communications Commission (FCC)][10]
for commercial and consumers, and the [National Telecommunications and Information Administration (NTIA)][54]
for Federal agencies (among other Federial ageancies) maintain databases of how these frequencies are used.
The FCC's database can be found [here][56] and the NTIA's database is [here][55].


## Creation of Radio Waves
While there are multiple source of [naturally occurring radio waves][49],
conveniently, radio frequency waves are invariably created by changing an electrical current in a wire.
This creates an [electromagnetic field][13] (also EMF or EM field)
that varies in a defined fashion with the changing electrical current.
The physics of electromagnetism require that parts of this varying field to propagate as a wave,
which is called [electromagnetic radiation][15] (EM radiation or EMR),
are detected by placing a wire in the field, and detecting the electricity [induced][14] in the wire.
The wire is known as an [antenna][16], and is a [transducer][52] that converts electrical energy within the conductive antenna structure and interfaces with free space, delivering electromagnetic energy.
An antenna can be any shape or size,
and for a practical application can be a simple wire or a very sophisticated apparatus.

The antenna (or aerial) is an electrical device which converts electric power
into electromagnetic radiation (e.g. radio waves), and vice versa.
Antennas are usually used with a [radio transmitter][17] or [radio receiver][18],
and when combined, the device is called a [transceiver][21].
In transmission, a radio transmitter supplies an oscillating radio frequency electric current to the antenna's terminals, and the antenna radiates the energy from the current as electromagnetic waves (radio waves).
In reception, an antenna intercepts some of the power of an electromagnetic wave in order to produce a tiny voltage at its terminals, that is applied to a receiver to be amplified.

The Radio Frequency spectrum is a somewhat variable part of the Electromagnetic
Spectrum that tends to grow as technology find better ways make transmission at higher and higher
frequencies better. At the lower end, the Radio Frequency spectrum is limited by the size of antennas
required to transmit the waves

We aimed at 110 Mhz, as 115 Mhz+ is where planes and other air traffic services tend to broadcast; lots of other cool things seem to talk on these frequencies too. Very little seems to sit around 100 Mhz and below that the military seems to start appearing.


## Electromagnetic Field
An [electromagnetic field][13] (also EMF or EM field) is a [physical field][51] produced by electrically charged objects.
The EMF affects the behavior of charged objects in the vicinity of the field.
The field can be viewed as the combination of an electric field and a magnetic field and cut across one another at right angles.
The electric field the surrounds the charges,
and the magnetic field is created by moving charges (currents).
Though the fields exist around the charged object, they propagate away from the charged object perpendicular to the two fields.
At some point beyond the charged object, the fields detach themselves and propagate independently. In fact, they support and regenerate one another along the way.
This “independent” wave is electromagnetic radiation, and when it frequency is less than 300GHz its called a radio wave.
Radiation is energy (sometimes called [radiant energy][50]) that travels
and is the mechanisms by which energy can enter or leave a system.

The radiant energy is associated with only the parts of the electromagnetic field that radiate into infinite space.
This radiant energy decrease in intensity by an inverse-square law of power, so that the total radiation energy that crosses through an imaginary spherical surface is the same, no matter how far away from the antenna the spherical surface is drawn.
This energy has left the antenna system, propagates outward, decreasing in intensity (i.e. quantity of energy per surface unit) but the total quantity is constant.

As it turns out, an electromagnetic field’s characteristics differ depending on the distance from the antenna.
These different field characteristics are typically divided into two regions — the [near field and far field][53].
Part of the field, the "near-field" close to the transmitter, is part of the changing electromagnetic field, but does not count as electromagnetic radiation.
The far field is the propagating radiant energy described above and the field portion we are most interested in.
For more on electromagnetic near fields and far fields, see:

* [EEVblog #1273 - EMC Near Field vs Far Field Explained](https://www.youtube.com/watch?v=lYmfVMWbIHQ&feature=em-uploademail)
* [Antenna Field Regions](http://www.ic.gc.ca/eic/site/smt-gst.nsf/eng/sf10112.html)
* [What’s The Difference Between EM Near Field And Far Field?](http://electronicdesign.com/energy/what-s-difference-between-em-near-field-and-far-field)


## Guided Wave and a Free-Space Wave
A [waveguide](https://en.wikipedia.org/wiki/Waveguide) is a structure that guides waves

an antenna is a transition device, or transducer, between a guided wave and a free space wave or vice versa. The antenna is a device which interfaces a circuit and space.

The concept of propagation refers to the various ways by which an electromagnetic (EM) wave travels from the transmitting antenna to the receiving antenna. Propagation of EM wave may also be regarded as a means of transferring energy or information from one point (a transmitter) to another (a receiver).


## Electromagnetic Radiation

* [How does an Antenna work? | ICT #4](https://www.youtube.com/watch?v=ZaXm6wau-jc)
* [Understanding Electromagnetic Radiation! | ICT #5](https://www.youtube.com/watch?v=FWCN_uI5ygY)


## The Physics Behind Antennas

* [The Physics Behind Antennas](https://hackaday.com/2019/07/11/the-physics-behind-antennas/)
* [Practical Guide to Radio-Frequency Analysis and Design](https://www.allaboutcircuits.com/textbook/radio-frequency-analysis-design/)



---------------



# What is an Antenna?
An antenna acts as an interface between a guided wave and a free-space wave.

The wire antennas are made of thin, conducting,
straight or curved wire segments or hollow tubes and are very easy to construct. It is suspended above the ground and the radius of the
wire is very small compared to the operating wavelength of the radio waves used. The dipole and monopole are examples of straight
wire antennas. The loop antenna is an example of curved wire antenna. The loop antenna is a radiating coil of any convenient cross
section of one or more turns carrying radio frequency current.


## Typical Antenna Designs

* [monopole antenna][41]
* [discone antenna][42]
* [Simple Antennas to Survive the Zombie Apocalypse](https://www.youtube.com/watch?v=MMnpBOwu2I0)
* [WA2OOO Provides a Complete Guide to Build Radio Antennas](https://www.bigtimedaily.com/wa2ooo-provides-a-complete-guide-to-build-radio-antennas/)

Most of the antenna designs described are all suitable for work requiring a relatively
narrow band of frequencies with an omni-directional pattern of radiation.
Also in the mechanical viewpoint, these designs are simple and easy to construct which
makes them very popular among radio operators.
However all of them have a limited bandwidth of 140-150 MHz.
If one attempts to operate  these antennas
outside these frequency limits with a wideband transceiver, the
signal response becomes weaker as the operating frequency of the transceiver
is moved farther away from the optimal operational band of the antenna.
At the same time the SWR in the transmission line increases and can reach an
intolerable point which may cause damage to the transceiver.
Although this limitation can be overcome by using a different antenna tuned to a different frequency band,
the process of changing antennas every time you
change your operating band becomes cumbersome or completely impractical.

This problem can be solved by using a broadband antenna, meaning an antenna that operates efficiently over a
wide range of frequencies.
There are several such broadband antenna designs, but we'll focus on one of these, the discone antenna.
Theoretically, a properly designed discone antenna can operate up to a frequency 10 times the value of its lowest operational frequency.
Specifically speaking, if a discone antenna is designed to operate with a lowest operational frequency of 140 MHz,
then it can be conveniently used up to 1.4 Gigahertz!
The lowest operational frequency is called cut-off frequency.
Below this frequency the SWR will increase rapidly.


### Driving the Antenna
When transmitting (or receiving) a radio signal via an antenna, you often have to consider
the wave nature of the radio signal because multiple wave cycles will be present within the body
of the current caring wire, called a [transmission line][22].
When not considered, the energy tends to radiate off the cable as radio waves, causing power losses.
In radio engineering, a transmission line is a specialized cable or other structure
designed to carry alternating current of radio frequency, that is, currents with a frequency high enough that their wave nature must be taken into account.
Transmission lines must be used when the frequency is high enough that the wavelength of the waves begins to approach the length of the cable used.


### Fundamental Antenna Parameters
Antennas are characterized by a number of performance measures which a user would be concerned with in selecting or designing an antenna for a particular application.
To establish the key figures of merit for an antenna, you first must establish a reference point from which all antennas can be compared.
That reference point is the [isotopic antenna][23].
An isotropic radiator is a theoretical point source of electromagnetic waves which
radiates the same intensity of radiation in all directions.
It has no preferred direction of radiation.
It radiates uniformly in all directions over a sphere centered on the source.
Radio wave isotropic radiators cannot really exist, but are used conceptually as reference radiators with which other sources are compared.

You can thing of an antenna as a transformer of the energy carried by a transmission line and to energy delivered into free space.
To describe an antenna, we must characterize its properties as a transmission line load (input impedance)
and the distribution of the electromagnetic energy that it radiates into space (radiation pattern).
There are a number of key parameters and concepts that we can use to describe the antenna's "transforming" properties.
A discription for some of these parameters is given below:

* [Radiation Pattern][43] - Some times called the antenna pattern or far-field pattern, this is a plot of the gain as a function of direction and will varies with wavelength. In most case, the radiation pattern is a far-field quantity but can be near-field. Very often, only the relative amplitude is plotted, normalized to the total radiated power. The plotted quantity may be shown on a linear scale, or in dB.
* [Radiation Intensity][46] - Some times called the radiation power density, is describes the power density that an antenna creates in a particular solid angle. A solid angle is a section of the surface of the imaginary sphere around the antenna. Its measurement units are watts per square meter.
* [Antenna Directivity][24] - This is a measures the power density the antenna radiates in the direction of its strongest emission, versus the power density radiated by an ideal isotropic radiator radiation pattern - directional characteristics.
* [Antenna Efficiency][25] - Also called "radiation efficiency", this is a measure of the efficiency with which a radio antenna converts the radio-frequency power accepted at its terminals into radiated power.
* [Antenna Gain][26] - Often called "power gain" or simply "gain", combines the antenna's directivity and electrical efficiency.  This figure describes how well the antenna converts input power into radio waves headed in a specified direction.
* [Polarization][47] - The polarization of an antenna is the orientation of the electric field (E-plane) of the radio wave with respect to the Earth's surface.
* [Antenna Bandwidth][48] - Antenna bandwidth is the range of frequencies within which the performance of the antenna, with respect to some characteristic, conforms to a specified standard. The bandwidth can be viewed as the frequencies left and right of the center frequency (usually the resonant frequency) in which the antenna performance meets the specified values.

An in depth and rigorous description of the key antenna parameters can be found in these documents:

* [ntroduction to Antenna Basics](https://hackaday.io/course/178490-introduction-to-antenna-basics)
* [Antenna Basics](http://highered.mcgraw-hill.com/sites/dl/free/0072321032/62577/ch02_011_056.pdf)
* [Fundamental Properties of Antennas](http://my.ece.ucsb.edu/York/Bobsclass/201C/Handouts/Chap3.pdf)
* [Antenna Patterns and Their Meaning](http://www.cisco.com/en/US/prod/collateral/wireless/ps7183/ps469/prod_white_paper0900aecd806a1a3e.pdf)
* [Basic Antenna Theory and Application](https://www.wpi.edu/Pubs/E-project/Available/E-project-042811-161838/unrestricted/ChuckFungFinalMQPpaper2.pdf)
* [Fundamental Antenna Parameters & Concepts](http://www.ece.uvic.ca/~jbornema/ELEC453/453-02-Fundamentals-1.pdf)
* [EMC Antenna Parameters and Their Relationships](http://www.ets-lindgren.com/pdf/antparameters.pdf)
* [General Notes About Input Format](https://wiki.edubuntu.org/SteveConklin/Test)
* [NEC-2 Manual, Part III: User’s Guide](http://www.nec2.org/other/nec2prt3.pdf)

It is also important to note that the receiving characteristics of an antenna are equivalent to the transmitting characteristics.
This electromagnetic fact, call [reciprocity][27], means we can state the antenna's properties
independently of its uses as a transmitter or receiver.


### Antenna Tuning

* [Antenna Tuning For GHz Frequencies](https://hackaday.com/2019/08/03/antenna-tuning-for-ghz-frequencies/)
* [Antenna Tuning for Beginners](https://www.baseapp.com/iot/antenna-tuning-for-beginners/)
* [Michael Ossmann: Simple RF Circuit Design](https://hackaday.com/2016/03/23/michael-ossmann-makes-you-an-rf-design-hero/)
* [Chris Gammell - Gaining RF Knowledge: An Analog Engineer Dives into RF Circuits](https://www.youtube.com/watch?v=AS8Ybhm0qk8)


### Comparing Antenna Perfromance

* [Comparing shortwave antennas with Python](http://www.hydrogen18.com/blog/comparing-shortwave-antennas-with-python.html)


### Phased Array Antenna
A phased array antenna is an array antenna whose single radiators can be fed with different phase shifts. As a result, the common antenna pattern can be steered electronically. The electronic steering is much more flexible and requires less maintenance than the mechanical steering of the antenna.

* [VISUALIZATION OF A PHASED ARRAY ANTENNA SYSTEM](https://hackaday.com/2017/01/05/visualization-of-a-phased-array-antenna-system/)
* [Hackaday Supercon - HunterScott : Why Phased Arrays are Cool and How to Build One](https://www.youtube.com/watch?v=ytBmoL2wZLw)



---------------



# Antenna Modeling

* [Antenna Modeling](http://www.arrl.org/antenna-modeling)
* [Antenna Modeling, Courtesy of Ubuntu and Wine](https://eksfiles.net/2008/01/antenna-modeling-courtesy-of-ubuntu-wine/)
* [Antennas in Linux](https://www.linuxjournal.com/content/antennas-linux)


# Electromagntic Numerical Analysis
Because of its popularity and [respect amoung the Ham Radio community][33] and others,
I have focused on the [Numerical Electromagnetic Code (NEC)][31] family of tools.
It is based on a numerical solution of electromagnetic ﬁeld integrals for thin,
perfectly conducting wire segments using the [Method of Moments (MoM)][32].

There are at least four generations of NEC, with NEC2 being the highest version of the code within the public domain.
A translation of NEC2 into C, is called NEC2C, and when given a GTK+ based GUI, called Xnec2c.
There is also nec2++, which is a port of NEC2 to C++, with a C/C++ interface and python bindings.
There also exist many variations of these versions of NEC and multiple specialized implementations and supporting tools.
A good starting point to navigate this confusion is the [Numerical Electromagnetic Code NEC2 unofficial home page][34]
and [The unofficial Numerical Electromagnetic Code (NEC) Archives][35].

I'll be using Xnec2c since it is is a [GTK+][37] graphical interactive version of nec2c and well suited for my Linux system.
It incorporates the nec2c core, which it uses for reading input files and calculating output data,
but it produce an output in graphical format by default.
The latest version of Xnec2c appears to be 2.3 and can be obtained from [here][36]
(Note: The Ubuntu / Debian packages appear to be version 1.4).
This package also includes many example input files and you can get more at [Steve Conklin's GitHub site][38].


## MMANA (Mini-NEC)

* [Antenna Modelling for Complete Beginners - Model your own Dipole, Vertical or Loop - MMANA NEC](https://www.youtube.com/watch?v=15qdzgYe24E)
* [Antenna Software Modelling](https://www.youtube.com/watch?v=jMhHIGB2iTI&list=PLAjpQM3cGOdO83PLddRqsmwQzEGGAAwHd)
* [MM HAMSoft](https://hamsoft.ca/pages/mmana-gal.php)
* [MMANA-GAL Antenna Modeling Program](https://www.smeter.net/antennas/mmana.php)


## NEC2, 4NEC2, NEC2++, XNEC2C, ... Electromagnetic Simulation Software
The Numerical Electromagnetics Code (NEC-2) is a comprehensive package for the analysis of the electromagnetic properties of structures. It can analyse radiating properties i.e. antenna gain, as well as scattering properties (radar cross section) of structures. NEC-2 was originally written in FORTRAN.

4NEC2 (Numerical Electric Code) is a simulation method for wire antennas, developed by the Lawrence Livermore Laboratory in
1981 for the Navy. To realize this, an antenna is divided into ―short segments‖ with linear variation of current and voltage. The results
are very convenient and the standard for this simulation technique is NEC2. The demerit of NEC2 is that the simulation errors occur
when wires are crossing in a very short distance or when using buried wires were overcome with 4NEC2. 4NEC2 offers a huge
amount of possibilities and options and it was programmed by Arie Voors. Its main advantages are the optimizing tools and the
parameter sweeps. It can be found and downloaded free of charge from the Internet. It is open source software. In 4NEC2, the
frequency, wavelength, length, radius can be changed and the radiation pattern, smith chart is generated accordingly. Also the
efficiency is calculated for the obtained radiation pattern.

NEC2++ is an extensive rewrite of NEC-2 in C++ by Tim Molteno. This work was helped tremendously by the work of N. Kyriazis who ported NEC-2 to C. The new portions of code are licensed under the GNU Public License (GPL).

* [NEC2](http://www.nec2.org/)
* [Nec2++](http://elec.otago.ac.nz/w/index.php/Necpp)
* [NEC2++ Electromagnetic Simulation Software](https://tmolteno.github.io/necpp/)
* [XNEC2C](https://www.qsl.net/5b4az/pkg/nec2/xnec2c/doc/xnec2c.html)
* [Modeling antennas in Python with NEC2++](http://astroelec.blogspot.com/2015/05/modeling-antennas-in-python-with-nec2.html)


## necpp
This module allows you to do antenna simulations in Python using the nec2++ antenna simulation package.

* [python-necpp: Antenna simulation in python](https://pypi.org/project/necpp/)


## Using NEC, 4NEC2, etc

* [How to produce a NEC antenna file (and what software to use it with)?](https://ham.stackexchange.com/questions/5405/how-to-produce-a-nec-antenna-file-and-what-software-to-use-it-with)
* [Antenna simulations with 4NEC2 including an application example for 2300MHz](http://www.vhfcomm.co.uk/4nec2%20antenna%20simulation%20english.pdf)
* [A Beginner’s Guide to Modeling with NEC: Part 1 - : Getting settled and getting started](http://wireless.ictp.it/school_2005/download/nec2/nec_part1.pdf)
* [A Beginner’s Guide to Modeling with NEC: Part 2 - The Ins and Outs of Modeling](http://wireless.ictp.it/school_2005/download/nec2/nec_part2.pdf)
* [A Beginner’s Guide to Modeling with NEC: Part 3 - Sources, grounds and sweeps](http://wireless.ictp.it/school_2005/download/nec2/nec_part3.pdf)
* [A Beginner’s Guide to Modeling with NEC: Part 4 - Loads, transmission lines, tests and limitations](http://wireless.ictp.it/school_2005/download/nec2/nec_part4.pdf)
* [Design of helical antenna using 4NEC2](http://pnrsolution.org/Datacenter/Vol3/Issue2/191.pdf)
* [Patch Antenna Design with NEC2](https://www.aeronetworks.ca/2018/07/patch-antenna-design-with-nec2.html)
* [Olde Skool Antenna Design with NEC2 on OpenBSD](https://www.aeronetworks.ca/2017/07/olde-skool-antenna-design-with-nec2-on.html)
* [Xnec2c dipole model quickstart](http://ag6cb.blogspot.com/2013/09/model-dipole-going-from-sketch-to-xyz.html)


## gprMax
gprMax is open source software that simulates electromagnetic wave propagation. It solves Maxwell’s equations in 3D using the Finite-Difference Time-Domain (FDTD) method. gprMax was designed for modelling Ground Penetrating Radar (GPR) but can also be used to model electromagnetic wave propagation for many other applications.

* [What is gprMax](http://docs.gprmax.com/en/latest/include_readme.html)
* [grpMax](http://www.gprmax.com/index.shtml)
* [GPR modelling using gprMax (online workshop, July 2020)](https://www.youtube.com/playlist?list=PLf_lDHRs1yH6h5T-s-RvPbkdXFMqLrhy4)


## Phased Array Design

* [No Moving Parts: Phased Array Antennas Move While Standing Still](https://hackaday.com/2019/01/11/no-moving-parts-phased-array-antennas-move-while-standing-still/)
* [MATLAB Based Toolbox for Phased Array Antenna Design and Analysis](https://zinka.wordpress.com/2008/10/03/ada/)


## Write Your Own Electromagntic Numerical Analysis
[Antenna Design, Analysis and Simulation](https://www.microwavejournal.com/articles/29437-antenna-design-analysis-and-simulation)

[Meep](https://meep.readthedocs.io/en/latest/) is a free and open-source software package for electromagnetics simulation via the finite-difference time-domain (FDTD) method spanning a broad range of applications.

* [Meep GitHub](https://github.com/NanoComp/meep)
* Documentation - [Meep: A flexible free-software package for electromagnetic simulations by the FDTD method](https://data.mendeley.com/datasets/42hb3hb2tt/1)
* [Simulations of electromagnetic waves with python-meep](https://www.fzu.cz/~dominecf/meep/)


## Long Range Antenna

* [#291 External antennas and ESP32 Long-Range mode](https://www.youtube.com/watch?v=2rujjTOPIRU)
* [#292 Wi-Fi Antennas with Gain and ESP32 Long-Range Mode (part2)](https://www.youtube.com/watch?v=PUppoaePi3A&t=647s)


---------------




# Discone Antenna Design
A discone antenna is a version of a [biconical antenna][19] is typically a wired structure,
its usually mounted vertically, with the disc at the top and the cone beneath.
The open litature discribes it as omnidirectional,
vertically polarized and with gain similar to a [dipole antenna][20], it is exceptionally wideband,
offering a frequency range ratio of up to approximately 10:1.
The radiation pattern in the horizontal plane is quite narrow, making its sensitivity highest in the direction of the horizon and rather less for signals coming from relatively close by.
A vertical whip may be affixed to the center of the disc in order to extend the low frequency response,
but this may compromise efficiency at higher frequencies.
In this configuration, at lower frequencies the discone may more closely resemble a ground plane antenna or a coaxial dipole.

As stated earlier, my aim is pickup frequencies around 115 Mhz+ is where planes and other air traffic services tend to broadcast.
We can expect the antenna size to increase if we attempt to reach lower frequencies.
Also, we are limited on the upper frequencies because of the 10:1 bandwidth typical for discone antennas.
With this lower bound, a discone could reasonably up to 1.15GHz.
Now this antenna bandwidth doesn't fully cover what the RTL-SDR can reasonable cover, which is [24MHz to 1850MHz][44].
We'll need to prioritize what frequencies we wish to go after or create multiple antennas,
but for now, we'll stick with one antenna.
We'll use this 115MHz to 1.15GHz starting point for the analysis
and perturb our parameters based on a more complete analysis.


## Discone Antenna Initial Design
I'll use the [Discone Antenna Calculator][45] to establish our baseline design.
Using this tool, I get the following results:

![Discone Dimensions](img/posts/jekyll-posts/discone-dimensions.jpg, "xxx")
![Discone Measurements](img/posts/jekyll-posts/discone-measurments.png, "xxx")


## Discone Antenna Electromagntic Numerical Analysis
We would like to solve [Maxwell's equations][28] for the discone antenna design to discover its radiation pattern, etc.
Solving these equations as a [closed-form expression][29] is hopeless except for the simplest types of antenna structures.
So we'll need to leverage [numerical methods][30] to perform the analysis of the discone antenna.
An online search for suitable tools produces multiple possibilities.
Because of its popularity and [respect amoung the Ham Radio community][33] and others,
I have focused on the [Numerical Electromagnetic Code (NEC)][31] family of tools.
It is based on a numerical solution of electromagnetic ﬁeld integrals for thin,
perfectly conducting wire segments using the [Method of Moments (MoM)][32].
It was developed at Lawrence Livermore Laboratories, and remains widely used,
despite the old fashioned punched card style input required.
Like all tools, it has it limitations.
One major limitation (but not for this analysis) is that it can model antenna's
structured out of wire but not solid structures.
Also, the tool may have difficulties in converging or accurately modeling antennas with complex shapes
(not clear if we should be concerned).

There are at least four generations of NEC, with NEC2 being the highest version of the code within the public domain.
A translation of NEC2 into C, is called NEC2C, and when given a GTK+ based GUI, called Xnec2c.
There is also nec2++, which is a port of NEC2 to C++, with a C/C++ interface and python bindings.
There also exist many variations of these versions of NEC and multiple specialized implementations and supporting tools.
A good starting point to navigate this confusion is the [Numerical Electromagnetic Code NEC2 unofficial home page][34]
and [The unofficial Numerical Electromagnetic Code (NEC) Archives][35].

I'll be using Xnec2c since it is is a [GTK+][37] graphical interactive version of nec2c and well suited for my Linux system.
It incorporates the nec2c core, which it uses for reading input files and calculating output data,
but it produce an output in graphical format by default.
The latest version of Xnec2c appears to be 2.3 and can be obtained from [here][36]
(Note: The Ubuntu / Debian packages appear to be version 1.4).
This package also includes many example input files and you can get more at [Steve Conklin's GitHub site][38].
From [here][36] I downloaded `xnec2c-2.3-beta.tar.bz2` into `~/src/xnec2c/` and proceed to do an install
as follows (You'll find very detail installation instructions in the file `INSTALL`):

```
cd ~/src/xnec2c
sudo apt-get install libgtk2.0-dev libghc-gtk-dev
tar xvjf xnec2c-2.3-beta.tar.bz2
cd xnec2c-2.3-beta
./configure
make
sudo make install
make clean
git clone https://github.com/sconklin/Antenna-Modeling.git
cp Antenna-Modeling/dumpnec/dumpnec ~/bin
```

>**Note:** During the initial run of the `./configure` step, I discovered that my system didn't have GTK+ installed.
So the first step above is for installing the required libraries.
When completed, the executable is located at `/usr/local/bin/xnec2c`
The 2nd to last line is to get additional example input files from Steve Conklin's GitHub site.
The last line copies the `dumpnec` utility to my bin.
`dumpnec` is a pretty printer for NEC input files (very handy!).

To test xnec2c out, try one of the provided example input file
(e.g. Yagi Antenna `xnec2c -i examples/13cm_Yagi.nec`][64].
To learn more about how to use xnec2c and create input files,
you'll need to tap into the documentation available for the multiple generations/versions of NEC software.
With a little bit of insight, you'll be able to leverage these "not quite xnec2c documentation" sources.
Check out these sources:

* [The Method of Moments: A Numerical Technique for Wire Antenna Design](http://www.highfrequencyelectronics.com/Archives/Feb06/HFE0206_Rawle.pdf)
* [Antenna Modelling for Radio Amateurs Made Easier](http://www.rafars.org/QRV_Articles/01/Antenna.html)
* Antenna modeling using nec2c on Ubuntu Linux: Video [part 1](http://www.popscreen.com/v/6b31Y/Antenna-modeling-using-xnec2c-part1) and [part 2](http://www.youtube.com/watch?v=KgYfU7wghso).
* A Beginner’s Guide to Modeling with NEC: [part 1](http://wireless.ictp.it/school_2005/download/nec2/nec_part1.pdf), [part 2](http://wireless.ictp.it/school_2005/download/nec2/nec_part2.pdf), [part 3](http://wireless.ictp.it/school_2005/download/nec2/nec_part3.pdf), and [part 4](http://wireless.ictp.it/school_2005/download/nec2/nec_part4.pdf).
* [MININEC: The Other Edge of The Sword](http://www.arrl.org/files/file/Technology/tis/info/pdf/9102018.pdf)
* [Wire Antenna Modelling with NEC-2](http://www.qsl.net/4nec2/Tutorial.pdf)
* [Xnec2c User Manual](http://www.qsl.net/5b4az/pkg/nec2/xnec2c/doc/xnec2c.html)
* [Simulation of Wire Antennas using 4NEC2](http://www.qsl.net/4nec2/Tutorial_4NEC2_english.pdf)
* [4NEC2 Tutorial: Electric Dipole Antenna Simulation](http://www.qsl.net/4nec2/NEC_tutorial1.pdf)


## Antenna Modeling of a Discone Antenna


## Cabling For Antenna
Connectors on Devices:

* SDR device - Female [micro coaxial (MCX)][57] connector (intended for a mono-pole antenna using a flexible small diameter [50 Ohm RG-174 cable][61]) and male [Universal Serial Bus (USB) A-Type][58]
* Raspberry Pi - female [Universal Serial Bus (USB) A-Type][58] and female [RJ45][60] Ethernet connector (also called [8P8C modular connector][59])

Cabling Require:

* Cable attached Discone - [50 Ohm RG-174 cable][61] attached to the antenna at xxx and terminated at the other end of the cable with a female [SubMiniature version A (SMA)][62] connector
* Cable from Discone-cable to SDR device - A long [50 Ohm RG-174 cable][61] with [SMA][62] male connector on one end and a female on the other end.  This cable is connected with a 6 inch coax cable assembly with a female to [MCX male][57].  The male MCX plugs into the SDR device.


## Why is Coax 50 Ohm?
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
According to [Microwaves 101][65], choice of 50 ohms is a compromise between power handling capability
and signal loss per unit length, for air dielectric.
For cheaper commercial cables, such as those that bring CATV to your home,
an impedance 75 ohms probably was a compromise between low loss and cable flexibility.

* [Why is Coax 50 Ohms?](https://www.youtube.com/watch?app=desktop&v=I-OnQZJv35I)



---------------


# Broadband Antenna
Vivaldi antennas are simple planar antennas that are very broadband.

* [Making an Ultra-wideband Antenna – Part 1 (UWB Antenna Options)](https://hexandflex.com/2017/12/03/making-an-ultrawideband-antenna-pt1/)
* [Making an Ultra-Wideband Antenna – Part 2 (Introducing the Palm Tree Vivaldi Antenna)](https://hexandflex.com/2017/12/06/making-an-ultra-wideband-antenna-part-2/)
* [Making an Ultra-Wideband Antenna – Part 3 (performance)](https://hexandflex.com/2017/12/11/making-an-ultra-wideband-antenna-part-3-performance/)
* [Vivaldi antennas](https://www.antenna-theory.com/antennas/aperture/vivaldi.php)


---------------


# What Makes a Good Antenna?
It sometimes seems as though antennas and RF design are portrayed as something of a Black Art, the exclusive preserve of an initiated group of RF mystics and beyond the reach of mere mortals.

NanoVNA as a useful tool in the antenna builder’s arsenal, one which gives a revolutionary window on performance compared to the trial-and-error of previous times.


# Antenna Tuner
A antenna tuner is a device used to match impedances between a transmitter and an antenna.

* [Manual Antenna Tuner Shows How Homebrewing Is Done](https://hackaday.com/2021/01/15/manual-antenna-tuner-shows-how-homebrewing-is-done/)
    * [End Fed Half Wave Antenna Tuner: Part 1 - Initial Build](https://www.youtube.com/watch?v=XKzWSsTBjCo&feature=emb_logo)
    * [End Fed Half Wave Antenna Tuner: Part 2 - Final Configuration](End Fed Half Wave Antenna Tuner: Part 2 - Final Configuration)
    * [End Fed Half Wave Antenna Tuner: Part 3 - Field Demonstration](https://www.youtube.com/watch?v=t9HAvY6n2gw)


## Tin Can DIY WiFi Antenna (Cantenna)

* [How To Build A Tin Can DIY WiFi Antenna](https://www.shtfpreparedness.com/build-tin-can-wifi-antenna/)


## Patch Antenna

* [A Patch Antenna Is Just A Rectangle, It Should Be Easy To Design, Right?](https://hackaday.com/2020/03/01/a-patch-antenna-is-just-a-rectangle-it-should-be-easy-to-design-right/)


## Active GNSS Antenna

* [Active GNSS Antenna: Quadrifilar Helix Antenna for GPS/GNSS](https://hackaday.io/project/176769-active-gnss-antenna)


## 1/4 Wave Antenna

* [What is a 1/4 Wave Stub and Why Does it Work](https://www.youtube.com/watch?v=l9YN6bPkdq8)
* [What's so special about a quarter-wavelength?](https://www.microwaves101.com/encyclopedias/quarter-wave-tricks)


## Loop Antenna

* [Alpha Antenna portable vhf/uhf/hf loop antenna](https://www.youtube.com/shorts/1zWDNKaLCRc)
    * [Alpha Antenna: VHF UHF HF EmComm MagLoop](https://www.alphaantenna.com/product/vhf-uhf-hf-emcomm-magloop-magnetic-loop-100-watts-alpha-antenna/)

* [Homebrew Loop Antenna Brings The Shortwave World To You](https://hackaday.com/2020/04/12/homebrew-loop-antenna-brings-the-shortwave-world-to-you/)
* [THE YOULOOP PASSIVE LOOP ANTENNA REVIEWED ON HF RECEPTION](https://www.rtl-sdr.com/the-youloop-passive-loop-antenna-reviewed-on-hf-reception/)
* [Antenna Pulls In AM Stations](https://hackaday.com/2020/08/19/antenna-pulls-in-am-stations/)
* [Affordable HF Loop Antenna Reviewed](https://hackaday.com/2022/01/21/affordable-hf-loop-antenna-reviewed/)
* [LOOP ANTENNA IS PORTABLE](https://hackaday.com/2017/02/25/loop-antenna-is-portable/)


## Yagi Antenna

* [DIY Yagi Antenna Sends LoRa Signals Farther](https://hackaday.com/2025/02/20/diy-yagi-antenna-sends-lora-signals-farther/)
* [On Point: The Yagi Antenna](https://hackaday.com/2017/05/24/on-point-the-yagi-antenna/)
* [Lowering The Boom On Yagi Element Isolation](https://hackaday.com/2020/05/10/lowering-the-boom-on-yagi-element-isolation/)
* [On Point: The Yagi Antenna](https://hackaday.com/2017/05/24/on-point-the-yagi-antenna/)
* [VHF/UHF Yagi Antenna Quick Designer](https://k7mem.com/Ant_Yagi_VHF_Quick.html)
* [#1456 PCB Yagi antenna for 2.4GHz](https://www.youtube.com/watch?v=JusiGUt5Ovg)
* [#1459 PCB Yagi antenna for 2.45GHz (part 1 of 2)](https://www.youtube.com/watch?v=I-5qf60oCKQ)
* [Pocketable Yagi Antenna Really Shoots For Distance](https://hackaday.com/2023/11/02/pocketable-yagi-antenna-really-shoots-for-distance/)


## Helical Antenna
A helical antenna is an antenna in which a conductor connected to ground plane, is wound into a helical shape. The
helix is the simplest antenna which generates circular polarized waves.

* [Handheld Satellite Dish Is 3D Printed](https://hackaday.com/2024/12/23/handheld-satellite-dish-is-3d-printed/)
* [No Dish? Try A Portable Weave Helix Antenna](https://hackaday.com/2024/01/28/no-dish-try-a-portable-weave-helix-antenna/)
* [Building a 2.4 GHz WiFi helical antenna](https://www.youtube.com/watch?v=xp6B3nVEFCI)
    * [Helical antenna calculator](https://sgcderek.github.io/tools/helix-calc.html)
    * [helix-antenna-scaffold](https://github.com/sgcderek/helix-antenna-scaffold)
    * [Field Testing a Home Made WiFi antenna](https://hackaday.com/2023/06/28/field-testing-a-home-made-wifi-antenna/)


## Extending WiFi Range

* [Uni-Directional WIFI Range Extender](https://hackaday.com/2019/08/01/boost-your-wifi-range-with-cookware/)
* [ESP32 WiFi Hits 10KM with a Little Help](https://hackaday.com/2017/04/11/esp32-wifi-hits-10km-with-a-little-help/#more-252084)
* [How to Make an Incredible DIY Directional Antenna for Almost Nothing](https://www.youtube.com/watch?v=1nHPbWPUYzk)
* [Real WiFi Trap DIY / Free Internet Rifle V 2.0](https://www.youtube.com/watch?v=GWq6L94ImX8)

[TP-Link AC1750 WiFi Range Extender](https://www.amazon.com/gp/product/B010S6SG3S/) (aka TP-Link RE450) [from Amazon][02]
I used this device to extend the range of of my home WiFi into places
where I currently get poor reception.
Like my router, its dual band (2.4GHz 450Mbps / 5GHz 1300Mbps)
and claims to be compatible with any type of Router/Gateway/Access Point.
The video shows three methods for setting up the range extender:
smart phone app, web browser, or router WPS button:
[How to set up a TP-Link Range Extender](https://www.youtube.com/watch?v=W9QxHvIyULQ)


## Antenna Balun
Balun definition:
A balun balanced to unbalanced is an electrical device that converts between a balanced signal and an unbalanced signal, or feed line. A balun can take many forms and may include devices that also transform impedances but need not do so.

* [A Cheap Dipole Antenna From An Extension Cord](https://hackaday.com/2021/07/16/a-cheap-dipole-antenna-from-an-extension-cord/)
* [Balanced-Unbalanced Antenna Structures and Baluns](https://incompliancemag.com/article/balanced-unbalanced-antenna-structures-and-baluns/)
* [Balanced line](https://en.wikipedia.org/wiki/Balanced_line)
* [Unbalanced line](https://en.wikipedia.org/wiki/Unbalanced_line)
* <https://www.antenna-theory.com/definitions/balun.php>


## NFC Antenna

* [NFC Performance: It’s All In The Antenna](https://hackaday.com/2021/11/10/nfc-performance-its`-all-in-the-antenna/)


## Frame Antenna

* [Frame Antenna Works the Low Bands](https://hackaday.com/2021/12/22/frame-antenna-works-the-low-bands/)


## Antenna Lightning Arrestor

* [RF Explorer RFEA-1 External Lightning Arrestor](https://www.seeedstudio.com/External-lightning-Arrestor-0-3GHz-20kA-N-Type-Male-Female-D24-6-L65-2mm-p-5303.html)
* [Coaxial N Type Lightning Arrestor 0 to 6 GHz](https://www.amazon.com/Lightning-Arrestor-N-Female-Protects-Antennas/dp/B07JY6TD2T)




[01]:http://en.wikipedia.org/wiki/Radio_frequency
[02]:http://en.wikipedia.org/wiki/Radio_spectrum
[03]:http://en.wikipedia.org/wiki/Electromagnetic_spectrum
[04]:http://en.wikipedia.org/wiki/Radio_waves
[05]:http://en.wikipedia.org/wiki/Radio
[07]:http://en.wikipedia.org/wiki/Bandplan
[08]:http://en.wikipedia.org/wiki/Electromagnetic_interference
[09]:http://en.wikipedia.org/wiki/International_Telecommunications_Union
[10]:http://en.wikipedia.org/wiki/Federal_Communications_Commission
[11]:http://www.jneuhaus.com/fccindex/spectrum.html
[12]:http://en.wikipedia.org/wiki/Spectrum_management
[13]:http://en.wikipedia.org/wiki/Electromagnetic_field
[14]:http://en.wikipedia.org/wiki/Electromagnetic_induction
[15]:http://en.wikipedia.org/wiki/Electromagnetic_radiation
[16]:http://en.wikipedia.org/wiki/Antenna_(radio)
[17]:http://en.wikipedia.org/wiki/Transmitter
[18]:http://en.wikipedia.org/wiki/Receiver_(radio)
[19]:http://en.wikipedia.org/wiki/Biconical_antenna
[20]:http://en.wikipedia.org/wiki/Dipole_antenna
[21]:http://en.wikipedia.org/wiki/Transceiver
[22]:http://en.wikipedia.org/wiki/Transmission_line
[23]:http://en.wikipedia.org/wiki/Isotropic_radiator
[24]:http://en.wikipedia.org/wiki/Directivity
[25]:http://en.wikipedia.org/wiki/Antenna_efficiency
[26]:http://en.wikipedia.org/wiki/Antenna_gain
[27]:http://en.wikipedia.org/wiki/Antenna_(radio)#Reciprocity
[28]:http://en.wikipedia.org/wiki/Maxwell's_equations
[29]:http://en.wikipedia.org/wiki/Closed-form_expression
[30]:http://en.wikipedia.org/wiki/Numerical_methods
[31]:http://en.wikipedia.org/wiki/Numerical_Electromagnetics_Code
[32]:http://www.highfrequencyelectronics.com/Archives/Feb06/HFE0206_Rawle.pdf
[33]:http://www.eham.net/reviews/detail/5192
[34]:http://www.nec2.org/
[35]:http://www.si-list.net/swindex.html
[36]:http://5b4az.chronos.org.uk/pages/nec2.html
[37]:http://www.gtk.org/
[38]:https://github.com/sconklin/Antenna-Modeling
[39]:http://en.wikipedia.org/wiki/Electronvolt
[40]:http://www.nooelec.com/store/software-defined-radio/sdr-receivers/tv28tv2.html#.Um25n670rv4
[41]:http://en.wikipedia.org/wiki/Monopole_antenna
[42]:http://en.wikipedia.org/wiki/Discone_antenna
[43]:http://en.wikipedia.org/wiki/Radiation_pattern
[44]:http://rtlsdr.org/start
[45]:http://www.changpuak.ch/electronics/calc_11.php
[46]:http://en.wikipedia.org/wiki/Radiation_intensity
[47]:http://en.wikipedia.org/wiki/Polarization_(antenna)#Polarization
[48]:http://en.wikipedia.org/wiki/Antenna_(radio)#Bandwidth
[49]:http://www.earthlyissues.com/radio.htm
[50]:http://en.wikipedia.org/wiki/Radiant_energy
[51]:http://en.wikipedia.org/wiki/Field_(physics)
[52]:http://en.wikipedia.org/wiki/Transducer
[53]:http://en.wikipedia.org/wiki/Near_and_far_field
[54]:http://www.ntia.doc.gov/
[55]:http://www.ntia.doc.gov/files/ntia/Spectrum_Use_Summary_Master-06212010.pdf
[56]:http://reboot.fcc.gov/reform/systems/spectrum-dashboard
[57]:http://en.wikipedia.org/wiki/MCX_connector
[58]:http://en.wikipedia.org/wiki/Usb#Standard_connectors
[59]:http://en.wikipedia.org/wiki/8P8C#8P8C
[60]:http://en.wikipedia.org/wiki/RJ45_(telecommunications)#RJ45
[61]:http://media.digikey.com/pdf/Data%20Sheets/General%20Cable%20PDFs/RG_174U_Type.pdf
[62]:http://en.wikipedia.org/wiki/SMA_connector
[63]:http://www.rohde-schwarz-usa.com/rs/rohdeschwarz/images/8GE01_Antenna_Basics.pdf
[64]:https://hackaday.com/2017/05/24/on-point-the-yagi-antenna/
[65]:http://www.microwaves101.com/encyclopedias/why-fifty-ohms
[66]:
[67]:
[68]:
[69]:
[70]:
