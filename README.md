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















