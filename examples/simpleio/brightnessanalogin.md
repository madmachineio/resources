# BrightnessAnalogIn

![](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2F134d7c3b3ca6c6870503907c7fed84bcfe0e9334.gif?alt=media)

In this example, we use an analog output \(pulse width modulation, PWM\) to adjust the brightness of an LED based on the position of the potentiometer.

PWM is a technology that obtains a very similar behavior from a digital output, which can be turned off and on very quickly, and the ratio between on and off time is different.

## What you need <a id="what-you-need"></a>

* SwiftIO board
* Jumper wires
* Potentiometer or Module
* LED and 330 ohm resistor or LED Module
* SwiftIO shield \(optional\)

#### Kits that meet the experimental conditions: <a id="kits-that-meet-the-experimental-conditions"></a>

* ​[Maker Kit for SwiftIO](https://www.madmachine.io/product-page/maker-kit-for-swiftio)​

## Circuit <a id="circuit"></a>

![](../../.gitbook/assets/image%20%283%29.png)

## Code <a id="code"></a>

```swift
// Read the analog input value and use it to set the PWM output in order to change the LED brightness.

// Import the library to enable the relevant classes and functions.
import SwiftIO

// Initialize an analog input and a digital output pin the components are connected to.
let sensor = AnalogIn(Id.A6)
let led = PWMOut(Id.PWM2B)

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

## Instruction <a id="instruction"></a>



Correspondingly, analogIn's `readRawValue()` is not called this time, but the corresponding return value range of `readPercent()` is 0 to 1.

### Why would choose PWM instead of traditional analog signal? <a id="why-would-pwm-instead-of-traditional-analog-signal"></a>

Unlike incandescent light bulbs, LEDs \(and also some other devices\) can only operate under certain voltage. Lowering the voltage on LEDs wouldn't result in a lower brightness, the LED will simply turn off if the voltage isn't high enough.

However, we can use PWM to control the overall power output of the LEDs. Indeed is the LED flashing, but our eyes cannot react quick enough for it. So it efficiently trick our brain into thinking this LED is darker.

> Side note: most of the mobile phones use the same method to control the brightness of the screen. However, if the frequency of the flashing is too low \(the screen is very dark\), it may be harmful to your eyes.

### Experiment more <a id="experiment-more"></a>

Once you get the example running, grab your SwiftIO board and shake it back and forth. What you are doing here is actually mapping time across the entire space. In our opinion, motion blurs each LED flashing into a line. As the LED fades in and out, the length of these thin lines will increase and decrease. Now you will see the pulse width.

## See Also <a id="see-also"></a>

* ​[PWMOut](https://swiftioapi.madmachine.io/Classes/PWMOut.html) - The PWMOut class is used to change the time of high voltage during one period to simulate different output. 

## References <a id="references"></a>

* ​[wiki: Pulse-width modulation](https://en.wikipedia.org/wiki/Pulse-width_modulation)​
* ​[wiki: Duty cycle](https://en.wikipedia.org/wiki/Duty_cycle)​
* ​[wiki: Potentiometer](https://en.wikipedia.org/wiki/Potentiometer)​
* ​[wiki: Voltage divider](https://en.wikipedia.org/wiki/Voltage_divider)​

## Tips <a id="tips"></a>

![](../../.gitbook/assets/image%20%289%29.png)

  


![](../../.gitbook/assets/image%20%282%29.png)

