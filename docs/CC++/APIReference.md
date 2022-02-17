#### Functions

<style>
    .md-typeset__table {
    min-width: 100%;
    }

    .md-typeset table:not([class]) {
        display: table;
    }
</style>

> ##### Drawing
>> |                   Syntax                                                           
   |----------------------------------------------------------------------------------------|
   | `void writePixel(uint16_t color)`<br><br>Writes `color` to pixel placed by `goto(...)` |
   | `void setX(uint8_t x, uint8_t end)`                                                    |
   | `void setY(uint8_t y, uint8_t end)`                                                    |
   | `void goTo(uint8_t x, uint8_t y)`                                                      |
   | `void drawPixel(uint8_t x, uint8_t y, uint16_t color)`                                 |
   | `void clear()`                                                                         |
   | `void clearWindow(uint8_t x, uint8_t y, uint8_t w, uint8_t h)`                         |
   | `void drawLine(int16_t x0, int16_t y0, int16_t x1, int16_t y1, uint16_t color)`<br><br>Draws line between points defined by `x0`, `y0` and `x1`, `y1` in `color` |
   | `void drawCircle(int16_t x0, int16_t y0, int16_t radius, uint16_t color)`              |

> ##### Font
>> |                   Syntax                                                               |
   |----------------------------------------------------------------------------------------|
   | `void setFont(const FONT_INFO&)`                                                       |
   | `uint8_t getFontHeight(const FONT_INFO&)`                                              |
   | `uint8_t getFontHeight(void)`                                                          |
   | `uint8_t getPrintWidth(char \* str)`                                                   |
   | `void setCursor(int x, int y)`                                                         |
   | `void fontColor(uint16_t f, uint16_t g)`                                               |
   | `size_t write(uint8_t ch)`                                                             |
   | `uint8_t* getBuffer()`                                                                 |
   | `uint16_t getBufferSize()`                                                             |

> ##### Audio
>> |                   Syntax                                                               |
   |----------------------------------------------------------------------------------------|
   | `void play(uint32_t freq, uint16_t duty)`                                              |
   | `void stopPlay()`                                                                      |

> ##### Link
>> |                   Syntax                                                               |
   |----------------------------------------------------------------------------------------|
   | `bool linkPack(uint8_t* dataBuf, uint8_t* packedBuf)`                                  |
   | `bool linkUnpack(uint8_t* packedBuf, uint8_t* dataBuf)`                                |