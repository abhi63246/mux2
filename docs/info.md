<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

This project implements a 3-bit Mod-6 synchronous counter.

The counter increments on every rising edge of the clock (clk).

It counts through the sequence 0 → 1 → 2 → 3 → 4 → 5 → 0 → … and repeats.

When the reset (rst_n) is asserted low, the counter is cleared back to 0.

The current counter value is driven on the lowest 3 output bits (uo[2:0]), while the other output pins are held at 0.

## How to test

Provide a clock signal to clk (default 1 MHz from TinyTapeout harness).

Hold rst_n = 0 for a few cycles to reset, then release (rst_n = 1).

Observe outputs:

uo[0] = Least Significant Bit (LSB) of the counter

uo[1] = Middle bit

uo[2] = Most Significant Bit (MSB) of the counter

The binary pattern on uo[2:0] should follow the sequence:

000 → 001 → 010 → 011 → 100 → 101 → 000 → …


You can use a logic analyzer or LEDs connected to uo[0..2] to see the counting in real time.

## External hardware

None required.

Optional: You can connect LEDs to uo[0], uo[1], and uo[2] to visually see the counter cycling through values.
