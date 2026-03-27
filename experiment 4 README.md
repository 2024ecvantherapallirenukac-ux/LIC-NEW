#####DIFFERENTIAL AMPLIFIER

###CIRCUIT 1

 # Aim:

"Design and analysis of the MOS differential amplifier circuit for the following specifications."

*Drain Supply Voltage (VDD):** 0.9V
* **Source Supply Voltage (VSS):** -0.9V
* **Maximum Power Dissipation (P):** <= 1.8mW
* **Input Common Mode (VinCM):** 0V
* **Output Common Mode (VoCM):** 0V
* **Tail Node Voltage (VP):** -0.7V
* **Load Capacitance (CL):** 10pF
* length :480nm
  εr = 3.9
ε0 = 8.854 × 10⁻¹² F/m
tox = 4.1 × 10⁻⁹ m
μn = 273.809 cm²/Vs
μp = 115.689 cm²/Vs

Circuit diagram:
<img width="1110" height="623" alt="circuit 1 exp4" src="https://github.com/user-attachments/assets/912517e4-d1b5-4c3c-a640-be70858b9273" />

 # 1.DC analysis:

 In the ideal balanced state (V_{in1} = V_{in2}), the tail current I_{SS} (labeled I1 in your schematic) splits equally between the two transistors (M1 and M2).

 I_{D1} = I_{D2} = \frac{I_{SS}}{2}
 
 I_{SS} = 1{mA}

 V_{out(DC)} = V_{DD} - (I_D \cdot R_d)

 0 = o.9-Rd*0.5mA

 Rd = 1.8k

# Verification for  circuit:

 V = 0.9{V}

 ID =0.5mA

 RD = 1.8k

 Vout(DC) = 0

 # NMOS width calculation ( for both M1 and M2)

   Oxide Capacitance (Cox)
Cox = εr ε0 / tox
Cox = (3.9 × 8.854 × 10⁻¹²) / (4.1 × 10⁻⁹)
Cox = 8.42 × 10⁻³ F/m²

VGS - VTH = 0.7-0.36 = 0.34V

  Drain current equation: ID/2 = (1/2) μn Cox (W/L) (VOV)²
Rearranging: Wn = ( ID L) / (μn Cox (VOV)²) Substitute values: Wn = (1x 10^-3 x 480 x 10^-9)
/ (273.809 × 10⁻⁴ × 8.42 × 10⁻³ × (0.34)²) Wn ≈ 18 µm

Wn = 19.9 µm → Id = 0.5mA

# Vicmin and Vincmax calculation:

 ## 📉 Input Common-Mode Range (ICMR) Analysis

The **ICMR** defines the allowable voltage range at the gates where all transistors remain in the **Saturation Region**.

---

### 1. Maximum Input Voltage ($V_{in,max}$)
To prevent $M_1/M_2$ from entering the triode region, the gate voltage must stay below the drain voltage plus one threshold voltage ($V_{th}$):

**Formula:**
$$V_{in,max} = V_{DD} - (I_D \cdot R_d) + V_{th}$$

**Calculation (Assuming $V_{th} \approx 0.36V$):**
* $V_{in,max} = 0.9V - (0.5mA \cdot 1.8k\Omega) + 0.4V$
* $V_{in,max} = 0.9V - 0.9V + 0.36V$
* **$V_{in,max} = 0.36V$**

---

### 2. Minimum Input Voltage ($V_{in,min}$)
To ensure the tail current source $I_1$ has enough "headroom" ($V_{DS,sat} \approx 0.2V$) to stay active:

**Formula:**
$$V_{in,min} = V_{SS} + V_{DS,sat} + V_{GS}$$

**Calculation (Assuming $V_{GS} \approx 0.6V$):**
* $V_{in,min} = -0.9V + 0.7 - 0.6V$
* **$V_{in,min} = -0.9v$**

---

### 📋 ICMR Summary Table

| Boundary | Condition | Value |
| :--- | :--- | :--- |
| **Upper Limit ($V_{in,max}$)** | Saturation of $M_1, M_2$ | **+0.4V** |
| **Lower Limit ($V_{in,min}$)** | Tail Source Headroom | **-0.1V** |


> For linear amplification, input common-mode signal must stay between **-0.9V and +0.36V**.
><img width="641" height="670" alt="transeient 1" src="https://github.com/user-attachments/assets/5b04c618-dcf1-4cf1-abd4-03b87e0b41e8" />

