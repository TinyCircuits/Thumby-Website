# Making Sprites

It's time to paint some pictures, and load them in your game!

This tutorial will introduce you to Sprites in the Thumby Code Editor, and how to load them in your Blockly workspace. It will then show you how to display them in your game, but it won't yet show you how to move them around in your game.

---

Let's get started!

Games sometimes have title screens that display the name of the game, and maybe a picture, just before the game loads. It can be nice way to make the game more pretty, and have more character.

We are going to make a title screen for a game (actually for the one we made in the previous tutorial), and show it on screen briefly, by making and display a Sprite.

---

Sprites are pictures that you can hand draw, or load from a picture file, which you can put in your game, move about, flip, mirror, and even make animations with! For this tutorial, we are just going to make a Sprite that fills the whole screen and display it for a few seconds.

---

## Drawing Sprites

First let's make a Sprite!

* Grab a <img src="../../images/editor-blockly-sprite-block.png" alt="[load sprite]" style="height:2.4em"> block from the **Sprites** category, and place it into an empty part of your workspace above any other blocks you might have in your workspace.

Putting it higher up makes it run first.

We now have a Sprite in our workspace that has been given a default name. Let's change it to something better.

* Right click on the dropdown at the end of your <img src="../../images/editor-blockly-sprite-block.png" alt="[load sprite]" style="height:2.4em"> block and click on "**Rename Sprite**".
* Give it the name "**title**".

---

Now let's display it on screen. First, we need to draw it to the next frame, then we need to send the frame to the display.

* Grab a <img src="../../images/editor-blockly-draw-sprite-title-block.png" alt="[draw title]" style="height:2.0em"> block from the **Sprites** category and add it underneath your load sprite block.
* Now add a <img src="../../images/editor-blockly-send-drawn-combo-block.png" alt="[send drawn frame to display] and [draw fill]" style="height:2.8em"> combo block underneath that.
* After that, add a <img src="../../images/editor-blockly-wait-block.png" alt="[wait]" style="height:2.0em"> block from the **Flow** category to make sure the Sprite shows on the display for a while. Change the value from "1" to "3" so the Sprite shows on the display for 3 seconds.
* Run it:

<center>
![Thumby blockly title stage1](../images/editor-blockly-title1.png)
</center>

Sweet!... Wait... Where did that picture come from? All Sprites come with a default picture already loaded. That is what you are seeing there.

---

**⚠ Note**: *Be careful when you delete <img src="../../images/editor-blockly-sprite-block.png" alt="[load sprite]" style="height:2.4em"> blocks, as the picture data they contain will be lost! You can keep a copy of them in the corner of your workspace just to be safe!*

Our next step is to change the picture!

---

## The Bitmap Builder

Sprites can have their pictures changed using the [**Bitmap Builder Widget**](../../Code-Editor/Widget-panels/#bitmap-builder).

Let's try to find the Bitmap Builder. It might be next to the Filesystem tab:

<center>
![Thumby blockly bitmap builder tab dark](../images/editor-blockly-bitmap-tab-dark.jpg)
</center>

Or it might be in the hidden-tab dropdown:

<center>
![Thumby blockly bitmap builder hidden tab dark](../images/editor-blockly-bitmap-hidden-tab-dark.jpg)
</center>

Or you might need to open it again with **UTILITIES** -> **WIDGETS** -> **+ BITMAP BUILDER**.

---

Once you have found it, it should look like this:

<center>
![Thumby bitmap builder dark](../images/editor-bitmap-builder-dark.jpg)
</center>

---

### Loading Sprites To The Bitmap Builder

To load a sprite from your workspace into the Bitmap Builder, you use the **IMPORT** button, but the Bitmap Builder needs to know which Sprite you want to open (you might have more than one), so you must make sure a <img src="../../images/editor-blockly-sprite-block.png" alt="[load sprite]" style="height:2.4em"> block is selected in your workspace.

* Select the <img src="../../images/editor-blockly-sprite-block.png" alt="[load sprite]" style="height:2.4em"> block in your workspace for the "**title**" Sprite.
* Click **IMPORT**.

You should see the Thumby Sprite loaded:

<center>
![Thumby bitmap builder of thumby dark](../images/editor-bitmap-builder-thumby-dark.jpg)
</center>

---

### Updating Sprites on the Workspace

First, we make some changes to the Sprite picture, then we update the Sprite back on our workspace.

* Click **INVERT** which will swap the colors.
* Make sure the <img src="../../images/editor-blockly-sprite-block.png" alt="[load sprite]" style="height:2.4em"> block in your workspace is still selected.
* Click **EXPORT**.

You should see that the pictures in the <img src="../../images/editor-blockly-sprite-block.png" alt="[load sprite]" style="height:2.4em"> blocks update:

<center>
![Thumby blockly load sprite block updated](../images/editor-blockly-load-sprite-block-updated.png)
</center>

Nice!

* Now run it!

<center>
![Thumby blockly sprite inverted running](../images/editor-blockly-sprite-inverted-running.png)
</center>

Title screens look best when they fill the whole screen and where they have been customized for the game. Let's do both next.

---

### Using the Bitmap Builder to Paint

First, let's make the Sprite the same size as the screen. The Thumby screen is 72 pixels wide, and 40 pixels high.

---

#### Resizing Sprites

**⚠ Note**: *Resizing your sprite will clear its contents. Don't resize your picture unless you don't mind losing it, or unless you have stored it back in your workspace.*

* Click **SIZE**.
* Enter **72** for the width and click **OK**.
* Enter **40** for the height and click **OK**.

You should now have a blank white drawing area with lots more pixels!

**⚠ Note**: *The Bitmap Builder has a maximum image size of 144 wide, and 80 tall, which is much larger than the Thumby screen!*

---

#### Drawing

To draw on the picture, use the mouse **Left Click** to draw black pixels, and use **Right Click** to draw white pixels. You can drag across the screen to scribble.

If you want to start over, use the **CLEAR** button to reset the whole picture to white.

To zoom in and out of the picture, use the **⊕** and **⊖** buttons.

---

### Opening Image Files From Your Computer

You can use the **IMAGE** button to open files from your computer. They will be automatically converted to black and white. The image file you open must not be larger than 144 wide and 80 high. Most image file formats will work.

* Try downloading the image to your computer and loading into the Bitmap Builder with the **IMAGE** button. Download this image:
<center>
![Thumby speed buzzer title screen](../images/speed-buzzer-title-screen.png)
<br>(Speed Buzzer Title Sprite 72x40)
</center>

* Now update the Sprite in your workspace with **EXPORT** and then run it with **START** to see what happens!

<center>
![Thumby blockly sprite title running](../images/editor-blockly-sprite-title.png)
</center>

---

[**Next Tutorial: Drawing and Dynamics**](../Drawing-and-Dynamics/)
