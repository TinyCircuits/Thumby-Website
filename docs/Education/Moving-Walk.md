# Walk Animation 

A walk cycle animation consists of a few or several different frames of the movements involved in walking. For a 2-legged human, there may be 2 frames of the right leg moving forward as the left leg moves further back. With different sprites that may have more legs or none at all, you may have to get creative with a walking animation! 

Here's an example of a simple cat walking:

<center>
![Walking cat](/images/walking-cat.gif)
</center>
<center>
*Cat Walking Animation*
</center>

```py
# Written by: Laveréna Wienclaw, Feb 2022
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

## Moving Background

With just the walking animation, it doesn't look like the cat is actually walking anywhere. With a moving, or scrolling, background we can add more movement to the scene. Here's a scrolling background:

<center>
![scrolling background](/images/scrolling-background.gif)
</center>
<center>
*Scrolling nighttime background*
</center>

```py
# Written by: Laveréna Wienclaw, Feb 2022
import thumby

# BITMAP: width: 72, height: 30
bg = bytearray([0,0,0,0,0,0,0,0,0,0,0,4,0,0,0,0,0,0,0,0,128,0,0,0,0,0,0,0,0,0,0,0,0,0,64,0,0,0,0,0,0,0,0,0,0,0,0,128,0,0,0,0,0,0,0,0,0,0,0,4,0,0,0,0,0,0,0,0,0,64,0,0,
            0,0,0,0,0,8,20,8,0,0,0,128,128,128,128,128,128,128,128,128,128,128,128,128,0,0,0,0,64,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,2,1,0,0,0,0,128,192,224,224,240,240,248,248,252,252,252,252,252,252,252,252,248,248,240,
            224,240,240,248,248,252,252,254,254,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,254,252,248,248,240,224,224,224,192,192,192,192,192,192,192,192,192,192,192,224,224,224,240,248,252,252,254,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,
            63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63])

bg2 = bytearray([0,0,0,2,0,0,0,16,64,0,0,0,0,128,64,128,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,16,0,0,0,0,0,0,0,0,0,0,16,40,16,0,0,0,0,0,0,0,0,0,0,0,0,0,32,0,0,0,0,0,0,0,0,64,160,64,2,0,
            240,224,192,128,128,128,0,8,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,8,0,128,128,128,192,224,240,240,248,248,248,252,252,252,254,254,254,255,255,255,255,255,254,254,254,254,252,252,252,248,248,240,240,225,224,192,192,128,128,0,0,0,0,0,32,0,0,0,
            255,255,255,255,255,255,255,255,254,254,254,254,252,252,252,252,252,252,252,254,254,254,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,254,252,252,248,240,240,224,224,
            63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63])

# Background sprites & x positions
bgSpr = thumby.Sprite(72, 30, bg)
bg2Spr = thumby.Sprite(72, 30, bg2)
bgSpr.x = 0
bg2Spr.x = 72

# Set the FPS 
thumby.display.setFPS(60)

# Used to keep track of loops and timing when the backgrounds should scroll
scrollCtr = 0

while(1):
    thumby.display.fill(1) # Fill canvas to white
    
    # Scrolling background
    scrollCtr += 1
    if(scrollCtr % 8 == 0):
        bgSpr.x -= 1
        bg2Spr.x -= 1
    
    # Re-place the x coordinate of backgrounds when they're unseen
    if (bg2Spr.x == 0):
        bgSpr.x = 72
    if (bg2Spr.x == -72):
        bg2Spr.x = 72
    
    thumby.display.drawSprite(bgSpr)
    thumby.display.drawSprite(bg2Spr)
    thumby.display.update()
```


## Walking Animation On Moving Background

Together, the walking animation on a scrolling background can achieve the full effect of a sprite moving during gameplay:

<center>
![scrolling background](/images/cat-scrolling-walk.gif)
</center>
<center>
*Walking cat on a scrolling nighttime background*
</center>

You may notice some improvements in displaying the cat animation - by using a **list** of the different cat frames, you can more easily cycle through a walking animation later in the program.

```py
# Written by: Laveréna Wienclaw, Feb 2022
import thumby

