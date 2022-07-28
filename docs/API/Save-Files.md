# Save Game Data

So you want to keep track of your high score in a Thumby game, or you want to save some game data to pick up where you left off? Look no further than this section of the API! 

The save methods available from the thumby API: 

`thumby.saveData.setName(subdirectoryName)` | creates a persistent.json file for save data to Saves/`subdirectoryName`/persistent.json

* `subdirectoryName`
    * type: string
    * value: use the name of your .py game file to keep the Saves/ directory clearly organized per game. 

*Note: The /persistent.json save file created under the `subdirectoryName` will persist in the Saves/ directory when updating the game, or removing the game from the Thumby. So, you can feel safe removing games and trying out different games from the Thumby Arcade while maintaining saved game data.*

---

`thumby.saveData.setItem(key, value)` | set a save entry under the `key` string name with `value` variable

* `key`
    * type: string
    * value: name of the game data or variable you wish to save in Saves/`subdirectoryName`/persistent.json

* `value`
    * type: bytearray, bytes, float, integer, list (all elements need to be the same type and in this list), string, tuple (all elements need to be the same type and be in this list)
    * value: save data you wish to keep throughout different game plays 

---

`thumby.saveData.getItem(key)` | get a save entry under `key` string name. Returns `value` saved at `key`.

* `key`
    * type: string
    * value: name of the game data or variable you wish to retrieve data from in Saves/`subdirectoryName`/persistent.json

---

`thumby.saveData.hasItem(key)` | check if save entry under `key` string name exists. Returns true if `key` exists, returns false otherwise.

* `key`
    * type: string
    * value: match the string value of the data entry previously set

---

`thumby.saveData.delItem(key)` | delete save entry under `key` string name. Returns none.

* `key`
    * type: string
    * value: match the string value of the data entry previously set

---

`thumby.saveData.save()` | write all set save data to persistent.json save file


`thumby.saveData.getName()` | returns the current save path

---

## Save high score example

For this short program, we'll use two buttons:

* A - Increases the high score
* B - Saves and quits "game" to the Thumby main game menu (on the hardware)

```python
import thumby
import time    # added for delay at end of program

# Create a save file titled HighScore to match game .py name
# This will save a persistent.json file with save data to Saves\HighScore\persisten.json
thumby.saveData.setName("HighScore")

# Game variables
newScore = 0
highScore = 0

if (thumby.saveData.hasItem("highscore")):
    highScore = int(thumby.saveData.getItem("highscore"))

if(newScore > highScore):
    thumby.saveData.setItem("highscore", newScore)
    thumby.saveData.save()

while(True):
    # Print the save contents
    thumby.display.fill(0)
    thumby.display.drawText("High Score: " + str(highScore), 3, 0, 1)
    thumby.display.drawText(str(highScore), 30, 10, 1)
    thumby.display.drawText("New Score: ", 5, 20, 1)
    thumby.display.drawText(str(newScore), 30, 30, 1)
    thumby.display.update()
    
    # A button increases the score
    if(thumby.buttonA.justPressed()):
        newScore += 1
        
    # B button saves and quits
    if(thumby.buttonB.justPressed()):
        thumby.display.fill(0)
        # If we're done playing, check if high score is bigger and save it
        if(newScore > highScore):
            thumby.display.drawText("New High", 10, 0, 1)
            thumby.display.drawText("Score!: " + str(newScore), 7, 10, 1)
            thumby.saveData.setItem("highscore", newScore)
            thumby.saveData.save()
        thumby.display.drawText("Saved & quit", 0, 30, 1)
        thumby.display.update()
        
        # Exit to game menu
        time.sleep(2) # delay game for a few seconds so player can read closing message
        thumby.reset()
```

As the program is written, you can save the above code in a file named "HighScore.py" and add the file under the Games folder on Thumby. *Note: Emulating this code in the Thumby Code Editor won't display the high score from the save file - test this program on the Thumby hardware for functionality.*
