# B202AA-PCIe <sup>V5.1</sup>

![GitHub release (latest by date)](https://img.shields.io/github/v/release/akkoyun/MAX78630) ![arduino-library-badge](https://www.ardu-badge.com/badge/MAX78630.svg?) ![GitHub stars](https://img.shields.io/github/stars/akkoyun/MAX78630?style=flat&logo=github) [![PlatformIO Registry](https://badges.registry.platformio.org/packages/akkoyun/library/MAX78630.svg)](https://registry.platformio.org/libraries/akkoyun/MAX78630)

---

 <center><img src="/Images/B202AA-PCIe.png" width="800"></center></br>

## Abstract

B202AA-PCIe module is an energy measurement module (EMM) for poly phase power monitoring systems. It is designed for real-time monitoring for a variety of typical three-phase configurations in industrial applications. It is available in a mini PCIe size PCB module.

The B202AA-PCIe provides up to six analog inputs for interfacing to voltage and current sensors. Scaled voltages from the sensors are fed to the single converter front-end utilizing a high-resolution delta-sigma converter. Supported current sensors include current transformers (CT), Rogowski coils, and resistive shunts.

An embedded 24-bit measurement processor and firmware perform all necessary computations and data formatting for accurate reporting to the host. With integrated flash memory for storing nonvolatile calibration coefficients and device configuration settings, the B201 is capable of being a completely autonomous solution.

<center><img src="/Images/Terminal.png" width="800"></center></br>

The B202AA-PCIe is designed to interface to the host processor via the UART interface.

* Full open hardware.
* Module connected MCU via UART and measure parameters.
* Module gives alarm output which is configured via library.
* Module gives output of VR,VS and VT Sense (optical isolated).
* Full mini PCIe size.

## Tech Files

[B202AA-PCIe Schematics](/Electronic/Output/Schematic%20Prints/Schematic%20Prints.PDF)

## PinOut

| Top Side            | Pin ID | Pin ID | Bottom Side          |
|--------------------:|:------:|:------:|:---------------------|
| -                   | 01     | 02     | -                    |
| -                   | 03     | 04     | -                    |
| -                   | 05     | 06     | -                    |
| 3V3                 | 07     | 08     | 3V3                  |
| -                   | 09     | 10     | -                    |
| -                   | 11     | 12     | -                    |
| -                   | 13     | 14     | -                    |
| GND                 | 15     | 16     | GND                  |
| -                   | Key    | Key    | -                    |
| GND                 | 17     | 18     | GND                  |
| -                   | 19     | 20     | Module UART RX       |
| -                   | 21     | 22     | Module UART TX       |
| GND                 | 23     | 24     | GND                  |
| -                   | 25     | 26     | VR Sense             |
| -                   | 27     | 28     | VS Sense             |
| -                   | 29     | 30     | VT Sense             |
| -                   | 31     | 32     | AL1                  |
| -                   | 33     | 34     | -                    |
| -                   | 35     | 36     | -                    |
| -                   | 37     | 38     | -                    |
| -                   | 39     | 40     | -                    |
| GND                 | 41     | 42     | GND                  |
| -                   | 43     | 44     | -                    |
| GND                 | 45     | 46     | GND                  |
| -                   | 47     | 48     | -                    |
| -                   | 49     | 50     | -                    |
| GND                 | 51     | 52     | GND                  |

## Measured Parameters

In this Arduino Library we can read all data of energy parameters.

| Parameter                  | Phase R | Phase S | Phase T |
|----------------------------|:-------:|:-------:|:-------:|
| Instant Voltage            | Yes     | Yes     | Yes     |
| RMS Voltage                | Yes     | Yes     | Yes     |
| Fundamental Voltage        | Yes     | Yes     | Yes     |
| Harmonic Voltage           | Yes     | Yes     | Yes     |
| Frequency                  | Yes     | -       | -       |
| Instant Current            | Yes     | Yes     | Yes     |
| RMS Current                | Yes     | Yes     | Yes     |
| Peak Current               | Yes     | Yes     | Yes     |
| Fundamental Current        | Yes     | Yes     | Yes     |
| Harmonic Current           | Yes     | Yes     | Yes     |
| Active Power               | Yes     | Yes     | Yes     |
| ReActive Power             | Yes     | Yes     | Yes     |
| Apparent Power             | Yes     | Yes     | Yes     |
| Fundamental Power          | Yes     | Yes     | Yes     |
| Harmonic Power             | Yes     | Yes     | Yes     |
| Power Factor               | Yes     | Yes     | Yes     |
| Fundamental ReActive Power | Yes     | Yes     | Yes     |
| Harmonic Reactive Power    | Yes     | Yes     | Yes     |
| Fundamental VA Power       | Yes     | Yes     | Yes     |
| IC Temperature             | -       | -       | -       |

Also set limits for alarm monitoring.

---

## Want to buy ?

[![Want to buu](https://img.shields.io/badge/I_Sell_on-Tindie-blue.svg)](https://www.tindie.com/stores/akkoyun)

    New PCIe version is waiting production.

---

[![Support me](https://img.shields.io/badge/Support-PATREON-GREEN.svg)](https://www.patreon.com/bePatron?u=62967889) ![Twitter Follow](https://img.shields.io/twitter/follow/gunceakkoyun?style=social) ![YouTube Channel Views](https://img.shields.io/youtube/channel/views/UCIguQGdaBT1GnnVMz5qAZ2Q?style=social) [![E-Mail](https://img.shields.io/badge/E_Mail-Mehmet_Gunce_Akkoyun-blue.svg)](mailto:akkoyun@me.com) ![GitHub](https://img.shields.io/github/license/akkoyun/Statistical) 