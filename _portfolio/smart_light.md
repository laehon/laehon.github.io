---
title: "Smart Night Light"
author_profile: true
key: 3
excerpt: "C, I2C, PWM, ADC, Timers, Audio"
classes: wide
header:
  teaser: /assets/images/smart-light.png
---

The goal of this project was to sustainable Smart Night Light using the Microbit V2. The light would turn off when there is no movement in the area and adjust its brightness based of the surrounding ambient light. It also has a party mode functionality where the light can sync up with the beat of music. 

Source code: [GitHub](https://github.com/laehon/Smart-Night-Light/tree/main)

## Video Demo
<iframe width="560" height="315" src="https://www.youtube.com/embed/A8SHZGoGKgQ?si=IsGszfH-rKeTw94K" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## System Hardware
* Microbit V2
* Sparkfun VEML6030 Ambient Light Sensor
* Sparkfun STHS34PF80 Human Presence and Motion Sensor
* SparkFun Electret Microphone
* High Power RGB LED

## System Workflow
In the Normal Night Light Mode, the system remains in a low-power sleep state, continuously monitoring the human presence sensor for any motion. Upon detecting movement, it awakens and initializes a timer to determine the duration the light should remain active. The Microbit then assesses the ambient light levels using its built-in sensor, adjusting the RGB LED brightness accordingly through Pulse Width Modulation (PWM) and transistors. In brighter environments, the LED dims to conserve energy, while in darker settings, it shines more brightly to provide adequate illumination. This adaptive behavior ensures that during daylight hours or when sufficient external light is present, the night light remains off, promoting energy efficiency. As long as the system continues to detect motion, the timer resets, keeping the light on. Once the timer expires without further motion detection, the light turns off, and the system reverts to its low-power sleep state, awaiting the next activation.

In Party Mode, the system offers a dynamic lighting experience by continuously cycling through various colors. The built-in microphone captures audio input via Analog-to-Digital Conversion (ADC), storing these samples in a buffer. Initially, the system calculates a baseline loudness level by averaging the initial set of sound samples. As new audio data is collected, this baseline is dynamically updated to reflect the current ambient sound environment. When the incoming sound level exceeds a predefined threshold relative to the baseline, the RGB LED flashes in sync with the detected beats, creating a visual accompaniment to the music. This mode ensures that the light display remains responsive to the rhythm of the surrounding audio, providing an engaging and synchronized lighting effect.