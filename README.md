# Experiment-1

## Aim
To do the **DC analysis, Transient analysis, and AC analysis** of a **Common Source (CS) amplifier** circuit and extract various parameters using **LT Spice**.

## Components Required
- **Mosfet:** `nmos4`, `pmos4`
- **Resistor:** `22kΩ`
- **Voltage Supply:** `1.8V`, `0.9V`
- **Connecting Wires**

## Theory
**MOSFET** is one of the most important components in electronics.

This importance is due to:
- Compact design  
- Low power consumption  
- Simple geometry  
- Compatibility in **VLSI technology**

### MOSFET Configurations
There are three different configurations in which the MOSFET can be connected:
1. **Common Drain**
2. **Common Gate**
3. **Common Source** *(Most popular)*

The **MOSFET acts as an amplifier** in the **saturation region**, where:
- `Vgs > Vth`
- `Vgd < Vth`
- `Vds ≥ Vov` *(For N-channel MOSFET)*

In the **Common Source configuration**:
- There is a **180-degree phase shift** between input and output.
- The **input impedance is very high** *(Ideally infinite, `Ig = 0`)*.

### Drain Current Equation
\[
Id = \frac{1}{2} k_n V_{ov}^2
\]
where:  
- **\(V_{ov} = V_{gs} - V_{th}\)**
- **\( k_n = \mu_n C_{ox} \frac{W}{L} \)**  

### Output Consideration
The output is taken from the **drain end**, rather than simply across the resistor, to maintain a **common ground reference**.

## Analysis Types

### **1. DC Analysis**
- Ensures the MOSFET operates in the **saturation region**.
- Determines the **DC operating point** of the transistor.
- Prevents **signal distortion**.
- Helps in the **determination of biasing resistors**.
- Maintains a **correct operating point** despite parameter fluctuations.

### **2. Transient Analysis**
- Analyzes the response of the circuit to **time-varying signals**.
- Helps determine:
  - **Signal distortion**
  - **DC shift between input and output**
  - **Phase distortion issues**
- Essential for **high-speed applications** (e.g., communication systems).

### **3. AC Analysis**
- Small signal analysis of the circuit.
- Determines the **gain** of the amplifier circuit.
- Helps analyze the **frequency response**.
- Gain is given by:

\[
A_v = -g_m R_d
\]
## Circuit - 1

