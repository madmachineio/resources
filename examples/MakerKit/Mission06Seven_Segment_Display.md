# <span style="color:#EA5823;font-weight:800">Example Name</span>


## <span style="color:#EA5823;font-weight:700">What you need</span>


## <span style="color:#EA5823;font-weight:700">Circuit</span>


## <span style="color:#EA5823;font-weight:700">Tips</span>


## <span style="color:#EA5823;font-weight:700">Code</span>

#### main.swift
```swift
/*
  Mission6 7-Segment Display

  You should see a number "6" on the 7-segment display.

  The circuit:
  - Connect the 7-segment display into the Arduino Sheild.
  - Note: 7-segment display consists of 7 LEDs, called segments, arranged in the shape of an “8”. 
    Most 7-segment displays actually have 8 segments, with a dot on the right side of the digit 
    that serves as a decimal point.

  created 2019
  by Orange J

  Try to show characters like “H” “E” “L” “L” “O” on it. 
  This example code is in the public domain.
  Visit madmachine.io for more info.
*/

import SwiftIO

let number = 6
let sevenSeg = SevenSegment()

while true {
    sevenSeg.print(number)

}

```

#### SevenSegment.swift
```swift
/*
  Show number 0-9 on a Common Anode 7-segment LED display.
    A
   ---
F |   | B
  | G |
   ---
E |   | C
  |   |
   ---
    D
  This example code is in the public domain.
 */

import SwiftIO

class SevenSegment {
    // Initialize the seven digital pins which are connected to the segment pins.
    static let a = DigitalOut(Id.D8)
    static let b = DigitalOut(Id.D7)
    static let c = DigitalOut(Id.D6)
    static let d = DigitalOut(Id.D5)
    static let e = DigitalOut(Id.D4)
    static let f = DigitalOut(Id.D2)
    static let g = DigitalOut(Id.D3)
    
    let leds = [a, b, c, d, e, f, g]
    // Use a binary data to store the status of each segment for the number from 0 to zero.
	let ledState: [UInt8] = [0x3F, 0x06, 0x5B, 0x4F, 0x66, 0x6D, 0x7D, 0x07, 0x7F, 0x6F]
    
    public func print(_ number: Int) {
        let num = number % 10
        let value = ledState[num] 
        
        // Get the value of each bit to determine whether the relevant segment is on or off.
        for i in 0..<7{
            let state = (value >> i) & 0x01
            if state == 0 {
                leds[i].write(true)
            } else {
                leds[i].write(false)
            }   
        }

    }
}

```

## <span style="color:#EA5823;font-weight:700">Video</span>


## <span style="color:#EA5823;font-weight:700">See Also</span>


## <span style="color:#EA5823;font-weight:700">References</span>

---
Last revision 2020/09/10 by Johnson