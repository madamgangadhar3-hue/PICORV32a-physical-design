# PicoRV32a Physical Design

## Overview
This repository contains the final physical design layout and signoff reports for the **PicoRV32a** microprocessor, synthesized and routed using the open-source **OpenLane** RTL-to-GDSII flow and the **SkyWater 130nm** Process Design Kit (PDK).

## Project Highlights
* **High Routing Success:** Achieved a **99.98%** successful routing rate with only **2** remaining antenna violations out of over 18,600 nets.
* **Perfect Timing:** Successfully met all setup and hold timing constraints with a final setup slack of **13.227 ns**.
* **Optimized Floorplan:** Iteratively tuned the core utilization and aspect ratio to ensure maximum standard cell density without causing OpenROAD routing congestion.

## Key Specifications
* **Core Design:** PicoRV32a (32-bit RISC-V CPU core)
* **Technology Node:** SkyWater 130nm (`sky130_fd_sc_hd`)
* **EDA Toolchain:** OpenLane (incorporating Yosys, OpenROAD, Magic, KLayout, and OpenSTA)

## Repository Contents
* `/results/` - Contains the physical layout databases.
  * `signoff/picorv32a.gds` - The final GDSII layout geometry.
  * `routing/picorv32a.def` - The Design Exchange Format (DEF) coordinate data.
  * `routing/picorv32a.odb` - The OpenROAD GUI database.
* `/reports/` - Contains all verification, synthesis, and timing logs.
  * `manufacturability.rpt` - Final DRC, LVS, and Antenna checks.
  * `signoff/` - Final Static Timing Analysis (STA) reports proving the chip's operating frequency.

## How to View the Layouts
You can inspect the microscopic manufacturing layout (GDS) or interact with the routing database (ODB) directly from the project root using the following commands:

```bash
# To view the final manufacturing geometry (GDSII)
klayout results/signoff/picorv32a.gds

# To view routing tracks, clock trees, and debug the 2 antenna violations
openroad -gui results/routing/picorv32a.odb
