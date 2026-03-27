DIFFERENTIAL AMPLIFIER

CIRCUIT 1

Aim:

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

 DC analysis:

 In the ideal balanced state (V_{in1} = V_{in2}), the tail current I_{SS} (labeled I1 in your schematic) splits equally between the two transistors (M1 and M2).

 I_{D1} = I_{D2} = \frac{I_{SS}}{2}
 
 I_{SS} = 1\text{mA}

 V_{out(DC)} = V_{DD} - (I_D \cdot R_d)

 0 = o.9-Rd*0.5mA

 Rd = 1.8k

 Verification for  circuit:

 V_{DD} = 0.9\text{V}
 


