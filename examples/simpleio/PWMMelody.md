# <span style="color:#EA5823;font-weight:800">Example Name</span>


## <span style="color:#EA5823;font-weight:700">What you need</span>


## <span style="color:#EA5823;font-weight:700">Circuit</span>


## <span style="color:#EA5823;font-weight:700">Tips</span>


## <span style="color:#EA5823;font-weight:700">Code</span>


```swift
/// Enable the speaker to play a simple melody by changing the frequency of PWM output.

/// Import the library to enable the relevant classes and functions.
import SwiftIO

/// Initialize a PWM output pin the speaker is connected to.
let speaker = PWMOut(Id.PWM0A)

/// Specify several frequencies corresponding to each note of the melody. 
let fre = [
    350,350,393,441,
    441,393,350,330,
    294,294,330,350,
    350,330,330
]

/// Allow the speaker to repeat the melody again and again.
while true {
    for f in fre {
        // Change the frequency and the duty cycle of output to produce each note.
        speaker.set(frequency: f, dutycycle: 0.5)
        sleep(ms: 250)
    }
}

```


## <span style="color:#EA5823;font-weight:700">Video</span>


## <span style="color:#EA5823;font-weight:700">See Also</span>


## <span style="color:#EA5823;font-weight:700">References</span>

---
Last revision 2020/09/10 by Johnson