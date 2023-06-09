# Voice-Controlled RoboCar
**Georgia Institute of Technology - ECE4180 Final Project**

**Creators: Bao Phuc Duong, Cody Ells, Austin Rowland**
## Table of Content
1. [Motivation](#Motivation)
2. [Showcase](#Showcase)
3. [Electronic Components](#Electronic-Components)
4. [System Connections](#System-Connections)
5. [Complete Schematic](#Complete-Schematic)
6. [How RoboCar works](#How-RoboCar-works)
7. [Future Improvements](#Future-Improvements)
## Motivation
* Throughout the course, we've learned a lot about embedded system programming and hardware design, so we're eager to create a brand new robot to see how we utilize our classroom knowledge and showcase our skills.
* We are impressed by how smart Vector and Emo robot can recognize the voice commands and do funny things based on the commands. We are confident we can also create one like that, so we decided to buid this RoboCar.
* We want to have a cool project to put on our resume and our GitHub repo.

## Showcase 
[![RoboCar](https://img.youtube.com/vi/Ly4dVhk6Lw0/0.jpg)](https://youtu.be/Ly4dVhk6Lw0)

**Slide Deck:** [ECE-4180 RoboCar Presentation](https://github.com/PatrickDuong3001/Voice-Controlled_RoboCar/blob/master/ECE4180RobotSildes.pptx?raw=true)

## Electronic Components
* Shadow Chassis: https://www.sparkfun.com/products/13301
* ARM Mbed LPC1768: https://www.sparkfun.com/products/9564
* EasyVR 3 Plus: https://www.sparkfun.com/products/15453
* DC Motor: https://www.sparkfun.com/products/11696
* Battery Holder with Switch: https://www.adafruit.com/product/3859
* LEDs: https://www.sparkfun.com/products/12062
* PCB-Mount Speaker: https://www.sparkfun.com/products/11089
* Dual H-Bridge Motor Driver: https://www.sparkfun.com/products/14451
* Driver Transistor: https://www.sparkfun.com/products/521
* uLCD-144-g2: https://www.sparkfun.com/products/11377

## System Connections
**EasyVR 3 Plus to Mbed**
|EasyVR|Mbed|Batteries|
| --- | --- | -------- |
| TX  | p14 |          |
| RX  | p13 |          |
| 5V  |     |     5V   |
| GND | GND |    GND   |

**Ultrasonic Sensor to Mbed**
|Sonar|Mbed|Batteries|
| --- |--- | --------|
| VCC |    |   5V    |
| Echo| p7 |         |
| Trig| p6 |         |
| GND | GND|  GND    |

**uLCD to Mbed**
|uLCD|Mbed|Batteries|
|--- | ---| ---     |
| 5V |    |   5V    |
| GND|    |  GND    |
| TX | p9 |         |
| RX | p10|         |
| RST| p30|         |

**H-Bridge Motor Driver to Mbed**
|H-Bridge     |     Mbed     |Batteries     |Left Motor  |Right Motor |
|-------------|--------------|--------------|------------|------------| 
| VM          |              |      5V      |            |            |
| VCC         |  VOUT        |              |            |            |
| GND         |  GND         |      GND     |            |            |
| AO1         |              |              |      +     |            |
| AO2         |              |              |      -     |            |
| BO1         |              |              |            |      +     |
| BO2         |              |              |            |      -     |
| PWMA        |  p21         |              |            |            |
| AI1         |  p17         |              |            |            |
| AI2         |  p15         |              |            |            |
| STBY        |  VOUT        |              |            |            |
| BI1         |  p19         |              |            |            |
| BI2         |  p20         |              |            |            |
| PWMB        |  p22         |              |            |            |
| GND         |  GND         |  GND         |            |            |

**Speaker to Mbed**
| Speaker | Mbed |Driver Transistor|Batteries |
| ---     | ---  |  ---            | ---      |
|   +     |      |                 |    5V    |
|         |  p23 |    B            |          |
|         |  GND |    E            |   GND    |
|   -     |      |      C          |          |

**LEDs to Mbed**
| LEDs             |Mbed|
| ---              | ---|
| Front Left LED + | p5 |
| Front Left LED - | GND|
| Front Right LED +| p8 |
| Front Right LED -| GND|
| Back Left LED +  |p18 |
| Back Left LED -  |GND |
| Back Right LED + | p16|
|Back Right LED -  | GND|

## Complete Schematic
<img src="https://github.com/PatrickDuong3001/Voice-Controlled_RoboCar/blob/master/RoboCar.png" width="476" height="685">

## How RoboCar works
**Functions Diagram** 
<img src="https://github.com/PatrickDuong3001/Voice-Controlled_RoboCar/blob/master/diagram.png" width="736" height="414">
* When powered on, the RoboCar actively waiting for voice commands (with EasyVR) and looking for obstacles (with Ultrasonic sensor) in front of it. 
* If the voice command is "Forward", the RoboCar moves forward until it detects an obstacle on its path. To avoid collisions, the RoboCar turns right and waits for the next command. 
* If the voice command is "Backward", the RoboCar moves backward for 3 seconds, then stops and waits for the next command. 
* If the voice command is "Left", the RoboCar turns left. If the voice command is "Right", the RoboCar turns right. After the turn, it waits for the next command. 
* Whenever there's an object within 50mm of the sensing range, no matter what the robot is doing (moving forward or idling), it immediately stops and turns right to avoid collisions. 
* When the RoboCar moves forward, it plays the "Barbie Girl" song with the speaker. When the RoboCar moves backward or turns left/right, it plays a suitable beeping sound.
* When the robot idles, the uLCD displays an idling animation. When the RoboCar moves or turns, the uLCD displays a happy animation.    
* The robot can be powered on and off with a slide switch on its battery case. 

## Future Improvements
* We can add another Ultrasonic sensor at the back of the RoboCar so that it can detect obstacles when moving backward. 
* In addition to "Forward", "Backward", "Left", "Right", we can teach the RoboCar to recognize more voice commands. 
* We can redesign the power source so that the Mbed and the DC Motors can share the same power source instead of using two separate sources. 
* We will redraw the facial expressions for the RoboCar to make it more colorful and lively. 
## Contact Us
**Bao Phuc Duong:** pduong3@gatech.edu

**Cody Ells:** cells3@gatech.edu

**Austin Rowland:** arowland33@gatech.edu
