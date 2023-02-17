# Thumby API Documentation

To get started using the entire Thumby API, import the module at the top of your MicroPython program:

```py
import thumby
```

### Constants

* `__version__`
    * type: string
    * values: 1.0 ~ limitless (increased for changes to library)

---

***Note: where*** `color` ***is mentioned in the Thumby API docs,*** `color` ***refers to 0 being a black (unlit) pixel, and the value 1 refers to a white (lit) pixel.***

---

## Methods

What are [**Thumby Submodules**](/API/Get-Started/#submodules)? 

<style>
   .md-typeset table:not([class]) {
      display: table;
      font-family: Roboto;
      font-size: 13pt;
   } 
</style>


| Thumby [**Submodule**](/API/Get-Started/#submodules)  	             | Documentation Page & Methods   	              |
|---------------------------------|------------------------------------------------|
| **thumbyHardware**              |[**Hardware:**](/API/Hardware/) <br><br> `.reset()`|
| **thumbyButton**                |[**Button**](/API/Buttons/) <br><br> `.buttonX.pressed()`<br><br>`.buttonX.justPressed()` <br><br> `.inputPressed()` <br><br> `.inputJustPressed()` <br><br> `.dpadPressed()` <br><br> `.dpadJustPressed()` <br><br> `.actionPressed()` <br><br> `.actionJustPressed()`|
| **thumbyGraphics**              |[**Text:**](/API/Text-and-Font/) <br><br>`.display.drawText(string, x, y, color)`<br><br>`.display.setFont(fontFilePath, width, height, space)` <br><br> [**General:**](/API/Graphics/) <br><br> Constants: `.display.width` and `.display.height` <br><br> `.display.update()`<br><br>`.display.setFPS(FPS)`<br><br>`.display.fill(color)`<br><br>`.display.brightness(brightness)` <br><br> [**Pixels:**](/API/Pixels/) <br><br> `.display.setPixel(x, y, color)`<br><br>`.display.getPixel(x, y)` <br><br> [**Lines:**](/API/Lines/) <br><br> `.display.drawLine(x1, y1, x2, y2, color)` <br><br> [**Rectangles:**](/API/Rectangles/) <br><br> `.display.drawFilledRectangle(x, y, w, h, color)`<br><br>`.display.drawRectangle(x, y, w, h, color)` <br><br> [**Blit:**](/API/Blit-Draw/) <br><br> `.display.blit(bitmapData, x, y, width, height, key, mirrorX, mirrorY)`<br><br>`.display.blitWithMask(bitmapData, x, y, width, height, key, mirrorX, mirrorY, maskBitmapData)`<br><br>`.display.drawSprite(sprite)`<br><br>`.display.drawSpriteWithMask(sprite, maskSprite)`  |
| **thumbySprite**                |[**Sprite**](/API/Sprites/) <br><br> `.Sprite(width, height, bitmapData, x, y, key, mirrorX, mirrorY)`<br><br>`.Sprite.getFrame()`<br><br>`.Sprite.setFrame(frame)`|
| **thumbyAudio**                 |[**Audio**](/API/Audio/)  <br><br> `.audio.play(freq, duration)`<br><br>`.audio.playBlocking(freq, duration)`<br><br>`.audio.stop()`<br><br>`.audio.setEnabled(setting)`<br><br> `audio.set(freq)`|
| **thumbyLink**                  |[**Link**](/API/Link/) <br><br> `.link.send(data)`<br><br>`.link.receive()` |
|  **thumbySaves**                |[**Saves**](/API/Save-Files/) <br><br> `.saveData.setName(subdirectoryName)` <br><br> `.saveData.setItem(key, value)` <br><br> `.saveData.getItem(key)` <br><br> `.saveData.hasItem(key)` <br><br> `.saveData.delItem(key)` <br><br> `.saveData.save()` <br><br> `.saveData.getName()`  |

---

## Submodules

In Thumby API version 1.7, the Thumby API was divided into submodules for those not using the entire API. Using Thumby submodules increases the speed of program load times. You can always import all thumby constants and methods using `import thumby`. To import submodules and to use their methods in your code, you would import the submodule name instead, and when using methods you would type the submodule name instead of "thumby". 

Let's look at the differences in two small examples that show how to import and use methods with the entire Thumby API and with a submodule. 

Using the full API:
```py
import thumby

thumby.display.fill(0)
thumby.display.drawText("Hello world", 0, 0, 1)
thumby.display.update()
```

Using a submodule of the API:
```py
import thumbyGraphics

thumbyGraphics.display.fill(0)
thumbyGraphics.display.drawText("Hello world", 0, 0, 1)
thumbyGraphics.display.update()
```

These code snippets work the same, but the second runs faster! Check out what methods are available in which submodule in the table below!