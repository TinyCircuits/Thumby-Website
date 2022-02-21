#Uploading sketches

With the programming environment setup, it's time to upload a sketch.

## Configuring upload parameters
* Open the Arduino IDE and ensure the follow parameters are set under `Tools`
    2. `Board: -> Raspberry Pi Pico`
    3. `Flash Size: -> 2MB no FS`
    4. `CPU Speed: -> 125MHz`
    5. `Debug Port -> Disabled`
    6. `USB Stack -> Pico SDK`
    7. `PORT:`

Leave the port blank for the first upload - it will be set later

## Uploading
1. Open the Arduino IDE
2. Open an example using `File -> Examples -> Thumby -> ThumbySimpleExample`
3. Put Thumby into BOOTSEL mode:
    1. Turn Thumby off
    2. Press and hold the down DPAD direction
    3. Turn Thumby on while continuing to hold the down DPAD direction
    4. Wait for a file explorer to pop up on the computer or for the "RPI-RP2" volume to automatically mount
    5. Click "Upload" in the top left of the IDE and wait for the "Done uploading" message above the console
    6. Select `Tools -> Port: -> XXX(Raspberry Pi Pico)` (select the port marked as a pico)

If successful, the Thumby will start showing something other than a black screen. The above process only needs to be done on the first time connecting a Thumby or if an error like "No drive to deploy" occurs.