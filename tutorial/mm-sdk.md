# MM SDK

The mm-sdk contains evething you need to compile a MadMachine project, either a library or an executable.

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

Run `~/mm-cli/tools_mac/scripts/dist/mm/mm -h` command for quick help.
Run `~/mm-cli/tools_mac/scripts/dist/mm/mm init -h` command for initializing quick help.
Run `~/mm-cli/tools_mac/scripts/dist/mm/mm build -h` command for building quick help.

## Initialize a library `DemoLibrary`

```shell
cd ~
mkdir DemoLibrary
cd DemoLibrary
~/mm-cli/tools_mac/scripts/dist/mm/mm init -t lib
```

