# India_RISC-V_Chip_Tapeout_Program
	
# Day 0 - Digital VLSI SOC Design and Planning
## Overview
### Phase 1: Chip Modeling and Specification

The initial phase focuses on creating a high-level, abstract representation of the chip's functionality. Here we define what the chip needs to do before we start hardware design.

* **O0 (GCC output):** This represents the chip's expected behavior as a software model, compiled using a tool **GCC**. A **testbench**, written in C, runs tests on this model.
* **O1 (Specs C model):** This is a more detailed software model of the chip, following the design specifications. The key goal is to ensure that **O0 = O1**, meaning the high-level C model matches the expected behavior from the compiled code. This step ensures functional correctness at the top level of abstraction.

---

### Phase 2: RTL Architecture 

After verifying the C models, the design moves to the Register-Transfer Level (RTL) architecture. This marks the first step in translating the software model into a hardware description.

* **O2 (Soft copy of Hardware using RTL):** This is the **RTL code**, usually written in a Hardware Description Language (HDL) like Verilog. This code describes digital logic, processors, peripherals, and IP blocks. The testbench is used again to verify that the RTL output (**O2**) matches the behavior of the C model (**O1**). At this stage, we check that **O1 = O2**.

---

### Phase 3: Synthesis and SoC Integration 

Synthesis involves converting the abstract RTL code into a physical representation of the hardware. This phase solidifies the design for a specific technology.

* **O3 (SoC Integration):** This is the **gate-level netlist**, which is a list of all the logic gates and their interconnections. It is generated from the RTL code through **synthesis**. The design integrates with other components, including hard macros and analog IPs. The goal is to ensure that the integrated design (**O3**) still functions as intended, verifying that **O2 = O3**. This step is crucial for confirming that the physical implementation matches the behavioral RTL model.

---

### Phase 4: Physical Implementation and GDSII 

This final phase prepares the design for manufacturing. The synthesized netlist translates into a physical layout.

* **O4 (Layout):** This is the final **GDSII** (Graphic Data System II) file. It includes the complete physical layout of the chip, such as floorplanning, placement, clock tree synthesis (CTS), and routing. This file is sent to the foundry for fabrication. The design is verified against the netlist to ensure that **O3 = O4**. This often occurs through **DRC** (Design Rule Checking) and **LVS** (Layout Versus Schematic) checks to ensure the physical layout accurately represents the schematic and adheres to manufacturing rules.
* **Final Verification:** The entire flow is a continuous verification process, where the output of each stage is checked against the previous one. The ultimate goal is to ensure that **O1 = O2 = O3 = O4**.
* **Applications:** The final manufactured chip can be used in many products, like smartwatches, Arduino boards, TV panels, and air conditioning applications. The chip's operating frequency can be optimized for specific uses.
