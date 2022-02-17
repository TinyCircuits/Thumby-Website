With the programming environment setup, it's time to upload a sketch.

### Uploading
1. Open the Arduino IDE
2. Open an example using `File -> Examples -> TinyCircuits-Thumby-Lib -> ThumbyVoxelExample`
3. Put Thumby into BOOTSEL mode:
    1. Turn Thumby off
    2. Press and hold the down DPAD direction
    3. Turn Thumby on while continuing to hold the down DPAD direction
    4. See a black screen on Thumby and a file explorer pop up the computer
    5. Click "Upload" in the top left of the IDE and wait for the "Done uploading" message above the console
    6. Select `Tools -> Port: -> XXX(Raspberry Pi Pico)` (select the port marked as a pico)

If successful, the Thumby will start showing something other than a black screen. The above process only needs to be redone if this is the first time connecting a Thumby or if an error like "No drive to deploy" occurs.