# Data Logger (and using cool sensors!)

*A lab report by Fabio Daiber*

## In The Report

For this lab, we will be experimenting with a variety of sensors, sending the data to the Arduino serial monitor, writing data to the EEPROM of the Arduino, and then playing the data back.

## Part A.  Writing to the Serial Monitor
 
**a. Based on the readings from the serial monitor, what is the range of the analog values being read?**

0 to 1023 
 
**b. How many bits of resolution does the analog to digital converter (ADC) on the Arduino have?**

10 bits of resolution

## Part B. RGB LED

**How might you use this with only the parts in your kit? Show us your solution.**

[My LED Video](https://drive.google.com/open?id=1SRsN0FYcIjWrv73loGzUpagxaswRwJ33)

## Part C. Voltage Varying Sensors 
 
### 1. FSR, Flex Sensor, Photo cell, Softpot

[]

**a. What voltage values do you see from your force sensor?**

0 to 1023 ideally, but I got with full force only to around 1000 on the serial plotter.

**b. What kind of relationship does the voltage have as a function of the force applied? (e.g., linear?)**

It seems to be a non-linear relationship. Since it is limited and pressing it lightly already has a much higher than linear increase in voltage, I would say its logarithmic 

**c. Can you change the LED fading code values so that you get the full range of output voltages from the LED when using your FSR?**

Yes, I just need to translate the values (0-1023) from the FSR to the the LED values (0-255).

**d. What resistance do you need to have in series to get a reasonable range of voltages from each sensor?**

I used the 10k resistor and got reasonable ranges for each of the sensors.

**e. What kind of relationship does the resistance have as a function of stimulus? (e.g., linear?)**

The flex sensor and FSR seemed to have a logarithmic relationship, the photosensor seemed more like a linear one.

### 2. Accelerometer
 
[Accelerometer Readout Code](https://github.com/fpdaiber/IDD-Fa19-Lab3/blob/master/Accelerometer_Readout.ino)

[My LED Accelerometer Code](https://github.com/fpdaiber/IDD-Fa19-Lab3/blob/master/LED_Accelerometer.ino)

[My Accelerometer Video](https://drive.google.com/open?id=1gqXsrwhZ9OIs06ask1yJv-BFlyHW9U0M)

[My LED Accelerometer Video](https://drive.google.com/open?id=1L6ip1XDxxLvCXOJw2VP8_syrSmLQGZ-4)

## Optional. Graphic Display

![alt text](https://github.com/fpdaiber/IDD-Fa19-Lab3/blob/master/IMG_2431.jpg)

## Part D. Logging values to the EEPROM and reading them back
 
### 1. Reading and writing values to the Arduino EEPROM

**a. Does it matter what actions are assigned to which state? Why?**

Yes, it matters. State 2 writes the memory, State 1 reads the memory and State 0 clears the memory. So, we need the actions exactly in that order to work. 

**b. Why is the code here all in the setup() functions and not in the loop() functions?**

Because we only want to run those code steps once and not have it in a continuous loop.

**c. How many byte-sized data samples can you store on the Atmega328?**

1024 byte-sized ones.

**d. How would you get analog data from the Arduino analog pins to be byte-sized? How about analog data from the I2C devices?**

We have to divide them by four because each byte of the EEPROM can only hold a value from 0 to 255, as analog values are 10 bits and EEPROM can only hold 8 bit ones.

**e. Alternately, how would we store the data if it were bigger than a byte? (hint: take a look at the [EEPROMPut](https://www.arduino.cc/en/Reference/EEPROMPut) example)**

The put method lets us split data bigger than a byte and store the data in multiple bytes of the EEPROM.

**Upload your modified code that takes in analog values from your sensors and prints them back out to the Arduino Serial Monitor.**

### 2. Design your logger
 
![alt text](https://github.com/fpdaiber/IDD-Fa19-Lab3/blob/master/IMG_2438.jpg)

### 3. Create your data logger!
 
**a. Record and upload a short demo video of your logger in action.**

I have changed the write and read example code so that the accelerometer's x variable is converted and stored into the memory and then read out. It does that in a loop every 2 seconds. 

[My Data Logger](https://drive.google.com/open?id=1TAHan60fghWIMEWZ-vNUmiHDqy9LhT3R)
