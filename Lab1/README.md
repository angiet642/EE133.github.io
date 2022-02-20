# Lab 1: Measuring "Parasitic" Properties of Passive Components with a VNA

## Authors:
Author: Angie Thai\
Lab Partner: Kylee Krzanich

## Abstract: 
Passive components are devices that do not generate energy or require power to operate, such as resistors, capacitors, and inductors. To analyze such devices, a vector network analyzer can be used to visualize and measure the parasitic properties of each component. Measuring parasitics will give rise to an important observation relative to the frequency and impedance. This observation is known as the self-resonant frequency.   

## Introduction:
In this lab, the performance of passive components are measured within a specified frequency band. These measurements were achieved using a vector network analyzer, a device that measures signals that pass through the device under test (DUT) and also the signals reflected back from the DUT. Thoughout the report, the transmitted signal will be referred to as the "S21" parameter, and the reflected signal will be referred to as the "S11" parameter. Measurements from the VNA include impedance measurements on a smith chart in addition to the magnitude of S21 and S11 signals. All measurements are swept through a predefined frequency range to show the continuous changes of a device as a function of frequency. 

## Procedure
### Setting up the VNA
Prior to measuring the parasitic effects of a capacitor and inductor, we first familiarized ourselves with the NanoVNA. Calibrating the NanoVNA was done using the RF demo kit board (pictured below). Blocks 13-16 on the board describe the SOLT calibration process, which stands for "short", "open", "load" and "through". This calibration must be done to account for the effects of the cables connected between the VNA and DUT. Each time the frequency sweep is adjusted, re-calibration is required. The NanoVNA-QT software was used to view measurements from the VNA through a USB connection to a laptop

<p align="center">
<img src="https://m.media-amazon.com/images/I/81smXiQSngL._SL1500_.jpg" width="400">
<img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/RF_DemoKIt.jpg" width="400" hspace="50"/>
</p>

### Measuring the RF Demo Kit Board
After calibrating the NanoVNA, we measured blocks 1-12 on the RF demo kit to verify the readings of various circuits as illustrated on the board. Overall, we found that our smith trace and measurements were aligned with the illustrations on the board.
<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture1.png" width="500" > 
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

With a NanoVNA, we can visualize the self resonant frequency by analyzing the trace on the smith chart. The bottom half of the smith chart represents the capacitive reigion, whereas the top half represents the inductive region. We can identify the self resonant frequency of a capacitor by finding the frequency at which the trace of the smith chart crosses from the capactive region to the inductive region. The same applies to the inductor except now we want to find the crossover from the inductive region to the capacitive region. 

<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/coppler_clad.jpg" width="300">  
  </p><p align = "center"> 'Figure 13: VNA Measurements: 200 pF Capacitor and 330nH Inductor + Copper Clad'
</p>




<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture13_200pf.png" width="500"> 
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Picture14_Inductor%20-%20277-4-01-w%20item%20number_2929SQ-331JE.png" width="500"> 
  </p><p align = "center"> 'Figure 14 & 15: VNA Measurements: 200 pF Capacitor and 330nH Inductor'
</p>


The reason this phenomenon occurs can be described through a more realisitic schematic of a capacitor and inductor as shown below. Each schematic shows that an "ideal" component actually contains other passive components in parallel or in series due to Maxwell's equations. 

<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Capacitor_model.png" width="500"> 
  </p><p align = "center"> 'Figure 16: Realistic Capacitor Model'
</p>

<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/inductor_model.png" width="300"> 
  </p><p align = "center"> 'Figure 17: Realistic Inductor Model'
</p>


## LTSpice Simulation Results
Another way to visualize the self resonant frequency effect is by simulating the more "realistic" schematics of the components in LTspice. We use AC analysis for simulation so we can plot the impedance as a function of frequency.

<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Capacitor.JPG"> 
  </p><p align = "center"> 'Figure 18: Realistic Capacitor Model Simulation'
</p>

__Using the cursor, the self resonant frequency is approximately 18.3MHz for the simulated capacitor__

<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/Inductor.JPG"> 
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab1/Lab1_Images/inductor_ltspice.JPG" width="250"> 
  </p><p align = "center"> 'Figure 19: Realistic Inductor Model Simulation'
</p>

__Using the cursor, the self resonant frequency is approximately 505MHz for the simulated inductor.__

## Discussion
To calculate the self-resonant frequency, we can use the equation below if the parasitic values are known. We can also compare the expected vs actual measurements, which are summarized in table 1 and 2 below. 
<p align="center"><img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRsW66-aeM90-AjHHNDqs0iN_Ph_5MxZrlm7Q&usqp=CAU" width="150"> </p>
<p align = "center"> 'Self-Resonant Frequency Equation'</p> 

__Table 1: Comparison between LTSpice and Hand Calculation__
|Component | Hand Calculation  | LTSpice Measurements |  
| ------------- | ------------- | ------------- | 
| 0.1uF Capacitor| 18.377 MHz | 18.3 MHz | 
|100nF Inductor| 503.3 MHZ| 505 MHz |

__Table 2: Comparison between NanoVNA and datasheet__
|Component | Data Sheet Spec  | NanoVNA Measurements |  
| ------------- | ------------- | ------------- | 
| 200 pf Silver Mica Capacitor| 336.27 MHz (if ESL = 1.12 nH) | 336 MHz | 
| 330 nH Inductor| 660 MHZ [Datasheet](https://octopart.com/2929sq-331jec-coilcraft-24518110)| 800 MHz |

In table 2, I was unable to find the datasheet for the capacitor used. Therefore, I calculateed what the expected ESL should be to achieve the result from the NanoVNA measurement. According to this [article](https://resources.altium.com/p/which-type-capacitor-should-you-use), the Silver Mica Capacitor should have low ESR/ESL values. Thus, we should expect a ESL that is small to maintain high precision of the component. 

For the 300 nH inductor, we see that our NanoVNA measurement differs from the datasheet by +140 MHz. This large discrepency is unexpected. One possibility that may have contributed to the error is due to distance between the SMA connectors that the inductor was soldered between. In lab, we struggled with soldering the inductor between the two SMA connectors because our connectors were far apart compared to other groups. We were cautious when moving the legs of the inductor to align with our SMA connector layout, however, we may have stretched the inductor coil during this process. When the inductor is stretched, the coils are less compact, which yields a weaker magnetic field. This would have decreased the inductance, which would have increased the self resonating frequency measurement. This proves that stretching the inductor is likely the cause for the high measurement from the NanoVNA. To reduce the error, we should have moved the SMA connectors closer together and leave the inductor legs untouched.

## Conclusion
In conclusion, we were able to successfully use a NanoVNA to measure different functions of the RF demo kit board. This confirmed our learnings pertinent to the smith chart and gave us confidence in using smith chart for analysis. We were also able to simulate, measure, and interpret the self-resonant frequency of an inductor and capacitor using the VNA and LTspice. We now have a clear understanding of self-resonant frequency and how parasitics can corrupt the performance of a circuit if the operating frequency range is not chosen carefully. In other words, we must be mindful of the self-resonant frequency when designing our circuits to account for any undesireable factors. Furthermore, we have added the NanoVNA to our measurement toolbox for future works. 
