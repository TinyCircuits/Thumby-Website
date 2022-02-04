# Walk Animation on Scrolling Background

A walk cycle animation consists of a few or several different frames of the movements involved in walking. For a 2-legged human, there may be 2 frames of the right leg moving forward as the left leg moves further back. With different sprites that may have more legs or none at all, you may have to get creative with a walking animation! 

Here's an example of a simple cat walking:

<center>
![Walking cat](/images/walking-cat.gif)
</center>
<center>
*Spaceship moving around using D-pad buttons*
</center>

```py
import thumby

# catFeetTogether = bytearray([243,133,135,231,231,128,129,248])
catFootForward = bytearray([243,133,135,231,231,128,193,184])
catFeetForward = bytearray([243,133,199,167,231,128,193,184])
catSplit = bytearray([177,199,199,167,231,128,225,152])
catFrontSplit =bytearray([179,197,135,231,167,192,193,184])
catFeetBack = bytearray([179,197,135,231,167,192,129,248])
catBackFootTail = bytearray([179,197,197,167,167,192,129,248])

# Make a sprite object using bytearray 
catFootForwardSpr = thumby.Sprite(8, 8, catFootForward, 28, 32)
catFeetForwardSpr = thumby.Sprite(8, 8, catFeetForward, 28, 32)
catSplitSpr = thumby.Sprite(8, 8, catSplit, 28, 32)
catFrontSplitSpr = thumby.Sprite(8, 8, catFrontSplit, 28, 32)
catFeetBackSpr = thumby.Sprite(8, 8, catFeetBack, 28, 32)
catBackFootTailSpr = thumby.Sprite(8, 8, catBackFootTail, 28, 32)

# Set the FPS (without this call, the default fps is 30)
thumby.display.setFPS(8)

while(1):
    thumby.display.fill(1) # Fill canvas to white
    
    # Display the sprite frames & 
    thumby.display.drawSprite(catFootForwardSpr)
    thumby.display.update()
    thumby.display.drawSprite(catFeetForwardSpr)
    thumby.display.update()
    thumby.display.drawSprite(catSplitSpr)
    thumby.display.update()
    thumby.display.drawSprite(catFrontSplitSpr)
    thumby.display.update()
    thumby.display.drawSprite(catFeetBackSpr)
    thumby.display.update()
    thumby.display.drawSprite(catBackFootTailSpr)
    thumby.display.update()
```


