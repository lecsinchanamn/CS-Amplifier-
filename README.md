# Experiment No 02
# CS Amplifer (common source Amplifer) Configurations using (tsmc 180nm)
# AIM
 Design the CS Amplifer Configuration using tsmc180nm.
 # Configuration
 1. CS Amplifer with Source Degeration.
 2. Casecode Amplifer.
 3. Current Mirror Loaded with Current Mirror Common.
 # Softer uses
 LT spice simulation with tsnc 180nm Technology.
 # what is MOS Amplifer?
The main component is a MOSFET (Metal-Oxide-Semiconductor Field Effect Transistor)
1.Gate (G) – where the input signal is given
2.Drain (D) – where the output comes from
3.Source (S) – reference terminal
 # How it works ?
1.A small voltage is applied to the gate.
2.The MOSFET controls the current flowing inside the circuit.
3.The output at the drain becomes stronger than the input signal.
# What is CS Amplifer with Source Degeration and it's related equation?
A Common Source amplifier with source degeneration is a MOSFET amplifier where a resistor is added in the source terminal to improve stability and linearity.

| Parameter            | Equation                        |
|----------------------|---------------------------------|
| Drain Current (ID)   | ID = (1/2) * kn * (VGS - VT)^2  |
| Transconductance     | gm = 2ID / (VGS - VT)           |
| Transconductance     | gm = sqrt(2 * kn * ID)          |
| Voltage Gain (Av)    | Av = -(gm * RD) / (1 + gm * RS) |
| Input Resistance     | Rin ≈ ∞                         |
| Output Resistance    | Rout ≈ RD                       |
# What is the Casecode Amplifer and it's realated eqation?
A Cascode amplifier is an amplifier that uses two transistors connected one above the other to increase gain and bandwidth.
| Parameter                | Equation                              |
|--------------------------|--------------------------------------|
| Drain Current (ID)       | ID = (1/2) * kn * (VGS - VT)^2       |
| Transconductance (gm)    | gm = 2ID / (VGS - VT)                |
| Transconductance (gm)    | gm = sqrt(2 * kn * ID)               |
| Output Resistance (Rout) | Rout ≈ gm * ro^2                     |
| Voltage Gain (Av)        | Av ≈ -gm * RD                        |
| Input Resistance (Rin)   | Rin ≈ ∞                              |
# What is the Current mirror loaded common source amplifer and it's realted eqatuin?
A Current mirror loaded common source amplifier is a common source (CS) MOS amplifier where the load resistor is replaced by a current mirror to obtain higher gain and better performance.
| Parameter                 | Equation                         |
|---------------------------|----------------------------------|
| Drain Current (ID)        | ID = (1/2) * kn * (VGS - VT)^2   |
| Transconductance (gm)     | gm = 2ID / (VGS - VT)            |
| Transconductance (gm)     | gm = sqrt(2 * kn * ID)           |
| Voltage Gain (Av)         | Av = -gm * (ro || ro)            |
| Output Resistance (Rout)  | Rout = ro || ro                  |
| Input Resistance (Rin)    | Rin ≈ ∞                          |
# Camparision btween three configuration
| Feature / Parameter          | CS Amplifier with Source Degeneration | Cascode Amplifier                   | Current Mirror Loaded CS Amplifier |
|-------------------------------|--------------------------------------|-----------------------------------|----------------------------------|
| Main Idea                     | CS stage with source resistor RS     | CS stage + CG stage in series      | CS stage with current mirror as load |
| Voltage Gain (Av)             | Av = -gm * RD / (1 + gm * RS)       | High, Av ≈ -gm * RD                | Very high, Av ≈ -gm * (ro || ro) |
| Input Resistance (Rin)        | High, Rin ≈ ∞                        | High, Rin ≈ ∞                       | High, Rin ≈ ∞                     |
| Output Resistance (Rout)      | Rout ≈ RD                             | High, Rout ≈ ro                     | High, Rout ≈ ro || ro             |
| Frequency Response            | Moderate                              | High, better than CS                | High, due to active load          |
| Stability / Linearity         | Improved (RS provides negative feedback) | Good                                | Moderate to good                   |
| Advantages                    | Simple, stable, reduces distortion    | High gain, high frequency          | Very high gain, compact IC design |
| Disadvantages                 | Gain lower than simple CS without RS   | More complex than simple CS         | Requires extra transistors for current mirror |
| Category / Concept                 | Equation / Value / Formula                                          | Notes / Variables |
# Equation requaried for the sloving circuit
| Category / Concept                 | Equation / Value / Formula                                          | Notes / Variables |
|-----------------------------------|--------------------------------------------------------------------|------------------|
| Device Parameters (TSMC 180 nm)   | Supply Voltage: VDD = 1.8 V                                        |                  |
|                                   | Target Drain Current: ID = 200 µA                                   |                  |
|                                   | NMOS Threshold: VTHn = 0.36 V                                       |                  |
|                                   | PMOS Threshold: VTHp = −0.39 V                                      |                  |
|                                   | Channel Length: L = 560 nm                                          |                  |
| Oxide Parameters                   | Oxide Permittivity: εox = 3.54 × 10⁻¹¹ F/m                          |                  |
|                                   | Oxide Thickness: tox = 4.1 × 10⁻⁹ m                                 |                  |
|                                   | Oxide Capacitance: Cox = εox / tox = 8.634 × 10⁻³ F/m²             |                  |
|                                   | Relative Permittivity: εr                                           |                  |
| Saturation Conditions              | NMOS: VDS ≥ VGS − VTHn                                              | Ensures MOSFET in saturation |
|                                   | PMOS: VSD ≥ VSG − |VTHp|                                             | Ensures MOSFET in saturation |
| Process Transconductance           | NMOS: μnCox = μn × Cox = 2.363 × 10⁻⁴ A/V²                          |                  |
|                                   | PMOS: μpCox = μp × Cox = 9.99 × 10⁻⁵ A/V²                           |                  |
| Saturation Current Equation        | ID = (1/2) × μCox × (W/L) × (VOV)²                                   | VOV = Overdrive Voltage |
| Width Calculation (W)              | W = (2 × ID × L) / [μCox × (VOV)²]                                  | Rearranged from saturation current |
|                                   | NMOS Width: WNMOS = 15.16 µm                                        | Using above formula |
|                                   | PMOS Width: WPMOS = 35.9 µm                                         | PMOS ≈ 2.3 × NMOS width |
| Observation / Notes                | NMOS mobility > PMOS mobility → NMOS requires smaller width         |                  |
|                                   | PMOS width ≈ 2.3 × NMOS width for same current                      |                  |
# CIRCUIT 01
# AIM
To design and implement a source-degenerated common source amplifier for ID = 200 µA with maximum symmetric output swing.
# Circuit diogram
https://github.com/lecsinchanamn/CS-Amplifier-/blob/96a6047638f61841df37029962a0f7b1299b8075/C1%20circuit%20diogram.jpeg
# DC Analysis
# DC Analysis design condition
| Parameter              | Value   |
|------------------------|---------|
| Supply Voltage (VDD)   | 1.8 V   |
| Target Drain Current (ID) | 200 µA |
| NMOS Threshold (VTHn)  | 0.36 V  |
| PMOS Threshold (VTHp)  | −0.39 V |
# Bias Design and voltage selection In Saturation Operation
| Parameter       | Minimum         | Maximum       | Reason                          |
|-----------------|----------------|---------------|--------------------------------|
| VGS (NMOS)      | ≥ VTH = 0.36 V | ≤ VDD = 1.8 V | Required for channel formation |
| VDS (NMOS)      | ≥ Vov           | ≤ VDD         | Required for saturation        |
| VSG (PMOS)      | ≥ VTHp = 0.39 V |               |                                |
| VSD (PMOS)      | ≥ Vov           | ≤ VDD         | Required for saturation        |
# Output Voltage for the maximum Swing
Get the maximum output swing, the NMOS drain voltage is set near half of the supply voltage.
| Calculation       | Result       |
|------------------|-------------|
| VDS = VDD / 2     | 1.8 / 2 = 0.9 V |
# Source Voltage Selection
A small source voltage is introduced using a source resistor to provide negative feedback and bias stabilization.
| Parameter | Value  |
|-----------|--------|
| VS        | 0.2 V  |
# Output voltage / Source Resister calucations and NMOS Voltage Verifition / Overdrive Rnage
| Parameter                     | Calculation / Result                       |
|-------------------------------|-------------------------------------------|
| Output Voltage (Vout)          | VDS = Vout − VS → 0.9 = Vout − 0.2 → Vout = 1.1 V |
| Source Resistor (RS)           | RS = VS / ID → 0.2 / 200µA = 1 kΩ        |
| NMOS Gate Bias (VGS)           | VGS = VTH + Vov → 0.36 + 0.25 = 0.61 V   |
| NMOS Gate Voltage (VG)         | VG = VGS + VS → 0.61 + 0.2 = 0.81 V      |
| Overdrive Voltage Verification | VGS = VG − VS → 0.81 − 0.2 = 0.61 V      |
| Overdrive Voltage Verification | Vov = VGS − VTH → 0.61 − 0.36 = 0.25 V   |
| Allowable Overdrive Range      | 0 < Vov < VDS → 0 < 0.25 < 0.9 V         |

