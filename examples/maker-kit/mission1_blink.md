# Mission1\_Blink

For our first project, let's try the "hello world" demo - Blink. 

## What you need

In this mission, you will blink the onboard RGB LED. You just need the SwiftIO board.

![](../../.gitbook/assets/swiftio%20%281%29.png)

## Example code 

You could open the code in the ![](../../.gitbook/assets/xnip2020-07-22_16-04-33.jpg) &gt; MakerKit &gt; Mission1\_Blink.

```swift
// Import the SwiftIO library to use everything in it.
import SwiftIO

// Import the board library to use the Id of the specific board.
import SwiftIOBoard

// initialize the blue LED
let led = DigitalOut(Id.BLUE)

while true {
     // The code here will run all the time.
     
     // Set Blue LED off.
     led.write(true) 
     sleep(ms: 1000) // Interval of LED blink (milliseconds).
     
     // Set Blue LED on.
     led.write(false)
     sleep(ms: 1000)
}
```

## What you'll see

As you successfully download the code, you could see the blue LED on your SwiftIO board turn off for 1s and on for 1s over and over again. 

## Onboard RGB LED

You could find RGB LED beside the download button. As you download the code, it serves as a status indicator. You could also control its color and state by setting the output voltage.

Since there are three colors, you could light any of them. If you turn on red and blue, you could notice it appears magenta. If all three are on, the LED seems to be white.

While the onboard LED is connected to 3.3V internally. If you set it to high voltage, there would actually be no current. So it will be lighted when you apply low voltage.

## Background: what is a digital signal?

The digital signal normally has two states, its value is either 1 or 0. For the SwiftIO board, 1 represents 3.3V, and 0 represents 0V. There are also other ways to express the same meaning: high or low, true or false. In this case, you will control the output voltage to turn on or off the LED.

![](../../.gitbook/assets/digital.png)

## Code analysis

`SwiftIO` consists of all the functionalities to control your board. `SwiftIOBoard` defines the corresponding pin id of the board. For the following projects, you always need to import these two libraries.

Before you set a specific pin, you need to initialize it. First, declare a constant: the keyword `let`, followed by a constant name `led`. Then make it an instance for `DigitalOut` class and initialize that pin. The built-in RGB LEDs use the id _RED, GREEN, or BLUE_. Thus the id of blue LED here is written as `Id.BLUE`.

In the dead loop `while true`, all code will run over and over again. Here, the pin outputs high voltage and then sleeps for 1 second. So in the first 1s, there is always a high voltage. Similarly, in the next 1s, the pin outputs low voltage.

## See also

\*\*\*\*[**DigitalOut**](https://swiftioapi.madmachine.io/Classes/DigitalOut.html) - this class is used to decide whether the pin output high or low voltage.

`init(_:mode:value:)` - initialize the digital output pin. The first parameter needs the `id`. It is listed in the [Id enumeration](https://swiftioapi.madmachine.io/Enums/Id.html). The parameters mode and value have already their default value.

`write(_:)` - set a specific pin to output high or low voltage. Its parameter is a boolean type: `true` or `false`. `true` corresponds to a high level and `false` corresponds to a low level.

[`sleep(ms:)`](https://swiftioapi.madmachine.io/Functions.html#/s:7SwiftIO5sleep2msySi_tF) - suspend the microcontroller's work and thus make the current state last for a certain time, measured in milliseconds.

