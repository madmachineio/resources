# <span style="color:#EA5823;font-weight:800">Debounce</span>

![](../../.gitbook/assets/Debounce/Debounce.gif)

## <span style="color:#EA5823;font-weight:700">What you need</span>

- SwiftIO board
- button
- wires

## <span style="color:#EA5823;font-weight:700">Circuit</span>

![](../../.gitbook/assets/Debounce/../ButtoncontrolLED/ButtoncontrolLED_bb.png)

## <span style="color:#EA5823;font-weight:700">Code</span>


```swift
/// Check if the button is definitely pressed.

/// Import the library to enable the relevant classes and functions.
import SwiftIO

/// Initialize the red onboard LED.
let red = DigitalOut(Id.RED)

/// Initialize a digital input pin D0 the button is connected to.
let button = DigitalIn(Id.D10, mode: .pullUp)

/// Declare the values in order to record and judge the button state.
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

## <span style="color:#EA5823;font-weight:700">Instruction</span>


## <span style="color:#EA5823;font-weight:700">See Also</span>


## <span style="color:#EA5823;font-weight:700">References</span>


## <span style="color:#EA5823;font-weight:700">Tips</span>


---
Last revision 2020/09/10 by Johnson