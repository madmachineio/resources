# <span style="color:#EA5823;font-weight:800">Example Name</span>


## <span style="color:#EA5823;font-weight:700">What you need</span>


## <span style="color:#EA5823;font-weight:700">Circuit</span>


## <span style="color:#EA5823;font-weight:700">Tips</span>


## <span style="color:#EA5823;font-weight:700">Code</span>


```swift
/*
  Mission7 DC Motor

  Turn the potentiometer and the motor will rotate in a different speed.

  The circuit:
  - Use Potentiometer Module, and connect it to an Analog Jack.
  - Use Motor Driver Module, and connect it to a Digital Jack.

  created 2019
  by Orange J

  Try to change the motor rotate in a diverse direction.
  This example code is in the public domain.
  Visit madmachine.io for more info.
*/

import SwiftIO

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


## <span style="color:#EA5823;font-weight:700">Video</span>


## <span style="color:#EA5823;font-weight:700">See Also</span>


## <span style="color:#EA5823;font-weight:700">References</span>

---
Last revision 2020/09/10 by Johnson