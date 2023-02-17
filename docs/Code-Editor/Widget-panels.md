# Thumby Code Editor Widgets and Panels

There are a few different widgets, or panels, to assist with programming Thumby. From left to right: 

* **Filesystem** - Displays all the files on the Thumby when a Thumby is connected to the Code Editor
* **Bitmap Builder** - A bitmap editor for simple, small graphics. Other drawing tools with more features, like GIMP, are recommended for more complex animating. 
* **Code Editor** - This is where the magic (code) happens!
* **Shell** - This terminal will print errors, and other helpful messages as you program and debug with Thumby.
* **Emulator** - Emulates the current program 'checked' for emulation in the **Code Editor** when 'Start' is pressed

---
## Filesystem

Thumby’s Filesystem. Manage all files on Thumby. Left click a file to delete. Right click a file to rename and open it in the editor. See **Thumby Filesystem structure** to learn more about properly organizing your code files to display correctly on Thumby.

* The storage available on the connected Thumby in MB is shown in a green storage bar at the top of the Filesystem.
* FORMAT: Delete all files on your Thumby and replace with default Thumby files and folders. Reboot your Thumby filesystem to a clean slate. 
* UPDATE: Update the firmware on the connected Thumby to the latest version. Will appear in pink if the firmware version detected on the connected Thumby is out of date.
* UPLOAD: Upload multiple files from your computer to Thumby fast. Similar to SAVE TO THUMBY and SAVE AS TO THUMBY buttons in the Editor without needing to open files one at a time. 
* ↻: Refresh the filesystem.


### Thumby Filesystem Structure

Ensure that you understand Thumby’s filesystem and have the required files in the correct locations for games to run properly. 

main.py: The first script to be run when Thumby powers on. It sets up the Thumby and runs the main screen.
menu.py: Displays the Thumby menu. 
thumby.cfg: A file used by main.py and menu.py to store settings. Users typically should not care about this.

#### lib folder (directory)

Files required for running Thumby and Thumby’s main program. Most users do not need to touch these files: 

* ssd1306.py: The display driver for the Thumby OLED screen. 
* thumby.py: The Thumby MicroPython library / API users use to render pixels and sprites on the Thumby screen and interact with Thumby buttons.
* credits.txt: The names and messages of our Special Edition kit supporters who backed our <a href="https://www.kickstarter.com/projects/kenburns/thumby-the-tiny-playable-keychain" target="_blank" alt="TinyCircuits Thumby Kickstarter page">**Kickstarter campaign**</a>!


#### Games folder

Where Thumby game files are stored. 

For every game folder, there should be a main python script to run that is the same name of the folder. 

To add your game to Thumby, place the game file in */Games/MyNewGame/MyNewGame.py* to add it to the playable Thumby 'GAMES' list. Make sure your python file has the exact same name as the game: i.e. if the game is called *TinyBlocks*, the source file is named *TinyBlocks.py*. The title is case sensitive, so *tinyblocks.py* would not work.

> For more information, check out this page: [**Submitting a Game to the Thumby Arcade**](../Code-Editor/Submit-Game.md)

---
## Bitmap Builder

A simple drawing interface to create and edit code bitmaps. Left click to draw black pixels. Right click to draw white pixels.

* SIZE: Change the SIZE (width and height) of the bitmap. Bitmaps and sprites can be as large as the user wants. However, the bitmap builder can only handle images up to 144 × 80 px. The larger the bitmap, the slower it will be rendered to the Thumby display.
* +/-: Zoom in/out of the Bitmap Builder using the +/- buttons.
* EXPORT: Put your mouse cursor at the location in your Code Editor you want to export your drawing data to, then click the EXPORT button. A comment with size dimensions and a bitmap will be printed in the Code Editor.
* IMPORT: Highlight a bitmap and the exported dimensions comment in your code and click IMPORT to view the drawing in the Bitmap Builder.
* IMAGE: Import your own IMAGE to be converted into a bitmap. Most image formats will work, but the maximum image size is 2× Thumby display dimensions,  144 × 80 px. An error will appear if the image exceeds maximum size. 
* INVERT: Inverts black and white pixels to white and black pixels, respectively. 
* CLEAR: Clears the bitmap editor to white pixels.

---
## Code Editor

Where code is made and displayed. By default, the editor will have a Thumby sprite animation program preloaded in it. The editor comes in two flavors, MicroPython (the default) for text-based coding, and Blockly for visual block-based programming. If you have several editor tabs open, the little green arrow on the top right of the Editor window will display any hidden editors when clicked.

