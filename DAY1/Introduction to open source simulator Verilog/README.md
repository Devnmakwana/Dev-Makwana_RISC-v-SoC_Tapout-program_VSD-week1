# 🚀 Iverilog-Based Digital Simulation Flow

The **Iverilog simulation flow** forms the backbone of digital design verification, enabling designers to validate and debug Verilog models before hardware implementation. The process integrates compilation, simulation, and waveform visualization in a streamlined workflow.

---

## **Step-by-Step Workflow**

### **1. Provide Design and Testbench to Iverilog**

* The process begins by preparing two key components:

  * **Design Under Test (DUT):** The actual Verilog RTL code that implements your digital logic.
  * **Testbench:** A Verilog module written to apply input stimuli, monitor outputs, and check DUT behavior.
* Both files are passed to the Iverilog compiler for compilation and simulation.

---

### **2. Compilation & Simulation**

* Iverilog first **compiles the Verilog source files** into an intermediate simulation executable.
* This executable is then run to simulate the design behavior.
* During simulation, **all signal transitions and timing data** are recorded in a **Value Change Dump (VCD)** file.

---

### **3. Generate Value Change Dump (VCD)**

* The **VCD file** is a structured log that captures:

  * Signal transitions
  * Timing of events
  * Hierarchical scope of signals
* It serves as a **bridge between simulation and visualization**, making it possible to analyze waveforms post-simulation.

---

### **4. Load VCD into GTKWave**

* The generated VCD is opened using **GTKWave**, a powerful open-source waveform viewer.
* GTKWave provides features like:

  * Hierarchical signal browsing
  * Zoom and cursor measurements
  * Multiple signal overlays for timing correlation

---

### **5. Visualize & Analyze the Waveform**

* With GTKWave, engineers can:

  * Inspect signal transitions over simulation time.
  * Validate DUT responses against expected behavior.
  * Debug functional or timing issues by correlating stimulus with output.
* This visualization step is critical for ensuring correctness before moving to synthesis or FPGA prototyping.

<img width="2425" height="1200" alt="image" src="https://github.com/user-attachments/assets/b92756bc-30ca-4b01-8fe4-4659232647e5" />


## **🛠 Tools Used**

* **Iverilog** – Open-source Verilog compiler and simulator.
* **GTKWave** – Open-source waveform viewer for debugging digital designs.




