# LEDsBrightnessControl



![](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2F3459b4d241632d2833cb8c647b87a4063a989e13.gif?alt=media)

This example demonstrates the use of Pulse Width Modulation \(PWM\) to fade three LEDs. PWM is a technique for getting an analog-like behavior from a digital output by switching it off and on very fast and with different ratio between on and off time.

## What you need <a id="what-you-need"></a>

* SwiftIO board
* Jumper wires
* 3color LEDs and 330k ohm resistors or 3 color LED Modules
* SwiftIO shield \(optional\)

## Circuit <a id="circuit"></a>

![](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2Fc09689f5d490512a854e0502bea444d5968bcc18.png?alt=media)

## Code <a id="code"></a>

```swift
// Change the LED state every second by setting the interrupt.

// Import the library to enable the relevant classes and functions.
import SwiftIO

// Initialize the pins the LEDs are connected to and put them in a array.
let red = PWMOut(Id.PWM2B)      //P10 D10
let green = PWMOut(Id.PWM3B)    //P12 D12
let blue = PWMOut(Id.PWM4A)     //P20 D20 A6
let leds = [red, green, blue]   //Arrays, one of Collection Types

// Declare a variable to store the value of duty cycle.
var value: Float = 0.0

// Change the brightness of each LED over and over again.
while true {
    for led in leds {
        // Brighten the LED in two seconds.
        while value <= 1.0 {
            led.setDutycycle(value)
            sleep(ms: 20)
            value += 0.01
        }
        // Keep the value of duty cycle between 0.0 and 1.0.
        value = 1.0
        // Dimming the LED in two seconds.
        while value >= 0 {
            print(value)
            led.setDutycycle(value)
            sleep(ms: 20)
            value -= 0.01
        }
        // Keep the value of duty cycle between 0.0 and 1.0.
        value = 0.0
    }
}
```

## Instruction <a id="instruction"></a>

`let leds = [red, green, blue]`Swift provides three primary collection types, known as arrays, arrays are ordered collections of values. You access and modify an array through its methods and properties, or by using subscript syntax, such as `leds.red`, `leds.green`, `leds.blue`. 

`var value: Float = 0.0` explicitly declares that the type of value is a floating-point number type, not an integer type. Explicitly declaring the type is very important for scenarios where the type is easy to be confused. The subsequent use shows that the variable must be a floating-point real number . 

You can iterate over the entire set of values in an array with the for-in loop: `for led in leds`. This is the reason why we want to create the array `leds`. With the for-in loop syntax structure, it becomes very convenient and concise when traversing and iterating.

## See Also <a id="see-also"></a>

* ​[Numeric Type Conversion](https://royals6234.gitbook.io/madmachine-examples/examples/simpleio/ledsbrightnesscontrol) - An integer type can be initialized with a Double or Float value.
* ​[for-in loops](https://docs.swift.org/swift-book/LanguageGuide/ControlFlow.html) - You use the for-in loop to iterate over a sequence, such as items in an array, ranges of numbers, or characters in a string.

## References <a id="references"></a>

* ​[Collection Types](https://docs.swift.org/swift-book/LanguageGuide/CollectionTypes.html)​
* [wiki: ​Pulse-width modulation​](https://en.wikipedia.org/wiki/Pulse-width_modulation)
* [wiki: ​Duty cycle](https://en.wikipedia.org/wiki/Duty_cycle)

