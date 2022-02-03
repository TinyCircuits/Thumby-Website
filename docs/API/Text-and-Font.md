# Text and Font

* `thumby.display.drawText(string, x, y, color)` | draws `string` in `color` at `x` and `y` with font specified by `thumby.display.setFont(...)`. Default font is 8x7px MicroPython font. Returns None, all parameters required.
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

            
* `thumby.display.setFont(fontFilePath, width, height, space)` | sets the `fontFilePath` pointing to binary font file with character `width`, `height`, and `space` between characters for use by `thumby.display.drawText(...)`. Returns None, all parameters required.
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