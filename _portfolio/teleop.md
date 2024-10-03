---
title: "Teleoperated Robot using Jetson Nano"
author_profile: true
key: 1
excerpt: "Python, I2C, PWM, Circuit Design"
classes: wide
header:
  teaser: /assets/gifs/Teleop_Robot.gif
---

This project focused on building a teleoperated robot from scratch, including the design of all circuitry for power distribution and control. A Jetson Nano is used to process all controller movements and control the robot wheels and arm through motor drivers and servo controllers.

Source code: [GitHub](https://github.com/laehon/Teleop-Robot)

## Video Demo
<iframe width="560" height="315" src="https://www.youtube.com/embed/25syFlk5F58?si=U_lDTquaZgg-EnwP" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Hardware
The following hardware was used in the project:
* Jetson Nano: Serves as the CPU of the robot
* 14.8V Lipo Battery: Power the robot
* XL4015 DC-DC Step Down: Convert 14.8V to 5V for logic and 9V for motors
* L298N: Motor drive controller for wheels
* PCA9685: Servo driver controller for robot arm

## System Overview
![Block Diagram]({{ site.url }}{{ site.baseurl }}/assets/images/teleop-diagram.png)

The projects uses the pygame python library on the Jetson Nano to read user inputs on an Xbox controller, then moves the robot according to the controller inputs. Power is supplied by a 14.8V LiPo battery, stepped down to 5V and 9V through two XL0415 regulators. The Jetson Nano uses I2C to communicate with the PCA9685 module to control the servos on robot arm. The robot arm is the [EEZYbotARM MK2](http://www.eezyrobots.it/eba_mk2.html), except with the MG946 servos replaces with MS61 servos for more power. The Nano also sends PWM signals to the L298n motor drivers which drive the mecanum wheel motors. Since the Jetson Nano only has 2 PWM pins broken out, software PWM was used instead. 
