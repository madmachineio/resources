# ButtoncontrolLED

![](../../.gitbook/assets/ButtoncontrolLED/buttoncontrolLED.gif)

In this example, you will use a pushbutton to control the LED. 

The input signal will change as you press the button. Thus, you can set LED status according to different input states.

## What you need

- SwiftIO board
- button
- wires

## Circuit

![](../../.gitbook/assets/button.png)

There is an onboard RGB LED. Please apply **low** voltage to light it.

The button has four legs. The two legs on same side are interconnected. 

- Connect the leg on left side to 3.3 pin. 
- Connect the leg on right side to digital pin D0.

In default mode, the digital pin reads `false`. When you press the button, the two points on the button will be connected. And the value of pin will be `true`.

So please be sure you connected the button in a right way. 

## Code

You can find the example code at the bottom left corner of IDE: ![](../../.gitbook/assets/xnip2020-07-22_16-04-33.jpg) &gt; SimpleIO &gt; ButtoncontrolLED.

```swift
// Read the input signal controlled by a button to turn on and off the LED.

// Import the library to enable everything in it, like relevant classes and methods. 
// This is first step for your coding process.
import SwiftIO

// Declare a constant. You may choose any descriptive name you like. 
// Initialize the onboard red LED. 
// The Id of onboard LED should be capitalized.
let red = DigitalOut(Id.RED)

// Initialize a digital input pin D0 the button is connected to.
let button = DigitalIn(Id.D0)

// Allow the button to control the LED all the time.
while true {
    // Check the state of button. 
    // If it is pressed, the value will be true and then turn off the LED.
    // Modify the code according to your button if necessary.
    if button.read() {
        red.write(false)
    } else {
        red.write(true)
    }
}

```
## <span style="color:#EA5823;font-weight:700">Instruction</span>

`DigitalIn` class is intended to detect the state of a digital input pin. The input value is either true(1) or false(0).`.read()` Read the value from a digital input pin.

## <span style="color:#EA5823;font-weight:700">See Also</span>
- [PWMOut](https://swiftioapi.madmachine.io/Classes/PWMOut.html) - The PWMOut class is used to vary the output voltage

## <span style="color:#EA5823;font-weight:700">References</span>

- [Pulse-width modulation](https://en.wikipedia.org/wiki/Pulse-width_modulation)

---
Last revision 2020/09/12 by Johnson


