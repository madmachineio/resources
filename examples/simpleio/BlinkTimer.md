# <span style="color:#EA5823;font-weight:800">BlinkTimer</span>

![](../../.gitbook/assets/BlinkTimer01.gif)

This example shows how to use the timer and interrupt mechanism on the SwiftIO Board to make the on-board Red LED blinking at a constant frequency.

## <span style="color:#EA5823;font-weight:700">What you need</span>

- SwiftIO board

### Kits that meet the experimental conditions: 
- [Maker Kit for SwiftIO](https://www.madmachine.io/product-page/maker-kit-for-swiftio)

## <span style="color:#EA5823;font-weight:700">Circuit</span>
![](../../.gitbook/assets/BlinkTimer/01.png)

Only the SwiftIO Board itself is required here. No extra shenanigans.

## <span style="color:#EA5823;font-weight:700">Code</span>

```swift
/// Change the LED state every second by setting the interrupt.

/// Import the library to enable the relevant classes and functions.
import SwiftIO

/// Initialize the red onboard LED and a timer to set interrupt.
let red = DigitalOut(Id.GREEN)
let timer = Timer()

/// Raise the interrupt to turn on or off the LED every second.
timer.setInterrupt(ms: 1000) {
    red.toggle()
}

while true {

}
```

## <span style="color:#EA5823;font-weight:700">Instruction</span>

### What is a timer?

Timer is precisely a part of the hardware on the SwiftIO board. It works just like an alarm clock, and it can be programmed by manipulation of some registers. You can set some parameters for the timer, which makes it trigger every so often.

<!--
什么是计时器？
计时器或更确切地说是计时器/计数器是SwiftIO板上内置的一块硬件。它就像一个闹钟，定时器可以通过一些特殊的寄存器进行编程。您可以为计时器预置参数，即可由固定时间间隔进行触发。
-->

### What is an interrupt?

An interrupt ensures that the processor responds quickly to some important events. When a interrupt signal is detected, the processor will stop its current job and perform some other codes, so that the board can react to the external signals quickly and accordingly.

<!--
什么是中断？
中断的工作是确保处理器对重要事件做出快速响应。当检测到某个信号时，中断会中断处理器正在执行的任何操作，并执行一些代码，以对馈入SwiftIO板的任何外部刺激做出反应。
-->

### What happens in this example?

In this case, the timer is set to be the internal interrupt source, which is done by using `.setInterrupt(ms: parameter)`, a method in the `Timer()` class. The parameter indicates that the timer triggers an interrupt every 1000 ms, or, every 1 s. 

The `.toggle()` (as the name implies) method of DigitalOut class means that the output level of the specific pin is inverted. In this case, the red LED light will be switch on or off when the interruption happens.

You can also use the `sleep(ms: )` function to achieve the same effect. But this function will make the processor unresponsive during this period of time, making it not do anything. Therefore, the advantage of using `interrupt` is that the processor can still do other things between two toggles. 

<!--
这个例子中，将定时器设置为内部的中断源，这就是Timer()对象的 setInterrupt（ms:1000）方法，传入的参数表示这个定时器每隔1000ms即1s触发中断。DigitalOut的toggle()（顾名思义）方法表示输出电平进行翻转。

用这种方法实现的定时重复事件（点亮、熄灭LED）的优点在于不必使用sleep(ms:)方法，不会占用SwiftIO控制器，在这期间它可以去做其它事情。

-->


## <span style="color:#EA5823;font-weight:700">See Also</span>
- [Timer()](https://swiftioapi.madmachine.io/Classes/Timer.html) - The Timer class is used to set the occasion to raise the interrupt.
- [toggle()](https://swiftioapi.madmachine.io/Classes/DigitalOut.html#/s:7SwiftIO10DigitalOutC6toggleyyF) - To alternate between two voltage level.

## <span style="color:#EA5823;font-weight:700">References</span>

- [wiki: Timer](https://en.wikipedia.org/wiki/Timer)
- [wiki: Interrupt](https://en.wikipedia.org/wiki/Interrupt)
- [wiki: toggle](https://en.wiktionary.org/wiki/toggle)


---
Last Edit 2020/09/13 by Martin

> Changes on instructions. 
>
> Spelling corrections

Last revision 2020/09/04 by Johnson