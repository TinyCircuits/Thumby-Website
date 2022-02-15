Thumby communication is half-duplex serial, meaning only one Thumby can talk at a time. The `.send(...)` function only succeeds if first time calling it, just received data through calling `.receive()`, or a timeout occurred.

`thumby.link.send(data)` | tries to send `data` over link cable. Returns False if have not received data before timeout or True if succeeds. All parameters required.

* `data`
    * type: bytes or bytearray
    * value: bytes or bytearray filled with integers scaled 0 to 255 (max array length is 512)

`thumby.link.receive()` | retrieves data sent over link cable. Returns bytearray containing integers scaled 0 to 255 (max array length is 512), None otherwise


## Thumby Link API Examples

The Thumby link API takes care of the half-duplex communication for you! Half-duplex communication is similar to how walkie-talkies work - only one device can communicate to the other at a time.

### Encoding, sending, receiving, and decoding data
Data needs to encoded to bytes before sending and decoded from bytes after receiving. MicroPython offers built-in utilities to help prepare data.

* **List of bytes** (each element is a value from 0 to 255). Wrap it with `bytearray` and use it like a normal array

```py
# Allow both Thumbys to move their own square

import thumby

# Set the FPS to something high. The other player's
# movement will be at half the refresh rate!
thumby.display.setFPS(90)

# Convert the list to a bytearray and use the first 
# element as an x position and the second as a y
myPlayerPos = bytearray([0, 0])
theirPlayerPos = bytearray([0, 0])

while True:
    # No screen bounds checking done
    if thumby.buttonU.pressed():
        myPlayerPos[1] -= 1
    elif thumby.buttonD.pressed():
        myPlayerPos[1] += 1
    elif thumby.buttonL.pressed():
        myPlayerPos[0] -= 1
    elif thumby.buttonR.pressed():
        myPlayerPos[0] += 1
    
    # Draw the squares
    thumby.display.fill(0)
    thumby.display.drawFilledRectangle(myPlayerPos[0], myPlayerPos[1], 2, 2, 1)
    thumby.display.drawFilledRectangle(theirPlayerPos[0], theirPlayerPos[1], 2, 2, 1)
    thumby.display.update()

    # .send(...) and .receive() should be called in the same
    # loop to ensure fastest back and forth communication!
    # The other Thumby won't send data until it gets something
    # back!
    thumby.link.send(myPlayerPos)
    received = thumby.link.receive()
    
    # Check that data was received and then
    # assign it to the other player's square
    if received != None:
        theirPlayerPos = received
```

* **Strings**. Use `.encode()` and `.decode()` on strings!

```py
# Send random texts to the other Thumby

import thumby
import random

# Set a low FPS since just texting back and forth
thumby.display.setFPS(15)

# Define alphabet get getting random characters from
alphabet = "abcdefghijklmnopqrstuvwxyz"

# Store last received message in this
lastReceivedMessage = ""

while True:
    # Unless a button is pressed later, a blank message will be sent
    message = ""

    # Make a random message on button press
    if thumby.buttonA.pressed():
        for i in range(0, 6, 1):
            message += alphabet[random.randint(0, 25)]

    # Send message after encoding even if "" or random
    thumby.link.send(message.encode())

    # Always try to receive data
    received = thumby.link.receive()
    if received != None:
        # Decode the string!
        received = received.decode()
        if received != "":
            lastReceivedMessage = received
    
    # Display the last message that was received
    thumby.display.fill(0)
    thumby.display.drawText("Received:", 0, 0, 1)
    thumby.display.drawText(lastReceivedMessage, 16, 14, 1)
    thumby.display.update()
```

