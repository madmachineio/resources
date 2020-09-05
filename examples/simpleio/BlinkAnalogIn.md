# <span style="color:#EA5823;font-weight:800">BlinkAnalogIn</span>

In this example we use a variable resistor (a potentiometer or a photoresistor), we read its value using one analog input of SwiftIO board and we change the blink period of the LED accordingly. The resistor's analog value is read as a voltage because this is how the analog inputs work.

## <span style="color:#EA5823;font-weight:700">What you need</span>
- SwiftIO board
- SwiftIO shield(optional)
- Potentiometer or Module
- LED or Module(optional)
#### Kits that meet the experimental conditions: 
- [Maker Kit for SwiftIO](https://www.madmachine.io/product-page/maker-kit-for-swiftio)

## <span style="color:#EA5823;font-weight:700">Circuit</span>

Connect three wires to the Arduino or Genuino board. The first goes to ground from one of the outer pins of the potentiometer. The second goes from 3.3V volts to the other outer pin of the potentiometer. The third goes from analog input A6 to the middle pin of the potentiometer. 

For this example, it is possible to use the board's built in LED attached to pin RGBLED. To use an additional LED, attach its longer leg (the positive leg, or anode), to digital pin 10 in series with the 220 ohm resistor, and it's shorter leg (the negative leg, or cathode) to the ground (GND) pin next to pin 10.

The circuit based on a photoresistor uses a resistor divider to allow the high impedence Analog input to measure the voltage. These inputs do not draw almost any current, therefore by Ohm's law the voltage measured on the other end of a resistor connected to 3.3V is always 3.3V, regardless the resistor's value. To get a voltage proportional to the photoresistor value, a resistor divider is necessary. This circuit uses a variable resistor, a fixed resistor and the measurement point is in the middle of the resistors. The voltage measured (Vout) follows this formula:

Vout=Vin*(R2/(R1+R2))

12-bit analog to digital converter, which means the analog Read Resolution is 12-bit. The function <code>readRawValue()</code> will read and return the current raw value from the specified analog pin, Data type: <code>int</code>.

## <span style="color:#EA5823;font-weight:700">Schematic</span>


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
    // Keep the led on or off for a certain period determined by the value you get.
    sleep(ms: value)
}


```


## <span style="color:#EA5823;font-weight:700">Video</span>



## <span style="color:#EA5823;font-weight:700">See Also</span>

- Id - Enumerations, public enum Id : UInt32
- AnalogIn.readRawValue() - Read the current raw value from the specified analog pin.

## <span style="color:#EA5823;font-weight:700">References</span>

- 维基百科 Potentiometer

---
Last revision 2020/09/04 by Johnson