<h2>What is an SoC</h2>
A System-on-Chip (SoC) is an IC or single-die chip that has some different IP cores, that consolidates all the components required for a functional system onto a single chip. It typically includes a central processing unit (CPU), memory, input/output ports, and secondary processing units like graphics processing units (GPUs) or digital signal processors (DSPs). SoCs are designed for specific applications, ranging from smartphones and tablets to embedded systems in cars and medical devices. By integrating multiple functions into a single chip, SoCs reduce size, power consumption, and cost, while improving performance and efficiency. This makes them a cornerstone of modern electronics, particularly in devices where space and energy efficiency are critical
single-die chip that has some different IP cores on it

<H2>VSDBabySoC</H2>



![vsdbabysoc_block_diagram](https://github.com/user-attachments/assets/383c0da4-7c45-4b91-8544-11c2054153e0)

VSDBabySoC is a small,  powerful RISCV-based SoC. The main purpose of the SoC is to test three open-source IP cores together for the first time and calibrate the analog part of it. VSDBabySoC contains one RVMYTH microprocessor, an 8x-PLL to generate a stable clock, and a 10-bit DAC to communicate with other analog devices.
This project demonstrates how these modules are integrated together to form a basic SoC, and focuses on simulating and verifying the design behavior both **before** and **after synthesis**. The goal is to check the functionality and performance of the system through these simulation stages.
## What is RVMYTH

`RISV-V based MYTH ( Microprocessor for you in thirty hour)` core is a simple RISCV-based CPU, introduced in a workshop by RedwoodEDA and VSD. During a 5-day workshop students (including middle-schoolers) managed to create a processor from scratch. The workshop used the TLV for faster development.
RISC -V is a *ISA

     *ISA (Instruction Set Architecture) is a critical concept in computer architecture. It refers to the abstract interface between hardware and software that 
    defines the set of instructions a processor can execute and the way in which software interacts with the processor.
<h3>RISC vs. CISC</h3>

| **Aspect**            | **RISC (Reduced Instruction Set Computing)** | **CISC (Complex Instruction Set Computing)**       |
|------------------------|---------------------------------------------|----------------------------------------------------|
| **Instruction Set**    | Small, simple, and uniform instructions.    | Large and complex instruction set.                |
| **Instruction Execution** | Most instructions execute in a single clock cycle. | Instructions may take multiple clock cycles.      |
| **Instruction Length** | Fixed-length instructions (e.g., 32 bits).  | Variable-length instructions.                     |
| **Complexity**         | Simplifies hardware; complexity moved to software. | Complex hardware to handle intricate instructions. |
| **Examples**           | ARM, RISC-V, MIPS, SPARC.                   | x86, VAX, System/360.                             |
| **Registers**          | More general-purpose registers for computation. | Fewer registers; relies more on memory operations. |
| **Memory Access**      | Load/Store architecture; memory accessed only via specific instructions. | Memory can be accessed directly by many instructions. |
| **Decoding**           | Simple decoding (less hardware required).   | Complex decoding (requires more hardware).        |
| **Performance**        | Optimized for pipelining and parallelism.   | Optimized for code compactness.                   |
| **Power Efficiency**   | Generally more power-efficient.             | Can be less power-efficient.                      |
| **Code Size**          | Larger code size (more instructions needed). | Smaller code size (fewer instructions needed).    |
## What is PLL

A phase-locked loop or PLL is a control system that generates an output signal whose phase is related to the phase of an input signal. PLLs are widely used for synchronization purposes, including clock generation and distribution.

## What is DAC

A digital-to-analog converter or DAC is a system that converts a digital signal into an analog signal. DACs are widely used in modern communication systems enabling the generation of digitally-defined transmission signals. As a result, high-speed DACs are used for mobile communications and ultra-high-speed DACs are employed in optical communications systems.

# VSDBabySoC Modeling
<h3>Whats is Modelling</h3>

- Modelling is the use of physical or logical reprasentation ( basicially the circuits ) to generate data.
- Modeling refers to creating a simplified representation of a system, process, or concept to analyze, understand, predict, or optimize its behavior

![VSDBabySoC_modelling](https://github.com/user-attachments/assets/9eb629fd-b035-49c1-8707-fe95040d3ecd)
  
Here we are going to model and simulate the VSDBabySoC using `iverilog`, then we will show the results using `gtkwave` tool. Some initial input signals will be fed into `vsdbabysoc` module that make the pll start generating the proper `CLK` for the circuit. The clock signal will make the `rvmyth` to execute instructions in its `imem`. As a result the register `r17` will be filled with some values cycle by cycle. These values are used by dac core to provide the final output signal named `OUT`. So we have 3 main elements (IP cores) and a wrapper as an SoC and of-course there would be also a testbench module out there.
### Project Structure
The project is organized in the following way:
- **`src/include/`**: This directory contains **header files** (with `.vh` extension) that define key **macros** and **parameters** for the SoC design. These may include configuration settings like clock frequencies, reset behaviors, or other design-specific constants.
  
- **`src/module/`**: This directory contains the **Verilog files** that define the logic and behavior of the individual modules in the SoC. These include the Verilog code for the RISC-V processor, PLL, DAC, and possibly other supporting modules.

- **`output/`**: The **output directory** is where all the generated files from the compilation and simulation processes will be stored. This includes compiled files, waveform files, and any other results generated from running simulations.

<h3>Modelling 3 main IP core </h3>

- The project involves two key stages of simulation:

1. **Pre-synthesis simulation**: Pre-synthesis occurs before the design is synthesized into a gate-level netlist. The design is described at the Register Transfer Level (RTL), usually in hardware description languages like Verilog.It focuses on simulating the RTL (Register Transfer Level) design to ensure functional correctness.

   
        The design has no information about technology-specific gates or timing delays.
        Power, area, and performance optimizations are not final.
  
3. **Post-synthesis simulation**: This is done after synthesis has been performed and takes into account how the design will behave once it is mapped to the actual hardware (e.g., gates, flip-flops, etc.). It is used to verify that the design will work as intended on actual hardware.



        The design is mapped to specific standard cells from a target library.
        Incorporates physical constraints such as wire delays, gate delays, and setup/hold times.

   
### Simulation Steps
#### Pre-Synthesis Simulation
Run the following command to perform a pre-synthesis simulation:

```tcl
iverilog -o output/pre_synth_sim/pre_synth_sim.out -DPRE_SYNTH_SIM \
    -I src/include -I src/module \
    src/module/testbench.v src/module/vsdbabysoc.v
cd output/pre_synth_sim
./pre_synth_sim.out
```
#### Viewing Waveform in GTKWave
After running the simulation, open the VCD file in GTKWave:
`gtkwave output/pre_synth_sim/pre_synth_sim.vcd`

![rymth new](https://github.com/user-attachments/assets/cda2a0af-b710-4cff-bc4d-e1e2cc5aa243)

**Explanation:**
   - -DPRE_SYNTH_SIM: Defines the PRE_SYNTH_SIM macro for conditional compilation in the testbench.

#### Post-Synthesis Simulation
To run a post-synthesis simulation, use:
```tcl
iverilog -o output/post_synth_sim/post_synth_sim.out -DPOST_SYNTH_SIM \
    -I src/include -I src/module \
    src/module/testbench.v output/synthesized/vsdbabysoc.synth.v
cd output/post_synth_sim
./post_synth_sim.out
```
<h2>Post-Synthesis Simulation (Gate Level Simulation) of BabySoC</h2>

## Setting Up the Environment

1. **Ensure Synopsys Library Compiler (lc_shell) is installed**: Needed for .lib to .db conversions.
2. **Download Required Libraries**: 
   - Use `wget` to download `sky130_fd_sc_hd__tt_025C_1v80.lib` from the [Skywater GitHub repository](https://github.com/efabless/skywater-pdk-libs-sky130_fd_sc_hd/tree/master/timing).

## Steps for Conversion of .lib to .db Files

We need `.db` files for `avsddac`, `avsdpll`, and `sky130_fd_sc_hd__tt_025C_1v80` libraries. Follow these steps:

### Converting `avsddac.lib` to `avsddac.db`

---

`cd Desktop/hemanth/VLSI/VSDBabySOC/src/lib/`

<img width="739" alt="Screenshot 2024-11-08 at 12 12 58 PM" src="https://github.com/user-attachments/assets/6257df5a-5775-45dc-adc9-9d49a949f917">

---

Launch `lc_shell`

<img width="736" alt="Screenshot 2024-11-08 at 12 13 45 PM" src="https://github.com/user-attachments/assets/1ded9195-26bc-46f6-bab3-b68618b7fde3">

---

Reading avsddac library `read_lib avsddac.lib`
<img width="879" alt="Screenshot 2024-11-08 at 12 27 30 PM" src="https://github.com/user-attachments/assets/27e09272-de9b-47d7-b4c0-bfec5344352b">

---

writing  .db file `write_lib avsddac -format db -output avsddac.db`

<img width="881" alt="Screenshot 2024-11-08 at 12 24 58 PM" src="https://github.com/user-attachments/assets/3a41681b-6dc7-4764-a3f1-ceedd29608a1">

---

### Converting `avsdpll.lib` to `avsdpll.db`

---

`cd Desktop/hemanth/VLSI/VSDBabySOC/src/lib/`

<img width="739" alt="Screenshot 2024-11-08 at 12 12 58 PM" src="https://github.com/user-attachments/assets/6257df5a-5775-45dc-adc9-9d49a949f917">

---

Launch `lc_shell`

<img width="736" alt="Screenshot 2024-11-08 at 12 13 45 PM" src="https://github.com/user-attachments/assets/1ded9195-26bc-46f6-bab3-b68618b7fde3">

---

Reading avsdpll library `read_lib avsdpll.lib`

<img width="849" alt="Screenshot 2024-11-08 at 12 30 25 PM" src="https://github.com/user-attachments/assets/460d4dd9-9a34-4709-92d1-b96f8f0fd1cc">

---

Writing .db file `write_lib avsdpll -format db -output avsdpll.db`

<img width="845" alt="Screenshot 2024-11-08 at 12 31 36 PM" src="https://github.com/user-attachments/assets/0d554a72-714f-463a-b72c-8c987dee1b12">

---

### Converting sky130_fd_sc_hd__tt_025C_1v80.lib to sky130_fd_sc_hd__tt_025C_1v80.db

---

First, download the .lib file

`wget https://raw.githubusercontent.com/efabless/skywater-pdk-libs-sky130_fd_sc_hd/master/timing/sky130_fd_sc_hd__tt_025C_1v80.lib`

---

`cd Desktop/hemanth/VLSI/VSDBabySOC/src/lib/`

<img width="739" alt="Screenshot 2024-11-08 at 12 12 58 PM" src="https://github.com/user-attachments/assets/6257df5a-5775-45dc-adc9-9d49a949f917">

---

Launch `lc_shell`

<img width="736" alt="Screenshot 2024-11-08 at 12 13 45 PM" src="https://github.com/user-attachments/assets/1ded9195-26bc-46f6-bab3-b68618b7fde3">

---

Reading sky130_fd_sc_hd__tt_025C_1v80 library `read_lib sky130_fd_sc_hd__tt_025C_1v80.lib`

<img width="740" alt="Screenshot 2024-11-08 at 12 35 50 PM" src="https://github.com/user-attachments/assets/784655f2-6ecd-462c-922a-db7da234e2f1">

---

Writing .db file `write_lib sky130_fd_sc_hd__tt_025C_1v80 -format db -output sky130_fd_sc_hd__tt_025C_1v80.db`

<img width="1366" alt="Screenshot 2024-11-08 at 12 37 59 PM" src="https://github.com/user-attachments/assets/3493c817-12e6-4ba7-9cc4-29a9a504c38c">

---

## Running Synthesis and GLS

After setting up the libraries, proceed with synthesis and GLS.

### Synthesis

---

`cd Desktop/hemanth/VLSI/VSDBabySOC/src/lib/`

<img width="739" alt="Screenshot 2024-11-08 at 12 12 58 PM" src="https://github.com/user-attachments/assets/6257df5a-5775-45dc-adc9-9d49a949f917">

---

Launch `dc_shell`

<img width="1371" alt="Screenshot 2024-11-08 at 12 40 06 PM" src="https://github.com/user-attachments/assets/bc412639-c9e2-44d8-94e5-9fd0ae185eae">

---

`set target_library /home/bhaskar/vsd/VSDBabySOC/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.db`

<img width="1002" alt="Screenshot 2024-11-08 at 12 30 49 AM" src="https://github.com/user-attachments/assets/f78b96ac-823b-496c-b1c3-3a9317fba1a3">

---

`set link_library {* /home/bhaskar/vsd/VSDBabySOC/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.db /home/bhaskar/vsd/VSDBabySOC/VSDBabySoC/src/lib/avsdpll.db /home/bhaskar/vsd/VSDBabySOC/VSDBabySoC/src/lib/avsddac.db}`

<img width="1440" alt="Screenshot 2024-11-08 at 12 31 29 AM" src="https://github.com/user-attachments/assets/8fb0f3e5-369b-4d58-a050-5df452e1bb87">

---

`set search_path {/home/bhaskar/vsd/VSDBabySOC/VSDBabySoC/src/include /home/bhaskar/vsd/VSDBabySOC/VSDBabySoC/src/module}`

<img width="1440" alt="Screenshot 2024-11-08 at 12 31 41 AM" src="https://github.com/user-attachments/assets/a8bea31f-f957-4e8c-8f7e-ee751f2d575b">

---

`read_file {sandpiper_gen.vh  sandpiper.vh  sp_default.vh  sp_verilog.vh clk_gate.v rvmyth.v rvmyth_gen.v vsdbabysoc.v} -autoread -top vsdbabysoc`

<img width="1440" alt="Screenshot 2024-11-08 at 12 40 01 AM" src="https://github.com/user-attachments/assets/8d2512d6-200d-4053-88a1-0cef7f25fb95">

Statistics for MUX_OPs

<img width="718" alt="Screenshot 2024-11-08 at 12 43 37 AM" src="https://github.com/user-attachments/assets/2bdd1d49-96b2-4902-a77c-c1af4bd03b0f">

---

`link`

<img width="1123" alt="Screenshot 2024-11-08 at 12 43 44 AM" src="https://github.com/user-attachments/assets/ad81ef9d-9a39-4deb-a057-524f94ac781a">

---

`compile_ultra`

<img width="1157" alt="Screenshot 2024-11-08 at 12 44 06 AM" src="https://github.com/user-attachments/assets/fa786166-2502-4ef8-958a-39373eb15b83">

<img width="928" alt="Screenshot 2024-11-08 at 12 44 44 AM" src="https://github.com/user-attachments/assets/bfaff94f-a8a8-41c3-b134-6b279fa16339">

<img width="966" alt="Screenshot 2024-11-08 at 12 46 58 AM" src="https://github.com/user-attachments/assets/f1259856-decb-4364-8a4b-7e9c4210d46b">

---

`write_file -format verilog -hierarchy -output /home/bhaskar/vsd/VSDBabySOC/VSDBabySoC/output/vsdbabysoc_net.v`

<img width="1112" alt="Screenshot 2024-11-08 at 12 47 38 AM" src="https://github.com/user-attachments/assets/b2de7330-208f-456f-9025-161f6b77e253">

---

`report_qor > report_qor.txt`

<img width="337" alt="Screenshot 2024-11-08 at 12 53 03 AM" src="https://github.com/user-attachments/assets/65dc9f04-35d3-43b3-aabb-69e45a1a2cf2">

<img width="573" alt="Screenshot 2024-11-08 at 12 53 23 AM" src="https://github.com/user-attachments/assets/27ca650d-1379-490e-b37a-65f0ceaf14d4">

---

## Post-Synthesis Simulation

---

`iverilog -DFUNCTIONAL -DUNIT_DELAY=#1 -o ./output/post_synth_sim.out ./src/gls_model/primitives.v ./src/gls_model/sky130_fd_sc_hd.v ./output/vsdbabysoc_net.v ./src/module/avsdpll.v ./src/module/avsddac.v ./src/module/testbench.v`

<img width="1440" alt="Screenshot 2024-11-08 at 12 50 03 AM" src="https://github.com/user-attachments/assets/3c752e3c-578a-4f0f-89ec-d0e6cc5eaa4e">

---
Debug the errors
---

`./post_synth_sim.out`

<img width="437" alt="Screenshot 2024-11-08 at 12 50 24 AM" src="https://github.com/user-attachments/assets/da6b1b6f-fc58-4aea-909f-0e44d2dc1870">

----

gtkwave dump.vcd

<img width="1003" alt="Screenshot 2024-11-08 at 12 23 24 AM" src="https://github.com/user-attachments/assets/05bf53de-860d-49c0-ae15-eb4f15cfb384">

---

Verify Pre-Synthesis vs Post-Synthesis

<img width="544" alt="Screenshot 2024-11-08 at 12 56 27 PM" src="https://github.com/user-attachments/assets/40470752-b8ed-4381-9c6a-60682739ef38">

---



