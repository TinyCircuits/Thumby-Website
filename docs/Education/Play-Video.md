# Editing a Video Animation for Thumby

This tutorial details how to display an animation on Thumby from how to edit the video itself, to the final step of uploading the animation! The animation highlighted in this tutorial was first shared here:

<center><blockquote class="tiktok-embed" cite="https://www.tiktok.com/@tinycircuits/video/7018217500441627910" data-video-id="7018217500441627910" style="max-width: 605px;min-width: 325px;" > <section> <a target="_blank" title="@tinycircuits" href="https://www.tiktok.com/@tinycircuits">@tinycircuits</a> Coding Permission to Dance on Thumby for Jimin’s birthday. Happy 26th Jimin! <a title="jimin" target="_blank" href="https://www.tiktok.com/tag/jimin">#jimin</a> <a title="bts" target="_blank" href="https://www.tiktok.com/tag/bts">#bts</a> <a title="jiminbirthday" target="_blank" href="https://www.tiktok.com/tag/jiminbirthday">#jiminbirthday</a> <a title="thumby" target="_blank" href="https://www.tiktok.com/tag/thumby">#thumby</a> <a title="tinycircuits" target="_blank" href="https://www.tiktok.com/tag/tinycircuits">#tinycircuits</a> <a title="fyp" target="_blank" href="https://www.tiktok.com/tag/fyp">#fyp</a> <a target="_blank" title="♬ original sound - TinyCircuits" href="https://www.tiktok.com/music/original-sound-7018217361236888326">♬ original sound - TinyCircuits</a> </section> </blockquote> <script async src="https://www.tiktok.com/embed.js"></script></center>

---

## Edit video to only black and white

<a href="" target="_blank" alt="">****</a>
<a href="" target="_blank" alt="">****</a>


Download <a href="https://shotcut.org/" target="_blank" alt="Download shotcut">**Shotcut**</a>. Once downloaded, open the app and create a project file.

<center>
![Opening shotcut screenshot](/images/Shotcut-opening-screen.JPG)
</center>

Import the video you want to see on Thumby. 

Adjust the saturation, lightness, and hue to create a black and white animation. Then apply chroma key, this <a href="https://forum.shotcut.org/t/silhouette-effect-in-shotcut/15509/4" target="_blank" alt="Shotcut forum post link">**Shotcut forum post**</a> shows a good example of the effect these changes should have on the video. 

---

### Rotate the video and scale it


---

### 
3. Add video track from playlist and add another track for background color (Open other in top bar)


---

###
4. Export as mp4 with correct 72x40 for both res and aspect


---

## Convert MP4 to Bitmap

To make the animation compatible with Thumby, we will want the video in terms of bitmaps.
5. Use ConvertMP4ToMPBitmaps.py to generate video.raw

```py
import cv2

print("Started")

video = cv2.VideoCapture('DancingThumbyAnimation2.mp4')
success, image = video.read()
frameCount = 0

EXPECTED_WIDTH = 72
EXPECTED_HEIGHT = 40
WHITE_THRESHOLD = 200

file = open("video.raw", 'wb')

while success:
    height, width, channels = image.shape
    frameBytes = []

    for y in range(0, EXPECTED_HEIGHT, 8):
        for x in range(0, EXPECTED_WIDTH, 1):
            byte = 0b00000000
            for i in range(0, 8, 1):
                if image[y+i, x, 0] > WHITE_THRESHOLD or image[y+i, x, 1] > WHITE_THRESHOLD or image[y+i, x, 2] > WHITE_THRESHOLD:
                    byte = byte | (1 << i)
                else:
                    byte = byte & ~(1 << i)
            frameBytes.append(byte)

    file.write(bytes(bytearray(frameBytes)))

    success, image = video.read()
    frameCount += 1
    print('Read a new frame: ', frameCount)

file.close()

print("")
print("Ended:")
print("   Frame count: ", frameCount)
print("   Total frame bytes (kB): ", (frameCount * 360)/1000)

print("")
print("############################################")
print("")
print("Data output to: video.raw")
print("")
```

---

## Upload the .raw video to Thumby

Use the following program to play the .raw animation, make sure the file path is pointing to the correct location:

```py
import time
import thumby
import math
import time

# video = open("/Games/VideoPlayer/video.raw", 'rb')
video = open("/video.raw", 'rb')

while(1):
    for frameIndex in range(0, 310, 1):
        frame = video.read(360)
        thumby.display.fill(0)
        thumby.display.blit(bytearray(frame), 0, 0, 72, 40, 0, 0, 0)
        thumby.display.update()
        time.sleep_ms(17)
    video.seek(0)
```
