# Lab 1: Using VNAs to Measure Parasitic Properties of Passive Componenets 

## Authors:
Author: Angie Thai\
Lab Partner: Kylee Krzanich

## Abstract: 
Passive components are devices that do not generate energy or require power to operate, such as resistors, capacitors, and inductors. To analyze such devices, a vector network analyzer can be used to visualize and measure the properties of each component.  

## Introduction:
In this lab, the performance of passive components are measured within a specified frequency band. These measurements were achieved using a vector network analyzer, a device that measures signals that pass through the device under test (DUT) and also the signals reflected back from the DUT. Thoughout the report, the transmitted signal will be referred to as the "S21" parameter, and the reflected signal will be referred to as the "S11" parameter. Measurements from the VNA include impedance measurements on a smith chart in addition to the magnitude of S21 and S11 signals. All measurements are swept through a predefined frequency range to show the continuous changes of a device as a function of frequency. 

## Procedure
### Setting up the VNA
Prior to measuring the parasitic effects of a capacitor and inductor, we first familiarized ourselves with the NanoVNA. Calibrating the NanoVNA was done using the RF demo kit board (pictured below). Blocks 13-16 on the board describe the SOLT calibration process, which stands for "short", "open", "load" and "through". This calibration must be done to account for the effects of the cables connected between the VNA and DUT. Each time the frequency sweep is adjusted, re-calibration is required. The NanoVNA-QT software was used to view measurements from the VNA through a USB connection to a laptop

<p align="center">
<img src="https://m.media-amazon.com/images/I/81smXiQSngL._SL1500_.jpg" width="400">
<img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/RF_DemoKIt.jpg" width="400">
</p>

### Measuring the RF Demo Kit Board
After calibrating the NanoVNA, we measured blocks 1-12 on the RF demo kit to verify the readings of various circuits as illustrated on the board. Overall, we found that our measurements were aligned with the illustrations on the board.
<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture1.png" width="500"> 
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture2.png" width="500"> 
  <p align = "center"> 'Figure 1 & 2: Low Pass and High Pass Filter'</p>
</p>

<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture3.png" width="500"> 
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture4.png" width="500"> 
  <p align = "center"> 'Figure 3 & 4: Band Pass and Band Stop Filter'
</p>
<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture5.png" width="500">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture6.png" width="500"> 
  <p align = "center"> 'Figure 5 & 6: 33 and 75 ohms'
</p>

<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture7.png" width="500"> 
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture8.png" width="500"> 
  <p align = "center"> 'Figure 7 & 8: Capacitor & Inductor'
</p>

<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture9.png" width="500"> 
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture10.png" width="500"> 
  </p><p align = "center"> 'Figure 9 & 10: RC & LC Circuit'
</p>
<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture11.png" width="500">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture12.png" width="500"> 
  </p><p align = "center"> 'Figure 11 & 12: (Capacitor + R || L) & LRC Circuit'
</p>

### Measuring Capacitors and Inductors through SMA Connectors
In this section of the lab, we soldered a 200 pF capacitor onto SMA connectors that were soldered onto a copper clad board. This was also repeated for a 330 nH inductor. The purpose of this experiment was to measure the self resonant frequency of the inductor and capacitor. We are interested in measuring the self resonant frequency because passive components are dominated by their parasitics once the frequency reaches beyond this value. 

With a NanoVNA, we can visualize the self resonant frequency by analyzing the trace on the smith chart. In general, we learned that the bottom half of the smith chart represents the capacitive reigion, whereas the top half represents the inductive region.

<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture13_200pf.png" width="500"> 
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture14_Inductor%20-%20277-4-01-w%20item%20number_2929SQ-331JE.png" width="500"> 
  </p><p align = "center"> 'Figure 15 & 16: VNA Measurements: 200 pF Capacitor and 330nH Inductor'
</p>

## Simulation Results
![Capacitor](https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Capacitor.JPG)
![Inductor](https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Inductor.JPG)
## Discussion

## Conclusion
