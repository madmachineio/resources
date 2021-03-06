# PWMBrightnessControl

![](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2Fb81e5137c8d3a490823f2e5c67617a86a1aba4e7.gif?alt=media)

In this project, let's try to control the brightness of LED - light gradually on and off LED.

You will use PWM to set the on-off ratio of the output signal to simulate different voltages. The pins marked with “~“ can be used for this.

## What you need

* SwiftIO board 
* LED 
* 330ohm resistor 
* Breadboard 
* Jumper wires

## Circuit

![](../../.gitbook/assets/PWMBrightnessControl.png)

Build the circuit as shown above.

* The anode \(positive leg\) of LED goes to PWM2B through a resistor.
* The cathode \(negative leg\) of LED connects to the ground.

## Code

You can find the example code at the bottom left corner of IDE: ![](../../.gitbook/assets/xnip2020-07-22_16-04-33.jpg) &gt; GettingStarted &gt; PWMBrightnessControl.

```swift
// Brighten or dimming the LED by changing the duty cycle of PWM signal.
// Import the library to enable the relevant classes and functions.
import SwiftIO

// Import the board library to use the Id of the specific board.
import SwiftIOBoard

// Initialize the PWM pin the LED is connected to, with other parameters set to default.
let led = PWMOut(Id.PWM0A)

// Initialize a variable to store the value of duty cycle.
var value: Float = 0.0

// Change the brightness from on to off and off to on over and over again.
while true {
    // Brighten the LED in two seconds.
    while value <= 1.0 {
        led.setDutycycle(value)
        sleep(ms: 20)
        value += 0.01
    }
    // Keep the duty cycle between 0.0 and 1.0.
    value = 1.0

    // Dimming the LED in two seconds.
    while value >= 0 {
        led.setDutycycle(value)
        sleep(ms: 20)
        value -= 0.01
    }
    // Keep the duty cycle between 0.0 and 1.0.
    value = 0.0
}
```

## Instruction

### What is Pulse Width Modulation \(PWM\)?

Pulse Width Modulation \(PWM\) can simulate analog results digitally. Digital control is used to create a square wave, a signal that switches between on and off. The duration of the "on-time" is called the **pulse width**. By changing the ratio of the on-time to the off-time, it will simulate the voltage between fully open \(3.3 volts\) and off \(0 volts\).  

For example, if you repeat this switching pattern with LEDs fast enough, the signal seems to be a stable voltage between 0 and 3.3v. And the LED would show different brightness.

Now come more concepts. A fixed time **period** consists of on and off time. The duration or period is the inverse of the PWM **frequency**. For example, when the PWM frequency is 500 Hz, one period is 2 milliseconds.

The **duty cycle** is the percentage of on-time of output signal during one period. Its range is 0-1. 1 means the output is always on. 0 means the output is always low. And the signal with a 0.5 duty cycle is on for 50% of the time and off for 50% of the time.

![https://commons.wikimedia.org/w/index.php?curid=72876123](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2Fc53ea8bfa1c0c448d7f35547069200ec05c939ac.png?alt=media)

### About code

You may notice the pin names of PWM are a little strange, with "A" or "B" after the number. Since there are 14 pins for PWM in total, some pins are paired, like PWM3A and PWM3B. Two paired pins can only share the same frequency. So check the `Id` enumeration [here](https://swiftioapi.madmachine.io/Enums/Id.html).

To change the brightness of the LED, the duty cycle would change all the time. So you need a variable to store its value. `var` is the keyword to declare a variable. Just like its name, its value can always change after it has been assigned. 

The `value` is explicitly declared as a floating-point number type. This is very important for scenarios where the type is easy to be confused, for example, 0.0 could be float or double. And each numeric type has a different range of numbers. 

In the loop `while true`, the first `while` loop is to ensure the value not bigger than 1.0 and gradually brighten the LED. `.setDutyCycle` method allows you to set the duty cycle. Each time, you will gradually increase the value by 0.01. The brightening process lasts for 2 minutes. To ensure a smooth brightness change, you need to set appropriate value change and sleep time. After finishing the first loop, the value is about 1.01. So `value = 1.0` is to keep it in the specified range.  The second while is similar but to dim the LED. 

## See Also

* [Id](https://swiftioapi.madmachine.io/Enums/Id.html) - Enumerations of all the pins on the board.
* ​[PWMOut.setDutyCycle](https://swiftioapi.madmachine.io/Classes/PWMOut.html#/s:7SwiftIO6PWMOutC12setDutycycleyySfF) - Set the duty cycle of a PWM output signal.
* [Numeric Type Conversion](https://docs.swift.org/swift-book/LanguageGuide/TheBasics.html) - An integer type can be initialized with a Double or Float value.

## References

* ​[wiki: Pulse-width modulation](https://en.wikipedia.org/wiki/Pulse-width_modulation)​
* ​[wiki: Duty cycle](https://en.wikipedia.org/wiki/Duty_cycle)​



