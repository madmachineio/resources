# Mission7\_DC\_Motors

In this mission, let's DIY a small fin. You will use a DC motor.

## What you need

![](../../.gitbook/assets/asset-36.png)

## Circuit

### Circuit diagram

![](../../.gitbook/assets/motor%20%281%29.png)

### Build your circuit

Place the shield on top of your SwiftIO board. 

Connect the **potentiometer** module to pin **A0** using a 4-pin cable. 

Connect **Motor Driver** module to pin **PWM2B** \(D10\). Then connect the DC motor to the motor and attach the fan blade to the shaft.

## Example code

You could open the code in the ![](../../.gitbook/assets/xnip2020-07-22_16-04-33.jpg) &gt; MakerKit &gt; Mission7\_DC\_Motors.

```swift
// Import the SwiftIO library to use everything in it.
import SwiftIO

// Import the board library to use the Id of the specific board.
import SwiftIOBoard

// Initialize the analog pin and the PWM pin 
let a0 = AnalogIn(Id.A0)
let motor = PWMOut(Id.PWM2B)

while true {
    // Read the input value and use it to set the duty cycle of pwm.
    let value = a0.readPercent()
    motor.setDutycycle(value) 
    sleep(ms: 50)
}

```

## What you'll see

After you download the code, the fan will start to rotate. You could feel the breeze from it.

## DC motors

DC motor or Direct Current Motor could concert the electricity into motion.

It normally has two legs, a positive one and a negative one. As you connect it to the power, it will start to rotate. And if you connect the legs in an opposite direction, the motor still works but will rotate the opposite way. 

Then why does it rotate when applying voltage? That's because as the current flows, there will be an electromagnet field, and will thus cause the motor to rotate. The speed of rotation could be controlled by the PWM signal. You could adjust its duty cycle to change the speed.

## Code Analysis

Import the two libraries: `SwiftIO` and `SwiftIOBoard`.

Initialize the analog pin A0 for the potentiometer and the PWM pin PWM2B for the motor.

In the dead loop, read the input value in percentage, then use this value to set the duty cycle of the PWM output. Set a suitable sleep time.

Ok, that's all about the code. It is quite straightforward.

