# SA-8: 8-Bit Serial Adder — Full Custom VLSI Layout

Full custom VLSI implementation of an 8-bit serial adder using **Cadence Virtuoso**, completed as part of Digital IC Design coursework at **Dhirubhai Ambani University (DA-IICT)**.

> ✅ DRC Clean | ✅ LVS Matched | ✅ Post-Layout RC Extraction & Simulation Complete

-----

## Project Overview

The SA-8 serially computes the sum of two 8-bit operands in **35 clock cycles**, producing a 9-bit result (8 sum bits + carry-out). All cells were designed from scratch — transistor level up to top-level integration.

-----

## Key Results

|Parameter                   |Value                       |
|----------------------------|----------------------------|
|Layout Area                 |400 µm × 130 µm = 52,000 µm²|
|Max Operating Frequency     |480.55 MHz                  |
|Min Clock Period            |2.08094 ns                  |
|Average Power (Random Input)|455.2 µW                    |
|Peak Supply Current         |13.47 mA                    |
|Energy per 8-bit Addition   |0.318 nJ                    |
|DRC Violations              |0                           |
|LVS Status                  |Matched                     |

-----

## Architecture

Three principal blocks connected through a 1-bit full adder and a 2×1 MUX:

- **17-bit Input SISO** — loads A[7:0], B[7:0], and Cin serially over 17 cycles
- **Datapath Cell** — OR gate + 1-bit Full Adder + MUX 2×1 + Carry D Flip-Flop
- **9-bit Output SISO** — captures 8 SUM bits + COUT, shifts out serially

### Operation Phases (35 Clock Cycles)

|Phase|Description          |Cycles|
|-----|---------------------|------|
|1    |Serial input loading |1–17  |
|2    |Addition, SUM capture|18–25 |
|3    |Carry capture        |26    |
|4    |Serial output        |27–35 |

-----

## Sub-Modules Designed (Transistor Level)

- D Flip-Flop (NAND-based, positive edge-triggered)
- MUX 2×1
- OR Gate
- 1-bit Full Adder
- 17-bit Input SISO Shift Register
- 9-bit Output SISO Shift Register
- Datapath Cell (hierarchical layout block)

-----

## Layout Strategy

Two placement strategies were evaluated. The **4-column layout** was selected:

- Folded 17-bit SISO into rows of 4 D-FFs
- Achieved compact 400 µm × 130 µm footprint
- Routing optimization reduced parasitic capacitance by ~40% (8000 → 4800 units)

-----

## Pre vs. Post-Layout Comparison

|Parameter       |Pre-Layout|Post-Layout|Delta      |
|----------------|----------|-----------|-----------|
|Max Frequency   |602.93 MHz|480.55 MHz |−122.38 MHz|
|Min Clock Period|1.659 ns  |2.081 ns   |+0.422 ns  |
|Average Power   |274.7 µW  |455.2 µW   |+65.7%     |
|Output Delay    |530.47 ns |530.64 ns  |+0.17 ns   |

Power increase (~66%) is expected due to routing parasitics across 27 flip-flop stages.

-----

## Tools Used

- **Cadence Virtuoso** — Schematic, Layout, ADE Simulation
- **Virtuoso DRC/LVS** — Physical verification
- **Spectre** — Post-layout transient, timing, and power simulation

-----

## Team

|Name       |Roll No. |Contributions                                                                     |
|-----------|---------|----------------------------------------------------------------------------------|
|Aum Bavarva|202404004|Architecture, schematics, timing analysis, D-FF layout, 4-column floorplan        |
|Om Hirapara|202404011|Physical layout, 17-bit SISO layout, Full Adder layout, CLK/reset routing, DRC/LVS|
|Preet Patel|202404027|Architecture, 9-bit SISO layout, CLK/CLR routing optimization, report             |

**Institution:** Dhirubhai Ambani University (formerly DA-IICT), Gandhinagar  
**Course:** ED312 — Digital IC Design
