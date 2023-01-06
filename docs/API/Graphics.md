
# General Graphics

### Constants

Use these screen dimension constants in place of the actual pixel dimensions of the screen to remove magic numbers from your code:

`thumby.display.width` | number of pixels that define the screen width

* type: int
* value: 72

`thumby.display.height` | number of pixels that define the screen height

* type: int
* value: 40

---

### Update Display

`thumby.display.update()` | updates screen at frames-per-second (FPS) specified by 

`thumby.display.setFPS(...)`. This function will block updates to maintain the set FPS setting. Default frame rate 0 (non-limited). Returns `None`

--- 

### Frame Per Second (FPS)

`thumby.display.setFPS(FPS)` | sets the max `FPS` used by `thumby.display.update()`. Returns None, all parameters required.

* `FPS`
    * type: float
    * values: 0 ~ integer max

Games are considered playable at above 20 fps, but 30 fps is generally accepted as a standard minimum with 60 fps as the ideal frame rate for responsiveness and fluidity of animation. 

Keep in mind - depending on how many Sprites or animations you build into your game and how efficiently you program these components - your frame rate may suffer and be less than what you set as the FPS. 

```py
import thumby

thumby.display.setFPS(60)

while(True):
    # Rest of program....
```

---

### Fill Screen Color

`thumby.display.fill(color)` | fills entire screen with `color`. Returns None

* `color`
    * type: int
    * values: 0 or 1 -- where 0 is black or an unlit pixel, and 1 is white or a lit pixel

***Note: where*** `color` ***is mentioned in the Thumby API docs,*** `color` ***refers to 0 being a black (unlit) pixel, and the value 1 refers to a white (lit) pixel.***

#### Fill Screen Example

Using this example, the hardware or emulator display will alternate between a white or black screen every second.

```py
import thumby

thumby.display.setFPS(1) # 1 frame per second

while(True):
    thumby.display.fill(1) # fill screen with white pixels
    thumby.display.update()
    
    thumby.display.fill(0) # fill screen with empty (black) pixels
    thumby.display.update()
```

---

### Screen Brightness

`thumby.display.brightness(brightness)` | sets screen to `brightness` value. Returns None, all parameters required.

* `brightness`
    * type: int
    * values: 0 (off) ~ 127 (max brightness)

#### Brightness Example

When uploaded on the Thumby hardware, this example will cycle through the full range of the brightness variable values, 0-127. 

```py
import thumby

brightness = 0
thumby.display.setFPS(30)
thumby.display.fill(1) # fill screen with white pixels

while(True):
    thumby.display.brightness(brightness)
    thumby.display.update()
    brightness += 1
    if brightness >= 127:
        brightness = 0
```