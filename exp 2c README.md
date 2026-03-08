AIM:

To design and simulate three MOSFET amplifier configurations using 180 nm CMOS technology in LTspice, perform DC, transient, and AC analyses, and compare their gain, bandwidth, power consumption, and overall performance.

Given Specifications
VDD = 1.2 V
ID = 200 µA
VOV = 0.2 V
CL = 0.5 pF
Ln = Lp = 180 nm
P<= 0.4mW
εr = 3.9
ε0 = 8.854 × 10⁻¹² F/m
tox = 4.1 × 10⁻⁹ m
μn = 273.809 cm²/Vs
μp = 115.689 cm²/Vs

Circuit  diagrram:
<img width="1070" height="607" alt="CIRCUIT 2C" src="https://github.com/user-attachments/assets/53a468f0-4786-402b-9e08-92eb6314094a" />

Calculations:

VOv=0.2v

VOV=VGS-VTH (NMOS)
VOV+VTH=VGS
0.2+0.36=VGS
VGS=0.56V
VS=0
VG=0.56V (M2)
VG=VD(FIXED BAISING)

VGS=VTH+VOV
VGS=VTH+0.2V
VGS=0.56V
VS OF M1 is equal to Vd of M2
vs=0.56v
vg=0.56+0.56=1.12v  (M1)

VSG=VTH+VOV
   =0.39+0.2
   0.61v
vs=vdd=1.2v
vg=0.61v  (M3)

Check Regions of Operation
M1 (Amplifying NMOS)

Source = Vro3 = 0.556 V

Gate = Vin = 1.12 V

VGS1​=1.12−0.556
VGS1​=0.564V
VOV1​=VGS​−VTN​







