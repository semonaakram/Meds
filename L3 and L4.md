# Digital Design and Computer Architecture (DDCA)
## Lecture 3 & 4 — Summary Notes

---

#  Lecture 3: Sequential Logic

##  Definition
- Output depends on:
  - Current input  
  - **Previous state (memory)** 0  

##  Key Components
- Latches  
- Flip-Flops (D, JK, T)  
- Registers  

##  Important Concepts
- Clock signal (synchronization)  
- Synchronous vs Asynchronous circuits  
- State = stored information  

##  Key Idea
- Sequential circuits use **memory elements (flip-flops)** to store data and control behavior 1  

---

#  Lecture 4: Sequential Logic II 

##  Finite State Machines (FSM)
- System with **finite states + transitions** 2  

##  FSM Components
- States  
- Inputs  
- Outputs  
- Next-state logic  
- State register  

##  Types
- **Moore Machine** → Output depends on state  
- **Mealy Machine** → Output depends on state + input  

##  Design Steps
1. State diagram  
2. State table  
3. Implementation  


## FPGAs

### What is FPGA?
- Reconfigurable digital hardware  

##  Key Components
- LUTs (Look-Up Tables)  
- Flip-Flops  
- Routing network  

##  Advantages
- Parallel processing  
- Flexible design  
- Fast prototyping  


## Verilog (HDL Basics)

### What is Verilog?
- Hardware Description Language for digital design  

###  Basic Example
```verilog
module example(input clk, d, output reg q);
  always @(posedge clk)
    q <= d;
endmodule
