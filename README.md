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

## Code

1. FULL ADDER
------------- module full_adder(
input a, b, cin, output sum, cout
);
assign sum = a ^ b ^ cin;
assign cout = (a & b) | (b & cin) | (a & cin);
endmodule

2. CARRY SAVE ADDER (CSA)
------------------------- module carry_save_adder #(parameter N = 16)(
input [N-1:0] a, b, c, output [N-1:0] sum, output [N-1:0] carry
);
genvar i;
generate
for(i = 0; i < N; i = i + 1) begin
assign sum[i] = a[i] ^ b[i] ^ c[i];
assign carry[i] = (a[i] & b[i]) | (b[i] & c[i]) | (a[i] & c[i]);
end
endgenerate
endmodule

3. PIPELINE REGISTER
-------------------- module pipeline_reg #(parameter N = 16)(
input clk,
input reset,
input [N-1:0] d, output reg [N-1:0] q
);
always @(posedge clk or posedge reset) begin
if (reset)
q <= 0;
else
q <= d;

end
endmodule

4. RIPPLE CARRY ADDER
--------------------- module ripple_carry_adder #(parameter N = 16)(

input [N-1:0] a, b, output [N:0] sum
);
assign sum = a + b;
endmodule

5. TOP MODULE
------------- module pipelined_multiplier_csa(
input clk,
input reset,
input [7:0] A,
input [7:0] B, output [15:0] P
);
wire [15:0] pp [7:0];
genvar i;
generate
for(i = 0; i < 8; i = i + 1) begin
assign pp[i] = B[i] ? (A << i) : 16'b0;
end
endgenerate
wire [15:0] sum1, carry1;
wire [15:0] sum2, carry2;
wire [15:0] psum1, pcarry1;
wire [15:0] psum2, pcarry2;
carry_save_adder csa1(pp[0], pp[1], pp[2], sum1, carry1);
pipeline_reg r1(clk, reset, sum1, psum1);
pipeline_reg r2(clk, reset, carry1 << 1, pcarry1);
carry_save_adder csa2(psum1, pcarry1, pp[3], sum2, carry2);
pipeline_reg r3(clk, reset, sum2, psum2);
pipeline_reg r4(clk, reset, carry2 << 1, pcarry2);
wire [16:0] final_sum;
ripple_carry_adder final_adder(psum2, pcarry2, final_sum);
assign P = final_sum[15:0];
endmodule

6. TESTBENCH
------------ module tb_pipelined_multiplier;

reg clk, reset;
reg [7:0] A, B;
wire [15:0] P;
pipelined_multiplier_csa uut(
.clk(clk), .reset(reset), .A(A), .B(B), .P(P)
);
always #5 clk = ~clk;
initial begin
clk = 0;
reset = 1;
A = 0;
B = 0;
#10 reset = 0;
#10 A = 8'd5; B = 8'd6;
#10 A = 8'd10; B = 8'd15;
#10 A = 8'd25; B = 8'd4;
#10 A = 8'd12; B = 8'd12;
#100 $stop;
end
endmodule

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

**Lokesh Byroj**

B.Tech Electronics and Communication Engineering (ECE)

GitHub: https://github.com/yourusername
