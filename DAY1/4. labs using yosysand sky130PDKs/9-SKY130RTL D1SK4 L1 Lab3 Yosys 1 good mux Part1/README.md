

````markdown
# ⚡ Yosys Synthesis Workflow for Sky130 RTL Design

## 📖 Introduction
This guide explains the steps involved in synthesizing a Verilog design using **Yosys** with the **Sky130 process library**.  
We will focus on a Verilog file (`good_mux.v`) and its testbench, and highlight differences that may arise across Yosys versions.

---

## ✅ Prerequisites
Make sure you have the following installed:
- **Yosys** (for synthesis)  
- **Sky130 process library** (`sky130_fd_sc_hd__tt_025C_1v80.lib`)  
- **Verilog source files** (e.g., `good_mux.v`)  
- **Testbenches** (for verification)  

---

## 🔧 Steps to Synthesize

### 1️⃣ Clone the Git Repository
```bash
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop
````

This repo contains the Verilog files, including MUX designs and testbenches.

---

### 2️⃣ Navigate to the Verilog Directory

```bash
cd sky130RTLDesignAndSynthesisWorkshop
```

---

### 3️⃣ Invoke Yosys

Run Yosys in the terminal:

```bash
yosys
```

---

### 4️⃣ Read the Liberty Library

```bash
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

* Loads **standard cell definitions** (timing, power, area, functionality).
* Provides available cells (e.g., NAND, NOR, INV, MUX).
* Needed for **technology mapping** later in synthesis.

---

### 5️⃣ Read the Verilog File

```bash
read_verilog good_mux.v
```

* Loads your RTL design (`good_mux.v`).
* Parses and builds an internal netlist representation.
* Prepares it for synthesis and optimization.

---

### 6️⃣ Synthesize the Design

```bash
synth -top good_mux
```

* Identifies `good_mux` as the **top-level module**.
* Converts RTL into a gate-level representation.
* Applies optimizations: constant propagation, dead-code elimination, simplification.
* Still **technology-independent** at this stage.
<img width="2525" height="1332" alt="image" src="https://github.com/user-attachments/assets/d91be722-67a7-42df-b929-47811faae83a" />

---

### 7️⃣ Perform ABC Optimization

```bash
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

* Maps generic logic to **Sky130 standard cells**.
* Optimizes for **timing, area, and limited power**.
* Netlist now consists only of Sky130 cells.
<img width="2538" height="1347" alt="image" src="https://github.com/user-attachments/assets/980e7d9b-c9d7-4878-baac-0a94864fa009" />

---

### 8️⃣ Visualize the Logic

```bash
show
```

* Opens a graphical view of the synthesized design.
* Displays gates, interconnections, and hierarchy.
* Useful for debugging and verification.

💡 If `show` doesn’t work, install Graphviz/GTK or output to a file:

```bash
write_svg output.svg
```
<img width="2576" height="858" alt="image" src="https://github.com/user-attachments/assets/a5ff6332-0c8c-4dd2-8410-2382bcfcd008" />

---

## 📊 Summary of Flow

| Step | Command               | Purpose                          |
| ---- | --------------------- | -------------------------------- |
| 4    | `read_liberty`        | Load standard cell definitions   |
| 5    | `read_verilog`        | Load RTL design                  |
| 6    | `synth -top <module>` | Convert RTL → gate-level netlist |
| 7    | `abc -liberty`        | Map logic to technology cells    |
| 8    | `show`                | Visualize post-synthesis netlist |

---

## 🔄 Version Differences

* In the tutorial’s older Yosys version → multiple cells used (`nand2_1`, `clkinv_1`, `o2lai_0`, `buf`).
* In the latest Yosys version → only a single cell (`mux2_1`) appears.
* These differences are due to **improved optimizations** and **different mapping strategies** in newer Yosys releases.

---

## 🏁 Conclusion

This workflow shows how to synthesize a Verilog design using Yosys with the Sky130 process library.
Be mindful of **version differences**, as they may impact the set of cells used and the final optimization results.

```

