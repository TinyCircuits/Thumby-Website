# IDE Widgets and Panels

There are a few different widgets, or panels, to assist with programming Thumby. From left to right: 

* **Filesystem** - Displays all the files on the Thumby when a Thumby is connected to the IDE
* **Bitmap Builder** - A bitmap editor for simple, small graphics. Other drawing tools with more features, like GIMP, are recommended for more complex animating. 
* **Code Editor** - This is where the magic (code) happens!
* **Shell** - This terminal will print errors, and other helpful messages as you program and debug with Thumby.
* **Emulator** - Emulates the current program 'checked' for emulation in the **Code Editor** when 'Start' is pressed

---
## Filesystem

Thumby’s Filesystem. Manage all files on Thumby. Left click a file to delete. Right click a file to rename and open it in the editor. See **Thumby Filesystem structure** to learn more about properly organizing your code files to display correctly on Thumby.

* FORMAT: Delete all files on your Thumby and replace with default Thumby files and folders. Reboot your Thumby filesystem to a clean slate. 
* UPLOAD: Upload multiple files from your computer to Thumby fast. Similar to SAVE TO THUMBY and SAVE AS TO THUMBY buttons in the Editor without needing to open files one at a time. 

### Thumby Filesystem Structure



Ensure that you understand Thumby’s filesystem and have the required files in the correct locations for games to run properly. 

main.py: The first script to be run when Thumby powers on. It sets up the Thumby and runs the main screen.
menu.py: Displays the Thumby menu. 
thumby.cfg: A file used by main.py and menu.py to store settings. Users typically should not care about this.

lib folder (directory)
Files required for running Thumby and Thumby’s main program. Most users do not need to touch this. 
ssd1306.py: The display driver code for the Thumby screen. 
thumby.py: The main API users use to render code on the Thumby screen and interact with Thumby buttons.
credits.txt: All our supporters who backed our campaign!
Games folder
Where Thumby game files are stored. 
For every game, there should only be 1 main python script to run. 
Place your game file in /Games/MyNewGame/MyNewGame.py for it to display on the Thumby main screen. Make sure your python file has the exact same name as the game. Ie. if the game is called TinyBlocks, the source file is named TinyBlocks.py
Submitting a game for the arcade
Python file with the same name as the game. Ie. if the game is called TinyBlocks, the source file is named TinyBlocks.py
.png (image) or .webm (video) file: Image or video of gameplay. Filename does not matter, but file extension is required for either file. If both files are present, the .webm file will be used. Please keep image and video resolution between anything from 8x (576x320px) to 16x (1152x640px).
.txt file: Description of game that appears when user hovers over the game in the Thumby.


---
## Bitmap Builder

A simple drawing interface to create and edit code bitmaps. Left click to set pixels to black. Right click to set pixels to white. 

* EXPORT: In the Editor, left click the location in your code you want to EXPORT your drawing data to, then click the EXPORT button to export the drawing data.
* IMPORT: Highlight a bitmap in your code and IMPORT it to view on the bitmap builder.
* IMAGE: Import your own IMAGE to be converted into a bitmap. Most image formats will work, but the maximum image size is 2x Thumby display dimensions, so 144x80px. An error will appear if the image exceeds maximum size. 
* SIZE: Change the SIZE (width and height) of the bitmap. Bitmaps and sprites can be as large as the user wants. However, the bitmap builder can only handle images up to 144x80px. The larger the bitmap or sprite, the slower the Thumby will render it. 32x32 was an arbitrary decision for the Animating Your First Sprite Tutorial that gave us enough pixels to detail our sprite. 
* Zoom in/out using the +/-.

---
## Code Editor

Where you write your code. By default, the editor will have a Thumby sprite animation preloaded in it. If you have hidden editors open, the little green arrow on the top right of the Editor window will display all hidden editors. There is a reskin of the IDE that would make switching between Editor tabs easier. 

* FILE:

    * NEW FILE: create a new file. Coming in the reskin. For now, use UTILITIES-> MAKE NEW GAME.
    * EXPORT TO PC: save your file to your computer.
    * IMPORT FROM PC: open a .py file in the Editor.
    * SAVE TO THUMBY: upload your file to the Thumby filesystem to the current path (set path via SET PATH). 
    * SAVE AS TO THUMBY: choose a new path/location on the Thumby filesystem to save the file to, then upload your file to the Thumby filesystem. You can also rename your file this way. 
    * SET PATH: User can set desired Thumby filesystem path to save the file to. You can also rename your file this way. 
    * EXAMPLES: This is an old button that will be removed. All games are available through the arcade. 

* VIEW: Change display of Editor. Adjust and reset font size. Toggle live autocomplete.
* FAST EXECUTE: 
* EMULATION: Click both the white and red checkbox to test the file in the Emulator. The white box uploads the file (script) to the emulator’s filesystem. The red box designates a script as the main script to run. Because of how Thumby works, only 1 file (main script, red checkbox) can be executed at a time. However, users may want to include other files that are not the main script during emulation (ie. binary sprite files or other modules). Check the white box for those supplementary files. This will be updated for clarity and ease in the re-skin of the IDE. 

---
## Shell

Terminal that displays output from running MicroPython games. The running code in the emulator or connected hardware will display here. Examples of possible output: successful connection of Thumby, successful upload of code to Thumby or emulator.

---
## Emulator

Emulates what your code will look like on Thumby, so you can develop games without a physical Thumby. The emulator does not display the main menu; it only runs the main python file (and other sprite files etc.). To “press a button”, either click on it using your mouse, or use the keys W A S D for the d pad, . for A, and , for B.

To upload a file to the emulator, check the white and red checkboxes in the Editor widget with the file you want to emulate. The white box uploads the file (script) to the emulator’s filesystem. The red box designates a script as the main script to run. Because of how Thumby works, only 1 file (main script, red checkbox) can be executed at a time on the device. However, users may want to include other files that are not the main script during emulation (ie. binary sprite files or other modules). Check the white box for those supplementary files. To be updated in the reskin of the IDE. 

* STOP: Stop emulation.
* START: Start emulation. 
* Zoom in/out using +/-. The circle on the left corner shows how many times the image is zoomed.
* ↻: Rotate Thumby display
* FILES: see the file(s) being run in the Emulator.
* 📷: Captures a snapshot of the emulation screen to your computer. 
* 🎥: Captures a .webm video of the emulation screen to your computer. Press the button to start recording. The button will turn red. Press again to stop. 

---
## Resizing Widgets

Click and drag the left/right edges of the widgets to resize the windows. Click on the tab name and drag to reorganize the layout. Click the top right to minimize/maximize the window. Click x to close the widget. Add a widget to your layout using 'Utilities' -> 'Widgets'. 


