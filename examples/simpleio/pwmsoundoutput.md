# PWMSoundOutput

![](../../.gitbook/assets/PWM.gif)

This example shows how to use the `PWMOut` to generate notes. It plays three tones repeatedly.

## What you need

* SwiftIO board
* Jumper wires
* Buzzer
* SwiftIO shield \(optional\)

## Circuit

![](../../.gitbook/assets/PWMSoundOutput%20%281%29.png)

## Code

```swift
// Produce different notes by changing the frequency of PWM signal.

// Import the library to enable the relevant classes and functions.
import SwiftIO

// Initialize a PWM output pin the speaker is connected to.
let speaker = PWMOut(Id.PWM2B)

// Specify several frequencies to produce different sound.
let fre = [262, 294, 330]

// Play recurrently these notes.
while true {
    for f in fre {
        // Set the frequency and the duty cycle of output to produce each note.
        speaker.set(frequency: f, dutycycle: 0.5)
        // Play each note for one second.
        sleep(ms: 1000)
    }

}
```

## Instruction

The code above uses a Frequency as musical pitches. For example, NOTE\_C4 is middle C, whose frequency is 262 Hz. Latter example MidiPlayer we will markdown all this musical note in a file. This file contains all the pitch values for typical notes. You may find it useful whenever you want to make musical notes.

## See Also

* [PWMOut](https://swiftioapi.madmachine.io/Classes/PWMOut.html) - The PWMOut class is used to change the time of high voltage during one period to simulate different output. 

## References

* [Frequency and Pitch](http://www.vias.org/crowhurstba/crowhurst_basic_audio_vol1_006.html)
* [Online Tone Generator](https://www.szynalski.com/tone-generator/)
* [wiki: Pitch \(music\)](https://en.wikipedia.org/wiki/Pitch_%28music%29)

