# <font color=#EA5823><big>Blink</big></font>

Let's first come to an easy beginner project - blink the onboard LED. This example shows the simplest thing you can do with just a SwiftIO board to see physical output: it blinks the on-board REG LED.

## <font color=#EA5823>What you need</font>

- SwiftIO board

## <font color=#EA5823>Circuit</font>

![](../../.gitbook/assets/untitled-sketch_bb.png)
image developed using Fritzing. For more circuit examples, see the Fritzing project page

For this project, we only need the SwiftIO board.

There is a built-in RGB LED on the board. You can control it using the methods in `DigitalOut` class.

_**Note**: the onboard LED will be turned on when you apply a **low** voltage._

Just plug the board to your computer through a USB cable after you finished code.

## <font color=#EA5823>Schematic</font>

###### click the image to enlarge


## <font color=#EA5823>Code</font>

It's time for the code. Let's see how it works.You can find the example code at the bottom left corner of IDE: ![](../../.gitbook/assets/xnip2020-07-22_16-04-33.jpg) &gt; GettingStarted &gt; Blink.


```swift
// Import the library to enable everything in it, like relevant classes and methods. 
// This is first step for your coding process.
import SwiftIO

// Declare a constant. You may choose any descriptive name you like. 
// Initialize the onboard green LED. 
// The Id of onboard LED should be capitalized.
let green = DigitalOut(Id.GREEN) 

// In the dead loop, the code will run over and over again.
while true {
    // Output 3.3V to turn off the green LED.
    green.write(true)
    // Pause for a second. Or, you won't notice LED state change. 
    // During this period, the board will do nothing but just wait.
    sleep(ms: 1000)
    
    // Output 0V to turn on the green LED.
    green.write(false)
    sleep(ms: 1000)
}
```
## <font color=#EA5823>Video</font>

![](../../.gitbook/assets/gif01.gif)

## <font color=#EA5823>See Also</font>

- sleep()
- DigitalOut()

---
Last revision 2020/09/04 by Johnson