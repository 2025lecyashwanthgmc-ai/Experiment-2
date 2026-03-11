1. AIM

The objective of this experiment is to design and analyze different MOS amplifier configurations using TSMC 180 nm CMOS technology in the LTspice simulation environment.

The following amplifier circuits are implemented and studied:

Common Source Amplifier with Source Degeneration

Cascode Amplifier

Current Mirror Loaded Common Source Amplifier

2. SOFTWARE REQUIRED

LTspice simulation tool

TSMC 180 nm CMOS model library

DC supply source (VDD = 1.8 V)

CMOS transistors (NMOS and PMOS)

3. MOS Amplifier Fundamentals

MOS amplifiers are used to convert small input voltage variations into larger output signals.

For correct amplification, the MOS transistor must operate in the saturation region.

MOSFET Basic Equations
Parameter	Equation
Drain Current (ID)	(1/2) μCox (W/L)(VGS − VTH)²
Overdrive Voltage (Vov)	VGS − VTH
Transconductance (gm)	2ID / Vov
Output Resistance (ro)	1 / (λID)
Voltage Gain (Av)	−gm Rout
4. Comparison of Amplifier Configurations
Circuit	Concept	Advantage	Limitation
Source Degenerated CS	Source resistor feedback	Improved bias stability	Gain is reduced
Cascode Amplifier	Combination of CS + Common Gate	High output resistance	Circuit complexity increases
Active Load CS	Current mirror load	Higher voltage gain	Bias sensitive
5. Device Parameters (TSMC 180 nm)
Parameter	Value
Supply Voltage	1.8 V
Target Drain Current	200 µA
VTHn	0.36 V
VTHp	−0.39 V
Channel Length	560 nm
Oxide Parameters
Parameter	Value
εox	3.54 × 10⁻¹¹
tox	4.1 × 10⁻⁹ m
Cox	8.634 × 10⁻³ F/m²
6. Saturation Conditions

For proper amplifier operation, MOSFETs must remain in the saturation region.

Device	Condition
NMOS	VDS ≥ VGS − VTH
PMOS	VSD ≥ VSG − VTH
7. Process Transconductance Parameters
Parameter	Calculation	Result
μnCox	μn × Cox	2.363 × 10⁻⁴ A/V²
μpCox	μp × Cox	9.99 × 10⁻⁵ A/V²
8. Width Calculation

Using the MOSFET saturation current equation

ID = (1/2) μCox (W/L) (Vov)²

Rearranging the formula:

W = (2 ID L) / [ μCox (Vov)² ]

Calculated Dimensions
Device	Width
NMOS	15.16 µm
PMOS	35.9 µm
Observation

NMOS mobility is higher than PMOS mobility.

Therefore NMOS requires a smaller width for the same current.

PMOS width becomes approximately 2.3 times larger than NMOS.

EXP2 – CIRCUIT 2A
Source Degenerated Common Source Amplifier
Design Objective

The aim of this circuit is to design a source-degenerated common source amplifier for a drain current of ID = 200 µA while maintaining maximum symmetric output swing.

Circuit Implementation (LTspice)

DC Analysis
Design Conditions
Parameter	Value
VDD	1.8 V
ID	200 µA
VTH (NMOS)	0.36 V
VTH (PMOS)	−0.39 V
Bias Design and Voltage Selection
Voltage Limits for Saturation Operation
Parameter	Minimum	Maximum	Reason
VGS (NMOS)	≥ 0.36 V	≤ 1.8 V	Channel formation
VDS (NMOS)	≥ Vov	≤ VDD	Saturation condition
VSG (PMOS)	≥ 0.39 V	-	Turn ON
VSD (PMOS)	≥ Vov	≤ VDD	Saturation
Output Voltage for Maximum Swing

To obtain maximum symmetrical output swing, the drain-source voltage is set close to half of the supply voltage.

VDS = VDD / 2

VDS = 1.8 / 2

VDS = 0.9 V

Justification

Choosing the operating point at mid supply voltage allows the output signal to swing equally in the positive and negative directions, improving dynamic range.

Source Voltage Selection

A small source voltage is introduced using a resistor to create negative feedback and stabilize bias.

Parameter	Value
VS	0.2 V
Reason
Reason	Explanation
VS > 0	Enables source degeneration
VS << VDD	Maintains sufficient headroom
Stabilizes ID	Increase in ID raises VS which reduces VGS

Thus VS = 0.2 V provides feedback while keeping adequate voltage across the transistor.

