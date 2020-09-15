# <span style="color:#EA5823;font-weight:800">ReadAnalogInput</span>

![](../../.gitbook/assets/ReadAnalogInput/ReadAnaloginput.gif)

---

![](../../.gitbook/assets/ReadAnalogInput/screen.gif)

In this new example, you are going to read analog input. We'll use a potentiometer.

The potentiometer can provide a certain range of resistance. When you twist the knob, the resistance will change, thus the input voltage will change with it.

When SwiftIO board reads from the pin, it will get a number between 0 and 4095. And then change it into a digital number between 0 and 3.3V.

## <span style="color:#EA5823;font-weight:700">What you need</span>

- SwiftIO board
- potentiometer
- wires

## <span style="color:#EA5823;font-weight:700">Circuit</span>

![](../../.gitbook/assets/ReadAnalogInput/ReadAnalogInput.png)

Let's build the circuit now. 

The potentiometer has three legs:

- the first leg on the left goes to analog pin A0
- the second leg goes to power
- the third leg goes to ground

Different potentiometer may vary, so please refer to its manual before building the circuit.

## <span style="color:#EA5823;font-weight:700">Code</span>

You can find the example code at the bottom left corner of IDE: ![](../../.gitbook/assets/xnip2020-07-22_16-04-33.jpg) &gt; GettingStarted &gt; ReadAnalogInput.
Well, you may try to read from to other modules, like sensors. It's quite interesting.

For the code, we will use the `AnalogIn` class.

```swift
// Read the input voltage on a specified analog pin. 
// The value you get will be a float number between 0.0 and 3.3.

// Import the library to enable everything in it, like relevant classes and methods. 
// This is first step for your coding process.
import SwiftIO

// Initialize the pin A0 as a analog input.
let pin = AnalogIn(Id.A6)

// Read the input voltage every second.
while true {
    // Declare a constant to store the value.
    // Read the voltage value from the analog pin.
    let value = pin.readVoltage()
    // Print the value and you can see it in the serial monitor.
    print(value)
    // Wait a second to slow the reading frequency.
    sleep(ms: 1000)
}
```
## <span style="color:#EA5823;font-weight:700">Instruction</span>

The parameter passed by the object `AnalogIn` must be the port (A0-A11) that can be used for analog input in the enumeration `Id`. There are three methods for returning the analog value in this object. `.readVoltage()` returns the voltage value , The return value is a floating point number between 0V-3.3V. The `print()` function is a parameter to print the result directly to the serial port. You can conveniently use a computer to connect to the serial port of the SwiftIO Board to view the results and debug. Please note that the SwiftIO Board has two USB ports. The port used to load programs cannot be used as a monitor serial port, so you need to change the line. For details, please see the Tips operations below. Both USB ports can be used as power supply ports for SwiftIO Board.

<!-- 对象`AnalogIn`传入的参数必须是枚举`Id`中可用于模拟输入的端口(A0-A11)，该对象中返回模拟值的方法有三个，`.readVoltage()`返回的是电压值，其返回值是介于0V-3.3V之间的浮点数。`print()`函数是直接向串口打印结果的参数，可以方便的使用计算机连接SwiftIO Board的串口后查看结果，并调试。请注意，SwiftIO Board有两个USB连接口，其中用于载入程序的接口并不能作为监听串口使用，所以需要进行换线操作，具体请查看下面Tips种的操作。这两个USB接口均可作为SwiftIO Board的供电接口。 -->

## <span style="color:#EA5823;font-weight:700">See Also</span>

- [Id](https://swiftioapi.madmachine.io/Enums/Id.html) - Enumerations, public enum Id : UInt32
- [AnalogIn.readRawValue()](https://swiftioapi.madmachine.io/Classes/AnalogIn.html#/s:7SwiftIO8AnalogInC12readRawValueSiyF) - Read the current raw value from the specified analog pin.

## <span style="color:#EA5823;font-weight:700">References</span>

- [Potentiometer](https://en.wikipedia.org/wiki/Potentiometer)
- [Voltage divider](https://en.wikipedia.org/wiki/Voltage_divider)

## <span style="color:#EA5823;font-weight:700"> Tips</span>

![](../../.gitbook/assets/ReadDigitalInput/changeWire.gif)

---
Last revision 2020/09/04 by Johnson

