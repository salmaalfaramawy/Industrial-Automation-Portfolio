# Industrial-Automation-Portfolio
A collection of RSLogix 500 ladder logic projects and HMI/SCADA interfaces (Ignition and Wonderware) for manufacturing and process control.
These projects were created as part of the PLC Dojo PLC courses (Part 2 and 3).

**Note:** Each file contains PDF reports for the code for those who do not have RSLogix 500 installed. 

____

## Table of Contents

\+ [Project Descriptions](#projects-and-details)

___

## Projects Details

**Automated Water Storage & Filtration Control System:**

This PLC program controls a water filtration and storage system with automated backwash to clear the filter. 
A pump draws water from a water source. The pump is active while the water level in the tank is below the "High Water Level" setpoint. It deactivates when it reaches this setpoint, and the discharge valve is energized to let the water flow out of the tank to where it is to be supplied. The pump activates again when the water level has reached the "Low Water Level" setpoint. 
Six valves control the direction that the water flows in. For normal flow, valves SV1, SV3, and SV5 are open, allowing water to flow to the tank to fill it. When it is time for a backwash cycle, valves SV2, SV4, and SV6 are open, which directs the flow backward, which dislodges the impurities present in the filter.
The backwash  cycle is automatically triggered once the differential pressure in the filter reaches the setpoint specified. 
An hour meter records system runtime and the number of backwash cycles is also recorded. These two can be reset using the Backwash Count and Runtime reset buttons. 
All of the valves and the pump have HOA (hand-off-auto) controls. 
There are High-High and Low-Low Tank Level alarms and notifications, as well as a High Filter Pressure and a Low Flow alarm and notification. All of these will be triggered on reaching the setpoints specified for them. The alarms and notifications are reset with the "Alarm Reset" button, and the notifications are silenced with the "Alarm Silence" button. 

[Ladder Logic](https://github.com/salmaalfaramawy/Industrial-Automation-Portfolio/tree/main/Automated%20Water%20Storage%20%26%20Filtration%20Control%20System/Logic) 

### Pump Control System with HOA Modes and Fault Protection:

This program controls a pump. The pump has 3 modes: hand, off, and auto.
When the hand button is pushed, the pump enters hand mode and runs, but stops running when the button is released.
When the auto button is pushed, the pump enters auto-mode and runs for 30 seconds, then stops for 10 seconds. The pump keeps cycling this way when the it is in auto-mode. 
The pump is off when in off mode. 
If no flow is detected, the flow switch does not close. If the flow switch does not close within 5 seconds, the flow alarm and notification turn on, and the flow fault indicator is switched on.
If the pressure exceeds 30 psi for 5 seconds, the pressure alarm and notification turn on, and the pressure fault indicator is switched on.

### Servo Control for Automated Valve Sequencing:

This program was written to control a servo.
When the cycle call bit activates, the servo cycles a control valve from the home switch to the fill switch (where it will stay for 10 seconds), then to the drain switch (where it will stay for 20 seconds), then to the flush switch (where it will stay for 10 seconds), then back to the home switch. 
The servo de-energizes when the home switch is reached, but energizes again when the cycle call bit activates.
A cycle terminates when the flush cycle ends or when the reset button is hit. When the cycle terminates, the servo remains energized and moves till it reaches the home position, where it deactivates again. 


### PLC Automated Sensor Calibration:

This program was written to record inputs recorded by an Oxygen (O2) sensor.
When the calibration button is pressed, a calibration cycle begins where a gas valve with 0% oxygen opens for 30 seconds. The readings taken by the
sensor over the 30s period are averaged, and this becomes the input minimum value in the scaling command (SCP on rung 0000).
When the 0% valve closes, the 30% valve opens for 30 seconds, and the same process is repeated. The average value calculated from this part of the
cycle is then used in calculations which set the input maximum value in the SCP block.
When the 30% valve is closed, the calibration cycle ends.



### Color Detection and Automated Box Filling Convetor System:

This program controls a conveyor belt with boxes that have colored (red or blue) labels on them.
A red and blue photo eye detect the colors of the labels on the box (red photo eye detects red, blue photo eye detects blue). 
When the red photo eye detects a red label, the walnut hopper energizes, filling the box with walnuts. 
When the blue photo eye detects a blue label, the pecan hopper energizes, filling the box with pecans. 
The conveyor belt is de-energized (stops moving) while the boxes are filling up.
A level switch detects whether the box is full. When it detects a full box, the conveyor belt starts moving again. 


