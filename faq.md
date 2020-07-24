# FAQ

## Can't install the IDE on Win10

Windows may not recognize the IDE and there might be some problems when you install it. Windows Defender will pop up with a warning message.

![](.gitbook/assets/windows-protected-your-pc-2.png)

First, click on the "**More info"**.

Then more info will appear. Click "**Run anyway**".

## Can't open IDE on Mac

When you want to open the IDE, a new window appears:

![](.gitbook/assets/xnip2020-07-24_15-02-58.jpg)

👇 Here comes the solution:

* click **OK**.
* select ![](https://help.apple.com/assets/5EF110D6680CE23B38350954/5EF110E3680CE23B3835095C/en_GB/e043ddf1a45711e13f0b30612db65e21.png) &gt; **System Preferences**
* open the **Security & Privacy** Preferences pane
* select the **General** tab

![](.gitbook/assets/xnip2020-07-24_15-05-19.jpg)

* click the 🔒 icon
* enter your **Password**
* click **Unlock**

![](.gitbook/assets/xnip2020-07-24_15-05-35.jpg)

* click **Open Anyway**

![](.gitbook/assets/xnip2020-07-24_15-06-09.jpg)

* click **Open**

![](.gitbook/assets/xnip2020-07-24_15-06-19.jpg)

Now the IDE can run normally.

![](.gitbook/assets/xnip2020-07-24_15-07-20.jpg)

## IDE can't find the USB drive

This is due to the security feature of macOS. You need to enable **Full Disk Access** for IDE.

* select **System Preferences** in ![](https://help.apple.com/assets/5EF110D6680CE23B38350954/5EF110E3680CE23B3835095C/en_GB/e043ddf1a45711e13f0b30612db65e21.png)Apple menu
* open the **Security & Privacy** Preferences pane
* select the **Privacy** tab
* click **Full Disk Access** in the left column

![](.gitbook/assets/xnip2020-07-21_17-36-32.jpg)

* click the 🔒 icon
* enter your **Password**
* click **Unlock**

![](.gitbook/assets/xnip2020-07-21_17-39-35.jpg)

* click the icon **+**

![](.gitbook/assets/xnip2020-07-21_17-44-20.jpg)

* click **Application**
* find the **MadMachine**
* click **Open**

![](.gitbook/assets/xnip2020-07-21_17-46-34.jpg)

* click **Quit Now**

![](.gitbook/assets/xnip2020-07-21_17-49-14.jpg)

Now you can try to download your project again.

## **USB driver can't be mounted**

Maybe you use a bad quality microUSB cable or third-party USB hub.

Just change it to a better one, and try again.

## **SwiftIO board reset repeatedly**

There is a maximum power limit for the USB port of your devices.

While some modules which is connected to the board may require a stronger one.

Thus, the voltage change will cause the board to reset automatically

You can try these ways:

1 ****connect the board to another port that can allows stronger power.‌

2 connect both two ports on the board to the power

3 use a power bank to supply the board

