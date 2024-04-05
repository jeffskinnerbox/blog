<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----



* [Use a Raspberry PI Zero W as a Wireless Print Server](https://community.element14.com/products/raspberry-pi/raspberrypi_projects/b/blog/posts/use-a-raspberry-pi-zero-w-as-a-wireless-print-server)
* [CUPS and Raspberry Pi AirPrinting](https://www.developer.com/mobile/cups-and-raspberry-pi-airprinting/)
* [How to Turn a Printer into a Wireless Printer with Raspberry Pi](https://www.youtube.com/watch?v=hdwqQjDjMzU)
* [Create your own Canon Printer server with Raspberry Pi](https://www.youtube.com/watch?v=3powPeY5_-k)
* [Turn your USB Printer into a Wireless Printer! 2019](https://www.youtube.com/watch?v=4g9vnk28480)
* [Turn USB Printer to WiFi Printer for $15 | Convert Any USB Printer Wireless](https://www.youtube.com/watch?v=P3XRi-CD1a0)




1. Update & Install CUPS
sudo apt install -y build-essential git autoconf libtool cups libcups2-dev libcupsimage2-dev

2. Install Drivers
git clone https://github.com/agalakhov/captdriver.git
cd captdriver
autoreconf -i
./configure
make

sudo cp src/rastertocapt /usr/lib/cups/filter/
sudo cp Canon*.ppd /usr/share/ppd/custom/

3. CUPS remote access
sudo cupsctl --remote-any
sudo usermod -a -G lpadmin <your-username>

