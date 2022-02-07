## Sprite


`thumby.Sprite(width, height, bitmapData, x, y, key, mirrorX, mirrorY)` | initialize sprite object with fixed frame `width` and `height` for frames in `bitmapData`, positioned at `x` and `y`, and rendered to screen mirrored depending on, `mirrorX` and `mirrorY`. Transparent pixels are defined by `key` (e.g. `key = 0` means black pixels are not drawn/are transparent). Returns Sprite.

* `width`
    * type: int
    * values: 0 ~ integer max
* `height`
    * type: int
    * values: 0 ~ integer max
* `bitmapData`
    * type: list or string
    * values: bytearray of VLSB data or string (128 ASCII character at max 256 characters long) pointing to binary file location of pixel data
* `x`
    * type: int
    * values: 0 (left) ~ 71 (right) (default: 0)
* `y`
    * type: int
    * values: 0 (top) ~ 39 (bottom) (default: 0)
* `key`
    * type: int
    * values: 0 or 1 (default: -1, both black and white pixels drawn)
* `mirrorX`
    * type: int
    * values: 0 (do not mirror) or 1 (do mirror) (default: 0)
* `mirrorY`
    * type: int
    * values: 0 (do not mirror) or 1 (do mirror) (default: 0)

---

`Sprite.getFrame()` | gets the current frame index of the sprite animation. Return int, automatically returns wrapped index if index greater than max number of frames.

---

`Sprite.setFrame(frame)` | sets the current `frame` index of the sprite animation. Needs to be used manually to progress animation, framerate handled by `thumby.display.update()`. Returns none, all parameters required.

* `frame`
    * type: int
    * values: 0 ~ overflow (values larger than the number of frames get wrapped)

---

### Sprite example: Shapes & More!

The Thumby API has a builtin function for drawing rectangles, but there's nothing built in for other shapes. To draw other shapes like triangles or circles, you can use the Sprite class! You can draw any shape or object or even scenery using the Sprite class.

<center>
![Bouncing ball](/images/lots-of-Sprites.png)
</center>
<center>
*Background, and small Sprite examples!*
</center>

```py
# Written by: Laveréna Wienclaw, Feb 2022
import thumby

# Small bitmaps: width: 8, height: 8
triangleMap = bytearray([128,192,160,144,136,132,130,255])
circleMap = bytearray([60,66,129,129,129,129,66,60])
cactusMap = bytearray([0,24,16,255,255,4,6,0])
shipMap = bytearray([195,231,189,219,102,36,60,24])
meteorMap = bytearray([28,122,126,223,175,223,118,60])
catMap = bytearray([28,242,242,48,48,254,252,14])
# Long bitmaps for background: width: 72, height: 14
moonStarsMap = bytearray([0,4,10,4,224,240,248,248,24,8,0,0,0,0,0,0,0,4,0,0,0,0,0,0,0,8,0,0,0,0,0,0,2,0,0,0,0,0,64,160,64,0,0,0,0,0,8,0,0,0,64,0,0,0,2,0,0,0,16,40,16,0,0,0,0,0,0,0,4,0,0,0,
            0,8,0,0,0,1,3,3,3,2,0,32,0,0,0,0,0,0,1,0,0,32,0,0,0,0,0,0,0,0,0,17,0,0,0,0,0,0,0,0,0,0,0,0,0,16,40,16,0,0,0,0,0,0,0,0,0,8,0,0,0,0,0,0,0,16,0,0,0,0,0,0])
grassMap = bytearray([240,192,0,128,0,0,240,128,192,176,96,128,128,224,128,0,224,128,128,192,128,0,240,0,128,224,128,0,128,224,192,0,192,192,0,224,192,96,128,0,240,0,128,0,192,0,192,0,128,224,128,192,112,208,128,112,160,0,0,96,192,120,192,128,192,128,192,240,224,32,252,112,
            61,62,63,61,62,63,62,59,63,62,63,61,63,63,61,61,62,63,63,63,63,62,63,63,63,62,62,63,61,63,63,63,61,63,59,63,59,54,61,63,56,63,59,63,63,63,63,62,61,62,63,63,62,62,63,63,57,63,56,63,61,62,63,63,63,61,62,58,57,63,63,63])

# Create Sprite objects using bitmaps
triangleSpr = thumby.Sprite(8, 8, triangleMap, 6, 16)
circleSpr = thumby.Sprite(8, 8, circleMap, 16, 16)
cactusSpr = thumby.Sprite(8, 8, cactusMap, 26, 16)
shipSpr = thumby.Sprite(8, 8, shipMap, 36, 16)
meteorSpr = thumby.Sprite(8, 8, meteorMap, 46, 16)
catSpr = thumby.Sprite(8, 8, catMap, 56, 16)
moonSpr = thumby.Sprite(72, 14, moonStarsMap, 0, 0)
grassSpr = thumby.Sprite(72, 14, grassMap, 0, 26)

thumby.display.fill(0) # Fill canvas to black

# Draw sprites and update display
thumby.display.drawSprite(triangleSpr)
thumby.display.drawSprite(circleSpr)
thumby.display.drawSprite(cactusSpr)
thumby.display.drawSprite(shipSpr)
thumby.display.drawSprite(meteorSpr)
thumby.display.drawSprite(catSpr)
thumby.display.drawSprite(moonSpr)
thumby.display.drawSprite(grassSpr)

thumby.display.update()
```