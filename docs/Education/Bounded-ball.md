# Ball Bounded by Thumby Screen

This example shows a modified snippet of the Brick Breaker Thumby game called Brick'd. When run, the ball Sprite in the program will bounce against the bounded walls of the Thumby screen. 

<center>
![Bouncing ball](/images/bounded-ball.gif)
</center>
<center>
*Bounded Bouncing Ball*
</center>

```py
# Written by: Laveréna Wienclaw, Jan 2022
import thumby

# Bitmaps
ballMap = bytearray([6,15,15,6]) # BITMAP: width: 4, height: 4

# Sprite data
ballSprite = thumby.Sprite(4, 4, ballMap, key=0)
ballSprite.x = 0 # Initial placement of ball and movable game pad
ballSprite.y = 40

# Initial ball direction and movement 
ballDir = 2
ballMove = 1

thumby.display.setFPS(45) # set frame rate, between 30-60 is usually best

# Begin main game loop that runs for the course of the game
while(1):
    thumby.display.fill(0) # Fill canvas to black

    # Ball movement directions following the pattern:
    #   3 \/ 2
    #   0 /\ 1
    if ballDir == 0: 
        ballSprite.x -= ballMove # left-down
        ballSprite.y += ballMove
    if ballDir == 1:
        ballSprite.x += ballMove # right-down
        ballSprite.y += ballMove
    if ballDir == 2:
        ballSprite.x += ballMove # right-up
        ballSprite.y -= ballMove
    if ballDir == 3:
        ballSprite.x -= ballMove # left-up
        ballSprite.y -= ballMove
        
    # DETECT BALL COLLISION WITH WALL & REDIRECT BALL
    if ballSprite.x <= 0 and ballDir == 0: # left side of screen |/ 0-ld, 2-ru
        ballDir = 1                        #                     |\ 1-rd, 3-lu
    elif ballSprite.x <= 0 and ballDir == 3: 
        ballDir = 2
    elif (ballSprite.x + 4) >= 72 and ballDir == 1: # right side of screen 
        ballDir = 0
    elif (ballSprite.x + 4) >= 72 and ballDir == 2: 
        ballDir = 3
    elif ballSprite.y <= 0 and ballDir == 2: # top of screen
        ballDir = 1
    elif ballSprite.y <= 0 and ballDir == 3: 
        ballDir = 0
    elif (ballSprite.y + 4) >= 40 and ballDir == 1:  # bottom of screen 
        ballDir = 2
    elif (ballSprite.y + 4) >= 40 and ballDir == 0: 
        ballDir = 3

    # DISPLAY SPRITES & UPDATE SCREEN
    thumby.display.drawSprite(ballSprite)
    thumby.display.update()
```