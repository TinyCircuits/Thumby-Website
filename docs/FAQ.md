---
hide:
  - navigation
---


# Frequently Asked Questions

If one of the below options doesn't answer your question(s), you can post on the <a href="http://forum.tinycircuits.com/" target="_blank" alt="Thumby Tinycircuits forum">**Thumby section of our forum**</a>, or get in touch with <a href="https://tinycircuits.com/pages/contact-us" target="_blank" alt="Send a message to tinycircuits support on this page">**customer support**</a>.

---

### Grayscale on Thumby

**Why are/is the grayscale games/library malfunctioning on my Thumby?**

> *Disclaimer: This library is not currently maintained nor guaranteed by the TinyCircuits team, use it as an external resource at your own discretion.*

The <a href="https://github.com/Timendus/thumby-grayscale" target="_blank" alt="Thumby grayscale library by Timendus, Doogle, Fuglaro">**Thumby Grayscale library**</a> uses a timing hack with the SSD1306 chip to create a grayscale effect, but this displayability is not guaranteed on all Thumby OLED screens. Some screens may need further individual calibration to work with the grayscale library and games, but this is still undergoing inspection and testing by community members with no guarantee of a full solution in the future. 

To report issues, or report findings or fixes, please use the <a href="https://github.com/Timendus/thumby-grayscale" target="_blank" alt="Thumby grayscale library by Timendus, Doogle, Fuglaro">**GitHub repository Issues and Pull Requests**</a>. For more information on current status or updates, refer to previous <a href="https://discord.gg/3nmqb37bJ8" target="_blank" alt="Thumby grayscale discussions on discord">**Discord**</a> discussions before asking questions that may have already been addressed previously in the server.


This is an ongoing community effort so we appreciate your continued patience and the dedication of the ***Grayscale Brain Titans*** working on bringing grayscale functionality to all Thumbys!

---

### Add More Storage to Thumby

For now, Thumby is limited to 2 MB in storage since the memory chip is built into the hardware. The games are easy to swap in and out and the save files will remain on the Thumby so that you can take games that have saved data off the Thumby without losing high scores or other saved game variables. 

It's possible to remove games from a Thumby to free up storage space by connecting it to the <a href="https://code.thumby.us/" target="_blank" alt="Thumby Code Editor online IDE for chromium browsers"><b>Thumby Code Editor</b></a>  and then right-clicking the game name in the Filesystem panel and then pressing the DELETE option. Then you <a href="/Code-Editor/Arcade-games/" target="_blank" alt="tutorial for adding games to Thumby, including a reference to connecting Thumby to the Code Editor">**can add more games**</a> with the space you've made. 

<center>
![TinyCircuits Thumby Code Editor Filesystem for Thumby](/images/Delete-game-from-filesystem-screenshot.jpg)
</center>
<center>
*<a href="https://code.thumby.us/" target="_blank" alt="Thumby Code Editor online IDE for chromium browsers"><b>Thumby Code Editor</b></a> Filesystem for Thumby Screenshot with DELETE option*
</center>


---

### Code Editor Connection

**Why is my Thumby not connecting to the Web Code Editor?**

* Make sure you only have one Code Editor tab open - sometimes an older tab can be connected to Thumby and interfere with your current attempt to connect
* Make sure the Thumby device is ON - power switch should be to the right when looking at the screen
* Try a different cable - Since no port is coming up at all when the Thumby is turned on - it's possible that the cable you are using does not have the necessary data lines for communicating with the Thumby. Many Micro USB cables have just the power and ground wires to charge or power electronics. Try another cable, or test that you are able to transfer data with that cable in a different way - possibly by transferring files or pictures from a different device.
* Unplug the device completely and open your 'Device Manager' (windows) -> click on 'Ports' -> plug the device back in to see if anything shows up. For Thumby you should see "USB Serial Device (COM##)" where ## can be any number
* Try a Code Editor Hard Reset: Save any unsaved files that are open in any Code Editor tabs, (as they will be lost after the hard reset) then choose Utilities Tab > Hard Reset.
* Try a 'full reboot' on your PC. It's possible you have some serial device interfering with your ability to communicate with Thumby, such as a USB hub or other peripheral devices, like a mouse. 
    * If you are on a Windows OS, Save any open documents, then click on the Windows Start Button, select the power icon, and then choose the Restart option. (not Shut Down).   
    * If Linux or Mac, Save any open documents, then hold the computers' power button down for +3 seconds to turn off, then again to turn it back on.  
* **Windows 7** users will need to change or install a serial driver in order to connect to Thumby:
    1. Plug the Thumby in and turn it on
    2. Download the latest .exe from this <a href="https://github.com/pbatard/libwdi/releases" target="_blank" alt="install new serial driver for windows 7 operating system">**release page**</a> and run it
    3. Select the Thumby in the top most drop-down
    4. Using the little up/down arrows, switch the driver to 'USB Serial (CDC)'
    5. Click 'Install Driver'
        * You might need to unplug and re-plug the Thumby afterwards or reboot your computer
* Lastly, you can try reloading the most recent firmware version: 

    1.  Plug Thumby into a computer
    2.	Turn Thumby off
    3.	Turn Thumby on while holding the down d-pad button (*Note: Earlier revisions of Thumby may require pressing one of the red action buttons instead of the down d-pad button*)
    4.	Wait for a file explorer to pop up or for the 'RPI-RP2' device to mount 
    5.	<a href="https://github.com/TinyCircuits/TinyCircuits-Thumby-Code-Editor/raw/master/ThumbyFirmware.uf2" alt="tinycircuits thumby code editor repository">**Download the ThumbyFirmware.uf2 file**</a>
    6.	Drag and drop the **ThumbyFirmware.uf2** file to the 'RPI-RP2' device (WARNING: this will delete all Thumby files)
    7.	Turn the Thumby off and on

