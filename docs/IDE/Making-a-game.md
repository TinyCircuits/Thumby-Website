# How to Make a Game using the Thumby MicroPython API

 This tutorial will show you how to make a game to the in the [**Thumby Editor IDE**](https://tinycircuits.github.io/ "Thumby Editor")!

To get some background on the features of the Thumby IDE, please go through the **[Thumby Getting Started Tutorial](https://tinycircuits.com/blogs/thumby/building-a-game-with-the-thumby-ide?_pos=3&_sid=e70ee7a2a&_ss=r "Thumby getting started with the ide tutorial")**. The rest of this tutorial assumes you are familiar with the tool!

---

## Materials 


### Hardware: 

*   **[Micro USB Cable](https://tinycircuits.com/collections/accessories/products/micro-usb-cable-3-feet)**
*   **Thumby** (optional)

### Software: 

*   [**TinyCircuits Thumby Editor IDE website**](https://tinycircuits.github.io/ "Thumby Editor")

*   **[Google Chrome](https://www.google.com/chrome/ "Google Chrome Download")** or **[Microsoft Edge](https://www.microsoft.com/en-us/edge "Microsoft Edge Download")** web browsers (other browsers not supported)

---

## Emulator First, Thumby Hardware Whenever 


You do not need the Thumby hardware to be able to make a Thumby game, you can get started right away using our free web browser Integrated Development Environment (IDE). Open a Google Chrome or Microsoft Edge window and navigate to the [**online Thumby IDE**](https://tinycircuits.github.io/ "Thumby IDE").

Whenever you are ready to upload your game to a Thumby, simply plug in the Thumby to your computer using a Micro USB cable and flip the power switch ON to the right. 

Connect your Thumby using the "CONNECT THUMBY" button at the top of the IDE, select the port your Thumby is connected to, and upload your game:

*   **Option 1:** 'Fast Execute' to upload just your game directly to the Thumby 
*   **Option 2:** Add your game to the list of games in the 'Filesystem' panel to make it playable from the Thumby default game list on the hardware

---

## Game Design Basics


The Thumby screen is a monochrome OLED with 72x40 drawable pixels. With this in mind, complex game graphics like those seen in modern games are not very possible with the limitations of the screen. Creating smaller game sprites and limiting text are some of the strategies that make simple games on Thumby work best. The Thumby API font implements a 5x7 character size, which leads to around 12 displayable characters per row, and 5 per column. So a story game with a lot of text may not be right type of game for the Thumby's screen size. 

### Conceptualizing and Visualizing Your Game

Steps:

1.  Create sample art of what gameplay might look like (if possible) - this will help you get started with creating game elements in the right size that you will need later on - keep in mind that the actual thumby screen is only 0.42" 
2.  Visualize a 72x40 grid for your game when you start creating sample sprites or art - you can use the bitmap builder available from the Thumby IDE to start drafting up some static images of gameplay. 


<center>![Thumby IDE bitmap builder of 72x40](https://cdn.shopify.com/s/files/1/1125/2198/files/image_1_af351171-657d-43c0-a525-28c3f2766846.png?v=1640597713)</center>
<center>_Thumby IDE bitmap builder of 72x40_</center>

You can make the bitmap builder full screen, zoom in, and draw up some bitmap ideas to help visualize the size and possibilities. Keep in mind that you will eventually want each bitmap, or game element by itself, rather than as a part of a full screen bitmap to keep your game efficient.

### Teaching Players How to Play Your Game (Optional)

Most games start with a tutorial to teach the player basic functions and actions the player can make to both play and (hopefully) win the game. Simple games like Snake, Tetris, or Flappy Birds might need no explanation at all given their popularity, but you will need to make that decision for your own individual game.

It's safe to assume a player will understand that the directional d-pad is used to move something in the game. For other functionality, it may be enough explanation to list what action each A/B button triggers in the game, what bad things to avoid in the game, or how to win the game. For example, with a brick breaker game it might suffice to say "Hit ball & break bricks".

---

## Programming

Once you know how your game should look, how it might work, and perhaps how to teach others to play - it's time to actually build the game! 

### List out, or think of each component & action

A great place to start is listing each Sprite, or viewable component of the game, and then what action each Sprite is capable of, how it interacts with other game Sprites, and what rules each Sprite needs to follow. For the brick breaker game there are three main components that interact with each other:

* **Ball Paddle** 

    *   Action: Move when the player uses the left and right buttons of the d-pad
    *   Interaction: Bounce **Ball** when the Sprites meet each other
    *   Rule: Should not leave the screen when moving left and right

*   **Ball**

    *   Action: Move through game after bouncing off a different object
    *   Interaction: Break **Bricks** that are touched during movement, and bounce off
    *   Interaction: Bounce off the **Ball Paddle** when touched 
    *   Interaction & Rule: when touching the edges of the screen, should bounce off instead of leaving the screen
    *   Rule: Disappear from screen when hitting the bottom

*   **Bricks** - there should be many of these on the screen

    *   View / Initialization: Appear on the screen in some pattern that makes sense
    *   Action: None, these bricks do not move

*   Moving bricks, however, could be a great future feature for different levels!

    *   Interaction: Break or disappear from screen when touched by the **Ball** - this involves collision detection
    *   Rule: All bricks are the same size and are 1 pixel away from each other

These above examples on component interactions & rules are how I think about a brick breaker game, but they are by no means the only possible way to think of the game or its components. Think about your game in whatever way makes sense to you - imagine all the different scenarios, placements, and interactions that are possible. Take notes, draw pictures, or just think about it!

### Review Thumby API and other Game Examples

The Thumby API includes functions and tools for some of the main building blocks to create a game. [**Review the documentation here**](/API/Get-Started "Thumby API documentation").

Luckily, there are also many public Thumby games available to peek through and use as examples when writing your own game. Navigate to the **Thumby Arcade** menu in the Thumby IDE, and open or download the code for any game with similar functionality that might help you write your own game.

### Create your game in small building steps and test it along the way!

At this point, you should have an idea of what your Sprites might look like and be able to start programming their actions.

To write the code, start with some of the easier components by themselves instead of trying to do everything at once. For example, start by importing the libraries you may use, and moving the Ball Paddle around the screen using the d-pad buttons:


```py
import time
import thumby
import math

padMap = bytearray([1,3,7,7,7,7,7,7,3,1]) # BITMAP: width: 10, height: 3
padSprite = thumby.Sprite(10, 3, padMap, key=0) # w, h, bitmapData, key

# Initial placement of ball and movable game pad
padSprite.x = 31
padSprite.y = 36

# Begin main game loop that runs for the course of the game
while(1):
    thumby.display.fill(0) # Fill canvas to black

    # MOVE BALL PADDLE
    if (thumby.buttonL.pressed() == True and padSprite.x > 0 ):
        padSprite.x -= 1
    if (thumby.buttonR.pressed() == True and padSprite.x < 62 ): # 72 - width of ball paddle Sprite (10)
        padSprite.x += 1

    # DISPLAY SPRITES & UPDATE SCREEN
    thumby.display.drawSprite(padSprite)
    thumby.display.update()
```

What the above program, we now have a movable **Ball Paddle**:

<center>![game paddle moving on the thumby screen when directional buttons are pressed](https://cdn.shopify.com/s/files/1/1125/2198/files/emulator_video.gif?v=1643147516)</center>

Then you can add other game elements, like the ability to lose the game, and the **Ball's** interaction with the **Ball Paddle** and constraints of the screen. For the direction of the **Ball** when hitting any of the walls, these are just numbered directions. This diagram might help the code make more sense:

<center>![Ball arrow direction diagram of thumby screen](https://cdn.shopify.com/s/files/1/1125/2198/files/brickd-game-ball-directions.png?v=1643669452)</center>
<center>_Ball direction image key_</center>

```py
import time
import thumby
import math

# Bitmaps
ballMap = bytearray([6,15,15,6]) # BITMAP: width: 4, height: 4
padMap = bytearray([1,3,7,7,7,7,7,7,3,1]) # BITMAP: width: 10, height: 3

# Sprite data
ballSprite = thumby.Sprite(4, 4, ballMap, key=0)
padSprite = thumby.Sprite(10, 3, padMap, key=0)
ballSprite.x = 33 # Initial placement of ball and movable game pad
ballSprite.y = 31
padSprite.x = 31
padSprite.y = 36

# Initial ball direction and movement 
ballDir = 2
ballMove = 1

# Game global variables
lose = False  
gameScore = 0 # keeps track of the number of bricks collided with
loopCtr = 0 # used to control the speed of the ball

# Begin main game loop that runs for the course of the game
while(1):
    thumby.display.fill(0) # Fill canvas to black

    # MOVE BALL PADDLE
    if (thumby.buttonL.pressed() == True and padSprite.x > 0 ):
        padSprite.x -= 1
    if (thumby.buttonR.pressed() == True and padSprite.x < 62 ): # 72 - width of ball paddle Sprite (10)
        padSprite.x += 1

    # MOVE BALL W/ MATH-GIC at half speed of game pad
    loopCtr += 1
    if(loopCtr % 2 == 0):
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
    
    # DETECT BALL COLLISION WITH MOVING PAD
    if (((ballSprite.y + 4) == padSprite.y) and ((ballSprite.x<= padSprite.x + 10) and (ballSprite.x + 4 >= padSprite.x))):
        if ballDir == 0:
            ballDir = 3
        if ballDir == 1:
            ballDir = 2
    
    # CHECK IF LOST GAME ;/
    if ballSprite.y >= 38: 
        lose = True

    # GAME OVER SCREEN
    if lose == True:
        thumby.display.fill(0)
        thumby.display.drawText("Game Over", 10, 5,1)

    # DISPLAY SPRITES & UPDATE SCREEN
    thumby.display.drawSprite(ballSprite)
    thumby.display.drawSprite(padSprite)
    thumby.display.update()
```

At this point, you have a moving Game Paddle that can bounce the Ball, the Ball can bounce against all the bounds of the game screen except the bottom of the screen which triggers the "Game Over" screen.

The code is getting pretty long, so let's just add the remaining components separately! You can comfortably fit around 3 rows of 10 bricks on the screen with the brick size 6x3. So we need to display all the bricks and make them able to store the data of being collided or not per each of the 30 bricks. I chose to implement this with a **Brick class** that holds a collision variable, and a function that will delete, or move the **Brick** off the screen when collision is detected.

With **Bricks** added to the game, we can keep score of how many are broken to Win the game! We can also add some more functionality to the Game Over menu to restart the game, or take the user back to the main Thumby menu using _machine.reset()._ These components:

```py
    # NOTE: library imports, ball, and pad variables should be here
    
    # Bitmaps
    ballMap = bytearray([6,15,15,6]) # BITMAP: width: 4, height: 4
    padMap = bytearray([1,3,7,7,7,7,7,7,3,1]) # BITMAP: width: 10, height: 3
    brickMap  = bytearray([7,7,7,7,7,7]) # BITMAP: width: 6, height: 3
    brickW = 6
    brickH = 3
    
    # Brick class to keep track of placement, collisions and delete (move off screen) state
    class Brick:
        def __init__(self, x, y, collisions):
            self.x = x
            self.y = y
            self.collisions = collisions
            
        def delete(self):
            self.x = -100
            self.y = -100
    
    # Create a list of bricks that covers three rows across the screen
    listOfBricks = []
    for i in range (0, 10):
        listOfBricks.append(Brick(1 + (i*7), 1, 0))
        listOfBricks.append(Brick(1 + (i*7), 5, 0))
        listOfBricks.append(Brick(1 + (i*7), 9, 0))
    
    
    # Begin main game loop
    while(1):
        thumby.display.fill(0) # Fill canvas to black
    
        # NOTE: Ball and Ball Paddle actions should be here
        
        # DETECT BALL COLLISION WITH BRICK
        for brick in listOfBricks:    
            # if ball at ballX * ballY checked against Brick.x + width, Brick y + height
            if (((ballSprite.x < brick.x + brickH) and (ballSprite.x + 4 > brick.x)) and ((brick.y < ballSprite.y + 4) and (brick.y + brickW > ballSprite.y))):
                brick.collisions = 1
                gameScore += 1
                
                if ballDir == 0: ballDir = 1
                if ballDir == 1: ballDir = 0
                if ballDir == 2: ballDir = 1
                if ballDir == 3: ballDir = 0
                
            if brick.collisions == 0:
                # thumby.display.blit(brickMap, brick.x, brick.y, brickW, brickH, 0, 0, 0)
                brickSprite.x = brick.x
                brickSprite.y = brick.y
                thumby.display.drawSprite(brickSprite) 
            else:
                brick.delete()
        
        # GAME OVER SCREEN
        if lose == True or gameScore == 30:
            thumby.display.fill(0)
            # CHECK IF WON GAME
            if gameScore == 30:
                thumby.display.drawText("You won!", 10, 5, 1) # text, x, y, color
            elif lose == True: # OR LOST...
                thumby.display.drawText("Game Over", 10, 5,1)
            
            thumby.display.drawText("Replay?", 15, 20, 1)
            thumby.display.drawText("A:N B:Y", 15, 30, 1)
            
            if time.ticks_ms() % 1000 < 500:
                thumby.display.drawLine(15, 37, 55, 37, 1) # (x1, y1, x2, y2, color)
            else:
                thumby.display.drawLine(15, 37, 55, 37, 0)
            
            if thumby.buttonA.pressed(): # go back to Thumby main menu
                machine.reset() 
                
            elif thumby.buttonB.pressed(): # Re-initialize values of variables to play again
                lose = False  
                gameScore = 0 
                loopCtr = 0 
                ballDir = 2
                ballMove = 1
                ballSprite.x = 33
                ballSprite.y = 31
                padSprite.x = 31
                padSprite.y = 36
            
                # Re-init list of bricks
                listOfBricks = []
                for i in range (0, 10):
                    listOfBricks.append(Brick(1 + (i*7), 1, 0))
                    listOfBricks.append(Brick(1 + (i*7), 5, 0))
                    listOfBricks.append(Brick(1 + (i*7), 9, 0))
                
        else:
            # NOTE: DISPLAY Ball and Ball Paddle sprites here
    
        # UPDATE SCREEN
        thumby.display.update()
```

With all the game functionality written, all that's left to add are the game start menu and game instructions so that others can play the game!

```py
    # NOTE: library imports and game variable initializations should be here
    
    # TITLE SCREEN 
    thumby.display.fill(0)
    thumby.display.drawRectangle(12, 4, 48, 12, 1) # x, y, w, h, color
    thumby.display.drawText("Brick'd", 16, 6, 1) # string, x, y, color
    for i in range(0, 5): # bricks across the screen for flare 
        thumby.display.drawFilledRectangle(1 + (i*14), 20, brickW, brickH, 1) # x, y, w, h, color
        thumby.display.drawFilledRectangle(8 + (i*14), 24, brickW, brickH, 1) 
    thumby.display.update()
    # Flashing line under Press A/B
    thumby.display.drawText("Press A/B", 10, 32, 1)
    while(thumby.buttonA.pressed() == False and thumby.buttonB.pressed() == False):
        if(time.ticks_ms() % 1000 < 500):
            thumby.display.drawLine(10, 39, 62, 39, 0)
        else:
            thumby.display.drawLine(10, 39, 62, 39, 1)
            
        thumby.display.update()
        pass
    # Game Instructions
    thumby.display.fill(0)
    thumby.display.drawText("Game Instr:", 0, 0, 1) # string, x, y, color
    thumby.display.drawLine(0, 8, 62, 8, 1)
    thumby.display.drawText("Hit Ball &", 0, 10, 1)
    thumby.display.drawText("Break Bricks", 0, 19, 1)
    thumby.display.update()
    time.sleep(4) # delay game for a few seconds so player can read instructions
    
    # NOTE: main game loop should be added here
```

Put it all together, and you have a playable Brick Breaker game, called _Brick'd._

At this point, you have a functional game that can be submitted to the Thumby Arcade to share your creation with other game developers and players. Or you can move on to the next step to add sound effects before submitting your game!

### Adding Audio

After adding everything else, this is arguably the simplest step, but it adds a lot to the gaming experience! You can choose to compose an entire backtrack song that plays for the course of your game, or you can just add a few key sound effects where interactions happen. 

Using the Thumby API function _thumby.audio.play(freq, duration, duty)_ you can play a tone at a frequency between 20Hz - 20,000Hz at a duration in milliseconds. You could technically play frequencies up to 125,000,000Hz, but humans can only hear sounds between around 20Hz and 20,000Hz - any higher than that and perhaps a dog or bat will be able to hear the sound effects, but not you! To get an idea on what some Hz values may sound like, you can find many YouTube videos that feature the spectrum of sounds:

<center><iframe width="560" height="315" src="https://www.youtube.com/embed/qNf9nzvnd1k" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></center>

The audio you execute will play without blocking any code execution - so if you play an entire song, everything else in your game will continue working while the song plays.

For Brick'd, I thought a happy noise when a brick is broken and a sad, continuous losing noise would be sufficient for sound effects.

```py
# Play a 'happy' sound when brick is deleted, at 440 hz for 300ms 
thumby.audio.play(440, 300) 

...

thumby.audio.play(260, 250) # losing sound
```

With everything working and added, all that's left to do is play-test to make sure everything's working. Then the game can be **[submitted to the Thumby Arcade for everyone to play](https://tinycircuits.com/blogs/learn/thumby-tutorial-submitting-a-game "submitting a thumby game to the IDE arcade via Github tutorial")**! 

---