# <span style="color:#EA5823;font-weight:800">BlinkAnalogIn</span>

![](../../.gitbook/assets/BlinkAnalogIn01.gif)

In this example, we use a variable resistor (aka potentiometer) to control the flashing speed of an LED light.

In order to do this, we read the value of the resistor first, by using the analog input function on the SwiftIO board. Then, we can use the code below to link the value of the resistor to the blinking speed of the LED light. The resistor's analog value is read as a voltage change, a key character of the analog circuit.


## <span style="color:#EA5823;font-weight:700">What you need</span>
- SwiftIO board
- Jumper wires
- Potentiometer or Module
- LED Module (LED and 10k ohm resistor)
- SwiftIO shield (optional)
  
#### Kits that meet the experimental conditions: 
- [Maker Kit for SwiftIO](https://www.madmachine.io/product-page/maker-kit-for-swiftio)

## <span style="color:#EA5823;font-weight:700">Circuit</span>


![](../../.gitbook/assets/BlinkAnalogIn/03.png)

Prepare the jumper wire cables, be aware of the female and male ends. Connect the male ends to the SwiftIO board at ports GND，3.3V and P20/A6 ports. 

Connect the P20/A6 wire to the middle pin of the potentiometer. Connect the GND wire to the outer pins of the potentiometer, and the 3.3V wire to the other outer pin of the potentiometer. 

On the LED module, connect jumper wires to GND and SIG ports. Connect the GND wire to the GND port of SwiftIO, and connect the SIG wire to the P10/D10 port.


## <span style="color:#EA5823;font-weight:700">Code</span>



```swift
/// Read the analog input and use it to set the rate of LED blink.

/// Import the library to enable the relevant classes and functions.
import SwiftIO

/// Initialize an analog input and a digital output pin the components are connected to,
let sensor = AnalogIn(Id.A6)
let led = DigitalOut(Id.D10)

/// Enable the LED to blink over and over again.
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


## <span style="color:#EA5823;font-weight:700">Instruction</span>

The `.readRawValue()` function reads the current raw value from the specified analog pin. Since the analog-to-digital converter on the SwiftIO Board has a resolution of 12-bit, the corresponding voltage is 0-3.3V. Therefore, the corresponding value would be 0-4095. 

The `.toggle()` function, as the name suggests, inverts the output level on a specific digital pin. 

Between each `.toggle()`, a `sleep(ms: )` function with a parameter `value` is used. This makes sure that there's a certain amount of time between each toggle, and the time is under control.


<!--
`.readRawValue()` Read the current raw value from the specified analog pin. 由于SwiftIO Board的模拟数字转换器是12bit分辨率的ADC，所以对应电压0-3.3V，将返回相应的数值是0-4095. 这个数值将作为D10端口高低电平`toggle()`的间隔时间。 The toggle() (as the name implies) method of DigitalOut means that the output level is inverted.
-->

## <span style="color:#EA5823;font-weight:700">See Also</span>

- [Id](https://swiftioapi.madmachine.io/Enums/Id.html) - Enumerations, public enum Id : UInt32
- [AnalogIn.readRawValue()](https://swiftioapi.madmachine.io/Classes/AnalogIn.html#/s:7SwiftIO8AnalogInC12readRawValueSiyF) - Read the current raw value from the specified analog pin.

## <span style="color:#EA5823;font-weight:700">References</span>

- [Potentiometer](https://en.wikipedia.org/wiki/Potentiometer)
- [Voltage divider](https://en.wikipedia.org/wiki/Voltage_divider)

## <span style="color:#EA5823;font-weight:700">Tips</span>

If you have the optional modules, you can also setup the circuit as shown belown.

![](../../.gitbook/assets/BlinkAnalogIn/01.png)

![](../../.gitbook/assets/BlinkAnalogIn/02.png)


---
Last Edit 2020/09/13 by Martin

> Language fixes.

Last revision 2020/09/04 by Johnson