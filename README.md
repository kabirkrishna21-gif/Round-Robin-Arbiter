# Round-Robin-Arbiter


Round Robin Arbiter (RTL Design in Verilog)
Project Overview

Designed and implemented a synthesizable 4-request Round Robin Arbiter in Verilog HDL to ensure fair and starvation-free resource allocation through rotating priority arbitration. Verified functionality using a custom testbench and behavioral simulation in AMD Vivado (XSim).

Key Features:-
4-request arbitration (req0–req3)
Fair round-robin scheduling
Starvation-free grant mechanism
Synchronous clocked RTL design
Active-high reset support
Behavioral simulation in Vivado
Waveform-based functional verification
Design Architecture

Inputs
clk — System clock
rst — Active-high reset
req0–req3 — Request signals from four clients
Outputs
gnt0–gnt3 — Grant signals indicating the selected requester
Internal Logic

The arbiter uses:

Latched grant registers (lgnt0–lgnt3)
Encoded grant tracking (lgnt[1:0])
Rotating mask registers (lmask1, lmask0)
Bus occupancy detection (lcomreq)
Sequential grant update logic driven by the system clock
Working Principle
Request signals are sampled on the rising edge of the clock.
The arbiter checks all active requests.
Priority starts from the requester following the previously granted requester.
The first valid request receives the grant.
The priority mask is updated to rotate the grant order for the next arbitration cycle.

This ensures that when multiple requests are asserted simultaneously, access is distributed fairly across all requesters.


Verification
A dedicated Verilog testbench (tb_arbiter.v) was created to validate:

Reset behavior
Single-request grants
Multiple simultaneous requests
Grant rotation across requesters
Correct round-robin fairness

The simulation waveform confirms proper arbitration and sequential grant allocation.