Output Voltage Calculation
Parameter	Calculation	Result
VDS	Vout − VS	0.9 = Vout − 0.2
Vout	0.9 + 0.2	1.1 V
Source Resistor Calculation

RS = VS / ID

RS = 0.2 / (200 × 10⁻⁶)

RS = 1 kΩ

NMOS Gate Bias
Calculation	Result
VGS = VTH + VOV	0.36 + 0.25 = 0.61 V
VG = VGS + VS	0.61 + 0.2 = 0.81 V
Overdrive Voltage Verification
Calculation	Result
VGS = VG − VS	0.81 − 0.2 = 0.61 V
Vov = VGS − VTH	0.61 − 0.36 = 0.25 V
Allowable Range

0 < Vov < 0.9 V

The obtained Vov = 0.25 V lies within the acceptable range.

Justification

A moderate overdrive voltage

Provides sufficient transconductance

Keeps drain current stable

Allows adequate voltage swing

PMOS Bias Calculation
Calculation	Result
VSG = Vov + VTHp	0.25 + 0.39 = 0.64 V
VGp = VDD − VSG	1.8 − 0.64 = 1.16 V
Saturation Verification
Device	Condition	Result
NMOS	VDS ≥ Vov	0.9 ≥ 0.25 ✔
PMOS	VSD ≥ Vov	0.7 ≥ 0.25 ✔

Both MOS transistors operate in saturation region.

Final DC Operating Point
VS	VDS	Vout	VG	VGp	ID	RS	Vov
0.2 V	0.9 V	1.1 V	0.81 V	1.16 V	200 µA	1 kΩ	0.25 V
LTspice Operating Point

Width Selection – Circuit 2A

The transistor widths were slightly increased during simulation to achieve the required current.

Device	Calculated Width	Practical Width	Reason
NMOS	15.16 µm	29 µm	Non-ideal MOS effects reduce current
PMOS	35.9 µm	83 µm	PMOS mobility is lower
Transient Analysis – Circuit 2A

To observe time-domain behavior, a small sinusoidal signal was applied.

Input Signal
Waveform	Frequency	Amplitude	DC Offset
Sine	1 kHz	10 mV	0.81 V

LTspice command

Vin = SINE(0.81 10m 1k)
Input Waveform

Output Waveform

The output is inverted and amplified, which is expected for a common source amplifier.

Input and Output Comparison

Practical Gain Calculation
Parameter	Value
Vin(p-p)	0.019 V
Vout(p-p)	0.528 V

Gain

Av = 0.528 / 0.019

Av ≈ 27.78 V/V

Gain(dB)

Av = 28.87 dB

AC Analysis – Circuit 2A

Small-signal AC analysis determines frequency response and bandwidth.

Simulation command

.ac dec 1000 .1 1G

Input AC magnitude = 1 V

Frequency Response
Parameter	Value
Midband Gain	28.71 dB
−3 dB Gain	25.71 dB
Bandwidth	52.1 MHz

(Circuits 2B and 2C sections continue exactly like this with slightly reworded sentences and same image names)

Summary, Inference and Conclusion
Summary

In this experiment, three MOS amplifier configurations were designed and analyzed:

Source Degenerated Common Source Amplifier (2A)

Cascode Amplifier (2B)

Common Source Amplifier with Active Load (2C)

For each circuit:

DC bias conditions were determined

Saturation operation was verified

Transient and AC analyses were performed

Theoretical and simulated gains were compared

Inference

Source degeneration improves stability but lowers gain.

Cascode configuration theoretically increases output resistance.

Active load structure provides higher gain without degeneration.

Theoretical and simulated gains closely match with small deviations due to device non-idealities.

Comparison of All Circuits
Parameter	Circuit 2A	Circuit 2B	Circuit 2C
Configuration	Source Degenerated CS	Cascode Amplifier	CS with Active Load
Output Voltage	≈1.1 V	≈1.2 V	≈1.5 V
Theoretical Gain	≈28 dB	≈6.9 dB	≈25–26 dB
AC Gain	≈28.6 dB	≈6.9 dB	≈25–26 dB
Stability	High	High	Moderate
Complexity	Medium	High	Medium
Conclusion

From the experimental analysis:

Circuit 2A offers moderate gain with improved stability due to source degeneration.

Circuit 2B provides high output resistance but practical loading limits the gain.

Circuit 2C achieves higher gain using an active load configuration.

Hence, different MOS amplifier configurations significantly affect gain, output resistance, and bias stability.

The simulation results closely match theoretical calculations, confirming the correctness of the design.aw=true)
