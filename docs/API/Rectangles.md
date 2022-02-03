# Draw Rectangles

* `thumby.display.drawFilledRectangle(x, y, w, h, color)` | creates filled rectangle with `color` at `x` and `y` with dimensions `w` (width) and `h` (height). Returns None, all parameters required.
    * `x`
        * type: int
        * values: 0 (left) ~ 71 (right)
    * `y`
        * type: int
        * values: 0 (top) ~ 39 (bottom)
    * `w`
        * type: int
        * values: 0 ~ 71
    * `h`
        * type: int
        * values: 0 ~ 39
    * `color`
        * type: int
        * values: 0 or 1

        
* `thumby.display.drawRectangle(x, y, w, h, color)` | creates 1px thick outline rectangle with `color` at `x` and `y` with dimensions `w` (width) and `h` (height) (thickness not variable). Returns None, all parameters required.
    * `x`
        * type: int
        * values: 0 (left) ~ 71 (right)
    * `y`
        * type: int
        * values: 0 (top) ~ 39 (bottom)
    * `w`
        * type: int
        * values: 0 ~ 71
    * `h`
        * type: int
        * values: 0 ~ 39
    * `color`
        * type: int
        * values: 0 or 1