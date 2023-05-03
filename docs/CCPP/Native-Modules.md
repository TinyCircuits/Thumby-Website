#Native Modules

Games, applications, and libraries can be built in C and then used with the Thumby MicroPython library! MicroPython provides a way to compile and link C into a `.mpy` module which can be imported into a Python script like any other module. More details are <a href="MicroPython native module documentation" target="_blank" alt="Download the Arduino IDE for most platforms">**here**</a> but this page will go through the process step-by-step.

This guide assumes you are using the Windows 10 operating system. If you're on Linux, this guide will also help you but you'll want to skip the WSL setup portion.

*Warning*: This is an advanced guide for people who are comfortable with C, the command-line, and Linux (even if using Windows) 

## Windows 10 WSL setup
It is easiest to build MicroPython and Micropython C modules on Linux, so to make this work in Windows we'll use the Windows Subsystem for Linux (WSL). You can follow the official Microsoft guide <a href="https://docs.microsoft.com/en-us/windows/wsl/setup/environment#get-started" target="_blank" alt="Getting started document">**here**</a> or the condensed steps below.

1. Open PowerShell using the Windows start menu
2. Setup the Ubuntu Subsystem using the command: `wsl --install`
3. Start the subsystem: `wsl`
4. Choose a username
5. Choose a password
6. Update the subsystem's packages: `sudo apt update && sudo apt upgrade`

## Setting up the build environment
1. Install build tools (taken from section 2.2 of the <a href="https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf" target="_blank" alt="Getting started document">**Getting Started with Raspberry Pi Pico**</a>) document: `sudo apt install cmake gcc-arm-none-eabi libnewlib-arm-none-eabi build-essential`
2. Install Python 3 and pip: `sudo apt install python3 pip`
3. Install another build tool: `python3 -m pip install 'pyelftools>=0.25'`
4. Move to a directory where the `micropython` directory should stay: `cd Desktop`
5. Clone the TinyCircuits MicroPython fork: `git clone https://github.com/TinyCircuits/micropython.git`
6. Move to the cloned directory: `cd micropython`
7. Move to the rp2040 port: `cd ports/rp2`
8. Make a new directory for your C module: `mkdir mymodule`
9. Move to the new directory: `cd mymodule`

## Designing a module
A minimal example can be found in the MicroPython documentation <a href="https://docs.micropython.org/en/latest/develop/natmod.html#minimal-example" target="_blank" alt="MicroPython minimal example">**here**</a>. The process of designing a more complex module using an external C library is shown below.

<a href="https://gitlab.com/drummyfish/small3dlib" target="_blank" alt="MicroPython minimal example">**small3dlib**</a> is a flexible and compact C library to render 3D graphics. We'll create a native module to make it useable in MicroPython and on Thumby.

1. `cd ports/rp2`
2. `git clone https://gitlab.com/drummyfish/small3dlib.git`
3. `cd small3dlib`
