# 6T SRAM Performance Analysis

A circuit-level performance analysis of the conventional **6-Transistor (6T) SRAM cell**, carried out in SPICE/Cadence-based simulation. The project evaluates the cell's stability, speed, and power characteristics, and studies low-power design techniques such as **header/footer switches** and the **stacking effect**.

## Overview

The 6T SRAM cell is the fundamental building block of on-chip cache memory, built from two cross-coupled inverters (4 transistors) and two access transistors connected to the bit lines. This project analyzes the cell's read, write, and hold behavior, quantifies its static noise margin, and explores circuit-level techniques to reduce leakage power without significantly degrading speed.

![6T SRAM Cell](6T%20SRAM%20Cell.jpeg)

## Key Analyses

### 1. Static Noise Margin (SNM)
Noise margin was measured using the butterfly curve method across the three operating conditions:
- **Hold condition** — stability while the cell retains data
- **Read condition** — stability during a read access (most noise-critical)
- **Write condition** — stability during a write operation

| Hold | Read | Write |
|---|---|---|
| ![SNM Hold](SNM%20-%20Hold%20condition.jpeg) | ![SNM Read](SNM%20-%20Read%20condition.jpeg) | ![SNM Write](SNM%20-%20Write%20condition.jpeg) |

The butterfly curve construction used to extract SNM is shown below:

![Butterfly Curve](Stattic%20noise%20margin%20-%20butterfly%20curve.jpeg)

### 2. Low-Power Techniques: Header/Footer Switches & Stacking Effect
To reduce leakage (static) power, PMOS **header switches** and NMOS **footer switches** were added to gate the SRAM cell's supply/ground path, along with an evaluation of the **stacking effect** (using two series transistors to exponentially suppress sub-threshold leakage).

| Header Switch | Footer Switch | Header + Footer Switch |
|---|---|---|
| ![Header Switch](Header%20Switch.jpeg) | ![Footer Switch](Footer%20Switch.jpeg) | ![Header and Footer Switch](Header%20and%20Footer%20Switch.jpeg) |

![Stacking Effect](Stacking%20Effect.jpeg)

Power was compared before and after applying the stacking effect:

| Before Stacking | After Stacking |
|---|---|
| ![Power before stacking](Power%20analysis%20before%20stacking%20effect.jpeg) | ![Power after stacking](Power%20Analysis%20after%20Stacking%20effect.jpeg) |

The combined impact of the header/footer switches on SNM was also verified:

![SNM Header Footer](SNM%20-%20Header%20-%20Footer.jpeg)

### 3. Read/Write Delay & Transient Analysis
Timing performance was characterized through transient simulation, measuring read delay, write delay, and overall signal propagation through the cell.

| Read Delay | Write Delay |
|---|---|
| ![Read Delay](Read%20delay.jpeg) | ![Write Delay](Write%20delay%20.jpeg) |

![Transient Analysis](Transient%20Analysis.jpeg)
![6T SRAM Time Delay](6T%20SRAM%20time%20delay.jpeg)

### 4. Sense Amplifier
A sense amplifier was designed and simulated to amplify the small differential voltage on the bit lines during a read operation into a full logic-level output.

| Sense Amplifier Circuit | Sense Amplifier Result |
|---|---|
| ![Sense Amplifier](Sense%20Amplifier.jpeg) | ![Sense Amplifier Result](Sense%20Amplifier%20result.jpeg) |

## Repository Contents

| File | Description |
|---|---|
| `6T SRAM PERFORMANCE ANALYSIS REPORT.pdf` | Full project report with methodology, simulation setup, and results |
| `6T SRAM PROJECT PRESENTATION.pdf` | Presentation slides summarizing the project |
| `*.jpeg` | Simulation waveforms and circuit schematics referenced throughout the report |

## Tools Used
- SPICE-based circuit simulator (Cadence Virtuoso / LTspice-class tool)
- Transient and DC analysis for delay, SNM, and power measurements

## Summary of Findings
- Header and footer switches reduce static leakage power at the cost of a small increase in access delay.
- The stacking effect further suppresses leakage current with minimal additional area overhead.
- SNM is lowest during the read operation, confirming it as the critical stability constraint in 6T SRAM design.
- The designed sense amplifier reliably resolves the bit-line differential into a valid logic output within the simulated timing budget.

## Author
Kankana
