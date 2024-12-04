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



