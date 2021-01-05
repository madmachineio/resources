# ReadDigitalInput

![](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2F28482b5134f9b71ba3d12d3b6f5d82d9732d680f.gif?alt=media)

![](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2F248974b7412722c96a260a31c8c1dd91cb365749.gif?alt=media)

In this example, let's try to read digital signal using a pushbutton. When you press or release the button, the input value will change accordingly. The value is true or false. You could see the result in serial monitor.

## What you need

* SwiftIO board
* Button
* Jumper wires

## Circuit

![](../../.gitbook/assets/digitalinput.jpg)

The button has four legs. The two legs on same side are shorted as the following image:

![](../../.gitbook/assets/button%20%281%29.png)

Connect one leg on the left side to 3.3V pin. And connect the leg on right side to digital pin D10. Usually in circuit diagram, the line connected to power is in red and the line to ground is in black.

In default mode, as there is no current, the digital pin reads `false`. When you press the button, the two points on the button will be shorted. And the value of pin will be `true`.

_**Note**: If you connected the two legs on the same side in this circuit, you would notice there will be no change whether you press or release the button. So please be sure to connect the button in a right way._

## Code

You can find the example code by clicking the bottom left corner of IDE: ![](../../.gitbook/assets/xnip2020-07-22_16-04-33.jpg) &gt; GettingStarted &gt; ReadDigitalInput.

```swift
// Read the input voltage on a specified digital pin. 
// The value you get will be either true or false.

// Import the library to enable everything in it, like relevant classes and methods. 
// This is first step for your coding process.
import SwiftIO

// Initialize the pin D10 as a digital input pin.
let pin = DigitalIn(Id.D10)

// read the input every second.
while true {
    // Declare a constant to store the value you read from the digital pin.
    let value = pin.read()
    // Print the value and you can see it in the serial monitor.
    print(value)
    // Wait a second to slow the reading frequency.
    sleep(ms: 1000)
}
```

## Instruction <a id="instruction"></a>

The parameter passed by the instance `DigitalIn` must be the pin \(D0-D45\) that can be used for digital input in the enumeration `Id`. When used as digital input, the pin state will be detected to identify if there is any change in the circuit.

_**Note**: these digital pins could be used for output and input. When you initialize the pin, you need to set the exact class, `DigitalIn` or `DigitalOut` according to your usage._

`.read` method is used to read the state of the pin. The return value is `true` or `false`, representing high level and low level respectively.

`print()` function is to print the result directly to the serial port. You can conveniently connect the computer to the serial port of the SwiftIO Board. In the IDE, there is a serial monitor to view the results and debug.

_**Note**: SwiftIO Board has two USB ports. Both USB ports can be used as power supply ports for SwiftIO Board. However, the port used to load programs cannot be used as a serial monitor port, so you need to change the port after download the code. For details, please see the_ [_operations_](readdigitalinput.md#tips) _below._ 

## See Also <a id="see-also"></a>

* ​[Id](https://swiftioapi.madmachine.io/Enums/Id.html) - Enumerations of all pins on the board.
* ​[DigitalIn.read\(\)](https://swiftioapi.madmachine.io/Classes/DigitalIn.html#/s:7SwiftIO9DigitalInC4readSbyF) - Detect the state of a digital input pin. The input value is either true \(1\) or false \(0\).

## Tips <a id="tips"></a>

![](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2Fe4d8c917db768afd4b8a62cd2dae310db00e818f.gif?alt=media)

