# <span style="color:#EA5823;font-weight:800">Example Name</span>


## <span style="color:#EA5823;font-weight:700">What you need</span>


## <span style="color:#EA5823;font-weight:700">Circuit</span>


## <span style="color:#EA5823;font-weight:700">Tips</span>


## <span style="color:#EA5823;font-weight:700">Code</span>

#### main.swift
```swift
/*
  Mission10 Humiture Sensor

  The LCD will show the temperature in Celsius. The data will be updated every second.

  The circuit:
  - Use Humiture Sensor, and connect it to I2C0 Jack.
  - Use LCD Module, and connect it to I2C0 Jack.

  created 2019
  by Orange J

  By changing the code you can display the temperature as a bar graph instead of
  a number. This example code is in the public domain. Visit madmachine.io for more info.
*/

import SwiftIO

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
let lcd = LCD16X02(i2c)
let sht = SHT3x(i2c)

while true{
    // Read and display the temperature on the LCD and update the value every 1s.

    let temp = sht.readTemperature()

    lcd.print("Temperature:",x:0,y:0)
    lcd.print(String(temp.format(1)),x: 0,y: 1)
    lcd.print(" ",x:4,y:1)
    lcd.print("C",x:5,y:1)

    sleep(ms: 1000)
}

```


#### LCD.swift
```swift
import SwiftIO

class LCD16X02 {

	private enum Command {
		static let clearDisplay: UInt8 = 0x01
    	static let returnHome: UInt8 = 0x02
    	static let entryModeSet: UInt8 = 0x04
    	static let displayControl: UInt8 = 0x08
    	static let cursorShift: UInt8 = 0x10
    	static let functionSet: UInt8 = 0x20
    	static let setCGRAMAddr: UInt8 = 0x40
    	static let setDDRAMAddr: UInt8 = 0x80
	}

	private enum EntryMode {
    	static let entryRight: UInt8 = 0x00
    	static let entryLeft: UInt8 = 0x02
    	static let entryShiftIncrement: UInt8 = 0x01
    	static let entryShiftDecrement: UInt8 = 0x00
	}

	private enum Control {
    	static let displayOn: UInt8 = 0x04
    	static let displayOff: UInt8 = 0x00
    	static let cursorOn: UInt8 = 0x02
    	static let cursorOff: UInt8 = 0x00
    	static let blinkOn: UInt8 = 0x01
    	static let blinkOff: UInt8 = 0x00
	}

	private enum Shift {
    	static let displayMove: UInt8 = 0x08
    	static let cursorMove: UInt8 = 0x00
    	static let moveRight: UInt8 = 0x04
    	static let moveLeft: UInt8 = 0x00
	}

	private enum Mode {
    	static let _8BitMode: UInt8 = 0x10
    	static let _4BitMode: UInt8 = 0x00
    	static let _2Line: UInt8 = 0x08
    	static let _1Line: UInt8 = 0x00
    	static let _5x10Dots: UInt8 = 0x04
    	static let _5x8Dots: UInt8 = 0x00
	}
    
  	let address: UInt8 = 0x3E
  

  	let i2c: I2C
  
  	var displayFunctionState: UInt8
  	var displayControlState: UInt8
  	var displayModeState: UInt8
  	var numLines: UInt8
  	var currLine: UInt8
  	
    
  	convenience init(_ i2c: I2C) {
      	self.init(i2c, 16, 2, 0)
    }
    
  	init(_ i2c: I2C, _ cols: UInt8, _ rows: UInt8, _ dotSize: UInt8) {
      	self.i2c = i2c
      
      	displayFunctionState = 0
      	displayControlState = 0
      	displayModeState = 0
      	
      	if rows > 1 {
          	displayFunctionState |= Mode._2Line
        }

      	numLines = rows
      	currLine = 0
      	
      	if dotSize != 0 && rows == 1 {
          	displayFunctionState |= Mode._5x10Dots
        }
      
      	command(Command.functionSet | displayFunctionState)
      	wait(us: 4500)
    
      	command(Command.functionSet | displayFunctionState)
      	wait(us: 150)
      
      	command(Command.functionSet | displayFunctionState)
      	command(Command.functionSet | displayFunctionState)
      
      	displayControlState = 	Control.displayOn | Control.cursorOff | Control.blinkOff
      	turnOn()
      	
      	clear()
      	
      	displayModeState = EntryMode.entryLeft | EntryMode.entryShiftDecrement
      	command(Command.entryModeSet | displayModeState)
    }
  

  
  	func turnOn() {
      	displayControlState |= Control.displayOn
      	command(Command.displayControl | displayControlState)
    }

  	func turnOff() {
      	displayControlState &= ~Control.displayOn;
      	command(Command.displayControl | displayControlState)
    }
  
  	func clear() {
      	command(Command.clearDisplay)
      	wait(us: 2000)
    }

	func home() {
		command(Command.returnHome)
		wait(us: 2000)
	}
  


  	func setCursor(_ x: UInt8, _ y: UInt8) {
      	let val: UInt8 = y == 0 ? x | 0x80 : x | 0xc0
      	command(val)
    }

	func noCursor() {
		displayControlState &= ~Control.cursorOn
		command(Command.displayControl | displayControlState)
	}

	func cursor() {
		displayControlState |= Control.cursorOn
		command(Command.displayControl | displayControlState)
	}

	func noBlink() {
		displayControlState &= ~Control.blinkOn
		command(Command.displayControl | displayControlState)
	}

	func blink() {
		displayControlState |= Control.blinkOn
		command(Command.displayControl | displayControlState)
	}
	
	func scrollLeft() {
      	command(Command.cursorShift | Shift.displayMove | Shift.moveLeft)
    }
  
  	func scrollRight() {
      	command(Command.cursorShift | Shift.displayMove | Shift.moveRight)
    }

	func leftToRight() {
		displayModeState |= EntryMode.entryLeft
		command(Command.entryModeSet | displayModeState)
	}

	func rightToLeft() {
		displayModeState &= ~EntryMode.entryLeft
		command(Command.entryModeSet | displayModeState)
	}

	func autoScroll() {
		displayModeState |= EntryMode.entryShiftIncrement
		command(Command.entryModeSet | displayModeState)
	}

	func noAutoScroll() {
		displayModeState &= ~EntryMode.entryShiftIncrement
		command(Command.entryModeSet | displayModeState)
	}

  	func command(_ value: UInt8) {
    	let data: [UInt8] = [0x80, value]
      	i2c.write(data, to: address)
    }

	func clear(_ count: UInt8, x: UInt8, y: UInt8) {
		let data: [UInt8] = [0x40, 0x20]

		setCursor(x, y)
		for _ in 1...count {
			i2c.write(data, to: address)
		}
		setCursor(x, y)
	}

    
  	func print(_ str: String) {
      	let array: [UInt8] = Array(str.utf8)
      	var data: [UInt8] = [0x40, 0]	
      
      	for item in array {
          	data[1] = UInt8(item)
          	i2c.write(data, to: address)
        }
    }

    func print(_ num: Int, x: UInt8, y: UInt8) {
        print(String(num), x: x, y: y)
    }
    
  	func print(_ str: String, x: UInt8, y: UInt8) {
      	setCursor(x, y)
      	print(str)
    }
    

}

```


#### SHT3X.swift
```swift
/// This is the library for SHT31 digital humidity and temperature Sensor. 
/// It supports I2C protocol. Refer to the datasheet for more detailed information.

import SwiftIO

class SHT3x {
	// Some common command with 16-bit data used to communicate with the sensor.
    private enum Command {
        static let readStatus: UInt16 = 0xF32D
        static let clearStatus: UInt16 = 0x3041
        static let softReset: UInt16 = 0x30A2
        static let heaterEnable: UInt16 = 0x306D
        static let heaterDisable: UInt16 = 0x3066
        // high repeatability measurement with clock stretching disabled.
        static let measurement: UInt16 = 0x2400

    }
    
    // SHT31 Default Address.
    let address: UInt8 = 0x44
	let i2c: I2C
    
    // Initialize the I2C bus and reset the sensor to prepare for the following commands.
    init(_ i2c: I2C) {
        self.i2c = i2c
        writeCommand(Command.softReset)
        sleep(ms: 10)
    }
    
	// Split the 16-bit data into two 8-bit data. 
    // Write the data to the default address of the sensor.
    func writeCommand(_ value: UInt16) {
        let array: [UInt8] = [UInt8(value >> 8), UInt8(value & 0xFF)]
        i2c.write(array, to: address)
    }
    
	// Send the command to start the measurement. The data returned will be stored in 6 bytes. 
    // The first two bytes are reserved for temperature.
    // Convert the data into a float representing the current temperature.
    func readTemperature() -> Float {
        writeCommand(Command.measurement)
        sleep(ms: 20)
        let array = i2c.read(count: 6, from: address)
        let value = UInt16(array[0]) << 8 | UInt16(array[1])
        let temp: Float = 175.0 / 65535.0 * Float(value) - 45.0
        return temp
    }
    
	// Send the command to start the measurement. The data returned will be stored in 6 bytes. 
    // The fourth and fifth bytes are reserved for humidity.
    // Convert the data into a float representing the current humidity.
    func readHumidity() -> Float {
        writeCommand(Command.measurement)
        sleep(ms: 20)
        let array = i2c.read(count: 6, from: address)
        let value = UInt16(array[3]) << 8 | UInt16(array[4])
        let humidity: Float = 100.0 * Float(value) / 65535.0
        return humidity
    }

}
```


## <span style="color:#EA5823;font-weight:700">Video</span>


## <span style="color:#EA5823;font-weight:700">See Also</span>


## <span style="color:#EA5823;font-weight:700">References</span>

---
Last revision 2020/09/10 by Johnson