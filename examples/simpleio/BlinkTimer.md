# <span style="color:#EA5823;font-weight:800">BlinkTimer</span>


## <span style="color:#EA5823;font-weight:700">What you need</span>

- SwiftIO board

#### Kits that meet the experimental conditions: 
- [Maker Kit for SwiftIO](https://www.madmachine.io/product-page/maker-kit-for-swiftio)

## <span style="color:#EA5823;font-weight:700">Circuit</span>
![](../../.gitbook/assets/BlinkTimer/01.png)

## <span style="color:#EA5823;font-weight:700">Tips</span>


What is a timer?
A timer or to be more precise a timer / counter is a piece of hardware builtin the SwiftIO Board  (other controllers have timer hardware, too). It is like a clock, and can be used to measure time events.
The timer can be programmed by some special registers. You can configure the prescaler for the timer, or the mode of operation and many other things.

What is a Interrupt?
An Interrupt's job is to make sure that the processor responds quickly to important events. When a certain signal is detected, an Interrupt (as the name suggests) interrupts whatever the processor is doing, and executes some code designed to react to whatever external stimulus is being fed to the SwiftIO Board.


## <span style="color:#EA5823;font-weight:700">Code</span>






```swift
/// Change the LED state every second by setting the interrupt.

/// Import the library to enable the relevant classes and functions.
import SwiftIO

/// Initialize the red onboard LED and a timer to set interrupt.
let red = DigitalOut(Id.RED)
let timer = Timer()

/// Raise the interrupt to turn on or off the LED every second.
timer.setInterrupt(ms: 1000) {
    red.toggle()
}

while true {

}
```


## <span style="color:#EA5823;font-weight:700">Video</span>
![](../../.gitbook/assets/BlinkTimer01.gif)

## <span style="color:#EA5823;font-weight:700">See Also</span>
- [Timer()](https://swiftioapi.madmachine.io/Classes/Timer.html) - The Timer class is used to set the occasion to raise the interrupt.
- [toggle()](https://swiftioapi.madmachine.io/Classes/DigitalOut.html#/s:7SwiftIO10DigitalOutC6toggleyyF) - To alternate between two voltagle level.

## <span style="color:#EA5823;font-weight:700">References</span>

- [Timer](https://en.wikipedia.org/wiki/Timer)
- [Interrupt](https://en.wikipedia.org/wiki/Interrupt)
- [toggle](https://en.wiktionary.org/wiki/toggle)


---
Last revision 2020/09/04 by Johnson