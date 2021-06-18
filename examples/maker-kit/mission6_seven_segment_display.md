# Mission6\_Seven\_Segment\_Display

You could always see 7-segment displays around you used to display digits, like in timer, clock, etc. In this mission, you are going to learn how it works and display numbers on it. Let's start.

## What you need

![](../../.gitbook/assets/asset-35.png)

## Circuit

### Circuit diagram

![](../../.gitbook/assets/circuit.png)

### Build your circuit

Place the shield on top of your SwiftIO board. 

Connect the **7-segment** display to pins reserved for it on the shield.

## Example code

You could open the code in the ![](../../.gitbook/assets/xnip2020-07-22_16-04-33.jpg) &gt; MakerKit &gt; Mission6\_Seven\_Segment\_Display.

The file `SevenSegment.swift`:

```swift
// Import the SwiftIO library to use everything in it.
import SwiftIO
// Import the board library to use the Id of the specific board.
import SwiftIOBoard

final class SevenSegment {
    // Initialize the seven digital pins which are connected to the segment pins.
    static let a = DigitalOut(Id.D8)
    static let b = DigitalOut(Id.D7)
    static let c = DigitalOut(Id.D6)
    static let d = DigitalOut(Id.D5)
    static let e = DigitalOut(Id.D4)
    static let f = DigitalOut(Id.D2)
    static let g = DigitalOut(Id.D3)
    
    
    let leds = [a, b, c, d, e, f, g]
    // Use a binary data to store the status of each segment for the number from 0 to 9.
    // For each data, the last bit represents A and the second bit represents G.
    let ledState: [UInt8] = [
            0b00111111, 0b00000110, 0b01011011, 0b01001111, 0b01100110, 
            0b01101101, 0b01111101, 0b00000111, 0b01111111, 0b01101111
        ]
    
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

The file `main.swift`:

```swift
// Import the SwiftIO library to use everything in it.
import SwiftIO

// Import the board library to use the Id of the specific board.
import SwiftIOBoard

let number = 6
let sevenSeg = SevenSegment()

while true {
    sevenSeg.print(number)
}
```

## What you'll see

After the code is successfully downloaded, the 7-segment display shows the number 6. You could also try to display other numbers or make a count down.

## 7-segment display

Why is it called a 7-segment display? Yeah, it's because it contains 7 segments 🤣. They are A, B, C, D, E, F, G, which are actually 7 LEDs. You could control them separately. 

![](../../.gitbook/assets/7-segment.png)

The anodes of 7 LEDs are connected together, and you could notice there's a pin for power connection. If you want A to be illuminated, you need to set the pin to low voltage.

The way you set these LEDs decides how the display looks like. The numbers from 0 to 9 are shown as follows. For example, to display the number 3, you will turn on A, B, C, D, G, and turn off E, F. Besides these numbers, you could display many other things, like characters.

![](../../.gitbook/assets/numbers.png)

## Code Analysis

In this mission, you will not write all code in one file and separate it into two parts. This makes your code more clear and organized.

* The file `SevenSegment.swift` sets the 7-segment display and provides some easy-to-use functionalities.
* The file `main.swift` is to show the digit on the 7-segment display.

### `SevenSegment.swift`

Let's look at this file in detail.

```swift
import SwiftIO
import SwiftIOBoard
```

As always, import the necessary libraries. 

```swift
final class SevenSegment {
    ...
}
```

Then you will write the code in a class named `SevenSegment`. Briefly speaking, the **class** contains a block of code that allows you to create many instances with similar characteristics. It usually has methods \(function in a class\) and properties \(constant or variable in a class\).

The class normally could be inherited, and with the keyword `final`, it cannot be inherited any longer.

_Note: the class is a reference type, so no matter how many instances you create, they actually point to the same one. If you change any of the instances, all will be changed with it. This is why the class is always used in your projects. Since the corresponding hardware is unique, any set will cause directly the change of the hardware._

```swift
static let a = DigitalOut(Id.D8)
static let b = DigitalOut(Id.D7)
static let c = DigitalOut(Id.D6)
static let d = DigitalOut(Id.D5)
static let e = DigitalOut(Id.D4)
static let f = DigitalOut(Id.D2)
static let g = DigitalOut(Id.D3)
```

Initialize the 7 digital pins. To better identify the segments later, you name these pins as a, b, c...  The pins should just match the segments, or the final display will go wrong. 

The keyword `static` make these properties belong to the class, rather than to any instance of the class.

```swift
let leds = [a, b, c, d, e, f, g]
```

To simplify the code, you put them into an array, so that you could iterate them instead of dealing with them one by one manually. 

An **array** is a collection of ordered values of the same type. To access its element, you could use its index. The index starts from 0. So if you want to access `a`, it's written as `led[0]`.

```swift
let ledState: [UInt8] = [
    0b00111111, 0b00000110, 0b01011011, 0b01001111, 0b01100110, 
    0b01101101, 0b01111101, 0b00000111, 0b01111111, 0b01101111
]
```

This array contains the data to store the LED states of numbers from 0 to 9.

How does it work? There are 7 LEDs in total, so you could use a byte to represent its states. Each bit corresponds to an LED. 1 means the LED is on, 0 means off. Take the digit 0 for example, the image below shows how the data is formed:

![](../../.gitbook/assets/0.png)

You will deal with the bits from the last one, so that bit is reserved for a. To display digit 0, other segments need to be lighted except g. The first bit doesn't match any LED, and you could just leave it as 0. Then you need to tell the computer the type of this data and add `ob` to indicate it's a byte.

```swift
public func print(_ number: Int) {
    ...
}
```

After the preparation above, you are ready to set the 7-segment display.

You will create a method to show the number you pass to it. The keyword `public` is added so that you could use this method in other files.

```swift
let num = number % 10
```

Declare a constant to store the digit to be displayed. Since the 7-segment display could only display 1 digit, you use the remainder operator `%`. The number will be divided by 10 to get the remainder. For example, if the number is 45, `num` will be 5.

```swift
let value = ledState[num] 
```

The `num` then used as an index to access the elements in `ledState`. In this way, you get exact `value` that stores the states of each LED.

```swift
for i in 0..<7{
    ...
}
```

There are 7 LEDs in total, you will iterate 7 times using a `for-in` loop. Here you will use the loop with a numeric range. `..<` is the half-open range operator, which means `i` starts from 0 to 7, but doesn't include 7. 

At first, `i` equals 0. After the code inside the brackets is executed, `i` will be 1, and restarts the code, then repeat the process until all number is reached.

```swift
let state = (value >> i) & 0x01
```

This statement is to get the value of the bit. Let's look at the operators here:

* &gt;&gt;: right shift, all bits will move to the right. The bits on the right will be discarded and 0 will be added to the empty bits on the left.
* &: bitwise AND operator, it will calculate each corresponding bit of two data. Only when both two bits are 1, the result will be 1, or it will be 0.

![](../../.gitbook/assets/operation.png)

Suppose the `value` is `0b01011011`. At first, i=0, the value remains unchanged and is calculated with 0x01, so the state will be 1, which represents LED a; when i=1, the state equals the last second bit of `value`, 1, that represents LED b; and so on. 

```swift
if state == 0 {
    leds[i].write(true)
} else {
    leds[i].write(false)
}
```

You get the value of the state, that is, you know the state of the LED, so time to set the output! 

The `if-else` statement is to decide the output voltage. If the value of `state` equals 0, that LED should be off, so write `true` to turn off it. Or else, that LED will be illuminated. As iterating over each bit, the states of all LEDs will be set. 

### `main.swift`

This file is quite simple since all work related to the 7-segment has done in another file. Let's take a quick look.

Import the libraries. Then of course it's the number you would like to display. 

Create an instance of the class `SevenSegment`, so you could use its method to display the number. Then use dot syntax to access the method and pass the number to it.

Well, it's done 🥳 .

This project uses one way to organize your code, there are still other ways, you'll look into it later.

