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

<img width="1457" height="747" alt="Screenshot 2026-03-01 222655" src="https://github.com/user-attachments/assets/d79b51e6-aef7-4d74-8c0d-951b917590d2" />



## DC Analysis
## DC Operating Point

### Perform DC Operating Point Analysis
1.Go to: Simulate → Edit Configure Analysis → Operating Point

2.Place the .op command on schematic.

3.Run simulation.

4.Note:

- ID

- VDS

- VGS

5.Verify MOSFET operates in saturation region.
<img width="846" height="635" alt="image" src="https://github.com/user-attachments/assets/060bffcc-5f7e-49aa-b008-44952559ca2c" />
## DC Sweep

### Perform DC Sweep Analysis
1. Go to:
   Simulate → Edit Configure Analysis → DC Sweep
2. Select:
   - Sweep Variable: Voltage source (Vin)
   - Start: 0 V
   - Stop: 1.8 V
   - Step: 0.01 V
3. Run simulation.
4. Plot V(out) vs Vin.
5. Identify:
   - Steepest curve (for different RD values).
6. Choose midpoint:
   Vout ≈ VDD/2 = 0.9 V
7. Note corresponding Vin → DC Offset (0.549 V).
<img width="950" height="845" alt="Screenshot 2026-02-24 065429" src="https://github.com/user-attachments/assets/fe82441f-89cf-4bdb-aa82-b172edac4ca2" />

<img width="1918" height="850" alt="dcsweep90k" src="https://github.com/user-attachments/assets/c2b135ba-ed13-469d-a492-07361e70dc23" />


### Drain Current

From DC operating point:

ID = 6.84951 × 10⁻⁶ A  
ID = 6.85 µA  

---

### Output Voltage Calculation

Formula:

Vout = VDD − (ID × RD)

Substituting values:

Vout = 1.8 − (6.85 × 10⁻⁶ × 130000)

Vout = 1.8 − 0.8905  

Vout ≈ 0.91 V  

This confirms the midpoint condition (≈ 0.9 V).

---

### Saturation Condition Check

Condition for saturation:

VDS > (VGS − VT)

Assuming:

VT ≈ 0.45 V  
VGS = 0.549 V  

VGS − VT = 0.099 V  

Since:

VDS ≈ 0.9 V >> 0.099 V  

The MOSFET operates in saturation region.

---


# Effect of Varying R

- Increasing R increases gain.
- Increasing R reduces bandwidth.
- Demonstrates gain–bandwidth tradeoff.
  

<img width="1918" height="850" alt="dcsweepvarR" src="https://github.com/user-attachments/assets/19981c97-ca8f-4314-8324-f06d2bae609b" />



# Effect of Varying W

- Increasing W increases drain current.
- gm increases.
- Gain increases.
- Q-point shifts left in transfer curve.

<img width="1918" height="847" alt="dcsweepvarW" src="https://github.com/user-attachments/assets/da82d59c-a5eb-44d5-93bb-1497dde596a0" />


### Observations:

- Increasing R increases voltage gain.
- Steepest transfer characteristic observed for R = 130kΩ.
- Midpoint condition:

    Vout = VDD / 2 = 0.9 V

- Corresponding input bias voltage:

    Vin = 0.549 V


### Inference:

- MOSFET operates in saturation region at selected Q-point.



# Transient Analysis and Calculations


### Input Applied :

SIN(0.549 10m 1k)

- DC offset = 0.549 V
- Amplitude = 10 mV
- Frequency = 1 kHz

  
## Procedure 

### Modify Input Source
Set input as:

SIN(0.549 10m 1k)

Where:
- 0.549 = DC offset
- 10m = amplitude
- 1k = frequency



### Step Add Transient Command
1. Go to:
   Simulate → Edit Configure Analysis → Transient
2. Set stop time (e.g., 5ms).
3. Place .tran command.
   


