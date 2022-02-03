# Move a Sprite Using the D-Pad

To create the effect of a moving sprite, one must continuously clear and rewrite the screen with the sprite's new position as it changes. With this in mind, the two lines to clear and update the screen are essential for any moving component in the game:

```py
thumby.display.fill(0) # Fill canvas with black pixels to 'clear' the screen 

thumby.display.update()
```

This next example will show a spaceship sprite that moves around the screen depending on which buttons on the D-pad are pressed, up, down, left, and right. A combination of 2 buttons being pressed will move the sprite between the two directions - so your sprite can move 8 directions using just 4 buttons!

Note that the spaceship will move off the screen with this code snippet since there is no bounding logic. Check out the [bounded ball page](Bounded-ball.md) for more information on keeping a sprite within view. 

<center>
![Bouncing ball](\images\move-ship-sprite.gif)
</center>
<center>
*Spaceship moving around using D-pad buttons*
</center>

```py
import thumby

# Spaceship bitmap: width: 13, height: 13
shipMap = bytearray([128,64,64,48,168,100,36,100,168,48,64,64,128,
           5,3,2,3,4,4,12,4,4,3,2,3,5])
           
shipSprite = thumby.Sprite(13, 13, shipMap, key=0)
shipSprite.x = 29 # Initial placement - middle of screen
shipSprite.y = 15

# Number of pixels sprite will move - increasing this makes movement choppy 
moveNum = 1

thumby.display.setFPS(45) # set frame rate, between 30-60 is usually best

# Begin main game loop that runs for the course of the game
while(1):
    thumby.display.fill(0) # Fill canvas to black
    
    # Up, down, left, right button movement logic
    # When pressing 2 buttons at the same time, diagonal movement is possible
    if thumby.buttonU.pressed():
        shipSprite.y -= moveNum
    if thumby.buttonD.pressed():
        shipSprite.y += moveNum
    if thumby.buttonL.pressed():
        shipSprite.x -= moveNum
    if thumby.buttonR.pressed():
        shipSprite.x += moveNum

    # Display Sprite & Update screen
    thumby.display.drawSprite(shipSprite)
    thumby.display.update()
```