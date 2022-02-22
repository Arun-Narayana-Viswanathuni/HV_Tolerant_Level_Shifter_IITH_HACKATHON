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
<img src=""></br>
  Fig. 1: Current Mirror 
</p>