### Run Simulation
1. Click on output node (V(out)).
2. Click on input node (V(in)).
3. Split pane if required:
   Plot Settings → Add Plot Pane
   


### Observe
1. Confirm:
   - Output is inverted (180° phase shift).
   - No clipping.
2. Measure amplitude.
3. Calculate gain = Vout/Vin.


<img width="1918" height="847" alt="transient analysis" src="https://github.com/user-attachments/assets/629a7607-7053-4e9e-a9d5-981fe7ba9a09" />


### Input Signal

Vin = 0.549 + 10mV sin(2πft)  

Where:

f = 1 kHz  

---

### Gain Conversion (from AC result)

Midband Gain ≈ 30 dB  

Linear gain:

Av = 10^(30/20)

Av ≈ 31.6  

---

### Output Amplitude

Input amplitude = 10 mV  

Output amplitude:

Vout = 31.6 × 10 mV  

Vout ≈ 316 mV  

Output swings around:

0.9 V ± 0.316 V  

Range:

0.584 V to 1.216 V  

No clipping observed.



### Observations:

- Output waveform is inverted (180° phase shift).
- Output DC level ≈ 0.9 V.


### Inference:

- CS amplifier shows proper amplification.
- Amplifier operates in active region.



# AC Analysis and Calculations

### AC Command Used :

.ac dec 10 100 1G

## Procedure 

### Step Modify Input Source
1. Keep DC value = 0.549 V.
2. Set AC amplitude = 1.



### Add AC Command
1. Go to:
   Simulate → Edit Simulation Cmd → AC Analysis
2. Select:
   - Type: Decade
   - Points/decade: 100
   - Start: 1 Hz
   - Stop: 1 GHz
3. Place .ac command.



### Run Simulation
1. Click output node.
2. Plot:
   dB(V(out)) for gain.
3. Observe:
   - Midband gain
   - -3 dB cutoff frequency
   - Phase response



<img width="1916" height="850" alt="image" src="https://github.com/user-attachments/assets/1c06dc4f-a527-41ee-b125-6a9f7de44b35" />



### Transconductance (gm)

Formula:

gm = 2ID / (VGS − VT)

gm = (2 × 6.85 µA) / 0.099  

gm ≈ 0.000138 A/V  

gm ≈ 0.138 mS  

---

### Theoretical Voltage Gain

Av = −gm × RD  

Av = −(0.000138 × 130000)

Av ≈ −17.9  

(Theoretical value slightly differs due to model parameters and parasitic effects.)

---

### High Frequency Cutoff

Output load capacitor CL = 1 pF  

Formula:

fH = 1 / (2πRC)

fH = 1 / (2π × 130k × 1pF)

fH ≈ 1.22 MHz  

This matches the simulated cutoff frequency (~1 MHz).

---

### Bandwidth

Since no coupling capacitors are used:

- Bandwidth ≈ fH  

- Bandwidth ≈ 1 MHz  

---


### Observations:
- High-frequency cutoff ≈ 1 MHz

- Phase shift confirms inverting behavior.
 
## Results
The DC analysis determined the biasing conditions of the MOSFET, verifying that the operating point is correctly set with ( I_D )=6.85 µA .

So the qpoint whould be ( 0.9v , 6.85 µA).

The Transient analysis showed the time-domain response of the CS amplifier, confirming signal amplification.

The AC analysis revealed a voltage gain of 19.95 (from graph).

## Inference
Important Parameters of CS Amplifier:

Voltage Gain (Av): Ratio of output voltage to input voltage.

Input Impedance (Zin): Resistance seen at the input terminal.

Output Impedance (Zout): Resistance seen at the output terminal.

Cutoff Frequency: Frequency at which gain drops by 3 dB from its mid-band value.

Phase Shift: The difference in phase between input and output signals.

voltage devider circuit has been impimented so that we get stable q point.

By increasing the width drain current increases.

In an actual IC transistors are replace other passive components like resistor.


