# BrightnessAnalogIn

![](../../.gitbook/assets/BrightnessAnalogIn01.gif)

In this example, we use PWM to adjust the brightness of an LED according to the position of the potentiometer.

## What you need

* SwiftIO board
* Jumper wires
* Potentiometer or Module
* LED light and a 330 ohm resistor \(or LED Module\)
* SwiftIO shield \(optional\)

#### Kits that meet the experimental conditions:

* [Maker Kit for SwiftIO](https://www.madmachine.io/product-page/maker-kit-for-swiftio)

## Circuit

![](../../.gitbook/assets/BrightnessAnalogIn.png)

## Code

```swift
// Read the analog input value and use it to set the PWM output in order to change the LED brightness.
// Import the library to enable the relevant classes and functions.
import SwiftIO

// Import the board library to use the Id of the specific board.
import SwiftIOBoard

// Initialize an analog input and a digital output pin the components are connected to.
let sensor = AnalogIn(Id.A0)
let led = PWMOut(Id.PWM0A)

// Allow the LED brightness control all the time.
while true {
    // Read the input voltage in percentage.
    let value = sensor.readPercent()
    // Light the LED by setting the duty cycle.
    led.setDutycycle(value)
    // Keep the current LED state for 200 millisecond.
    sleep(ms: 200)
}
```

## Instruction

### About code

To get analog input value, there are three available methods. In this case, you will need `.readPercentage`. It will return a decimal number that represents the ratio of actual voltage and reference voltage \(3.3V\). The value will then be used as duty cycle to set the LED brightness.

### Experiment more

Once you get the example running, grab your SwiftIO board and shake it back and forth. What you are doing here is actually mapping time across the entire space. In our opinion, motion blurs each LED flashing into a line. As the LED fades in and out, the length of these thin lines will increase and decrease. Now you will see the pulse width.

### Why would PWM instead of traditional analog signal?

Unlike incandescent light bulbs, LEDs \(and also some other devices\) can only operate under certain voltage. Lowering the voltage on LEDs wouldn't result in a lower brightness, the LED will simply turn off if the voltage isn't high enough.

However, we can use PWM to control the overall power output of the LEDs. Actually, the LED is flashing, but our eyes cannot react quickly enough for it. So it efficiently tricks our brain into thinking this LED is darker.

> Side note: most of the mobile phones use the same method to control the brightness of the screen. However, if the frequency of the flashing is too low \(the screen is very dark\), it may be harmful to your eyes.

## See Also

* [PWMOut](https://swiftioapi.madmachine.io/Classes/PWMOut.html) - The PWMOut class is used to change the time of high voltage during one period to simulate different output. 

## References

* [wiki: Pulse-width modulation](https://en.wikipedia.org/wiki/Pulse-width_modulation)
* [wiki: Duty cycle](https://en.wikipedia.org/wiki/Duty_cycle)
* [wiki: Potentiometer](https://en.wikipedia.org/wiki/Potentiometer)
* [wiki: Voltage divider](https://en.wikipedia.org/wiki/Voltage_divider)

## Tips

![](../../.gitbook/assets/01%20%282%29.png)

![](../../.gitbook/assets/02%20%281%29.png)

