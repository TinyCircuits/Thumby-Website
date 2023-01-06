# Draw Line Function

`thumby.display.drawLine(x1, y1, x2, y2, color)` | draws 1px thick line in `color` from `x1` and `y1` to `x2` and `y2` (thickness not variable). Returns None, all parameters required.

* `x1`
    * type: int
    * values: 0 (left) ~ 71 (right)
* `y1`
    * type: int
    * values: 0 (top) ~ 39 (bottom)
* `x2`
    * type: int
    * values: 0 (left) ~ 71 (right)
* `y2`
    * type: int
    * values: 0 (top) ~ 39 (bottom)
* `color`
    * type: int
    * values: 0 or 1 -- where 0 is black or an unlit pixel, and 1 is white or a lit pixel

---

### Line Example

When drawing lines, it may be helpful to use the `thumby.display.width` and `thumby.display.height` member variables for the screen width (72), and the height (40). Otherwise, you can do the math yourself. This example uses both methods to draw three different lines:

<center>
![Bouncing ball](/images/lines-example.jpg)
</center>
<center>
*Three lines across the screen horizontally, vertically, and diagonally*
</center>

```py
# Written by: Laveréna Wienclaw, Feb 2022
import thumby

thumby.display.fill(0) # Fill canvas to black

# Draw a diagonal line from the top left to the bottom right corner
thumby.display.drawLine(0, 0, thumby.display.width, thumby.display.height, 1) # (x1, y1, x2, y2, color)
# Draw another line in the middle, top to bottom
thumby.display.drawLine(36, 0, 36, 40, 1)
# Draw a last line in the middle of the screen from left to right
thumby.display.drawLine(0, 20, 72, 20, 1)

# Update display
thumby.display.update()

```