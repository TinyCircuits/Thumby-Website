# Jump a Sprite

To make a sprite jump, you need to change the coordinates of where the sprite is moving during a jump action, all while clearing and updating the screen to show the full jump movement. This example sprite has no other movement than jumping up and landing back in its original spot when using the A action button. 

<center>
![Bouncing ball](/images/jump-animation.gif)
</center>
<center>
*Sprite jumping up and falling down*
</center>

```py
import thumby

# Stand and Jump bitmaps: width: 13, height: 9
standMap = bytearray([16,8,4,60,194,74,66,74,194,60,4,8,16,
           0,0,0,0,1,0,0,0,1,0,0,0,0])
jumpMap = bytearray([1,2,4,60,194,74,66,74,194,60,4,2,1,
           0,0,0,0,1,0,0,0,1,0,0,0,0])

# Make a sprite consisting of two frames
jumpSprite = thumby.Sprite(13, 9, standMap+jumpMap, key=0)

# Initial placement - middle, bottom of screen
jumpSprite.x = 29
jumpSprite.y = 30

# Number of pixels sprite will move - increasing this makes movement choppy 
jumpNum = 1

# Limit game refresh rate to 30 times a second, max
thumby.display.setFPS(30) 

# Begin main game loop that runs for the course of the game
while(True):
    thumby.display.fill(0) # Fill canvas to black
    
    if thumby.buttonA.justPressed() and jumpSprite.y >= 20: # limit the height the Sprite can reach when jumping
        for i in range (0, 10): # jump up 10 pixels
            thumby.display.fill(0)
            jumpSprite.y -= jumpNum 
            jumpSprite.setFrame(1)
            thumby.display.drawSprite(jumpSprite) # draw jumping sprite while jumping
            thumby.display.update() # redraw sprite during jump frames
    else:
        jumpSprite.setFrame(0)
        thumby.display.drawSprite(jumpSprite) # draw standing sprite while falling & standing
        if jumpSprite.y <= 30: 
            jumpSprite.y += jumpNum

    # Update screen
    thumby.display.update()
```

---

### Jump with Velocity


<center>
![Bouncing ball](/images/jump-animation.gif)
</center>
<center>
*Sprite jumping *
</center> 

```py
import thumby

# Stand and Jump bitmaps: width: 13, height: 9
standMap = bytearray([16,8,4,60,194,74,66,74,194,60,4,8,16,
           0,0,0,0,1,0,0,0,1,0,0,0,0])
jumpMap = bytearray([1,2,4,60,194,74,66,74,194,60,4,2,1,
           0,0,0,0,1,0,0,0,1,0,0,0,0])

# Make a sprite consisting of two frames
sprite = thumby.Sprite(13, 9, standMap+jumpMap, key=0)

# Initial placement - middle, bottom of screen
sprite.x = 29
sprite.y = 30

# Add some velocity attributes to the sprite
sprite.xVel = 0
sprite.yVel = 0

# Limit game refresh rate to 60 times a second, max
thumby.display.setFPS(60) 

# Begin main game loop that runs for the course of the game
while(1):
    # Fill canvas to black
    thumby.display.fill(0)

    # When A is pressed and the sprite is on the ground,
    # jump by setting velocity. Show the sprite's jump frame
    if thumby.buttonA.pressed() and sprite.yVel == 0:
        sprite.yVel = 2.5
        sprite.setFrame(1)
    
    # Apply y velocity to y position
    sprite.y -= sprite.yVel
    
    # Only apply 'gravity' if sprite vertical velocity not zero
    if sprite.yVel != 0:
        sprite.yVel -= 0.15
        
    # Sprite hit the ground, make sure it's on the ground exactly,
    # velcoity returned to zero, and that it is back to standing
    if sprite.y >= 30:
        sprite.y = 30
        sprite.yVel = 0
        sprite.setFrame(0)
    
    # Draw sprite and update screen
    thumby.display.drawSprite(sprite)
    thumby.display.update()
```

---

### Parabolic Jump with Velocity

<center>
![Bouncing ball](/images/jump-animation-parabola.gif)
</center>
<center>
*Parabolic jumping using X and Y planes*
</center> 

```py
import thumby

# Stand and Jump bitmaps: width: 13, height: 9
standMap = bytearray([16,8,4,60,194,74,66,74,194,60,4,8,16,
           0,0,0,0,1,0,0,0,1,0,0,0,0])
jumpMap = bytearray([1,2,4,60,194,74,66,74,194,60,4,2,1,
           0,0,0,0,1,0,0,0,1,0,0,0,0])

# Make a sprite consisting of two frames
sprite = thumby.Sprite(13, 9, standMap+jumpMap, key=0)

# Initial placement - middle, bottom of screen
sprite.x = 29
sprite.y = 30

# Add some velocity attributes to the sprite
sprite.xVel = 0
sprite.yVel = 0

# Limit game refresh rate to 60 times a second, max
thumby.display.setFPS(60) 

# Begin main game loop that runs for the course of the game
while(1):
    # Fill canvas to black
    thumby.display.fill(0)

    # When A is pressed and the sprite is on the ground,
    # jump by setting velocity. Show the sprite's jump frame
    if thumby.buttonA.pressed() and sprite.yVel == 0:
        sprite.yVel = 2.5
        sprite.setFrame(1)
    
    if thumby.buttonL.pressed() and sprite.xVel >= -1.95:
        sprite.xVel -= 0.05
    
    if thumby.buttonR.pressed() and sprite.xVel <= 1.95:
        sprite.xVel += 0.05
    
    sprite.x += sprite.xVel
    sprite.y -= sprite.yVel
    
    # Only apply 'gravity' if sprite vertical velocity not zero
    if sprite.yVel != 0:
        sprite.yVel -= 0.15
    
    if sprite.xVel <= -0.05:
        sprite.xVel += 0.05/2
    elif sprite.xVel >= 0.05:
        sprite.xVel -= 0.05/2
    else:
        sprite.xVel = 0
        
    # Sprite hit the ground, make sure it's on the ground exactly,
    # velcoity returned to zero, and that it is back to standing
    if sprite.y >= 30:
        sprite.y = 30
        sprite.yVel = 0
        sprite.setFrame(0)
    
    # Draw sprite and update screen
    thumby.display.drawSprite(sprite)
    thumby.display.update()
```