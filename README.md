# Yagi Antenna Design

Designed, simulated, constructed, and tested a 3-element Yagi antenna
tuned for the FM broadcast band, targeting 98.3 MHz. Built as part of
a 4-person team (ESET 355, Group 14) — my primary contributions were
NEC modeling and VNA measurement and tuning

## What it does
- Directional 3-element Yagi (reflector, driven dipole, director)
  providing gain and front-to-back directivity over a simple dipole
- Theoretical element lengths calculated in EZNEC, then tuned
  empirically against real-world VSWR measurements
- Uses a coaxial balun (8-turn choke) to prevent common-mode currents
  on the feedline from distorting the radiation pattern
- Direct-fed for simplicity (no matching network/gamma match)

## Tools
- EZNEC / 4nec2 (NEC-based antenna simulation and optimization)
- NanoVNA (impedance, VSWR, and resonance measurement)
- SDRuno + RSP SDR receiver (azimuthal radiation pattern measurement)
- Smith chart analysis

## Design summary
- Target frequency: 98.3 MHz (FM broadcast)
- Elements: reflector, driven dipole, director
- Boom: half-inch PVC pipe and connectors, steel hose clamps
- Elements: 1-inch steel tape measure stock
- Feed: direct feed (no matching network)

| Element   | Theoretical length (EZNEC) | Final built length |
|-----------|----------------------------|---------------------|
| Reflector | 61.27 in                   | 60.75 in            |
| Dipole    | 58.55 in                   | 56.75 in            |
| Director  | 54.46 in                   | 52.50 in            |

Elements were shortened from theoretical values to compensate for the
velocity factor of the tape-measure stock and proximity to the PVC
mounting structure.

## Results
- Measured VSWR at 98.3 MHz: **1.679**
- Measured input impedance: **31.75 Ω + j19.8 nH**
- Front-to-back ratio: **3.3 dB** (main lobe measured at 150°,
  opposite null at 330° — see azimuthal pattern below)
- Effective resonant frequency of the final build: **~101.3 MHz**
  (vs. 98.3 MHz target)

### Azimuthal pattern (measured via SDRuno, 30° increments)
| Angle | Signal (dBm) |
|-------|--------------|
| 0/360 | -39.8 | 24.2 |
| 30    | -49.9 | 21.3 |
| 60    | -47.2 | 27.4 |
| 90    | -42.5 | 29.1 |
| 120   | -38.1 | 29.3 |
| 150   | -36.5 | 30.6 |
| 180   | -42.0 | 26.0 |
| 210   | -47.2 | 25.8 |
| 240   | -46.0 | 28.8 |
| 270   | -44.2 | 27.0 |
| 300   | -44.5 | 27.0 |
| 330   | -39.8 | 26.1 |

## Files
- `*.nec` / `*.out` — NEC model file for element lengths/spacing
- `smith_chart.png` — measured Smith chart at 98.3 MHz
- `vswr_plot.png` — measured VSWR sweep
- `azimuthal_pattern.png` — polar plot of normalized gain vs. angle
- `yagi_construction.jpg` — photo of the physical build

## Discrepancies & lessons learned
The final build resonated closer to 101.3 MHz than the 98.3 MHz
target. Contributing factors identified: a slight curve in the boom
(which lowered VSWR around the effective frequency), cold/dry test
conditions, and imperfect trim ratios between the three elements
relative to the theoretical model. The measured front-to-back ratio
(3.3 dB) was also lower than an idealized 3-element Yagi would
predict, and the main lobe was offset toward 150° rather than 0°,
likely due to the position of the transmitter relative to the test
setup rather than an antenna defect.

This was a useful exercise in the gap between simulated and physical
RF performance — small mechanical/environmental factors have an
outsized effect on tuned antenna behavior.
