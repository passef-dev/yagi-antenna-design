# Yagi Antenna Design

Designed, simulated, constructed, and tested a Yagi antenna operating
in the FM broadcast band (88-108 MHz), optimized in NEC before
physical construction.

## What it does
- Directional Yagi design providing gain and azimuthal directivity
  over a simple dipole
- Optimized element lengths and spacing in NEC (4nec2) based on
  target frequency and physical constraints
- Includes a custom matching network designed to achieve VSWR < 1.5
- Physically constructed on a PVC boom and mast-mounted for field testing

## Tools
- 4nec2 (NEC-based antenna simulation and optimization)
- NanoVNA (impedance, VSWR, and resonance measurement)
- Smith chart analysis for matching network design

## Design summary
- Frequency: 98.3 MHz
- Number of elements: 3 (1 driven, 1 director, 1 reflector)
- Target VSWR: < 1.5

## Results
- Measured input impedance: 31.75  + 19.8 nH
- Measured VSWR at resonance: 1.679
- Resonant frequency: 101.3 MHz

## Files
- Example1.nec — NEC model file(s) used for simulation/optimization
- smith_chart.png — matching network Smith chart analysis
- vswr_plot.png — NanoVNA screenshot(s) of measured results
- pattern.png — azimuthal pattern screenshot

## What I learned
Hands-on experience translating an antenna design from simulation
(NEC optimization) into a working physical build, including impedance
matching and using a VNA to validate real-world performance against
predicted results — and troubleshooting the gap between simulated
and measured performance.
