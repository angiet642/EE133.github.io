# Lab 2: Generating Waveforms on a Si5351 Clock Generator Chip
## Authors:
Author: Angie Thai\
Lab Partner: Kylee Krzanich

## Abstract:
In this lab, we use a [Si5351 Clock Generator](https://learn.adafruit.com/adafruit-si5351-clock-generator-breakout/overview) to generate waveforms, which allowed us to learn more about clock generators and how they are used in modern day electronics. To do this, we used an [ItsyBitsy M4 Express microcontroller](https://learn.adafruit.com/introducing-adafruit-itsybitsy-m4?view=all) and circuit python to configure the devices. 

## Background:
In digital circuits, we often analyze the output behavior of a logic design using terms such as the "rising edge" or "falling edge" of the clock. An example of a typical clock signal is a square wave as shown in the image below:
<p align="center">
  <img src="https://www.electronics-tutorials.ws/wp-content/uploads/2018/05/sequential-seq4.gif" width="400"> 
  <p align = "center"> 'Figure 1'</p>
</p>


## Procedure
This lab required using an ItsyBitsy to interface with the Si5351 clock generator. Therefore, we began by soldering pin headers to the board and mounting the components on a breadboard. Once this was complete, wired connections were made between the ItsyBitsy and the Si5351 I2C and power ports.
<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab2/Lab2_image/IMG_9278.jpg" width="400"> 
  <p align = "center"> 'Figure 1'</p>
</p>

## Results
<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab2/Lab2_image/IMG_5028.JPG" width="500"> 
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab2/Lab2_image/IMG_5034.JPG" width="500"> 
  <p align = "center"> 'Figures 2,3: Time domain representation of each channel'</p>
</p>


<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab2/Lab2_image/IMG_5029.JPG" width="500">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab2/Lab2_image/IMG_5035.JPG" width="500"> 
  <p align = "center"> 'Figures 4,5: Frequency domain representation of each channel'</p>
</p>

<p align="center">
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab2/Lab2_image/IMG_5030.JPG" width="500"> 
  <img src="https://github.com/angiet642/EE133.github.io/blob/main/Lab2/Lab2_image/IMG_5036.JPG" width="500"> 
  <p align = "center"> 'Figures 6,7: Frequency domain representation of each channel'</p>
</p>



##Discussion


## Conclusion
