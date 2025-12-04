# 3.3V to 2.8V Sub-Regulator Design

## Project Overview

This repository contains the design, simulation, and analysis of a precision sub-regulator circuit. This project was conducted as part of the CMOS References and Regulators (EC2.410) curriculum, utilizing the architecture concepts covered in the lecture on October 23rd.

The primary objective is to design a robust regulator capable of handling specific load transients and process variations while maintaining high stability and Power Supply Rejection Ratio (PSRR).

## Design Specifications

The sub-regulator is designed to meet the following electrical constraints:

| **Parameter** | **Specification** | **Conditions** |
| :--- | :--- | :--- |
| **Input Voltage** | 3.3V | Range: ±10% (2.97V - 3.63V) |
| **Output Voltage** | 2.8V | Target |
| **Load Current** | 0 to 1mA | Nominal Range |
| **Quiescent Current** | < 500 µA | No Load condition |
| **PVT Variation** | < 5 mV | Across Process, Voltage, Temperature |
| **Monte Carlo (MC)** | < ±1.5% | Random Variation |
| **Phase Margin** | > 45° | Full Load |
| **UGB** | > 1 MHz | Full Load |
| **PSRR (DC)** | > 40 dB |  |
| **PSRR (High Freq)** | > 0 dB | Must not drop below 0dB at any frequency |

### Transient Requirements

* **Impulse Response:** Capable of handling a sudden **6mA impulse** on top of a 1mA static load with a maximum undershoot of **25mV**.

* **De-coupling Capacitor:** optimized to meet the undershoot specification.

## Simulation & Reporting Checklist

The final report and simulation logs located in this repository cover the following characterizations:

### 1. Static & Random Analysis

* [ ] **PVT Analysis:** Static variation in output voltage across corners. (4-bit Resistive Trimming has to be performed for 5 corners)

* [ ] **Monte Carlo Analysis:** Random variation histogram and statistical summary (Mean/Sigma) relative to the ±1.5% target.

### 2. Transient Response

* [ ] **Load Transients:** - 0 to 1mA step response.

  * **Impulse Response:** 6mA impulse (superimposed on 1mA load) to verify <25mV undershoot.

* [ ] **Settling Time:** Analysis of output recovery time at no-load conditions.

* [ ] **Load Profile:** Plot of Output Voltage vs. Time alongside the applied Load Current profile.

### 3. Loop Dynamics & Stability

* [ ] **Loop Gain & Phase:** Bode plots showing Phase Margin (>45°) and UGB (>1MHz).

* [ ] **Bandwidth:** 3dB Bandwidth extraction across PVT corners.

### 4. Regulation & Rejection

* [ ] **DC Load Regulation:** Output Voltage vs. Load Current plot across PVT.

* [ ] **PSRR:** Magnitude plot vs. Frequency (verifying >40dB at DC and >0dB globally).

## Tools Used

* **Design:** Cadence Virtuoso, TSMC 180nm PDK

* **Simulator:** Spectre

## Reference Textbooks Used
- Analog Integrated Circuit Design, 2nd Edition (Tony Chan Carusone, David A. Johns,Kenneth W. Martin) - Chapter 7
- CMOS Analog Circuit Design, 3rd Edition ( Phillip E. Allen,  Douglas R. Holberg) - Section 5.2.7
- Design of Analog CMOS Integrated Circuits, 2nd Edition (Behzad Razavi) - Chapter 5,10,12

## Designer

* Madhan Sai Krishna