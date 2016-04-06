# Auto-Docking-Design

# Demo video
* https://www.youtube.com/watch?v=8TJdYG-1yr4

# INTRODUCTION
* This is the auto docking design draft for the ANDBOT.
* The same design could be used in Rogby, Angel and Roadbot.


# COMPONENTS
* On docking station
 * Three IR emitters 
* On ANDBOT
 * Two IR receivers for Z1
 * Two IR receivers for Z2 and Z3.(這兩顆IR receivers 需要安裝地比較深入, 指向能力才會比較高)
 * microSW

# BASIC OPERATIONS
## Architecture
![](https://docs.google.com/drawings/d/10qjkzlVpxTzHJOy8nBXIwdnfUWQLuOGBx5gQOHoDPro/pub?w=955&h=878)

## State diagram
![](https://docs.google.com/drawings/d/1y88r8ekS2AH1VXI44CYqL3lbkHgwUZl5kNnLzkqsd8c/pub?w=960&h=720)

* We will use ROS navigation to command the ANDBOT to move to the landing point, which should be in 0.7 meter in front of the docking station. The ANDBOT's back is supposed to be faced to the docking station.
 * ROS navigation can cause around 0.2m position errors and 0.3rad orientation errors. 
* Then, ANDBOT should rotate in-place until any of following conditions:
 * The R0 or R1 got signals which is greater than the pre-defined threshold. It means the robot is in the zone Z1.
 * The R2 got signals from E2, which means it is in the zone Z2.
  * Then, the ANDBOT should move ahead until it lost the E2 signal
  * Then, it should rotate in-place until the R0 or R1 got signals which is greater than the pre-defined threshold. 
  * Now it should be in the zone Z1.
 * The R3 got signals from E3, which means it is in the zone Z3.
  * Then, the ANDBOT should move ahead until it lost the E3 signal 
  * Then, it should rotate in-place until the R0 or R1 got signals which is greater than the pre-defined threshold. 
  * Now it should be in the zone Z1. 
* Then, ANDBOT should start to do orientation PID control to move toward the docking station and keep the R0 & R1 readings balanced.
* Until the microSW on.



# ISSUES
* n/a