We have Overdrive range becase
Thus
0 < Vov < 0.9
The obtained value Vov = 0.25 V lies well within this allowable range.
# POMOS bias calucation and Saturation Verification
| Parameter / Device              | Calculation / Condition                     | Result  |
|--------------------------------|--------------------------------------------|---------|
| PMOS Gate-Source Voltage (VSG)  | VSG = Vov + VTHp → 0.25 + 0.39            | 0.64 V  |
| PMOS Gate Voltage (VGp)         | VGp = VDD − VSG → 1.8 − 0.64              | 1.16 V  |
| NMOS Saturation Check           | VDS ≥ Vov → 0.9 ≥ 0.25                     | ✔       |
| PMOS Saturation Check           | VSD ≥ Vov → 0.7 ≥ 0.25                     | ✔       |

✅ This one table now includes both PMOS gate bias calculations and NMOS/PMOS saturation verification clearly.
# DC Operating Point
| Parameter          | Value       |
|-------------------|------------|
| Source Voltage (VS)| 0.2 V      |
| Drain-Source Voltage (VDS) | 0.9 V |
| Output Voltage (Vout)      | 1.1 V |
| NMOS Gate Voltage (VG)     | 0.81 V |
| PMOS Gate Voltage (VGp)    | 1.16 V |

