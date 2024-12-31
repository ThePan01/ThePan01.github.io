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


## Conclusion
By using the Arduino Nano C to control the movement of the servos, the heart can currently simulate a real heartbeat. In the future, I may use this device to simulate different heart conditions. At the same time, I am considering whether, with the ongoing development of brain-machine interfaces, it might be possible to connect the artificial heart to the nervous system, allowing it to better simulate the function of a natural heart.

_Reference: [https://www.instructables.com/Silicone-Skin-3D-Printed-Realistic-Animatronic-Hea/](https://www.instructables.com/Silicone-Skin-3D-Printed-Realistic-Animatronic-Hea/)_

![featured2](https://github.com/user-attachments/assets/0d7168e0-1a38-4d96-8666-c13ee8584448)
![featured3](https://github.com/user-attachments/assets/3910a45e-2c21-4826-845b-1ce38b7f2214)