if we increase the vin values then graph will be clipped( square form)
<img width="628" height="656" alt="clipped 1" src="https://github.com/user-attachments/assets/7f0d1a3a-b006-4dd0-9a8c-42f59f484646" /><img width="1279" height="695" alt="dc exp4 1" src="https://github.com/user-attachments/assets/07da19b2-d1ab-46f4-aabb-832e838bf6c2" />

# Vocm max and vocm min calculation:

VOcmax=VDD = 0.9v

vocmin = VDD-IDRD = 0v



## 📈 Small-Signal Differential Gain ($A_d$) Analysis

The **Differential Gain ($A_d$)** defines how much the difference between the two input signals ($V_{in1} - V_{in2}$) is amplified at the output ($V_{out1} - V_{out2}$).

---

### 1. Fundamental Formula
For a MOSFET differential pair with resistive loads, the gain is given by:

$$A_d = -g_m \cdot R_d$$

Where:
- **$g_m$**: Transconductance of the NMOS transistors ($M_1, M_2$).
- **$R_d$**: Drain resistance ($1.8\text{k}\Omega$).

---

### 2. Calculating Transconductance ($g_m$)
To get an accurate gain, we first find $g_m$. Using the branch current ($I_D = 0.5\text{mA}$):

**Formula:**
$$g_m = \sqrt{2 \mu_n C_{ox} \frac{W}{L} I_D} \quad \text{or} \quad g_m = \frac{2 I_D}{V_{GS} - V_{th}}$$

*Assuming typical 0.18µm parameters ($V_{ov} \approx 0.2\text{V}$):*
- $g_m = \frac{2 \cdot 0.5\text{mA}}{0.34\text{V}} = \mathbf{2.94\text{mS (mA/V)}}$

---

### 3. Final Gain Calculation
Plugging the values into the gain equation:

$$A_d = -(2.94\text{mS}) \cdot (1.8\text{k}\Omega)$$
$$A_d = \mathbf{-5.29\text{ V/V}}$$

**In Decibels (dB):**
$$Gain(dB) = 20 \cdot \log_{10}(5.29) \approx \mathbf{14.46\text{dB}}$$

---

### 📋 Gain Summary Table

| Parameter | Symbol | Estimated Value |
| :--- | :--- | :--- |
| **Transconductance** | $g_m$ | $5\text{mS}$ |
| **Load Resistance** | $R_d$ | $1.8\text{k}\Omega$ |
| **Differential Gain** | $A_d$ | **9 V/V (14.469 dB)** |
| **Output Type** | Differential | $V_{out1} - V_{out2}$ |

# practical gain

Measured peak-to-peak value
            Measured peak-to-peak values:
* **Input Voltage:** $V_{in(p-p)} = 100\text{mV} - (-100\text{mV}) = 200\text{mV}$
* **Output Voltage:** $V_{out(p-p)} = 602\text{mV} - (-602\text{mV}) = 1204\text{mV}$

* AV= voutp-p/vinp-p

* 1204/200 === 6.02

* V(DB) =20 *log(6.02) = 15.59




# vid<root2 Vov

When the differential input voltage V_{id} (the difference between your two inputs $V_2$ and $V_3$) is less than $\sqrt{2} \cdot V_{ov}$ (where $V_{ov}$ is the overdrive voltage $V_{GS} - V_{th}$), the circuit is operating in its Linear Region.

## 📉 Operation for $V_{id} < \sqrt{2}V_{ov}$ (Linear Region)

When the differential input $V_{id}$ is small, both transistors ($M_1$ and $M_2$) remain **ON** and conduct a portion of the tail current. This is the intended operating range for an amplifier.
<img width="641" height="670" alt="transeient 1" src="https://github.com/user-attachments/assets/7c8218f9-dfaf-4aa2-bf37-64e4bd0f1f14" />



---

### 1. Current Steering Behavior
In this range, the tail current $I_{SS}$ (1mA) is shared between both branches. The current in each transistor changes linearly with the input:

- **$I_{D1} \approx \frac{I_{SS}}{2} + \frac{g_m V_{id}}{2}$**
- **$I_{D2} \approx \frac{I_{SS}}{2} - \frac{g_m V_{id}}{2}$**

As $V_{in1}$ increases, $M_1$ takes more of the 1mA current, and $M_2$ takes less, but **neither transistor is cut off yet.**

---

