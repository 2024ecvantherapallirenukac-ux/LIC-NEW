###  Adder and Subtractor circuit 

### # Op-Amp Circuit Design: Part (b)

This design implements the output function:
### $$y_2(t) = 2x_2(t) + 6x_3(t)$$

## 1. Circuit Topology
Since all coefficients are positive, we use a **Non-Inverting Summing Amplifier**. This configuration allows us to sum the inputs and apply gain without inverting the signal phase.

### Schematic Requirements
* **Op-Amp:** Standard (e.g., LM741 or TL081)
* **Supply Voltage ($V_{CC}$):** $\pm 15V$
* **Input Stage:** A resistive summing network connected to the non-inverting (+) terminal.
* **Gain Stage:** A standard non-inverting feedback loop.

---

## 2. Component Selection

To achieve the specific weights of **2** and **6**, we calculate the resistor values based on the non-inverting summing formula:
$$V_{out} = \left( 1 + \frac{R_f}{R_g} \right) \left( \frac{V_1 R_2 + V_2 R_1}{R_1 + R_2} \right)$$

| Component | Label | Value | Description |
| :--- | :--- | :--- | :--- |
| **Resistor 1** | $R_2$ | $30 k\Omega$ | Connected to input $x_2(t)$ |
| **Resistor 2** | $R_3$ | $10 k\Omega$ | Connected to input $x_3(t)$ |
| **Feedback Resistor** | $R_f$ | $70 k\Omega$ | Connected between Output and Inverting (-) pin |
| **Gain Resistor** | $R_g$ | $10 k\Omega$ | Connected between Inverting (-) pin and Ground |

---

## 3. Mathematical Verification

### Step 1: Voltage at Non-Inverting Pin ($V_+$)
Using the voltage divider principle between the two inputs:
$$V_+ = \frac{x_2(t) \cdot 10k + x_3(t) \cdot 30k}{10k + 30k} = \frac{10}{40}x_2(t) + \frac{30}{40}x_3(t)$$
$$V_+ = 0.25x_2(t) + 0.75x_3(t)$$

### Step 2: Amplifier Gain ($A_v$)
The gain of the non-inverting stage is determined by $R_f$ and $R_g$:
$$A_v = 1 + \frac{R_f}{R_g} = 1 + \frac{70k}{10k} = 8$$

### Step 3: Final Output ($y_2$)
$$y_2(t) = A_v \cdot V_+$$
$$y_2(t) = 8 \cdot [0.25x_2(t) + 0.75x_3(t)]$$
$$y_2(t) = 2x_2(t) + 6x_3(t)$$

---

## 4. Operation Limits
Given the input values:
* $x_2(t) = 0.5 \sin(2000\pi t)$ (Peak $\pm 0.5V$)
* $x_3(t) = +1V$

**Maximum Peak Output:**
$y_{2,max} = 2(0.5) + 6(1) = 7V$

Since $7V$ is well within the $\pm 15V$ supply rails, the op-amp will operate in its linear region without clipping.

# Working Principle: Non-Inverting Summing Amplifier

The Non-Inverting Summing Amplifier works by combining multiple input signals into a single voltage and then amplifying that combined signal without changing its polarity (phase).

It operates in two distinct stages:

---

## 1. Passive Summing Stage (The "Mixer")
In this stage, the input voltages ($x_1, x_2, ... x_n$) are connected to the **Non-Inverting (+) Terminal** through a network of resistors.

* **No Current Flow:** Because an ideal op-amp has infinite input impedance, no current flows into the (+) terminal.
* **Weighted Average:** The resistors form a voltage divider. The voltage at the (+) pin becomes a weighted average of all inputs.
* **Phase Preservation:** Since the signals enter the (+) terminal, a positive increase in input results in a positive increase in output.



---

## 2. Active Amplification Stage (The "Booster")
Once the inputs are "mixed" at the (+) terminal, the op-amp acts as a standard **Non-Inverting Amplifier**.

* **Negative Feedback:** Resistors $R_f$ (feedback) and $R_g$ (ground) create a feedback loop to the Inverting (-) terminal.
* **Voltage Follower Logic:** The op-amp automatically adjusts its output so that the voltage at the (-) terminal matches the voltage at the (+) terminal.
* **Gain Multiplication:** The "mixed" voltage at the (+) terminal is multiplied by the Gain ($A_v$):
    $$A_v = 1 + \frac{R_f}{R_g}$$

---

## 3. The Final Result
The output is the mathematical product of the **Mixed Input** and the **Gain**.

$$V_{out} = \text{Gain} \times \text{Weighted Average of Inputs}$$

### Circuit diagram 

<img width="432" height="436" alt="Screenshot 2026-04-14 163535" src="https://github.com/user-attachments/assets/55fccd8a-62d8-4bc6-8635-8592a3fc2786" />

### DC Analysis 