1.The bias point keeps both NMOS and PMOS transistors in saturation.
2.This allows maximum output swing without distortion.
3.It provides enough voltage headroom for the output signal.
https://github.com/lecsinchanamn/CS-Amplifier-/blob/70376820038862b376ba638e759f4d7787873038/C1%20DC%20Analysis.jpeg
# Transient Analysis 
A small sinusoidal signal was applied to the gate of the source-degenerated common-source amplifier to analyze its time-domain response.
| Waveform Type | Frequency | Amplitude | DC Offset | LTspice Input Command |
|---------------|-----------|-----------|-----------|---------------------|
| Sine          | 1 kHz     | 10 mV     | 0.81 V    | V1 N001 0 SIN(0.81 0.01 1k) |
The DC offset corresponds to the calculated gate bias voltage required to maintain ID ≈ 200 µA.
# Input Waveform
https://github.com/lecsinchanamn/CS-Amplifier-/blob/bff5e321dfe553754a48edd6285e629573bfa983/C1%20TA%20ip%20wave.jpeg
The seems the sinusoidal input which is applied to the gate terminal.
# Output Waveform
https://github.com/lecsinchanamn/CS-Amplifier-/blob/45ae96166965a094bb6a9a214d3a664b2a9166f2/C1%20TA%20op%20wave.jpeg
The output signal is inverted with repect to the large amplitude.
# Input and output 
https://github.com/lecsinchanamn/CS-Amplifier-/blob/9635ce3df65668b926326c989acc58176b7dcf5e/C1%20TA%20IO%20wave.jpeg
The both input and output sihnal give the 180 dgree phase sift.
# Pratical Gain calucation fromTransient Waveform
| Parameter        | Calculation / Formula                 | Result       |
|-----------------|--------------------------------------|-------------|
| Vout (p-p)       | Vout(max) − Vout(min)                | 0.528 V − 0.019 V = 0.509 V |
| Voltage Gain (Av) | Av = Vout / Vin                       | 0.509 / 0.019 = 27.78 V/V |
| Gain (dB)         | 20 log₁₀(Av)                          | 20 log₁₀(27.78) = 28.87 dB |

