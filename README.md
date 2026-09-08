# 252330 BJT Amplifier Lab

A LTSpice + Python lab notebook for course 252330: characterizing a bipolar
junction transistor, building its three classic single-stage amplifier
configurations, and comparing inter-stage coupling methods.

Every experiment follows the same pipeline: design and simulate the circuit
in LTSpice, parse the raw waveform data in Python (`ltspice` +
`numpy`), then compute and plot the results with `matplotlib`.

## Contents

- [Lab 1 · BJT Characterization](#lab-1--bjt-characterization)
- [Lab 1 · Single-Stage Amplifiers](#lab-1--single-stage-amplifiers)
  - [Common Emitter (CE)](#common-emitter-ce)
  - [Common Collector (CC)](#common-collector-cc)
  - [Common Base (CB)](#common-base-cb)
- [Lab 2 · Coupling Comparison](#lab-2--coupling-comparison)
- [Repository Layout](#repository-layout)
- [Requirements](#requirements)

## Lab 1 · BJT Characterization

I<sub>C</sub>–V<sub>CE</sub> curves swept across several base currents, used
to extrapolate the transistor's Early voltage from the slope of the
active-region load lines.

```
Early Voltage: -98.65 V
```

![IV char](https://github.com/ssupawat/252330-lab/blob/master/bjt-char-lab/figure/graphout.png?raw=true)

## Lab 1 · Single-Stage Amplifiers

The same transistor built into the three classic single-stage topologies,
each analyzed in the time domain (V<sub>in</sub> vs V<sub>out</sub>) and
frequency domain (gain vs frequency, with the −3 dB bandwidth marked).

### Common Emitter (CE)

| V<sub>in</sub>–V<sub>out</sub> | Frequency response |
| --- | --- |
| ![CE vout-vin](https://github.com/ssupawat/252330-lab/blob/master/bjt-amp-lab/figure/1-1.png?raw=true) | ![CE Freq. Res.](https://github.com/ssupawat/252330-lab/blob/master/bjt-amp-lab/figure/1-1-freq.png?raw=true) |

### Common Collector (CC)

| V<sub>in</sub>–V<sub>out</sub> | Frequency response |
| --- | --- |
| ![CC vout-vin](https://github.com/ssupawat/252330-lab/blob/master/bjt-amp-lab/figure/1-2.png?raw=true) | ![CC Freq. Res.](https://github.com/ssupawat/252330-lab/blob/master/bjt-amp-lab/figure/1-2-freq.png?raw=true) |

### Common Base (CB)

| V<sub>in</sub>–V<sub>out</sub> | Frequency response |
| --- | --- |
| ![CB vout-vin](https://github.com/ssupawat/252330-lab/blob/master/bjt-amp-lab/figure/1-3.png?raw=true) | ![CB Freq. Res.](https://github.com/ssupawat/252330-lab/blob/master/bjt-amp-lab/figure/1-3(2nd)-freq.png?raw=true) |

## Lab 2 · Coupling Comparison

Two amplifier stages chained together, comparing how the choice of
inter-stage coupling shapes the combined frequency response.

| Method | How it works | Trade-off |
| --- | --- | --- |
| Capacitor coupling | AC-couples stages through a series capacitor | Blocks DC, adds a low-frequency roll-off |
| Direct coupling | Stages wired together with no coupling element | Passes DC, but bias points interact between stages |

| Capacitor coupling | Direct coupling |
| --- | --- |
| ![Capa. Coup. Freq. Res.](https://github.com/ssupawat/252330-lab/blob/master/capacitor-coupling-lab/figure/3-1-freq.png?raw=true) | ![Direct Coup. Freq. Res.](https://github.com/ssupawat/252330-lab/blob/master/direct-coupling-lab/figure/3-2-freq.png?raw=true) |

## Repository Layout

Each lab lives in its own folder with the same shape:

```
<lab>/
  ltspice/       schematics (.asc) and raw simulation output (.raw)
  source code/   Python scripts that parse and plot the results
  figure/        generated PNG plots
```

- `bjt-char-lab/` — Lab 1, BJT characterization
- `bjt-amp-lab/` — Lab 1, CE/CC/CB amplifiers
- `capacitor-coupling-lab/` — Lab 2, capacitor coupling
- `direct-coupling-lab/` — Lab 2, direct coupling
- `site/` — static summary page of this project

## Requirements

```
pip install -r requirements.txt
```
