<h2>What is an SoC</h2>
A System-on-Chip (SoC) is an IC or single-die chip that has some different IP cores, that consolidates all the components required for a functional system onto a single chip. It typically includes a central processing unit (CPU), memory, input/output ports, and secondary processing units like graphics processing units (GPUs) or digital signal processors (DSPs). SoCs are designed for specific applications, ranging from smartphones and tablets to embedded systems in cars and medical devices. By integrating multiple functions into a single chip, SoCs reduce size, power consumption, and cost, while improving performance and efficiency. This makes them a cornerstone of modern electronics, particularly in devices where space and energy efficiency are critical
single-die chip that has some different IP cores on it
<H2>VSDBabySoC</H2>
VSDBabySoC is a small,  powerful RISCV-based SoC. The main purpose of the SoC is to test three open-source IP cores together for the first time and calibrate the analog part of it. VSDBabySoC contains one RVMYTH microprocessor, an 8x-PLL to generate a stable clock, and a 10-bit DAC to communicate with other analog devices.
This project demonstrates how these modules are integrated together to form a basic SoC, and focuses on simulating and verifying the design behavior both **before** and **after synthesis**. The goal is to check the functionality and performance of the system through these simulation stages.

### Project Structure
The project is organized in the following way:
- **`src/include/`**: This directory contains **header files** (with `.vh` extension) that define key **macros** and **parameters** for the SoC design. These may include configuration settings like clock frequencies, reset behaviors, or other design-specific constants.
  
- **`src/module/`**: This directory contains the **Verilog files** that define the logic and behavior of the individual modules in the SoC. These include the Verilog code for the RISC-V processor, PLL, DAC, and possibly other supporting modules.

- **`output/`**: The **output directory** is where all the generated files from the compilation and simulation processes will be stored. This includes compiled files, waveform files, and any other results generated from running simulations.
