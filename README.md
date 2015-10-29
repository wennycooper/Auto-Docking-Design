# Auto-Docking-Design

# INTRODUCTION
* This is a design draft for the Robot auto ducking.


# COMPONENTS
* On docking station
 * IR emitter 
* On Robot
 * Two IR receivers 

# BASIC OPERATIONS
* We will use ROS navigation to command Robot to be 1 or 2 meter in front or the docking station. The Robot's back will be facing to the docking station.
 * ROS navigation can cause around 30cm position errors
* Then, two IR receivers will receive IR signals.
* The Robot will start to to PID control to keep the two IR receiver reading balanced.
* Until the PMU got the charging flag.

# ISSUES
* We didn't found proper IR emitter and IR receivers. Keep looking at it. 


