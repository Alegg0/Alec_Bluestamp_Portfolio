# coreXY 3d printer
A coreXY 3d printer involves a gantry where the x and y axes move, and a vertical z axis. This configuration of 3d printer is superior to traditional "bed slinger" printers where the y and z axes are attatched to each other, inducing stress on the system as the z axis has to lift the heavy toolead. A coreXY alleviates this issue by moving z axis independently from the x and y, allowing for longer printer lifespan and faster prints.


| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Alec G | Saratoga High School | Aerospace Engineering | incoming junior

<!--- ![Headstone Image](Alec.jpg) -->
<img src = "Alec.jpg" style= "width:50%; height: 50%">

# Third Milestone
My third milestone involved installing firmware on my 3d printer and getting it to print a "benchy" (a benchmark test in the shape of a boat for 3d printers). 

This milestone was by far the most challenging, but I also learned the most from it. Throughout the process of achieving an acceptable print, I short circuited and fried a motherboard, caused a small explosion, and had to rewire my entire printer several times. 

I began the process by using Raspberry Imager to setup a Mainsail/Klipper profile on a raspberry pi 4. I then used SSH to access my raspberry pi console (running on Debian Linux), where I was able to flash Klipper on my SKR Pico motherboard. I had some issues with SSH, being unable to connect to it on my laptop. However, after reconfiguring my computer's IP v6 compatabiliy, I was able to access my raspberry pi and Mainsail interface.

After wiring everything together, I attempted to "home" my 3d printer using sensorless homing. However, I ran into the issue that my printer was unable to detect when the stepper motors were experiencing a stall, and therefore, the sensorless homing would fail every time. I tried to fix this issue by jumping the pins for the x and y endstops (which I did not have), but that caused a short circuit and fried my motherboard.

I replaced the SKR Pico with an SKR Mini V3, and redid the entire process of flashing Klipper and using SSH to create the configuration files for my printer. However, because I still had not jumped the x and y axes endstop pins, sensorless homing still did not work. The SKR Mini V3 has diagnostic pins for the x and y endstops, and after jumping those pins, sensorless homing started working. I was able to begin my first print, but the printer was underextruding, resulting in nothing coming out the nozzle. After a bit of troubleshooting with the extruder, I found that loosening a screw on the Sherpa Mini extruder fixed the extrusion issue. 

However, my initial benchy prints either failed or completely ripped off the bed. The Klippy log files displayed an error of m2 and m3 arcs not being recognized, so after a bit of research I configured my printer to recognize m2 and m3 arcs. After this, my prints looked much cleaner and I was able to print a benchy that surpassed the quality of ender 3 printers, and approaching the quality of high-end printers such as Prusas and Bambulabs.

## SKR Pico 


# Second Milestone

My second milestone involved the assembly and wiring of my printer. This task involved redesigning and printing several components, and the usage of several materials such as PLA and PETG.
### Upper Frame
I began with the assembly of the upper frame and gantry of my printer, which involved using 3x4x5 heat inserts to make threaded holes in my plastic parts. These heat inserts allowed me to screw on 200mm MGN9C linear rails with 4 m3x16 screws for the X axis as well as the motor and ilder mounts (using m3x8). The idler bearings were screwed on with m5x25 screws, and the motors with m3x8 screws. 
### Heatbed Assembly
The bed required a few tries to get right because of some spacing issues with the 8mm linear bearings, and an issue with Z-Axis belting. For bed leveling, I installed 3 thumb screws and 3 springs on m3x50 screws, and attatched the heat bed on top of them. 
### Y axis
For the Y axis, I attatched the 150mm MGN9C rail to the left and right carriages with m3x8 screws.
### Linear Rod Installation
I then attatched the 200x8mm linear rods to both the top and bottom frames, using heat inserts and m3x6 screws a set screws to hold them in. Anticipating damage to the rods because of the set screws, I covered the ends of the linear rods with painter's tape. 
### Bottom Frame
Assembling the bottom frame also took several iterations. The first iteration lacked set screws, so the linear rods would often detatch. The second iteration had an unforseen issue of motherboard mounting, and the third iteration fixed all of these issues. I then mounted the SKR Pico motherboard using m3x4x4 heat inserts, the Z axis endstop switch with m2 screws, and the Z motor with m3x8 screws. The feet were mounted with m5x20 screws.
### Toolhead
I used a soldering iron to heat press m3 nuts into the toolhead (which was printed in PETG for better heat resistance), and screwed in the CR-10 Hotend. The 2 part cooling fans were installed on the side using m2.5 screws, and the central hotened fan was installed by heat inserting screws into small holes. 
### Extruder
My printer uses a sherpa mini extruder in a direct-drive configuration to move filament, but when I 3d printed the parts I found that the tolerances were way too off for the extruder to be effective. I instead used a CNCed aluminum version, which worked much better.
### Wiring
Wiring was an issue, as I did not have access to JST wire extendors. Therefore, I cut the existing wires and soldered more wire onto them, extending my wires to the necessary lengths. I had to do this for all 3 of the fan wires, and the thermistor wire for my heatbed. I also had to cut and rearrange the wires for my stepper motors, as I discovered that the configuration they were in was not compatible with the SKR Pico motherboard. 

