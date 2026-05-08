## INTEGRATOR AND DIFFERENTIATOR USING OP-AMP

---

### AIM

To design and simulate Integrator and Differentiator circuits using Op-Amp (µA741) and observe the output waveforms for square, triangular, and sine wave inputs.

---

### COMPONENTS / PARTS REQUIRED

| Component | Specification / Value |
|---|---|
| Op-Amp IC | µA741 (LM741) |
| Resistors | 15 kΩ (R1), 470 kΩ (R2), 15 kΩ (Rf) |
| Capacitors | 0.01 µF |
| Signal Generator | — |
| DC Power Supply | ±12 V |
| CRO / Output Meter | — |

**Virtual Lab Reference:** https://be-iitkgp.vlabs.ac.in/exp/operational-amplifier/theory.html

---

### THEORY

**Operational Amplifier (Op-Amp)** is a linear electronic device with three terminals: two high-impedance inputs and one output. It can perform multiple functions depending on the feedback combination (resistive, capacitive, or both). The ideal Op-Amp has infinite open-loop gain, infinite input impedance, zero output impedance, zero offset voltage, and infinite bandwidth.

#### INTEGRATOR

The integrator circuit is designed so that the output is proportional to the amplitude and duration of the input signal — it performs mathematical integration. The circuit is identical to an inverting amplifier, except the feedback resistor is replaced by a capacitor, making the circuit frequency-dependent.

When voltage is applied, the initially uncharged capacitor allows maximum current to flow. Due to virtual ground at the inverting input, no current flows into the Op-Amp. The capacitor charges at the rate of the RC time constant; as its impedance increases, the charging current decreases, producing a linearly increasing ramp output that continues until the capacitor is fully charged.

**Output voltage expression:**

$$V_o = -\frac{1}{RC} \int V_i \, dt + k$$

where $k$ is the constant of integration (depends on $V_o$ at $t = 0$).

The peak output voltage $V_T$ is given by:

$$V_T = \frac{VT}{4RC}$$

where $T$ is the time period of the input square wave.

> **Applications:** Analog computers, wave-shaping networks, ramp generators.

---

#### DIFFERENTIATOR

The differentiator circuit has its input connected to the inverting terminal of the Op-Amp through a capacitor (C), and negative feedback is provided through a resistor (Rf). It is essentially an integrator with the feedback capacitor and input resistor swapped.

The output is the first derivative of the input signal — 180° out of phase and amplified by a factor of $R_f \times C$. The input capacitor blocks DC and passes only AC. At low frequencies, capacitive reactance is high, resulting in low gain. At high frequencies, gain increases but the circuit becomes unstable and susceptible to noise.

**Output voltage expression:**

$$V_o = -R_f C_i \frac{dV_i}{dt}$$

The differentiator acts as a **high-pass filter**. At high frequencies it becomes unstable and may oscillate. Both stability and noise problems can be mitigated by adding a small series resistor $R_1$ in series with the input capacitor and a small capacitor $C_f$ in parallel with $R_f$ (practical differentiator).

---


### CIRCUIT DIAGRAMS

####  Integrator Circuit 

###### Therotical 

<img width="582" height="237" alt="image" src="https://github.com/user-attachments/assets/3a0da8a0-6601-469a-b8b1-ccd493e346c2" />

###### Simulator

<img width="531" height="382" alt="ckt for int" src="https://github.com/user-attachments/assets/c47b2a65-a88c-47c7-af87-42981683b2ba" />

---

#### Differentiator Circuit 

###### Therotical 

<img width="536" height="251" alt="image" src="https://github.com/user-attachments/assets/59856a05-c1da-4fa6-b541-a804e297be2d" />

###### Simulator

<img width="536" height="392" alt="ckt for diff" src="https://github.com/user-attachments/assets/ce241155-9cb4-4db4-8790-c1ab1244e060" />

---


### PROCEDURE

#### Integrator

1. Set up the integrator circuit as shown in Fig. 3. Apply a rectangular (square) wave of ±5 V (10 V peak-to-peak) at 1 kHz to the input. Observe both input and output simultaneously on the CRO.
2. Vary the DC offset of the square wave input and observe the change in the output waveform.
3. Repeat the experiment by feeding a **triangular wave** at the input. Observe and record the output.
4. Repeat the experiment by feeding a **sine wave** at the input. Observe and record the output.

#### Differentiator

1. Set up the differentiator circuit as shown in Fig. 4. Apply a rectangular (square) wave of ±5 V (10 V peak-to-peak) at 1 kHz to the input. Observe both input and output simultaneously on the CRO.
2. Repeat the experiment by feeding a **triangular wave** at the input. Observe and record the output.
3. Repeat the experiment by feeding a **sine wave** at the input. Observe and record the output.

---

### WAVEFORMS

####  Integrator Output (Square wave input → Triangular wave output)

<img width="603" height="602" alt="square outputp for int" src="https://github.com/user-attachments/assets/d21d5d09-ff53-40f3-bc78-857a701134fc" />

####  Integrator Output 

<img width="602" height="603" alt="sine outputp for int" src="https://github.com/user-attachments/assets/13ae090c-e307-468d-aa5c-5f6235c35a57" />

---

####  Differentiator Output (Square wave input → Pulse/spike output)

<img width="603" height="605" alt="square outputp for diff" src="https://github.com/user-attachments/assets/9f9801aa-06a4-404f-b217-1cc6b920066d" />


####  Differentiator Output 

<img width="606" height="602" alt="outputp for diff" src="https://github.com/user-attachments/assets/0f3f95c4-0070-41ce-8987-f8d628a73215" />

---

### INFERENCE

The Op-Amp integrator circuit produces an output that is the mathematical integral of the input signal. A square wave input yields a triangular wave, confirming that the integral of a constant is a ramp. 
The Op-Amp differentiator produces the mathematical derivative of the input; a square wave input gives narrow impulse spikes at each edge, confirming differentiation of step transitions.




---


