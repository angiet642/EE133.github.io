# Lab 3: Building a MOSFET Ring Mixer
Author: Angie Thai\
Lab Partner: Kylee Krzanich

## Abstract: 

In this lab, a double balanced FET ring mixer was built. The choice to create a FET ring mixer was based on its ability to switch more robustly with less leakage current, unlike the diode ring mixer. Although the FET ring mixer appears more ideal in a switching sense, intrinsic and extrinsic capacitances of the MOSFET are introduced. This could potentially create nonidealities, especially at higher frequencies.

## Background:
__Definition of a mixer:__ A device that generates the sum or difference frequencies of two input signals. They can be referred to other names, such as modulators, demodulators, multipliers, synchronous detectors, phase detectors, upconverters or downconverters.

__Real Life Applications of a Mixer__
Mixers allow frequencies to be shifted from one frequency range to another. This is important because if data is transmitted simultaneously within the same frequency range of another signal, there will be interference. To receive both signals, one can shift the frequency range of the first signal to a different band and eliminate the possiblity of the two signals overlapping with one another. The idea of mixing frequencies is crucial for wireless communication, where WIFI data (for example) can only be sent over a 2.4 or 5.4 GHz channel. 

__Key Terms__
- __IF:__ Intermediate Frequency (output or input - in this lab, it is configured as the output)
- __RF:__ Receieved Frequency (input or output - in this lab, it is configured the input)
- __LO:__ Local oscillator (generally larger than RF)
- __Downconversion:__ Shift RF to a lower IF (IF = LO - RF)
- __Upconversion:__ Shift RF to a higher IF (RF1 = LO - IF) & (RF2 = LO + IF) 

<p align="center">
  <img src="https://www.microwavejournal.com/ext/resources/article-images-2019/Microwave-Mixer-Basics/Fig1a.jpg" width="600"> 
  <p align = "center"> 'Figure 1: RF Mixer Overview'</p>
</p>

#### Performance Measures
- __Conversion Loss/Gain:__ Power IF output/Power (RF) input (dB). This measures the efficiency of the mixer.
- __Noise Figure:__ SNR (RF) / SNR(IF)
- __Linearity and Isolation:__ The idea that the IF output is proportional to the RF input to some extent
- __Spurious responses (spurs):__ Unwanted frequencies that appear to be mixed in addition to the main frequencies of interest


<p align="center">
  <img src="https://edadocs.software.keysight.com/download/attachments/7532576/compressioncurve.gif?version=1&modificationDate=1477261038000&api=v2" width="600"> 
  <p align = "center"> 'Figure 2: Performance Boundaries of an RF Mixer'</p>
</p>

#### Types of Mixers
There are several types of mixer circuits. For the purpose of this lab, the focus will be on double balanced mixers, which uses differential circuits at the input to minimize the presence of unwanted RF and LO signals at the output. Double balanced mixers are also widely used because they yield increased linearity and better supression of spurs. Some examples of double balanced mixers are shown below. The following sections will discuss the steps to build a FET ring. 
| Figure 3: Diode Ring  | Figure 4: FET Ring |  Figure 5: Gilbert Cell |
|-------------------|-------------------| -------------------|
| <img src="https://www.electronics-notes.com/images/mixer-double-balanced-circuit-01.svg" width="400"> | <img src="https://www.electronics-notes.com/images/mixer-double-balanced-fet-circuit-01.png" width="500"> |<img src="https://www.researchgate.net/profile/Giovanni-Piccinni/publication/320373836/figure/fig1/AS:590496279838720@1517796692383/Architecture-of-a-conventional-double-balanced-Gilbert-cell-mixer.png" width="600">
<p align = "center"> Table 1: Various Mixer Circuits </p>

## Procedure

