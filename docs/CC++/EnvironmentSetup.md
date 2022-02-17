This page will go through the process of installing needed software and libraries to program Thumby in Arduino C/C++. This should be doable on Windows, Linux, and Mac.

## Dependencies
A few items are needed to setup a programming environment for Thumby

1. <a href="https://www.arduino.cc/en/software" target="_blank" alt="Download the Arduino IDE for most platforms">**Arduino IDE**</a>
2. <a href="https://github.com/TinyCircuits/TinyCircuits-GraphicsBuffer-Lib" target="_blank" alt="View the GraphicsBuffer Library source and download it">**GraphicsBuffer Library**</a>
3. <a href="https://github.com/TinyCircuits/TinyCircuits-Thumby-Lib" target="_blank" alt="View the Thumby Library source and download it">**Thumby C/C++ Library**</a>
4. <a href="https://github.com/earlephilhower/arduino-pico" target="_blank" alt="View the RP2040 Arduino board package source">**Raspberry Pi Pico/RP2040 Arduino board package**</a>

### Installing the Arduino IDE
See the Arduino installation <a href="https://www.arduino.cc/en/Guide" target="_blank" alt="See how to install the Arduino IDE on your platform">**guide**</a>

### Installing the GraphicsBuffer Library
1. Visit the GraphicsBuffer Library GitHub <a href="https://github.com/TinyCircuits/TinyCircuits-GraphicsBuffer-Lib" target="_blank" alt="View the GraphicsBuffer Library source and download it">**page**</a>
2. On the GitHub page, click the green "Code" dropdown and select "Download ZIP"
3. In the Arduino IDE, click `Sketch->Include Library->Add .ZIP Library...` and then select the downloaded .zip file

### Installing the Thumby Library
1. Visit the Thumby Library GitHub <a href="https://github.com/TinyCircuits/TinyCircuits-Thumby-Lib" target="_blank" alt="View the Thumby Library source and download it">**page**</a>
2. On the GitHub page, click the green "Code" dropdown and select "Download ZIP"
3. In the Arduino IDE, click `Sketch->Include Library->Add .ZIP Library...` and then select the downloaded .zip file

See this <a href="https://docs.arduino.cc/software/ide-v1/tutorials/installing-libraries" target="_blank" alt="View the RP2040 Arduino board package source">**page**</a> for a visual step through of installing libraries through the Arduino IDE.

### Installing the RP2040 Arduino board package
Follow the instructions <a href="https://github.com/earlephilhower/arduino-pico#installing-via-arduino-boards-manager" target="_blank" alt="View the RP2040 Arduino board package source">**here**</a> to see the installation process in the Arduino IDE boards manager.

## Configuring upload parameters
* Open the Arduino IDE and ensure the follow parameters are set under `Tools`
    2. `Board: -> Raspberry Pi Pico`
    3. `Flash Size: -> 2MB no FS`
    4. `CPU Speed: -> 125MHz`
    5. `Debug Port -> Disabled`
    6. `USB Stack -> Pico SDK`
    7. `PORT:`

Leave the port blank for the first upload - it will be set later