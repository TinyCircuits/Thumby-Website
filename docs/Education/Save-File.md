# Save Game Data Forever

So you want to keep track of your high score in a Thumby game, or you want to save some game data to pick up where you left off? Look no further than this tutorial! 

We have a simple example for saving a high score to a .txt file as well as two extended examples that save an integer, float, and string using either a .txt file or .json file. 

---

## Save a high score

For this short program, we'll use two buttons:

* A - Increases the high score
* B - Saves and quits "game" to the Thumby main game menu (on the hardware)

The steps we need to program in order to save a high score number to a save file are as follows: 

* Try to open the save file if returning to play or create a new one during the first play
* Load `highScore` variable from the saveFile.txt, or initiate it to 0 (or the lowest score possible)
* Enter the game loop
    * Increase the high score using button A and print score to the screen
    * Exit game loop when B button is pressed 
* Erase the previous save file and write a new one with the newest `highScore` value
* *Important*: Close the save file after use - <a href="https://stackoverflow.com/questions/25070854/why-should-i-close-files-in-python" target="_blank" alt="stackoverflow post answering why closing files is important">**read more about why you should close files in Python**</a>

```python
import thumby
import os

# If a saved file exists, try to open and read from it
try:
    saveFile = open("Games/HighScore/saveFile.txt", "r+")                     # 'r+' will throw an exception if the file does not exist
    
except OSError:
    # print("saveFile.txt does not exist, creating...")
    
    saveFile = open("Games/HighScore/saveFile.txt", "w+")                     # 'w+' will create the file if it does not exist
    saveFile.write("HighScore 0") # Write default data to the save file
    saveFile.seek(0, 0)                                       # Because we wrote data, we need to go back to the beginning of the file

# Now that we have either loaded or made the save file, let's read the data from it
saveData = saveFile.read().split()

for i in range(len(saveData)):
    # Scan for our saved data. If the i-th string is the name of a piece of data,
    # we care about, then the next string is the data itself.
    if saveData[i] == "HighScore":
        highScore = int(saveData[i+1])

# Game variables
playing = True

while(playing):
    # Print the save contents
    thumby.display.fill(0)
    thumby.display.drawText("High Score: ", 5, 10, 1)
    thumby.display.drawText(str(highScore), 30, 20, 1)
    thumby.display.update()
    
    # A button increases the score
    if(thumby.buttonA.justPressed()):
        highScore += 1
        
    # B button saves and quits
    if(thumby.buttonB.justPressed()):
        thumby.display.drawText("Saved & quit", 0, 30, 1)
        thumby.display.update()
        playing = False

# If we're done playing, delete the old save and write the new data
saveFile.close()
os.remove("Games/HighScore/saveFile.txt")

saveFile = open("Games/HighScore/saveFile.txt", "w")
saveFile.write("HighScore " + str(highScore))

# Clean up
saveFile.close()
```

As the program is written, you can save the above code in a file named "HighScore.py" and add the file under the Games folder on Thumby. *Note: Emulating this code in the Thumby Code Editor won't work after the initial Save & Quit action.*

Some improvements that could be made to this example:

