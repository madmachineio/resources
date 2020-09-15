# Debounce



![](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2F618651fbd064bcefa30a543505d0d1b633bd6229.gif?alt=media)

When we use Pushbutton as toggle switch, it often generates spurious open/close transitions when pressed, due to mechanical and physical issues. This example demonstrates how to debounce an input, which means checking twice in a short period of time to make sure the pushbutton is definitely pressed.

## What you need <a id="what-you-need"></a>

* SwiftIO board
* button
* wires

## Circuit <a id="circuit"></a>

![](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2Fa9ed2bb74e7e4359b9cfda05e22088f241b1690a.png?alt=media)

## Code <a id="code"></a>

```swift
// Check if the button is definitely pressed.

// Import the library to enable the relevant classes and functions.
import SwiftIO

// Initialize the red onboard LED.
let red = DigitalOut(Id.RED)

// Initialize a digital input pin D0 the button is connected to.
let button = DigitalIn(Id.D10, mode: .pullUp)

// Declare the values in order to record and judge the button state.
var count = 0
var triggered = false


while true {
    // Read from the input pin.
    let value = button.read()

    // Ignore the change due to the noise.
    if value == false {
        count += 1
    } else {
        count = 0
        triggered = false
    }

    // Wait a certain period to check if the button is definitely pressed. 
    // Toggle the LED and then reset the value for next press.
    if count > 50 && !triggered {
        red.toggle()
        triggered = true
        count = 0
    }

    // Wait a millisecond and then read to ensure the current state last for enough time. 
    sleep(ms: 1)

}
```

## Instruction <a id="instruction"></a>

Swift has a basic Boolean type, called Bool. Boolean values are referred to as logical, because they can only ever be true or false. Swift provides two Boolean constant values, true and false. `var triggered` is define as Bool to store the digital input change.

The `DigitalOut` class has `Mode` enumeration which includes the available output modes. The default output mode in most cases is `pushPull`. The `pushPull` mode enables the digital pin to output high and low voltage levels while the open-drain output cannot truly output a high level.

Due to mechanical and physical issues, pushbuttons often generate spurious open/close transitions when pressed, these transitions may be read as multiple presses in a very short time fooling the program. This example demonstrates how to debounce an input, which means checking twice in a short period of time to make sure the pushbutton is definitely pressed. Without debouncing, pressing the button once may cause unpredictable results. This code uses the `sleep(ms: 1)` 50 times to keep track of the time passed since the button was pressed.

## See Also <a id="see-also"></a>

* ​[DigitalOut](https://swiftioapi.madmachine.io/Classes/DigitalOut.html) - The DigitalOut class is used to set a High or Low voltage output to a digital output pin.
* ​[DigitalOut Mode](https://swiftioapi.madmachine.io/Classes/DigitalOut/Mode.html) - The Mode enumerate includes the available output modes.

## References <a id="references"></a>

* ​[Boolean type](https://docs.swift.org/swift-book/LanguageGuide/TheBasics.html)​
* [wiki: ​Push–pull output](https://en.wikipedia.org/wiki/Push%E2%80%93pull_output)

