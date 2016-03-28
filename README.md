# Auto-Docking-Design

# INTRODUCTION
* This is the auto docking design draft for the ANDBOT.
* The same design could be used in Rogby, Angel and Roadbot.


# COMPONENTS
* On docking station
 * IR emitter 
* On ANDBOT
 * Two IR receivers 
 * microSW

# BASIC OPERATIONS
![](https://docs.google.com/drawings/d/10qjkzlVpxTzHJOy8nBXIwdnfUWQLuOGBx5gQOHoDPro/pub?w=955&h=878)

![](https://docs.google.com/drawings/d/1y88r8ekS2AH1VXI44CYqL3lbkHgwUZl5kNnLzkqsd8c/pub?w=960&h=720)

* We will use ROS navigation to command Robot to move to the landing point, which should be in 0.7 meter in front of the docking station. The ANDBOT's back will be facing to the docking station.
 * ROS navigation can cause around 20cm position errors
* Then, ANDBOT should rotate in-place until the IR receiver got signals which is greater then the pre-defined threshold.
* Then, ANDBOT will start to do PID control to move to the docking station and keep the two IR receiver reading balanced.
* Until the microSW on.

# ISSUES
* We didn't found proper IR emitter and IR receivers. Keep looking at it. 


