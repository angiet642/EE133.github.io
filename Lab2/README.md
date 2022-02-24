# Lab 2: Generating Waveforms on a Si5351 Clock Generator Chip
## Authors:
Author: Angie Thai\
Lab Partner: Kylee Krzanich

## Abstract:
In this lab, we use a [Si5351 Clock Generator](https://learn.adafruit.com/adafruit-si5351-clock-generator-breakout/overview) to generate waveforms, which allowed us to learn more about clock generators and how they are used in modern day electronics. To do this, we used an [ItsyBitsy M4 Express microcontroller](https://learn.adafruit.com/introducing-adafruit-itsybitsy-m4?view=all) and circuit python to configure the devices. 

## Background:
In digital circuits, we often analyze the output behavior of a logic design using terms such as the "rising edge" or "falling edge" of the clock. An example of a typical clock signal is a square wave (as shown in Figure 1). Without a clock signal, the output data will not change with respect to the input. Thus, we can recognize the clock generator being one of the key components in all digital circuits.
<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab2/Lab2_image/sequential-seq4.gif" width="350"> 
  <p align = "center"> 'Figure 1: Sequential Logic Circuit High Level Diagram'</p>
</p>

The Si5351 is a programmable clock generator that can generate frequencies from 8KHz to 150MHz using PLL's and dividers. To understand the internal structure of the chip, we can refer to the block diagram illustrated in figure 2. According to the diagram, we see that the chip uses two phased lock loops (PLLs) with 3 synthesizers. We will understand how these blocks are used in the following section.

<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab2/Lab2_image/block_diagram.JPG" width="600"> 
  <p align = "center"> 'Figure 2: Si5351 Block Diagram from Datasheet'</p>
</p>

## Procedure
This lab required using an ItsyBitsy to interface with the Si5351 clock generator. Therefore, we began by soldering pin headers to the breakout board and mounting the components on a breadboard. Once this was complete, wired connections were made between the ItsyBitsy and the Si5351 I2C and power ports. The final assembly is shown in Figure 3.
<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab2/Lab2_image/IMG_9278.jpg" width="400"> 
  <p align = "center"> 'Figure 3: Si5351 breakout board connected to an ItsyBitsy MCU'</p>
</p>

Now that the boards are connected, we followed a circuit python [tutorial](https://learn.adafruit.com/adafruit-si5351-clock-generator-breakout/circuitpython) to control the output clocks of the Si5351 board. Below is a snippet of the code that was used to generate the clock waveforms at various frequencies. 
- Clock 0: 112.5 MHZ
- Clock 1: 13.55 MHz
- Clock 2: 10.706 kHz 

These waveforms were also measured on an ocsilloscope and spectrum analyzer, which will be discussed in the results section. The reason I included a snippet of the code below is to show the comments that clearly describe how the clock generator synthesizer is set up to generate the different output clock frequencies. We see that the common factor used between the 3 clock outputs is 25 MHz, which is the frequency of the crystal inside the chip. This frequency is multipled (using the PLL's) to create an "intermediate" clock at a higher frequency, before it is divided to achieve the desired output frequency. Overall, the code decribes how the functional blocks are used in the block diagram from figure 2, which matches the funtional description in the Si5331 [datasheet](https://cdn-shop.adafruit.com/datasheets/Si5351.pdf)

```python
  /* INTEGER ONLY MODE --> most accurate output */
  /* Setup PLLA to integer only mode @ 900MHz (must be 600..900MHz) */
  /* Set Multisynth 0 to 112.5MHz using integer only mode (div by 4/6/8) */
  /* 25MHz * 36 = 900 MHz, then 900 MHz / 8 = 112.5 MHz */
  Serial.println("Set PLLA to 900MHz");
  clockgen.setupPLLInt(SI5351_PLL_A, 36);
  Serial.println("Set Output #0 to 112.5MHz");
  clockgen.setupMultisynthInt(0, SI5351_PLL_A, SI5351_MULTISYNTH_DIV_8);

  /* FRACTIONAL MODE --> More flexible but introduce clock jitter */
  /* Setup PLLB to fractional mode @616.66667MHz (XTAL * 24 + 2/3) */
  /* Setup Multisynth 1 to 13.55311MHz (PLLB/45.5) */
  clockgen.setupPLL(SI5351_PLL_B, 24, 2, 3);
  Serial.println("Set Output #1 to 13.553115MHz");
  clockgen.setupMultisynth(1, SI5351_PLL_B, 45, 1, 2);

  /* Multisynth 2 is not yet used and won't be enabled, but can be */
  /* Use PLLB @ 616.66667MHz, then divide by 900 -> 685.185 KHz */
  /* then divide by 64 for 10.706 KHz */
  /* configured using either PLL in either integer or fractional mode */

  Serial.println("Set Output #2 to 10.706 KHz");
  clockgen.setupMultisynth(2, SI5351_PLL_B, 900, 0, 1);
  clockgen.setupRdiv(2, SI5351_R_DIV_64);
```

## Results
Now that we have understood how the PLL's and synthesizers are used to generate the different clock frequencies, we can verify outputs by taking measurements on an oscilloscope and spectrum analyzer. At each clock output, we expect to see a square wave.

In figures 4 and 5, we measured the 10.706 kHz clock output. On the oscilloscope, we noticed that the square wave is very clear with no visible distortion. In the frequency domain, it is clear that maximum amplitude is around the center frequency of 10.5kHz. 
<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab2/Lab2_image/IMG_5030.JPG" width="500"> 
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab2/Lab2_image/IMG_5036.JPG" width="500"> 
  <p align = "center">  <b>'Figures 4,5: Time/Frequency Measurement of Clock Frequency at 10.706 kHz'</b></p>
</p>

In figures 6 and 7, we measured the 13.55 MHz clock output. On the oscilloscope, we noticed that the square wave is more visible, but has slight distortion. In the frequency domain, it is clear that maximum amplitude is around a center frequency of 13.5MHz. However, the peak has a larger bandwidth compared to the 10.7kHz output, indicating that  other frequencies are present; therefore distorting the square wave shape of the output.
<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab2/Lab2_image/IMG_5029.JPG" width="500">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab2/Lab2_image/IMG_5035.JPG" width="500"> 
  <p align = "center">  <b>'Figures 6,7: Time/Frequency Measurement of Clock Frequency at 13.55 MHz'</b></p>
</p>

In figures 8 and 9, we measured the 112.5 MHz clock output. On the oscilloscope, we noticed that the square wave is visibly distorted. This distortion goes hand-in-hand with the large bandwith shown at center frequency of 112.5 MHz, which indicates that there is strong frequency content present around the center frequency.
<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab2/Lab2_image/IMG_5028.JPG" width="500"> 
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab2/Lab2_image/IMG_5034.JPG" width="500"> 
  <p align = "center"> <b>'Figures 8,9: Time/Frequency Measurement of Clock Frequency at 112.5 MHZ'</b></p>
</p>


## Discussion
An interesting observation from our measurements is that the square wave measurement became distorted as the frequency of the clock generated increased. In the datasheet, we were warned that certain oscilloscopes may be unable to accurately measure the 112 MHz waveform. This led me to investigate the model of the oscilloscope that we used, which was the "__DSO6054A Oscilloscope: 500 MHz, 4 Analog Channels__". According to the datasheet, the oscilloscope is capable of measuring waveforms up to 500 MHz; therefore the oscilloscope was not the cause of the distortion in the clock waveform. We also ruled out oscilloscope probes as a source of error/potential bandwidth limiter since we directly used SMA to BNC connectors for our measurements. With the oscilloscope probes, we saw a more sinusoidal waveform in the time domain for the high frequency output. This meant that a direct connection between the SMA and BNC was in our favor and gave us a "better" result. 

Since the oscilloscope was not the root cause of distortion, the other possiblity could be due to high frequency attenuation. We know that square waves can be decomposed into various out of phase sinusoidal waves at high frequencies. Therefore, it is possible that frequencies beyond 14-112 MHz that help make up the high-frequency square wave are filtered out by parasitic capacitors from the PCB board.  

## Conclusion
Using the Si5351, we were able to explore how PLL's and synthesizers can be used to generate different output clock frequencies based on a single resonant crystal. The functionality of the chip is then described through code via circuit python, which allowed us to control the chip through the ItsyBitsy MCU I2C channels. This lab gave us better intution about clock generators and their internal structure/behavior while considering how external factors can effect high frequency signals. Furthermore, interfacting with the embedded devices through hardware and software gave us transferrable skills for future projects that may involve putting together different modules to achieve some goal.
