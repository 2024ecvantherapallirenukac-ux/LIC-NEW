Aim:

To design and analyze a Common Source amplifier using 180nm CMOS technology with current source load and to determine:

DC Operating Point
Gate Bias Voltages
Transistor Widths
Voltage Gain
Frequency Response
Given:

VDD = 1.2 V

Power ≤ 0.4 mW

CL = 0.5 pF

Technology = 180 nm

Ln = 360 nm

Vth(n) = 0.366 V

Vth(p) = 0.39 V

Circuit diagram:
<img width="1424" height="793" alt="Circuit2" src="https://github.com/user-attachments/assets/427cdc61-0d41-4818-bf6e-62c163e86605" />


Assumed parameters:

ID = 200 µA

VOV = 0.2 V

λn = 0.1

λp = 0.12

calculation:

DC Design Calculations:

Power Verification:
P = VDD × ID

P = 1.2 × 200µA

P = 0.24 mW

Since 0.24 mW < 0.4 mW

Power condition satisfied.

Gate voltage Calculations:
For M1,

VOV = VGS − VTH

VGS = 0.2 + 0.366

VGS = 0.566 V

Assume VS1 = 0.3 V

VG1 = VGS + VS1

VG1 = 0.566 + 0.3

VG1 = 0.866 V

For M2,

VS2 = 0 V

VGS2 = 0.566 V

VG2 = 0.566 V

For M3(PMOS),

0.2 = VSG − 0.39

VSG = 0.59 V

VG3 = 1.2 − 0.59

VG3 = 0.61 V

Output Voltage:
Vout ≈ VDD / 2

Vout = 1.2 / 2

Vout = 0.6 V

Saturation Verification:
M3,

VSD3 = 1.2 − 0.6

VSD3 = 0.6 V

0.6 ≥ 0.2 (satisifed)

M1,

VDS1 = 0.6 − 0.3

VDS1 = 0.3 V

0.3 ≥ 0.2 (satisified)

M2,

VDS2 = 0.3 V

0.3 ≥ 0.2 (satisified)

Width Calculations:
NMOS,

ID = (µnCox /2)(W/L)(VOV)^2

200µA = (µnCox /2)(W/360nm)(0.2)^2

Wn ≈ 7.8 µm

PMOS,

200µA = (µpCox /2)(W/360nm)(0.2)^2

Wp ≈ 18.47 µm

and we should put this values in simulation and we have to do Dc operating
for this W value we will get Id has 50uA,so we shoukd increase the width to increase the cuttent

DC operating point:
![dc op](https://github.com/user-attachments/assets/532bf4cf-12b0-4479-8ed4-92f8b0328c1f)
so at Wn =34.305um and Wp=44.873um the current is 200uA and Vout is 0.6v
baising is verified

Transient analysis:
<img width="1919" height="944" alt="Trans2b" src="https://github.com/user-attachments/assets/3437477a-c7bd-4872-9e1f-914e97c3a370" />
Vin(p-p) = 20 mV

Vout(p-p) ≈ 41.89 mV

Av ≈ 2.094 V/V

Av(dB) ≈ 6.4 d

theoretical calculation for gain:
gm = 2ID / VOV

gm = (2 × 200µA) / 0.2

gm = 2 mS

ro1 = 1 / (0.1 × 200µA)

ro1 = 50 kΩ

ro3 = 1 / (0.12 × 200µA)

ro3 = 41.66 kΩ

Rout = ro1 || ro3

Rout ≈ 22.7 kΩ

Theoretical gain:
Av = (-gm*(ro1||ro3))/(1+(gm*ro2))

Av ≈ -0.45 V/V

Av(dB) = 20 log(0.45)

Av(dB) ≈ -6.9357 dB

AC analysis:
<img width="1906" height="886" alt="ac2b" src="https://github.com/user-attachments/assets/db4bdf36-cb9f-40ef-9a14-dbd6b5442a1f" />
<img width="1893" height="921" alt="ACDB2B" src="https://github.com/user-attachments/assets/64475503-ff8a-43ad-91d2-94b5503c07f8" />

.ac dec 100 10 100G

Midband Gain ≈ 6.4 dB

fH=138.181MHz

fL=0Hz

BW = 138.151MHz

inference:

All MOSFETs operate in saturation.

Power constraint satisfied.

AC and transient gains match closely.

Result:







