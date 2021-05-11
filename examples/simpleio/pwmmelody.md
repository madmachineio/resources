# PWMMelody

![](../../.gitbook/assets/PWM%20%281%29.gif)

This example shows how to use the `PWMOut` to generate notes. It plays a little melody which you may have heard before.

## What you need

* SwiftIO board
* Jumper wires
* Piezo buzzer or a speaker
* SwiftIO shield \(optional\)

## Circuit

![](../../.gitbook/assets/PWMSoundOutput.png)

## Code

```swift
// Enable the speaker to play a simple melody by changing the frequency of PWM output.

// Import the library to enable the relevant classes and functions.
import SwiftIO

// Initialize a PWM output pin the speaker is connected to.
let speaker = PWMOut(Id.PWM2B)

// Specify several frequencies corresponding to each note of the melody. 
let fre = [
    330,330,349,392,
    392,349,330,294,
    262,262,294,330,
    330,294,294
]

// Allow the speaker to repeat the melody again and again.
while true {
    for f in fre {
        // Change the frequency and the duty cycle of output to produce each note.
        speaker.set(frequency: f, dutycycle: 0.5)
        sleep(ms: 250)
    }
}
```

## Instruction

The PWM signal outputs high and low voltage alternatively. Inside the buzzer, there is a material that could change back and forth as the signal switches between on and off. Thus the buzzer produces the notes. And the frequency will influence the pitch. 

## See Also

* [PWMOut](https://swiftioapi.madmachine.io/Classes/PWMOut.html) - The PWMOut class is used to change the time of high voltage during one period to simulate different output. 

## References

* [Frequency and Pitch](http://www.vias.org/crowhurstba/crowhurst_basic_audio_vol1_006.html)
* [Online Tone Generator](https://www.szynalski.com/tone-generator/)
* [wiki: Pitch \(music\)](https://en.wikipedia.org/wiki/Pitch_%28music%29)

