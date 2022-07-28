# Hardware Reset

A great way to close your game when the player has finished playing is to offer a menu along the lines of "Play Again: B, Quit: A" To communicate to the player which button should be pressed to quit the game and return to the main menu, or to give them a chance to replay the game without restarting from the main menu. 

Since Thumby games are written in MicroPython, the main game files have a .py extension and function like any normal script written in refular Python. A acript is a sequence of instructions that is carried out and then ends, so it's possible that your game script is already ending and returning to the main menu by itself when the player is done playing your game. You can write and test your game in this way, or you can add the `.reset()` command to take out the possibility of any logic errors. 

This short example shows how it might be used to tell the player how to exit the game: 

```py 
import thumby
import time

while(True):
    thumby.display.fill(0)
    thumby.display.drawText("Press A to", 0, 0, 1)
    thumby.display.drawText("Exit.", 0, 10, 1)
    if(thumby.buttonA.justPressed()):
        thumby.display.fill(0)
        thumby.display.drawText("Exiting...", 0, 0, 1)
        thumby.display.update()
        time.sleep(2) # delay game for a few seconds so player can read closing message
        thumby.reset() # exit game to main menu
        
    thumby.display.update()
```

You can use the reset method by either importing the entire Thumby API using `import thumby` and then type `thumby.reset()` in your code where you want to return to the main menu, or you can import a submodule of the Thumby API `import thumbyHardware` and `thumbyHardware.reset()`. [**Submodule**](/API/Get-Started/#submodules) are available in Thumby API version 1.7 and later.