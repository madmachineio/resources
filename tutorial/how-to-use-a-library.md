# How to use a library

Each time you deal with some devices, there are so many works to do - refer to its datasheet to get familiar with it, send a lot of data to communicate with it. It's really tiring. 

However, libraries will let you get rid of all these dirty works and make your coding process easier. You just need to import it and write a few lines of code with the preset methods. 

Now you may find there are few available libraries😔, we will create more as package management is done.

## Install a library

Now let's learn how to install a library.

1.First, download the library from Github. ‌ I'll take the library MadSHT3x for example.

2.Enter the MadSHT3x. Select **Code** &gt; **Download ZIP**.

![](../.gitbook/assets/1.jpg)

3.Unzip the package and move the folder to **Documents** &gt; **MadMachine** &gt; **Library**.

![](../.gitbook/assets/2.jpg)

## Explore the examples in the library

There will be some examples in the library files downloaded from Github. Let's use it first.

1.Open the IDE. Then create a new project. If you have opened the IDE, please make sure to close it and open it again. 

![](../.gitbook/assets/1%20%281%29.jpg)

2.Click the ![](../.gitbook/assets/xnip2020-07-22_16-04-33.jpg) button on the bottom. You would notice the example MadSHT3x appears in the **Library** folder if you have successfully installed the library.

![](../.gitbook/assets/3%20%281%29.jpg)

3.Double click the file **ReadTempAndHumidity**. A new window will pop up.

![](../.gitbook/assets/3%20%282%29.jpg)

4.Build the files.

![](../.gitbook/assets/4%20%281%29.jpg)

## Use library in your project

Now you are going to know how to apply new libraries in your own project.

1.Open the IDE. Create a new project.

![](../.gitbook/assets/3.jpg)

2.In the file `.mmp`, add the library MadSHT3x in **dependencies**. ‌

![](../.gitbook/assets/4.jpg)

3.Import the two libraries in `main.swift` file.

![](../.gitbook/assets/5.jpg)

‌ Now you can use everything in the library to create your project.

