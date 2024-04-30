<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----


* [Raspberry Pi 5. Major eeprom update 17/04/2024. Network install & more](https://www.youtube.com/watch?v=prqzOg-GC40)
* [Ubuntu 24.04 LTS Raspberry Pi 5. NVMe install Fix](https://www.youtube.com/watch?v=2qkqCB8x2nM)
* [Raspberry Pi 5 vs Intel N100 mini PC comparison – Features, Benchmarks, and Price](https://www.cnx-software.com/2024/04/29/raspberry-pi-5-intel-n100-mini-pc-comparison-features-benchmarks-price/)



* [The Best Raspberry pi 5 Case Is here! Argon NEO 5 BRED Hands On](https://www.youtube.com/watch?v=4FQFgsnKvYM)
    * [Argon NEO 5 BRED for Raspberry Pi 5](https://www.amazon.com/Argon-NEO-BRED-Raspberry-Pi/dp/B0CP3MGMTD)
* [Unleash the power of the Raspberry Pi 5 - 1TB NVME and Argon ONE NVME case](https://www.youtube.com/watch?v=kmgTrwNmZV8)
    * [Argon ONE V3 M.2 NVME PCIE Case](https://argon40.com/products/argon-one-v3-m-2-nvme-case)
    * [Argon NEO 5 M.2 NVME PCIE Case for Raspberry Pi 5](https://argon40.com/products/argon-neo-5-m-2-nvme-for-raspberry-pi-5)

* [Dual Edge TPU: Double Power, Same Slot](https://www.youtube.com/watch?v=W-LlUe_EXjg)
* [AI on a Pi? Believe it!](https://www.youtube.com/watch?v=so8_h0EKPWU&t=634s)
* [CPU vs GPU vs TPU vs DPU vs QPU](https://www.youtube.com/watch?v=r5NQecwZs1A)

* [Testing Cytron MAKERDISK M.2 NVMe SSDs on Raspberry Pi 5 with GEEKWORM X1001 and Waveshare M.2 PCIe HAT+](https://www.cnx-software.com/2024/04/07/review-cytron-makerdisk-nvme-ssd-raspberry-pi-5-geekworm-x1001-waveshare-m2-pcie-hat/)


|:-----------------------------------------------|:-------------------|:------:|
| [Raspberry Pi 5 / 8GB RAM][01]                 | [Seeed Studio][AA] |  $ 80  |
| [Raspberry Pi Active Cooler][02]               | [Seeed Studio][BB] |  $  5  |
| [Tensor Processing Unit (TPU)][03]             | [Amazon][CC]       |  $ 89  |
| [Coral M.2 Accelerator with Dual Edge TPU][04] | [Amazon][DD]       |  $ 85  |
| M.2 NVMe SSD                                   |                    |        |
| 27W USB-C Power Supply                         |                    |        |
|                                                |                    |        |
|                                                |                    |        |

# How to Boot From SSD
* [Testing Cytron MAKERDISK M.2 NVMe SSDs on Raspberry Pi 5 with GEEKWORM X1001 and Waveshare M.2 PCIe HAT+](https://www.cnx-software.com/2024/04/07/review-cytron-makerdisk-nvme-ssd-raspberry-pi-5-geekworm-x1001-waveshare-m2-pcie-hat/)



[01]:https://www.raspberrypi.com/products/raspberry-pi-5/
[02]:https://www.raspberrypi.com/products/active-cooler/
[03]:https://cloud.google.com/tpu/docs/intro-to-tpu
[04]:https://pi3g.com/products/machine-learning/google-coral/coral-m-2-accelerator-with-dual-edge-tpu/
[05]:

[AA]:https://www.seeedstudio.com/Raspberry-Pi-5-8GB-p-5810.html
[BB]:https://www.seeedstudio.com/Raspberry-Pi-Active-Cooler-p-5813.html
[CC]:https://www.amazon.com/dp/B07S214S5Y
[DD]:https://www.amazon.com/dp/B08KTSGN7F/









* [My Raspberry Pi 5 is a delight, and I'm excited about all its future uses](https://www.pocket-lint.com/raspberry-pi-5-review/)
* [Raspberry Pi 5 review: A huge upgrade for the tiny single-board computer](https://www.pcworld.com/article/2219346/raspberry-pi-5-review.html)
* [Raspberry Pi 5 review: The first Pi that can truly serve as a desktop](https://www.expertreviews.co.uk/raspberry-pi-foundation/raspberry-pi-5-review)
* [Raspberry Pi 5 vs N100 PC (featuring Ubuntu 23.10)](https://www.youtube.com/watch?v=hekzpSH25lk)

* [A Step-by-Step Guide to Install Kali Linux on Raspberry Pi 5](https://thesecmaster.com/a-step-by-step-guide-to-install-kali-linux-on-raspberry-pi-5/)

# Raspberry Pi Benchmark Tools
* [FINALLY! NVMe SSDs on the Raspberry Pi](https://www.youtube.com/watch?v=EXWu4SUsaY8)
* [Pi Benchmarks](https://pibenchmarks.com/)

```bash
# to run the benchmark paste/type
sudo curl https://raw.githubusercontent.com/TheRemote/PiBenchmarks/master/Storage.sh | sudo bash

# benchmark suite which allows you to quickly get an impression of system performance
# https://www.howtoforge.com/how-to-benchmark-your-system-cpu-file-io-mysql-with-sysbench
# https://www.phoronix-test-suite.com/

# cpu benchmark
sysbench cpu --cpu-max-prime=20000 --threads=4 --time=0 --events=10000 run

# file io benchmark
sysbench --test=fileio --file-total-size=150G prepare    # create a test file that is much bigger than your RAM (because otherwise, the system will use RAM for caching which tampers with the benchmark results) - 150GB is a good value
.
.
.
```

# Overclocking
* [In honor of Pi day, here's how to supercharge your Raspberry Pi 5](https://www.pocket-lint.com/how-to-speed-up-and-overclock-raspberry-pi-5-install-ssd/)
* [How to overclock the Raspberry Pi 5 beyond 3 GHz!](https://www.tomshardware.com/raspberry-pi/how-to-overclock-the-raspberry-pi-5-beyond-3-ghz)
* [The Raspberry Pi 5's 3GHz Limit Is Lifted, Thanks to a "Very Not At All Recommended" Firmware](https://www.hackster.io/news/the-raspberry-pi-5-s-3ghz-limit-is-lifted-thanks-to-a-very-not-at-all-recommended-firmware-328e7bbcaab5)

* [Raspberry Pi 5 became 25% faster by changing some numbers in the configuration file](https://technewsspace.com/raspberry-pi-5-became-25-faster-by-changing-some-numbers-in-the-configuration-file/)
* [How to overclock a Raspberry Pi 5 to 3GHz and beyond](https://www.geeky-gadgets.com/how-to-overclock-a-raspberry-pi-5/)
* [Don't buy a Raspberry Pi 5 without also buying this amazing accessory](https://www.zdnet.com/home-and-office/dont-buy-a-raspberry-pi-5-without-also-buying-this-amazing-accessory/)
* [Upgrade your Raspberry Pi 5 with a powerful graphics card](https://www.geeky-gadgets.com/add-a-graphics-card-to-raspberry-pi/)
* [I Wrote a Paper for a PhD Course on an Overclocked Raspberry Pi 4](https://medium.com/an-idea/i-wrote-a-paper-for-a-phd-course-on-an-overclocked-raspberry-pi-4-cb14c9210ed4)
* [What accessories do I need to overclock my Raspberry Pi 3 B+?](https://www.androidcentral.com/what-accessories-do-i-need-overclock-my-raspberry-pi-3-b)
* [config.txt - Overclocking options](https://www.raspberrypi.org/documentation/configuration/config-txt/overclocking.md)
* [Overclock Your Raspberry Pi The Right Way](https://hackaday.com/2018/01/16/__trashed-5/)
* [How to Overclock Any Raspberry Pi](https://www.tomshardware.com/how-to/overclock-any-raspberry-pi)

# Proxmox Server
* [Is the Raspberry Pi5 the better Proxmox Server?](https://www.youtube.com/watch?v=Qit-3upR6iA)

# Large Language Model (LLM)
* [Deploy and run LLM on Raspberry Pi 5 vs Raspberry Pi 4B (LLaMA, LLaMA2, Phi-2, Mixtral-MOE, mamba-gpt)](https://www.dfrobot.com/blog-13498.html?tracking=6594dccfd2dcd)
* [I Ran Advanced LLMs on the Raspberry Pi 5!](https://www.youtube.com/watch?v=Y2ldwg8xsgE)
* [Running a ChatGPT-Like LLM on the Raspberry Pi 5](https://www.hackster.io/shahizat/running-a-chatgpt-like-llm-on-the-raspberry-pi-5-fd67f9)

# Tensor Processing Unit (TPU)
* [Pineberry Pi Unveils New Raspberry Pi 5 HAT Add-Ons with AI Acceleration, 2.5-gig Ethernet, and More](https://www.hackster.io/news/pineberry-pi-unveils-new-raspberry-pi-5-hat-add-ons-with-ai-acceleration-2-5-gig-ethernet-and-more-1316e932d903)
* [Local AI Just Got Easy (and Cheap)](https://www.youtube.com/watch?v=mdOEaNV8NXw)
* [Coral USB Accelerator](https://www.amazon.com/dp/B07S214S5Y)
* [AI on a Pi? Believe it!](https://www.youtube.com/watch?v=so8_h0EKPWU)
* [GET STARTED WITH CORAL AND RASPBERRY PI](https://www.okdo.com/getting-started/get-started-with-google-coral-and-raspberry-pi/)
* [M.2 E-Key Wi-Fi 7 HAT for Raspberry Pi 5 also supports Google TPU](https://www.cnx-software.com/2024/02/02/m2-e-key-wifi-7-hat-for-raspberry-pi-5-google-tpu/)

* Coral USB TPU 👉 https://amzn.to/3vUkUJH
* Coral PCIe TPU 👉 https://amzn.to/3vLKfVW

* [Coral: Hardware & Software](https://coral.ai/)

# NVMe SSD
* [FINALLY! NVMe SSDs on the Raspberry Pi](https://www.youtube.com/watch?v=EXWu4SUsaY8)
* [Raspberry Pi 5 M.2 HatDrive!](https://www.youtube.com/watch?v=B9OwWnAftb4)
* [Raspberry Pi 5 with 2TB NVME SSD Geekworm Shield](https://www.youtube.com/watch?v=IUxP31rNRY4)

# TensorFlow
* [Install TensorFlow on Raspberry 64 OS](https://qengineering.eu/install-tensorflow-on-raspberry-64-os.html)

