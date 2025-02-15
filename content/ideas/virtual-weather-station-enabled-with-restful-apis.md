<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------




* [Build your own Raspberry Pi weather station with weather forecast and ESP32 wireless sensors](https://www.haraldkreuzer.net/en/news/build-your-own-raspberry-pi-weather-station-weather-forecast-and-esp32-wireless-sensors)
* [Forget Dark Sky — Build Your Own DIY Weather App](https://onezero.medium.com/forget-dark-sky-build-your-own-diy-weather-app-126809c2091c)
* [Long Range weather station](https://hackaday.io/project/191652-long-range-weather-station)

I have been considered purchasing or building my own home weather station for my backyard.
I would make it part of my larger plan to instrument my home for automation and monitoring.
A sophisticated weather stations could be bristling with devices like:

* **Anemometer** is a device for measuring wind speed.
* **Wind Vane** is a device that measures the direction of the wind.
* **Thermometer** is a device that measures temperature.
* **Hygrometer** is a device that measures relative humidity.
* **Barometer** is an instrument used to measure atmospheric pressure.
* **Rain Gauge** is a device that measures liquid precipitation (rain), as opposed to solid precipitation (snow gauge) over a set period of time.
* **Solar Radiation sensor** measures solar energy from the sun.
* **Ultraviolet sensor** (UV sensor) is a device that measures UV light from the Sun.
* **Leaf Wetness sensor** detects the presence of surface moisture and is measured between 0 (dry) and 15 (saturated).
* **Soil Moisture sensor** measures the quantity of water contained in a material, such as soil on a volumetric or gravimetric basis.
* **Soil Temperature sensor** measures the temperature of the soil

So potential there are many expensive sensors,
then of course their is the user interface,
the installation, and continuing maintenance of the station.

I then thought about it, and frankly, I'm not prepared to make this commitment.
I would like the data, but the cost and labor I would like to avoid.
My solution to this will be a vertual weather station.
No hardware mounted to my house,
just a Raspberry Pi, or other such device, making use of published API to get my local weather.
The vertual weather station will
itself be API emabled so that you can quere for realtime status, hsitoral data,
and support mutiple thypes of user interfaces
(e.g. web page, mobile app, or even a repurposed old Kindle).



---------------


# Hyper-Local Weather Forcasting
[ClimaCell](https://www.climacell.co/)
provides minute-by-minute, street-by-street-level forecasts.
HyperCast is based on the company's Weather Operating System (Weather OS),
which combines "Weather-of-Things" data,
including cell tower signals, and data from connected cars, airplanes, drones and IoT devices,
with AI-driven models that analyze the data at resolutions of hundreds of meters and minutes.

* [You Don’t Need A Weatherman To Know Which Way The Drone Blows](https://hackaday.com/2020/09/07/you-dont-need-a-weatherman-to-know-which-way-the-drone-blows/)
* [ClimaCell API](https://developer.climacell.co/)


# Collecting Weather Data

* [Where Do Weather Apps Get Their Info From?](https://www.howtogeek.com/880368/where-do-weather-apps-get-their-info-from/)
* [WeatherCollector](https://github.com/CorentinJ/WeatherCollector) - A python script to collect daily weather data from anywhere in the world within any time range


# Sage
In September of 2019, the National Science Foundation awarded a multi-institutional team,
led by Northwestern University, a $9 million grant to launch the [Sage project](https://sagecontinuum.org/),
a novel cyberinfrastructure created to exploit dramatic improvements in artificial intelligence technology.
The goal: to build a continent-spanning network of smart sensors.


# Calling Home via Satellite

* [PR-Holonet: Disaster Area Emergency Comms](https://hackaday.io/project/140426-pr-holonet-disaster-area-emergency-comms)
* [RockBLOCK Mk2 - Iridium SatComm Module](https://www.sparkfun.com/products/13745)
* [Satellite communication with RockBLOCK](http://www.makersnake.com/rockblock/)


# Weather Alerts Software / APIS
There’s no shortage of ways to receive weather information.
We all have our favorite weather app or forecasting site,
and there are emergency alerts to cell phones, TV, and radio stations as well.
If none of that suits you, though, you can also [roll out your own weather alert readerboard](https://github.com/damageddolphin/readerboard).


Some simple weather station setups:
Nice Design

* [DIY 3D Printed IoT Weather Station Using an ESP32](https://www.the-diy-life.com/diy-3d-printed-iot-weather-station-using-an-esp32/)
*
* [Nothing Should Cloud The Build Of This Wieldy Weather Widget](https://hackaday.com/2021/08/23/nothing-should-cloud-the-build-of-this-wieldy-weather-widget/)
* [NRF52 Weather Station Gives Forecast With Style](https://hackaday.com/2021/03/11/nrf52-weather-station-gives-forecast-with-style/)
* [Building ESP8266 Weather station with BME280 (part I)](http://itohi.com/blog/building-esp8266-weather-station-part-i/)
* [Building ESP8266 Weather station with BME280 (part II)](http://itohi.com/blog/building-esp8266-weather-station-part-ii/)
* [ESP8266 Colored Weather Station](https://www.instructables.com/id/ESP8266-Colored-Weather-Station/)
* [Stylish desktop ESP8266 weather station](https://hackaday.io/project/174508-stylish-desktop-esp8266-weather-station)
* [Weather Station with ePaper and Raspberry Pi](Weather Station with ePaper and Raspberry Pi)
* [Weather Pyramid](https://hackaday.io/project/153208-weather-pyramid)
* [ESP8266 Weather Station - with Wind and Rain Sensors](https://tysonpower.de/blog/esp8266-weather-station)
* [Capacitive Rainmeter Measures The Sky Water Just Fine](https://hackaday.com/2023/11/28/capacitive-rainmeter-measures-the-sky-water-just-fine/)
* [Weather Station Is A Tutorial in Low Power Design](https://hackaday.com/2018/11/04/weather-station-is-a-tutorial-in-low-power-design/)
* [The Cult Of Really Low-Power Circuits: Scrounging, Sipping, And Seeing Power](https://hackaday.com/2020/02/03/the-cult-of-really-low-power-circuits-scrounging-sipping-and-seeing-power/)
* [Solar Powered WiFi Weather Station V1.0: 19 Steps](https://www.instructables.com/id/Solar-Powered-WiFi-Weather-Station/)
* [Solar Powered WiFi Weather Station V2.0](https://www.instructables.com/id/Solar-Powered-WiFi-Weather-Station-V20/)
* [SolarMAX - A Solar Power System for your Maker project!](https://www.kickstarter.com/projects/sunair/solarmax-a-solar-power-system-for-your-maker-project)
* [Solar powered Bluetooth Thermometer with Supercap](https://hackaday.io/project/177910-solar-powered-bluetooth-thermometer-with-supercap)
* [Checking The Weather Without A Window](https://hackaday.com/2018/04/27/checking-the-weather-without-a-window/)
* [ESP32 Weather Station on a PCB](https://hackaday.com/2018/02/10/esp32-weather-station-on-a-pcb/)
* [ESP8266 WiFi Weather Station with Color TFT Display](https://learn.adafruit.com/wifi-weather-station-with-tft-display)
* [Sparklines For Your ESP32 Projects](https://hackaday.com/2020/06/06/sparklines-for-your-esp32-projects/)
* [ESP32 Weathercloud Weather Station](https://www.instructables.com/id/ESP32-Weathercloud-Weather-Station/?linkId=71473200)
* [IoT Made Simple: Home Weather Station With NodeMCU and OLED](https://www.hackster.io/mjrobot/iot-made-simple-home-weather-station-with-nodemcu-and-oled-27d3a9)
* [Desktop Weather Monitor Leaves Nothing to Chance](https://hackaday.com/2019/05/19/desktop-weather-monitor-leaves-nothing-to-chance/)
* [Analog VU Meter - I2C OLED SH1106 - OLEDMeter Animation](https://forum.arduino.cc/index.php)
* [Improving OLED VU Meters With A Little Physics](https://hackaday.com/2021/08/09/improving-oled-vu-meters-with-a-little-physics/)
* [Round LCDs Put To Work In Rack Mount Gauge Cluster](https://hackaday.com/2022/05/13/round-lcds-put-to-work-in-rack-mount-gauge-cluster/)
* [Laser Draws Weather Report](https://hackaday.com/2018/06/23/laser-draws-weather-report/)

* [The Solid State Weather Station](https://hackaday.com/2018/05/17/the-solid-state-weather-station/)
* [Weather Station – DHT11, MQTT, Node-RED, Google Chart, Oh My!](http://www.internetoflego.com/weather-station-dht11-mqtt-node-red-google-chart-oh-my/)
* [node-red-node-weather-underground](https://www.npmjs.com/package/node-red-node-weather-underground)
* [Hyper-local Weather Dashboard: Wunderground + Pi Sense HAT](https://github.com/InitialState/wunderground-sensehat/wiki)
* [How to Monitor Room Temperature With a Raspberry Pi](https://www.jeremymorgan.com/tutorials/raspberry-pi/monitor-room-temperature-raspberry-pi/)
* [Make a Weather Station With a Raspberry Pi 2](<https://www.jeremymorgan.com/tutorials/raspberry-pi/how-to-weather-station-raspberry-pi/?utm_source=feedburner&utm_medium=email&utm_campaign=Feed:+JeremyMorganTutorials+(Jeremy)>
* [Mini weather station with Attiny85](http://www.instructables.com/id/Mini-weather-station-with-Attiny85/)
* [Home environment monitor](https://www.hackster.io/breakpointer/home-environment-monitor-e1173e?ref=newsletter&utm_source=Hackster.io+newsletter&utm_campaign=ea4231d547-2015_4_17_Top_projects4_16_2015&utm_medium=email&utm_term=0_6ff81e3e5b-ea4231d547-140225889)
* [ESP8266 weather station](http://dangerousprototypes.com/2015/11/30/esp8266-weather-station/)
* [ESP8266 weather station](http://dangerousprototypes.com/2015/11/30/esp8266-weather-station/)
* [NodeMCU Weather Widget](https://www.youtube.com/watch?v=NnS7sFmU-c4)
* Weather station - [Using the 4 pins of the ESP8266-01](https://arduinodiy.wordpress.com/2016/10/11/using-the-4-pins-of-the-esp8266-01/)
* [PiClock: an all in one clock, weather forecast and radar map](https://blog.adafruit.com/2015/06/12/piclock-an-all-in-one-clock-weather-forecast-and-radar-map-piday-raspberrypi-raspberry_pi/)
* [11 Best Weather Stations](http://www.instructables.com/id/11-Best-Weather-Stations/)

* [Weather Font](http://www.dafont.com/weather.font)

* [Improve battery life in Ultra Low Power wireless applications](https://blog.nordicsemi.com/getconnected/improve-battery-life-in-ultra-low-power-wireless-applications)
* [Battery Life Calculator for Projects with Sleep Mode](https://www.geekstips.com/battery-life-calculator-sleep-mode/)


# Measuring LiPo Charge Level
Battery-powered projects require you to monitor your battery's life.
Measuring battery voltage is not ideal, because the voltage doesn't drop linearly.
Battery charge level, aka fuel gauges, are a better alternative.
They work straight away, don't consume power while in standby,
and they're accurate without any calibration!

* [Correctly Measure Battery Level - MAX17048 (ESP32 + Arduino series)](https://www.youtube.com/watch?v=mhmD-QA6kf0)
* [Adafruit MAX17048 LiPoly / LiIon Fuel Gauge and Battery Monitor](https://learn.adafruit.com/adafruit-max17048-lipoly-liion-fuel-gauge-and-battery-monitor)


# Weather APIs

* [RapidAPI](https://docs.rapidapi.com/docs/what-is-rapidapi)
* [Top 6 Best Free Weather APIs to Access Global Weather Data (Updated for 2020)](https://rapidapi.com/blog/access-global-weather-data-with-these-weather-apis/)

* [WeatherCloud](https://weathercloud.net/site/about)
* [National Weather Service](https://www.weather.gov/documentation/)
    * [National Weather Service Weather Alerts](https://alerts.weather.gov/)
    * [Weather Alert Light System](https://www.instructables.com/id/Weather-Alert-Light-System/)
* [OpenWeatherMap](http://openweathermap.org/)
    * [Real-Time Weather with Raspberry Pi 4](https://www.hackster.io/gatoninja236/real-time-weather-with-raspberry-pi-4-ad621f)
    * [Fetching real-time weather data and controlling the speed of a motor fan with Raspberry Pi on Raspbe](https://community.dfrobot.com/makelog-308300.html)
* [MetaWeather](https://www.metaweather.com/)
* [Dark Sky API](https://darksky.net/dev/)
    * [Dark Sky API PyPortal and Weather Dashboard](https://www.hackster.io/elizabethna/dark-sky-api-pyportal-and-weather-dashboard-9383ee)
* [Foreca](https://corporate.foreca.com/en/weather-data/weather-api)
* [cli-weather](https://www.npmjs.com/package/cli-weather)
* [Migrating a Project from Weather Underground to Open Weather Maps](https://www.sparkfun.com/news/2858)

* [Build a Wireless “Tipping Bucket” Rain Gauge, Part 1—Assembling the Bucket](http://www.allaboutcircuits.com/projects/build-a-wireless-tipping-bucket-rain-gauge-part-1assembling-the-base/)

* [climatic simulation](https://hackaday.com/2019/08/02/simulate-climate-with-an-arduino/)

Gulp - <http://gulpjs.com/>
Mocha - <http://mochajs.org/>
Chai - <http://chaijs.com/>
Sinon - <http://sinonjs.org/>
Angular - <https://angularjs.org/#>!
Node API - <http://coenraets.org/blog/2012/10/creating-a-rest-api-using-node-js-express-and-mongodb/>
<https://scotch.io/tutorials/build-a-restful-api-using-node-and-express-4>
<https://scotch.io/tutorials/setting-up-a-mean-stack-single-page-application>,
Authenticate a Node API with Tokens - <https://scotch.io/tutorials/authenticate-a-node-js-api-with-json-web-tokens>
Sample Application with Backbone.js, Twitter Bootstrap, Node.js, Express, and MongoDB - <http://coenraets.org/blog/2012/10/nodecellar-sample-application-with-backbone-js-twitter-bootstrap-node-js-express-and-mongodb/>
[PiClock – Time and Weather Information Overload](http://hackaday.com/2015/06/10/piclock-time-and-weather-information-overload/)
[Weather Underground APIs](http://www.wunderground.com/weather/api)
[National Digital Forecast Database (NDFD) Simple Object Access Protocol (SOAP) Web Service](http://graphical.weather.gov/xml/)

[Mockable.io](https://www.mockable.io/#)
is a simple configurable service to mock out RESTful API or SOAP web-services.
This online service allows you to quickly define REST API or SOAP endpoints and have them return JSON or XML data.


# Weather Ballons

* [Chasing Weather Balloons With Software-Defined Radio How to hunt for downed radiosonde beacons with a cheap SDR receiver](https://spectrum.ieee.org/chasing-weather-balloons-with-sdr)
* [TRACKING RADIOSONDES WITH AN RTL-SDR AND RADIOSONDE_AUTO_RX](https://www.rtl-sdr.com/tracking-radiosondes-with-an-rtl-sdr-and-radiosonde_auto_rx/)
* [RadioSonde Auto RX: How To Install Radiosonde_Auto_RX from a Prebuilt Image](https://rrc.org.au/2021/08/15/auto_rx-prebuilt-image/)
* [STM32 Development Boards (literally) Falling From The Sky](https://www.youtube.com/watch?v=YBy-bXEWZeM&t=1s)
    * [Global Wind Speed](https://earth.nullschool.net/)
    * [sondehub](https://sondehub.org/)
    * [tracker sondehub](https://sondehub.org/)
    * [RS41 RADIOSONDE TRACKING SOFTWARE](https://www.rtl-sdr.com/rs41-radiosonde-tracking-software/)


# PLA Waterproofing

* [Truck Bed Liners Improve 3D Prints](https://hackaday.com/2021/02/14/truck-bed-liners-improve-3d-prints/)


# Solar Powered Weather Station

* [Solar Powered Weather Station](https://hackaday.io/project/19324-weather-station)
* [Stack Of Plant Saucers, Transformed Into Low Cost Solar Shield](https://hackaday.com/2019/09/01/stack-of-plant-saucers-transformed-into-low-cost-solar-shield/)
* [A lightweight, self contained, solar-powered weather station for the Raspberry Pi](https://github.com/masneyb/weather-station)
* [Solar-powered Weather Station Has the Complete Suite of Sensors](http://hackaday.com/2016/08/17/solar-powered-weather-station-has-the-complete-suite-of-sensors/)
* [Wireless Weather Station Gets Solar-Powered Supercap Upgrade](https://hackaday.com/2022/04/07/wireless-weather-station-gets-solar-powered-supercap-upgrade/)


# Solar Powered: Pro & Con

* [Is Solar Right For You? Find Out!](https://hackaday.com/2019/09/07/is-solar-right-for-you-find-out/)
* [The Dark Side Of Solar Power](https://hackaday.com/2020/12/02/the-dark-side-of-solar-power/#more-429117)


# Space Weather
Space Weather is the term scientists use to describe the ever changing conditions in space. Explosions on the Sun create storms of radiation, fluctuating magnetic fields, and swarms of energetic particles. These phenomena travel outward through the Solar System with the solar wind. Upon arrival at Earth, they interact in complex ways with Earth's magnetic field, creating Earth's radiation belts and the Aurora. Some space weather storms can damage satellites, disable electric power grids, and disrupt cell phone communications systems.

* [NASA APIs](https://api.nasa.gov/index.html)
* [SPACE WEATHER PREDICTION CENTER](https://www.swpc.noaa.gov/communities/space-weather-enthusiasts)
* [Welcome To Solar Cycle 25; Our Sun Enters A New 11-Year Period](https://hackaday.com/2020/10/06/welcome-to-solar-cycle-25-our-sun-enters-a-new-11-year-period/)
* [Solar Flares And Radio Communications — How Precarious Are Our Electronics?](https://hackaday.com/2020/12/30/solar-flares-and-radio-communications-how-precarious-are-our-electronics/)
* [Solar Flare Quiets A Quarter Of The Globe](https://hackaday.com/2022/09/18/solar-flare-quiets-a-quarter-of-the-globe/)


# Creating APIs

* [How to set-up a powerful API with Nodejs, GraphQL, MongoDB, Hapi, and Swagger](https://medium.freecodecamp.org/how-to-setup-a-powerful-api-with-nodejs-graphql-mongodb-hapi-and-swagger-e251ac189649)


# High Level Design
Within the Raspberry Pi, I will create an RESTful API service
using [Node.js][01],
also using [Express][02] web framework and its [Router][03],
[Mongoose][04] to interact with a [MongoDB][05] [NoSQL database][08],
and [body-parser][09] will let us pull POST content from our HTTP request.
We will also be testing our API using [Postman][06] in Chrome.

* Handle all the functions of create, read, update and delete (CRUD)
* Have a standard URL to access the weather data (`http://home.rpi/weather/api`)
* Use the proper HTTP verbs to make it RESTful (GET, POST, PUT, and DELETE)
* Return [JSON data][07]
* Log all requests to the console

For our file structure, we'll use the following
(I used `tree /home/jeff/src/vws`):

```
vws
├── node_modules        // created by npm, holds our dependencies/packages
└── weather_station     // weather station model



- app/
    ----- models/
    ---------- bear.js  // our bear model
    - node_modules/     // created by npm. holds our dependencies/packages
    - package.json      // define all our node app and dependencies
    - server.js         // configure our application and create routes
```


# Install Your Tools
I created the folder `/home/jeff/src/vws`.
Within this folder,
as with all of our Node projects,
I define the packages needed in `package.json`:

```jason
{
    "name": "vertual weather station",
    "description": "Simulates a home weather station by using data harvested from the web.",
    "version": "0.0.1",
    "private": true,
    "dependencies": {
        "express": "3.x"
    }
}
```

I then ran Node.js to create my development environment:

```bash
# Node package manager will create your development environment
npm install
```

A`node_modules` folder is created in the vws folder,
and the Express and other modules are installed in a subfolder of `node_modules`.

Open `server.js` and replace its content as follows:

```js
```


# Outdoors Electronics

* [How to assemble an outdoors electronics project](https://www.youtube.com/watch?v=IObVtX9ZrJo)


# Hardware Design

* [Build your own elegant e-paper weather display powered by an ESP32 microcontroller](https://www.xda-developers.com/build-elegant-e-paper-weather-display-esp32-microcontroller/)
* [ESP8266 weather station with e-paper display](http://embedded-lab.com/blog/esp8266-weather-station-e-paper-display/)
* [7.5inch Passive NFC-Powered e-Paper without Battery](https://www.seeedstudio.com/7-5inch-Passive-NFC-Powered-e-Paper-without-Battery-p-4494.html)
* [ESP8266 Weather display](https://github.com/andrei7c4/weatherdisplay)
* [Run a Linux Terminal on Cheap E-Ink Displays](https://hackaday.com/2018/08/14/run-a-linux-terminal-on-cheap-e-ink-displays/)
* [How to Make Pocket Sized IoT Weather Station](https://www.instructables.com/id/How-to-Make-Pocket-Sized-IoT-Weather-Station/?linkId=71510722)

As an alternative to buying general purpose e-paper solution, repurposing a Kindle.
Kindle 4 (eInk) or Kindle PaperWhite seems like the best pick for features vs price.

* [Kindle Gets Downgraded to an Expensive Thermostat](http://hackaday.com/2014/05/29/kindle-paperwhite-gets-downgraded-to-an-expensive-thermostat/)
* [Kindle weather and recycling display](http://hackaday.com/2013/04/01/kindle-weather-and-recycling-display/)
* [Turning a Kindle into a weather display](http://hackaday.com/2012/09/17/turning-a-kindle-into-a-weather-display/)
    * [Kindle hack adds value to the wallpaper](http://hackaday.com/2013/08/28/kindle-hack-ads-value-to-the-wallpaper/)
* [How to Jailbreak Your Kindle Paperwhite for Screensavers, Apps, and More](http://www.howtogeek.com/168844/how-to-jail-break-your-kindle-paperwhite-for-screensavers-apps-and-more/)
* [Raspberry Pi and Kindle Together Again](http://hackaday.com/2015/04/30/raspberry-pi-and-kindle-together-again/)
* [KindleBerry Pi](http://www.ponnuki.net/2012/09/kindleberry-pi/)
* [A Jailbreak For Every Kindle](http://hackaday.com/2016/07/09/a-jailbreak-for-every-kindle/)


# Air Particulate Pollution

* [Measuring Particulate Pollution With The ESP32](https://hackaday.com/2019/08/29/measuring-particulate-pollution-with-the-esp32/)
* [Measuring Air Quality Using Mobile Sensors for the Masses](https://hackaday.com/2021/12/13/measuring-air-quality-using-mobile-sensors-for-the-masses/)


# Fire Tracker

* [Fire Information for Resource Management System US/Canada](https://firms.modaps.eosdis.nasa.gov/usfs/)


# Lightning Storm Alerts

* [LIGHTNING ALERTS and DASHBOARDS using Weather Integrations in Home Assistant](https://www.youtube.com/watch?v=dvNkmBxKPEk)


# Lightning Storm Detector

* [Lightning Basics](https://www.nssl.noaa.gov/education/svrwx101/lightning/)
* [The Electrifying Debate Around Where Lightning Comes From](https://hackaday.com/2022/02/17/the-electrifying-debate-around-where-lightning-comes-from/)

* [An Introduction to Storm Detector Modules](https://hackaday.com/2018/03/22/an-introduction-to-storm-detector-modules/)
    * [Storm Detector Modules: Dancing in the Rain](https://hackaday.com/2018/03/28/storm-detector-modules-dancing-in-the-rain/)
* [Playing With Fusion, Inc](https://github.com/PlayingWithFusion)
* [Lightning Analysis With Your SDR](https://hackaday.com/2020/08/07/lightning-analysis-with-your-sdr/)


## Lightning "Emulator"

* [Lightning "Emulator" Shield](https://www.playingwithfusion.com/productview.php?pdid=55)


## "Triditional" Detector

* [This Lightning Detector Is Remarkably Sensitive](https://hackaday.com/2019/10/03/this-lightning-detector-is-remarkably-sensitive/)


## Specialized IC Detector

* [Raspberry Pi Lightning Detector](https://www.hackster.io/news/raspberry-pi-lightning-detector-f85780ffce0d)
* [AMS AS3935 Franklin Lightning Sensor](https://esphome.io/components/sensor/as3935.html)
* [SparkFun Lightning Detector - AS3935](https://www.sparkfun.com/products/15276)
* [Lightning Sensor Breakout](https://www.playingwithfusion.com/productview.php?pdid=22&catid=1012)
* Linux script to monitor AS3935 lightning detector and report detections to MQTT: [lightning-detector-MQTT2HA-Daemon](https://github.com/ironsheep/lightning-detector-MQTT2HA-Daemon)
* [AS3935 Franklin Lightning sensor](https://tasmota.github.io/docs/AS3935/)


## AM Receiver Detector

* [Detect Lightning Strikes With An Arduino](https://hackaday.com/2021/09/01/detect-lightning-strikes-with-an-arduino/)


## SDR Radio Detector

* [Lightning Analysis With Your SDR](https://hackaday.com/2020/08/07/lightning-analysis-with-your-sdr/)
* [ANALYZING LIGHTNING DISCHARGES WITH AN RTL-SDR AND THE SAGE NETWORK](https://www.rtl-sdr.com/analyzing-lightning-discharges-with-an-rtl-sdr-and-the-sage-network/)


## Weather Services

* [Lightning Maps](https://www.lightningmaps.org/?lang=en#m=oss;t=3;s=0;o=0;b=;ts=0;)
* [Blitzortung](https://www.blitzortung.org/en/live_lightning_maps.php)
* [GOES-East CONUS - Geostationary Lightning Mapper](https://www.star.nesdis.noaa.gov/GOES/conus_band.php?sat=G16&band=EXTENT&length=12)


# Anemometer

* [Open Source Ultrasonic Anemometer](https://hackaday.com/2021/07/06/open-source-ultrasonic-anemometer/)


# Dust Detection

* [Weather Warnings and Dust Detection from this Meteorological Marvel](https://hackaday.com/2020/09/14/weather-warnings-and-dust-detection-from-this-meteorological-marvel/)
* [The SDS011 sensor and fine dust](https://www.settorezero.com/wordpress/il-sensore-sds011-e-le-polveri-sottili/#Set_Working_Period)


# Bat Detector

* [What Does The Bat Say? Tune In With This Heterodyne Detector](https://hackaday.com/2020/06/27/what-does-the-bat-say-tune-in-with-this-heterodyne-detector/)
* [Hack Together Your Own Bat Signal](https://hackaday.com/2020/07/11/hack-together-your-own-bat-signal/)
* [Why MEMS Microphones Are the Best Choice for Your Project](https://www.hackster.io/news/why-mems-microphones-are-the-best-choice-for-your-project-fb4c3a61f33d)


# Open Source Seismometer

* [ASK HACKADAY: INCIDENTAL EARTHQUAKE DETECTION](https://hackaday.com/2023/02/09/ask-hackaday-incidental-earthquake-detection/)
* [A SIMPLE SEISMOMETER YOU CAN BUILD YOURSELF](https://hackaday.com/2024/03/16/a-simple-seismometer-you-can-build-yourself/)
* [Earthquake Detection On A Chip](https://hackaday.com/2019/07/06/earthquake-detection-on-a-chip/)
* [Earthquake Detector](https://avtanski.net/projects/seismic_sensor/)
* [Classroom seismometers could monitor earthquakes worldwide](http://physicsworld.com/cws/article/news/2014/jan/28/classroom-seismometers-could-monitor-earthquakes-worldwide)
* [TC1 Seismometers for Schools and Others on a Budget!](http://tc1seismometer.wordpress.com/)
* [Instructables Seismometer](http://www.instructables.com/id/Seismometer/?ALLSTEPS)
* [Build A Seismometer Out Of Plumbing Parts](https://hackaday.com/2019/01/22/build-a-seismometer-out-of-plumbing-parts/)
* [Detecting seismic waves with a piezo element](https://getpocket.com/a/read/122486014)
* [Listen to the Earth move!](https://www.youtube.com/watch?v=fcuX1FTfeaA)
* [Raspberry Pi-powered boom sensor: Detect earthquakes, H-bombs, SpaceX launches](http://www.zdnet.com/article/raspberry-pi-powered-boom-sensor-detect-earthquakes-h-bombs-spacex-launches/)
* [Watch Earthquake Roll Across A Continent In Seismograph Visualization Video](https://hackaday.com/2019/07/22/watch-earthquake-roll-across-a-continent-in-seismograph-visualization-video/)
* [Simple Seismic Sensor Makes Earthquake Detection Personal](https://hackaday.com/2019/10/28/simple-seismic-sensor-makes-earthquake-detection-personal/)
* [Earthquake sensor from OpenElectronicsStore on Tindie](https://www.tindie.com/products/openelectronics/earthquake-sensor/)
* [USB Mouse Hack For Pachyderm Protection](https://hackaday.com/2021/08/13/usb-mouse-hack-for-pachyderm-protection/)
* [An Earthquake Display To Keep You Abreast of Rumblings Worldwide](https://hackaday.com/2021/09/03/an-earthquake-display-to-keep-you-abreast-of-rumblings-worldwide/)
* [WATCH EARTHQUAKE ROLL ACROSS A CONTINENT IN SEISMOGRAPH VISUALIZATION VIDEO](https://hackaday.com/2019/07/22/watch-earthquake-roll-across-a-continent-in-seismograph-visualization-video/)
* [Raspberry Pi Plots World Wide Earthquakes](https://hackaday.com/2021/10/05/raspberry-pi-plots-world-wide-earthquakes/)

* [Raspberry Shake 4D (RS4D)](https://shop.raspberryshake.org/product/turnkey-iot-home-earth-monitor-rs-4d/)
* [RasberryShake 4D (RD29A) Chino Hills, Ca Live Stream Overview](https://www.youtube.com/watch?v=lV4CXGVGKaY)
* [Earthquake enthusiast? Raspberry Shake is your personal seismograph](http://www.digitaltrends.com/cool-tech/raspberry-shake-seismograph/)
* [Raspberry Shake Detects Quakes](https://hackaday.com/2018/08/25/raspberry-shake-detects-quakes/)
* [Raspberry Shake - The Personal Seismograph](http://www.engineering.com/DesignerEdge/DesignerEdgeArticles/ArticleID/12810/Raspberry-Shake--The-Personal-Seismograph.aspx)
* [Raspberry Shake - Home Earthquake Monitor (RS1D)](https://www.sparkfun.com/products/14835)
* [BUILD A SEISMOGRAPH WITH RASPBERRY SHAKE](https://www.blogdot.tv/build-a-seismograph-with-raspberry-shake/)
* [Raspberry Shake HAT brings earthquake monitoring to the Raspberry Pi SBC](https://www.cnx-software.com/2023/08/25/raspberry-shake-hat-brings-earthquake-monitoring-to-the-raspberry-pi-sbc/)
* [Tiny Box In Southern Wyoming Can Detect Earthquakes Around The World](https://cowboystatedaily.com/2024/12/15/tiny-box-in-southern-wyoming-can-detect-earthquakes-around-the-world/)
    * [Raspberry Shake StationView](https://stationview.raspberryshake.org/#/?lat=41.30631&lon=-105.65666&zoom=7.425&event=rs2024yggyxc&sta=R60D2)

* [Grove - D7S Vibration Sensor - Real-Time Earthquake Detect, I2C, Low Power Consumption](https://www.electromaker.io/shop/product/grove-d7s-vibration-sensor-real-time-earthquake-detect-i2c-low-power-consumption)


# Geophone vs Seismometers
Compared with geophones, seismometers are more suitable for extremely small ground motion detection, as they cover a larger frequency band, including the frequency range below their natural frequency, normally from 0.01 to 50 Hz. For conventional geophones, the frequency band falls into the range of 1–15 Hz.

* [DIY Geophone Build Performs Well](https://hackaday.com/2024/03/02/diy-geophone-build-performs-well/)
    * [DIY Extremly Sensitive and cheap Geophone sensor](https://hackaday.io/project/194956-diy-extremly-sensitive-and-cheap-geophone-sensor)


# Sensing The Earth’s Wobble

* [Sensing The Earth’s Wobble In Time](https://hackaday.com/2020/10/08/sensing-the-earths-wobble-in-time/)


# OpenEEW
earthquake early-warning systems OpenEEW

* [The Linux Foundation, Grillo and IBM Announce New Earthquake Early-Warning Open Source Project](https://www.linuxfoundation.org/press-release/2020/08/the-linux-foundation-grillo-and-ibm-announce-new-earthquake-early-warning-open-source-project/)


# Earthquake Notification
The United States Geological Survey provides a program called ShakeCast
that can send notifications within minutes of an earthquake.

* [ShakeCast](https://earthquake.usgs.gov/research/software/shakecast.php)
* [ShakeAlert Promises Earthquake Early Warning Of About 10 Seconds](https://hackaday.com/2021/06/04/shakealert-promises-earthquake-early-warning-of-about-10-seconds/)


# Geomagnetic Storms

* [Measuring a geomagnetic storm with a Raspberry Pi magnetometer](http://www.southgatearc.org/news/2019/january/measuring-a-geomagnetic-storm-with-a-raspberry-pi-magnetometer.htm#.XDle9svYrhN)


# Radiation Detection (Geiger-Muller Counter)

* [Gravity: Geiger Counter Module Ionizing Radiation Detector](https://www.dfrobot.com/product-2547.html)
* [DIY Scintillation Detector Is Mighty Sensitive](https://hackaday.com/2019/07/19/diy-scintillation-detector-is-mighty-sensitive/)
* [Working Geiger Counter W/ Minimal Parts](https://www.instructables.com/id/Working-Geiger-Counter-W-Minimal-Parts/)
* [DIY Geiger Counter Is Sure To Generate Clicks](https://hackaday.com/2019/08/19/diy-geiger-counter-is-sure-to-generate-clicks/)
* [You Didn’t See Graphite Around This Geiger Counter](https://hackaday.com/2019/09/08/you-didnt-see-graphite-around-this-geiger-counter/)
* [This Raspberry Pi Zero Geiger Counter Costs Under $100](https://www.tomshardware.com/news/raspberry-pi-zero-geiger-counter)
* [Detecting Alpha Particles Using Copper Wire And High Voltage](https://hackaday.com/2022/01/22/detecting-alpha-particles-using-copper-wire-and-high-voltage/)
* [Global Radiation Montoring And Tracking Nuclear Disasters At Home](https://hackaday.com/2019/08/28/global-radiation-montoring-and-tracking-nuclear-disasters-at-home/)
* [Warwalking For Radiation](https://hackaday.com/2019/09/10/warwalking-for-radiation/)
* [Ionizing Radiation Detector For Safer Foraging](https://blog.tindie.com/2021/06/ionizing-radiation-detector-for-safer-foraging/)
* [Flexible Radiation Monitoring System Speaks LoRa and WiFi](https://hackaday.com/2022/09/10/flexible-radiation-monitoring-system-speaks-lora-and-wifi/)
* [An Open Source Firmware For Cheap Geiger Counters](https://hackaday.com/2023/06/24/an-open-source-firmware-for-cheap-geiger-counters/)
* [Raspberry Pi Radiation Monitor Goes Wireless With Pico W](https://www.tomshardware.com/news/raspberry-pi-radiation-monitor-goes-wireless-with-pico-w)
* [Geiger Counter using SBM-20 and ESP8266](https://hackaday.io/project/194208-geiger-counter-using-sbm-20-and-esp8266)


# Spectrophotometer

* [Spot Adulterated Olive Oil With This Spectrophotometer](https://hackaday.com/2019/08/31/spot-adulterated-olive-oil-with-this-spectrophotometer/)
* [Arduino Rig Does Spectrophotometry](https://hackaday.com/2020/08/24/arduino-rig-does-spectrophotometry/)
* [High-Speed Spectrometer Built With Cheap Linear CCD](https://hackaday.com/2020/11/21/high-speed-spectrometer-built-with-cheap-linear-ccd/)
* [Pi-Based Spectrometer Puts The Complexity In The Software](https://hackaday.com/2021/04/23/pi-based-spectrometer-puts-the-complexity-in-the-software/)
* [Spectrometer Detects Chemicals By Zapping Samples With A Laser Beam](https://hackaday.com/2022/02/19/spectrometer-detects-chemicals-by-zapping-samples-with-a-laser-beam/)
* [Pi-based Spectrometer Gets An Upgrade](https://hackaday.com/2022/10/29/pi-based-spectrometer-gets-an-upgrade/)
* [Guillermo Perez Guillen's Raspberry Pi Spectrometer Puts the Power of Light at Your Fingertips](https://www.hackster.io/news/guillermo-perez-guillen-s-raspberry-pi-spectrometer-puts-the-power-of-light-at-your-fingertips-33cbbfd35373)
* [Gamma Ray Spectroscopy the Pomelo Way](https://hackaday.com/2024/06/05/gamma-ray-spectroscopy-the-pomelo-way/)


# Cosmic Ray Detector

* [Cosmic Pi - a low cost distributed cosmic ray detector, based on Raspberry Pi](https://ohwr.org/project/cosmic-pi/-/wikis/home)
    * [Cosmic Pi low cost cosmic ray detector project](https://github.com/CosmicPi)


# NOAA Weather Satellite Data

* [Raspberry Pi NOAA Satellite Receiver: A Comprehensive Guide](https://nnn.ng/faq/34215/)
* [Instructions for Building a Portable Double Cross Antenna: Great for NOAA/Meteor Weather Satellites](http://www.rtl-sdr.com/instructions-for-building-a-double-cross-antenna-great-for-noaameteor-weather-satellites/)
* [Receive Weather Satellite Images With Software-Defined Radio](http://mattg.co.uk/words/noaa_sdr/)
* [Downloading Satellite Images via FM Radio](http://hackaday.com/2015/08/02/downloading-satellite-images-via-fm-radio/)
* [NOAA Weather Satellite Reception with GNU Radio and USRP](http://www.oz9aec.net/index.php/gnu-radio-blog/350-noaa-weather-satellite-reception-with-gnu-radio-and-usrp)
* [Decoding NOAA Satellite Images In Python](https://hackaday.com/2021/01/27/decoding-noaa-satellite-images-in-python/)
* [Reading Weather Data with Software-Defined Radio](http://www.linux-magazine.com/Online/Features/Reading-Weather-Data-with-Software-Defined-Radio)
* [Downloading Satellite Images via FM Radio](http://hackaday.com/2015/08/02/downloading-satellite-images-via-fm-radio/)
* [GNUradio decoders for different satellites](https://github.com/daniestevez/gr-satellites)
* [L Band Satellite Antennas Revealed](https://hackaday.com/2019/08/04/l-band-satellite-antennas-revealed/)
* [Satellite Ground Station Upcycles Trash](https://hackaday.com/2021/04/03/satellite-ground-station-upcycles-trash/)


# Satellite Weather Images
With free software that can be downloaded on the Raspberry Pi, you can obtain pictures of Earth from satellites orbiting above. Along with images, you can also receive telemetry data and satellite statuses. The R2Cloud Project was created by a hobbyist and is maintained on GitHub.

* [How To Get Live Satellite Images Directly From Space](https://www.youtube.com/watch?v=icADyjm3PBE)
* [R2Cloud Project](https://github.com/dernasherbrezon/r2cloud)


# Weather Alerts

* [Weather Websites: IEMbot](https://www.edwardjensen.net/dispatches/weather-websites-iembot/6412/)


# Radiosonde
A [radiosonde][10] is a battery-powered telemetry instrument carried into the atmosphere usually by a weather balloon that measures various atmospheric parameters and transmits them by radio to a ground receiver.

* [Radiosonders: Getting Data from Upstairs](https://hackaday.com/2017/12/08/radiosondes/)
* [A Tracker For Radio Sondes](https://hackaday.com/2020/12/27/a-tracker-for-radio-sondes/)


# Allsky Meteor Surveillance
Use Raspberry Pi hardware to capture mesmerizing time-lapse images of the heavens

* [Create Your Own AllSky Camera (UPDATED!)](https://www.youtube.com/watch?v=7TGpGz5SeVI)
* [Roll Your Own All-Sky, Raspberry Pi Camera](https://spectrum.ieee.org/all-sky-camera)



[01]:https://nodejs.org/
[02]:http://expressjs.com/
[03]:http://expressjs.com/4x/api.html#router
[04]:http://mongoosejs.com/
[05]:https://www.mongodb.org/
[06]:https://www.getpostman.com/
[07]:http://json.org/
[08]:http://en.wikipedia.org/wiki/NoSQL
[09]:https://github.com/expressjs/body-parser
[10]:https://en.wikipedia.org/wiki/Radiosonde
[11]:
[12]:
[13]:
[14]:
[15]:
[16]:
[17]:
[18]:
[19]:
[20]:
