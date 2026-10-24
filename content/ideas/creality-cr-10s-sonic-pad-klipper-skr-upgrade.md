

* [The 10 Upgrades I Install on EVERY Klipper 3D Printer](https://www.youtube.com/watch?v=h6g8DoTc7ys)





* [SKR V1.3 32-bit board upgrade for the CR-10](https://3dpblog.com/skr-32bit-control-board-upgrade-cr10/)
* [Klipper Setup](https://www.youtube.com/playlist?list=PLC4bOo0vesmLJ211bmSiWaJ9ahBUQUjjv)
* [Sonic Pad Basics](https://www.youtube.com/playlist?list=PLC4bOo0vesmLWWEeBWwv6oR4QzhP-0ctf)


## Creality Sonic Pad
The Creality Sonic Pad is a Klipper-based touchscreen tablet designed to supercharge your FDM (Fused Deposition Modeling) 3D printer.
It significantly boosts printing speeds and quality through advanced resonance compensation (input shaping).

The Sonic Pad comes pre-configured for most popular Creality models,
like the Ender-3 V3, Ender-3 S1, and CR-10 series.
Setup takes about 10–20 minutes, involving selecting your printer model,
updating the firmware via USB, and calibrating the device.
While it is intended for Creality printers,
the community has also adapted it for various third-party machines.

Key Features:
* **Lightning-Fast Speeds:** Powered by a 64-bit SoC, it replaces your printer's standard firmware (like Marlin)
  to allow drastically increased print speeds without sacrificing model quality.
* **Input Shaping:** Uses an included accelerometer to measure and cancel out
  printer vibrations, mitigating ghosting and ringing at high speeds.
* **Remote Management & Monitoring:** Features built-in WiFi and Ethernet.
  By plugging in a USB webcam, you can monitor prints remotely and record time-lapses.
* **Multi-Printer Control:** Capable of running and controlling up to 4 different FDM printers simultaneously via USB.

>**Advanced Resonance Compensation (Input Shaping)**
>is a firmware-level technique that cancels out machine vibrations by modifying motion commands.
>It eliminates ringing, ghosting, and rippling on printed surfaces,
>allowing you to push 3D printers to much higher speeds and accelerations without sacrificing quality
>
>**The Problem:** When a printhead or bed rapidly changes direction, the mechanical parts (frames, belts) flex and vibrate.
>These vibrations show up as wavy patterns (ringing) on your prints.
>
>**The Solution:** Input shaping artificially creates an opposing vibrational wave in the control signal.
>When the opposing wave meets the physical vibration, they cancel each other out.

* [Creality Sonic Pad in-depth review | Faster, easier 3D printing?](https://www.youtube.com/watch?v=IybJlj0WqKg)
* [Klipper On 4 3d Printers? Creality Sonic Pad 3 Months Later](https://www.youtube.com/watch?v=5Sz-cGuHZn4)
* [Maximizing Acceleration with the Sonic Pad on the CR-10S Pro V2 - Print speed is only half the story](https://www.youtube.com/watch?v=_socSGTgGcw)

* [Input Shaper - Klipper - Chris's Basement - 2023](https://www.youtube.com/playlist?list=PLB_0YGFjbOnZroPzoxA12NfsGMBCxctwH)

## Bigtreetech SKR V1.4
The [Bigtreetech](https://biqu.equipment/collections/control-board)
(BTT) SKR V1.4 is the "brain" and central motherboard of your 3D printer.
It processes G-code from your computer or SD card, tells the motors exactly how to move,
and regulates temperatures for the hot end and heated bed.

Upgrading to the SKR V1.4 provides several notable enhancements:
* **32-Bit Processing:** Unlike older 8-bit boards, the 32-bit architecture processes commands much faster.
  This allows for smoother curves, faster print speeds, and easier firmware updates via SD card.
* **Silent Stepper Motor Drivers:** The board has sockets for upgraded, removable motor drivers (like the popular TMC2209s),
  which eliminate the loud, whining motor noises and add features like "sensorless homing"
  (finding zero without needing physical end stop switches).
* **Extensive Upgradability:** It features built-in expansion ports for modern upgrades like a BLTouch for auto-bed leveling,
  Filament Run-Out Sensors, RGB light strips, and even a WiFi module.
* **Dual Z-Axis Support:** It includes dedicated, independent ports for running two separate stepper motors on your Z-axis,
  making leveling much easier.

>In the Bigtreetech (BTT) SKR series of 3D printer motherboards,
>"SKR" is widely believed to be an abbreviation based on the Chinese Pinyin for Shuai Ke Ran,
>which translates loosely to "Cool, Agile, and Decisive" or "Speedy."
>While Bigtreetech has never explicitly published an official, literal acronym for it in English,
>the SKR line is highly recognizable as their baseline of open-source,
>32-bit control boards designed for makers and DIY upgraders.

* [BigTreeTech SKR v1.4 First Look! | Overview & New Features](https://www.youtube.com/watch?v=pACQwIcyTtI&t=6s)
* [Bigtreetech SKR V1.4 (Turbo) comprehensive guide](https://www.youtube.com/watch?v=-Gdk0wHg51w)
* [SKR V1.3 32bit control board upgrade for CR-10](https://www.youtube.com/watch?v=B7gzDwh8UEM)
* [SKR 1.4 Tutorials](https://www.youtube.com/playlist?list=PLP-VDZmS6bFo6qyPS8MyBFKqepQHpjCEB)
* [BigTreeTech SKR v1.4 Mainboard - Full Install Part 1 - 2209 Drivers - Chris's Basement](https://www.youtube.com/watch?v=oHMZ0ocTYvM)

## Smart Filament Sensor
BTT SFS (Bigtreetech Smart Filament Sensor) V2.0 Break Detection Module - <https://www.amazon.com/dp/B0FLCV1H6Q?th=1>

## Touch Auto Bed Leveling
BL-Touch - <https://www.amazon.com/Upgraded-BL-Touch-Replacement-Brackets-Compatible/dp/B0CGHJDWHW/>
Creality CR Touch Auto Bed Leveling Sensor Kit - <https://www.amazon.com/dp/B0995H2X92/>











# Creality Sonic Pad + CR-10S (300) — Installation Resources

> **Note:** No guide or video exists specifically for the CR-10S (300) + Sonic Pad combination.
> The resources below are the closest available, covering similar CR-10 variants and the
> "user-defined printer" path for non-listed models.

---

## YouTube Videos

### CR-10S Pro V2 — Sonic Pad Klipper Install
Closest match to the CR-10S 300. The installation process is very similar.
* <https://www.youtube.com/watch?v=TzxjDuTZBHY>

### CR-10 Max — Sonic Pad Klipper Install
Documents using the Sonic Pad as a Klipper replacement on a non-officially-listed CR-10 variant.
* <https://www.youtube.com/watch?v=wdVBX194IeM>

---

## Written Guides

### Creality Experts — Sonic Pad Setup Guide
General setup guide covering the Sonic Pad with Creality printers, including custom/non-listed models.
* <https://www.crealityexperts.com/creality-sonic-pad-setup-guide>

### DREMC Knowledge Base — Sonic Pad (Klipper)
Covers firmware flashing for non-default printers, root access, resonance testing, and links to
Creality's official custom printer install manual on GitHub.
* <https://support.dremc.com.au/support/solutions/articles/51000321087-creality-sonic-pad-klipper->

---

## Key Config File

### Klipper Official CR-10S (2017) `printer.cfg`
The official Klipper repository includes a pre-made config for the CR-10S. This is the file you
would load via the Sonic Pad's **user-defined printer** path — the critical missing piece since
no official Sonic Pad preset exists for the CR-10S 300.
* <https://github.com/Klipper3d/klipper/blob/master/config/printer-creality-cr10s-2017.cfg>

---

## Recommended Approach

1. Follow the **DREMC guide** for the general Sonic Pad custom printer setup flow.
2. Use the **YouTube CR-10S Pro V2 video** to understand the firmware flashing steps.
3. Use the **Klipper CR-10S `printer.cfg`** as your starting configuration file.












# Creality CR-10S Upgrade Recommendations
### Goal: Speed + Quality + Quiet Operation (Full Stock Build)

> Upgrades are listed in priority order, with a suggested installation sequence at the bottom.

---

## 1. Stepper Drivers — Do This First
**BTT TMC2208 or TMC2209 drop-in stepper drivers**

The CR-10S stock drivers are loud. TMC2208/2209s are the single biggest bang-for-buck upgrade —
near-silent motion. Klipper has excellent TMC support (UART mode, stealthChop, spreadCycle tuning).
The 2209s are preferred as they also support sensorless homing.

---

## 2. Bed Leveling
**BLTouch or CR Touch (Creality's clone)**

Klipper's `bed_mesh` feature is excellent, but requires a probe. On a 300x300 bed this matters a
lot — manual leveling a large bed is tedious and the CR-10S bed is known to warp. The CR Touch is
cheaper and works fine with Klipper.

---

## 3. Extruder
**Dual-drive extruder (BMG clone or Orbiter)**

The stock CR-10S extruder is a single-drive arm-style unit that skips under pressure. A dual-drive
extruder dramatically improves filament grip, which matters even more at the higher speeds you'll
get with Klipper.

---

## 4. Hot End
**Micro Swiss all-metal hot end**

The stock PTFE-lined hot end limits you to ~240°C max safely. An all-metal hot end opens up ABS,
ASA, and PETG at higher speeds, and pairs well with Klipper's pressure advance tuning.

---

## 5. Part Cooling
**5015 blower fan**

Klipper's higher speeds expose weak part cooling quickly. The stock fan is mediocre. A 5015 blower
significantly improves overhangs and bridging at speed.

---

## 6. Input Shaper (Resonance Compensation)
**ADXL345 accelerometer**

The Sonic Pad includes one — confirm your kit has it. Klipper's input shaper (`[resonance_tester]`)
measures your printer's actual resonance frequencies and compensates automatically. This is what
lets you push speed without ringing artifacts, and is essential for getting the most out of the
Sonic Pad.

---

## 7. Frame Rigidity
**Dual Z-axis lead screw kit**

The CR-10S is single-Z stock, which causes Z-wobble and layer inconsistency at speed. Creality
sells an official dual-Z kit. Klipper also supports `Z_TILT_ADJUST` to automatically level dual-Z
setups.

---

## Nice-to-Have Additions

| Upgrade | Benefit |
| --- | --- |
| PEI spring steel sheet | Replaces glass bed; far better adhesion, prints pop off when cool |
| Capricorn PTFE tubing | Tighter 1.9mm ID (vs 2.0mm stock) reduces Bowden play, improves retraction |
| USB webcam | Remote monitoring beyond what the Sonic Pad offers (Pad handles most of this already) |


---

## Suggested Order of Operations

1. **TMC drivers + Sonic Pad/Klipper** — do these together as one job
2. **CR Touch** — configure `bed_mesh` in Klipper immediately after
3. **Dual-Z kit** — enable `Z_TILT_ADJUST` in Klipper config
4. **BMG dual-drive extruder** — tune pressure advance in Klipper after install
5. **PEI sheet** — easy win, do whenever
6. **All-metal hot end + 5015 fan** — prioritize if printing anything beyond PLA

