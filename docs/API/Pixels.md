# Get and Set Pixels

If you need to plop a few pixels on the screen, but don't want to go to the hassle of initializing a sprite just for a dot, this section is for you!

Setting and getting the state of pixels can be useful for effects like snow, rain, or stars

`thumby.display.setPixel(x, y, color)` | sets pixel to `color` at `x` and `y`. Returns None, all parameters required.

* `x`
    * type: int
    * values: 0 (left) ~ 71 (right)
* `y`
    * type: int
    * values: 0 (top) ~ 39 (bottom)
* `color`
    * type: int
    * values: 0 or 1

`thumby.display.getPixel(x, y)` | gets value of pixel at `x` and `y`. Returns int (0 or 1), all parameters required.

* `x`
    * type: int
    * values: 0 (left) ~ 71 (right)
* `y`
    * type: int
    * values: 0 (top) ~ 39 (bottom)
    
---

## Example

<center>
![pixel display](/images/pixels.png)
</center>
<center>
*Five pixels located in the 4 corners and the center of the screen*
</center>

```py
import thumby

thumby.display.fill(0)
thumby.display.setPixel(0, 0, 1)
thumby.display.setPixel(71, 0, 1)
thumby.display.setPixel(0, 39, 1)
thumby.display.setPixel(71, 39, 1)
thumby.display.setPixel(36, 20, 1)
thumby.display.update()

if (thumby.display.getPixel(0, 0) == 1):
    print("Pixel 0, 0 is white") # print to shell
    
if (thumby.display.getPixel(1, 1) == 0):
    print("Pixel 1, 1 is black")
```