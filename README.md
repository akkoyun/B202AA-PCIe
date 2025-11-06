# B202AA-PCIe  
### 3-Phase Energy Analyzer Module  
**Project:** PollyPhase Energy Analyzer  
**Author:** Mehmet Günce Akkoyun  
**Version:** 02.00.01  
**Date:** 06.11.2025  

---

## Overview  

**B202AA-PCIe** is a high-precision **three-phase energy analyzer module** designed for industrial and agricultural environments.  
The module is built around the **MAX78630+PPM/D00** poly-phase metering SoC and interfaces to the host system through a **custom PCIe-compatible connector**.  

It performs real-time measurement of:
- Line-to-neutral and line-to-line **voltages (VR, VS, VT)**  
- Phase currents via external **Current Transformers (CTs)**  
- Derived parameters such as **active/reactive/apparent power**, **energy (Wh)**, **power factor**, and **frequency**

The design focuses on:
- **High accuracy (Class 0.2S)** metering  
- **Complete galvanic isolation** for UART and alarm interfaces  
- **Wide input range and fault tolerance** for rugged field applications  

---

## Functional Blocks  

| Block | Function | Key Components |
|-------|-----------|----------------|
| Voltage Input | Phase voltage scaling & isolation | 3×(3.3 M? + 1 k? divider, 22 nF filter, opto-isolator VOM617A) |
| Current Input | CT burden and protection | 3×(24.9 ? ± 0.1 % + 10 ? series, BAS316 clamps, 470 pF filter) |
| Measurement Core | 3-Phase metering | MAX78630+PPM/D00 |
| Isolation | UART & Alarm isolation | ISOW7821FDWE (UART), TLP2362 (AL1/AL2) |
| Power Isolation | 3.3 V - 3.3 V ISO DC/DC | PBT01F03S3V3 |
| Connector | Custom PCIe-style 52-pin edge | Compatible with all S-Bus PCIe modules |

---

## Measurement Inputs  

| Parameter | Nominal | Max (Continuous) | Description |
|------------|----------|------------------|--------------|
| Voltage (Phase–Neutral) | 230 V RMS | 400 V RMS | AC measurement via precision divider |
| Voltage (Phase–Phase) | 400 V RMS | 584 V RMS (safety) | Tested to 825 Vpk isolation |
| Current (CT input) | 5 A RMS nominal | 7 A RMS max | External CT, burden 24.9 ? + 10 ? |
| Frequency | 45 – 65 Hz | – | Automatic zero-cross detect |

---

## Electrical & Safety Specifications  

| Feature | Value / Description |
|----------|--------------------|
| **Galvanic Isolation** | ? 6 mm creepage/clearance (IPC9592 compliant) |
| **UART Isolation Voltage** | 2500 Vrms (ISOW7821) |
| **Alarm Isolation Voltage** | 3750 Vrms (TLP2362) |
| **TVS Protection** | 440 V (SMAJ440A) per phase |
| **Operating Temperature** | –25 °C to +85 °C |
| **Supply Voltage** | 3.3 V / 3.3 V ISO |
| **Power Consumption** | ? 0.8 W total |

---

## Accuracy & Error Budget  

### Voltage Channel (per phase)
| Item | Value | Note |
|------|--------|------|
| Divider ratio | 3.3 M? : 1 k? | 0.1 % tolerance |
| Gain error (uncalibrated) | ±0.20 % | RSS of divider & ADC |
| Phase error (50 Hz) | –0.40° | From 22 nF filter |
| Gain drift (0–70 °C) | ±0.18 % | Typical |
| After calibration | ±0.05 % gain / ±0.05° phase | with 2-point + phase comp |

### Current Channel (per phase)
| Item | Value | Note |
|------|--------|------|
| Burden | 24.9 ? ± 0.1 % + 10 ? | Kelvin connection |
| Gain error (uncalibrated) | ±0.20 % | ADC + burden |
| CT class impact | ±0.2 % – ±1.0 % | per CT rating |
| After calibration | ±0.10 – 0.20 % | typical |

### Combined Power (Active Power Error)
| Condition | PF = 1.0 | PF = 0.9 | PF = 0.5 |
|------------|-----------|-----------|-----------|
| Uncalibrated (CT = 0.5 %) | ±0.58 % | ±0.67 % | ±1.34 % |
| Calibrated | ±0.10 – 0.20 % | ±0.15 – 0.25 % | ±0.20 – 0.35 % |

**Energy (Wh) Accuracy:**  
Limited by power error + timebase tolerance (20 MHz ± 50 ppm).  
Resulting energy error typically **< ±0.25 % over 24 h** integration.

---

## Safety Margin Calculations  

### Voltage Divider  
- Total resistance: 3.301 M?  
- At 230 Vac: I ? 0.32 mA › P_total = 0.073 W  
- At 400 Vac: I ? 0.56 mA › P_total = 0.22 W  
- Per resistor (180 k?): ? 56 mW / 0.5 W = 11 % load  
- Temperature rise ? +14 °C › **safe below 74 °C**

### CT Burden Protection  
- Normal V_burden ? 0.25 Vpk (5 A RMS)  
- Clamp limit ? ±0.7 V › 3× margin  
- Diodes conduct only under fault, ensuring **no influence on phase**.

### Isolation  
- Creepage/clearance: ? 6 mm  
- TVS breakdown: 440 V pk  
- Withstand: 2.5 kVrms (UART) / 3.75 kVrms (Alarm)  

---

## Performance Summary  

| Parameter | Result |
|------------|---------|
| Voltage Accuracy | ±0.05 % (calibrated) |
| Current Accuracy | ±0.10 – 0.20 % (CT dependent) |
| Active Power Accuracy | ±0.20 – 0.35 % (typical PF range) |
| Energy Accuracy | ±0.25 % / day |
| Phase Drift | ? 0.05° (after compensation) |
| Temperature Coefficient | < 0.02 % / °C |
| Safety Margin (400 V RMS) | +45 % |

---

## Subsystem Scores  

| Subsystem | Score (10) | Notes |
|------------|-------------|-------|
| Phase Sense / Opto Isolation | **9.5** | Excellent thermal and fault safety |
| Voltage Divider & Filter | **9.0** | Very accurate; phase comp suggested |
| CT Channel & Protection | **9.5** | Ideal burden use, safe clamp |
| UART Isolation | **9.0** | Layout decoupling critical |
| Alarm Isolation | **9.0** | LED logic verified, add 100 ? ESD resistor |
| MAX78630 Core Integration | **9.5** | Datasheet-accurate, stable design |
| Power & EMC Architecture | **9.0** | Add CMC for field noise immunity |
| Connector & System Integration | **9.0** | Solid mechanical & logical design |

**Overall Design Score:** ? **9.2 / 10**

---

## Calibration & Testing  

**Recommended Calibration Steps:**  
1. Two-point voltage and current gain calibration (0.5 FS & FS).  
2. Phase compensation per channel at 50 Hz reference.  
3. Optional temperature drift mapping (25 °C / 50 °C / 70 °C).  
4. Verify PF = 1.0 and PF = 0.5 energy accumulation error.  

**Expected Post-Calibration Class:**  
- **Class 0.2 / 0.2S** accuracy (EN 62053-22 compliant).

---

## Licensing & Documentation  

© 2025 Günce Akkoyun – All Rights Reserved  
Design and documentation by **Mehmet Günce Akkoyun**  
Commercial use without permission is prohibited.  

**Repository:** [github.com/akkoyun/B202AA-PCIe](https://github.com/akkoyun/B202AA-PCIe)  
**Contact:** akkoyun@me.com  

---