* FILE:

    * EXPORT TO PC: save your file to your computer.
    * IMPORT FROM PC: open a .py file in the Editor.
    * SAVE TO THUMBY: upload your file to the Thumby filesystem to the current path (set path via SET PATH). 
    * SAVE AS TO THUMBY: choose a new path/location on the Thumby filesystem to save the file to, then upload your file to the Thumby filesystem. You can also rename your file this way. 
    * SET PATH: User can set desired Thumby filesystem path to save the file to. You can also rename your file this way. 
    * NEW TAB: Open a new empty editor tab for MicroPython coding.
    * NEW BLOCKLY TAB: Open a new empty editor tab for Blockly programming. 
    * You can also create new Code Editor MicroPython file, using UTILITIES-> MAKE NEW GAME.

* VIEW: Change display of Editor. Adjust and reset font size. Toggle live autocomplete (MicroPython only).
* OPEN PYTHON: Open a new editor tab with the contents of the Blockly program converted to MicroPython (Viewable in Blockly Editor only).
* FAST EXECUTE: When pressed, will execute a single file at the root level of a connected Thumby device. 
* EMULATION: Click both the white and red checkbox to test the file in the Emulator. The white box uploads the file (script) to the emulator’s filesystem. The red box designates a script as the main script to run. Because of how Thumby works, only 1 file (main script, red checkbox) can be executed at a time. However, users may want to include other files that are not the main script during emulation (e.g. binary sprite files or other modules). Check the white box for those supplementary files. 

---
## Shell

Terminal that displays output from running MicroPython games. The running code warnings/errors/printouts in the emulator and connected hardware status messages will also display here. Examples of possible output: successful connection of Thumby, successful upload of code to Thumby or emulator.

---
## Emulator

This panel with a virtual Thumby emulates what your code will look like on the hardware, so you can develop games without a physical Thumby. To play games on the Emulator or interact with your code, click on the virtual Thumby buttons using your mouse, or use the keys 'W' 'A' 'S' 'D' for the directional-pad, and use '.' and ',' for the A and B action buttons.

The emulator will not display the main game menu seen on the Thumby hardware, it will only emulate files in the Code Editor that are selected for emulation.

To upload a file to the emulator, check the white and red checkboxes in the Code Editor panel with the file you want to emulate. The white box uploads the file (script) to the emulator’s filesystem. The red box designates a script as the main script to run. Because of how Thumby works, only 1 file (main script, red checkbox) can be executed at a time on the device. However, users may want to include other files that are not the main script during emulation (e.g. binary sprite files or other modules). Check the white box for those supplementary files.

* STOP: Stop emulation.
* START: Start emulation of the checked files in the Code Editor. 
* +/-: Zoom in/out using. The circle in the left corner shows how many times the image has been zoomed.
* ↻: Rotate the virtual Thumby 
* MUTE/UNMUTE: Toggle the emulated volume off or on.
* FILES: see the file(s) being run in the Emulator.
* 📷: Captures a snapshot of the emulation screen to your computer. 
* 🎥: Captures a .webm video of the emulation screen to your computer. Press the button to start recording - the button will turn red. Press again to stop. 

*Speed Note: Your code will run faster on the Thumby hardware than on the Emulator. To standardize game speed, make sure to set the [**FPS**](../API/Graphics.md) value in your program.*

---
## Resizing Widgets

Click and drag the left/right edges of the widgets to resize the windows. Click on the tab name and drag to reorganize the layout. Click the top right to minimize/maximize the window. Click x to close the widget. Add a widget to your layout using 'Utilities' -> 'Widgets'. 

---
## Other tabs

* Tutorial: Redirects to the Getting Started Thumby Code Editor tutorial.
* Thumby API: Redirects to the MicroPython API documentation with examples.
* Add Game To Arcade: Redirects to the relevant tutorial.
* Other Links:
    * Thumby Website: Redirects to the Thumby Documentation Website (this website).
    * Report a Bug: Redirected to GitHub issues for reporting any bugs with the Editor.
    * Changelog: The documentation on changes that have been made and features that have been added to the Code Editor.
    * Forums: Redirects to the TinyCircuits forum that includes a 
    * Store: Redirects to the TinyCircuits store where Thumby will be purchasable. 
    * Contact Us: Redirects to our contact form for customer support. 
* Version XX.XX.XXXX_X: The last day the Code Editor was updated.
