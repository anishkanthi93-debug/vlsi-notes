# Day 1 (27 Oct 2026)
1. `always @(posedge clk or negedge rst_n)` means "run this block whenever the clock rises OR the reset falls". posedge = rising edge (0 to 1), negedge = falling edge (1 to 0). Because reset is in the list, the reset works immediately (asynchronous) without waiting for a clock edge. The `_n` means active-low: reset is active when rst_n is 0.

2. A design needs a reset because flip-flops power up with unknown values. Reset forces every register into a known starting state, so the circuit behaves the same way every time.

3. With no reset, q stayed X (unknown) the whole run. The counter computes q + 1, and unknown + 1 is still unknown, so it never got a real value to start counting from.

4. A testbench is code that runs only in simulation. It has no hardware equivalent. Mine generates a clock, holds reset low then releases it, turns the enable on and off, connects to the counter and mux, and writes the signal changes to wave.vcd so I can view them in Surfer.

5. The hardest part of setup was fixing the broken line in .zshrc (a path with spaces and no quotes), then setting up Homebrew's PATH so the terminal could find the tools, and finding a waveform viewer that works on an M2.
