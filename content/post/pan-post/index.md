---
title: Reproducing the Servo Heart
date: 2024-12-30
---

## Project Introduction
This project involves creating a 3D-printed electronic heart, driven by an Arduino Nano C to control an MG90 servo motor. The servo moves the 3D-printed shell, simulating the beating of a heart.

![featured](https://github.com/user-attachments/assets/a269c019-39e6-472d-8758-301a98ef41e4)

## Materials Needed  
M2*6 self-tapping screws, M3*10 self-tapping flat head screws (several)  

Arduino Nano C (type-C 5V1A power supply)  
 _The original motherboard is an Arduino Micro, but since I had a similar-functioning Arduino Nano C, I used it as a substitute. In terms of functionality, the two are quite similar._ 

MG90 servo motors *3  
_The original design used a servo driver board, but after analysis, I determined that both Arduino boards can directly drive the servos, so I removed this part._  

Potentiometer  

Wires (several)  

# 3D Printing  
The 3D printer used is the Bambu Lab P1P.  
The 3D printing material used is Bambu Lab PLA Biasc.  
There are no special requirements for printing, except that the components must have reasonable high resolution and strength. The default printing settings are sufficient.
![featured](https://github.com/user-attachments/assets/a717f789-58b3-4032-80ff-255a09770054)

# Assembly and Debugging  
1. Install the three servos onto the base and thread the servo wires through the reserved holes.  
2. Drill holes and cut the servo plates, then connect them to the printed linkages with screws. Afterward, fix the servo plates and linkages to the servos and the shell.  
3. Adjust the tightness of the screws to ensure that all parts are movable.  
4. Install the potentiometer in a suitable position and connect the wires from the servos and potentiometer to the Nano C.  
5. Program the servos to rotate and simulate the heartbeat.

{{< highlight cpp >}}
//Nilheim Mechatronics Servo Heart Mechanism Code
//Make sure you have the Adafruit servo driver library installed >>>>> https://github.com/adafruit/Adafruit-PWM-Servo-Driver-Library
//Potentiometer Pin = A0


#include <Wire.h>
#include <Adafruit_PWMServoDriver.h>

// called this way, it uses the default address 0x40
Adafruit_PWMServoDriver pwm = Adafruit_PWMServoDriver();
// you can also call it with a different address you want
//Adafruit_PWMServoDriver pwm = Adafruit_PWMServoDriver(0x41);
// you can also call it with a different address and I2C interface
//Adafruit_PWMServoDriver pwm = Adafruit_PWMServoDriver(&Wire, 0x40);

// Depending on your servo make, the pulse width min and max may vary, you 
// want these to be as small/large as possible without hitting the hard stop
// for max range. You'll have to tweak them as necessary to match the servos you
// have!
#define SERVOMIN  140 // this is the 'minimum' pulse length count (out of 4096)
#define SERVOMAX  520 // this is the 'maximum' pulse length count (out of 4096)

// our servo # counter
uint8_t servonum = 0;

int sensorValue = 0;        // value read from the pot
int outputValue = 0;

int xval;
int timePeriod = 1000;
float y=0;
float t=0;
float d=330;


void setup() {
  Serial.begin(9600);
  Serial.println("8 channel Servo test!");
  pinMode(A0, INPUT);
  pinMode(2, INPUT);
  pwm.begin();
  
  pwm.setPWMFreq(60);  // Analog servos run at ~60 Hz updates

  delay(10);
}

// you can use this function if you'd like to set the pulse length in seconds
// e.g. setServoPulse(0, 0.001) is a ~1 millisecond pulse width. its not precise!
void setServoPulse(uint8_t n, double pulse) {
  double pulselength;
  
  pulselength = 1000000;   // 1,000,000 us per second
  pulselength /= 60;   // 60 Hz
  Serial.print(pulselength); Serial.println(" us per period"); 
  pulselength /= 4096;  // 12 bits of resolution
  Serial.print(pulselength); Serial.println(" us per bit"); 
  pulse *= 1000000;  // convert to us
  pulse /= pulselength;
  Serial.println(pulse);
 // pwm.setPWM(n,
{{< /highlight >}}

## Conclusion
By using the Arduino Nano C to control the movement of the servos, the heart can currently simulate a real heartbeat. In the future, I may use this device to simulate different heart conditions. At the same time, I am considering whether, with the ongoing development of brain-machine interfaces, it might be possible to connect the artificial heart to the nervous system, allowing it to better simulate the function of a natural heart.

_Reference: [https://www.instructables.com/Silicone-Skin-3D-Printed-Realistic-Animatronic-Hea/](https://www.instructables.com/Silicone-Skin-3D-Printed-Realistic-Animatronic-Hea/)_

![featured2](https://github.com/user-attachments/assets/0d7168e0-1a38-4d96-8666-c13ee8584448)
![featured3](https://github.com/user-attachments/assets/3910a45e-2c21-4826-845b-1ce38b7f2214)




