# DFF UVM Testbench

This repository contains a **SystemVerilog UVM-style testbench** for a simple **D Flip-Flop (DFF)** design. The testbench demonstrates functional verification using transactions, generator, driver, monitor, scoreboard, and coverage.

---

## Table of Contents
- [Design Overview](#design-overview)
- [Architecture](#architecture)
- [Simulation](#simulation)
- [How to Run](#how-to-run)
- [Results](#results)

---

## Design Overview

The DUT is a **D Flip-Flop (DFF)** with synchronous reset.

- **Inputs:** `din`, `rst`, `clk`  
- **Output:** `dout`  
- On reset (`rst = 1`), `dout` is cleared to `0`.  
- Otherwise, `dout` follows `din` at the positive edge of `clk`.  

---

## Architecture

The verification environment consists of:

1. **Transaction Class** (`transaction.sv`)  
   Represents a single input/output transaction with `din` and `dout`.

2. **Generator Class** (`generator.sv`)  
   Randomizes and sends transactions to the driver and reference mailbox.

3. **Driver Class** (`driver.sv`)  
   Drives DUT inputs from transactions received from the generator.

4. **Monitor Class** (`monitor.sv`)  
   Observes DUT signals and forwards transactions to the scoreboard and coverage.

5. **Scoreboard Class** (`scoreboard.sv`)  
   Compares DUT output with reference and reports pass/fail.

6. **Coverage Class** (`dff_coverage.sv`)  
   Functional coverage on `din` and `dout`.

7. **Environment Class** (`environment.sv`)  
   Instantiates all components, connects mailboxes, and coordinates test execution.

---

### Environment Block Diagram

