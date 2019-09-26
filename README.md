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

[My LED Video]

## Part C. Voltage Varying Sensors 
 
### 1. FSR, Flex Sensor, Photo cell, Softpot

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
 
**a. Include your accelerometer read-out code in your write-up.**

[My LED Accelerometer Code]https://github.com/fpdaiber/IDD-Fa19-Lab3/blob/master/LED_Accelerometer.ino

### 3. IR Proximity Sensor

**a. Describe the voltage change over the sensing range of the sensor. A sketch of voltage vs. distance would work also. Does it match up with what you expect from the datasheet?**

**b. Upload your merged code to your lab report repository and link to it here.**

## Optional. Graphic Display

**Take a picture of your screen working insert it here!**

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
 
**a. Insert here a copy of your final state diagram.**

### 3. Create your data logger!
 
**a. Record and upload a short demo video of your logger in action.**
