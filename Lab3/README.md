# Lab 3: Building a MOSFET Ring Mixer
Author: Angie Thai\
Lab Partner: Kylee Krzanich

## Abstract: 

In this lab, a double balanced FET ring mixer was built. The choice to create a FET ring mixer was based on its ability to switch more robustly with less leakage current, unlike the diode ring mixer. Although the FET ring mixer appears more ideal in a switching sense, intrinsic and extrinsic capacitances of the MOSFET are introduced. This could potentially create nonidealities, especially at higher frequencies.

## Background:
__Definition of a mixer:__ A device that generates the sum or difference frequencies of two input signals. They can be referred to other names, such as modulators, demodulators, multipliers, synchronous detectors, phase detectors, upconverters or downconverters.

__Real Life Applications of a Mixer__
Mixers allow frequencies to be shifted from one frequency range to another. This is important because if data is transmitted simultaneously within the same frequency range of another signal, there will be interference. To receive both signals, we can shift the frequency range of the first signal to a different band and eliminate the possiblity of the two signals overlapping with one another. The idea of mixing frequencies is crucial for wireless communication, where WIFI data (for example) can only be sent over a 2.4 or 5.4 GHz channel. 

__Some Definitions__
- __IF:__ Intermediate Frequency (output)
- __RF:__ Receieved Frequency (input)
- __LO:__ Local oscillator (generally larger than RF)
- __Downconversion:__ Shift RF to a lower IF (IF = LO - RF)
- __Upconversion:__ Shift RF to a higher IF (RF1 = LO - IF) & (RF2 = LO + IF) 

#### Performance Measures
- __Conversion Loss/Gain:__ Power IF output/Power (RF) input (dB)
- __Noise Figure:__ SNR (RF) / SNR(IF)
- __Linearity and Isolation:__ The idea that the IF output is proportional to the RF input to some extent
- __Spurious responses (spurs):__ Unwanted frequencies that appear to be mixed in addition to the main frequencies of interest

#### Types of Mixers
There are several types of mixer circuits. For the purpose of this lab, the focus will be on double balanced mixers, which uses differential circuits at the input to minimize the presence of unwanted RF and LO signals at the output. Double balanced mixers are also widely used because they yield increased linearity and better supression of spurs. Some examples of double balanced mixers are shown below. This report will discuss the steps to a FET ring in the following sections. 
| Diode Ring  | FET Ring |  Gilbert Cell |
|-------------------|-------------------| -------------------|
| <img src="https://www.electronics-notes.com/images/mixer-double-balanced-circuit-01.svg" width="400"> | <img src="https://www.electronics-notes.com/images/mixer-double-balanced-fet-circuit-01.png" width="500"> |<img src="https://www.researchgate.net/profile/Giovanni-Piccinni/publication/320373836/figure/fig1/AS:590496279838720@1517796692383/Architecture-of-a-conventional-double-balanced-Gilbert-cell-mixer.png" width="600">
<p align = "center"> Table 1: Various Mixer Circuits </p>


## Procedure

