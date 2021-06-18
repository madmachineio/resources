# What is SwiftIO board

SwiftIO board is our first typical board that runs swift source code on microcontrollers. Before knowing more about it, let's get some info about the Swift language and microcontroller.

![](https://static.wixstatic.com/media/ccab1c_247c008846064e94ba0c4a5e63845e39~mv2_d_2336_1558_s_2.png/v1/fit/w_300,h_300,al_c,q_5/file.png)

#### About Swift language

Swift is a powerful, efficient and safe programming language. It is now widely used for app development. But now we can do more with it.

It absorbs many other languages’ features without affecting the real-time performance of the embedded system. It is one of the few modern languages suitable for industrial microcontroller programming.

#### About microcontroller

You could always find it in your daily life even if you don't know it. It is often embedded in different devices, like home appliances. 

A microcontroller \(or MCU\) is an integrated circuit device that can be programmed to execute specific tasks or control other electronic devices. It usually contains a processor, memory, and all kinds of peripherals with different functions \(like GPIO, ADC, Timer, I2C, etc\). 

**As for SwiftIO board**

SwiftIO board is the combination of these two. You may have heard of Arduino or MicrPython:

![A comparison between Arduino, MicroPython, and MadMachine.](https://static.wixstatic.com/media/ccab1c_b9bb5de391434dadb287c5a18cb83223~mv2.jpg/v1/fill/w_740,h_313,al_c,q_90,usm_0.66_1.00_0.01/ccab1c_b9bb5de391434dadb287c5a18cb83223~mv2.webp)

SwiftIO board has huge potential to make microcontroller projects easier than ever before. You can use it to control motors, lighting, or build a simple robot like many other microcontrollers. What's more, it could work well on some complicated projects and is really suitable for GUI programming, thanks to the modern features of the language and the great performance of the microcontroller. 

This is the pinout diagram of SwiftIO. Let’s take a quick tour. 

![](../.gitbook/assets/pinout-diagram-of-swiftio%20%281%29.png)

{% file src="../.gitbook/assets/pinout-diagram-of-swiftio.png" caption="Download the diagram" %}

* Microcontroller RT1052 with ARM cortex M7 core 600 Mega Hz.
* **Reset button**: reboot your SwiftIO’s program.
* **Download button**: download your code.
* **Power-related pins**: power and ground pins.
* **Communication interfaces**: including I2C, SPI, UART, CAN. They allow the board to send and receive data in order to communicate with different devices.
* **46 digital pins**: output 3.3V for a digital 1, and 0V for a digital 0.
* **12 analog input pins**: measure continuous voltages anywhere from 0V to 3.3V.
* **14 PWM pins**: output pulse width modulated square waves to simulate an average voltage between 0V and 3.3V. They could normally be applied in motor controlling, buzzer, or brightness control.

SwiftIO board puts all those things together in an easy-to-use way. Welcome to explore more interesting stuff with us.