* **Objects (lists, tuples, dictionaries, and sets)**. Use the [`ujson`](https://docs.micropython.org/en/v1.15/library/ujson.html) module to serialize and deserialize the object. The below example uses lists with different type elements but `ujson` works with other objects. WARNING: Serialization and deserialization can be slow!

```py
# Allow each thumby to move their own named square

import thumby
import ujson
import random

# Set the FPS to something high. The other player's
# movement will be at half the refresh rate!
thumby.display.setFPS(90)

# Make a list for each player containing an x position,
# y position, and a name. This is a list with different
# type elements - bytearray cannot be used directly
myPlayerInfo = [0, 0, "Thumby" + str(random.randint(0, 1000))]
theirPlayerInfo = [0, 0, ""]

while True:
    # No screen bounds checking done
    if thumby.buttonU.pressed():
        myPlayerInfo[1] -= 1
    elif thumby.buttonD.pressed():
        myPlayerInfo[1] += 1
    elif thumby.buttonL.pressed():
        myPlayerInfo[0] -= 1
    elif thumby.buttonR.pressed():
        myPlayerInfo[0] += 1
    
    # Draw the squares and their names
    thumby.display.fill(0)
    thumby.display.drawText(myPlayerInfo[2], myPlayerInfo[0] - 25, myPlayerInfo[1] - 8, 1)
    thumby.display.drawFilledRectangle(myPlayerInfo[0], myPlayerInfo[1], 2, 2, 1)

    thumby.display.drawText(theirPlayerInfo[2], theirPlayerInfo[0] - 10, theirPlayerInfo[1] - 8, 1)
    thumby.display.drawFilledRectangle(theirPlayerInfo[0], theirPlayerInfo[1], 2, 2, 1)
    thumby.display.update()

    # .send(...) and .receive() should be called in the same
    # loop to ensure fastest back and forth communication!
    # The other Thumby won't send data until it gets something
    # back!
    thumby.link.send(ujson.dumps(myPlayerInfo).encode())
    received = thumby.link.receive()
    
    # Check that data was received and then
    # assign it to the other player's square
    if received != None:
        theirPlayerInfo = ujson.loads(received.decode())
```

### Advanced
See the [Tennis](https://github.com/TinyCircuits/TinyCircuits-Thumby-Games/blob/master/Tennis/Tennis.py) game for an example of complex usage of the link API. Tennis provides examples on how to sync various aspects of a game, such as the current game screen, sprite positions, sound, etc

## Script structure
The above examples only showed structures that work well but here is a structure that does not

```py
# Allow both Thumbys to move their own square

import thumby

# Set the FPS to something high. The other player's
# movement will be at half the refresh rate!
thumby.display.setFPS(90)

# Convert the list to a bytearray and use the first 
# element as an x position and the second as a y
myPlayerPos = bytearray([0, 0])
theirPlayerPos = bytearray([0, 0])

while True:
    # Move player but do not check screen 
    # bounds, also send on button press
    if thumby.buttonU.pressed():
        myPlayerPos[1] -= 1
        thumby.link.send(myPlayerPos)
    elif thumby.buttonD.pressed():
        myPlayerPos[1] += 1
        thumby.link.send(myPlayerPos)
    elif thumby.buttonL.pressed():
        myPlayerPos[0] -= 1
        thumby.link.send(myPlayerPos)
    elif thumby.buttonR.pressed():
        myPlayerPos[0] += 1
        thumby.link.send(myPlayerPos)
    
    # Draw the squares
    thumby.display.fill(0)
    thumby.display.drawFilledRectangle(myPlayerPos[0], myPlayerPos[1], 2, 2, 1)
    thumby.display.drawFilledRectangle(theirPlayerPos[0], theirPlayerPos[1], 2, 2, 1)
    thumby.display.update()

    received = thumby.link.receive()
    
    # Check that data was received and then
    # assign it to the other player's square
    if received != None:
        theirPlayerPos = received
```
The issue in the above script is that `thumby.link.send(...)` is only called when a button is pressed and not every frame.
This means at least one Thumby will have data to be sent but it can't because it hasn't gotten a response.

Trying to send data every frame, even if it will be ignored, is a way to ensure each Thumby is able to send data as soon as possible.

## Debugging
Sometimes it is necessary to see what crashed a game; however, with the Thumbys connected to each other, there is no way to see the output on a shell. There are two ways to debug your game

1. Step through your code by placing calls to a draw function until the place just before execution stops is found. For example, place `thumby.display.drawText(...)` and `thumby.display.update()` at various places in the code - the instance that does not display on the screen is a hint to where the script crashes
2. Wrap the code in a `try` and `except` block then write the exception to a file. For example,

```py
import thumby

try:
    # Code that crashes
except Exception as e:
    f = open("/crash.log", "w")
    f.write(str(e))
    f.close()
```
This will not print the full traceback but the file can be opened to see the exception message.