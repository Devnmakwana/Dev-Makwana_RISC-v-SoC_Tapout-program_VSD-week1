## Step 1:

````markdown
# Running the Sky130 RTL Design and Synthesis Workshop Simulation

This section explains how to run a simulation for the `good_mux` Verilog module using **Icarus Verilog (iverilog)** and **GTKWave**.

---

## Step 1: Move to the Workshop Directory
Go into the folder where you cloned the workshop repository:

```bash
cd sky130RTLDesignAndSynthesisWorkshop
````

---

## Step 2: Open the Verilog Source Folder

Next, switch into the directory containing the Verilog source files:

```bash
cd verilog_files
```

---

## Step 3: Check the Available Files

List the files inside this folder:

```bash
ls
```

You should see something like:

* `good_mux.v` → the Verilog design file
* `tb_good_mux.v` → the testbench file

---

## Step 4: Compile the Design and Testbench

Use **Icarus Verilog** to compile both files together:

```bash
iverilog good_mux.v tb_good_mux.v
```
<img width="2240" height="537" alt="image" src="https://github.com/user-attachments/assets/507e8e23-29fb-4484-b9b8-8041c85c74fd" />

This will generate an executable named **`a.out`** in the same directory.

---

## Step 5: Run the Compiled Simulation

Execute the simulation by running:

```bash
./a.out
```

After running, a file called **`tb_good_mux.vcd`** will be created.
This file stores the waveform data.

---

## Step 6: Open the Waveform in GTKWave

To view the simulation results, open the `.vcd` file with GTKWave:

```bash
gtkwave tb_good_mux.vcd
```

---

## Step 7: Add Signals to the Waveform

Inside GTKWave, drag the signals from the left panel and drop them into the waveform display area.
This will allow you to observe how the signals in the `good_mux` module change over time.
<img width="2544" height="1069" alt="image" src="https://github.com/user-attachments/assets/82190cfa-5509-488a-a945-bfe385483ab6" />

---

✅ You’ve now successfully simulated and visualized the `good_mux` design!

```



