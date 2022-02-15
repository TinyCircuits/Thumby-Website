# Get and Set Pixels

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

    