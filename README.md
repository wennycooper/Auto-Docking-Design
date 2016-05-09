# Auto-Docking-Design

# Demo video
* https://www.youtube.com/watch?v=3ovoX-Vu5Eo

# INTRODUCTION
* This is the auto docking design draft for the ANDBOT.
* The same design could be used in Rugby, Angel and Roadbot.


# COMPONENTS
* On docking station
 * One IR emitter (ASE-1L7), radiant angle = 30 degree
 * Arduino UNO
* On ANDBOT
 * Two IR receiver modules (KSM-963-LM4M), separated by a barrier
 * LimitSW
 * Arduino UNO

# WIRING
* On docking station
 * ![](https://github.com/wennycooper/Auto-Docking-Design/blob/master/onDockingStation.png)

* On ANDBOT 
 * ![](https://github.com/wennycooper/Auto-Docking-Design/blob/master/onRobot.png)


# BASIC OPERATIONS
## Architecture
![](https://docs.google.com/drawings/d/10qjkzlVpxTzHJOy8nBXIwdnfUWQLuOGBx5gQOHoDPro/pub?w=955&h=878)

## State diagram
![](https://docs.google.com/drawings/d/1y88r8ekS2AH1VXI44CYqL3lbkHgwUZl5kNnLzkqsd8c/pub?w=960&h=720)

## Configurations
* The IR emitter E1 periodically generate modulated IR RC5(0x43) code.
* The IR receivers R0 & R1 are separated by a barrier.   

## Algorithm
* When we want the ANDBOT to go back to the docking station, firstly, we will use ROS navigation to command the ANDBOT to move to the landing point, which should be in 1.5 meter in front of the docking station. The ANDBOT is supposed to be backed the docking station.
 * Note: ROS navigation can cause around 0.2m position errors and 0.3rad orientation errors. 
* Then, ANDBOT should rotate in-place until R0 or R1 got the RC5(0x43) code:
* Then, ANDBOT should start to do orientation PID control to move toward the docking station.
 * If only R0 got RC5(0x43) code, the robot should rotate in CCW.
 * If only R1 got RC5(0x43) code, the robot should rotate in CW.
 * If both R0 and R1 got RC5(0x43) code, the robot should move forward.
 * If neither R0 nor R1 got RC5(0x43) code for a period of time, it should be treat as "lost docking station", and it should go back to the previous stop. 
* Until the sensor limitSW is contact to the docking station. Then stop the base.

## Regarding to the landing point
* emitter angle = 30 degree
* landing point is 1.5m in front of the docking station
* the width of the zone is about 1.5m * sin(15) * 2 = 0.775m, which is okay compared to the navigation errors.


# IMPLEMENTATIONS

* Design document
 * https://github.com/wennycooper/Auto-Docking-Design.git
* Receiver code on Arduino
 * https://github.com/wennycooper/IR_receiver_rosserial_ircode.git
* Receiver code on ROS
 * https://github.com/wennycooper/mybot_autodocking/blob/master/src/mybot_autodocking_irCode.cpp

# ISSUES
* n/a


