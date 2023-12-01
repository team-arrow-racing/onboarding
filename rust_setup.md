# What you will need

A relatively new computer running Windows, macOS, or Linux.

Some kind of STM32 development board.

## Step 0: Install Drivers for STM32

The easiest way to do this is by downloading STLINK. This will install the drivers during installation. This is also useful to ensure your computer can see the board you’ve plugged in. Ensure the micro-USB cable being used is a data cable and not just a power cable.

https://www.st.com/en/development-tools/stsw-link004.html 

## Step 1: Install Visual Studio Code

This is not necessarily required, but has a lot of useful tools and features like code completion and debugging plugins.

https://code.visualstudio.com/download

## Step 2: Install Rust

Rust is the programming lanuage we use. The installer, rustup will also install cargo which is Rust’s package manager and build tool.

https://www.rust-lang.org/tools/install 

## Step 3: Add the special compilation target

You need to do this because we are developing for embedded devices which use a different architecture than our host.

```shell
rustup target add thumbv7em-none-eabihf
```


## Step 4: Install additional rust tools

These will let us flash boards.

```shell
cargo install probe-rs cargo-embed cargo-flash
```

## (optional) Step 5: Install the ARM toolchain for debugging tooling

The ARM toolchain is not very standardised across platforms, so this step is different depending on what you’re running.

### Windows

It is believed that these are already installed with the STM32 drivers from Step 0.

### macOS

Install the ARM GCC toolchain (which includes GDB) using Brew.

```shell
brew install  --cask gcc-arm-embedded
```

### Linux

The default distribution of GDB for Linux is multi-arch which means it should work out of the box.

The following command will install GDB on Ubuntu distributions if you don’t already have it.

```shell
sudo apt-get update
sudo apt-get install gdb
```

## Cortex-Debug VSCode Plugin

Aditionally you can install the Cortex-Debug plugin for Visual Studio Code to have interactive debugging inside your IDE.

https://marketplace.visualstudio.com/items?itemName=marus25.cortex-debug

Step 6: Compiling and running your first project

```shell
# Download the vehicle controller repo
git clone git@gitlab.com:team-arrow-racing/arrow-3/vehicle-controller.git
cd vehicle-controller
# Open the repo in VSCode
code ./
# Get cargo to first download packages, compile the code and then
# flash it to the device with probe-run.
cargo run
```

Got stuck?

If you have any issues along the way, the #firmware channel is a good place to get help from other team members.
