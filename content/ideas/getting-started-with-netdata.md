<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


-----



Netdata - `localhost:19999`


* [Proxmox + NetData for Better Insights and Notifications](https://dbtechreviews.com/2023/12/06/proxmox-real-time-monitoring-ne/)


# Real-Time Performance Monitoring with Netdata
[Netdata][01] is a distributed, real-time, performance and health monitoring for systems and applications.
It is a monitoring agent you install on all your systems and containers,
telling you what is happening on the systems using interactive web dashboards.
Netdata data collection is extensible so you can monitor anything you can get a metric for using its Plugins.


* [Provisioning real-time performance monitoring with Netdata](https://appfleet.com/blog/provisioning-real-time-performance-monitoring-with-netdata-on-gcp/)

## Install Netdata
By default, [Netdata collects anonymous usage information][02]
from a monitoring agent and sends it to a Netdata analytics platform [PostHog][03].
You can [opt-out of this][04] by creating a file by running
`touch .opt-out-from-anonymous-statistics` within your Netdata configuration directory
or when using Docker, set your `DO_NOT_TRACK` environment variable to `1`.

https://learn.netdata.cloud/docs/agent/packaging/docker

```bash
# install the docker container for netdata
sudo docker run -d --name=netdata \
  -p 19999:19999 \
  -v netdataconfig:/etc/netdata \
  -v netdatalib:/var/lib/netdata \
  -v netdatacache:/var/cache/netdata \
  -v /etc/passwd:/host/etc/passwd:ro \
  -v /etc/group:/host/etc/group:ro \
  -v /proc:/host/proc:ro \
  -v /sys:/host/sys:ro \
  -v /etc/os-release:/host/etc/os-release:ro \
  --restart unless-stopped \
  --cap-add SYS_PTRACE \
  --security-opt apparmor=unconfined \
  netdata/netdata:latest
```

The `docker-compose` equivalent is

```yaml
version: '3'
services:
  netdata:
    container_name: netdata
    image: netdata/netdata:latest
    hostname: desktop.jeffskinnerbox.me    # set to fqdn of host
    ports:
      - 19999:19999
    restart: unless-stopped
    cap_add:
      - SYS_PTRACE
    security_opt:
      - apparmor:unconfined
    volumes:
      - /home/jeff/tmp/docker-volumes/netdata/netdataconfig:/etc/netdata
      - /home/jeff/tmp/docker-volumes/netdata/netdatalib:/var/lib/netdata
      - /home/jeff/tmp/docker-volumes/netdata/netdatacache:/var/cache/netdata
      - /etc/passwd:/host/etc/passwd:ro
      - /etc/group:/host/etc/group:ro
      - /proc:/host/proc:ro
      - /sys:/host/sys:ro
```

>**NOTE:** An FQDN is a complete address for a website, computer, server or similar entity that exists on the internet. An FQDN consists of three labels, including the hostname, second-level domain name and top-level domain name (TLD), each separated by a period, ending with a trailing period.
>For example, an FQDN for a hypothetical mail server might be mymail.somecollege.edu . The hostname is mymail, and the host is located within the domain somecollege.edu.
>[Fully Qualified Domain Name (FQDN) explained](https://www.ionos.com/digitalguide/domains/domain-administration/fqdn-fully-qualified-domain-name/)

Next, let check on the status of Netdata which as a UI on port 19999
(See [here][05] to understand how the dashboard works):

```bash
# go to the netdata user interface
google-chrome http://localhost:19999
```

# Netdata Cloud / Streaming and Replication
* [Guides](https://learn.netdata.cloud/guides/)
* [The step-by-step Netdata guide](https://learn.netdata.cloud/guides/step-by-step/step-00)
* https://www.netdata.cloud/cloud/
* https://learn.netdata.cloud/docs/agent/streaming
* https://learn.netdata.cloud/docs/dashboard/how-dashboard-works

* [Learn Netdata](https://learn.netdata.cloud)
    * [Get started with Netdata](https://learn.netdata.cloud/docs/get-started)
    * [Overview](https://learn.netdata.cloud/docs/visualize/overview-infrastructure)
    * [Spaces](https://learn.netdata.cloud/docs/cloud/spaces)
    * [Build new dashboards](https://learn.netdata.cloud/docs/cloud/visualize/dashboards)
    * [Alert notifications](https://learn.netdata.cloud/docs/cloud/alerts-notifications/notifications)
    * [Kubernetes visualizations](https://learn.netdata.cloud/docs/cloud/visualize/kubernetes)






[01]:https://appfleet.com/blog/provisioning-real-time-performance-monitoring-with-netdata-on-gcp/
[02]:https://learn.netdata.cloud/docs/agent/anonymous-statistics
[03]:https://posthog.com/
[04]:https://learn.netdata.cloud/docs/agent/anonymous-statistics#opt-out
[05]:https://learn.netdata.cloud/docs/dashboard/how-dashboard-works
[06]:
[07]:
[08]:
[09]:
[10]:
