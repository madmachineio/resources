# Getting Started

Get your SwiftIO board? Where do I start? Let's start with the hello world project - LED blink. 

Here is a simple instruction manual about the whole process:

![](.gitbook/assets/212.png)

Well, please follow us step-by-step. You will know how to run your first project on your SwiftIO board.

## **Step 1: Download and install the MadMachine IDE**

MadMachine IDE is what you use to write and download the code. It provides you with an easy way to code, and you no longer need to face all the complicated stuff. 

If you're an experienced programmer, you may edit your code wherever you like, and then just use the IDE to download your code to the board.

The IDE is now available on Windows and Mac. You'll find the latest software package [here](https://github.com/madmachineio/MadMachineIDERelease/releases). Select the appropriate version according to your operating system. 

Double click the downloaded file and follow the installation instructions.

If you meet with any problem, please refer to [FAQ](faq.md).

When you first open up the MadMachine IDE, it appears like this:

![](.gitbook/assets/ide.jpg)

Now you just begin to play with it, it's empty on the right side. As you try more projects and explore more, it will be filled with all kinds of projects.

## **Step 2: Coding in the IDE**

It's time to start your first project in the IDE. It's pretty simple.

First of all, create a new project.

![](.gitbook/assets/create.jpg)

We call it "Blink". Just try to choose a descriptive name as you like for the project.

Then click **Create**.

![](.gitbook/assets/blink.jpg)

Here is a simple example for your reference:

```swift
import SwiftIO

let green = DigitalOut(Id.GREEN)
​
while true {
    green.write(true)
    sleep(ms: 1000)
    green.write(false)
    sleep(ms: 1000)
}
```

You could also see some example codes in the IDE by clicking on the button ![](.gitbook/assets/xnip2020-07-22_16-04-33.jpg) on the bottom left corner. 

![](.gitbook/assets/xnip2020-10-29_12-55-53.jpg)

Choose **GettingStarted** &gt; **Blink**. The code will show up in a new window.

![](.gitbook/assets/code.jpg)

## **Step 3: Prepare SD card and confirm USB connection**

**Make sure** that you have inserted an SD card into the slot.

Connect your SwiftIO board to your computer through the **Download port** using a Micro-USB cable.

Press the **DOWNLOAD** button. SwiftIO will mount the SD card as a USB Flash Drive on your computer.

_**Note:** Bad quality USB cable or some third-party USB hub may cause connection failure._

The onboard RGB LED will show the current status of the USB connection:

| LED State | RED | GREEN | BLUE |
| :--- | :--- | :--- | :--- |
| On | USB communication failed | USB connection established | - |
| Slow flashing | Fail to verify file `swiftio.bin` | - | - |
| Fast flashing | Fail to open file `swiftio.bin` | Detecting USB connection | Detecting SD card |

## **Step 4: Build your code and download it to the board**

Once the SD card is mounted successfully, an icon ![](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAkACQAAD/4QB0RXhpZgAATU0AKgAAAAgABAEaAAUAAAABAAAAPgEbAAUAAAABAAAARgEoAAMAAAABAAIAAIdpAAQAAAABAAAATgAAAAAAAACQAAAAAQAAAJAAAAABAAKgAgAEAAAAAQAAACigAwAEAAAAAQAAACYAAAAA/+0AOFBob3Rvc2hvcCAzLjAAOEJJTQQEAAAAAAAAOEJJTQQlAAAAAAAQ1B2M2Y8AsgTpgAmY7PhCfv/iD6xJQ0NfUFJPRklMRQABAQAAD5xhcHBsAhAAAG1udHJSR0IgWFlaIAfkAAMAEwAFACYACmFjc3BBUFBMAAAAAEFQUEwAAAAAAAAAAAAAAAAAAAAAAAD21gABAAAAANMtYXBwbAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAEWRlc2MAAAFQAAAAYmRzY20AAAG0AAAEgmNwcnQAAAY4AAAAI3d0cHQAAAZcAAAAFHJYWVoAAAZwAAAAFGdYWVoAAAaEAAAAFGJYWVoAAAaYAAAAFHJUUkMAAAasAAAIDGFhcmcAAA64AAAAIHZjZ3QAAA7YAAAAMG5kaW4AAA8IAAAAPmNoYWQAAA9IAAAALG1tb2QAAA90AAAAKGJUUkMAAAasAAAIDGdUUkMAAAasAAAIDGFhYmcAAA64AAAAIGFhZ2cAAA64AAAAIGRlc2MAAAAAAAAACERpc3BsYXkAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABtbHVjAAAAAAAAACYAAAAMaHJIUgAAABQAAAHYa29LUgAAAAwAAAHsbmJOTwAAABIAAAH4aWQAAAAAABIAAAIKaHVIVQAAABQAAAIcY3NDWgAAABYAAAIwZGFESwAAABwAAAJGbmxOTAAAABYAAAJiZmlGSQAAABAAAAJ4aXRJVAAAABQAAAKIZXNFUwAAABIAAAKccm9STwAAABIAAAKcZnJDQQAAABYAAAKuYXIAAAAAABQAAALEdWtVQQAAABwAAALYaGVJTAAAABYAAAL0emhUVwAAAAoAAAMKdmlWTgAAAA4AAAMUc2tTSwAAABYAAAMiemhDTgAAAAoAAAMKcnVSVQAAACQAAAM4ZW5HQgAAABQAAANcZnJGUgAAABYAAANwbXMAAAAAABIAAAOGaGlJTgAAABIAAAOYdGhUSAAAAAwAAAOqY2FFUwAAABgAAAO2ZW5BVQAAABQAAANcZXNYTAAAABIAAAKcZGVERQAAABAAAAPOZW5VUwAAABIAAAPecHRCUgAAABgAAAPwcGxQTAAAABIAAAQIZWxHUgAAACIAAAQac3ZTRQAAABAAAAQ8dHJUUgAAABQAAARMcHRQVAAAABYAAARgamFKUAAAAAwAAAR2AEwAQwBEACAAdQAgAGIAbwBqAGnO7LfsACAATABDAEQARgBhAHIAZwBlAC0ATABDAEQATABDAEQAIABXAGEAcgBuAGEAUwB6AO0AbgBlAHMAIABMAEMARABCAGEAcgBlAHYAbgD9ACAATABDAEQATABDAEQALQBmAGEAcgB2AGUAcwBrAOYAcgBtAEsAbABlAHUAcgBlAG4ALQBMAEMARABWAOQAcgBpAC0ATABDAEQATABDAEQAIABjAG8AbABvAHIAaQBMAEMARAAgAGMAbwBsAG8AcgBBAEMATAAgAGMAbwB1AGwAZQB1AHIgDwBMAEMARAAgBkUGRAZIBkYGKQQaBD4EOwRMBD4EQAQ+BDIEOAQ5ACAATABDAEQgDwBMAEMARAAgBeYF0QXiBdUF4AXZX2mCcgBMAEMARABMAEMARAAgAE0A4AB1AEYAYQByAGUAYgBuAP0AIABMAEMARAQmBDIENQRCBD0EPgQ5ACAEFgQaAC0ENAQ4BEEEPwQ7BDUEOQBDAG8AbABvAHUAcgAgAEwAQwBEAEwAQwBEACAAYwBvAHUAbABlAHUAcgBXAGEAcgBuAGEAIABMAEMARAkwCQIJFwlACSgAIABMAEMARABMAEMARAAgDioONQBMAEMARAAgAGUAbgAgAGMAbwBsAG8AcgBGAGEAcgBiAC0ATABDAEQAQwBvAGwAbwByACAATABDAEQATABDAEQAIABDAG8AbABvAHIAaQBkAG8ASwBvAGwAbwByACAATABDAEQDiAOzA8cDwQPJA7wDtwAgA78DuAPMA70DtwAgAEwAQwBEAEYA5AByAGcALQBMAEMARABSAGUAbgBrAGwAaQAgAEwAQwBEAEwAQwBEACAAYQAgAEMAbwByAGUAczCrMOkw/ABMAEMARAAAdGV4dAAAAABDb3B5cmlnaHQgQXBwbGUgSW5jLiwgMjAyMAAAWFlaIAAAAAAAAPMWAAEAAAABFspYWVogAAAAAAAAgo0AAD00////vFhZWiAAAAAAAABMDwAAtFQAAArjWFlaIAAAAAAAACg6AAAOeAAAyI5jdXJ2AAAAAAAABAAAAAAFAAoADwAUABkAHgAjACgALQAyADYAOwBAAEUASgBPAFQAWQBeAGMAaABtAHIAdwB8AIEAhgCLAJAAlQCaAJ8AowCoAK0AsgC3ALwAwQDGAMsA0ADVANsA4ADlAOsA8AD2APsBAQEHAQ0BEwEZAR8BJQErATIBOAE+AUUBTAFSAVkBYAFnAW4BdQF8AYMBiwGSAZoBoQGpAbEBuQHBAckB0QHZAeEB6QHyAfoCAwIMAhQCHQImAi8COAJBAksCVAJdAmcCcQJ6AoQCjgKYAqICrAK2AsECywLVAuAC6wL1AwADCwMWAyEDLQM4A0MDTwNaA2YDcgN+A4oDlgOiA64DugPHA9MD4APsA/kEBgQTBCAELQQ7BEgEVQRjBHEEfgSMBJoEqAS2BMQE0wThBPAE/gUNBRwFKwU6BUkFWAVnBXcFhgWWBaYFtQXFBdUF5QX2BgYGFgYnBjcGSAZZBmoGewaMBp0GrwbABtEG4wb1BwcHGQcrBz0HTwdhB3QHhgeZB6wHvwfSB+UH+AgLCB8IMghGCFoIbgiCCJYIqgi+CNII5wj7CRAJJQk6CU8JZAl5CY8JpAm6Cc8J5Qn7ChEKJwo9ClQKagqBCpgKrgrFCtwK8wsLCyILOQtRC2kLgAuYC7ALyAvhC/kMEgwqDEMMXAx1DI4MpwzADNkM8w0NDSYNQA1aDXQNjg2pDcMN3g34DhMOLg5JDmQOfw6bDrYO0g7uDwkPJQ9BD14Peg+WD7MPzw/sEAkQJhBDEGEQfhCbELkQ1xD1ERMRMRFPEW0RjBGqEckR6BIHEiYSRRJkEoQSoxLDEuMTAxMjE0MTYxODE6QTxRPlFAYUJxRJFGoUixStFM4U8BUSFTQVVhV4FZsVvRXgFgMWJhZJFmwWjxayFtYW+hcdF0EXZReJF64X0hf3GBsYQBhlGIoYrxjVGPoZIBlFGWsZkRm3Gd0aBBoqGlEadxqeGsUa7BsUGzsbYxuKG7Ib2hwCHCocUhx7HKMczBz1HR4dRx1wHZkdwx3sHhYeQB5qHpQevh7pHxMfPh9pH5Qfvx/qIBUgQSBsIJggxCDwIRwhSCF1IaEhziH7IiciVSKCIq8i3SMKIzgjZiOUI8Ij8CQfJE0kfCSrJNolCSU4JWgllyXHJfcmJyZXJocmtyboJxgnSSd6J6sn3CgNKD8ocSiiKNQpBik4KWspnSnQKgIqNSpoKpsqzysCKzYraSudK9EsBSw5LG4soizXLQwtQS12Last4S4WLkwugi63Lu4vJC9aL5Evxy/+MDUwbDCkMNsxEjFKMYIxujHyMioyYzKbMtQzDTNGM38zuDPxNCs0ZTSeNNg1EzVNNYc1wjX9Njc2cjauNuk3JDdgN5w31zgUOFA4jDjIOQU5Qjl/Obw5+To2OnQ6sjrvOy07azuqO+g8JzxlPKQ84z0iPWE9oT3gPiA+YD6gPuA/IT9hP6I/4kAjQGRApkDnQSlBakGsQe5CMEJyQrVC90M6Q31DwEQDREdEikTORRJFVUWaRd5GIkZnRqtG8Ec1R3tHwEgFSEtIkUjXSR1JY0mpSfBKN0p9SsRLDEtTS5pL4kwqTHJMuk0CTUpNk03cTiVObk63TwBPSU+TT91QJ1BxULtRBlFQUZtR5lIxUnxSx1MTU19TqlP2VEJUj1TbVShVdVXCVg9WXFapVvdXRFeSV+BYL1h9WMtZGllpWbhaB1pWWqZa9VtFW5Vb5Vw1XIZc1l0nXXhdyV4aXmxevV8PX2Ffs2AFYFdgqmD8YU9homH1YklinGLwY0Njl2PrZEBklGTpZT1lkmXnZj1mkmboZz1nk2fpaD9olmjsaUNpmmnxakhqn2r3a09rp2v/bFdsr20IbWBtuW4SbmtuxG8eb3hv0XArcIZw4HE6cZVx8HJLcqZzAXNdc7h0FHRwdMx1KHWFdeF2Pnabdvh3VnezeBF4bnjMeSp5iXnnekZ6pXsEe2N7wnwhfIF84X1BfaF+AX5ifsJ/I3+Ef+WAR4CogQqBa4HNgjCCkoL0g1eDuoQdhICE44VHhauGDoZyhteHO4efiASIaYjOiTOJmYn+imSKyoswi5aL/IxjjMqNMY2Yjf+OZo7OjzaPnpAGkG6Q1pE/kaiSEZJ6kuOTTZO2lCCUipT0lV+VyZY0lp+XCpd1l+CYTJi4mSSZkJn8mmia1ZtCm6+cHJyJnPedZJ3SnkCerp8dn4uf+qBpoNihR6G2oiailqMGo3aj5qRWpMelOKWpphqmi6b9p26n4KhSqMSpN6mpqhyqj6sCq3Wr6axcrNCtRK24ri2uoa8Wr4uwALB1sOqxYLHWskuywrM4s660JbSctRO1irYBtnm28Ldot+C4WbjRuUq5wro7urW7LrunvCG8m70VvY++Cr6Evv+/er/1wHDA7MFnwePCX8Lbw1jD1MRRxM7FS8XIxkbGw8dBx7/IPci8yTrJuco4yrfLNsu2zDXMtc01zbXONs62zzfPuNA50LrRPNG+0j/SwdNE08bUSdTL1U7V0dZV1tjXXNfg2GTY6Nls2fHadtr724DcBdyK3RDdlt4c3qLfKd+v4DbgveFE4cziU+Lb42Pj6+Rz5PzlhOYN5pbnH+ep6DLovOlG6dDqW+rl63Dr++yG7RHtnO4o7rTvQO/M8Fjw5fFy8f/yjPMZ86f0NPTC9VD13vZt9vv3ivgZ+Kj5OPnH+lf65/t3/Af8mP0p/br+S/7c/23//3BhcmEAAAAAAAMAAAACZmYAAPKnAAANWQAAE9AAAApbdmNndAAAAAAAAAABAAEAAAAAAAAAAQAAAAEAAAAAAAAAAQAAAAEAAAAAAAAAAQAAbmRpbgAAAAAAAAA2AACuAAAAUgAAAEPAAACwwAAAJsAAAA2AAABQAAAAVEAAAjMzAAIzMwACMzMAAAAAAAAAAHNmMzIAAAAAAAEMcgAABfj///MdAAAHugAA/XL///ud///9pAAAA9kAAMBxbW1vZAAAAAAAAAYQAACgNAAAAADSFniAAAAAAAAAAAAAAAAAAAAAAP/AABEIACYAKAMBIgACEQEDEQH/xAAfAAABBQEBAQEBAQAAAAAAAAAAAQIDBAUGBwgJCgv/xAC1EAACAQMDAgQDBQUEBAAAAX0BAgMABBEFEiExQQYTUWEHInEUMoGRoQgjQrHBFVLR8CQzYnKCCQoWFxgZGiUmJygpKjQ1Njc4OTpDREVGR0hJSlNUVVZXWFlaY2RlZmdoaWpzdHV2d3h5eoOEhYaHiImKkpOUlZaXmJmaoqOkpaanqKmqsrO0tba3uLm6wsPExcbHyMnK0tPU1dbX2Nna4eLj5OXm5+jp6vHy8/T19vf4+fr/xAAfAQADAQEBAQEBAQEBAAAAAAAAAQIDBAUGBwgJCgv/xAC1EQACAQIEBAMEBwUEBAABAncAAQIDEQQFITEGEkFRB2FxEyIygQgUQpGhscEJIzNS8BVictEKFiQ04SXxFxgZGiYnKCkqNTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqCg4SFhoeIiYqSk5SVlpeYmZqio6Slpqeoqaqys7S1tre4ubrCw8TFxsfIycrS09TV1tfY2dri4+Tl5ufo6ery8/T19vf4+fr/2wBDAAEBAQEBAQIBAQIDAgICAwQDAwMDBAYEBAQEBAYHBgYGBgYGBwcHBwcHBwcICAgICAgJCQkJCQsLCwsLCwsLCwv/2wBDAQICAgMDAwUDAwULCAYICwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwsLCwv/3QAEAAP/2gAMAwEAAhEDEQA/AP5t/wBk39mX4jftkftF+FP2ZvhMIf7e8W3htbeS5YrDCkaNLNNIVDNsiiR5G2gttU4BPFf1p2X/AAZ33klpE+o/tDpFcFQZEj8KGRFbHIVjqiFgD0JUZ9BX4rf8G6f/ACmR+Dv/AHMP/pj1Cv8ASJ/ad+Kvi74J/DW6+JmiWD3ul6ZG8uqSW8DXdxYwKM/axbJ89zBCRm5hjKzGEs8RLoEfur1JKSjFkpH8lH/EHZ/1cV/5aP8A99qrXv8AwZ33kdpK+nftDpLcBSY0k8KGNGbHAZhqjlQT1IU49DX9FWl/tk/Dr9tn9l/x7afAPxZD4f8AiH4f0SbUI1sruO4ksbuKMzWd9BIP3d5p8siqUlC+VNGWilVH82Jdn/gk3+37p3/BR/8AY00P4+y20dh4htZX0fxFaRf6qLVbVUaQxjJIjlSRJkUklVfaSSuTk6tVK7Y7I/y6f2sv2ZfiN+xv+0X4r/Zm+LIh/t7wleC1uJLZi0MySIssM0ZYK2yWJ0kXcA21hkA8V871+2X/AAcWf8pkfjF/3L3/AKY9Pr8Ta7YO8UyD/9D84f8Ag3T/AOUyPwd/7mH/ANMeoV/oQ/tiftywfsOxL47+L/gTxBrPw8eIvceI/DduuojSpE+8NQttySxQt1S4jEiZ+VxGQpf/ADjf+CG/xl+HPwB/4KqfCP4n/FnU4dG0G2vNRsri9uXEcMD6lp11ZwtI7EKiebOm52IVVySQBX+q1b3Gnazp6XVq8d1a3UYZXQh45I3HBBGQykH6EV1Yn402iYn+XX/wU/8A2j/2Fb/9pq3/AGgv+CUer+J/B97q8N2Nctobc6Xp0T3QKyGy2yiVEuAzie3MQh5+U4YoP6Af+DRr4k+HdP8Ahx8VfgRqiXNp4ilvbLxLbxzxlI7jTpY/s3mRE/e2SphzjHzrgnnH9M8f7AP7CkXjYfEmL4MeB18QLJ5w1AeH7EXIlznzPM8ndvz/AB53e9fS+oaV4TsdSXxxqlvaQ3en2k1ut/KiLJBayFJJU804Kxs0SM4yFJRSegqZ1k48qQ7H+YX/AMHFn/KZH4xf9y9/6Y9Pr8Ta/WH/AILkfGX4c/H7/gqp8XPif8JtTh1nQbm806yt722cSQzvpunWtnM0bqSrp5sD7XUlWXBBINfk9XbT+FEM/9H+S+iiivYMwooooAKKKKAP/9k=) will appear in the status bar.

Click the **Download** ![](.gitbook/assets/xnip2020-07-22_16-00-42.jpg) button.

![](.gitbook/assets/code.png)

The IDE begins to build your project and then download it to the board if there is no error.

![](.gitbook/assets/download.png)

After a few seconds, you will see the USB flash drive is removed automatically.

And then, the onboard LED will blink✨.

Btw, you can also watch this tutorial [video](https://www.youtube.com/watch?v=frVKQXU12LQ) to get more info.