### 2. Output Voltage Effect
Since the currents are changing linearly, the output voltage at $V_{out1}$ and $V_{out2}$ will track the input signal accurately without significant distortion.

**Differential Output Formula:**
$$V_{out1} - V_{out2} = -g_m \cdot R_d \cdot V_{id}$$

**For your circuit:**
* The output will be a **sine wave** (if the input is a sine wave).
* The gain remains constant at approximately **5.29 V/V**.
* The output signal will be "clean" and follow the shape of the input.

---



Beyond this point ($V_{id} > \sqrt{2}V_{ov}$), the amplifier **saturates**. The output will "flat-top" or clip because the current cannot increase further than the 1mA provided by the tail source.

---

### 📋 Operation Summary

| Condition | Transistor Status | Output Behavior |
| :--- | :--- | :--- |
| **$V_{id} < \sqrt{2}V_{ov}$** | Both M1, M2 are **ON** | **Linear Amplification** (No Clipping) |
| **$V_{id} = \sqrt{2}V_{ov}$** | One is maxed, one is at 0 | **Edge of Saturation** |
| **$V_{id} > \sqrt{2}V_{ov}$** | One is **OFF** | **Output Clipping** (Distortion) |

> 
# vid>root2 Vov

## ⚠️ Operation for $V_{id} > \sqrt{2}V_{ov}$ (Current Steering/Clipping)

When the input difference is larger than $\sqrt{2}V_{ov}$, the differential pair can no longer amplify the signal linearly. The tail current is completely "steered" into one of the two transistors.
<img width="628" height="656" alt="clipped 1" src="https://github.com/user-attachments/assets/954e407c-810f-45fc-bf2a-13a0be5e6198" />

---

### 1. Transistor States (The "Switch" Effect)
In this condition:
- **One transistor ($M_1$ or $M_2$)** carries the **entire 1mA** tail current.
- **The other transistor** is completely **OFF** (Cutoff), carrying 0mA.



### 2. Output Voltage Saturation (Clipping)
Since the current in the branches can no longer increase (it is limited by the 1mA tail source), the output voltage reaches its maximum possible "swing" and stays there. This is known as **Clipping**.

**Maximum Output Levels:**
- **$V_{out,min}$**: $V_{DD} - (I_{SS} \cdot R_d) = 0.9V - (1mA \cdot 1.8k\Omega) = \mathbf{0V}$
- **$V_{out,max}$**: $V_{DD} - (0 \cdot R_d) = \mathbf{0.9V}$

The differential output ($V_{out1} - V_{out2}$) will flat-line at $\pm 0.9V$.

---

### 3. Visual Changes in the Output Waveform
If you run a **Transient Analysis (`.tran`)**, you will see the following:

- **Shape Distortion:** A sine wave input will turn into a **Square-like wave** with "flat tops."
- **Gain Drop:** The "Small-Signal Gain" ($A_v$) effectively drops to zero at the peaks because $dV_{out} / dV_{in} = 0$.
- **Harmonic Distortion:** The output will contain high-frequency harmonics because it is no longer a pure sine wave.

---

### 📋 Comparison Table

| Feature | Linear ($V_{id} < \sqrt{2}V_{ov}$) | Saturated ($V_{id} > \sqrt{2}V_{ov}$) |
| :--- | :--- | :--- |
| **Current $I_{D1}, I_{D2}$** | Both transistors share current | One is 1mA, one is 0mA |
| **Output Waveform** | Clean Sine Wave | **Clipped / Flat-topped** |
| **Transconductance** | Constant $g_m$ | $g_m$ drops to **0** |
| **Function** | Linear Amplifier | **Comparator / Switch** |

>
> **Your Simulation:** Since your input $V_2$ and $V_3$ have a 0.9V amplitude, your total $V_{id}$ is **1.8V peak-to-peak**. This is massive compared to a typical $\sqrt{2}V_{ov} \approx 0.3V$. You will see extreme clipping in  LTspice results.
>
> # AC analysis:
><img width="1278" height="725" alt="AC 1  GREEN" src="https://github.com/user-attachments/assets/562d95d9-40b0-4b14-ac3b-6b1b6e9bed78" />


AV = 14.33db

AV-3 =13.33-3= 10.33

FL=0HZ

FH =  7. 21HZ

BW = 7.21

UGB = AV * BW 

UGB = 74.47 

### CIRCUIT 2

> 








