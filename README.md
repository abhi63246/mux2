![](../../workflows/gds/badge.svg) ![](../../workflows/docs/badge.svg) ![](../../workflows/test/badge.svg) ![](../../workflows/fpga/badge.svg)

# Mod-6 Counter (TinyTapeout Project)

## Design Name
**3-bit Mod-6 Counter**

---

## Working
This project implements a **synchronous 3-bit Modulo-6 counter**.  
- The counter increments on each **rising edge** of the clock (`clk`).  
- When the counter reaches **5 (`101`)**, it wraps back to **0** on the next clock cycle.  
- An **active-low reset (`rst_n`)** resets the counter to 0.  
- The output is connected to the **TinyTapeout user outputs (`uo_out[2:0]`)**, while unused IOs are tied low.

---

## Waveform
Example simulation waveform:


*(You can generate and view this waveform using GTKWave with the provided testbench.)*

---

## Block Diagram
     +-------------------------+
clk --->| |
rst_n -->| 3-bit Counter (Mod-6) |---> uo_out[2:0]
| |
+-------------------------+

---

## IO’s

| Signal        | Direction | Width | Description                                |
|---------------|-----------|-------|--------------------------------------------|
| `clk`         | Input     | 1     | Clock signal                               |
| `rst_n`       | Input     | 1     | Active-low reset (synchronous)             |
| `ena`         | Input     | 1     | Enable signal (from TinyTapeout harness)   |
| `ui_in`       | Input     | 8     | Unused (set to 0)                          |
| `uio_in`      | Input     | 8     | Unused                                     |
| `uio_out`     | Output    | 8     | Unused                                     |
| `uio_oe`      | Output    | 8     | Unused                                     |
| `uo_out[2:0]` | Output    | 3     | Counter output (binary value 0–5)          |
| `uo_out[7:3]` | Output    | 5     | Unused (set to 0)                          |

---

## How to Test
1. **Simulation:**
   - Run the testbench (`tb.v`) in a Verilog simulator (Icarus, Verilator, etc.).
   - Open the output VCD file in GTKWave.
   - Verify that the output counts `0 → 5 → 0`.

2. **On TinyTapeout Hardware:**
   - Apply a clock signal to `clk`.
   - Keep `rst_n = 1` to allow counting.
   - Observe the counter output on `uo_out[2:0]` (can connect LEDs).

---

## External Hardware
- **None required.**  
- Optional:  
  - **3 LEDs** on `uo_out[2:0]` to visualize the count.  
  - Logic analyzer to capture output transitions.

---