![b dc ](https://github.com/user-attachments/assets/f36e7e72-fc8e-45b1-a5f6-024f09e77d00)

This section documents the results of the **DC Operating Point (.op)** simulation used to verify the circuit's accuracy against the design requirements.

## 1. Simulation Setup
The simulation was performed with the following static inputs to test the gain coefficients:
* **Input $x_2(t)$:** $0V$ (Reference Ground)
* **Input $x_3(t)$:** $+1V$ (DC Source)
* **Power Supply ($V_{CC}$):** $\pm 15V$

---

## 2. DC Operating Point Data
Based on the simulation log, the following node voltages and currents were captured:

| Parameter | Node/Variable | Simulated Value |
| :--- | :--- | :--- |
| **Summing Node Voltage** | $V(vin)$ | **0.74994 V** |
| **Final Output Voltage** | $V(vout)$ | **5.9998 V** |
| **Positive Rail** | $V(n002)$ | $15.0 V$ |
| **Negative Rail** | $V(n003)$ | $-15.0 V$ |
| **Op-Amp Input Current** | $Ix(u1:1)$ | $8.007 \times 10^{-8} A$ |

---

## 3. Mathematical Validation

The target design equation is:
$$y_2(t) = 2x_2(t) + 6x_3(t)$$

### Verification Calculation:
By substituting the simulation inputs ($x_2 = 0, x_3 = 1$):
$$y_2 = 2(0) + 6(1) = 6.0V$$

### Transient Analysis 

![b trans](https://github.com/user-attachments/assets/0fb63a55-10c0-4998-b9ca-1d9ed97583e8)

Transient Analysis Report

The transient analysis (time-domain simulation) was performed to observe the circuit's response to a time-varying input $x_2(t)$ combined with a constant DC offset from $x_3(t)$.

### 1. Simulation Parameters
* **Input $x_2(t)$:** $0.5 \sin(2000\pi t)$ (Sine wave: $1V$ peak-to-peak, frequency $1kHz$)
* **Input $x_3(t)$:** $+1V$ (Constant DC)
* **Time Scale:** $0ms$ to $5ms$ (Shows 5 full cycles of the $1kHz$ signal)

---

### 2. Waveform Observations
From the simulation plot of $V(vout)$, we can verify the following:

* **DC Offset (Center Line):** The sine wave is centered at **$6V$**. This is expected because the DC component $6 \times x_3(1V) = 6V$.
* **Peak-to-Peak Amplitude:** The wave fluctuates between **$5V$** and **$7V$**. 
    * The $1V$ amplitude (from $6V$ to $7V$) matches the calculation: $2 \times 0.5V = 1V$.
* **Frequency:** There is one full cycle every $1ms$, which confirms the frequency $f = \frac{1}{T} = 1000Hz$ (consistent with $2000\pi$ rad/s).

---

### 3. Verification of the Design Equation
The output waveform follows the transient equation:
$$y_2(t) = 2(0.5 \sin(2000\pi t)) + 6(1)$$
$$y_2(t) = 1 \sin(2000\pi t) + 6$$

**Mathematical vs. Simulated Match:**
* **Theoretical Max:** $6 + 1 = 7V$ 
* **Theoretical Min:** $6 - 1 = 5V$
* **Simulation Result:** The plot shows the peaks touching exactly $7.0V$ and $5.0V$, providing **100% verification** of the gain coefficients.

### AC analysis 

![b ac](https://github.com/user-attachments/assets/1c66038a-62f0-48fd-8e84-da2e5416841f)

### 1. Magnitude Analysis (Solid Line)
* **Mid-band Gain:** The flat portion of the graph shows a constant gain of approximately **$6dB$**. 
    * *Calculation:* Since our gain factor for the AC signal ($x_2$) is $2$, the decibel gain is $20 \log_{10}(2) \approx 6.02dB$.
* **Bandwidth / Cut-off Frequency:** The gain remains flat until approximately **$100kHz$**, after which it begins to roll off. This indicates the usable frequency range of the op-amp before its internal compensation limits the performance.
* **Roll-off:** Beyond the corner frequency, the gain drops at a rate of $-20dB$ per decade, which is characteristic of a standard internally compensated op-amp (single-pole response).

* ### 2. Phase Analysis (Dotted Line)
* **Low Frequency:** At lower frequencies (below $10kHz$), the phase shift is **$0^\circ$**. This confirms the circuit is **Non-Inverting** (the output is in phase with the input).
* **High Frequency:** As frequency increases toward the MHz range, the phase starts to drop (lag). At the gain-bandwidth limit, the phase shift reaches $-180^\circ$ and beyond, indicating the propagation delay within the op-amp's internal circuitry.

# Conclusion

The objective of this design task was to implement an operational amplifier circuit capable of performing the specific mathematical function:
**$y_2(t) = 2x_2(t) + 6x_3(t)$**

Through theoretical design and multi-stage simulation verification, the following conclusions have been reached:

### 1. Design Integrity
The use of a **Non-Inverting Summing Amplifier** topology proved to be the most efficient solution. It allowed for the successful summation and scaling of multiple inputs using a single op-amp stage, maintaining phase consistency without the need for additional inverting buffers.

### 2. Simulation Validation
* **DC Analysis:** Confirmed that the chosen resistor ratios ($10k\Omega, 30k\Omega, 70k\Omega$) produced the exact weighted sum required. The output of $\approx 6V$ for a $1V$ DC input verified the gain accuracy to within $0.003\%$.
* **Transient Analysis:** Demonstrated the circuit's dynamic reliability. The output correctly combined a $1kHz$ sine wave with a DC offset, oscillating perfectly between the calculated boundaries of $5V$ and $7V$.
* **AC Analysis:** Verified that the circuit provides a stable flat-band gain of $6dB$ (gain of 2 for the AC component) and possesses a bandwidth exceeding $100kHz$, which is more than sufficient for the required $1kHz$ operating frequency.

### 3. Operational Performance
With a supply voltage of $\pm 15V$, the circuit operates comfortably within its linear region. The maximum peak output of $7V$ provides a safety margin of $8V$ before reaching the saturation rails, ensuring high signal fidelity and zero clipping.

### 4. Final Verdict
The circuit design is **fully validated** and meets all specified mathematical and electrical requirements. The results from the LTspice simulations align perfectly with the theoretical derivations, proving the circuit is ready for physical hardware implementation.



