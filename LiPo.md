These are the LiPo Specifications and the logic behind why for this assembly:

Voltage Requirements:
1. LM780D (5V) / 7V (2V dropoff)
2. LCD Display(5V)
3. Arduino(5V)

As per these requirements, we can safely a utilize a 2S LiPo voltage, which has a nominal voltage of 7.4V. This is to note that the effectiveness of the battery will decline overtime, with the battery failing at 25% charge (7V) because of the dropout voltage of the LM7805 module(it loses on average 2V to run a 5V output). Hence, it requires 7V.

Current requirements:
1. Arduino uno: 50mA
2. LCD Display(i2C w/ Backlight): ~20mA
3. Piezo Buzzer: 5mA
4. DC Motor: 300mA / 60mA(no load)
5. L293D Driver: 10mA

Peak Current: 385 mA
Average Current: 145 mA(with DC motor Idle)

So, ideally we'd like to use something like a 2200mAh or even 1000mAh battery. Now, let us assume a safety margin of say, 50%.

Current Requirement(as per safety margin) = (150/100) x 0.385A = 0.58A
Utilizing a 1000mAh battery we obtain,
 Required C rating =  0.58A / 1Ah = 0.58C
Utilizing a 2200 mAh battery we obtain,
 Required C rating = 0.58A / 2.2Ah = 0.26C

 So we can say for certain that the rating of the LiPo battery should ideally be: 2S, 0.58C.

As for voltage regulation, no- it isn't additionally required since we already have the LM7805 to regulate. This is because the LM7805
regulates the 7V-8.4V provided by the cell which exceeds the Arduino as well as LCD safe limits(5V max). Hence, it is a correct measure for voltage regulation.
