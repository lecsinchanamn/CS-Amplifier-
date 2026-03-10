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







