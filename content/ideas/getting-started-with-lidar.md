<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


---------------

I purchased on 11/8/25 (5 week delivery) from DFRobot the RPLiDAR S2L - ToF LiDAR 360° Laser Range Scanner - [RPLiDAR S2L](https://www.dfrobot.com/product-2617.html)
* <https://www.amazon.com/dp/B0BGXXTXSB>
* [10 Best Slamtec Rplidar Lidar Slam of 2025](https://reviews.oneclearwinner.com/product/slamtec-rplidar-lidar-slam/)
* [RPlidar S2](https://www.slamtec.com/en/S2)
* [RPLIDAR S2 Key parameters](https://www.slamtec.com/en/S2/Spec)

* [RoomMapper: Room Measurement with RPLidar and Raspberry Pi](https://www.hackster.io/aula-jazmati/roommapper-room-measurement-with-rplidar-and-raspberry-pi-7bf728)





Claude Code Prompt:

```text
Think hard about this analysis.
I want to gather price, popularity, size, features, speed of operation, and technical specifications for several LiDAR products.
I will use this information to determine the LiDAR products suitability for a robotic vehicle I'm currently designing.
Technical specification should include the following:
  * Measuring Range    [example: 0.15m - 12m]
  * Sampling Frequency    [example: 8K]
  * Rotational Speed    [example: 5.5Hz]
  * Angular Resolution    [example: ≤1°]
  * Dimensions    [example: 96.8 x 70.3 x 55mm]
  * System Voltage    [example: 5V]
  * System Current    [example: 100mA]
  * Power Consumption    [example: 0.5W]
  * Digital Output    [example: UART Serial (3.3 voltage level)]
  * Temperature Range    [example: 0℃-40℃]
  * Angular Range    [example: 360°]
  * Range Resolution    [example: ≤1% of the range（≤12m), ≤2% of the range（12m～16m)]
  * Accuracy   [1% of the range（≤3 m, 2% of the range（3-5 m, 2.5% of the range（5-25m)]
The LiDAR supplier I want you analyze is [SLAMTEC](https://www.slamtec.com/en)

I want the information to be summarized and organized as follows:
  * put the information table format with LiDAR product name across the top of the table
    and price, popularity, size, features, speed of operation, and technical specifications, etc. down the left side
  * Each product should be summarized with 500 words or less.  This summary should include:
    * typical use case
    * most note worthy or unique features
    * applicability to SLAM algorithm
    * popularity (if possible)
    * year of first offer (if possible)
    * suitability for a small robot capable rapid turns, speeds of one meter/sec, with Raspberry Pi 5 computer on board
  * supply your results in a markdown file
```






# SLAMTEC RPLIDAR Product Analysis
## Comprehensive Evaluation for Robotic Vehicle Design

---------------

## Product Specifications Comparison Table

| **Specification** | **RPLIDAR A1** | **RPLIDAR A2** | **RPLIDAR A3** | **RPLIDAR C1** | **RPLIDAR S2** | **RPLIDAR S3** |
|---|---|---|---|---|---|---|
| **Technology** | Triangulation | Triangulation | Triangulation | Fusion DTOF | DTOF (TOF) | DTOF (TOF) |
| **Price (USD)** | $99-117 | $229-258 | $584-599 | $65-81 | $399-537 | $549 |
| **Measuring Range** | 0.15m - 12m | 0.15m - 12m (A2M8)<br>0.15m - 16m (A2M12) | 0.2m - 25m (Enhanced)<br>0.2m - 20m (Outdoor) | 0.05m - 12m | 0.05m - 30m (S2)<br>0.05m - 18m (S2L) | 0.05m - 40m (70% reflect)<br>0.05m - 15m (10% reflect) |
| **Sampling Frequency** | 8,000 Hz (8K) | 8,000 Hz (8K) | 16,000 Hz (Enhanced)<br>10,000 Hz (Outdoor) | 5,000 Hz (5K) | 32,000 Hz (32K) | 32,000 Hz (32K) |
| **Rotational Speed** | 5.5 Hz typical<br>(2-10 Hz adjustable) | 10 Hz typical<br>(5-15 Hz adjustable) | 15 Hz typical<br>(10-20 Hz adjustable) | 10 Hz typical<br>(5-15 Hz adjustable) | 15 Hz typical<br>(10-20 Hz adjustable) | 15 Hz typical<br>(10-20 Hz adjustable) |
| **Angular Resolution** | ≤1° (at 5.5Hz) | 0.45° - 1.35°<br>(0.9° at 10Hz) | 0.225° - 0.45° | 0.45° - 1.35° | 0.234° - 0.468° | 0.1125° - 0.338° |
| **Dimensions** | 98.5mm (W) x 60mm (H) | 101mm (W) x 40mm (H) | 76mm (W) x 41mm (H) | 98mm (W) x 62mm (H) | 95mm (W) x 40mm (H) | 95mm (W) x 40mm (H) |
| **Weight** | 170g | 190g | 190g | ~165g | ~190g | ~175g |
| **System Voltage** | 5V DC | 5V DC | 5V DC | 5V DC | 5V DC | 5V DC |
| **System Current** | 400-500mA | 400-500mA | 500-800mA | 400-500mA | 500-800mA | 500-800mA |
| **Power Consumption** | 2-2.5W | 2-2.5W | 2.5-4W | 2-2.5W | 2.5-4W | 2.5-4W |
| **Digital Output** | UART (115200 bps)<br>3.3V TTL | UART (115200 bps)<br>3.3V TTL | UART (256000 bps)<br>3.3V TTL | UART (115200 bps)<br>3.3V TTL | UART/Ethernet<br>3.3V TTL | UART/Ethernet<br>3.3V TTL |
| **Temperature Range** | 0°C - 40°C | 0°C - 50°C | 0°C - 50°C | 0°C - 50°C | -10°C - 60°C | -10°C - 60°C |
| **Angular Range** | 360° | 360° | 360° | 360° | 360° | 360° |
| **Range Resolution** | <1% (≤12m) | <1.5% (≤12m)<br><2% (12-16m) | <0.5% (indoor)<br><1% (outdoor) | <2% (≤12m) | <1% (≤30m) | <1% (≤40m) |
| **Accuracy** | ≤1% at <3m<br>≤2% at 3-12m | ≤1% at <3m<br>≤2% at 3-12m | ≤0.5% at <10m<br>≤1% at 10-25m | ≤2% at <12m | ≤1% at <30m | ≤1% at <40m |
| **Scan Optical Height** | 60mm | 18mm | 41mm | 62mm | 18mm | 40mm |
| **Year First Offered** | 2014 | 2016 | 2017-2018 | 2023 | 2020-2021 | 2023-2024 |
| **Laser Safety** | Class 1 (<5mW) | Class 1 (<3mW) | Class 1 (<3mW) | Class 1 | Class 1 | Class 1 |
| **Operating Mode** | Indoor/No sunlight | Indoor/No sunlight | Enhanced/Outdoor | Indoor/Outdoor | Indoor/Outdoor | Indoor/Outdoor |
| **IP Rating** | None | None | None | None | IP65 (with cover) | None |

---------------

## Detailed Product Summaries
### RPLIDAR A1 (A1M8-R6)

**Typical Use Case:** Entry-level robotics education, hobbyist projects, small indoor mobile robots, educational SLAM implementations,
and cost-sensitive applications requiring basic 360° scanning.

**Most Noteworthy Features:**
* Most affordable SLAMTEC LiDAR at under $100
* OPTMAG contactless power/data transmission technology for extended lifespan
* 8,000 samples per second at economic price point
* Plug-and-play USB connectivity
* Established, mature product with extensive community support
* 12-meter range (upgraded from earlier 6m models)

**Applicability to SLAM Algorithms:**
The A1 was specifically designed for SLAM applications and remains highly suitable.
Its 8K sampling rate provides adequate point density for most 2D SLAM implementations including GMapping, Cartographer, and Hector SLAM.
The triangulation-based measurement provides consistent accuracy in typical indoor environments.
While not the highest resolution option, it delivers reliable performance for loop closure detection and map building in controlled indoor spaces.

**Popularity:**
The RPLIDAR A1 is arguably the most popular and widely deployed low-cost LiDAR in the robotics community.
Extensive ROS/ROS2 support, abundant tutorials, and a large user base make it the default choice for educational robotics and DIY projects.
Available through major distributors globally with strong ecosystem support.

**Year of First Offer:**
2014 (original release), with the A1M8-R6 revision released around 2021

**Suitability for Small Robot (Raspberry Pi 5, 1 m/s, Rapid Turns):** **EXCELLENT**
The A1 is highly suitable for your application.
At 170g and compact dimensions, it won't significantly affect robot dynamics.
The 8K sampling rate at 5.5-10Hz scan rates provides sufficient update frequency for 1 m/s velocity.
UART communication at 115200 bps integrates seamlessly with Raspberry Pi 5. The 12m range exceeds typical indoor navigation requirements.
Rapid turns are well-supported due to the 360° scanning nature and adjustable scan rates.
The low power consumption (2-2.5W) is manageable for battery-powered systems.

Primary limitation:
limited outdoor capability without direct sunlight, and lower angular resolution may miss thin obstacles during rapid rotation.

---------------

### RPLIDAR A2 (A2M12)

**Typical Use Case:** Commercial service robots, industrial AGVs, educational robotics requiring longer range, upgraded indoor mobile platforms, and applications demanding improved reliability and lifespan over the A1.

**Most Noteworthy Features:**
* Brushless motor with OPTMAG technology for 5-year lifespan (24/7 operation)
* Ultra-thin profile at only 40mm height
* Improved 16-meter range capability (A2M12 variant)
* Higher scan rate options (5-15 Hz adjustable)
* Enhanced angular resolution of 0.9° at 10Hz
* Quieter operation compared to A1
* Superior mechanical reliability for commercial deployments

**Applicability to SLAM Algorithms:** The A2 represents a significant upgrade for SLAM applications. The extended 16m range enables mapping of larger spaces, while the improved angular resolution and higher scan rates (up to 15Hz) provide better feature detection for place recognition. The enhanced reliability makes it suitable for long-term autonomous deployments where sensor failure is unacceptable. Compatible with all major SLAM frameworks and offers more stable odometry integration due to consistent scan timing.

**Popularity:** Very popular in commercial and semi-professional robotics. Widely adopted by research labs and robotics startups as the "step-up" from A1. Strong ROS/ROS2 driver support and proven deployment track record in commercial cleaning robots and warehouse AGVs.

**Year of First Offer:** 2016 (A2 series), with A2M12 variant released around 2019-2020

**Suitability for Small Robot (Raspberry Pi 5, 1 m/s, Rapid Turns):**
**EXCELLENT** - The A2M12 is exceptionally well-suited for your robot. The ultra-thin 40mm profile minimizes vertical space requirements, crucial for compact robot designs. At 190g, it remains lightweight. The 10Hz typical scan rate (up to 15Hz) ensures responsive obstacle detection even during rapid directional changes at 1 m/s. The 16m extended range provides generous look-ahead distance for path planning. UART interface works perfectly with Raspberry Pi 5. The improved angular resolution (0.9° vs 1°) better captures thin obstacles during fast rotations. The brushless motor ensures silent operation and eliminates vibration-induced odometry errors. Only minor consideration: slightly higher power draw (2-2.5W) and still limited to indoor use without direct sunlight.

---------------

### RPLIDAR A3 (A3M1)

**Typical Use Case:** Professional service robots, outdoor/indoor hybrid applications, large-scale mapping projects, advanced research platforms, commercial delivery robots, and applications requiring maximum triangulation-based range and performance.

**Most Noteworthy Features:**
* Longest range of triangulation-based RPLIDAR series at 25 meters
* Dual operating modes: Enhanced (indoor) and Outdoor (sunlight resistance)
* Highest sampling rate in A-series at 16,000 Hz
* Superior angular resolution of 0.225°
* Enhanced mode: 25m white objects, 10m dark objects
* Outdoor mode: 20m with daylight interference resistance
* Fast 15Hz scan rate (10-20Hz adjustable)
* RPVision 3.0 long-distance measurement engine

**Applicability to SLAM Algorithms:** The A3 represents the pinnacle of triangulation-based LiDAR for SLAM. The 16K sampling frequency and 0.225° angular resolution provide exceptionally dense point clouds, enabling precise feature extraction and robust loop closure even in challenging environments. The outdoor mode expands SLAM capabilities to mixed indoor/outdoor scenarios, previously problematic for triangulation sensors. The 25m range enables SLAM in warehouses, parking structures, and other large spaces. Particularly effective with graph-based SLAM (GTSAM, g2o) that leverage high-density measurements.

**Popularity:** Popular among professional robotics companies and advanced research institutions. Standard choice for commercial autonomous mobile robots (AMRs) in logistics. Strong presence in academic research papers on autonomous navigation. Premium pricing limits hobbyist adoption but widespread in industry.

**Year of First Offer:** 2017-2018

**Suitability for Small Robot (Raspberry Pi 5, 1 m/s, Rapid Turns):**
**VERY GOOD** - The A3 is well-suited but possibly over-specified for your application. The 190g weight and 41mm height are manageable. The exceptional 16K sampling rate and 15Hz scan frequency provide excellent temporal resolution for rapid turn detection. The 0.225° angular resolution ensures thin obstacles are detected even during fast rotation. The 25m range far exceeds indoor navigation needs but enables outdoor expansion. Higher bandwidth UART (256Kbps) integrates well with Pi 5. However, the higher cost may not be justified for 1 m/s indoor applications where A2 performance suffices. The outdoor mode is valuable if future semi-outdoor operation is planned. Power consumption (2.5-4W) is higher but manageable. Best choice if budget allows and outdoor capability or maximum precision is needed.

---------------

### RPLIDAR C1

**Typical Use Case:** Budget-conscious consumer robotics, home service robots, robot vacuums, compact mobile platforms, hobbyist projects requiring better close-range performance than triangulation sensors, and educational SLAM with modern TOF technology.

**Most Noteworthy Features:**
* Lowest cost DTOF LiDAR at $65-81
* Fusion technology combining triangulation and DTOF advantages
* Excellent close-range performance with 0.05m minimum distance (vs 0.15-0.2m for A-series)
* Provides reflectivity data and 2.5D information beyond basic ranging
* Minimal blind zone for obstacle avoidance
* Superior detection of dark/low-reflectivity objects
* High compatibility with existing SLAMTEC ecosystem
* Compact and quiet operation

**Applicability to SLAM Algorithms:** The C1 brings DTOF advantages to SLAM at entry-level pricing. The 0.05m minimum range eliminates the blind zone problem common in triangulation sensors, enabling wall-following and tight-space navigation. The reflectivity output provides additional features for place recognition and loop closure. The 5K sampling rate, while lower than A2/A3, is adequate for typical SLAM implementations. The fusion technology provides more consistent measurements across varying surface types (dark/shiny objects), reducing false obstacles. Well-suited for modern probabilistic SLAM frameworks that can incorporate intensity data.

**Popularity:** Rapidly growing popularity since 2023 release. Strong adoption in home robotics and DIY community due to low price and improved close-range capability. Increasingly common in robot vacuum projects and budget AMR platforms. ROS2 support is mature and actively maintained.

**Year of First Offer:** 2023

**Suitability for Small Robot (Raspberry Pi 5, 1 m/s, Rapid Turns):**
**EXCELLENT** - The C1 is highly suitable and potentially the best value choice. At approximately 165g and 98mm diameter, size/weight are comparable to A1. The 5K sampling at 10Hz provides adequate update rates for 1 m/s navigation. The critical advantage is the 0.05m minimum range, allowing detection of obstacles immediately adjacent to the robot - essential for rapid turns in confined spaces. The DTOF technology provides more consistent measurements during rotation versus triangulation. The 12m maximum range suffices for indoor navigation. UART integration with Pi 5 is straightforward. The reflectivity output can enhance obstacle classification. Power consumption (2-2.5W) is low. The $65-81 price point offers exceptional value. Main limitation: 5K sampling is lower than A2/A3, potentially missing very thin obstacles during fastest turns, but adequate for most applications.

---------------

### RPLIDAR S2 (S2/S2L/S2E variants)

**Typical Use Case:** Commercial service robots, industrial AMRs, outdoor/indoor navigation, warehouse automation, parking lot navigation, delivery robots, agricultural robots, and applications requiring IP65 protection with long-range capability.

**Most Noteworthy Features:**
* Professional-grade 30m range (S2) or 18m (S2L variant)
* Industry-leading 32,000 Hz sampling frequency
* True indoor/outdoor operation with 80Klux sunlight resistance
* IP65 rating (with protective cover) for dusty/wet environments
* Ultra-thin 18mm optical scanning height
* Detects specular/mirror-like surfaces reliably
* 10m range on 10% reflectivity (dark) objects
* Dual communication interfaces: UART and Ethernet
* Backward compatible with A-series interfaces

**Applicability to SLAM Algorithms:** The S2 represents professional-grade SLAM capability. The 32K sampling frequency provides the highest point density in the RPLIDAR lineup, enabling precise feature extraction and robust data association. The 30m range enables SLAM in outdoor and large industrial spaces. The DTOF technology's immunity to ambient light allows consistent SLAM operation in variable lighting, including direct sunlight - previously impossible with triangulation sensors. The high sampling density improves loop closure detection and reduces drift in long-term mapping. Ethernet connectivity enables efficient large-scale point cloud transmission. Ideal for production-grade autonomous systems requiring 24/7 operation.

**Popularity:** Standard choice for commercial and industrial robotics. Widely deployed in logistics automation, commercial cleaning robots, and autonomous delivery platforms. Strong presence in agricultural robotics market. Professional pricing limits hobbyist adoption but extensive industry validation.

**Year of First Offer:** 2020-2021

**Suitability for Small Robot (Raspberry Pi 5, 1 m/s, Rapid Turns):**
**VERY GOOD** - The S2 is well-suited but over-specified for basic 1 m/s indoor robots. At ~190g and 40mm height, physical integration is feasible. The exceptional 32K sampling and 15Hz scan rate provide outstanding temporal resolution for rapid maneuvers - likely overkill for 1 m/s but ensures zero missed detections. The 18mm optical height is ideal for low-profile robots. UART or Ethernet communication both work with Pi 5. The 30m range vastly exceeds indoor needs but enables future outdoor expansion. IP65 protection is unnecessary for clean indoor environments but valuable if exposed to dust/moisture. Power consumption (2.5-4W) is higher. The $399-537 price point may not be justified unless professional-grade reliability, outdoor capability, or future commercial deployment is planned. Excellent choice for expandable platforms or semi-outdoor operation.

---------------

### RPLIDAR S3

**Typical Use Case:** Premium service robots, advanced outdoor navigation, drone/UAV obstacle avoidance, security robots, autonomous vehicles (campus shuttles), long-range mapping applications, and systems requiring maximum performance in compact form factor.

**Most Noteworthy Features:**
* Longest range in RPLIDAR lineup at 40m (70% reflectivity)
* Ultra-compact at only 40mm total height
* Highest angular resolution at 0.1125° (smallest LiDAR from SLAMTEC)
* 32,000 Hz sampling frequency
* SL-TOF proprietary ranging technology
* 15m range on low-reflectivity (10% black) objects
* 80Klux extreme sunlight immunity
* 15Hz typical scan rate (10-20Hz adjustable)
* Full ecosystem compatibility

**Applicability to SLAM Algorithms:** The S3 delivers flagship SLAM performance in a compact package. The 40m range enables large-scale outdoor SLAM for campus navigation, parking lots, and open industrial areas. The 0.1125° angular resolution provides the finest spatial detail, critical for detecting small features and improving map precision. The 32K sampling ensures dense point clouds even at maximum 20Hz scan rates. The SL-TOF technology's robustness to ambient light enables reliable outdoor SLAM without degradation. Particularly valuable for multi-session SLAM where precise localization across different lighting conditions is required. Supports advanced graph optimization and NDT (Normal Distributions Transform) algorithms that benefit from high-resolution measurements.

**Popularity:** Flagship product gaining rapid adoption in premium robotics applications. Popular in outdoor autonomous platforms, security robots, and advanced research projects. Growing presence in commercial autonomous vehicles. Premium pricing ($549) positions it as professional/industrial solution rather than hobbyist choice, but increasing popularity in well-funded startups.

**Year of First Offer:** 2023-2024

**Suitability for Small Robot (Raspberry Pi 5, 1 m/s, Rapid Turns):**
**GOOD** - The S3 is capable but likely over-specified for your application. At ~175g and 40mm height, it's physically suitable. The 32K sampling and exceptional 0.1125° resolution provide maximum obstacle detection during rapid turns - detecting even thin wires or small protrusions. The 15-20Hz scan rate ensures real-time responsiveness. However, the 40m range is excessive for indoor 1 m/s robots, and the precision may exceed sensor fusion capabilities of typical small robot systems. UART/Ethernet communication works with Pi 5. Power (2.5-4W) is manageable. The $549 price point is difficult to justify unless you need outdoor capability, maximum precision for research, or future deployment scaling. Consider only if budget allows and outdoor expansion or extreme precision (sub-centimeter mapping) is required. For pure indoor 1 m/s operation, C1, A1, or A2 offer better value while meeting performance needs.

---------------

## Summary Recommendations for Your Robotic Vehicle

### Primary Recommendations (Prioritized)

1. **RPLIDAR C1** ($65-81) - **BEST VALUE CHOICE**
   * Excellent price-to-performance ratio
   * Superior close-range detection (0.05m blind zone) crucial for rapid turns
   * DTOF technology provides consistent measurements during rotation
   * Adequate 12m range and 5K sampling for 1 m/s indoor navigation
   * Lightest option, minimal impact on robot dynamics
   * Modern technology with strong future support

2. **RPLIDAR A1** ($99-117) - **PROVEN & RELIABLE**
   * Most established product with largest community support
   * Extensive tutorials and troubleshooting resources
   * Proven performance in countless DIY robots
   * Low power consumption
   * Slightly larger blind zone (0.15m) but adequate for most applications

3. **RPLIDAR A2M12** ($229-258) - **PROFESSIONAL UPGRADE**
   * Best choice if budget allows for quality-of-life improvements
   * Ultra-thin 40mm profile ideal for compact robots
   * 16m extended range for larger spaces
   * 5-year lifespan critical for long-term projects
   * Silent operation improves overall robot refinement

### Conditional Recommendations

4. **RPLIDAR S2** ($399-537) - If outdoor operation or IP65 protection needed
5. **RPLIDAR A3** ($584-599) - If maximum precision or outdoor mode required
6. **RPLIDAR S3** ($549) - Only if future outdoor expansion or flagship performance justified

### Not Recommended
None - all SLAMTEC products are viable, but S2/A3/S3 are over-specified for basic 1 m/s indoor applications.

---------------

## Technical Integration Notes

All RPLIDAR products interface cleanly with Raspberry Pi 5:
* **Communication**: UART (3.3V TTL) directly compatible with Pi 5 GPIO, or use included USB adapter
* **Power**: All run on 5V (2-4W), can be powered from Pi 5 or separate regulated supply
* **Software**: Mature ROS/ROS2 drivers, Python libraries, and C++ SDKs available
* **Real-time Performance**: Pi 5 easily handles LiDAR data processing with CPU overhead to spare

**Rapid Turn Considerations**:
* C1's 0.05m minimum range is significant advantage in tight maneuvers
* Higher scan rates (A2/A3: 10-15Hz) reduce motion blur during rotation
* All products support 360° scanning, no dead zones during turns
* For 1 m/s max speed: 5-10Hz scan rate is adequate; 15Hz+ is conservative

**Power Budget Planning**:
* A1/C1: ~2-2.5W (400-500mA @ 5V)
* A2: ~2-2.5W (400-500mA @ 5V)
* A3/S2/S3: ~2.5-4W (500-800mA @ 5V)

---------------

## Conclusion

For a Raspberry Pi 5-based robot operating at 1 m/s with rapid turn capability, the **RPLIDAR C1** offers the best combination of value, performance, and modern features. Its DTOF technology and minimal blind zone address the key challenges of compact robot navigation. The **RPLIDAR A1** remains an excellent choice for budget-conscious builds with proven reliability. For professional or long-term projects where budget allows, the **RPLIDAR A2M12** provides meaningful improvements in range, resolution, and longevity that justify the incremental cost.

The higher-end S2, A3, and S3 models deliver exceptional performance but are optimized for applications (outdoor navigation, 30m+ range, industrial environments) that exceed your stated requirements. Reserve these for future platform upgrades or if specific capabilities (outdoor operation, IP65 rating, maximum range) are mission-critical.

---------------

*Document compiled from SLAMTEC official specifications, retailer data, and user community feedback as of November 2025.*

















### Lidar DTOF vs Triangulation
Lidar DTOF (Direct Time-of-Flight) measures distance by timing how long it takes a light pulse to travel to an object and back,
making it faster and better for long-range, real-time applications like autonomous driving.
Triangulation measures distance by using the angle between a laser and a sensor's receiver, which is more accurate for short-range,
high-precision tasks like those in industrial robotics, but is slower and less accurate at longer distances.

Sources:
* [Do you know how to choose lidar ?](https://www.youtube.com/watch?v=mUuI32JQolo&t=1s)
* [7 Tips for Choosing a Lidar](https://www.youtube.com/watch?v=Yf1SRjS1Rxg)
* [SLAM Lidar RPLIDAR A1 A2 A3 S1 S2 MapperM2 support Mapping navigation for ROS robot](https://www.youtube.com/watch?v=3j2vGMQMyH8)

### FAST-LIO, Navigation2
* [Robust Odometry and Fully Autonomous Driving Robot | ATCrawler x FAST-LIO x Navigation2](https://www.youtube.com/watch?v=0oBHPxRycTk&t=101s)








* [Self-Driving Cars And The Fight Over The Necessity Of Lidar](https://hackaday.com/2025/10/30/self-driving-cars-and-the-fight-over-the-necessity-of-lidar/)



* [LiDAR, Radar, and PCR: What's The Difference?](https://www.sparkfun.com/news/10536)
* [How to choose Radar Sensors (Tutorial). Incl. PIR and LIDAR](https://www.youtube.com/watch?v=PNbAM9IhfBE)
* [Linear Array Solid LiDAR (25-300mm)](https://www.dfrobot.com/product-2645.html)

* [An Explainer on the Different Types of LiDAR Devices](https://www.crowdsupply.com/onion/tau-lidar-camera/updates/an-explainer-on-the-different-types-of-lidar-devices)
* [TFmini Plus - ToF LIDAR Range Finder](https://www.seeedstudio.com/TFmini-Plus-LIDAR-Range-Finder-based-on-ToF-p-3222.html)
* [Homemade Lidar: OpenTOFLidar](https://hackaday.com/2020/03/24/lidar-system-isnt-just-a-rangefinder-anymore/)
* [Stereo Vision and LiDAR Powered Donkey Car](https://www.hackster.io/bluetiger9/stereo-vision-and-lidar-powered-donkey-car-575769)
* [Autonomous Rover Navigates The House With LIDAR](https://hackaday.com/2020/09/22/autonomous-rover-navigates-the-house-with-lidar/)
* [Lidar House Looks Good, Looks All Around](https://hackaday.com/2020/12/20/lidar-house-looks-good-looks-all-around/)


# A Quick Guide to LiDAR

* [A Quick Guide to LiDAR: Part 1 - Theory](https://medium.com/mlearning-ai/a-quick-guide-to-lidar-part-1-theory-7c8ff48af0b9)
* [A Quick Guide to LiDAR: Part 2](https://medium.com/mlearning-ai/a-quick-guide-to-lidar-part-2-cd2dcd2e60fd)
* [Lidar Types and How They Work](https://www.dfrobot.com/blog-1643.html)
* [7 Real-World Applications of LiDAR Technology](https://www.dfrobot.com/blog-1644.html)
* [What is the Open Source Framework for LiDAR?](https://www.dfrobot.com/blog-1647.html)
* [FAQ about LiDAR](https://www.dfrobot.com/forum/topic/320253)
* [A Pi-Based LiDAR Scanner](https://hackaday.com/2025/04/18/a-pi-based-lidar-scanner/)
  * [GitHub: PiLiDAR/PiLiDAR](https://github.com/PiLiDAR/PiLiDAR)



#### Distance Sensor

* [Make A Super Cute LiDAR Measurement Module](https://hackaday.com/2024/06/02/make-a-super-cute-lidar-measurement-module/)
  * [Ultra Compact LiDAR Distance Meter/Range Finder](https://www.instructables.com/Tiny-LiDAR-Laser-Range-Finder/)
  * [Inside a VL53L0X](https://hackaday.io/project/25571-mappydot/log/63298-inside-a-vl53l0x)

* [An Explainer on the Different Types of LiDAR Devices](https://www.crowdsupply.com/onion/tau-lidar-camera/updates/an-explainer-on-the-different-types-of-lidar-devices)
* [best distance sensor for robots](http://www.teraranger.com/products/teraranger-one/)
* [Linear Array Solid LiDAR (25-300mm)](https://www.dfrobot.com/product-2645.html)
* [RPLIDAR A1M8 - 360 Degree Laser Scanner Development Kit](https://www.dfrobot.com/product-1125.html)
* [Xaxxon OpenLIDAR Sensor offers open hardware and software](https://www.geeky-gadgets.com/xaxxon-openlidar-sensor-16-10-2019/)
* [Make Your Own LIDAR Sensor](https://dzone.com/articles/make-your-own-lidar-sensor)
  * <https://www.adafruit.com/product/3316>
  * <https://www.adafruit.com/product/3317>
  * [TF-Luna (ToF) Micro Single-point Ranging LiDAR](https://www.dfrobot.com/product-1995.html?tracking=5e72005d37725)
* [Steering Self Driving Car without LIDAR](https://medium.com/towards-data-science/steering-self-driving-car-without-lidar-a6b0a4d2e2f1)
* [Lidar House Looks Good, Looks All Around](https://hackaday.com/2020/12/20/lidar-house-looks-good-looks-all-around/)
* [LIDAR Built On Familiar Platform](https://hackaday.com/2020/04/11/lidar-built-on-familiar-platform/)
* [TFmini Plus - ToF LIDAR Range Finder](https://www.seeedstudio.com/TFmini-Plus-LIDAR-Range-Finder-based-on-ToF-p-3222.html)
* [Homemade Lidar: OpenTOFLidar](https://hackaday.com/2020/03/24/lidar-system-isnt-just-a-rangefinder-anymore/)
* [Stereo Vision and LiDAR Powered Donkey Car](https://www.hackster.io/bluetiger9/stereo-vision-and-lidar-powered-donkey-car-575769)


#### Sensor Fusion

* [Sensor Fusion](https://towardsdatascience.com/sensor-fusion-90135614fde6)
* [Sensor Fusion of LiDAR and Camera — An Overview](https://medium.com/@navin.rahim/sensor-fusion-of-lidar-and-camera-an-overview-697eb41223a3)
* [Camera-Lidar sensor fusion in real time for autonomous surface vehicles](http://folk.ntnu.no/edmundfo/msc2019-2020/norbye-lidar-camera-reduced.pdf)



