# <span style="color:#EA5823;font-weight:800">Example Name</span>


## <span style="color:#EA5823;font-weight:700">What you need</span>


## <span style="color:#EA5823;font-weight:700">Circuit</span>


## <span style="color:#EA5823;font-weight:700">Tips</span>


## <span style="color:#EA5823;font-weight:700">Code</span>


```swift
/// Produce different notes by changing the frequency of PWM signal.

/// Import the library to enable the relevant classes and functions.
import SwiftIO

/// Initialize a PWM output pin the speaker is connected to.
let speaker = PWMOut(Id.PWM0A)

/// Specify several frequencies to produce different sound.
let fre = [262, 294, 330]

/// Play recurrently these notes.
while true {
    for f in fre {
        // Set the frequency and the duty cycle of output to produce each note.
        speaker.set(frequency: f, dutycycle: 0.5)
        // Play each note for one second.
        sleep(ms: 1000)
    }
    
}
```


## <span style="color:#EA5823;font-weight:700">Video</span>


## <span style="color:#EA5823;font-weight:700">See Also</span>


## <span style="color:#EA5823;font-weight:700">References</span>

---
Last revision 2020/09/10 by Johnson