To construct a passive FET ring mixer, the following items are needed:
1. (1) Perf board
2. [(1)Broadband Quad MOSFET Array](https://www.psemi.com/pdf/datasheets/pe4141ds.pdf) 
3. [(3) RF transformers (used as baluns)](https://www.minicircuits.com/pdfs/ADT4-1WT+.pdf) 
4. (3) SMA connectors

The datasheet can be referenced to understand how the MOSFET ring chip can be connected to the three different baluns as illustrated below. Once the connections were established, the components were mounted onto a solderable perf board. SMA connectors are used as an interface between the mixer and the spectrum analyzer + function generator.

| Schematic  | Assembly |
|-------------------|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/Schematic.JPG" width="600"> | <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-9299.jpg" width="300"> |

<p align = "center"> Table 2: Schematic and Assembly </p>


## Measurements

### Mixer Results

After assembling the mixer, the function generated is used to generate waveforms on the RF and LO channels. The IF channel is connected to the spectrum analyzer to visualize the mixed frequencies.  In the table below, the LO channel is set to 3 MHz and the RF channel is set to 10 MHz.   

| Figure #1: LO Frequency  | Figure #2: RF Frequency  |
|-------------------|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-9297.jpg" width="500"> | <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-9296.jpg" width="500"> |
<p align = "center"> Table 3: Function Generater Setup </p>

The expected result is to see two peaks, one at 7 MHz (the difference of the two frequencies) and 13 MHz (the addition of the two frequencies). This particular set-up uses a low-side downconversion since LO is smaller than the RF signal. In figures 3 and 4, the comparison is made between two FET ring mixers. The two figures show the difference and addition of the RF and LO channels. However, figure 3 shows a large peak at 3 MHz. This indicates that there is a large LO leakage due to poor LO and RF isolation unlike the mixer in figure 4, which does not show a large peak at the LO frequency. The mixer in figure 4 was used as a baseline or example of an "ideal" FET mixer created with the same components by Greig Scott. The difference in performance between the two mixers is likely caused by poor contact at the pins of the MOSFET ring. This component was difficult to solder without shorting the pins, which took several attempts. 

| Figure #3: Mixer Result  | Figure #4: Better Mixer (Courtesy of Greig Scott)  |
|-------------------|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-9291.jpg" width="500"> | <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-9295.jpg" width="500"> |
<p align = "center"> Table 4: Comparisons between two mixers </p>

### Mixer Performance Measurements
A week later, the mixer in figure 3, along with the mixer in figure 4 was no longer functional. After careful debugging with a DMM and microscope, the conclusion was that a component in the assembly was "blown" and could not be recreated due to limited parts. Thus, the following measurements were taken from a third mixer of the same topology, but constructed by Kylee Krzanich.

__Measurements__
- conversion gain (loss) vs LO drive level (like the graph we saw on the slides today)
- picture of spur levels

For this set up, the LO (12 MHz) is greater than the RF (2 MHz) signal. Thus, the system is a high-side down converter.

| Figure #5  | Figure #6  |
|-------------------|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-5065.JPG" width="500"> | <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-5066.JPG" width="500"> |
<p align = "center"> Table 5: Function Generator Set-Up </p>

In the figures below, the peaks appear at 8 MHz and 14 MHz as expected. The purpose of figure 8 was to show the measurement of the maximum IF gain at the 1dB compression point. To find the 1dB compression point, the amplitude of the RF signal was increased by 1dB at a time until the IF amplitude was no longer increased by the same amount. This measurement was around 15 dB for the particular mixer. For typical MOSFET mixers, the 1dB compression point is generally 3db higher than the LO power level.

| Figure #7  | Figure #8  |
|-------------------|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-5064.JPG" width="500"> | <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-5067.JPG" width="500"> |


The Conversion Gain/Loss of the RF Mixer = Output IF power [dBm] – RF input power[dBm]. \
For this mixer, the conversion loss was around 9 db.

The minimum IF frequency can be measured by setting the RF and LO channel to have a small frequency difference. Then, the RF frequency is decreased until the IF frequency becomes distorted as shown below. 


| Figure #9  |
|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-5068.JPG" width="500"> |


## Discussions
We talked about the 1dB compression point. Why is this an important performance metric? Can we change it? If so, how might we do that?
There was some discussion about LO leakage. Why is that important and what can be done about that?
Did you use your mixer as an up converter? As a down converter? If you didn't try both of these, why not?
Did you measure the conversion gain vs LO drive level. I guess you must have if you determined the 1dB compression point. How did you make those measurements? Was this at a single frequency? If so was there anything special about the frequency you chose? If you did the measurements at different frequencies, did you find about the same result?
There were a number of questions about why one would be concerned about the minimum IF frequency. Greig pointed out that the diode ring mixer should "go to DC" but that the FET ring wouldn't. Why might that be something one would be concerned about? What about the Gilbert cell mixer; should that "go to DC"? Does all this have anything to do with zero IF SDR's or radar stuff?
In the mixer you built, why wouldn't the mixer go to zero IF? What could be done if you want it to go to zero IF?

## Conclusion