# AC Analysis
A small-amplitude alternating signal is applied to the amplifier to study its behavior over a range of frequencies. This analysis helps determine the frequency response, including how the gain varies with frequency, and allows calculation of the midband gain, where the amplifier operates most linearly.
# Simulation Parameters
| Parameter         | Value        |
|------------------|-------------|
| Command Type      | AC          |
| AC Magnitude      | 1 V         |
| Sweep Type        | .ac dec     |
| Points per Decade  | 1000        |
| Start Frequency   | 0.1 Hz      |
| Stop Frequency    | 1 GHz       |

https://github.com/lecsinchanamn/CS-Amplifier-/blob/daa57e26c4d617ea7b03a6dbb0583781100fb845/C1%20AC%20analysis.jpeg
# Frequency Response Result
| Parameter       | Value         |
|----------------|---------------|
| Midband Gain    | 28.71 dB      |
| −3 dB Gain      | 25.71 dB      |
| Bandwidth       | 52.1 MHz      |

# Theoretical Gain

| Parameter / Term                   | Value / Calculation                                   |
|-----------------------------------|------------------------------------------------------|
| Transconductance (gm₁)             | 1.6 mS                                              |
| NMOS Output Resistance (ro₁)       | 58.8 kΩ                                             |
| PMOS Output Resistance (ro₂)       | 58.8 kΩ                                             |
| Source Resistor (RS)                | 1 kΩ                                                |
| Gain Denominator Term               | 1 + gm₁ RS + RS/ro₁ → 1 + (1.6e-3 × 1e3) + (1e3 / 58.8e3) ≈ 2.617 |
| Parallel Output Resistance Term    | [gm₁ RS ro₁ + RS + ro₁] ∥ ro₂ ≈ 42.6 kΩ            |
| Voltage Gain (Av, V/V)             | Av = -gm₁ / Denominator × Parallel Term → (1.6e-3 / 2.617) × 42.6 kΩ ≈ 26 V/V |
| Voltage Gain (Av, dB)              | 20 log₁₀(26) ≈ 28 dB                                |
| Technology Note                     | TSMC 180 nm: λ ≈ 0.1–0.2 V⁻¹ → output resistance matches LTspice OP |

1. Voltage Gain of Source-Degenerated CS Amplifier with Active Load
Av = - gm / (1 + gm * RS + RS/ro1) * ( (gm * RS * ro1 + RS + ro1) || ro2 )
2.Using TSMC 180 nm parameters:
gm  = 1.6e-3   # Transconductance in S (mS)
RS  = 1e3      # Source resistor in ohms
ro1 = 58.8e3   # NMOS output resistance in ohms
ro2 = 58.8e3   # PMOS load output resistance in ohms
3.Clculated Voltage Gain:
4. Av = - gm / (1 + gm * RS + RS/ro1) * ( (gm * RS * ro1 + RS + ro1) || ro2 )
Av_VperV = 26      # Voltage gain in V/V
Av_dB    = 20 * log10(Av_VperV)  # Voltage gain in dB
5.Av_dB ≈ 28 dB
6. Design Highlights:
7. High gain amplifier
8. Good linearity due to source degeneration
9. Proper output swing ensured
# Observation
The AC analysis shows a midband gain of 28.71 dB, closely matching the theoretical and transient gain values; the small difference occurs because theoretical calculations assume ideal device behavior, while LTspice includes practical effects such as channel-length modulation.

