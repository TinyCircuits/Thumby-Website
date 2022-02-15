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

---

`thumby.display.drawSprite(sprite)` | draw `sprite` to screen using its internal properties (position, dimensions, etc). Returns none, all parameters required.

* `sprite`
    * type: Sprite (`thumby.Sprite`)

---

`thumby.display.drawSpriteWithMask(sprite, maskSprite)` | draws `sprite` to screen using internal properties for position and size with per-pixel transparency provided by `maskSprite`. Returns none, all parameters required.

* `sprite`
    * type: Sprite (`thumby.Sprite`)
* `maskSprite`
    * type: Sprite (`thumby.Sprite`) (pixels set to 1 are transparent, while 0 pixels are not drawn)