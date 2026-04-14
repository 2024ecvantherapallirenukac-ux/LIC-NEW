#### Inverting Amplifier 

##AIM 

To design and analyze a inverting amplifier using an operational amplifier and verify the gain.

# Working Principle: Inverting Amplifier

The Inverting Amplifier uses negative feedback to amplify an input signal while reversing its phase. The operation is defined by the "Virtual Ground" concept.

### 1. The Virtual Ground Concept
* The non-inverting terminal ($V_+$) is connected to **Ground (0V)**.
* Due to the high open-loop gain of the op-amp, it maintains the inverting terminal ($V_-$) at the same potential.
* This makes the inverting terminal a **Virtual Ground (0V)**.

### 2. Current Analysis (KCL)
Since the input impedance of the op-amp is nearly infinite, no current flows into the inverting input. Therefore, the current flowing through $R_1$ must equal the current flowing through $R_f$.

1. **Input Current ($I_{in}$):**
   $$I_{in} = \frac{V_{in} - V_-}{R_1} = \frac{V_{in} - 0}{R_1} = \frac{V_{in}}{R_1}$$

2. **Feedback Current ($I_f$):**
   $$I_f = \frac{V_- - V_{out}}{R_f} = \frac{0 - V_{out}}{R_f} = -\frac{V_{out}}{R_f}$$

### 3. Deriving the Gain
By equating the currents ($I_{in} = I_f$):
$$\frac{V_{in}}{R_1} = -\frac{V_{out}}{R_f}$$

Rearranging for the Output Voltage:
$$V_{out} = -V_{in} \left( \frac{R_f}{R_1} \right)$$

The Voltage Gain ($A_V$) is:
$$A_V = \frac{V_{out}}{V_{in}} = -\frac{R_f}{R_1}$$


The negative sign indicates a **180° phase inversion**, meaning the output signal is the mirror image of the input signal across the 0V axis.

### Circuit diagram
<img width="830" height="593" alt="inverting circuit" src="https://github.com/user-attachments/assets/9a7f4dd2-0a2e-4567-af85-3b7223ce56b3" />

### Design part

given :

AV = -7v/v

# Inverting Amplifier Design
**Target Gain:** $A_V = -7 \text{ V/V}$

### 1. Design Calculations
The voltage gain for an inverting amplifier is given by the formula:
$$A_V = \frac{V_{out}}{V_{in}} = -\frac{R_f}{R_1}$$

**Given:**
$A_V = -7$

**Derivation:**
$$-7 = -\frac{R_f}{R_1}$$
$$R_f = 7 \cdot R_1$$

**Assumed Values:**
* Let $R_1 = 1\text{k}\Omega$
* Therefore, $R_f = 7\text{k}\Omega$

  ### DC Analysis

  ![inverting dc](https://github.com/user-attachments/assets/36ab48c9-c6b1-4fa1-a5fc-9a0049ce201e)

### Transient Analysis

![inverting T](https://github.com/user-attachments/assets/bef35e01-ead8-4339-a529-f5ecd866205e)

output calculation 

Vin(max) = 6 V
Vout = 7 × 5 = 42 V
Since supply voltage is ±15V:

Output cannot reach 55 V
Output will saturate at ≈ ±13.5 V
Clipping occurs because the required output voltage exceeds the supply voltage
This causes distortion in the output waveform

#### AC Analysis

![VERTING AC ](https://github.com/user-attachments/assets/2124b602-7157-4ab7-a370-7013d2daf0da)

At low frequency: Gain ≈ 16.9 dB (since Av = 7)
Gain remains constant up to bandwidth
After cut-off frequency: Gain decreases

###### **Voltage follower **

### Aim 

To design and analyze a voltage follower circuit using an operational amplifier and verify that the output voltage follows the input voltage (unity gain).

###Circuit diagram

<img width="804" height="544" alt="voltage circuit" src="https://github.com/user-attachments/assets/72220fc7-6cc6-40c6-b278-d4b14d18a045" />

A voltage follower is a special case of a non-inverting amplifier where the output is directly fed back to the inverting terminal.

General gain formula of non-inverting amplifier: Av = 1 + (Rf / R1)

For voltage follower: Rf = 0 and R1 = ∞

So, Av = 1

Therefore, Vout = Vin

Input is applied to non-inverting terminal (+)
Output is directly connected to inverting terminal (−)
No resistors are used -Device current → current through simple elements (R, V, etc.) -Subckt current → current entering/leaving a subcircuit block .
### DC Analysis

Given: Vin(p-p) = 10 V
Vcc = 15V
RL = 5.6kΩ

Gain: Av = 1

![WhatsApp Image 2026-04-14 at 11 36 59](https://github.com/user-attachments/assets/e1e85282-284f-48df-b08b-a8ed1c8ef29f)

### Transient Analysis

![WhatsApp Image 2026-04-14 at 11 40 28](https://github.com/user-attachments/assets/20b0871a-ebd0-4aff-8427-aa1b37ea098f)

Output Signal
Output waveform is also sinusoidal
Amplitude: 5 V
Peak-to-peak voltage: 10 V
Frequency: Same as input (1 kHz)
Vout = Vin

Type: Sinusoidal wave
Amplitude: 5 V
Peak-to-peak voltage: 10 V
Frequency: 1 kHz
Vin = 5 sin(2πft)

No Phase Shift
Input and output peaks occur at the same time

No Clipping
Output remains within ±5 V
Supply voltage (±13 V) is sufficient

### AC analysis

![WhatsApp Image 2026-04-14 at 11 42 15](https://github.com/user-attachments/assets/d1a88e9d-1550-4895-aad1-947559caeb86)

## Reason for Dip in Frequency Response

### Explanation
The dip observed in the frequency response graph is attributed to the **non-ideal characteristics** of the **uA741 op-amp model**. 

* **Internal Poles and Zeros:** In a real-world or modeled uA741, internal transistors and compensation networks create multiple poles and zeros. At specific frequencies, these elements interact with one another.
* **Gain Reduction:** This interaction results in a localized loss of magnitude, causing a **temporary drop in gain (dip)** before the final high-frequency roll-off occurs.

## Voltage Follower (Unity Gain Buffer)

### Analysis
The voltage follower is characterized by **unity gain** ($A_V = 1$), meaning the output voltage directly tracks the input voltage. Its primary function is to serve as a **buffer** between stages of a circuit.

### Key Characteristics
* **Impedance Transformation:** It features **high input impedance**, which prevents loading of the preceding stage, and **low output impedance**, allowing it to drive subsequent loads efficiently.
* **Signal Integrity:** By acting as an isolation layer, it ensures accurate signal transfer and prevents voltage drop across the source's internal resistance.
* **Phase Retention:** The output remains in phase with the input, providing a 1:1 voltage replica.





  
