---
title: "PID Motor Control"
author_profile: true
key: 3
excerpt: "C, Python, I2C, PWM, UART"
classes: wide
header:
  teaser: /assets/images/PID-graph.png
---

This project implemented a PID Loop on a PIC32 microcontroller to control a motor speed and position. The system was used achieve accurate trajectory tracking of any user inputed trajectory.

Source code: [GitHub](https://github.com/laehon/PID-Motor-Control)

## Video Demo
<iframe width="560" height="315" src="https://www.youtube.com/embed/GBV9OVCr9AA?si=gfWJpxpqskLao0uU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


## System Overview
![Block Diagram]({{ site.url }}{{ site.baseurl }}/assets/images/PID-diagram.png)

The user can first input a trajectory which is first stored as data for the motion controller. The motion controller uses the data to compute current commands for the current controller, which sends a corresponding PWM signal to the H-Bridge to control the motor. Both the current controller and motion controller work of a PID Loop, the current controller uses the current sensor to measure the actual current going to the motor and the motion controller uses an encoder to measure the position of the motor.


## Hardware Schematic
![Scehmatic Diagram]({{ site.url }}{{ site.baseurl }}/assets/images/PID-schematic.png)

The hardware schematic provides a detailed view of the physical connections used in the system. The PIC32 microcontroller is programmed in C as both the motion controller and current controller for the trajectory tracking system. The Raspberry Pi Pico is used soley for tracking the encoder position of the motor and sending the data to the PIC32 microcontroller. The INA219 is the current sensor used for the current controller which sends its data to the PIC32 over I2C. The H-Bridge is used to drive the motor using a PWM and GPIO pin.

## Results
![Results Graph]({{ site.url }}{{ site.baseurl }}/assets/images/PID-graph.png)

The graph compares the motor's actual position (red) with the desired trajectory (blue) over time, with the x-axis representing time (index) and the y-axis showing the motor's angle. The score at the top of the graph quantifies the tracking error, indicating that the system maintained good accuracy throughout the process.