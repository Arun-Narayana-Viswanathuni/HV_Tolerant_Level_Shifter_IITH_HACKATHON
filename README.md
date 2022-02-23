# HV_Tolerant_Level_Shifter_IITH_HACKATHON

This repository presents the design of High Voltage Tolerant Level Shifter implemented using Synopsis Custom Compiler on 28nm CMOS Technology.

# Table of Contents
   * [Abstract](#abstract)
  * [Reference Circuit Details](#reference-circuit-details)
  * [Reference Circuit Diagram](#reference-circuit-diagram)
  * [Reference Circuit Waveform](#reference-circuit-waveform)
- [Simulation in Synopsys](#simulation-in-synopsys)
  * [Schematic](#schematic)
  * [Parameters set for Pulse Voltage Source for VIN](#parameters-set-for-pulse-voltage-source-for-vin)
  * [Parameters set for DC Voltage Source for VDDL](#parameters-set-for-dc-voltage-source-for-vddl)
  * [Parameters set for DC Voltage Source for VDDH](#parameters-set-for-dc-voltage-source-for-vddh)
  * [Parameters set for DC Voltage Source for Vbias](#parameters-set-for-dc-voltage-source-for-vbias)
  * [Transient Settings](#transient-settings)
  * [Netlist](#netlist)
  * [Waveform](#waveform)
  * [Conclusion](#conclusion)
  * [Acknowledgement](#acknowlegement)
  * [References](#references)


## Abstract

A High-Voltage (HV)-Tolerant Level Shifter with combinational functionality is proposed based on conventional level shifters. This level shifter is tolerant to supply voltages higher than the process limit for individual CMOS transistors. The proposed HV level shifter is particularly useful when it is mandatory to constrain the output using a logic function during out of the normal mode periods (power-up, power-down, reset, etc.). This proposed level shifter is based on 28nm CMOS logic process. [1]

## Reference Circuit Details

The HV-tolerant level shifter with the topology shown in Fig. 1. This circuit shifts both voltage levels of Xn, from ground and VDDL to Vbias = VSS and VDDH, respectively. This is an HV-tolerant level shifter, because the input circuit (Mn1 to Mn4 and Mp1 to Mp4) is powered between VDDH and ground, whose difference is higher than Vmax. Mn3 and Mn4 act as voltage limiters when Mn2 or Mn1 are off, limiting voltages VA,AN < Vbias – Vtn. Similarly, Mp3 and Mp4 limit the voltages at X2 and X2n to values higher than Vbias + | Vtp |, thus protecting Mp1 and Mp2 from overvoltage. This inverter is powered between VDDH and Vbias, and its state is controlled by the intermediate output X2 signal, with voltage levels VDDH and Vbias + | Vtp |. As a consequence, the inverter’s input nMOS transistor VGS equals | Vtp | when X2 equals Vbias + | Vtp |. This VGS value does not guarantee that the nMOS transistor is off. To overcome this drawback, two solutions can be used: 1) modify the HV-Tolerant level-shifter circuit or 2) connect a conventional level shifter at the X2 intermediate output as shown in Fig 1.

The first solution requires an additional bias voltage source in the circuit valuing VSS - | Vtp |. This new bias voltage source replaces the Vbias = VSS only in the level shifter shown in Fig 1. The level shifter presented in the second solution, shifts the X2 lower signal level from VSS + | Vtp | to VSS. The added level shifter is shown in Fig 1 This solution is implemented because it avoids static current without requiring additional bias voltages.

The HV compatibility of the level shifter shown in Fig. 1 can be extended to higher voltage values by connecting Mn3 – Mn4 – Mp3 – Mp4 in a totem pole configuration biased with appropriate voltage values.

An HV-tolerant level shifter that shifts both digital levels from VDDH and Vbias = VSS to Vbias = VDD and ground, respectively, can easily be derived from the one shown in Fig.1 using a complementary circuit topology. Such complementary level shifter can be useful when designing the shoot- through control circuit presented in some integrated dc–dc converters[1]

## Reference Circuit Diagram
<p align="center">
<img src="Images/Reference Circuit diagram.jpeg"></br>
  Fig. 1: HV Tolerant Level shifter Reference circuit Diagram 
</p>

## Reference Circuit Waveform
<p align="center">
<img src="Images/Reference Circuit waveforms.jpeg"></br>
  Fig. 1: HV Tolerant Level shifter Reference circuit Diagram 
</p>

# Simulation in Synopsys
## Schematic
![image](https://user-images.githubusercontent.com/58599984/155003310-dc58ccd8-5dc6-4d4b-94a0-c6d212ab88d7.png)
![image](https://user-images.githubusercontent.com/58599984/155003329-7643df8d-93fe-45a8-9809-77aa23e641ba.png)
Note: The transmission gate using M24 nad M25 is soley used to separate the input and output just for the simulation purpose, to plot input and output separately.
## Parameters set for Voltage Source for Input A
![image](https://user-images.githubusercontent.com/58599984/154890823-6743f686-9eed-4966-9420-56bd3a0ee0e2.png)
## Parameters set for Voltage Source for Input B
![image](https://user-images.githubusercontent.com/58599984/154891712-f6c4bfae-d422-4c86-8f40-9874719ed230.png)

## Transient Settings
![image](https://user-images.githubusercontent.com/58599984/154890716-35c2d360-befc-4476-9041-c360d751f378.png)

## Netlist
```
*  Generated for: PrimeSim
*  Design library name: Feynman_gate
*  Design cell name: Feynman_gate
*  Design view name: schematic
.lib 'saed32nm.lib' TT
*Custom Compiler Version S-2021.09
*Mon Feb 21 17:53:36 2022
.global gnd! vdd!
********************************************************************************
* Library          : Feynman_gate
* Cell             : Feynman_gate
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
xm24 p net80 a gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm7 net74 q b gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm6 q net74 b gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm5 net74 p gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm0 q b net74 gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm25 a gnd! p vdd! p105 w=0.1u l=0.03u nf=1 m=1
xm4 p q b vdd! p105 w=0.1u l=0.03u nf=1 m=1
xm3 q p b vdd! p105 w=0.1u l=0.03u nf=1 m=1
xm2 q b p vdd! p105 w=0.1u l=0.03u nf=1 m=1
xm1 net74 p net80 vdd! p105 w=0.1u l=0.03u nf=1 m=1
v26 net80 gnd! dc=1.8
v17 b gnd! dc=0.01 pulse ( 1.8 0 0.1n 0.1n 0.1n 2u 4u )
v18 a gnd! dc=0.01 pulse ( 1.8 0 0.1n 0.1n 0.1n 1u 2u )
.tran '1u' '20u' name=tran
.option primesim_remove_probe_prefix = 0
.probe v(*) i(*) level=1
.probe tran v(a) v(b) v(p) v(q)
.temp 25
.option primesim_output=wdf
.option parhier = LOCAL
.end
```
## Waveform
![image](https://user-images.githubusercontent.com/58599984/155003205-6933feb1-ec81-4627-8230-37746e44282a.png)
# Interchanging the outputs and inputs

## Schematic
![image](https://user-images.githubusercontent.com/58599984/155004055-dc48126a-26dd-4999-89d2-43b3a89d3ebf.png)
![image](https://user-images.githubusercontent.com/58599984/155004113-993a4526-4246-4214-a6da-bc1e19a51a54.png)
## Netlist
```
*  Generated for: PrimeSim
*  Design library name: Feynman_gate
*  Design cell name: Feynman_gate
*  Design view name: schematic
.lib 'saed32nm.lib' TT
*Custom Compiler Version S-2021.09
*Mon Feb 21 17:41:35 2022
.global gnd! vdd!
********************************************************************************
* Library          : Feynman_gate
* Cell             : Feynman_gate
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
xm24 p net80 a gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm7 net74 q b gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm6 q net74 b gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm5 net74 p gnd! gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm0 q b net74 gnd! n105 w=0.1u l=0.03u nf=1 m=1
xm25 a gnd! p vdd! p105 w=0.1u l=0.03u nf=1 m=1
xm4 p q b vdd! p105 w=0.1u l=0.03u nf=1 m=1
xm3 q p b vdd! p105 w=0.1u l=0.03u nf=1 m=1
xm2 q b p vdd! p105 w=0.1u l=0.03u nf=1 m=1
xm1 net74 p net80 vdd! p105 w=0.1u l=0.03u nf=1 m=1
v26 net80 gnd! dc=1.8
v17 q gnd! dc=0.01 pulse ( 1.8 0 0.1n 0.1n 0.1n 2u 4u )
v18 p gnd! dc=0.01 pulse ( 1.8 0 0.1n 0.1n 0.1n 1u 2u )
.tran '1u' '20u' name=tran
.option primesim_remove_probe_prefix = 0
.probe v(*) i(*) level=1
.probe tran v(a) v(b) v(p) v(q)
.temp 25
.option primesim_output=wdf
.option parhier = LOCAL
.end
```
## Waveform
![image](https://user-images.githubusercontent.com/58599984/155003970-690e6a0e-0664-4543-96f0-a0aa1cea5a87.png)
## Conclusion
Thus, the input and output can be interchanged in the Feynman Gate and the functionality of the Feynman Gate is verified using 32nm Technology node of Synopsys.
## Acknowledgement
1. Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd. - kunalpghosh@gmail.com
2. Chinmay panda, IIT Hyderabad
3. Sameer Durgoji, NIT Karnataka
## References
1.	U. Kumar, L. Sahu and U. Sharma, "Performance evaluation of reversible logic gates," 2016 International Conference on ICT in Business Industry & Government (ICTBIG), 2016, pp. 1-4, doi: 10.1109/ICTBIG.2016.7892693.
2.	A. K. Rajput, S. Chouhan and M. Pattanaik, "Low Power Boolean Logic Circuits using Reversible Logic Gates," 2019 International Conference on Advances in Computing, Communication and Control (ICAC3), 2019, pp. 1-6, doi: 10.1109/ICAC347590.2019.9036799.

