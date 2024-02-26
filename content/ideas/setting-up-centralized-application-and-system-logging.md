<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


------


# Centralized Logging
There are many merits for centralized logging;

* you want to know when an unknown computer (hacker?) has connected to your network.
* You need to know when hardware or software on any computer on your network is fails.
* You should be notified of repeated login failures.
* Centralized logging and analysis can tell you all of that and potential more.
* Create security dashboards to monitor key metrics
* It’s also good for maintenance and troubleshooting.
You can receive alerts when certain events occur or search through log history to try and pinpoint issues.

* [Remote logging for easier Raspberry Pi debugging](https://www.dzombak.com/blog/2023/12/Remote-logging-for-easier-Raspberry-Pi-debugging.html)
* [Centralizing Docker Logging Using Logspout and Graylog](https://hometechhacker.com/centralizing-docker-logging-using-logspout-and-graylog/)
* [How to Create a Graylog Container in Docker](https://hometechhacker.com/how-to-create-a-graylog-container-in-docker/)
* [5 Ways Centralized Logging Improves Home Network Security](https://hometechhacker.com/centralized-logging-improves-home-network-security/)

* [Meet Grafana LOKI, a Log Aggregation System for EVERYTHING](https://www.youtube.com/watch?v=h_GGd7HfKQ8)
* [Grafana Loki: Like Prometheus, But for logs. - Tom Wilkie, Grafana Labs](https://www.youtube.com/watch?v=CQiawXlgabQ)

# Logspout
Logspout is a Docker container that routes logs for Docker containers using the Docker API instead of a driver. It attaches to all containers running on the host and routes their logs as configured. Logspout can route logs from different containers to different locations. It can also route logs from the same container to multiple locations.

With such rich, built in logging capabilities why would you use Logspout instead of a logging driver? Well, there are a few reasons:

If you like routing to syslog as I do, you won’t be able to use the docker logs command because it isn’t compatible with the syslog driver.
Logspout allows you to manage all your Docker logging outside of each container, which is more in line with the microservices approach.
Many of the logging drivers have dependencies on the host system. Logspout eliminates these dependencies. This makes moving containers to different hosts easier.
Docker doesn’t support multiple logging drivers at the same time. With Logspout you can send logs to multiple locations.
