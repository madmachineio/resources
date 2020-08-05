# MM SDK

The mm-sdk contains eveything you need to compile a MadMachine project, either a library or an executable.

A MadMachine project is structured like a SPM package. A Python script is used to build the project now and it would be replaced by Swift Package Manager in the futrue.

All the latest features would be added to this SDK first and then integrated into the MadMachine IDE.

Download the latest version [here]() depends on your operating system.

# What is inside the SDK

1. tools\_linux/tools\_mac/tools\_win:

   * Swift compilier and standard libary for ARM-Cortex M7
   * ARM-GCC compiler and binutils
   * Compiled Python scripts

2. scripts:

   * Python scripts which are used like [Swift Package Manager](https://swift.org/package-manager) temporarily

3. hal:

   * Board abstraction library based on [Zephyr]

4. Examples & Library:

   * Latest examples and libraries

# Usage(Take macOS for example)

Download and unzip the sdk to the directory `~`

Run `~/mm-sdk/tools_mac/scripts/dist/mm/mm -h` command for quick help.

Run `~/mm-sdk/tools_mac/scripts/dist/mm/mm init -h` command for initializing quick help.

Run `~/mm-sdk/tools_mac/scripts/dist/mm/mm build -h` command for building quick help.

## Initialize a library `DemoLibrary`

```shell
cd ~/mm-sdk/Library
mkdir DemoLibrary
cd DemoLibrary
~/mm-sdk/tools_mac/scripts/dist/mm/mm init -t lib
```

## Initialize an executable `DemoProgram`

```shell
cd ~
mkdir DemoProgram
cd DemoProgram
~/mm-sdk/tools_mac/scripts/dist/mm/mm init
```

## Add the `DemoLibrary` as a dependency for `DemoProgram`

1. Open the `DemoProgram.mmswift` by any text editor
2. Add `"DemoLibrary"` in the `dependecies`
3. Save and quit
4. Then you can `import DemoLibrary` in project `DemoProgram`


## Build a library

```shell
cd ~/mm-sdk/Library/DemoLibrary
~/mm-sdk/tools_mac/scripts/dist/mm/mm build --sdk ~/mm-sdk --module ~/mm-sdk/Library
```

## Build an executable

When building an project(either library or executable), the Python script would try to find the dependent libraries in the speicified directory.

If the dependent library is not builded yet, it would build the library at first. Use `--rebuild` to force rebuild all dependent libries.

```shell
cd ~/RgbBlink
~/mm-sdk/tools_mac/scripts/dist/mm/mm build --sdk ~/mm-sdk --module ~/mm-sdk/Library
```