### **Circuit Diagram**
![image](https://github.com/user-attachments/assets/0dc2fe6a-72bd-4bdf-8584-fae024369d56)

## Procedure  

### **1. Design the CS amplifier circuit**  
- Name the **NMOS** as `CMOSN`.

### **2. DC Analysis**  
- Apply **DC voltage** of:  
  - `VDD = 1.8V`  
  - `VGS = 0.9V`  
- In **LTSpice**:  
  1. Go to **Simulate → Edit Simulation Command**.  
  2. Click on **DC Analysis**, then press **OK**.  
  3. Click on **Run** to obtain the **DC operating point (Vout)**.  
- **Set the Length as constant** and **determine the Width** such that `ID = 48.33µA`.  

### **3. Transient Analysis**  
- Modify the **VGS voltage source** to a **sine wave input** with:  
  - **DC level:** `0.9V`  
  - **Amplitude:** `50mV`  
  - **Frequency:** `1kHz`  
- In **LTSpice**:  
  1. Go to **Edit Simulation Command → Transient Analysis**.  
  2. Set **Stop Time** as `5ms`, then click **OK**.  

### **4. AC Analysis**  
- In **Edit Simulation Command**:  
  1. Select **AC Analysis**.  
  2. Set **Type of Sweep** to **Decade**.  
  3. Set **Points per Decade** to `10`.  
  4. Set **Frequency Range** from **0.1Hz to 1THz**.  
  5. Click **OK**.  
- Determine the **gain and frequency response** of the circuit.  

---

## **Calculation**  

### **Power Calculation**  
\[
P = 100µW
\]

### **Drain Equation**  
\[
VDD = VDS + ID \times RD
\]

\[
P = I \times V
\]

- **Given:**  
  - `ID = 48.33µA`  
  - `VDD = 1.8V`  
- **Thus:**  
  \[
  VDS = Vout
  \]

### **Resistor and MOSFET Parameters**
- **Calculated RD:** `32.4kΩ` *(Used: `22kΩ`)*  
- **Length:** `180nm`  
- **Width:** `18µm` *(Found by keeping the length constant)*  
- **VDS:** `0.735V`  

### **Q-Point**
\[
Q = (0.735V, 48.33µA)
\]
##  **Results**  

### 🔹 **1. DC Analysis**  
![image](https://github.com/user-attachments/assets/630e5d48-014f-47b3-be95-da59029de78c)
Drain Current, Id = 48.33 µA  
Vout = 0.735V  
Width = 18 µm for Length = 180 nm '''

### 🔹 **2. Transient Analysis**  
![image](https://github.com/user-attachments/assets/4db56dd2-f8c5-44b6-b2e2-8f8f4454c19d)
There is a 180-degree phase shift between input and output.

### 🔹 **3. AC Analysis** 
![image](https://github.com/user-attachments/assets/14425c78-2fdf-4c1b-90e6-6171c15cc0a1)


### 🔹 **Inference**  
1. The Drain current is directly influenced by the Width of the MOSFET.  
2. By adjusting the dimensions of the MOSFET, the Drain current can be precisely controlled.  
3. A 180-degree phase shift is observed between the input and output waveforms.  
4. The Common Source (CS) amplifier exhibits a significant gain of 20 dB, meaning the output signal is 20 times larger than the input signal.  

## Circuit 2: Simulation of CMOS Amplifier

### 🔹 **Aim**  
Simulate the DC analysis, Transient, and AC analysis of a CMOS amplifier circuit using LTSpice.

### 🔹 **Circuit**
![image](https://github.com/user-attachments/assets/add2aed4-a355-41ac-8a38-d584d3ad0616)

🔹 Procedure
Design the CMOS amplifier circuit.

Name the NMOS as CMOSN and PMOS as CMOSP.

Apply the DC voltage of VDD = 1.8 V.

DC Sweep Analysis:
Go to the Edit Simulation Command and select the DC Sweep option. Set the following:

Source name: Vin
Type of Sweep: Linear
Start value: 0
Stop value: VDD = 1.8 V
Increment: 0.1
Find the Vin from the VTC curve.

DC Analysis:
Put the appropriate Vin value.
Go to the Simulate option and select Edit Simulation Command.
Choose DC Analysis, then click OK.
Click Run in the tab menu to obtain the DC operating point Vout.
Set the length as constant and determine the width such that ID = 55.5 µA.

Transient Analysis:
Modify the Vin voltage source to a sine wave input with the following parameters:

DC level: 0.9 V
Amplitude: 50 mV
Frequency: 1 kHz
In LTSpice, go to Edit Simulation Command, select Transient Analysis.
Set the Stop Time as 5 ms, then click OK.

AC Analysis:
In Edit Simulation Command, select AC Analysis.
Set the Type of Sweep to Decade.
Set Points per Decade to 10.
Set the Frequency Range from 0.1 Hz to 1 THz.
Click OK. Determine the gain and frequency response of the circuit.

🔹 Calculation
ID = 48.3 µA, VDD = 1.8 V

Length M1 = 180 nm  
Width = 190 nm (found by keeping the Length of M1 constant)

Length M2 = 180 nm  
Width = 449 µm (found by keeping the Length of M2 constant)

##  **Results**

### 🔹 **1. DC Sweep Analysis**  
![image](https://github.com/user-attachments/assets/918022d1-4709-4471-9276-2f7703513fcd)
VTC Curve: vtc

The value of Vin is selected as **0.8V** as it is present in the middle of the saturation region of the VTC Curve.
🔹 2. DC Analysis
![image](https://github.com/user-attachments/assets/9973aa23-63fd-4f2c-b5f9-dedd5e59c293)


Voltage Output: v1

Drain Current, Id =19.55 µA  
Vout = 1.67 V  

Device Dimensions:  
Length M1 = 180 nm, Width = 190 nm  
Length M2 = 180 nm, Width = 449 µm  

🔹 3. Transient Analysis
![image](https://github.com/user-attachments/assets/08f4324f-87ce-42f0-83b5-99d0b9c07e6c)
Waveform Output: v2
There is a **180-degree phase shift** between the input and output signals.

🔹 4. AC Analysis
![image](https://github.com/user-attachments/assets/e79d2176-ee55-47ce-ba9e-d79e616f9165)
Frequency Response: v3

## Inference

1. The width of the MOSFET directly affects the drain current.  
2. By changing the dimensions of the MOSFET:  
   - **M1 (PMOS):** Varying the width causes only a slight change in drain current.  
   - **M2 (NMOS):** Increasing the width significantly increases the drain current.  
3. A larger MOSFET width results in a higher gain.  
4. There is a **180-degree phase shift** between the input and output waveforms.  


