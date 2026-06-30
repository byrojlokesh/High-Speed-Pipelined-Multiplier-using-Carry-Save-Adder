# High-Speed-Pipelined-Multiplier-using-Carry-Save-Adder
High-Speed Pipelined Multiplier using Carry Save Adder (CSA) implemented in Verilog HDL. The project improves multiplication speed by reducing carry propagation delay through CSA-based reduction and pipelining. Developed as a B.Tech major project and verified using Xilinx Vivado.


# High Speed Pipelined Multiplier Using Carry Save Adder

## Overview

This project presents the design and implementation of a High-Speed Pipelined Multiplier using Carry Save Adders (CSA). The multiplier is designed to reduce propagation delay and improve throughput by combining Carry Save Addition with pipelining techniques.

The project was developed as my B.Tech Major Project using Verilog HDL and simulated using Xilinx Vivado.

---

## Objectives

- Design a high-speed multiplier architecture.
- Reduce critical path delay using Carry Save Adders.
- Improve throughput through pipelining.
- Verify functionality using simulation.
- Compare performance with conventional multiplier architectures.

---

## Features

- High-speed multiplication
- Carry Save Adder (CSA) based reduction tree
- Pipeline registers for higher operating frequency
- Verilog HDL implementation
- Simulation using Xilinx Vivado
- Synthesizable RTL design

---

## Architecture

The multiplier consists of the following stages:

1. Partial Product Generation
2. Carry Save Adder Reduction
3. Pipeline Registers
4. Final Carry Propagate Adder (CPA)
5. Product Generation

---

## Project Structure

```
├── RTL/
│   ├── csa.v
│   ├── full_adder.v
│   ├── pipelined_multiplier.v
│   └── top_module.v
│
├── Testbench/
│   └── multiplier_tb.v
│
├── Simulation/
│   ├── waveform.png
│   └── simulation_results.png
│
├── Documentation/
│   ├── project_report.pdf
│   ├── architecture.png
│   └── block_diagram.png
│
└── README.md
```

---

## Tools Used

- Verilog HDL
- Xilinx Vivado
- FPGA Design Flow
- Digital Logic Design

---

## Simulation Results

The design was simulated successfully in Xilinx Vivado.

Example:

| Input A | Input B | Product |
|----------|----------|----------|
| 25 | 13 | 325 |
| 89 | 123 | 10947 |
| 150 | 200 | 30000 |

---

## Advantages

- Reduced carry propagation delay
- Increased operating frequency
- High throughput
- Suitable for DSP applications
- Efficient VLSI implementation

---

## Applications

- Digital Signal Processing (DSP)
- Arithmetic Logic Units (ALU)
- Image Processing
- Communication Systems
- Embedded Systems

---

## Future Improvements

- Wallace Tree Multiplier implementation
- Booth Multiplier optimization
- FPGA implementation and timing analysis
- ASIC synthesis

---

## Author

**Vamsi Kasi**

B.Tech Electronics and Communication Engineering (ECE)

GitHub: https://github.com/yourusername
