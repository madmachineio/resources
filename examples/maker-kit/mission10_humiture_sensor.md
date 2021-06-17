# Mission10\_Humiture\_Sensor \(editing\)

## What you need

![](../../.gitbook/assets/asset-39.png)

## Circuit

### Circuit diagram

![](../../.gitbook/assets/humiture.png)

### Build your circuit





## Example code

You could open the code in the ![](../../.gitbook/assets/xnip2020-07-22_16-04-33.jpg) &gt; MakerKit &gt; Mission10\_Humiture\_Sensor.

```swift
// Import the SwiftIO library to use everything in it.
import SwiftIO

// Import the board library to use the Id of the specific board.
import SwiftIOBoard

// Get a number with one decimal place.
extension Float {
    func format(_ f: Int) -> Float {
        guard f > 0 else {return self}
        var mul = 10
        for _ in 1..<f {
            mul *= 10
        }
        let data = Int(self * Float(mul))
        return Float(data) / Float(mul)
    }
}

// Initialize the LCD and sensor to use the I2C communication.
let i2c = I2C(Id.I2C0)
let lcd = LCD1602(i2c)
let sht = SHT3x(i2c)

while true{
    // Read and display the temperature on the LCD and update the value every 1s.
    let temp = sht.readCelsius()

    lcd.write(x:0, y:0, "Temperature:")
    lcd.write(x: 0, y: 1, String(temp.format(1)))
    lcd.write(x:4, y:1, " ")
    lcd.write(x:5, y:1, "C")

    sleep(ms: 1000)
}

```

## What you'll see

## Humiture sensor





## Code Analysis



## See also



