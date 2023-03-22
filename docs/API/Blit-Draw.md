# Blit, Draw, and Sprites


`thumby.display.blit(bitmapData, x, y, width, height, key, mirrorX, mirrorY)` | draws pixels defined in `bitmapData` (VLSB) array at `x` and `y` provided the bitmap's `width` and `height` with transparent pixels defined by `key` (e.g. `key = 0` means black pixels are not drawn/are transparent) with possibility of mirroring using `mirrorX` (across x-axis) and `mirrorY` (across y-axis). Returns None, all parameters required.

* `bitmapData`
    * type: bytearray
    * values: each byte consisting of VLSB aligned data where each bit being 1 (white) or 0 (black)
* `x`
    * type: int
    * values: 0 (left) ~ 71 (right)
* `y`
    * type: int
    * values: 0 (top) ~ 39 (bottom)
* `width`
    * type: int
    * values: 0 ~ 71
* `height`
    * type: int
    * values: 0 ~ 39
* `key`
    * type: int
    * values: 0 or 1 (default: -1, both black and white pixels drawn)
* `mirrorX`
    * type: int
    * values: 0 (do not mirror) or 1 (do mirror)
* `mirrorY`
    * type: int
    * values: 0 (do not mirror) or 1 (do mirror)

--- 

## Masked bitmaps

`thumby.display.blitWithMask(bitmapData, x, y, width, height, key, mirrorX, mirrorY, maskBitmapData)` | draws pixels defined in `bitmapData` array at `x` and `y` provided the bitmap's `width` and `height` with transparent pixels defined by `key` (e.g. `key = 0` means black pixels are not drawn/are transparent) with possibility of mirroring using `mirrorX` (across x-axis) and `mirrorY` (across y-axis). On conjunction with `key`, use `maskBitmapData` to specify pixels to be transparent (provides per-pixel transparency). Returns None, all parameters required.

* `bitmapData`
    * type: bytearray
    * values: each byte consisting of VLSB aligned data where each bit being 1 (white) or 0 (black)
* `x`
    * type: int
    * values: 0 (left) ~ 71 (right)
* `y`
    * type: int
    * values: 0 (top) ~ 39 (bottom)
* `width`
    * type: int
    * values: 0 ~ 71
* `height`
    * type: int
    * values: 0 ~ 39
* `key`
    * type: int
    * values: 0 or 1 (default: -1, both black and white pixels drawn)
* `mirrorX`
    * type: int
    * values: 0 (do not mirror) or 1 (do mirror)
* `mirrorY`
    * type: int
    * values: 0 (do not mirror) or 1 (do mirror)
* `maskBitmapData`
    * type: bytearray
    * values: each byte consisting of VLSB aligned data where each bit being 1 (transparent) or 0 (not-drawn)


### blitWithMask Example

Using the bitmap of a square 16 by 16 smiley face:

<center>
<img src="../../images/smileBitmap.png" alt="16 by 16 bitmap grid displaying a white smiley face on a black background" style="width:30%;border:1px solid black">
</center>

With the mask: 

<center>
<img src="../../images/roundBitmap.png" alt="16 by 16 bitmap grid displaying a white circle with black corners shaping the round edges" style="width:30%;border:1px solid black">
</center>

An alternate mask including a nose:
<center>
<img src="../../images/roundNoseBitmap.JPG" alt="16 by 16 bitmap grid displaying a white circle with black corners shaping the round edges, with a nose in the center of the white circle drawn in black" style="width:30%;border:1px solid black">
</center>

The resulting graphic with the below code:

<center>
<img src="../../images/blitWithMask-animation.gif" alt="16 by 16 bitmap grid displaying a white circle with black corners shaping the round edges, with a nose in the center of the white circle drawn in black" style="width:30%;border:1px solid black">
</center>

In this example, using key value `0`, the original bitmap of a square black pixel smiley face is changed to be a round smiley face with a nose by using a mask bitmap to make some of the original bitmap's pixels transparent. 

