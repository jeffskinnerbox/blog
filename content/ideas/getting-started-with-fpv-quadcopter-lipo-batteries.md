<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>



-----


Review this again -  [LIPO BATTERY USER GUIDE](https://hobbytechtoys.com.au/pages/lipo-battery-user-guide)
[How to Charge LiPo Battery](https://robocraze.com/blogs/post/how-to-charge-lipo-battery)
[How to Charge a LiPo Battery](https://www.makeuseof.com/how-to-charge-a-lipo-battery/)




# Lithium-Ion vs Lithium Polymer Battery
While [Lithium-ion batteries (Li-ion)][01] have remained traditionally in all your portable gadgets and smartphones,
[lithium polymer battery (LiPo)][02] are the ones that get utilized in more advanced devices and modern flagship gadgets,
but most of today's all-electric vehicles use Li-ion batteries (though the exact chemistry often varies from that of consumer electronics batteries).
You might think if both these batteries get used in electronic gadgets, they are interchangeable ... not true.
There are important differences between the two, mainly convenience, longevity, and battery safety.

Li-ion batteries have existed for a long time now,
and it is still the most prevalent battery choice for almost every electronic device.
The main reason why these batteries are so popular is that they are long-lasting,
hold a high energy density, and are comparatively affordable to create.
Li-ion batteries can last for approximately 2-3 years or 300-500 charge rounds.

LiPo batteries utilizes a dry solid, gel-like electrolyte rather than a liquid electrolyte,
giving them more options in configurations and sizes.
They are generally consider safter than Li-ion but are not immune from problems like getting punctured or overheated.

For an excellent comparison of Li-ion and LiPo batteries, see [this article][03].
Key technical considerations when choosing a battery are
[energy density][04], [specific energy][05], [memory effect][06] and [self-discharge][07].
The bottomline, for hobbies and most consumer electronics, LiPo batteries are safer, lighter,
have a longer life, charge faster, but can be twice as expensive as Li-ion batteries.

Sources:
* [Lithium Ion vs. Lithium Polymer Batteries – Which Is Better?](https://blog.ravpower.com/2017/06/lithium-ion-vs-lithium-polymer-batteries/)
* [Lithium-Ion vs Lithium Polymer Battery][03]
* [Lithium-ion vs Lithium-Polymer Batteries](https://www.linkedin.com/pulse/lithium-ion-vs-lithium-polymer-batteries-sumit-vashista/)

# Selecting and Caring for LiPo Batteries
* [A Guide to Understanding LiPo Batteries](https://www.rogershobbycenter.com/lipoguide)
* [LiPo 3S Battery 101: All About LiPo 3S Batteries](https://www.batteryequivalents.com/lipo-3s-battery-101-all-about-lipo-3s-batteries.html)
* [LiPo Battery Charge Rate Calculator](https://www.hopptbattery.com/a-quick-guide-of-manufacturing-options-for-wearables-4/)

## How are LiPo Batteries Identified
There are four main ratings that you need to be aware of on a LiPo battery.
Lets say we have a battery that states its a 50C, 5000mAh, 3C Charge Rate, 2S 7.4V battery.
What does all this mean:

* **Cell Count / Voltage** - A LiPo cell has a nominal voltage of 3.7V.
For the 7.4V battery above, that means that there are two cells in series (which means the voltage gets added together).
This is sometimes why you will hear people talk about a "2S" battery pack - it means that there are 2 cells in Series.
So a two-cell (2S) pack is 7.4V, a three-cell (3S) pack is 11.1V, and so on.
* **Capacity** - The capacity of a battery is basically a measure of how much power the battery can hold.
The typical unit of measure here is milliamp hours (mAh).
This is saying how much drain can be put on the battery to discharge it in one hour.
Sometime Capacity is expressed in ampere hours (Ah), where 1Ah = 1000mAh.
* **Discharge Rating ("C" Rating)** - The C Rating (the "C" in C Rating actually stands for Capacity)
is simply a measure of how fast the battery can be discharged safely and without harming the battery.
Using the above battery, here's the way you find out the maximum safe continuous amp draw:
50C = 50 x Capacity (in Amps). Calculating the C-Rating of our example battery: 50 x 5A = 250A
* **Charge Rate** - Just as a battery has a C rating for discharging, C rating for charging as well.
For the vast majority of LiPo, the Charge Rate is 1C.
The equation works the same way as the previous discharge rating, where 1000mAh = 1A.
So, for our 5000mAh LiPo, we should set the charger at 5A as the correct charge rate.
The safest charge rate for our LiPo batteries is 3C, or 3 x capacity of battery in Amps.

>**NOTE:** Nominal voltage is not printed on the battery but is the default,
>resting voltage of a battery pack. Its valued for a 1S battery is 3.7V.
>This is how the battery industry has decided to discuss and compare batteries.
>It is not, however, the full charge voltage of the cell.
>LiPo batteries are fully charged when they reach 4.2V/cell, and their minimum safe charge,
>as we will discuss in detail later, is 3.0V/cell.
>3.7V is pretty much in the middle, and that is the nominal charge of the cell.

### The Parameter's Practical Meaning
**Voltage** directly influences the RPM of the electric motor (brushless motors are rated by kV, which means 'RPM per Volt').
So if you have a brushless motor with a rating of 3,500kV,
that motor will spin 3,500 RPM for every volt you apply to it.
On a 2S LiPo battery, that motor will spin around 25,900 RPM (2 x 3.7 x 3500 = 25,900 RPM).
On a 3S, it will spin a whopping 38,850 RPM (3 x 3.7 x 3500 = 38,850 RPM).
So the more voltage you have, the faster you're going to go.

**Capacity** of the battery is like the fuel tank - which means the capacity determines how long you can run before you have to recharge.
The higher the number, the longer the run time.
The bigger the capacity, the bigger the physical size and weight of the battery.
Another consideration is heat build up in the motor and speed control over such a long run.
Unless periodically checked, you can easily burn up a motor if it isn't given enough time to cool down.
Keep that in mind when picking up a battery with a large capacity.

The **C Rating** lets us calculate the maximum sustained amperage load you can safely put on the battery.
Going higher than that will result in, at best, the degradation of the battery at a faster than normal pace.
At worst, it could burst into flames. So our example battery can handle a maximum continuous load of 250A.

While the **Charge Rate** is the safe rate to charge you LiPo battery,
never charge your LiPo batteries unattended!
There is always the potential for fire when using or charging a LiPo batteries.
Another safety precaution is to charge the LiPo in a fire-resistant container.

## How to Charge LiPo Battery
Lithium polymer (LiPo) batteries are a wonder of the modern age
and have revolutionized the hobby of flying RC planes.
But LiPo batteries require specialized care and therefore a LiPo-compatable charger.
They charge using a system called **CC/CV charging**.
It stands for Constant Current / Constant Voltage.
Basically, the charger will keep the current, or charge rate,
constant until the battery reaches its peak voltage (4.2V per cell in a battery pack).

The second reason that you need a LiPo-compatible charger is **balancing**.
Balancing is a term we use to describe the act of equalizing the voltage of each cell in a battery pack.
We balance LiPo batteries to ensure each cell discharges the same amount.
This helps with the performance of the battery. It is also crucial for safety reasons.

For the vast majority of LiPo battries,
the safest charge rate for most LiPo batteries is 1C, or 1 x capacity of battery in Amps.
However, more and more LiPo batteries are coming out these days that advertise faster charging capabilities,
like the example battery we had in the previous section.

Sources:
* [Understanding RC Batteries By Horizon Hobby](https://www.youtube.com/watch?v=PaPpRaJrzyI)
* [All about lipos for RC models](https://www.youtube.com/watch?v=ZJHlJYDJohc)
* [How to Charge LiPo Battery](https://robocraze.com/blogs/post/how-to-charge-lipo-battery)
* [HobbyTech Toys: LiPo Battery User Giude](https://hobbytechtoys.com.au/pages/lipo-battery-user-guide)

### Parallel vs. Series Charging

### How to Make Your Batterys Last Longer and When to Throw Them Out
* [Is Your LiPo Safe To Charge | WHEN TO THROW IT OUT](https://www.youtube.com/watch?v=l43Kx0OxpKI)
* [LiPo Battery Basics: How to Make Them Last Longer!](https://www.youtube.com/watch?v=94t0_uEmtg0)

### Balance Charger
A balance charger (or balancer) does this by monitoring the individual cell voltages in a pack through a connector on the pack (called a balance connector) and adjusting their rate of charge accordingly. When such a balancer is built into a charger, the charger is known as a Balance Charger or Balancing Charger.

* [The most over-looked lipo charger spec: Balance Current](https://www.youtube.com/watch?v=XEIWdZHXK1c)

### Battery Charger
I purchased the [Tenergy TB-6B 50W Balancing Charger][50]
for NiMH/NiCD/Li-PO/Li-Fe/SLA batteries.
It can a 1S to 6S cell Li-Ion/Li-Po/LiFe pack with a maximum current of 5A
and maximum discharge current of 1A.
it contains a wide range of charging connectors:
[XT90](https://components101.com/connectors/xt90-battery-connector),
[XT60](https://www.gobilda.com/xt60-connector-pack-mh-fc-x-5-fh-mc-x-5/),
HiTech, JST, Tamiya, Mini Tamiya, Deans, bare leads, and EC3.
And if you have a wide range of battery types you are using,
it can store up to 10 different battery charging profiles.

* [Tenergy TB-6B manual](https://system.na2.netsuite.com/core/media/media.nl?id=1036221&c=671216&h=41002c9378503e4db96c&_xt=.pdf)
* [iMAX B6 Pro: How to Safely Charge Your Batteries // Quick Tip](https://www.youtube.com/watch?v=MeAlEUb_vgg)
* [Understanding RC Battery Chargers by Horizon Hobby](https://www.youtube.com/watch?v=MLfILtFVE_Q)
* [The 4 Best LiPo Chargers for the Money – Reviews 2019](http://www.mechanicalcaveman.com/best-lipo-charger-review-for-the-money-rc-lithium-polymer-battery/)

## Battery Charger
For charging the LiPo battery,
I purchased the [Tenergy TB6-B Balance Charger/Discharger][27],
one of the [top of the line chargers][28].
It can charge 1S to 6S battery packs for NiMH/NiCD/LiPo/LiFe
and comes with octopus multi-charging harness with
tamiya, mini tamiya, JST, HiTec, EC3, Deans connectors to be compatible with many charging connectors.
It has features like Li-ion / LiPo balancing charging, fast charging,
data storage, cyclic charging and discharging,
with a maximum charge current is 5A, and the maximum discharge current is 1A.

For operating the charge,
check out the [TB6B Product Manual][29],
or better yet, [this video][30] or [this video][31].
For learning more about battery care and safety,
consider the following videos:

* [Top 5 causes of Lipo Battery Fires - Lipo charging mistakes](https://www.youtube.com/watch?v=LIWUYSDWjfk)
* [Lessons In Li-Ion Safety](https://hackaday.com/2019/11/13/lessons-in-li-ion-safety/)

## 1S Whoop Battery Charger
ViFLY WhoopStor 3is a 6 port charger and dis-charger specifically for 1S whoop batteries.

* It comes with a LCD status display, and can support both PH2.0 and BT2.0 connectors which are popular on Tiny Whoop quadcopters.
* It includes both charging and discharging functions. Just select your target voltage, it will do it for you automatically.
* The charge current range is from 0.3A to 1.3A, you can choose different charge current for different size batteries.
* 6 independent charging channels, not necessary to ensure the batteries are all the same voltage and same size. You also can unplug one that's done and plug in another while the others are still charging.
* It supports Type-C, XT60 and DC power input. Type-C used PD and QC protocol that supports fast charge at 9V and 12V, but it not supports regular 5V USB charge.
* Memory feature of remembering last time settings, no need to set the charge current every time you turn it on.

* [The New Best Tiny Whoop 1S LiPo Charger // WHOOPSTOR V3](https://www.youtube.com/watch?v=inUlovUoYj0)
* [They say it's the BEST 1S Lipo Charger? - ViFly WhoopStor 3 Review](https://www.youtube.com/watch?v=BC7urftC1KQ)

* [The best way to charge and store 1S LiPo batteries](https://www.youtube.com/watch?v=OjaQzCA1b8A)


Make sure to charge a sutable 1S LiPo battery (regular or high voltage).
I'm using [BetaFPV's BT2.0 550mAh 1S Batteries][33], a high voltage battery, on the Meteor75 Pro.

* Specification for BetaFPV BT2.0 550mAh 1S Battery
    * **Capacity:** 550mAh
    * **Rate:** 40C (continuous) / 80C (burst)
    * **Voltage:** 3.8V
    * **Battery type：LiHv (3.8~4.35V)
    * **Dimension:** 69.5*16.2*6.5mm
    * **Connector:** BT2.0 connector
    * **Weight:** 13.99g
* Charging for BT2.0 550mAh 1S Battery
    * **Charging Voltage & Current:** 4.35V at 0.5A
    * **Fully Charged:** This battry is considered fully charged when its at 4.35V
    * **Storage Charge:** When storing the battery, its voltage should be 3.85V

I'm using the [VIFLY WhoopStor 3 1S LiPo Battery Storage Charger and Discharger][34].
Setting that you should use are:
* Storage Charge for regular LiPo: 3.80V
* Storage Charge for high voltage LiPo: 3.85V
* Full Charge for regular LiPo: 4.20V
* Full Charge for high voltage LiPo: 4.35V

>**NOTE:** For the vast majority of LiPos, the Charge Rate is 1C. So for our 550mAh battery, 0.55Ah / 1C = 0.55A
>A 1S LiPo cell should NEVER be discharged below 3.0V.
>Discharging a LiPo cell lower than 3.0V causes a usually permanent degradation of the cell's ability to absorb and retain a charge.

Sources:
* [BetaFPV's BT2.0 550mAh 1S Batteries][33]
* [Vifly Whoopstor 3 1s Battery Storage Charger And Discharger - Review And Demo](https://www.youtube.com/watch?v=PXdE8ZXIqd4)
* [The BEST 1S Charger Just Got BETTER - VIFLY WhoopStor 3 Review](https://www.youtube.com/watch?v=5qgU6P_DOBs)



## Measuring LiPo Charge Level
Battery-powered projects require you to monitor your battery's life.
Measuring battery voltage is not ideal, because the voltage doesn't drop linearly.
Battery charge level, aka fuel gauges, are a better alternative.
They work straight away, don't consume power while in standby,
and they're accurate without any calibration!

* [Vifly Whoopstor 3 1s Battery Storage Charger And Discharger - Review And Demo](https://www.youtube.com/watch?v=PXdE8ZXIqd4)
* [Correctly Measure Battery Level - MAX17048 (ESP32 + Arduino series)](https://www.youtube.com/watch?v=mhmD-QA6kf0)
* [Adafruit MAX17048 LiPoly / LiIon Fuel Gauge and Battery Monitor](https://learn.adafruit.com/adafruit-max17048-lipoly-liion-fuel-gauge-and-battery-monitor)

# Battery Safety

## LiPo Storage
* [How long can you leave your lipos fully charged without damaging them?](https://www.youtube.com/watch?v=Y9jAU1KL8oc)

## LiPo Battery Storage Bag
* [Hobbymate Lipo Safety Bag Review and Test](https://www.youtube.com/watch?v=dSnYDvj3BDs)

LiPo batteries will be permanently damaged if the voltage of any cell drops below 3.0 volts.





# Best battries
* [These are the best Whoop battery. It's not even close](https://www.youtube.com/watch?v=0j_xoeO1Las)










# Background
* [Batteries? What For?](https://www.sparkfun.com/news/2913)
* [A Quick History of the Battery](http://hackaday.com/2016/10/29/a-quick-history-of-the-battery/)
* [Understanding Advanced Batteries and Energy Storage – Part I](http://investorintel.com/technology-metals-intel/understanding-advanced-batteries-energy-storage-part/)
* [A Description of Maddening Battery Terminology](http://hackaday.com/2014/09/26/a-description-of-maddening-battery-terminology/)
* [An Average Introduction To LiPo Batteries](http://www.averagemanvsraspberrypi.com/2016/06/lipo-batteries.html)
* [A Beginner’s Guide to Lithium Rechargeable Batteries](https://hackaday.com/2020/06/11/a-beginners-guide-to-lithium-rechargeable-batteries/)
* [Lithium-Ion Shipping and Travel Regulations: What You Need to Know](https://www.allaboutcircuits.com/news/lithium-ion-shipping-and-travel-regulations-what-you-need-to-know/?utm_source=All+About+Circuits+Members&utm_campaign=2e59b3d647-EMAIL_CAMPAIGN_2017_04_06&utm_medium=email&utm_term=0_2565529c4b-2e59b3d647-270523833/)
* [Battery management training](http://www.ti.com/power-management/battery-management/support-training.html)
* [Coin Cells: The Mythical Milliamp-Hour](https://hackaday.com/2017/12/22/coin-cells-the-mythical-milliamp-hour/)
* [A Deep Dive On Battery Life](https://hackaday.com/2023/07/28/a-deep-dive-on-battery-life/)

* [n Exhaustive Guide To Building 18650 Packs](https://hackaday.com/2019/06/12/an-exhaustive-guide-to-building-18650-packs/)

* [All About Batteries](https://learn.adafruit.com/all-about-batteries)

* [Battery University](https://batteryuniversity.com/)

* [Li-ion Battery Low-Level Intricacies Explained Excellently](https://hackaday.com/2021/12/21/li-ion-battery-low-level-intricacies-explained-excellently/)

# Lithium-ion Batteries
* [Lithium-Ion Batteries Are Your Friends](https://hackaday.com/2022/09/06/lithium-ion-batteries-are-your-friends/)
* [Lithium-Ion Batteries Are Easy To Find](https://hackaday.com/2022/10/03/lithium-ion-batteries-are-easy-to-find/)
* [Li-Ion & LiPoly Batteries](https://learn.adafruit.com/li-ion-and-lipoly-batteries)
* [Better Battery Management Through Chemistry](https://hackaday.com/2019/10/07/better-battery-management-through-chemistry/#more-377655)
* [Protect Your Batteries Before You Wreck Your Batteries](https://hackaday.com/2019/10/30/protect-your-batteries-before-you-wreck-your-batteries/)

http://batteryuniversity.com/learn/article/types_of_lithium_ion
http://www.digikey.com/en/articles/techzone/2012/sep/a-designers-guide-to-lithium-battery-charging

* [Chemistry Nobel Goes to Lithium Battery Innovators](https://www.quantamagazine.org/chemistry-nobel-goes-to-lithium-battery-innovators-20191009/)



# Choosing Battery Technology
* [Battery Basics – Choosing a Battery for Your Project](http://hackaday.com/2014/12/16/battery-basics-choosing-a-battery-for-your-project/)
* [An Obsessively Thorough Battery (and more) Showdown](http://hackaday.com/2014/09/05/an-obsessively-thorough-battery-and-more-showdown/)
* [Choosing The Right Battery For Your Electric Vehicle Build](https://hackaday.com/2020/01/07/choosing-the-right-battery-for-your-electric-vehicle-build/)

* [Why Samsung’s Lithium Batteries Explode and How They Could Change Electronics](http://www.allaboutcircuits.com/news/why-samsungs-lithium-batteries-explode-and-how-they-could-change-electronic/?utm_source=All+About+Circuits+Members&utm_campaign=5a64219bdc-EMAIL_CAMPAIGN_2016_11_03&utm_medium=email&utm_term=0_2565529c4b-5a64219bdc-270523833/)
* [Tour de Force Battery Hacking](http://hackaday.com/2016/09/03/tour-de-force-battery-hacking/)
* [A Li-ion Battery Charging Guide](http://hackaday.com/2014/09/21/a-li-ion-battery-charging-guide/)
* [Multi-Cell LiPo Charging](https://learn.adafruit.com/multi-cell-lipo-charging)
* [Li-ion battery charging](http://www.instructables.com/id/Li-ion-battery-charging/?ALLSTEPS)
* [AN OBSESSIVELY THOROUGH BATTERY (AND MORE) SHOWDOWN](http://hackaday.com/2014/09/05/an-obsessively-thorough-battery-and-more-showdown/)
* [The Mystery of the Boiled Batteries](http://hackaday.com/2016/01/02/the-mystery-of-the-boiled-batteries/)
* [The Best NiMh Charger?](http://hackaday.com/2015/07/09/the-best-nimh-charger/)
* [Hackaday Dictionary: Lithium Ion Batteries](http://hackaday.com/2016/05/20/hackaday-dictionary-lithium-ion-batteries/)

* [Are LiFePO Batteries better? How to Use them For Small Projects](https://www.youtube.com/watch?v=eiyBavjQ1Rk)


# LiPo Charger Board
* [This True Hardware Hack Supercharges Your ATtiny MCU, or Alternatively, Gives Your Batteries Brains!](https://www.hackster.io/news/this-true-hardware-hack-supercharges-your-attiny-mcu-or-alternatively-gives-your-batteries-brains-97d747bfa7c7)
* [TP4056 - Battery Charging Board](https://www.amazon.com/HiLetgo-Lithium-Battery-Charging-Protect/dp/B00LTQU2RK/ref=asc_df_B00LTQU2RK)





* [10 RC LiPo Mistakes & How to Avoid Them](https://www.youtube.com/watch?v=lQtKgiv70DQ)



## Battery
[Gens ace 5000mAh 11.1V 3S 50C 3 Cell LiPo Battery Pack][32] with XT60 and Deans Plug



## Electronic Speed Control (ESC)
An [Electronic Speed Control (ESC)][10] is an electronic circuit that
controls and regulates the speed of an electric motor.
It may also provide reversing of the motor and [dynamic braking][09].

The ESC receive an input pulse position modulation (PPM) signal from the receiver.
This PPM signal is the exact same type of signal that controls the servos.
The ESC uses this proportional signal from the throttle channel of the receiver
to determine how much power to send to your motor to maintain the desired speed.

In the early days of RC technology, it wasn't uncommon to use
one battery for the receiver and another for the motor.
Now a days a battery eliminator circuit (BEC) with in the ESC to the receiver battery.
The high voltage of your LiPo pack is stepped down by the BEC to
a lower voltage of 5-6 volts to power a typical receiver.

An ESC will have three sets of wires.
One set of leads will plug into your your RC car's main battery.
The second set of leads will have a standard servo wire that plugs
into the throttle channel of your RC car's receiver.
The third set of wires actually power the motor.

ESC's are rated for a maximum current.
The more current an ESC is rated for,
the more expensive and heavier it will be.
Choose an electronic speed controller that is rated for slightly
more than what your motor will pull at full throttle.

LiPo batteries will be permanently damaged if the voltage of any cell drops below 3.0 volts.
For this reason, LiPo batteries require an ESC with a low voltage cutoff (LVC).
The LVC will cut the power to the motor when the voltage reached 3.2V,
or whatever you set the LVC to be.

You will also need to choose an ESC that can handle the voltage of the battery pack you plan to use.
The voltage rating for each ESC is clearly stated in the specifications.

* [RC Basics - Understanding Electronic Speed Controllers (ESC)](https://www.youtube.com/watch?v=OZNxbxL7cdc)
* [An Open Source ESC For Brushless Motors](https://hackaday.com/2019/05/15/an-open-source-esc-for-brushless-motors/)

## Hobbypower 60A SL V2 ESC
I used the recommended [Hobbypower 60A SL V2 ESC][12]
which suports 2-3 cells LiPo
with a continuous current 60A and burst current 380A.
It has a built in BEC who's output is 6V/1.5A to power the radio transmitter.

>**NOTE:** A [battery eliminator circuit (BEC)][34] is an electronic circuit designed
>to deliver electrical power to other circuitry without the need for multiple batteries.
>This ESC has a builtin BEC to deliver power to the radio system.

* Racing Features
    * It has three running modes: Racing mode (Forward), Forward/Backward mode, and Rock Crawler mode.
    * Proportional ABS brake function with 4 steps of maximum brake force adjustment,
    8 steps of drag-brake force adjustment and 4 steps of initial brake force adjustment.
    * It has 9 start modes (Also called "Punch" ) from "Soft" to "Very aggressive".

* Protection Featues
    * Multiple protection features: Low voltage cut-off protection for lithium or nickel battery,
    Over-heat protection, throttle signal loss protection, motor blocked protection.

* Programming Feature
    * With 8 steps of timing adjustment to get the best compatibility with various of motors.
    * Easily program with only one button and compatible with pocket-sized program card.
    * The ESC is USB supported. The firmware of the ESC can be updated through
    an USB adapter on the Advanced LCD Program Box (Optional device).

* [An Open Source ESC For Brushless Motors](https://hackaday.com/2019/05/15/an-open-source-esc-for-brushless-motors/)
* [Battle Tested Current Limiter for Cheap DC Motor Controllers](https://hackaday.com/2019/05/11/battle-tested-current-limiter-for-cheap-dc-motor-controllers/)

Hobbypower 60A SL V2 Brushless Speed Controller ESC - https://www.amazon.com/gp/product/B071777MG2/
http://www.rcuniverse.com/forum/rc-electric-off-road-trucks-buggies-truggies-more-147/11640199-60a-sl-brushless-esc.html
http://www.hobbywing.com/products/enpdf/EzRun60A.pdf




The [Gens ace 5000mAh 11.1V 3S 50C 3 Cell LiPo Battery Pack][32]



# Cold Environment - Lithium Iron Phosphate
LiPo cells must not be charged in freezing temperatures (apart from certain special low temp products), else the cell can rapidly be destroyed due to lithium metal deposition at the anode. Also you need to be careful charging them, especially when they’re heavily discharged, as they are easily damaged without the proper treatment. LiPo cells operate based on chemical principles – lithium ions literally have to move around inside the structure, and eventually the battery will wear out.

Supercapacitors have the advantage of very long life (but sometimes, they do leak) much more aggressive charging and discharging behaviours and will operate down to very low temperatures. This makes them very useful when a large amount of power is available sporadically (for super fast charge cycles) or in places where temperatures stay persistently very low, such as up a mountain were solar will work, albeit slowly, but LiPo batteries will definitely not be suitable.

Other battery chemistries are available, such as Lithium Iron Phosphate which can tolerate the cold.

# LiFePO Batteries
* [#64 What is the Ideal Battery Technology to Power 3.3V Devices like the ESP8266?](https://www.youtube.com/watch?v=heD1zw3bMhw)
* [#65 How to use Lifepo4 Batteries (Tutorial)](https://www.youtube.com/watch?v=DicVZfW5YL0)
* [Are LiFePO Batteries better? How to Use them For Small Projects](https://www.youtube.com/watch?v=eiyBavjQ1Rk)
* [#400 The Best Power Source for ESP32/ ESP8266 Projects](https://www.youtube.com/watch?v=FrCgQgahzsI)

## Voltages
Depending on the design and chemistry of your lithium cell,
you may see them sold under different nominal voltages.
Almost all lithium polymer batteries are 3.7V or 4.2V batteries.
What this means is that the maximum voltage of the cell is 4.2v
and that the "nominal" (average) voltage is 3.7V.
As the battery is used, the voltage will drop lower and lower.
Once you hit 3.4V the battery is consided dead
and at 3.0V the protective cutoff circuitry disconnects the battery.
You should see the number 3.7V written on the battery itself somewhere.

**NOTE:** You may also run across 4.1V/3.6V batteries.
These are older than 4.2V/3.7V - they use a
slightly different chemistry and you'll see the 3.6V marking on the cell.
Nowadays you may also be able to purchase 4.35V cells!
These are the latest chemistry, they have a little more power as indicated
by the voltage being higher than 4.2V.
They tend to be cylinder lithium ion's used for laptop batteries, and lights.
Make sure when you're buying batteries and chargers to match them up!
Overcharging a 3.6V battery by attaching it to a 4.2V battery charger
can at the very least permanently damage your battery and at worst cause a fire!

## Protective Circuity
Lithium ion/polymer batteries are extremely power dense.
This makes them great for reducing size and weight of projects.
However, they are not 'safe' batteries and require extra care.
Under certain conditions, some battery chemistries and Lithium is one of them,
are at risk of [thermal runaway][52], leading to cell rupture or combustion.
Thermal runaway is a situation where an increase in temperature changes
the chemical conditions causing a further increase in temperature,
sometimes leading to a destructive heating or fire.

A circuit board attached to the battery can monitor the battery voltage and
the current going out.
These are often referred to simply as protection circuits.
They are very common on standard batteries but you must check the datasheet
or product image to verify that a protection circuit is attached
On Adafruit's lithium ion/ployer batteries,
a protection circuit is soldered onto the battery
and then taped into the little cavity at the top of the battery.
This is very common for lipoly cells and generally provide the following protection:


# How to Prolong Battery Life
* [Elevating Self Discharge](https://batteryuniversity.com/learn/article/elevating_self_discharge)
* [Battery Life Optimization in IoT devices with the Multi-Channel Power Probe](https://scdn.rohde-schwarz.com/ur/pws/dl_downloads/dl_application/application_notes/1td07/1TD07_1e_BatteryLife_IoT~1.pdf)
* [Power consumption explained](https://blog.nordicsemi.com/getconnected/power-consumption-explained)
* [How to optimize energy efficiency in smart devices](https://blog.nordicsemi.com/getconnected/how-to-optimize-energy-efficiency-in-smart-devices)
* [The Importance of Average Power Consumption to Battery Life](https://blog.nordicsemi.com/getconnected/the-importance-of-average-power-consumption-to-battery-life)
* [Improve battery life in Ultra Low Power wireless applications](https://blog.nordicsemi.com/getconnected/improve-battery-life-in-ultra-low-power-wireless-applications)
* [Power Profiler Kit II](https://blog.nordicsemi.com/getconnected/power-profiler-kit-ii-brings-greater-insight-to-wireless-power-consumption)

## Self Discharge
Much attention can be paid to extending battery life through the use of
low-power semiconductors, communication protocols,
and minimizing the time a device spends in “active’ mode.
However, for very long running applications,
these energy-saving techniques cannot equal the amount of energy lost to
annual battery self-discharge, which often approaches the total amount of energy used to operate the device.

Power sources alkaline batteries are ill-suited for long term deployments,
suffering from very high annual self-discharge rates that exhaust their capacity in 2-3 years or less.
Conversely, bobbin-type Lithium-thionyl chloride (LiSOCl2) batteries
are preferred for long-term deployments due to their
high energy density, high capacity, high voltage (3.6 V),
and an incredibly low annual self-discharge rate that permits up to 40-year battery life.

* http://www.tadiranbat.com/pulsesplus.html
* https://www.amazon.com/Professional-Lithium-Batteries-3-6-Volts/dp/B074QMH2DZ/ref=sr_1_1_sspa

# Smart Battery System
Smart Battery System (SBS) is a specification for managing a smart battery, usually for a portable computer. It allows operating systems to perform power management operations via a smart battery charger based on remaining estimated run times by determining accurate state of charge readings.

* [PackProbe Reports Laptop Battery Health](https://hackaday.com/2019/06/26/packprobe-reports-laptop-battery-health/)
* [build a dedicated SMBus scanner](https://hackaday.com/2016/09/03/tour-de-force-battery-hacking/)
* [Turn Off Those Batteries With Their Protection Chip](https://hackaday.com/2020/04/05/turn-off-those-batteries-with-their-protection-chip/)

# Battery Degradation
A useful why to think about a batterys degradation or age
in terms of present capacity versus original (new) capacity.

A useful battery has predictable behavior; it can supply a constant amount of power, for a predictable amount of time, within a narrow voltage range. The ‘capacity’ or ‘C rating’ for batteries is probably the most useful parameter to express this.

* [Predicting Battery Degradation with a Trinket M0 and Python Software Algorithms](https://www.allaboutcircuits.com/projects/how-to-build-battery-age-prediction-using-software-algorithms)

## Smoke Stopper / ShortSaver
The [Flight XT30/ XT60 Smoke Stopper][51]
short-circuit protection / safety inspector for 2S to 6S LiPo batteries.
It can help avoid damage when you power on your quadcopter for the first time.
It has both a XT30 and XT60 connector so it can fit a range of batteries.
The Smoke Stopper has an LED indicator that turns solid green in normal situation (aka correctly wired & no short circuit),
but the LED indicator turns off and starts beeping in abnormal situation (aka there is a wiring error & there is an overload or short circuit).

* [ViFly ShortSaver is the smoke stopper you always wanted](https://www.youtube.com/watch?app=desktop&v=f37FeWSYrmo)
* [Your smoke stopper is lying to you. Here's the truth](https://www.youtube.com/watch?v=0CQA5dPMYJQ)
* [VIFLY Short Saver V2 - No More Magic Smoke](https://www.youtube.com/watch?v=RT_5AQTq5Ig)



------



# CellMeter
I also purchased a [Cellmeter 8 Digital Battery Capacity Checker][13] from Amazon in October of 2023.
This device support battery types LiPo, LiFe, Li-ion, NiCd, NiMH
It measure battery cell voltages, total voltages, lowest cell voltage, highest cell voltage,
voltage gap between highest cell voltage and lowest cell voltage, remaining battery capacity (%).

Sources:
* [How to Use the CellMeter 8](https://www.youtube.com/watch?v=xAI3VjOPfN4)
* [DRASTICALLY REDUCE your storage charge time. Cellmeter 8. Tech Tuesday](https://www.youtube.com/watch?v=rWcpb_nSEqM)



[01]:https://en.wikipedia.org/wiki/Lithium-ion_battery
[02]:https://en.wikipedia.org/wiki/Lithium_polymer_battery
[03]:https://robocraze.com/blogs/post/lithium-ion-vs-lithium-polymer-battery
[04]:https://en.wikipedia.org/wiki/Energy_density
[05]:https://en.wikipedia.org/wiki/Specific_energy
[06]:https://en.wikipedia.org/wiki/Memory_effect
[07]:https://en.wikipedia.org/wiki/Self-discharge
[08]:
[09]:https://en.wikipedia.org/wiki/Dynamic_braking
[10]:https://en.wikipedia.org/wiki/Electronic_speed_control
[11]:https://www.hobbypartz.com/07e-hobbywing-led-programcard.html
[12]:https://www.amazon.com/gp/product/B071777MG2/
[13]:https://www.amazon.com/gp/product/B08K8WZ828/?th=1

[27]:https://www.amazon.com/gp/product/B00466PKE0/ref=ppx_yo_dt_b_asin_title_o08_s01
[28]:https://www.thesmartconsumer.com/best-lipo-charger
[29]:https://power.tenergy.com/content/manuals/01435_manual.pdf
[30]:https://www.youtube.com/watch?v=5AIAomVTKHw
[31]:https://www.youtube.com/watch?v=xbM4pjMIGHY
[32]:https://www.amazon.com/gp/product/B01JCSOJIY/ref=ppx_yo_dt_b_asin_title_o08_s01
[33]:https://betafpv.com/collections/batt-1s/products/bt2-0-550mah-1s-battery-4pcs
[34]:https://viflydrone.com/products/vifly-whoopstor-6-ports-1s-battery-storage-charger-discharger

[50]:http://www.tenergy.com/01321
[51]:https://www.amazon.com/iFlight-Stopper-Short-Circuit-Protection-Inspecting/dp/B08MT4YKJY
[52]:https://en.wikipedia.org/wiki/Thermal_runaway




