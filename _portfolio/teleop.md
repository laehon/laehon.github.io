---
title: "Teleoperated Robot using Jetson Nano"
author_profile: true
key: 6
excerpt: "Python, I2C, PWM, Circuit Design"
classes: wide
header:
  teaser: /assets/gifs/botrista.gif
---

This project focused on building a teleoperated robot from scratch, including the design of all circuitry for power distribution and control. A Jetson Nano is used to process all controller movements and control the robot wheels and arm through motor drivers and servo controllers

Source code: [GitHub]

## Video Demo

## Hardware
The following hardware was used in the project:
* Jetson Nano: Serves as the CPU of the robot
* 14.8V Lipo Battery: Power the robot
* XL4015 DC-DC Step Down: Convert 14.8V to 5V for logic and 9V for motors
* L298N: Motor drive controller for wheels
* PCA9685: Servo driver controller for robot arm

## System Overview
