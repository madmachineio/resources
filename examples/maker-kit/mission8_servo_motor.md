# Mission8\_Servo\_Motor \(editing\)

## What you need

![](../../.gitbook/assets/asset-37.png)

## Circuit

### Circuit diagram

![](../../.gitbook/assets/servo.png)

### Build your circuit





## Example code

You could open the code in the ![](../../.gitbook/assets/xnip2020-07-22_16-04-33.jpg) &gt; MakerKit &gt; Mission8\_Servo\_Motor.

```swift
// Import the SwiftIO library to use everything in it.
import SwiftIO

// Import the board library to use the Id of the specific board.
import SwiftIOBoard

let a0 = AnalogIn(Id.A0) // Initialize the analog pin.
// Each cycle of the signal lasts for 20 milliseconds.
// The pulse should last between 0.5 and 2.5 milliseconds to activate the servo.
// With a 0.5ms pulse, the servo will turn to 0 degrees and with a 2.5ms pulse, it will at 180 degrees.
// In between, it is at an angle between 0–180.
let servo = PWMOut(Id.PWM4A)

while true {
    let value = a0.readPercent() // Read the analog value and return a value between 0.0 and 1.0.
    let pulse = Int(500 + 2000 * value) // Calculate the value to get the pulse duration.
    servo.set(period: 20000, pulse: pulse) // Set the servo position according to the scaled value.
    sleep(ms: 20)
}

```

## What you'll see

## Servo motor





## Code Analysis



## See also



