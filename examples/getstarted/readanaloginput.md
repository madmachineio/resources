# ReadAnalogInput

![](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2F1f512fb1e8e125c5d2569d65a1949228efd3e823.gif?alt=media)

![](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2F34b9f65cbe730fe9ae247b9da52cf046ba69585a.gif?alt=media)

In this new example, you are going to read analog input. And you'll use a potentiometer to get different results.

The potentiometer can provide a certain range of resistance. When you twist the knob, the resistance in the circuit will change, thus the input voltage will change with it.

When the SwiftIO board reads from the pin, it will get a number between 0 and 4095. And then change it into a digital number between 0 and 3.3V.

## What you need

* SwiftIO board
* Potentiometer
* Jumper wires

## Circuit

![](../../.gitbook/assets/ReadAnalogInput.png)

Let's build the circuit now.

The potentiometer has three legs:

* the first leg on the left goes to ground
* the second leg goes to power
* the third leg goes to goes to analog pin A6

Different potentiometers may vary, so please refer to its manual before building the circuit.

## Code

You can find the example code at the bottom left corner of IDE: ![](../../.gitbook/assets/xnip2020-07-22_16-04-33.jpg) &gt; GettingStarted &gt; ReadAnalogInput. Well, you may try to read from to other modules, like sensors. It's quite interesting.

For the code, you will use the `AnalogIn` class.

```swift
// Read the input voltage on a specified analog pin. The value you get will be a decimal between 0.0 and 3.3.
// Import the library to enable the relevant classes and functions.
import SwiftIO

// Import the board library to use the Id of the specific board.
import SwiftIOBoard

// Initialize the pin A0 as a analog input pin.
let pin = AnalogIn(Id.A0)

// Read the input voltage every second.
while true {
    // Declare a constant to store the value you read from the analog pin.
    let value = pin.readVoltage()
    // Print the value and you can see it in the serial monitor.
    print(value)
    // Wait a second and then continue to read.
    sleep(ms: 1000)
}
```

## Instruction

### What is analog input?

![](../../.gitbook/assets/analog.jpg)

Analog signal is different from the digital signal. Its voltage always changes with time. The value ranges in a certain range, between 0V and 3.3V. So you are able to get 1.5V, 2V...The resolution is used to describe the possible values. The SwiftIO board has a 12-bit resolution, which means there are 4096 \(0-4095\) values in total. 

Let's see the working process for analog to digital conversion. When the board reads from the analog pin, it will first get a raw value between 0 and 4095. Then this value will be converted to voltage value proportionally. Their relationship is like this:

![](../../.gitbook/assets/image%20%2815%29.png)

### About code

The pin available for AnalogIn is from A0 to A11. Before using the pin, you need to initialize it.

`.readVoltage()` returns directly the voltage value. The return value is a floating-point number between 0V-3.3V.

`print()` function is to print the result directly to the serial port. You can conveniently connect the computer to the serial port of the SwiftIO Board. In the IDE, there is a serial monitor to view the results and debug.

_**Note**: SwiftIO Board has two USB ports. Both USB ports can be used as power supply ports for SwiftIO Board. However, the port used to load programs cannot be used as a serial monitor port, so you need to change the port after downloading the code. For details, please see the_ [_operations_](readdigitalinput.md#tips) _below._ 

## See Also

* [Id](https://swiftioapi.madmachine.io/Enums/Id.html) - Enumerations of all pins on the board
* [AnalogIn.readVoltage\(\) ](https://swiftioapi.madmachine.io/Classes/AnalogIn.html#/s:7SwiftIO8AnalogInC11readVoltageSfyF)- Read the voltage from the specified analog pin.

## References

* [wiki: Potentiometer](https://en.wikipedia.org/wiki/Potentiometer)
* [wiki: Voltage divider](https://en.wikipedia.org/wiki/Voltage_divider)

## Tips

![](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2Fe4d8c917db768afd4b8a62cd2dae310db00e818f.gif?alt=media)

