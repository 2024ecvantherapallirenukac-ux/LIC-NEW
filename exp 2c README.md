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

Check Regions of Operation:

M1 (Amplifying NMOS)

Source = Vro3 = 0.556 V

Gate = Vin = 1.12 V

VGS1​=1.12−0.556

VGS1​=0.564V

VOV1​=VGS​−VTN

VOV1​=0.564−0.36

VDS1​=0.882−0.556

VDS1​=0.326V

VDS1​>VOV1​

0.326>0.204

✅ M1 is in saturation

M2 (Diode Connected NMOS)

VDS2​=VGS2​

VGS2​=0.556V

VGS2​−VTN​=0.556−0.36 =0.196v

VDS2​=0.556>0.196

✅ M2 is in saturation

M3 (PMOS Load)

Source = 1.2V

Gate = 0.61V

VSG3​=1.2−0.61

VOV3​=0.59−0.39

V0v3=0.20V

Drain = 0.882V

VSD3​=1.2−0.882=0.318v

VSD3​>VOV3​

0.318>0.20

✅ PMOS also in saturation

1. Maximum Output Voltage

maximum output voltage
Upper limit occurs when PMOS M3 leaves saturation.

VSD3​≥VOVp

VSD3​=VDD​−Vout​

At boundary:

Vout,max​=VDD​−VOVp​

Vout,max​=1.2−0.20=1.0v

2. Minimum output voltage:

Lower limit occurs when NMOS M1 leaves saturation.

Condition:

 VDS1​≥VOV

 VDS1​=Vout​−Vro3

 Vout,min​=Vro3​+VOVn​)(at boundaries)

 Vout,min​=0.556+0.20 = 0.756v

 Check Symmetry

 Vout,Q​=0.882V

 Upper swing:

1.0−0.882=0.118V

lower swing : 0.882−0.756=0.126V

ID = (1/2) µ Cox (W/L) VOV²
Rearranging for W: W = (2 ID L) / (µ Cox VOV²)

NMOS Width Calculation
Wn = (2 × 200×10⁻⁶ × 0.18×10⁻⁶)
/ (0.02738 × 8.42×10⁻³ × (0.1)²)

Numerator: = 7.2 × 10⁻¹¹
Denominator: = 2.305 × 10⁻⁶
Wn = 3.12 × 10⁻⁵ m
Wn = 31.2 µm

NMOS Width
Wn ≈ 31 µm

(M1 and M3 if identical)

PMOS Width Calculation
Wp = (2 × 200×10⁻⁶ × 0.18×10⁻⁶)
/ (0.01157 × 8.42×10⁻³ × (0.1)²)

Denominator: = 9.74 × 10⁻⁷
Wp = 7.39 × 10⁻⁵ m
Wp = 73.9 µm

PMOS Width
Wp ≈ 74 µm
 if we uplad this value in simulation we will get Id has 120uA ,to get Id has 200uA we should increase the wisth


DC analysis:
<img width="470" height="391" alt="DC 2C" src="https://github.com/user-attachments/assets/05a0807c-b6c6-4723-9fe0-8051da33adbd" />


so at wp=49.6u and wn=33.567u we willl get Id has approx 200uA

Transient analysis:
<img width="1280" height="704" alt="trasneint 2c" src="https://github.com/user-attachments/assets/6d0aa6f1-23a9-4e63-846e-3aa3c336e83a" />

AV=10.6
AV(db)=20*log(10.6)
     =20.506

AC analysis:
<img width="1280" height="703" alt="AC analysis" src="https://github.com/user-attachments/assets/b6a50550-f025-4049-a6b1-860ec7911503" />


     
     


​


​







