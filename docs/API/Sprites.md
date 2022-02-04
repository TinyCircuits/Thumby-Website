## Sprite


### Functions
* `thumby.Sprite(width, height, bitmapData, x, y, key, mirrorX, mirrorY)` | initialize sprite object with fixed frame `width` and `height` for frames in `bitmapData`, positioned at `x` and `y`, and rendered to screen mirrored depending on, `mirrorX` and `mirrorY`. Transparent pixels are defined by `key` (e.g. `key = 0` means black pixels are not drawn/are transparent). Returns Sprite.
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
* `Sprite.getFrame()` | gets the current frame index of the sprite animation. Return int, automatically returns wrapped index if index greater than max number of frames.
* `Sprite.setFrame(frame)` | sets the current `frame` index of the sprite animation. Needs to be used manually to progress animation, framerate handled by `thumby.display.update()`. Returns none, all parameters required.
    * `frame`
        * type: int
        * values: 0 ~ overflow (values larger than the number of frames get wrapped)