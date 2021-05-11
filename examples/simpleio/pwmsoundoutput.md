# PWMSoundOutput

![](../../.gitbook/assets/PWM.gif)

This example shows how to use the `PWMOut` to generate notes. It plays musical notes repeatedly.

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
let fre = [262, 294, 330, 349, 392, 440, 494]

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

The PWM signal outputs high and low voltage alternatively. Inside the buzzer, there is a material that could change back and forth as the signal switches between on and off. Thus the buzzer produces the notes. And the frequency will influence the pitch. 

The code above uses frequencies to set musical pitches. For example, NOTE\_C4 is middle C, whose frequency is 262 Hz. There are seven notes from 1 to 7 in the array. 

To produce the sound, frequency is the important factor. `.set` method allows you to set both frequency and duty cycle at the same time.

`sleep` defines the duration of notes. Each note will last one second.

## See Also

* [PWMOut](https://swiftioapi.madmachine.io/Classes/PWMOut.html) - The PWMOut class is used to change the time of high voltage during one period to simulate different output. 

## References

* [Frequency and Pitch](http://www.vias.org/crowhurstba/crowhurst_basic_audio_vol1_006.html)
* [Online Tone Generator](https://www.szynalski.com/tone-generator/)
* [wiki: Pitch \(music\)](https://en.wikipedia.org/wiki/Pitch_%28music%29)