```py 
import thumby

# BITMAPs: width: 16, height: 16
bitmapSmile = bytearray([0,0,0,56,56,56,0,0,0,0,56,56,56,0,0,0,
           0,0,14,24,48,96,96,96,96,96,96,48,24,14,0,0])
bitmapRound = bytearray([224,248,252,254,254,255,255,255,255,255,255,254,254,252,248,224,
           7,31,63,127,127,255,255,255,255,255,255,127,127,63,31,7])
bitmapRoundNose = bytearray([224,248,252,254,254,255,255,127,127,255,255,254,254,252,248,224,
           7,31,63,127,127,255,252,253,253,252,255,127,127,63,31,7])
           
# Variables important to load into the blitWithMask() function
height = 16
width = 16
key = 0 # 0 - black pixels are not drawn/are transparent
noMirror = 0 # use for both x and y mirror arguments
# Center the sprite using screen and bitmap dimensions and apply bob offset
xPosition = int((thumby.display.width/2) - (width/2))
yPosition = int((thumby.display.height/2) - (height/2))

thumby.display.setFPS(1)

while(1):
    # Display the blit and mask bitmaps using bitmap data, position, bitmap dimensions, mirror values, and mask key
    thumby.display.fill(1) # Fill display with white pixels
    thumby.display.blitWithMask(bitmapSmile, xPosition, yPosition, width, height, key, noMirror, noMirror, bitmapRound)
    thumby.display.update()
    
    thumby.display.fill(1) 
    thumby.display.blitWithMask(bitmapSmile, xPosition, yPosition, width, height, key, noMirror, noMirror, bitmapRoundNose)
    thumby.display.update()
```

A masked bitmap can interact with other graphics in the environment through transparency outlined by the mask bitmap, in this way, one does not need to include an entire 16 by 16 pixel square to display a round graphic that fits within the space. Here's an example of the masked bitmap and how it interacts with a line crossing its width:

<center>
<img src="../../images/lineBehind.gif" alt="Black pixel round smiley face on a white background with a black line moving behind the smiley face, the line is visible through the corners and nose where the bitmap mask exists" style="width:30%;border:1px solid black">
</center>

```py
import thumby

# BITMAPs: width: 16, height: 16
bitmapSmile = bytearray([0,0,0,56,56,56,0,0,0,0,56,56,56,0,0,0,
           0,0,14,24,48,96,96,96,96,96,96,48,24,14,0,0])
bitmapRoundNose = bytearray([224,248,252,254,254,255,255,127,127,255,255,254,254,252,248,224,
           7,31,63,127,127,255,252,253,253,252,255,127,127,63,31,7])
           
# Variables important to load into the blitWithMask() function
height = 16
width = 16
key = 0 # 0 - black pixels are not drawn/are transparent, 
noMirror = 0 # use for both x and y mirror arguments
# Center the sprite using screen and bitmap dimensions and apply bob offset
xPosition = int((thumby.display.width/2) - (width/2))
yPosition = int((thumby.display.height/2) - (height/2))

thumby.display.setFPS(4)
counter = 0

while(1):
    # Draw a line passing the width of the masked graphic to visually show masking effects
    thumby.display.fill(1) # Fill display with white pixels
    thumby.display.drawLine(xPosition + counter, yPosition - 2, xPosition + counter, yPosition + 17, 0)
    counter = counter + 1
    if counter > 15:
        counter = 0
        
    # Display the blit and mask bitmaps using bitmap data, position, bitmap dimensions, mirror values, and mask key
    thumby.display.blitWithMask(bitmapSmile, xPosition, yPosition, width, height, key, noMirror, noMirror, bitmapRoundNose)
    thumby.display.update()
```

Check out the <a href="https://en.wikipedia.org/wiki/Mask_(computing)#Image_masks" alt="Wikipedia article for masks in reference to computing" target="_blank">**wiki for image masks**</a> for more general information on how masks work!

---

## Draw Sprite

`thumby.display.drawSprite(sprite)` | draw `sprite` to screen using its internal properties (position, dimensions, etc). Returns none, all parameters required.

* `sprite`
    * type: Sprite (`thumby.Sprite`)

---



`thumby.display.drawSpriteWithMask(sprite, maskSprite)` | draws `sprite` to screen using internal properties for position and size with per-pixel transparency provided by `maskSprite`. Returns none, all parameters required.

* `sprite`
    * type: Sprite (`thumby.Sprite`)
* `maskSprite`
    * type: Sprite (`thumby.Sprite`) (pixels set to 1 are transparent, while 0 pixels are not drawn)