**The Thumby hardware freezes when it connects to the Code Editor, is it broken?**

Not at all! This is natural behavior. The Thumby hardware appears to stop working when you connect it since you can no longer access the game menu, but everything is fine! The screen should display "Thumby Code Editor" when connected as of March 9th, 2022.

To test games or changes you upload to the Thumby, you will need to disconnect the unit and power cycle it (turn it off and back on). Otherwise, you can use "Fast Execute" to upload just the game you are currently reviewing or working on. 

---

### Thumby Settings menu

**Can I change the audio and brightness?**

Yes! Turn on the Thumby, scroll down once to the 'GAMES' menu and right once to view the 'SETTINGS'. Here you can press the d-pad down button to the setting you want to alter and press either red action button to change the setting mode:

* Audio: On/Off
* Brightness: Mid/Hi/Low     *-- Note: we couldn't fit the whole word Brightness on the screen, so it reads as just Brite*

The changes automatically save after being changed. 

---

### Thumby Credits

**Where is the credits menu and whose names are on it?**

To view the credits menu on the Thumby, turn Thumby on, scroll down once to the 'GAMES' menu and press the d-pad button right twice to scroll past the 'SETTINGS' menu to see the credits roll 4 names at a time.

Kickstarter backers that selected a Special Edition Thumby were able to submit one 16 character name (or something) on the credits list per Special Edition Thumby purchased. To view the full credits list, you can connect Thumby to the <a href="https://code.thumby.us/" target="_blank" alt="TinyCircuits Thumby Web Browser Code Editor page">**Thumby Code Editor**</a> and view the credits.txt file from the 'filesystem' directory.

---

### Playing and Adding More Games

***How do I play the games on the Thumby?***

Turn on the Thumby and once the "Start" text displays below the Thumby logo, you can scroll down to see the list of games downloaded to the Thumby. There are 5+ games preloaded onto the Thumby.

Select any game with a red action button to start playing. When you want to stop playing or play a different game, turn the Thumby off and back on with the power switch. Thumby will remember the last game you played. When the Thumby is first powered on and the 'Start' text is selected, you can press a red action button to start playing the last game played.

**How do I add more games?**

There are plenty of free games made by the community that you can play on your Thumby. <a href="https://thumby.us/Code-Editor/Arcade-games/" target="_blank" alt="TinyCircuits Thumby add games tutorial">**Check out this tutorial to learn how to add games to Thumby**</a>. 

---


### Multiplayer Link Cable

**Is the Thumby Link cable the same as an OTG cable, or is it different?**


The pin wiring of the OTG cable would need to be verified. 

<center>
![TinyCircuits Thumby Link cable](/images/USB-pinout.jpg)
</center>
<center>
*Micro USB Pinout diagram*
</center>

The Thumby Link cable is a custom cable that connects GND to GND (pin 5), and ID pin to ID pin (pin 4) for data transfer.

---

### Audio

**How can I test that the audio is working?**

Check that the Audio is turned on in the settings menu: Turn Thumby on -> scroll down once -> scroll to the right once -> check that the 'Audio' setting is 'ON'.

Not every game has sound effects, but some of the preloaded games do. You can test audio with the game **SaurRun** - try playing this game and holding the Thumby closer to your ear to hear the tiny piezo sounds while jumping the running Dinosaur. Or play the **TinyBlocks** game to hear tiny ticking sounds as the play blocks fall down the screen.

---

### Charging & Battery Life

**How long does Thumby take to charge? Is there an indicator when it is charged?**

Thumby takes around 1 hour to completely charge. An indicator LED will turn on from inside the Thumby case to show that the battery is being charged. The LED will turn off when the battery is fully charged. The LED is located to the left of the micro USB connector.

*Note: The charging LED may be difficult to see through opaque plastic cases. Try turning off the lights in the room you are in if you are having difficulty seeing the LED while charging.*

**How long can I play Thumby on a full charge?**

You can play Thumby for up to two hours on a full charge. Games that display more white pixels will use more power than games that are darker.

--- 

### Software Updates

**How do I know if my Thumby has the latest firmware/software?**

You can update the Thumby firmware after connecting your Thumby to the Web Code Editor - the files system panel has an 'Update' button that will turn red when it detects your software is not up-to-date. Press the 'Update' button to load the newest software. The update will only overwrite a few core Thumby files.

--- 

### Linux with Thumby

**How do I connect Thumby to a Linux system?**

If you have already tried to connect Thumby to your Linux machine and failed, it's likely you have encountered an error message like: "Could not open serial port /dev/ttyUSB0"

You will need to add your user to the ```dialout``` group to have access to the USB device. Use the command: 

```sudo adduser $USER dialout```

The $USER keyword will fetch your username, so there is no need to alter the command. Then, log out of your user account or restart your machine for the changes to take effect.

---

### Distributing Thumby

**Can I distribute Thumby?**

Yes! Check out the different levels of our <a href="https://tinycircuits.com/pages/reseller-program" target="_blank" alt="Distributor program information">**distribution program**</a> on our main page.
