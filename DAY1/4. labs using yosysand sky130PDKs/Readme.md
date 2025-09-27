###  GOOD MUX NETLIST
````markdown
# 🧠 Good MUX Netlist

This repository contains a **Verilog netlist** for a multiplexer (MUX) circuit that has been synthesized and exported using **Synopsys Design Compiler**.  

The process demonstrates how to extract a clean netlist from a synthesized design and view or edit it using a text editor.

---

## 📌 In this Example
- Synthesized a MUX design using **Synopsys Design Compiler**.  
- Exported the synthesized **gate-level design** as a Verilog netlist.  
- Opened it in a text editor (e.g., `gvim`) to verify or manually inspect the generated logic.  

---

## 🔧 Step-by-Step: How the Netlist Was Generated

### 1️⃣ Run Yosys and Synthesize the Design
Inside a terminal, launch `yosys` and run the following command to synthesize your MUX design:

```bash
write_verilog -noattr good_mux_netlist.v
````

**Explanation:**

* `write_verilog` → Exports the synthesized netlist in Verilog format.
* `-noattr` → Ensures the output file does not include Yosys-specific attributes (like `(* keep *)`, `(* src = ... *)`, etc.), making it cleaner and more portable.
* `good_mux_netlist.v` → The name of the generated netlist file.

✅ *Tip:* Before running `write_verilog`, make sure you’ve already **read, parsed, and synthesized** your RTL design inside Yosys.

---

### 2️⃣ Open the Netlist for Inspection

After generating the netlist, open it in a text editor for inspection:

```bash
!gvim good_mux_netlist.v
```
<img width="2533" height="1345" alt="image" src="https://github.com/user-attachments/assets/5f9a182f-0c5c-40b0-9b5a-bb0ede6e6a4c" />

---

## 📁 Files Included

* **`good_mux_netlist.v`** → Gate-level Verilog netlist generated after synthesis.

  * Contains instances of standard cells (e.g., AND, OR, MUX gates).
  * Represents the synthesized logic of the MUX design.
<img width="2549" height="1061" alt="image" src="https://github.com/user-attachments/assets/70bbbc01-3b7e-42cd-87fa-f6192e464ff5" />

---

## 📂 Use Cases

This netlist can be used for:

* ✅ **Formal verification** (comparing RTL vs gate-level).
* ✅ **Logic simulation**.
* ✅ **Backend flows** (e.g., place & route if targeting ASIC or FPGA).

```


