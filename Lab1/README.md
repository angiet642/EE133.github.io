# Lab 1: Using VNAs to Measure Parasitic Properties of Passive Componenets 

## Authors:
Author: Angie Thai\
Lab Partner: Kylee Krzanich

## Abstract: 
Passive components are devices that do not generate energy or require power to operate, such as resistors, capacitors, and inductors. To analyze such devices, a vector network analyzer can be used to visualize and measure the properties of each component.  

## Introduction:
In this lab, the performance of passive components are measured within a specified frequency band. These measurements were achieved using a vector network analyzer, a device that measures signals that pass through the device under test (DUT) and also the signals reflected back from the DUT. Thoughout the report, the transmitted signal will be referred to as the "S21" parameter, and the reflected signal will be referred to as the "S11" parameter. Measurements from the VNA include impedance measurements on a smith chart in addition to the magnitude of S21 and S11 signals. All measurements are swept through a predefined frequency range to show the continuous changes of a device as a function of frequency. 

## Experimental Set-Up
Prior to measuring the parasitic effects of a capacitor and inductor, we first familiarized ourselves with the NanoVNA. Calibrating the NanoVNA was done using the RF demo kit board (pictured below). Blocks 13-16 on the board describe the SOLT calibration process, which stands for "short", "open", "load" and "through". This calibration must be done to account for the effects of the cables connected between the VNA and DUT. Each time the frequency sweep is adjusted, re-calibration is required. 

<p align="center">
<img src="https://m.media-amazon.com/images/I/81smXiQSngL._SL1500_.jpg" width="400">
<img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/RF_DemoKIt.jpg" width="400">
</p>

## Measurements and Results

## Simulation Results
![Capacitor](https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Capacitor.JPG)
![Inductor](https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Inductor.JPG)
## Discussion

## Conclusion
