# Blink

![](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2F1c0786da15a6ea5af09f22d777797fdffbda14d9.gif?alt=media)

Let's first come to an easy beginner project - blink the onboard LED. 

This example shows the simplest thing you can do with just a SwiftIO board to see physical output: it blinks the onboard RGB LED.

## What you need

* SwiftIO board 

## Circuit

![](../../.gitbook/assets/image%20%2813%29.png)

For this project, you only need the SwiftIO board.

There is a built-in RGB LED on the board as shown in the image above. You can control it using the methods in `DigitalOut` class.

_**Note**: the onboard LED will be turned on when you apply a **low** voltage._

Just plug the board into your computer with a USB cable to download your code.

## Schematic

![](../../.gitbook/assets/image%20%285%29.png)

As the schematic shows, the LEDs are connected in parallel to 3.3V power. Each LED is connected to a resistor in series, so you don't need to worry about the current limit.

The current will always flow from high voltage to low voltage. So if you apply a low voltage to one LED, the current will flow through the LED, so that LED will be on; if it is high voltage instead, there is no voltage difference in the circuit and thus no current.

## Code

It's time for the code. Let's see how it works. You can find the example code at the bottom left corner of IDE: ![](../../.gitbook/assets/xnip2020-07-22_16-04-33.jpg) &gt; GettingStarted &gt; Blink.

```swift
// Turn on and off the onboard LED continuously.
// Import the library to enable the relevant classes and functions.
import SwiftIO

// Import the board library to use the Id of the specific board.
import SwiftIOBoard

// Initialize the onboard green LED with other parameters set to default.
let green = DigitalOut(Id.GREEN)

// Blink the LED over and over again.
while true {
    // Apply a high votage and turn off the LED.
    green.write(true)
    // Keep the light off for a minute.
    sleep(ms: 1000)
    // Apply a low voltage and turn on the LED.
    green.write(false)
    // Keep the light on for a minute.
    sleep(ms: 1000)
}
```

## Instruction

### What is the digital signal?

The digital signal normally has two states, its value is either 1 or 0. For the SwiftIO board, 1 represents 3.3V, and 0 represents 0V. There are also other ways to express the same meaning: high or low, true or false. In this case, you will control the output voltage to turn on or off the LED.

![](../../.gitbook/assets/digital.png)



### About code

`import SwiftIO` refers to this named library [SwiftIO](https://swiftioapi.madmachine.io/). This library includes the basic commands to control input and output. All case programs must first reference it so that you can use everything in it, like classes and functions. 

[SwiftIOBoard](https://github.com/madmachineio/MadBoards/blob/main/Sources/SwiftIOBoard/Id.swift) defined the id of the SwiftIO board. The pins of different boards are different. So this library tells the IDE you are dealing with the SwiftIO board, not any other boards. Then you could use the id in it.

`let` is a keyword for Swift language to declare constants. You will often use it to assign a name to each port for easy reference in the future. This statement is to create an instance for `DigitalOut` class and initialize the specified pin, so the pin would be able to output high or low voltage.

`Id` is an enumeration. All types of enumerated ids can be viewed in the library SwiftIOBoard. It includes all IO ports. 

_**Note**: You may be confused why RED, GREEN, and BLUE are not marked on pinMap. Because the SwiftIO board is equipped with a built-in RGB three-color LED by default. When you need to initialize one of them, just use its id  RED, GREEN, or BLUE._

Setting the `while` loop `true` means that the loop check will always run. It will not stop after entering, unless the hardware power off or restart. What will be executed over and over again is written in the loop, enclosed by a pair of curly braces `{}`. 

The  `.write()`  belongs to the `DigitalOut` instance and its incoming values ​​are `true` and `false`. They represent high-level output \(3.3V\) and low level \(0V or GND\) respectively. And for these three LED, you need `false` to turn on them.

The `sleep(ms:)` function is a built-in function, which means the delay time, calculated in milliseconds. The parameter name `ms` must be added to pass in the parameter.

## See Also

* [Id](https://swiftioapi.madmachine.io/Enums/Id.html) - enumerations of all pins on the board.
* [sleep\(ms:\)](https://swiftioapi.madmachine.io/Functions.html#/s:7SwiftIO5sleep2msySi_tF) - suspend the processor’s work in a given time period \(in milliseconds\).
* [DigitalOut.write\(\)](https://swiftioapi.madmachine.io/Classes/DigitalOut.html#/s:7SwiftIO10DigitalOutC5writeyySbF) - DigitalOut class is used to set a High or Low voltage output to a digital output pin.

## Reference

* [wiki: Digital signal](https://en.wikipedia.org/wiki/Digital_signal)
* [voltage, current and resistance](https://learn.sparkfun.com/tutorials/voltage-current-resistance-and-ohms-law?_ga=2.44615847.20613811.1609746258-596483498.1609383800)

