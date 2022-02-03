* API reference expects thumby imported as `import thumby`

## General
* ### Constants
    * `__version__`
        * type: string
        * values: 1.0 ~ limitless (increased for changes to library)

## Graphics
* ### Constants
    * `thumby.display.width` | number of pixels that define the screen width
        * type: int
        * value: 72
    * `thumby.display.height` | number of pixels that define the screen height
        * type: int
        * value: 40
* ### Functions
    * `thumby.display.setFPS(FPS)` | sets the max `FPS` used by `thumby.display.update()`. Returns None, all parameters required.
        * `FPS`
            * type: float
            * values: 0 ~ integer max
    * `thumby.display.update()` | updates screen at frames-per-second (FPS) specified by `thumby.display.setFPS(...)`. Will block to not exceed fps setting. Default framerate 0 (non-limited). Returns `None`

    * `thumby.display.fill(color)` | fills entire screen with `color`. Returns None
        * `color`
            * type: int
            * values: 0 or 1


    * `thumby.display.brightness(bightness)` | sets screen to `brightness` value. Returns None, all parameters required.
        * `brightness`
            * type: int
            * values: 0 (off) ~ 127 (max brightness)