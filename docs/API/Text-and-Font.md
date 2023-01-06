# Text & Font

The Thumby screen is small at its 0.42" size, but you can still add perfectly readable text for game dialog, menus, rules, etc - you just won't be able to comfortably fit novels of text. 

--- 

### Printing Text

Text is important for communication, scores, and displaying the title of a game.

`thumby.display.drawText(string, x, y, color)` | draws `string` in `color` at `x` and `y` with font specified by `thumby.display.setFont(...)`. Returns None, all parameters required.

* `string`
    * type: str
    * values: 128 ASCII characters
* `x`
    * type: int
    * values: 0 (left) ~ 71 (right)
* `y`
    * type: int
    * values: 0 (top) ~ 39 (bottom)
* `color`
    * type: int
    * values: 0 or 1

---

## Setting Font


You can use any font you would like with the Thumby. The default font on the Thumby is 5×7, but there is also an 8×8 font included with the Thumby software under the lib/ folder. 

`thumby.display.setFont(fontFilePath, width, height, space)` | sets the `fontFilePath` pointing to binary font file with character `width`, `height`, and `space` between characters for use by `thumby.display.drawText(...)`. Returns None, all parameters required.

* `fontFilePath`
    * type: string
    * values: 128 ASCII character string up to 256 characters long ('/' separated)
* `width`:
    * type: int
    * values: 0 ~ integer max
* `height`:
    * type: int
    * values: 0 ~ integer max
* `space`:
    * type: int
    * values: 0 ~ integer max

---

### Combined Example

This example uses both the drawText() and setFont() functions to show the appearance of the different sized fonts: 

<center>
![scrolling background](/images/text-and-font.gif)
</center>
<center>
*5x7 and 8x8 font text swapping back and forth on display*
</center>

```py
import thumby

thumby.display.setFPS(1)

while(1):
    thumby.display.fill(0) # Fill canvas to black
    thumby.display.setFont("/lib/font5x7.bin", 5, 7, 1)
    thumby.display.drawText("Font5x7", 5, 16, 1)
    thumby.display.update()
    
    thumby.display.fill(0) 
    thumby.display.setFont("/lib/font8x8.bin", 8, 8, 1)
    thumby.display.drawText("Font8x8", 5, 16, 1)
    thumby.display.update()
```