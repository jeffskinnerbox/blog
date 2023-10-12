<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----



#Your First Read
* [So you want to build an embedded Linux system?](https://jaycarlson.net/embedded-linux/)
* [Introduction to Embedded Linux](https://www.youtube.com/playlist?list=PLEBQazB0HUyTpoJoZecRK6PpDG31Y7RPB)

# Followed By This
* [4 tools for building embedded Linux systems](https://opensource.com/article/18/6/embedded-linux-build-tools)
* [SO YOU WANT TO BUILD AN EMBEDDED LINUX SYSTEM?](https://jaycarlson.net/embedded-linux/)
* [Mastering Embedded Linux](https://www.thirtythreeforty.net/series/mastering-embedded-linux/)


* [Run UNIX On Microcontrollers With PDP-11 Emulator](https://hackaday.com/2021/11/19/run-unix-on-microcontrollers-with-pdp-11-emulator/)
* [A PDP 11 by Any Other Name: Heathkit H11 Teardown and Repair](https://hackaday.com/2021/11/22/a-pdp-11-by-any-other-name-heathkit-h11-teardown-and-repair/)



----



# Potential Tools for Embedded Linux

## SerenityOS
A graphical Unix-like operating system for desktop computers!
SerenityOS is a love letter to '90s user interfaces with a custom Unix-like core. It flatters with sincerity by stealing beautiful ideas from various other systems.
Roughly speaking, the goal is a marriage between the aesthetic of late-1990s productivity software and the power-user accessibility of late-2000s *nix.

* [SerenityOS](https://serenityos.org/)

## Newlib
Newlib is a C library intended for use on embedded systems. It is a conglomeration of several library parts, all under free software licenses that make them easily usable on embedded products.

* [THE NEWLIB EMBEDDED C STANDARD LIBRARY AND HOW TO USE IT](https://hackaday.com/2021/07/19/the-newlib-embedded-c-standard-library-and-how-to-use-it/)
* [Newlib](https://sourceware.org/newlib/)

## picolibc
Picolibc is library offering standard C library APIs that targets small embedded systems with limited RAM. Picolibc was formed by blending code from Newlib and AVR Libc.

* [PRETTY PETITE PICOLIBC POWERS PROCESSORS](https://hackaday.com/2022/11/14/pretty-petite-picolibc-powers-processors/)

## BusyBox
* [How to use BusyBox on Linux](https://opensource.com/article/21/8/what-busybox)

## Buildroot
* [Buildroot](https://buildroot.org/)
* [Buildroot Training](https://bootlin.com/doc/training/buildroot/buildroot-labs.pdf)
* [Building custom Linux for Raspberry Pi using Buildroot](https://medium.com/@hungryspider/building-custom-linux-for-raspberry-pi-using-buildroot-f81efc7aa817)

## OpenWRT
* [OpenWrt ](https://openwrt.org/)

## Yocto
* [Yocto Project (YP)](https://www.yoctoproject.org/)

## μClinux
* [μClinux](https://en.wikipedia.org/wiki/%CE%9CClinux)
* [Tiny Linux On A No-MMU RISC-V Microcontroller](https://hackaday.com/2023/10/11/tiny-linux-on-a-no-mmu-risc-v-microcontroller/)
    * [789 KB Linux Without MMU on RISC-V](https://popovicu.com/posts/789-kb-linux-without-mmu-riscv/)

## X1501 Pico SoM
* [X1501 Pico SoM – MIPS, Linux in a 16x16mm module](https://www.cnx-software.com/2022/06/06/x1501-pico-som-mips-linux-in-a-16x16mm-module/)
* [X1501 Pico SoM](https://hackaday.io/project/185562-x1501-pico-som)

## Juice RV
* [It’s Linux – But On An ESP32](https://hackaday.com/2021/07/21/its-linux-but-on-an-esp32/)

## TinyEMU
The ESP32 is unable to run Linux because it lacks a memory management unit.
A work around is to emulating a RISC-V processor on it and booting a RISC-V version of the kernel.
The emulator is performed by TinyEMU,
a piece of software that brings both RISC-V and x86 to limited-spec platforms.

* [TinyEMU](https://bellard.org/tinyemu/)
* [It’s Linux. On An ESP32](https://hackaday.com/2022/07/14/its-linux-on-an-esp32/)

## Linux on ESP32-S3
* [Run Linux on ESP32 - how to run the Linux kernel on an ESP32](https://www.youtube.com/watch?v=5oKeVyxgwzk)
* [GitHub: xhackerustc/uc-rv32ima](https://github.com/xhackerustc/uc-rv32ima)

## Bootloader
[uboot][29] which is a popular [bootloader][30] that
supports multiple architectures (ARM, MIPS, AVR32, Nios, Microblaze, 68K and x86)
and filesystems (FAT32, ext2, ext3, ext4 and Cramfs).

Strictly speaking, a bootloader is not required to boot Linux.
The use of one (or several) bootloaders in a row to chainload (or [bootstrap][49])
a Kernel is not a categorical necessity,
but it is a preferred method to start an operating system.

* [Das U-Boot -- the Universal Boot Loader](https://www.denx.de/wiki/U-Boot)



[29]:http://www.linuxjournal.com/content/handy-u-boot-trick
[30]:http://www.addictivetips.com/mobile/what-is-bootloader-and-how-to-unlock-bootloader-on-android-phones-complete-guide/
[49]:https://en.wikipedia.org/wiki/Bootstrapping#Computing

