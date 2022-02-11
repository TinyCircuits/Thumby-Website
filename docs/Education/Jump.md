# Jump a Sprite

To make a sprite jump, you need to change the coordinates of where the sprite is moving during a jump action, all while clearing and updating the screen to show the full jump movement. This example sprite has no other movement than jumping up and landing back in its original spot when using the A action button. 

<center>
![Bouncing ball](/images/jump-animation.gif)
</center>
<center>
*Sprite jumping up and falling down*
</center>

```py
# Written by: Laveréna Wienclaw, Feb 2022
import thumby

# Stand and Jump bitmaps: width: 13, height: 9
standMap = bytearray([16,8,4,60,194,74,66,74,194,60,4,8,16,
           0,0,0,0,1,0,0,0,1,0,0,0,0])
jumpMap = bytearray([1,2,4,60,194,74,66,74,194,60,4,2,1,
           0,0,0,0,1,0,0,0,1,0,0,0,0])

standSprite = thumby.Sprite(13, 9, standMap, key=0)
jumpSprite = thumby.Sprite(13, 9, jumpMap, key=0)
standSprite.x = 29 # Initial placement - middle, bottom of screen
standSprite.y = 30
jumpSprite.x = 29 
jumpSprite.y = 30

# Number of pixels sprite will move - increasing this makes movement choppy 
jumpNum = 1

thumby.display.setFPS(30) 

# Begin main game loop that runs for the course of the game
while(True):
    thumby.display.fill(0) # Fill canvas to black
    
    if thumby.buttonA.justPressed():
        if standSprite.y >= 20: # limit the height the Sprite can reach when jumping
            for i in range (0, 10): # jump up 10 pixels
                thumby.display.fill(0)
                jumpSprite.y -= jumpNum 
                thumby.display.drawSprite(jumpSprite) # draw jumping sprite while jumping
                thumby.display.update() # redraw sprite during jump frames
            standSprite.y = jumpSprite.y # keep both sprites in the same position
    else:
        thumby.display.drawSprite(standSprite) # draw standing sprite while falling & standing
        if standSprite.y <= 30: 
            standSprite.y += jumpNum
        jumpSprite.y = standSprite.y

    # Update screen
    thumby.display.update()
```