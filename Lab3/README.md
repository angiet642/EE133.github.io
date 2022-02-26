# Lab 3: Building a MOSFET Ring Mixer
Author: Angie Thai\
Lab Partner: Kylee Krzanich

## Abstract: 

In this lab, a double balanced FET ring mixer was built. The choice to create a FET ring mixer was based on its ability to switch more robustly with less leakage current, unlike the diode ring mixer. Although the FET ring mixer appears more ideal in a switching sense, intrinsic and extrinsic capacitances of the MOSFET are introduced. This could potentially create nonidealities, especially at higher frequencies.

## Background:
Types of Mixers
| Diode Ring  | FET Ring |  Gilbert Cell |
|-------------------|-------------------| -------------------|
| <img src="https://www.electronics-notes.com/images/mixer-double-balanced-circuit-01.svg" width="400"> | <img src="https://www.electronics-notes.com/images/mixer-double-balanced-fet-circuit-01.png" width="500"> |<img src="https://www.researchgate.net/profile/Giovanni-Piccinni/publication/320373836/figure/fig1/AS:590496279838720@1517796692383/Architecture-of-a-conventional-double-balanced-Gilbert-cell-mixer.png" width="600">

#### Acronyms 
- __Definition of a mixer:__ A device that generates the sum or difference frequencies of two input signals. They can be referred to other names, such as modulators, demodulators, multipliers, synchronous detectors, phase detectors, upconverters or downcoonverters.
- __IF:__ Intermediate Frequency
- __RF:__ Receieved Frequency
- __LO:__ Local oscillator
- __Downconversion:__ 
- __Upconversion:__

#### Performance Measures
- __Conversion Gain:__ Power of desired IF output/RF power input (dB)
- __Noise Figure:__
- __Linearity and Isolation:__
- __Spurious responses (spurs):__

## Procedure

__Materials Needed__
1. (1) Perf board
2. [(1)Broadband Quad MOSFET Array](https://www.psemi.com/pdf/datasheets/pe4141ds.pdf) 
3. [(3) RF transformers](https://www.minicircuits.com/pdfs/ADT4-1WT+.pdf) 
4. (3) SMA connectors

| Figure #1  | Figure #2  |
|-------------------|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/Schematic.JPG" width="600"> | <img src="https://www.electronics-notes.com/images/mixer-double-balanced-fet-circuit-01.png" width="300"> |



__Measurements__
- 1 dB compression point
- LO leakage (and how do you know that peak is the LO leakage?)
- conversion gain (loss) vs LO drive level (like the graph we saw on the slides today)
- picture of spur levels
- minimum IF frequency

  
  
<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-9299.jpg" width="300"> 
  <p align = "center"> 'Figure 1'</p>
</p>

## Discussion

### Mixing Results

| Figure #1  | Figure #2  |
|-------------------|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-9297.jpg" width="500"> | <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-9296.jpg" width="500"> |

| Figure #3  | Figure #4  |
|-------------------|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-9291.jpg" width="500"> | <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-9295.jpg" width="500"> |
<p align = "center"> 'Figure 1'</p>

### Mixer Performance Measurements

| Figure #5  | Figure #6  |
|-------------------|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-5065.JPG" width="500"> | <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-5066.JPG" width="500"> |

| Figure #7  | Figure #8  |
|-------------------|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-5064.JPG" width="500"> | <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-5067.JPG" width="500"> |


| Figure #9  |
|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-5068.JPG" width="500"> |


## Discussions


## Conclusion
