## 8-Bit Serial Adder (SA-8) | Full Custom VLSI Design

# Overview

This project presents the complete custom VLSI implementation of an 8-Bit Serial Adder (SA-8) designed using Cadence Virtuoso.

The project covers the entire custom IC design flow including transistor-level schematic design, functional verification, physical layout implementation, post-layout extraction (PEX), timing analysis, power analysis, DRC verification, and LVS verification.

The architecture performs serial addition of two 8-bit operands and produces a 9-bit result including carry-out.

## Architecture

The design consists of:

* 17-bit Input SISO Register
* 9-bit Output SISO Register
* 1-bit Full Adder
*  D Flip-Flop
* 2×1 Multiplexer
* OR Gate

The complete addition operation is performed in 35 clock cycles.

## Physical Design Highlights

During post-layout analysis, significant routing parasitics were observed on critical interconnect paths.

To improve performance, routing optimization was performed by refining CLK, CLR, VDD, and GND networks and reducing unnecessary metal overlap. These optimizations reduced extracted parasitic capacitance from approximately 8000 units to around 5500 units while also reducing current consumption.

## Post-Layout Results

| Parameter            | Value      |
| -------------------- | ---------- |
| Minimum Clock Period | 2.08094 ns |
| Maximum Frequency    | 480.55 MHz |
|8-bitFAWorst-Case Delay    | 0.6151 ns  |
| Average Power        | 455.2 µW   |
| Peak Current         | 13.47 mA   |
| Layout Area          | 52,000 µm² |
| DRC Status           | Clean      |
| LVS Status           | Matched    |

## Verification

* DRC Verification Passed
* LVS Verification Passed
* PEX Extraction Completed
* Hold Time Requirements Satisfied
* Post-Layout Timing Verified

## Tools Used

* Cadence Virtuoso
* Cadence Maestro
* Spectre Simulator
* DRC
* LVS

## Team Members

* Om Hirapara
* Aum Bavarva
* Preet Patel

## Acknowledgements

We would like to thank Prof. Biswajit and Prof. Purvi Man for their guidance and support throughout the project.

## Project Report

The complete project report is available below:

📄 [SA8 Post Layout Report](./SA8_Post_Layout_Report.pdf)

