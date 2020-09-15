# Blink

![](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2F1c0786da15a6ea5af09f22d777797fdffbda14d9.gif?alt=media)

Let's first come to an easy beginner project - blink the onboard LED. This example shows the simplest thing you can do with just a SwiftIO board to see physical output: it blinks the on-board REG LED.

## What you need

• SwiftIO board 

## Circuit

![Image developed using Fritzing. For more circuit examples, see the Fritzing project page](../../.gitbook/assets/untitled-sketch_bb.png)

For this project, you only need the SwiftIO board.

There is a built-in RGB LED on the board. You can control it using the methods in `DigitalOut` class.

_**Note**: the onboard LED will be turned on when you apply a **low** voltage._

Just plug the board to your computer through a USB cable after you finished code.

## Schematic

![](../../.gitbook/assets/image%20%285%29.png)

## Code

It's time for the code. Let's see how it works. You can find the example code at the bottom left corner of IDE: ![](../../.gitbook/assets/xnip2020-07-22_16-04-33.jpg) &gt; GettingStarted &gt; Blink.

```swift
// Import the library to enable everything in it, like relevant classes and methods. 
// This is first step for your coding process.
import SwiftIO

// Declare a constant. You may choose any descriptive name you like. 
// Initialize the onboard green LED. 
// The Id of onboard LED should be capitalized.
let green = DigitalOut(Id.GREEN) 

// In the dead loop, the code will run over and over again.
while true {
    // Output 3.3V to turn off the green LED.
    green.write(true)
    // Pause for a second. Or, you won't notice LED state change. 
    // During this period, the board will do nothing but just wait.
    sleep(ms: 1000)
    
    // Output 0V to turn on the green LED.
    green.write(false)
    sleep(ms: 1000)
}
```

## Instruction

### What is digital signal?

Digital signal has only two state, its value is either 1 or 0. For SwiftIO board, 1 represents 3.3V and 0 represents 0V. Thus, we can control the output voltage to turn on or off the LED.

### About code

`import SwiftIO` refers to this named library. In this tutorial, all case programs must first reference this library so that we can use everything in it, like classes and functions. 

`let` is a keyword for Swift language to declare constants. We will often use it to assign names to each port for easy reference in the future. 

`Id` is an enumeration. All types of enumerated Id can be viewed [here](https://swiftioapi.madmachine.io/Enums/Id.html). Its members include all IO ports. You may be confused why RED, GREEN, and BLUE are not marked on pinMap. Because the SwiftIO board is equipped with built-in RGB three-color LEDs by default and connected in series with resistors, the corresponding pins of the LEDs connected to the three ports are shown in the circuit diagram. 

Setting the `while` loop to `true` means that the loop check will always be true, unless the hardware is powered off or restarted, the loop will not stop after entering. The loop body is the part of the loop code, enclosed by a pair of braces `{}` and needs to be indented for reading. 

The `.write()` method belongs to the `DigitalOut` object and its incoming values ​​are `true` and `false`, which represent output high level \(3.3V\) and low level \(0V or GND\) respectively. And for these three LED, we need `false` to turn on them.

The `sleep(ms:)` function is a built-in function, which means the delay time, calculated in milliseconds. The external name of the parameter `ms` must be added to pass in the parameter.

## See Also

* [Id](https://swiftioapi.madmachine.io/Enums/Id.html) - Enumerations of all pins on the board.
* [sleep\(ms:\)](https://swiftioapi.madmachine.io/Functions.html#/s:7SwiftIO5sleep2msySi_tF) - suspend the processor’s work in a given time period \(in millisecond\).
* [DigitalOut.write\(\)](https://swiftioapi.madmachine.io/Classes/DigitalOut.html#/s:7SwiftIO10DigitalOutC5writeyySbF) - DigitalOut class is used to set a High or Low voltage output to a digital output pin

## Reference

* [wiki: digital signal](https://en.wikipedia.org/wiki/Digital_signal)

