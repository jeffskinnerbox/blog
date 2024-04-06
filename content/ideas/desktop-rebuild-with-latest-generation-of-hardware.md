<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


----




* [How to build a PC, the last guide you'll ever need!](https://www.youtube.com/watch?v=BL4DCEp7blY)
* [How to Swap your PC Motherboard - Step by Step Guide](https://www.youtube.com/watch?v=NwuSXgiGVpo)

* [Power Supply - Understanding all the Power Supply Connectors in your PC](https://www.youtube.com/watch?v=7SjQo7wrWq4)
* [I9-12900 install into MSI Pro Z690 wifi LGA 1700 motherboard](https://www.youtube.com/watch?v=dRVop7xmP7A)
* [Intel i7-13700K Install in LGA 1700 on MSI MPG Z690 Carbon WiFi Motherboard](https://www.youtube.com/watch?v=yC1f5_cWFNU)
* [How To Install an NVME M.2 SSD on MSI MPG Z690 Carbon WiFi Motherboard](https://www.youtube.com/watch?v=mM2e5BxzfPo)
* [Bios Update MSI Pro Z690 A D4 Motherboard How to, step by step procedure 13th gen compatibility](https://www.youtube.com/watch?v=KkA8gPvBy9c)




I built my current desktop Linux box,
using the [Intel Desktop Board DZ77GA-70K][05] motherboard with LGA 1155 CPU socket and DDR3 memory,
and [purchase from Amazon][06] in April 2013.
I outfited that purchase with a [3rd Gen (Ivy Bridge) 3.4GHz Intel 4 Cores i5-3570K][07]
and [8GB (2x4GB) of Corsair DDR3 1600MHz (PC3-12800) RAM][08].
(**NOTE:** As of November of 2022, you can purchase the same motherboard, CPU, and RAM for $249 + $111 + $65 = $425.)

Lately, my system has been having some stability problems, plus CPU running so hot it is forced to idle,
and given the hardware is nearly 10 years old at this time (November of 2022),
I'm thinking its time to replace it.
After much research, my replacement selection was the following:

* [MSI PRO Z690-A ProSeries][09] motherboard with LGA 1700 CPU socket, DDR5 memory, and Intel Z690 Chipset - $246 November 2022 from [Amazon][13]
    * [Manual & Document][14]
    * [Drivers & Downloads: BIOS][15]
* [12th Gen (Adler Lake) Cores i5-12600K][10] with Intel UHD 770 Graphics, 10 Cores (6P+4E) with 20M Cache, up to 4.9 GHz Unlocked, and LGA1700 600 Series Chipset 125W - $252 November 2022 from [Amazon][16]
    * [Latest Drivers & Software][17]
* [32GB (2x16GB) of Corsair DDR5 5200MHz (PC5-41600) RAM][11]
* [Crucial P3 Plus 500GB PCIe 4.0 3D NAND NVMe M.2 SSD][18] - $143 November 2022 from [Amazon][19]
* [Vetroo V5 CPU Air Cooler with 5 Heat Pipes 120mm PWM Processor Cooler for Intel LGA 1700/1200/115X][20] - $28 April 2024 from [Amazon][21]

Intel's Z690 chipset and is suitable for all 12th Gen Core (Alder Lake) processors
and supports DDR5 memory only with speeds of up to DDR5-6400.
Take note that DDR5 memory slot is NOT compatible with DDR3 or DDR4 RAM.

Research Sources:

* [How to Choose a Gaming Motherboard](https://www.intel.com/content/www/us/en/gaming/resources/how-to-choose-a-motherboard.html)
* [Best processors 2022: the top desktop CPUs from AMD and Intel](https://www.techradar.com/news/best-processors)
* [Intel Core i9-12900K and Core i5-12600K review](https://www.techradar.com/reviews/intel-core-i9-12900k-and-core-i5-12600k)
* [Intel CPUs Explained: What Are E-Cores and P-Cores?](https://www.makeuseof.com/intel-cpus-explained-what-are-e-cores-and-p-cores/)
* [Intel Core i3 vs. i5 vs. i7: Which CPU Should You Buy?](https://www.makeuseof.com/tag/intel-core-i3-vs-i5-vs-i7-one-really-need/)
* [The Best Intel Processors, Ranked](https://www.makeuseof.com/best-intel-processors-ranked/)
* [What Is Intel's Alder Lake? 4 Things You Need to Know](https://www.makeuseof.com/what-is-intels-alder-lake-architecture/)
* [How to Choose a Gaming Motherboard](https://www.intel.com/content/www/us/en/gaming/resources/how-to-choose-a-motherboard.html)
* [DDR4 vs. DDR5, The Best Memory For Gamers? Core i9-12900K, 41 Game Benchmark](https://www.youtube.com/watch?v=omumzW1AtGE)
* [DDR5 vs. DDR4 RAM: Is DDR5 worth it?](https://www.digitaltrends.com/computing/ddr5-vs-dd4-memory/)
* [DDR5 vs. DDR4: How Much Performance Will You Gain From Today's Newest RAM?](https://www.pcmag.com/news/ddr5-vs-ddr4-how-much-performance-will-you-gain-from-todays-newest-ram)
* [DDR5 vs DDR4: Is It Time To Upgrade Your RAM?](https://www.tomshardware.com/features/ddr5-vs-ddr4-is-it-time-to-upgrade-your-ram)




-----



# Benchmark Linux Desktop System
Using the article "[How to Benchmark Your Linux System][01]" as my guide,
I performed several performance benchmark test on my Linux Desktop for my
old 2013 system and my new 2024 system


Geekbench 5, Cinebench R23, and PCMark 10 to synthetically push processors to the limit using realistic workloads that you're likely to experience in day-to-day use.

[Learn How To Benchmark YOUR Linux PC!](https://www.youtube.com/watch?v=TXf5R1AOkCk)
[Benchmarking Linux Systems](https://www.baeldung.com/linux/benchmarking)
[Linux benchmark scripts and tools](https://haydenjames.io/linux-benchmark-scripts-tools/)
[9 Best Free Linux Benchmark Tools](https://www.linuxlinks.com/benchmarktools/)

## Temperature
* [How To Check CPU Temperature On Linux](https://www.technewstoday.com/cpu-temperature-linux/)
* [How to Check CPU Temperature on Linux](https://phoenixnap.com/kb/linux-cpu-temp)
* [How to check CPU temperature on Ubuntu Linux](https://www.cyberciti.biz/faq/how-to-check-cpu-temperature-on-ubuntu-linux/)
* [How to Check CPU Temperature in Linux](https://linuxhint.com/check-cpu-temperature-linux/)
* [Find Out CPU Temperature from the Command-Line](https://www.baeldung.com/linux/cpu-temperature)



[01]:https://linuxconfig.org/how-to-benchmark-your-linux-system
[02]:
[03]:
[04]:
[05]:https://www.intel.com/content/www/us/en/products/sku/63244/intel-desktop-board-dz77ga70k/specifications.html
[06]:https://www.amazon.com/gp/product/B007SSJWDS/
[07]:https://www.amazon.com/gp/product/B007SZ0E1K
[08]:https://www.amazon.com/gp/product/B004QBUL1C/
[09]:https://www.amazon.com/dp/B09KKYS967
[10]:https://www.amazon.com/gp/product/B09FX4D72T
[11]:https://www.amazon.com/gp/product/B09NCPTVX5/
[12]:
[13]:https://www.amazon.com/gp/product/B09KKYS967/
[14]:https://www.msi.com/Motherboard/PRO-Z690-A/support#manual
[15]:https://www.msi.com/Motherboard/PRO-Z690-A/support#bios
[16]:https://www.amazon.com/gp/product/B09FX4D72T/
[17]:https://www.intel.com/content/www/us/en/products/sku/134589/intel-core-i512600k-processor-20m-cache-up-to-4-90-ghz/downloads.html
[18]:https://www.crucial.com/ssd/p3-plus/ct500p3pssd8
[19]:https://www.amazon.com/gp/product/B09NCPTVX5/?th=1
[20]:https://vetroo.com/products/vetroo-v5-120mm-pwm-argb-sync-cpu-cooler-5-heat-pipes-150w-tdp?variant=43428661887210
[21]:https://www.amazon.com/gp/product/B08F21X2VP

