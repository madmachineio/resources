# BlinkTimer

![](../../.gitbook/assets/BlinkTimer01.gif)

This example shows how to use the timer and interrupt mechanism on the SwiftIO Board to make the onboard red LED blink at a constant frequency.

## What you need

* SwiftIO board

### Kits that meet the experimental conditions:

* [Maker Kit for SwiftIO](https://www.madmachine.io/product-page/maker-kit-for-swiftio)

## Circuit

![](../../.gitbook/assets/01%20%281%29.png)

Only the SwiftIO Board itself is required here. 

## Code

```swift
// Change the LED state every second by setting the interrupt.
// Import the library to enable the relevant classes and functions.
import SwiftIO

// Import the board library to use the Id of the specific board.
import SwiftIOBoard

// Initialize the red onboard LED and a timer to set interrupt.
let red = DigitalOut(Id.RED)
let timer = Timer()

// Raise the interrupt to turn on or off the LED every second.
timer.setInterrupt(ms: 1000) {
    red.toggle()
}


while true {

}
```

## Instruction

### What is an interrupt?

An interrupt ensures that the processor responds quickly to some important events. When an interrupt signal is detected, the processor will stop its current job and perform some other codes, so that the board can react to the external signals quickly and accordingly.

The function you choose for interrupt should be able to execute extremely quickly. Usually, we tend to change the state or number of some values. 

###  What is a timer?

The timer is precisely a part of the hardware on the SwiftIO board. It works just like an alarm clock. You set the time interval for the interrupt. If the time is up, the microcontroller will execute the program set for the interrupt. 

### What happens in this example?

In this case, the timer is set to be the internal interrupt source, which is done by using `.setInterrupt(ms: )`, a method in the `Timer()` class. The parameter indicates that the timer triggers an interrupt every 1000 ms or every 1 s.

The `.toggle()` method of DigitalOut class means that the output level of the specific pin will be inverted. In this case, the red LED light will be switch on or off when the interruption happens.

You can also use the `sleep(ms: )` function to achieve the same effect as the [Blink](../getstarted/blink.md). But this function will make the processor unresponsive during this period of time, making it do nothing. Therefore, the advantage of using `interrupt` is that the processor can still do other things in between.

## See Also

* [Timer.setInterrupt\(\)](https://swiftioapi.madmachine.io/Classes/Timer.html#/s:7SwiftIO5TimerC12setInterrupt2ms4mode5start_ySi_AC4ModeOSbyyctF) - The Timer class is used to set the occasion to raise the interrupt.
* [toggle\(\)](https://swiftioapi.madmachine.io/Classes/DigitalOut.html#/s:7SwiftIO10DigitalOutC6toggleyyF) - To alternate between two voltage level.