To construct a passive FET ring mixer, the following items are needed:
1. (1) Perf board
2. [(1)Broadband Quad MOSFET Array](https://www.psemi.com/pdf/datasheets/pe4141ds.pdf) 
3. [(3) RF transformers (used as baluns)](https://www.minicircuits.com/pdfs/ADT4-1WT+.pdf) 
4. (3) SMA connectors

The datasheet can be referenced to understand how the MOSFET ring chip can be connected to the three different baluns as illustrated below. Once the connections were established, the components were mounted onto a solderable perf board (figure 5). SMA connectors are used as an interface between the mixer and the spectrum analyzer + function generator.

| Figure 6: Schematic  | Figure 7: Assembly |
|-------------------|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/Schematic.JPG" width="600"> | <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-9299.jpg" width="300"> |

<p align = "center"> Table 2: Schematic and Assembly </p>


## Measurements

### Visualizing the Output IF with a Spectrum Analyzer

After assembling the mixer, the function generator is used to generate signals for the RF and LO channels. The IF channel is connected to the spectrum analyzer to visualize the mixed output frequencies. In the table below, the LO channel is set to 3 MHz and the RF channel is set to 10 MHz.   

| Figure 8: LO Frequency  | Figure 9: RF Frequency  |
|-------------------|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-9297.jpg" width="500"> | <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-9296.jpg" width="500"> |
<p align = "center"> Table 3: Function Generater Setup </p>

The expected result is to see two peaks, one at 7 MHz (the difference of the two frequencies) and 13 MHz (the addition of the two frequencies). This particular set-up uses a low-side downconversion since LO is smaller than the RF signal. In figures 3 and 4, the comparison is made between two FET ring mixers. The two figures show the difference and addition of the RF and LO channels as the large peaks. However, figure 3 shows a large peak at 3 MHz. This indicates that there is a large LO leakage due to poor LO and RF isolation unlike the mixer in figure 4, which does not show a large peak at the LO frequency.

The mixer in figure 4 was used as a baseline or example of an "ideal" FET mixer created with the same components by Greig Scott. The difference in performance between the two mixers is likely caused by poor contact at the pins of the MOSFET ring. This component was difficult to solder without shorting the pins, which took several attempts. The presence of other peaks are also known as "spurs" which was defined as the unwanted frequencies that were unintentionally mixed. 

| Figure 10: Mixer Result  | Figure 11: Better Mixer (Courtesy of Greig Scott)  |
|-------------------|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-9291.jpg" width="500"> | <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-9295.jpg" width="500"> |
<p align = "center"> Table 4: Comparisons between two mixers </p>

### Mixer Performance Measurements
A week later, the mixer in figure 3, along with the mixer in figure 4 was no longer functional. After careful debugging with a DMM and microscope, the conclusion was that a component in the assembly was "blown" and could not be recreated due to limited parts. Thus, the following measurements were taken from a third mixer of the same topology, but constructed by Kylee Krzanich.

For this set up, the LO (12 MHz) is greater than the RF (2 MHz) signal. Thus, the system is a high-side down converter.

| Figure 12  | Figure 13  |
|-------------------|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-5065.JPG" width="500"> | <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-5066.JPG" width="500"> |
<p align = "center"> Table 5: Function Generator Set-Up </p>

In the figures below, the peaks appear at 8 MHz and 14 MHz as expected. The purpose of figure 8 was to show the measurement of the maximum IF gain at the 1dB compression point. To find the 1dB compression point, the amplitude of the RF signal was increased by 1dB at a time until the IF amplitude was no longer increased by the same amount. This measurement was around 15 dB for the particular mixer. For typical MOSFET mixers, the 1dB compression point is generally 3db higher than the LO power level.

| Figure 14  | Figure 15 |
|-------------------|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-5064.JPG" width="500"> | <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-5067.JPG" width="500"> |
<p align = "center"> Table 6: Outputs of the RF Mixer </p>


The Conversion Gain/Loss of the RF Mixer = Output IF power [dBm] – RF input power[dBm]. \
For this mixer, the conversion loss was around 9 db. According to [digikey](https://www.digikey.com/en/articles/the-basics-of-mixers#:~:text=The%20purpose%20of%20the%20mixer,at%20the%20other%20two%20ports.), typical values of conversion loss are between 4.5 to 9 dB. This indicates that the conversion loss for FET mixers to be relatively high, which is one of the trade offs for passive FET mixers.

The minimum IF frequency can be measured by setting the RF and LO channel to have a small frequency difference. This is achieved by decreasing the RF frequency until the IF frequency becomes distorted as shown in the figure below. For this mixer, the minimum IF frequency was 30 kHz. This measurement was made on the oscilloscope with an additional low pass filter terminal to help visualize the signal. Typically, caution is taken to avoid mixing to __zero__ IF because this would put the IF at the flicker noise band, which occurs at lower frequencies due to defects in the conductive channels.

| Figure 16  |
|-------------------|
| <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab3/Lab3_Images/IMG-5068.JPG" width="500"> |


## Discussions
__Summary of results__
- 1dB compression point = 15 dB
- Conversion loss = 9 db
- Minimum IF Frequency = 30 kHz

__Takeaways__ \
  __1. Compression Point__
  - It is important to find the 1dB compression point for a mixer because it is the point at which the mixer does not behave linearly and becomes unpredictable. 
  - Operating far from the 1dB compression point will result in lower distortion and levels of spurious output frequencies. 
  - To improve the 1dB compression point, one can analyze the RF signal chain to find the saturated regions and attempt to improve the dynamic range for signal block. 
  - For a diode ring mixer, the compression point can be improved by using higher turn on diodes. This allows for a high RF power to be applied without impacting the diodes, but also requires a larger LO to switch the diodes.

  __2. LO Leakage__
  - LO leakage occurs from poor LO to RF or LO to IF isolation. 
  - To elimate the LO leakage, one can generate a signal that is equal in amplitude but opposite in phase as described in this [article from analog devices](https://www.analog.com/en/analog-dialogue/articles/transmit-lo-leakage-lol-an-issue-of-zero-if-that-isn-t-making-people-laugh-out-loud.html 

  __3. Minimum IF__

For reference, the balun is used to create equal and opposite signals, which is illustrated below.
<p align="center">
  <img src="https://www.electronicspecifier.com/cms/images/Using%20a%20wideband%20balun%20with%20ADCs.jpg" width="400"> 
  <p align = "center"> 'Figure 17: Usage of Balun'</p>
</p>

  - Going to DC is important to understand because it may be desired for different applications
    - The diode ring mixer should "go to DC"
      - Looking at the double balanced diode ring mixer, we see that the output IF is connected to the center tap of the transformer, which is directly connected to the diode ring. Thus, DC current is able to pass through the diodes
    - The FET ring mixer should not "go to DC" 
      - Looking at the double balanced FET ring mixer, the IF channel is connected to the primary windings of the balun, which blocks DC current. Thus, the FET ring cannot go to DC.       
      - Hence, this explains why the FET ring mixer had a minimum IF of 30kHz 
      - If one desires to have a FET ring go to DC, the balun can be replaced with a differential op amp or configuration that is differential and allows DC current to pass.
    - The Gilbert Cell Mixer should be able to go to DC, as long as the differential output isnt coupled by a large capacitance. 
  - Applications that require 0 Hz
    - Digital communication
    - CW Radars
    - Sofware defined radios
    - Phase detectors
 - Advantages of a zero-IF design
    - Eliminates the need for IF related circuitry (such as filtering)
    - Can ease the demodulations of very wideband RF signals
 - Cautions with zero-IF design
    - Relies heavily on LO and mixer performance
    - If there are any imperfections, the overall system performance will suffer greatly
    - Challenging to achieve sufficient dynamic range
## Conclusion
At the end of this lab, key performance indicators of the FET ring mixer were documented and analyzed. Nonidealities were also observed, which resulted in discussions related to avoiding or improving such outcomes.