# CIRCUIT 02
# AIM
Design and implement the Casecode amplifer in LTspices usong 180nm technolgy
# Circuit diogram
https://github.com/lecsinchanamn/CS-Amplifier-/blob/9c8eacf18bddd1d2dae304446485eedf6b3dd824/C2%20circuit%20diogram.jpeg
# DC Analysis
# Design paramater
+----------------+-------+
| Parameter      | Value |
+----------------+-------+
| DDIDVTHn       | VTHp  |
| Voltage        | 1.8 V |
| Current        | 200 µA|
| Voltage Value1 | 0.36 V|
| Voltage Value2 | -0.39 V|
+----------------+-------+

# Voltage limits for proper operation / Overdrive voltage determination / Allowable Range
+----------------------+-------------------------+----------------------+-----------+----------------------+
| Parameter            | Condition / Equation    | Calculation          | Range     | Reason               |
+----------------------+-------------------------+----------------------+-----------+----------------------+
| VGS (NMOS)           | VGS ≥ VTH               | VTH = 0.36 V         | ≤ 1.8 V   | Channel formation    |
| VDS (NMOS)           | VDS ≥ VOV               | VOV = 0.25 V         | ≤ 1.8 V   | Saturation condition |
| VSG (PMOS)           | VSG ≥ |VTHp|            | VTHp = 0.39 V        | ≤ 1.8 V   | Channel formation    |
| VSD (PMOS)           | VSD ≥ VOV               | VOV = 0.25 V         | ≤ 1.8 V   | Saturation condition |
| VGS Calculation      | VGS = VTH + VOV         | 0.36 + 0.25          | 0.61 V    | Overdrive relation   |
| VOV Verification     | VOV = VGS − VTH         | 0.61 − 0.36          | 0.25 V    | Overdrive check      |
| Minimum VOV          | VOV > 0                 | Condition            | Valid     | Proper operation     |
| Maximum VOV          | VOV < VDS               | Condition            | Valid     | Saturation region    |
+----------------------+-------------------------+----------------------+-----------+----------------------+

1.Since the drain–source voltage is approximately half of the supply voltage, it can be written as:
VDS ≈ VDD / 2 = 0.9 V
2.Therefore, the allowable operating range for the overdrive voltage (VOV) becomes:
0 < VOV < 0.9 V
3.The calculated overdrive voltage is:
VOV = 0.25 V
This value clearly lies within the allowable range, which confirms that the chosen operating point satisfies the required condition for proper transistor operation.
# Justification:
A moderate value of overdrive voltage is preferred in MOSFET design because it offers several advantages:
1. It provides sufficient transconductance (gm), which improves the amplification capability of the transistor.
2. It helps maintain a stable drain current, making the circuit operation more reliable.
3. It leaves adequate voltage headroom for signal swing, allowing the output signal to vary without pushing the transistor out of the desired operating region.
# Intermediate node voltage / Output voltage selection / Saturation Verification/ Desihn Justification

