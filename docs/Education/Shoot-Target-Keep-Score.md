# Shoot and Hit Target

Some games involve the need to remove objects blocking a path forward, and what better way to do that than with a laser? 

Whether it be a harmless obstacle, or an opponent that needs some laser-ing, keeping track of the score for game points or knowing when an opponent is defeated can be an important to gameplay. This example shows a simple way to shoot a laser beam at a meteor from a spaceship, and how to keep track of the number of times a laser beam has hit the meteor.

<center>
![Bouncing ball](/images/shoot-meteor-keep-score.gif)
</center>
<center>
*Spaceship laser beam hitting a meteor*
</center>


```py
# Written by: Laveréna Wienclaw, Feb 2022
import thumby

# BITMAP: width: 8, height: 8
shipMap = bytearray([195,231,189,219,102,36,60,24])
meteorMap = bytearray([28,122,126,223,175,223,118,60])
beamMap = bytearray([1,1])

# Make a sprite object 
shipSpr = thumby.Sprite(8, 8, shipMap, 5, 20)
meteorSpr = thumby.Sprite(8, 8, meteorMap, 60,20)
beamSpr = thumby.Sprite(2, 1, beamMap)
beamSpr.x = 11 # place beam so it's hidden at the tip of the ship
beamSpr.y = 24

# Set the FPS (without this call, the default fps is 30)
thumby.display.setFPS(30)

# Game state variables
score = 0
shootBeam = False

while(1):
    # Fill canvas to black
    thumby.display.fill(0)

    if thumby.buttonA.justPressed():
        shootBeam = True
    if shootBeam == True:
        thumby.display.fill(0)
        beamSpr.x += 1

        # Check if beam has collided with meteor
        if(beamSpr.x >= meteorSpr.x):
            beamSpr.x = 11 # Reload beam after hitting meteor
            score += 1     # Increase score and change game state
            shootBeam = False

    # Draw the score and sprites
    thumby.display.drawText("Score: ", 15, 3, 1)
    thumby.display.drawText(str(score), 55, 3, 1)
    thumby.display.drawSprite(shipSpr)
    thumby.display.drawSprite(meteorSpr)
    thumby.display.drawSprite(beamSpr)
    thumby.display.update()
```