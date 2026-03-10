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
# 1. Drain Current (Saturation Region)
ID = (1/2) * kn * (VGS - VT)^2
# 2. Transconductance
gm = 2ID / (VGS - VT)
# Voltage Gain (with Source Degeneration)
Av = - (gm * RD) / (1 + gm * RS)
# Input Resistance
Rin ≈ ∞
# Output Resistance
Rout ≈ RD
+----------------------+---------------------------------------+
| Parameter            | Equation                              |
+----------------------+---------------------------------------+
| Drain Current (ID)   | ID = (1/2) * kn * (VGS - VT)^2        |
| Transconductance     | gm = 2ID / (VGS - VT)                 |
| Transconductance     | gm = sqrt(2 * kn * ID)                |
| Voltage Gain (Av)    | Av = -(gm * RD) / (1 + gm * RS)       |
| Input Resistance     | Rin ≈ ∞                               |
| Output Resistance    | Rout ≈ RD                             |
+----------------------+---------------------------------------+


















