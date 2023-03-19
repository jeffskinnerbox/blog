<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----


WatchYourLAN is a lightweight, continuiously operating network IP scanner with web GUI.
It is packaged as a Docker Container and can be found on DockerHub as [aceberg/watchyourlan][03].

Currently `docker0` is not allowed, as arp-scan wouldn't work with it correctly

#### Step X: Idenify Your LAN & WiFi Interfaces to Scan
To get the network interfaces you need to scan to assemble your data,
usein teh following script:

```bash
# list your network interfaces
sudo ip link show
```

#### Step X: Docker Compose File for Portainer

```yaml
version: "3"
services:
  watchyourlan:
    container_name: watchyourlan
    image: aceberg/watchyourlan
    network_mode: "host"                # needs access to host network to do network scan
    restart: unless-stopped
    volumes:
      - ~/.docker/wyl:/data             # where sqlite data will be stored
    environment:
      TZ: America/New_York              # required: needs your TZ for correct time
      IFACE: "eno1 eth1 wlx94dbc95110ca" # required: interface to scan, could be one or more, separated by space
      DBPATH: "/data/db.sqlite"         # optional, path to database, default: /data/db.sqlite
      GUIIP: "0.0.0.0"                  # optional, default: ip address fore web gui, default: localhost
      GUIPORT: "8840"                   # optional, port for we gui default: 8840
      TIMEOUT: "120"                    # optional, time, in seconds, between scans, default: 60
      SHOUTRRR_URL: ""                  # optional, url for notification service: Shoutrrr (pushover, email, telegram and others)
      THEME: "darkly"                   # optional, any theme name from https://bootswatch.com in lowcase
      IGNOREIP: "no"                    # optional, if you want to detect unknown hosts by MAC only, set this to "yes"
```

* [This is How You WatchYourLan](https://www.youtube.com/watch?v=DknqJrnlLQo)
* [Pi.Alert or WatchYourLAN can alert you to unknown devices appearing on your WiFi or LAN network](https://www.youtube.com/watch?v=v6an9QG2xF0)


#### Step X: Test GUI
WatchYourLAN will serve its Web GUI at `http://localhost:8840` (aka `http://desktop:8840` in my case).




[01]:
[02]:
[03]:https://hub.docker.com/r/aceberg/watchyourlan
[04]:
[05]:
[06]:
[07]:
[08]:
[09]:
[10]:
