# PWMSoundOutput



![](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2Ff7e2e1f92f1adcd02176d07c8516d839562c1e42.gif?alt=media)

This example shows how to use the `PWMOut` to generate notes. It plays three tones repeatedly.

## What you need <a id="what-you-need"></a>

* SwiftIO board
* Jumper wires
* Buzzer
* SwiftIO shield \(optional\)

## Circuit <a id="circuit"></a>

![](https://gblobscdn.gitbook.com/assets%2F-MGOJWkptBbZ3bq0TpEw%2Fsync%2F0bac2c11aa75def028e3b4e68dcd2d9219d83ba7.png?alt=media)

## Code <a id="code"></a>

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

## Instruction <a id="instruction"></a>

The code above uses a Frequency as musical pitches. For example, NOTE\_C4 is middle C which frequency is 262. Latter example MidiPlayer we will markdown all this musical note in a file. This file contains all the pitch values for typical notes. You may find it useful whenever you want to make musical notes.

## See Also <a id="see-also"></a>

* ​[PWMOut](https://swiftioapi.madmachine.io/Classes/PWMOut.html) - The PWMOut class is used to change the time of high voltage during one period to simulate different output. 

## References <a id="references"></a>

* ​[Frequency and Pitch](http://www.vias.org/crowhurstba/crowhurst_basic_audio_vol1_006.html)​
* ​[Online Tone Generator](https://www.szynalski.com/tone-generator/)​
* [Pitch \(music\)](https://en.wikipedia.org/wiki/Pitch_%28music%29)