# Cat bitmaps 8x8
catFootForward = bytearray([243,133,135,231,231,128,193,184])
catFeetForward = bytearray([243,133,199,167,231,128,193,184])
catSplit = bytearray([177,199,199,167,231,128,225,152])
catFrontSplit =bytearray([179,197,135,231,167,192,193,184])
catFeetBack = bytearray([179,197,135,231,167,192,129,248])
catBackFootTail = bytearray([179,197,197,167,167,192,129,248])


# BITMAP: width: 72, height: 30
bg = bytearray([0,0,0,0,0,0,0,0,0,0,0,4,0,0,0,0,0,0,0,0,128,0,0,0,0,0,0,0,0,0,0,0,0,0,64,0,0,0,0,0,0,0,0,0,0,0,0,128,0,0,0,0,0,0,0,0,0,0,0,4,0,0,0,0,0,0,0,0,0,64,0,0,
            0,0,0,0,0,8,20,8,0,0,0,128,128,128,128,128,128,128,128,128,128,128,128,128,0,0,0,0,64,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,1,2,1,0,0,0,0,128,192,224,224,240,240,248,248,252,252,252,252,252,252,252,252,248,248,240,
            224,240,240,248,248,252,252,254,254,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,254,252,248,248,240,224,224,224,192,192,192,192,192,192,192,192,192,192,192,224,224,224,240,248,252,252,254,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,
            63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63])

bg2 = bytearray([0,0,0,2,0,0,0,16,64,0,0,0,0,128,64,128,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,16,0,0,0,0,0,0,0,0,0,0,16,40,16,0,0,0,0,0,0,0,0,0,0,0,0,0,32,0,0,0,0,0,0,0,0,64,160,64,2,0,
            240,224,192,128,128,128,0,8,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,8,0,128,128,128,192,224,240,240,248,248,248,252,252,252,254,254,254,255,255,255,255,255,254,254,254,254,252,252,252,248,248,240,240,225,224,192,192,128,128,0,0,0,0,0,32,0,0,0,
            255,255,255,255,255,255,255,255,254,254,254,254,252,252,252,252,252,252,252,254,254,254,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,254,252,252,248,240,240,224,224,
            63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63,63])


# Make a sprite object using bytearray 
catFootForwardSpr = thumby.Sprite(8, 8, catFootForward, 28, 32)
catFeetForwardSpr = thumby.Sprite(8, 8, catFeetForward, 28, 32)
catSplitSpr = thumby.Sprite(8, 8, catSplit, 28, 32)
catFrontSplitSpr = thumby.Sprite(8, 8, catFrontSplit, 28, 32)
catFeetBackSpr = thumby.Sprite(8, 8, catFeetBack, 28, 32)
catBackFootTailSpr = thumby.Sprite(8, 8, catBackFootTail, 28, 32)

catSprList = [catFootForwardSpr, catFeetForwardSpr, catSplitSpr, catFrontSplitSpr, catFeetBackSpr, catBackFootTailSpr]

# Background sprites & initial x positions
bgSpr = thumby.Sprite(72, 30, bg)
bg2Spr = thumby.Sprite(72, 30, bg2)
bgSpr.x = 0
bg2Spr.x = 72

# Set the FPS (without this call, the default fps is 30)
thumby.display.setFPS(60)

# You can set the FPS lower, or you can alter the timing of the animations 
# and movement using simple counters and the modulo operator
scrollCtr = 0
catSprCtr = 0

while(1):
    thumby.display.fill(1) # Fill canvas to white
    
    # Scrolling background
    scrollCtr += 1
    if(scrollCtr % 8 == 0): # Move the background every 8 loops
        bgSpr.x -= 1
        bg2Spr.x -= 1
        
        catSprCtr += 1
        if(catSprCtr >= 5): # There are 6 frames in the list, in the placement 0-5
            catSprCtr = 0
            
    # Re-place the x coordinate of backgrounds when they're unseen
    if (bg2Spr.x == 0):
        bgSpr.x = 72
    if (bg2Spr.x == -72):
        bg2Spr.x = 72

    # Draw sprites and update display
    thumby.display.drawSprite(bgSpr)
    thumby.display.drawSprite(bg2Spr)
    thumby.display.drawSprite(catSprList[catSprCtr])
    thumby.display.update()
```


