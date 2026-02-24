# linear-integrated-circuite
# CS Amplifier Analysis using LTSpice

## Aim
To perform DC analysis, Transient analysis, and AC analysis of a Common Source (CS) amplifier circuit and extract various parameters using LTSpice.

## Components Required
- MOSFET (cmosn, cmosp)
-Resistor
- Voltage supply
- Connecting wires

## Theory
A **MOSFET (Metal-Oxide-Semiconductor Field-Effect Transistor)** is a type of field-effect transistor (FET) that controls the flow of current using an electric field. MOSFETs are widely used in amplifier circuits due to their high input impedance and fast switching characteristics.

A **Common Source (CS) amplifier** is a basic MOSFET amplifier configuration where the source terminal is common to both input and output. It provides voltage gain and is used in various analog applications.


## Procedure
1. Design the CS amplifier circuit using LTSpice.
2. Connect the required components as per the circuit diagram.
3. Perform DC analysis to determine the biasing conditions.
4. Perform transient analysis to study the time-domain response.
5. Perform AC analysis to extract gain and frequency response characteristics.
6. Record observations and extract relevant parameters.

# Circuit 1

<img width="1135" height="605" alt="Screenshot 2026-02-24 013038" src="https://github.com/user-attachments/assets/5823c2e4-8d24-4748-9c86-6c0064019b09" />


## DC Analysis


<img width="950" height="845" alt="Screenshot 2026-02-24 065429" src="https://github.com/user-attachments/assets/fe82441f-89cf-4bdb-aa82-b172edac4ca2" />

## Transient Analysis


![WhatsApp Image 2026-02-24 at 07 04 44](https://github.com/user-attachments/assets/176a6cfd-6b3f-48f5-8d3e-778e25f5a94e)

## AC Analysis


![WhatsApp Image 2026-02-24 at 07 05 07](https://github.com/user-attachments/assets/173b2ef8-f9dd-4743-a9d3-441ed0f1acbd)

Results
The DC analysis determined the biasing conditions of the MOSFET, verifying that the operating point is correctly set with ( I_D ) .
So the qpoint whould be ()
The Transient analysis showed the time-domain response of the CS amplifier, confirming signal amplification.
The AC analysis revealed a voltage gain of _____.
Inference
Important Parameters of CS Amplifier:

Voltage Gain (Av): Ratio of output voltage to input voltage.
Input Impedance (Zin): Resistance seen at the input terminal.
Output Impedance (Zout): Resistance seen at the output terminal.
Cutoff Frequency: Frequency at which gain drops by 3 dB from its mid-band value.
Phase Shift: The difference in phase between input and output signals.
voltage devider circuit has been impimented so that we get stable q point.
By increasing the width drain current increases.
In an actual IC transistors are replace other passive components like resistor.


