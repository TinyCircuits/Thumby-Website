# Frequently Asked Questions

If one of the below options doesn't answer your question(s), you can post on the <a href="http://forum.tinycircuits.com/" target="_blank" alt="Thumby Tinycircuits forum">**Thumby section of our forum**</a>, or get in touch with <a href="https://tinycircuits.com/pages/contact-us" target="_blank" alt="Send a message to tinycircuits support on this page">**customer support**</a>.

---

### IDE Connection

**Why is my Thumby not connecting to the Web IDE?**

* Make sure you only have one IDE tab open - sometimes an older tab can be connected to Thumby and interfere with your current attempt to connect
* Make sure the Thumby device is ON - power switch should be to the right when looking at the screen
* Try a different cable - Since no port is coming up at all when the Thumby is turned on - it's possible that the cable you are using does not have the necessary data lines for communicating with the Thumby. Many Micro USB cables have just the power and ground wires to charge or power electronics. Try another cable, or test that you are able to transfer data with that cable in a different way - possibly by transferring files or pictures from a different device.
* Unplug the device completely and open your 'Device Manager' (windows) -> click on 'Ports' -> plug the device back in to see if anything shows up. For thumby you should see "USB Serial Device (COM##)" where ## can be any number
* If you still don't see anything showing up, try turning your computer off and restart. It's possible you have some serial device interfering with your ability to communicate with Thumby. Such as a USB hub or other peripheral devices, like a mouse.

**The Thumby hardware freezes when it connects to the IDE, is it broken?**

No! This is natural behavior. The Thumby hardware stops working because it is being 

---


### Multiplayer Link Cable

**Is the Thumby Link cable the same as an OTG cable, or is it different?**


The pin wiring of the OTG cable would need to be verified. 

<center>
![TinyCircuits Thumby Link cable](/images/USB-pinout.png)
</center>
<center>
*Micro USB Pinout diagram*
</center>

The Thumby Link cable is a custom cable that connects GND to GND (pin 5), and ID pin to ID pin (pin 4) for data transfer.

---

### Audio

**How can I test that the audio is working?**

Not every game has audio, but some definitely do! The game **SaurRun** likely has the loudest audio of the games loaded onto Thumby. You can try playing this game and holding the Thumby closer to your ear to hear the tiny piezo sounds while jumping the running Dinosaur. It may also help to check that the Audio is turned on in the settings menu (Turn Thumby on -> scroll down once -> scroll to the right once -> check that the 'Audio' setting is 'ON')

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

You can update the Thumby firmware after connecting your Thumby to the Web IDE - the files system panel has an 'Update' button that will turn red when it detects your software is not up-to-date. Press the 'Update' button to load the newest software. The update will only overwrite a few core Thumby files.

--- 

### Distributing Thumby

**Can I distribute Thumby?**

Yes! Check out the different levels of our <a href="https://tinycircuits.com/pages/reseller-program" target="_blank" alt="Distributor program information">**distribution program**</a> on our main page.