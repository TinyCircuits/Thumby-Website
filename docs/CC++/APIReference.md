#API Reference

<style>
   .md-typeset h5 {
      color: var(--md-typeset-color);
   }

   .md-typeset h6 {
      color: transparent;
      line-height: 0;
   }

   .md-typeset table:not([class]) {
      display: table;
      font-family: Roboto;
      font-size: 12pt;
      color: var(--md-typeset-color);
      font-weight: bold;
   } 
</style>


## Thumby.h
`#include <Thumby.h>`

Main library for screen, button, audio, and link cable interaction.

Inherits most functionality from `GraphicsBuffer.h` and `font.h` libraries. This section is a summary of what is accessible and useful through the `Thumby.h` library.

---

### Defines

|  Name                    | value |
|--------------------------|-------|
|  `THUMBY_SCREEN_WIDTH`   |  `72` |
|  `THUMBY_SCREEN_HEIGHT`  |  `40` |
|  `BUTTON_L`              | `0x01`|
|  `BUTTON_R`              | `0x02`|
|  `BUTTON_U`              | `0x04`|
|  `BUTTON_D`              | `0x08`|
|  `BUTTON_B`              | `0x10`|
|  `BUTTON_A`              | `0x20`|

---

### Classes
#### Thumby
Class for driving and using Thumby peripheral components.

##### Public member functions

###### General
|                   General                                                           
|-----------------------------------------------------------------------|
|`void begin()`<br><br>Sets up pins and libraries                       |
|`void update()`<br><br>Sends the internal graphics buffer to the screen|

###### Drawing
|                   Drawing                                                           
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `void writePixel(uint16_t color)`<br><br>Writes `color` to pixel placed by `goto(...)`, `setX(...)`, or `setY(...)`                                                                                                           |
| `void setX(uint8_t x, uint8_t end)`<br><br>Sets drawing X position to `x` and row jump position at `end` (e.g. after calling `writePixel(...)` `end` times, pixels on the next increment of `y` starting at `x` will be drawn)|
| `void setY(uint8_t y, uint8_t end)`<br><br>Sets drawing Y position to `y` and row loop position at `end` (e.g. after calling `writePixel(...)` enough times to draw rows defined by `setX(...)`, loop back to this `y`)       |
| `void goTo(uint8_t x, uint8_t y)`<br><br>Quick wrapper of `setX(...)` and `setY(...)`                                                                                                                                         |
| `void drawPixel(uint8_t x, uint8_t y, uint16_t color)`<br><br>Set pixel to `color` at `x` and `y`                                                                                                                             |
| `void clear()`<br><br>Clears all pixels in buffer to black                                                                                                                                                                    |
| `void clearWindow(uint8_t x, uint8_t y, uint8_t w, uint8_t h)`<br><br>Clears rectangle defined by `x`, `y`, `w`, and `h` to black                                                                                             |
| `void drawLine(int16_t x0, int16_t y0, int16_t x1, int16_t y1, uint16_t color)`<br><br>Draws line between points defined by `x0`, `y0` and `x1`, `y1` in `color`                                                              |
| `void drawCircle(int16_t x0, int16_t y0, int16_t radius, uint16_t color)`<br><br>Draws circle with center at `x0`, and `y0` with `radius` in `color`                                                                          |

###### Font
|                   Font                                                                                                                                                                                        |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `void setFont(const FONT_INFO&)`<br><br>Set font parameters to those defined in `FONT_INFO`. Predefined fonts are available in the GraphicsBuffer library `font.h` file (default is `thinPixel7_10ptFontInfo`)|
| `uint8_t getFontHeight(const FONT_INFO&)`<br><br>Returns font height value (in pixels) from `FONT_INFO`                                                                                                       |
| `uint8_t getFontHeight(void)`<br><br>Returns the current set font height value (in pixels)                                                                                                                    |
| `uint8_t getPrintWidth(char* str)`<br><br>Returns the number of pixels characters in `str` will occupy in width                                                                                               |
| `void setCursor(int x, int y)`<br><br>Sets the cursor `x` and `y` position the characters will print at (top left corner of string)                                                                           |
| `void fontColor(uint16_t f, uint16_t g)`<br><br>Sets the foreground (text) and background colors to `f` and `g` respectively                                                                                  |
| `size_t write(uint8_t ch)`<br><br>Writes a single character `ch` to the buffer at the current set cursor position. Returns `true` if successful `false` otherwise                                             |
| `uint8_t* getBuffer()`<br><br>Returns (pointer to) graphics buffer                                                                                                                                            |
| `uint16_t getBufferSize()`<br><br>Returns the number of bytes the graphics buffer occupies                                                                                                                    |
| `void print(uint8_t* str)`<br><br>Draws characters in `str` to buffer                                                                                                                                         |

###### Audio
|                   Audio                                                                                                                          |
|--------------------------------------------------------------------------------------------------------------------------------------------------|
| `void play(uint32_t freq, uint16_t duty)`<br><br>Starts playing sound at `freq` (only 20 - 20kHz is useful for human hearing) and `duty` cycle   |
| `void stopPlay()`<br><br>Stops playing sound started by `play(...)`                                                                              |

###### Buttons
|                   Buttons                                                                                                                                          |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `bool isPressed(uint8_t mask)`<br><br>Returns `true` if any buttons correlating to the ORed button `mask` (see "Defines" section) are pressed, `false` otherwise   |

###### Link
|                   Link                                                                                                                                                                                                                                |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `int8_t linkPack(uint8_t* dataBuf, uint16_t dataBufLen, uint8_t* packedBuf, uint16_t packedBufLen)`<br><br>Packs/copies `dataBufLen` number of bytes from `dataBuf` to `packedBuf` up to `packedBufLen`. Adds three additional bytes for size and checksum. Returns -1 if `dataBufLen` > 512 or `dataBufLen+3` > `packedBufLen`. Returns the full packet length if succeeds (`dataBufLen+3`)|
| `int8_t linkUnpack(uint8_t* packedBuf, uint16_t packedBufLen, uint8_t* dataBuf, uint16_t dataBufLen)`<br><br>Unpacks/copies `dataBufLen` number of bytes from `packedBuf` to `dataBuf` while removing data and checksum bytes. Returns `-1` if checksum in `packedBuf` does not match that generated from extracted data or if data from `packedBuf` cannot fit into `dataBuf`. Returns `dataLength`|

##### Public member variables
|  Name                                   | Description                         |
|-----------------------------------------|-------------------------------------|
|  `const uint16_t width`                 |Current set screen width (in pixels) |
|  `const uint16_t height`                |Current set screen height (in pixels)|
|  `const uint8_t bitsPerPixel`           |Current screen color bit depth       |

---

### Structs
#### FONT_CHAR_INFO
##### Public member variables
|  Name                    | Description                                        |
|--------------------------|----------------------------------------------------|
|  `const uint8_t width`   |Width of a character in pixels                      |
|  `const uint16_t offset` |Offset from the end of the character width in pixels|

#### FONT_INFO
##### Public member variables
|  Name                             | Description                                        |
|-----------------------------------|----------------------------------------------------|
|  `const unsigned char height`     |Height of the font in pixels                        |
|  `const char startCh`             |First character in font                             |
|  `const char endCh`               |Last character in font                              |
|  `const FONT_CHAR_INFO* charDesc` |Description of characters in the font               |
|  `const unsigned char* bitmap`    |Bitmap used by the font                             |