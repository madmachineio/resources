# BlinkAnalogIn

![](../../.gitbook/assets/BlinkAnalogIn01.gif)

In this example, we use a variable resistor \(aka potentiometer\) to control the flashing speed of an LED light.

In order to do this, we read the value of the resistor first, by using the analog input function on the SwiftIO board. Then, we can use the code below to link the value of the resistor to the blinking speed of the LED light. The resistor's analog value is read as a voltage change, a key character of the analog circuit.

## What you need

* SwiftIO board
* Jumper wires
* Potentiometer or Module
* LED and 330 ohm resistor \(or LED Module\)
* SwiftIO shield \(optional\)

### Kits that meet the experimental conditions:

* [Maker Kit for SwiftIO](https://www.madmachine.io/product-page/maker-kit-for-swiftio)

## Circuit

![](../../.gitbook/assets/BlinkAnalogIn.png)

Prepare the jumper wire cables, be aware of the female and male ends. Connect the male ends to the SwiftIO board at ports GND, 3.3V and P20/A6 ports.

Connect the P20/A6 wire to the middle pin of the potentiometer. Connect the GND wire to the outer pins of the potentiometer, and the 3.3V wire to the other outer pin of the potentiometer.

On the LED module, connect jumper wires to GND and SIG ports. Connect the GND wire to the GND port of SwiftIO, and connect the SIG wire to the P10/D10 port.

## Code

```swift
// Read the analog input and use it to set the rate of LED blink.

// Import the library to enable the relevant classes and functions.
import SwiftIO

// Initialize an analog input and a digital output pin the components are connected to
let sensor = AnalogIn(Id.A6)
let led = DigitalOut(Id.D10)

// Enable the LED to blink over and over again.
while true {
    // Read the input voltage in percentage.
    let value = sensor.readRawValue()
    print(value)
    // Change the current LED state.
    led.toggle()
    // Keep the led on or off for a certain amount of time determined by the value you get.
    sleep(ms: value)
}
```

## Instruction

The `.readRawValue()` function reads the current raw value from the specified analog pin. Since the analog-to-digital converter on the SwiftIO Board has a resolution of 12-bit, the corresponding voltage is 0-3.3V. Therefore, the corresponding value would be 0-4095.

The `.toggle()` function, as the name suggests, inverts the output level on a specific digital pin.

Between each `.toggle()`, a `sleep(ms: )` function with a parameter `value` is used. This makes sure that there's a certain amount of time between each toggle, and the time is under control.

## See Also

* [Id](https://swiftioapi.madmachine.io/Enums/Id.html) - Enumerations of all pins on the board
* [AnalogIn.readRawValue\(\)](https://swiftioapi.madmachine.io/Classes/AnalogIn.html#/s:7SwiftIO8AnalogInC12readRawValueSiyF) - Read the current raw value from the specified analog pin.

## References

* [Potentiometer](https://en.wikipedia.org/wiki/Potentiometer)
* [Voltage divider](https://en.wikipedia.org/wiki/Voltage_divider)

## Tips

If you have the optional modules, you can also setup the circuit as shown below.

![](../../.gitbook/assets/01.png)

![](../../.gitbook/assets/02.png)

