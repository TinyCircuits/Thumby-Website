# Button Input

There are 6 total individual buttons available to use as input for Thumby. 4 directional buttions for up, down, left, and right, and there are two action buttons. Multiple buttons can be combined to add more button actions to gameplay.

### Objects

* `thumby.buttonA` | for accessing A button (right red button)
* `thumby.buttonB` | for accessing B button (left red button)
* `thumby.buttonU` | for accessing up direction on DPAD
* `thumby.buttonD` | for accessing down direction on DPAD
* `thumby.buttonL` | for accessing left direction on DPAD
* `thumby.buttonR` | for accessing right direction on DPAD

### Functions
* `thumby.buttonX.pressed()` 
    * Returns True if `thumby.buttonX` is currently pressed
    * Returns False otherwise (replace `buttonX` by any of the above button objects)
* `thumby.buttonX.justPressed()`
    * Returns True if the last button pressed was `thumby.buttonX`
    * Returns False otherwise (replace `buttonX` by any of the above button objects)


### Example with Graphics

This example uses an instance of a Sprite object and some rectangles to create the outline of the direction-pad button, and the two action button outlines, respectively. When each button is pressed, the corresponding letter of the button is printed inside the button outlines to show a nice visual display triggered by buttons being pressed. You can press each button individually, or all of the buttons at once for this example. 

<center>
![Bouncing ball](/images/button-display.gif)
</center>
<center>
*Background, and small Sprite examples!*
</center>

```py
# Written by: Laveréna Wienclaw, Feb 2022
import thumby

# BITMAP: width: 21, height: 21
dpadMap = bytearray([224,32,32,32,32,63,1,1,1,1,1,1,1,1,1,63,32,32,32,32,224,
            255,128,128,128,128,128,0,0,0,0,0,0,0,0,0,128,128,128,128,128,255,
            0,0,0,0,0,31,16,16,16,16,16,16,16,16,16,31,0,0,0,0,0])

# Make a sprite object using bytearray (a path to binary file from 'IMPORT SPRITE' is also valid)
dpadSpr = thumby.Sprite(21, 21, dpadMap, 10, 10)

# Begin main game loop that runs for the course of the game
while(True):
    thumby.display.fill(0) # Fill canvas to black
    
    # draw the dpad sprite first so the text is placed over it
    thumby.display.drawSprite(dpadSpr) 
    
    # Up, down, left, right, and action a, and b button movement logic
    if thumby.buttonU.pressed():
        thumby.display.drawText("U", 18, 12, 1)
    if thumby.buttonD.pressed():
        thumby.display.drawText("D", 18, 22, 1)
    
    if thumby.buttonL.pressed():
        thumby.display.drawText("L", 12, 17, 1)
    if thumby.buttonR.pressed():
        thumby.display.drawText("R", 24, 17, 1)
        
    if thumby.buttonA.pressed():
        thumby.display.drawText("A", 52, 12, 1)
    if thumby.buttonB.pressed():
        thumby.display.drawText("B", 42, 22, 1)
    
    # Display the bitmap using bitmap data, position, and bitmap dimensions
    thumby.display.drawRectangle(50, 10, 9, 11, 1)  # a
    thumby.display.drawRectangle(40, 20, 9, 11, 1)  # b
    thumby.display.update()

```

