# Editing a Video Animation for Thumby

This tutorial details how to display an animation on Thumby from how to edit the video itself, to the final step of uploading the animation! The animation highlighted in this tutorial was first shared here:

<center><blockquote class="tiktok-embed" cite="https://www.tiktok.com/@tinycircuits/video/7018217500441627910" data-video-id="7018217500441627910" style="max-width: 605px;min-width: 325px;" > <section> <a target="_blank" title="@tinycircuits" href="https://www.tiktok.com/@tinycircuits">@tinycircuits</a> Coding Permission to Dance on Thumby for Jimin’s birthday. Happy 26th Jimin! <a title="jimin" target="_blank" href="https://www.tiktok.com/tag/jimin">#jimin</a> <a title="bts" target="_blank" href="https://www.tiktok.com/tag/bts">#bts</a> <a title="jiminbirthday" target="_blank" href="https://www.tiktok.com/tag/jiminbirthday">#jiminbirthday</a> <a title="thumby" target="_blank" href="https://www.tiktok.com/tag/thumby">#thumby</a> <a title="tinycircuits" target="_blank" href="https://www.tiktok.com/tag/tinycircuits">#tinycircuits</a> <a title="fyp" target="_blank" href="https://www.tiktok.com/tag/fyp">#fyp</a> <a target="_blank" title="♬ original sound - TinyCircuits" href="https://www.tiktok.com/music/original-sound-7018217361236888326">♬ original sound - TinyCircuits</a> </section> </blockquote> <script async src="https://www.tiktok.com/embed.js"></script></center>

This tutorial will involve some video editing and programming.



<a href="" target="_blank" alt="">****</a>
<a href="" target="_blank" alt="">****</a>


Download the video editing software <a href="https://shotcut.org/" target="_blank" alt="Download shotcut">**Shotcut**</a>. Once downloaded, open the app and create a project file.

<center>
![Opening shotcut screenshot](/images/Shotcut-opening-screen.JPG)
</center>

Import the video you want to see on Thumby. If you want to follow along with this tutorial, you can <a href="https://github.com/TinyCircuits/Thumby-Website/raw/main/docs/images/DancingAnimation.mp4" target="_blank" alt="">**download the video we used**</a>. 


---

## Edit video to only black and white

For this, we will need to add some filters to achieve a fully black and white video. Keep in mind that this process will require more steps if your video contains a lot of colors or doesn't have a solid color background.

To accomplish this, we will use the Shotcut filter *Hue/Lightness/Saturation* to adjust the saturation, lightness, and hue values. When edited correctly, the video video should appear so saturated and brightened that you only see two colors. 

Navigate to the filters list to locate *Hue/Lightness/Saturation*: 

<center>
![Shotcut filters screenshot](/images/Shotcut-filters.JPG)
</center>
<center>*Click Filters*</center>

<center>
![Shotcut filters list screenshot](/images/Shotcut-filters-list.JPG)
</center>
<center>*Scroll or search for Hue/Lightness/Saturation filter*</center>

<center>
![Shotcut filters list hue/lightness/saturation screenshot](/images/Shotcut-filters-sat-light-hue.JPG)
</center>

<center>
![Shotcut filters lightness before screenshot](/images/Shotcut-lightness-before.JPG)
</center>
<center>*The default Hue/Lightness/Saturation values are on sliders you can toggle*</center>


For this video, the orange background became a very light yellow so it may be difficult to distinguish that there are two colors after applying the following settings:

* Hue: -21
* Lightness: 200 (max)
* Saturation: 100

<center>
![Shotcut filter hue/lightness/saturation applied screenshot](/images/Shotcut-saturated-before-chroma-key.JPG)
</center>

Now we need to make the video appear as just black and white. To do this, we will first key out the light-yellow background color and then add a black video to replace the background. Search for the *Chroma Key: Simple* filter. Once open, take the color dropper tool and select the background, in this case the light yellow. Nothing will visually change here until we layer in  some black footage. To do this, select the *Open Other* dropdown in the top left, and press *Color*:

<center>
![Shotcut add color](/images/Shotcut-open-color.jpg)
</center>

Select the color black and press *OK* to add it:

<center>
![Shotcut add color black](/images/Shotcut-open-color-black.jpg)
</center>

From there, you can move the black track to a separate *Output* and extend it to match the length of the animation. Move the black footage to *Output V1* and the animation to *Output V2* so that the animation is layered on top of the black footage: 

<center>
![Shotcut add color black](/images/Shotcut-black-track-background.jpg)
</center>


The last filter to add would be *Crop: Source* to remove the YouTube watermark and resize the video to better fit the Thumby screen dimensions of 72x40 pixels: 

<center>
![Shotcut crop source filter applied](/images/Shotcut-crop-filter.jpg)
</center>

---

### Rotate the video and scale it

The Thumby screen is a typical wide rectangle, so to make this tall phone-style video fit onto the screen better, we will need to rotate and scale it before exporting it. Click on *View* and select *Export*:

<center>
![Shotcut export](/images/Shotcut-export.jpg)
</center>

Once the settings are open, change the *Aspect ratio* values to 72 and 40 and set the *Rotation* to 90. Click on *Convert* and then press *OK* on the window that opens to export the modified video: 

<center>
![Shotcut export settings](/images/Shotcut-export-settings.jpg)
</center>

Name the edited video *DancingAnimation-edited.mp4* so that it will be compatible with the program used in the next step.

---

## Convert MP4 to Bitmap

To make the animation compatible with Thumby, we will want the video in terms of bitmaps. Use the following program *ConvertMP4ToMPBitmaps.py* to generate *video.raw* that will be used in the next, final step to get the video onto Thumby.

```py
import cv2

print("Started")

video = cv2.VideoCapture('DancingAnimation-edited.mp4')
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

Use the following program in the <a href="https://code.thumby.us/" target="_blank" alt="Thumby Web Browser programming editor">**Thumby Code Editor**</a> to play the video.raw animation. If you're unfamiliar with the Thumby Code Editor, it may help to go through the <a href="https://thumby.us/Code-Editor/Get-Started/" target="_blank" alt="Thumby code editor tutorial">**Getting Started tutorial**</a>.

Copy the below code and paste it into the Editor section of the site:

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


<center>
![Shotcut code editor](/images/Shotcut-code-editor.jpg)
</center>

Then select *File* and *Import from PC* to import the video.raw file:

<center>
![Shotcut code editor import](/images/Shotcut-code-editor-import.jpg)
</center>


Make sure the file path on line 6 or 7 is pointing to the correct location, whether you have the video.raw file just in the emulator, or if you later add it to a folder on the Thumby hardware.

That's everything! You can emulate the animation directly in the Code Editor, or you can download it to your Thumby.