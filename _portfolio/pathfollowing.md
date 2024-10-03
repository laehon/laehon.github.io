---
title: "Pathfollowing Robot"
author_profile: true
key: 2
excerpt: "C, Python, I2C, PWM, UART"
classes: wide
header:
  teaser: /assets/images/path-robot.png
---

The goal of this project was to create a differential dive robot from scratch to follow a line. This was implemented using a PiCamera to take a picture of the line, a Raspberry Pi Zero for image processing in Python, and a Raspberry Pi Pico for controlling the differential drive.

Source code: [GitHub](https://github.com/laehon/me433/tree/main/hw17)

## Robot
![Robot Image]({{ site.url }}{{ site.baseurl }}/assets/images/path-robot.png)

## System Overview
![Block Diagram]({{ site.url }}{{ site.baseurl }}/assets/images/path-diagram.png)

The first step in the path following robot process is for the Raspberry Pi Zero to send a signal to the PiCamera to take a picture. When the picture is taken, the Pi Zero then uses a derivative brightness method to detect the edges of the path. The Pi Zero then takes this data and converts it to a number from 1-100 to send to the Raspberry Pi Pico over UART (50 being the line is in the middle, < 50 being to the left, and > 50 being to the right). The Pi Pico then takes the line position and runs a differential drive program to control the motor wheels using the H-bridge motor driver.


## Robot CAD
![CAD Image]({{ site.url }}{{ site.baseurl }}/assets/images/path-cad.png)

[CAD Files](https://cad.onshape.com/documents/bebdd82f9fd5bc179522273e/w/8f20ae77808cc4db014a51f7/e/67e4745bc3ac82c99155d9d5)

The PCBs for the main electronics and the motor were used as part of the robot shell. The PCB connectors and wheels were 3D printed with the CAD files above.

## Image Processing
![Image Processing]({{ site.url }}{{ site.baseurl }}/assets/images/path-line.png)

Here is a picture taken by the PiCamera after the image processing was applied to it. The Pi Zero calculates the change in brightness across every row of pictures to find the 2 biggest changes of brightness values, which are then set as the edges of the line (marked in green). Then by averaging these values, it gets the center of the line (marked in red).