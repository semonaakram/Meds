# Lecture 5 and Lecture 6 Notes

---

## Lecture 5 — HDL: Verilog II

### Behavioral Modeling
- `always @(*)` for combinational; `always @(posedge clk)` for sequential
- Use `=` (blocking) in combinational blocks; `<=` (non-blocking) in sequential blocks
- Blocking: executes sequentially; Non-blocking: all RHS evaluated first, then assigned simultaneously

### Combinational & Sequential `always` Blocks
```verilog
// Combinational
always @(*) begin
  case (sel)
    2'b00: y = a; 2'b01: y = b; default: y = 0;
  endcase
end

// Sequential (async reset)
always @(posedge clk, posedge reset) begin
  if (reset) q <= 0;
  else       q <= d;
end
```

### FSMs & Parameterized Modules
- Split FSMs into: state register, next-state logic, output logic
- Moore: outputs depend on state only; Mealy: outputs depend on state + inputs
- Use `parameter` for reusable generic modules: `mux #(.WIDTH(16)) inst(...);`



---

## Timing and Verification

### Key Timing Parameters
- **t_setup:** Data stable before clock edge; **t_hold:** Data stable after clock edge
- **t_cq:** Clock-to-Q delay; **t_pd:** Combinational propagation delay


### Verification
| Method | What it checks |
|---|---|
| Functional simulation | Logical correctness, no timing |
| Timing simulation | Gate delays post-synthesis |
| Static Timing Analysis | All paths, setup/hold slack |
| Formal verification | Exhaustive mathematical proof |

---

## Lecture 6 — Sequential Logic

### Latches vs. Flip-Flops
| | D Latch | D Flip-Flop |
|---|---|---|
| Triggered by | Level (CLK=1) | Rising edge |
| Transparent | Yes | No |

- SR Latch: S=R=1 is **forbidden**; D Latch is transparent when CLK=1 → glitches propagate
- D FF = master-slave latch pair; Q changes only at clock edge

### Registers, Shift Registers & Counters
- **Register:** N D flip-flops sharing a clock
- **Shift register:** data shifts one position/cycle; used for serial comms, scan chains
- **Synchronous counter:** all FFs share clock (no ripple); wraps at 2^N

### Synchronizers & FSMs
- Async inputs risk **metastability** → use two-FF synchronizer chain
- FSM state stored in registers; next-state + output logic are combinational
- State encoding options: binary, one-hot, gray code

---