## Challenges
During the assembly of the printer I encountered many issues regarding spacing. These issues caused me to have to reprint many large parts after changing something very small, resulting in a large amount of wasted filament. 
#### Heatbed
Like the toolhead, the heatbed was printed out of PETG material instead of PLA, due to its ability to withstand high temperatures. During assembly, I realized that there was too much tolerance on the bearing holes, causing the bed to slip on and off of the bearings. I solved this issue by drilling 4mm holes into the walls, and using 3x4x5 heat inserts and m3 screws as set screws to hold the printed part in place. 
#### Wiring
When testing, I noticed that all of my stepper motors were vibrating, instead of revolving. Initially believing this to be a software issue, I spent many hours on the printer.config file trying to debug the issue. However, I realized that the color ordering of the 4 pin connectors were inconsistent, leading me to the conclusion that the motors were not functioning due to this inconsistency. After cutting the wires and resoldering them together in different configurations, the motors moved in the correct directions.

# First Milestone
<iframe width="560" height="315" src="https://www.youtube.com/watch?v=mP-Wq3X1T_g" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

My project is a mostly 3d printed CoreXY 3d printer, and for my first milestone I CADed all the necessary parts. After taking some inspiration from Rolohaun3D's "Rook" CoreXY printer, I used Onshape, a browser-based CAD software to model 3 nema 17 stepper motor mounts, 2 carriages, 2 idlers, the upper and lower frames, build plate/bed support, and mounts for the motherboard and power supply.

## Challenges
While CADing, I ran into the issue of part dimensions, and the issue of spacing. I was able to find an open source library of common 3d printer parts on the internet, and imported them into my Onshape document. I then used the assembly feature to make sure that all the parts I modeled would fit together. 

In addition, I printed out a couple of parts for testing, and though I did try to compensate for prints shrinking, there was still a significant amount of shrinking that made some parts unsuitable for use. Before reprinting, I made sure that the new parts had more tolerance.

# Starter Project

<iframe width="560" height="315" src="https://www.youtube.com/embed/ft7FQacSrX8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Description:

My starter project used the Arduino starter kit, and is a small trashcan whose lid opens when a ultrasonic sensor detects an object within 10 cm of it. When it triggers, a servo turns to the 90 degree position, functioning as the lid. The servo will remain in the 90 degree position until the object is no longer within a certain threshold. I used Onshape to model a box and a lid, and printed them out. I also routed most of the wiring inside the box for aesthetic purposes. For the circuit itself, I created a prototype on a breadboard, and after testing my code on it, I transferred the wiring to a protoshield. 

## Software:
My project was programmed in the Arduino IDE, and involves a while loop that runs if there is an object within the distance threshold, checking every 100 milliseconds. If the while loop triggers, it triggers the servo to move to the 90 degree position, and then refreshes its value for the distance to the object. Once the loop stops running, the servo is programmed to return to the neutral position.

## Challenges:
I experienced some trouble while using the Arduino IDE. As I am familiar with other programming languages such as java and python, I assumed that the "output" window on the IDE was its console, so when I was looking for the values my code was supposed to be outputting, I couldnt find anything on the output. I thought that it was a software issue, so I spent a long time searching for a bug. However, I eventually discovered the "Serial Console", which was where my values were being output.
# Code

```c++
#include <Servo.h>

#define echoPin 12
#define trigPin 11
// choose pin for the buzzer
int servoPin = 9;      // Servo Pin
int distanceThreshold = 10;

Servo Servo1;             // creating servo object

void setup() {
  Serial.begin (9600);
  pinMode(trigPin, OUTPUT); // Set trigPin as OUTPUT
  pinMode(echoPin, INPUT);  // Set echoPin as INPUT
  Servo1.attach(servoPin);  // attaching servo pin
}

void loop() {
  long duration, distance;
  
  // Send a pulse to trigPin
  digitalWrite(trigPin, LOW); 
  delayMicroseconds(2); 
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10); 
  digitalWrite(trigPin, LOW);
  
  duration = pulseIn(echoPin, HIGH);
  distance = (duration / 2) / 29.1;

  Serial.print(distance);
  Serial.print(" ");

  while (distance < distanceThreshold){
    Servo1.write(90);
 
    Serial.print("something happened! ");
    digitalWrite(trigPin, LOW); 
    delayMicroseconds(2); 
    digitalWrite(trigPin, HIGH);
    delayMicroseconds(10); 
    digitalWrite(trigPin, LOW);
    duration = pulseIn(echoPin, HIGH);
    distance = (duration / 2) / 29.1;
    delay(500);
  }

    Servo1.write(0);

  delay(1000);
}
```
<!---
# Bill of Materials
-->
<!---
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
-->