* Add a check if the newest score is higher than the previous high score in the saveFile.txt
* You will likely be using buttons for gameplay, so work in saving the game data when it makes sense in your game's flow rather than attaching the save logic to a button (unless that works for you!)
    * Example: The player just lost your game. Once the losing message/screen is displayed, check the score they achieved against the current high score and update the saved high score (or don't) accordingly.
* A .txt file works great, but you can use a .json file to shorten your program by a few lines when saving more data

For saving more than a single number for a high score, check out the below, extended examples!

---

## Save an integer, float, and string

Both examples below function using the same button actions, and produce the same results. The button controls:

* D-pad Left/Right - Increases or decreases the Integer variable by 1
* D-pad Up/Down - increase or decreases the Float variable by 0.2
* A - Randomly changes the String variable greeting
* B - Saves and quits "game" to the Thumby main game menu (on the hardware)

When these examples are loaded onto the Thumby hardware as is, the save files will be generated in the main directory. To change the save file's location, edit the file path. For example, change every mention of `"saveFile.txt"` or `"saveFile.json"` to `"Games/GameFolderName/saveFile.txt"` or `"Games/GameFolderName/saveFile.json"`, respectively.

---

### Save to a .txt file

Works just like the high score example above, but adds a few more data types:

```py
import thumby
import random
import os

try:
    # If a saved file exists, try to open and read from it
    saveFile = open("saveFile.txt", "r+")                     # 'r+' will throw an exception if the file does not exist
    
except OSError:
    print("savefile does not exist, creating...")
    
    saveFile = open("saveFile.txt", "w+")                     # 'w+' will create the file if it does not exist
    saveFile.write("firstnumber 0 secondnumber 0 word hey") # Write default data to the save file
    saveFile.seek(0, 0)                                       # Because we wrote data, we need to go back to the beginning of the file


# Now that we have either loaded or made the save file, let's read the data from it
saveData = saveFile.read().split()

for i in range(len(saveData)):
    # Scan for our saved data. If the i-th string is the name of a piece of data,
    # we care about, then the next string is the data itself.
    if saveData[i] == "firstnumber":
        firstNum = int(saveData[i+1])
        
    elif saveData[i] == "secondnumber":
        secondNum = float(saveData[i+1])
        
    elif saveData[i] == "word":
        word = saveData[i+1]

print(saveData)

running = True
while(running):
    # Make sure the numbers are reasonably sized
    firstNum %= 100
    secondNum %= 100
    
    # Print the save contents
    thumby.display.fill(0)
    thumby.display.drawText("int: "+str(firstNum), 0, 0, 1)
    thumby.display.drawText("float: "+str(secondNum), 0, 10, 1)
    thumby.display.drawText("word: "+word, 0, 20, 1)
    thumby.display.update()
    
    # D-pad Left/Right change the first number
    if(thumby.buttonL.justPressed()):
        firstNum -= 1
    if(thumby.buttonR.justPressed()):
        firstNum += 1
    
    # D-pad Up/Down change the second number
    if(thumby.buttonD.justPressed()):
        secondNum -= 0.2
    if(thumby.buttonU.justPressed()):
        secondNum += 0.2
    
    # A button changes the word
    if(thumby.buttonA.justPressed()):
        word = random.choice(("hey", "hi", "yo", "hello"))
        
    # B button saves and quits
    if(thumby.buttonB.justPressed()):
        thumby.display.drawText("Saved & quit", 0, 30, 1)
        thumby.display.update()
        running = False

# If we're done running, delete the old save and write the new data
saveFile.close()
os.remove("saveFile.txt")

saveFile = open("saveFile.txt", "w")
saveFile.write("firstnumber "+str(firstNum)+" secondnumber "+str(secondNum)+" word "+word)

# Clean up
saveFile.close()
```

---

### Save to a .json file (shorter!)

This example produces the same results as the above .txt code, but uses a .json save file type instead. This version uses a few less lines of code and might make more sense to you: 

```py
import thumby
import random
import json
import os

try:
    # If a saved file exists, try to open and read from it
    saveFile = open("saveFile.json", "r+")                                 # 'r+' will throw an exception if the file does not exist
    
except OSError:
    print("savefile does not exist, creating...")
    saveFile = open("saveFile.json", "w+")                                 # 'w+' will create the file if it does not exist
    json.dump({"firstnumber":0, "secondnumber":0, "word":"hey"}, saveFile) # Write default data to the save file
    saveFile.seek(0, 0)                                                    # Because we wrote data, we need to go back to the beginning of the file

# Now that we have either loaded or made the save file, let's read the data from it
saveData = json.load(saveFile)
firstNum = saveData["firstnumber"]
secondNum = saveData["secondnumber"]
word = saveData["word"]
running = True

while(running):
    
    # Make sure the numbers are reasonably sized
    firstNum %= 100
    secondNum %= 100
    
    # Print the save contents
    thumby.display.fill(0)
    thumby.display.drawText("int: "+str(firstNum), 0, 0, 1)
    thumby.display.drawText("float: "+str(secondNum), 0, 10, 1)
    thumby.display.drawText("word: "+word, 0, 20, 1)
    thumby.display.update()
    
    # D-pad L/R change the first number
    if(thumby.buttonL.justPressed()):
        firstNum -= 1
    if(thumby.buttonR.justPressed()):
        firstNum += 1
    
   # D-pad U/D change the second number
    if(thumby.buttonD.justPressed()):
        secondNum -= 0.2
    if(thumby.buttonU.justPressed()):
        secondNum += 0.2
    
    # D-pad Up/Down change the second number
    if(thumby.buttonA.justPressed()):
        word = random.choice(("hey", "hi", "yo", "hello"))
        
    # B button saves and quits
    if(thumby.buttonB.justPressed()):
        thumby.display.drawText("Saved & quit", 0, 30, 1)
        thumby.display.update()
        running = False

# If we're done running, delete the old save and write the new data
saveFile.close()
os.remove("saveFile.json")
saveFile = open("saveFile.json", "w")
json.dump({"firstnumber":firstNum, "secondnumber":secondNum, "word":word}, saveFile)

# Clean up
saveFile.close()
```