+---------------------------+---------------------------+------------------------+-----------+--------------------------------------+
| Section                   | Parameter / Device        | Equation / Condition   | Value     | Explanation / Result                 |
+---------------------------+---------------------------+------------------------+-----------+--------------------------------------+
| Intermediate Node Voltage | VS1 Condition             | VS1 ≥ VOV              | ≥ 0.25 V  | Keeps lower NMOS (M2) in saturation  |
|                           | Selected VS1              | Design choice          | 0.3 V     | Satisfies saturation requirement     |
|                           | VDS2                      | VDS2 = VD2 − VS2       | VS1       | Since VS2 = 0                        |
|                           | Required VDS2             | VDS2 ≥ VOV             | ≥ 0.25 V  | Ensures M2 operates in saturation    |
+---------------------------+---------------------------+------------------------+-----------+--------------------------------------+
| Output Voltage Selection  | Drain-Source Voltage      | VDS ≈ VDD / 2          | 0.9 V     | Allows maximum signal swing          |
|                           | Output Voltage (Vout)     | Vout = VDS + VS1       | 1.2 V     | 0.9 + 0.3                            |
+---------------------------+---------------------------+------------------------+-----------+--------------------------------------+
| Saturation Verification   | M2 (NMOS)                 | VDS2 ≥ VOV             | 0.3 ≥0.25 | ✔ Saturation condition satisfied     |
|                           | M1 (NMOS)                 | VDS1 ≥ VOV             | 0.9 ≥0.25 | ✔ Saturation condition satisfied     |
|                           | M3 (PMOS)                 | VSD ≥ VOV              | 0.6 ≥0.25 | ✔ Saturation condition satisfied     |
+---------------------------+---------------------------+------------------------+-----------+--------------------------------------+
| Design Justification      | VS1 > VOV                 | Bias condition         | Valid     | Keeps lower NMOS in saturation       |
|                           | VS1 << VDD                | Headroom condition     | Valid     | Preserves voltage headroom           |
|                           | Stable bias               | Cascode requirement    | Valid     | Ensures proper cascode operation     |
+---------------------------+---------------------------+------------------------+-----------+--------------------------------------+
# Theory Justification for the Cascode Amplifier Bias Conditions
The table summarizes the biasing and operating conditions required to ensure that all MOSFETs in the cascode amplifier operate in the saturation region. Proper biasing is essential for achieving high gain, good linearity, and maximum signal swing.
1. Intermediate Node Voltage (VS1)
In a cascode amplifier, the drain of the lower NMOS transistor (M2) is directly connected to the source of the upper NMOS transistor (M1). This node is represented by VS1. For the lower transistor M2 to remain in saturation, the drain–source voltage must satisfy the condition:
VDS2 ≥ VOV
Since the source of M2 is grounded (VS2 = 0), the drain–source voltage becomes:
VDS2 = VD2 − VS2 = VS1 − 0 = VS1
Therefore, the condition for saturation becomes:
VS1 ≥ VOV
Given that the overdrive voltage VOV is 0.25 V, the intermediate node voltage must be at least 0.25 V. Choosing VS1 ≈ 0.3 V ensures that the saturation condition is satisfied while still maintaining sufficient voltage headroom for the rest of the circuit.
2. Output Voltage Selection
To achieve maximum symmetrical signal swing in analog amplifier design, the drain–source voltage is typically chosen to be approximately half of the supply voltage:
DS ≈ VDD / 2
With a supply voltage of VDD = 1.8 V, the drain–source voltage becomes:
VDS = 1.8 / 2 = 0.9 V
The output node voltage is the sum of the intermediate node voltage and the drain–source voltage:
Vout = VDS + VS1
Substituting the values:
Vout = 0.9 + 0.3 = 1.2 V
This operating point allows the output signal to swing both upward and downward without driving the transistors out of the saturation region.
3. Saturation Verification
For proper amplifier operation, all transistors must remain in the saturation region.
• For M2 (lower NMOS):
VDS2 = 0.3 V and VOV = 0.25 V  
Since 0.3 ≥ 0.25, M2 operates in saturation.
• For M1 (upper NMOS):
VDS1 = 0.9 V and VOV = 0.25 V  
Since 0.9 ≥ 0.25, M1 also operates in saturation.
• For M3 (PMOS load transistor):
The saturation condition is:
VSD ≥ VOV
With VSD = 0.6 V and VOV = 0.25 V, the condition is satisfied, ensuring that the PMOS device also operates in saturation.
4. Design Justification
The selected bias conditions provide several advantages for the cascode amplifier:
• VS1 > VOV ensures that the lower NMOS transistor remains in saturation, which is necessary for proper amplification.
• VS1 << VDD preserves sufficient voltage headroom for the upper transistor and the output signal swing.
• Stable biasing ensures correct cascode operation, which improves gain, increases output resistance, and enhances overall amplifier performance.
# DC Operating Point






