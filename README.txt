Buy those Pictured components and Connect them accordingly with arduino.


1. HC-05:
 TXD - 0
 RXD - 1
 VCC - 3.3V VCC of Arduino UNO  
 GND - Any GND Of Arduino UNO
leave the other two(State and KEY) disconnected.  

2. L293D:

Connect the IN1 pin to the D2 pin of the Arduino UNO.
Connect the IN2 pin to the D3 pin of the Arduino UNO.
Connect the IN3 pin to the D4 pin of the Arduino UNO.
Connect the IN4 pin to the D5 pin of the Arduino UNO.



3. Ultrasonic Sensor:

Component	    Arduino Pin
Ultrasonic TRIG 	9
Ultrasonic ECHO	       10
VCC                     5V
GND                   GND

4.Motor : 
LeftFront and LeftBack with Left part or L293D of M1 of picture. 
RightFront and RightBack with Right part or L293D of M1 of picture. 

5. Battery:

 Arduino UNO -
  Positive(+) of battey: VIN of Arduino
  Negative(-) of battey: any GND of Arduino  

 L293D - 

  battary Positive(+) : with Left   12V of L293D
battary Negative(-) : with Right   GND of L293D
Leave The Middle one.

