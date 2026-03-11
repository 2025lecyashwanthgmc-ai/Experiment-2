# Experiment-2
Experiment 2
  
#Aim : Design the amplifigurations using tsmc 180nm tech

## Introduction

Analog amplifiers are fundamental building blocks in modern integrated circuits and are widely used in communication systems, signal processing, and electronic instrumentation. With the continuous scaling of semiconductor technology, CMOS processes such as **TSMC 180 nm technology** have become widely used for designing low-power and high-performance analog circuits.  

This project focuses on the **design and analysis of amplifier configurations using TSMC 180 nm CMOS technology**. The aim is to understand the behavior and performance of MOSFET-based amplifiers implemented with realistic technology models.

In this project, different **amplifier configurations** such as:

- Common Source (CS) Amplifier  
- Common Drain (CD) Amplifier  
- Common Gate (CG) Amplifier  

are designed using **NMOS and PMOS transistors**.

The circuits are simulated using **SPICE-based simulation tools** with the **TSMC 180 nm model library**. Various analyses are performed to evaluate the circuit performance, including:

- **DC Analysis** – To determine the biasing point of the amplifier.
- **AC Analysis** – To study the frequency response and voltage gain.
- **Transient Analysis** – To observe the time-domain response of the amplifier.


## Design Specifications

The amplifier is designed using **TSMC 180 nm CMOS technology** with the objective of achieving stable operation and sufficient voltage gain for analog signal amplification. The following design specifications are considered during the circuit implementation and simulation.

| Parameter | Specification |
|-----------|--------------|
| Technology | TSMC 180 nm CMOS |
| Supply Voltage (VDD) | 1.2 V  |
| Transistor Type | M1:NMOS, M2:PMOS |
| Channel Length (L) | 180 nm |
|Maximum power supply | 0.4mW |
Load Capacitance | 0.5 pF |
| Channel Length |  180 nm |
| Threshold Voltage | $\approx 0.366$ V |
