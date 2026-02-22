COMMON SOURCE AMPLIFIER
Aim:
To perform the DC, Transient, AC Analysis of a Common Source amplifier circuit using LTSpice and extract the associated parameters.
Components Required:
TSMC 180nm NMOS transistor (CMOSN), a drain resistor and voltage sources(2).
circuit diagram
<img width="1586" height="1085" alt="Screenshot 2026-02-16 163209" src="https://github.com/user-attachments/assets/f07cad1a-973a-4703-9921-cba2da190a6e" />
Given paramters:
VDD=2V
P<=1.2mw
Cl=0.7pf
Length=180nm
Vth=0.36

Procedure:
1.Design the CS amplifier as per the circuit diagram using LTSpice.
2.Set the components values as per the given parameters.
3.Create a new folder and save the LTSpice file in this folder along with the library file
4.Calculate the drain current value for the given power=1.2mW.
Calculation:
P=V*I  ---------(1)
From 1st equation we will get I
I=p/v
I=0.6mA (assume I is 200mA because p<=1.2mw)
Vout=VDD-I*Rd ---------(2)
Vout=Vds(VDD/2)------(3)
Subst 3 in 2 
VDD/2=VDD-I*Rd
From this equation v will get Rd as 5kohm
Find W from Id equation 
Id=kn*0.5*(Vgs-Vth)^2 --------(4)
Vgs=0.9v,Vth=0.36v,id=200mA,un=273.8094484,tox=4.1*10^-9,eox=3.45306*10^-11
From 4th equation v will get w=1.07072um
Enter this value in Ltspice and do dc analysis 
DC analysis:
DC Analysis is done to check if the MOSFET is operating in the saturation region and to obtain the DC operation point.
1.After setting up the circuit as per the circuit diagram, apply the dc voltage VDD=2V and Vgs=0.9V.
2.Go to Simultae option in the tab and the DC opt option and click 'ok'.
3.Click on run to run the circuit.
4.DC operating point is obtained.
<img width="870" height="568" alt="Screenshot 2026-02-16 163045" src="https://github.com/user-attachments/assets/14aa2b18-172a-458e-9185-ca627ad3a2b1" />
<img width="931" height="764" alt="Screenshot 2026-02-22 101116" src="https://github.com/user-attachments/assets/4c949e0b-571d-4243-b38c-97ede1e65a35" />
From LT SPICE we are getting I has 186mA ,so vary the width to get I has 200mA if width increases ,current also will increase(directly proportional)
At w=1.377u we will get I has 200mA .
AC Analysis
1.Go to simulate option and click on AC analysis and enter the time of sweep as decade, no. of points as 20, frequency 0.1Hz-1THz.
2.Click ok and run the circuit to obtain the gain and frequency response of the circuit.
<img width="2559" height="1463" alt="Screenshot 2026-02-16 162750" src="https://github.com/user-attachments/assets/ecfbaacf-ae96-4190-b0a2-9c9aebbe9d47" />
Gain=-gm*Rd
Gain=2I*Rd/Vov
Gain=3.7037v
Gain in dB=11.372012

Transient Analysis:
1.Apply a sine wave input of frequency 1KHz and amplitude 10mV and Vgs=0.9V.
2.Go to simulate option in the tab and click on transient analysis and enter the stop time as 5ms(.tans 5ms).
3.Run the circuit and observe the response of the circuit to a time varying signal.
<img width="2557" height="1478" alt="Screenshot 2026-02-16 160254" src="https://github.com/user-attachments/assets/7bca256c-9032-43dd-a744-2e8731796dd5" />
Av=gain=VOUT/VIN
AV=2.7756, AVdB=8.86713

Bandwidth:
BW=fh-fl=fh=22.2336GHz
<img width="2558" height="1490" alt="Screenshot 2026-02-22 112655" src="https://github.com/user-attachments/assets/9fbf128d-6621-475a-8ed2-d0234ceb32a6" />

Inference

DC Analysis
Current directly depends on the width of the MOSFET.Current varies with the width of the MOSFET.
Variation in Id is due to the channel length modulation.
If Id is too low, we need to increase W for proper biasing.

Transient Analysis
Analysis used to determine the signal distortion, DC shift between input and output and signal amplification.
Vds needs to be checked to ensure saturation if distortion occurs.
Increase in gain if there is low amplitude output.

AC Analysis
Small signal analysis of the circuit to determine the gain of the circuit.
We observe that there is low gain due to low value of gm and rd.Increase gm and Rd to increase gain of the circuit.
