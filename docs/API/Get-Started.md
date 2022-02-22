# Thumby API Documentation

To get started using the Thumby API, import the module at the top of your MicroPython program:

```py
import thumby
```

### Constants

* `__version__`
    * type: string
    * values: 1.0 ~ limitless (increased for changes to library)

---

Use these screen dimension constants in place of the actual pixel dimensions of the screen to remove magic numbers from your code:

`thumby.display.width` | number of pixels that define the screen width

* type: int
* value: 72

`thumby.display.height` | number of pixels that define the screen height

* type: int
* value: 40

---

## Methods

<style>
   .md-typeset table:not([class]) {
      display: table;
      font-family: Roboto;
      font-size: 13pt;
   } 
</style>

| Documentation Page    	             | Functions   	                             |
|----------------------------------------|-------------------------------------------|
| [**Display basics**](/API/Graphics/)   | `thumby.display.update()`<br><br>`thumby.display.setFPS(FPS)`<br><br>`thumby.display.fill(color)`<br><br>`thumby.display.brightness(brightness)` |
| [**Text & Font**](/API/Text-and-Font/) | `thumby.display.drawText(string, x, y, color)`<br><br>`thumby.display.setFont(fontFilePath, width, height, space)` |
| [**Get & Set Pixels**](/API/Pixels/)   | `thumby.display.setPixel(x, y, color)`<br><br>`thumby.display.getPixel(x, y)` |
| [**Draw Lines**](/API/Lines/)          | `thumby.display.drawLine(x1, y1, x2, y2, color)` |
| [**Draw Rectangles**](/API/Rectangles/)| `thumby.display.drawFilledRectangle(x, y, w, h, color)`<br><br>`thumby.display.drawRectangle(x, y, w, h, color)` |
| [**Draw Sprites**](/API/Sprites/)      | `thumby.Sprite(width, height, bitmapData, x, y, key, mirrorX, mirrorY)`<br><br>`Sprite.getFrame()`<br><br>`Sprite.setFrame(frame)` |
| [**Button Input** ](/API/Buttons/)     | `thumby.buttonX.pressed()`<br><br>`thumby.buttonX.justPressed()`  	|
| [**Audio**](/API/Audio/)               | `thumby.audio.play(freq, duration, duty)`<br><br>`thumby.audio.playBlocking(freq, duration, duty)`<br><br>`thumby.audio.stop()`<br><br>`thumby.audio.set_enabled(setting)`|
| [**Multiplayer Link** ](/API/Link/)    | `thumby.link.send(data)`<br><br>`thumby.link.receive()`  	|
| [**Draw Using Blit**](/API/Blit-Draw/) | `thumby.display.blit(bitmapData, x, y, width, height, key, mirrorX, mirrorY)`<br><br>`thumby.display.blitWithMask(bitmapData, x, y, width, height, key, mirrorX, mirrorY, maskBitmapData)`<br><br>`thumby.display.drawSprite(sprite)`<br><br>`thumby.display.drawSpriteWithMask(sprite, maskSprite)`  	|
