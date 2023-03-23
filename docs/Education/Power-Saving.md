# Power Saving (Experimental)

Thumby is a small console with a small battery that lasts around 2 hours of gameplay on a full charge, depending on what games with what colors at what speed are being played. 

In the case of wanting to display a static image on the Thumby screen long term, you may be able to get more hours of display time by adjusting the frequency. Here is an example with some notes contributed by <a href="https://gist.github.com/ace-dent/7bc73b4ad466331af0d1917834261a8a" target="_blank" alt="gist example Thumby code for power saving while displaying a static image">**ace-dent on GitHub**</a>:

```py
from machine import freq, reset, lightsleep
freq(250_000_000) # Speed up CPU for faster imports
import thumbyGraphics
from thumbyButton import actionPressed

# Tweaks for extended battery life
freq(24_000_000) # Lowest stable CPU frequency
thumbyGraphics.display.brightness(1) # Low brightness
thumbyGraphics.display.setFPS(0) # Minimal frame rate: draws buffer without delay

# 72 x 40 px, fullscreen image 
img = bytearray([252,254,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,254,252,255,255,255,255,255,255,255,255,255,255,255,255,127,31,15,15,15,31,127,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,127,31,15,15,15,31,127,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,252,248,248,248,252,255,255,255,255,255,255,255,255,31,15,79,143,79,143,79,143,79,143,79,143,79,143,79,143,79,143,79,143,79,15,31,255,255,255,255,255,255,252,248,248,248,252,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,254,248,241,226,229,202,205,206,207,206,207,206,207,206,207,230,231,242,241,248,252,254,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,63,127,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,255,127,63])

thumbyGraphics.display.blit(img, 0, 0, 72, 40, -1, 0, 0)
thumbyGraphics.display.update()

while(True):
    lightsleep(2000) # 2 second power nap
    # Hold down an action button to exit
    if(actionPressed()):
        thumbyGraphics.display.fill(0)
        thumbyGraphics.display.drawText("Bye bye...", 0, 0, 1)
        thumbyGraphics.display.update()
        lightsleep(1000) # Delay to read the closing message
        reset() # Exit game to main menu
```

The benchmark for running the above example with a new, fully charged Thumby at ~23˚C with 93% lit pixels produced a promising runtime of 4 hours and 8 minutes. 

Some other factors <a href="https://gist.github.com/ace-dent" alt="ace-dent github account profile page" target="_blank">**ace-dent**</a> mentioned for future possible testing:

* Setup GPIO interrupts, so that lightsleep() can be used without the 2s alarm;
* Adjust OLED clock multiplier, to see if lower CPU clocks can maintain a stable display;
* Adjust OLED charge pump settings;
* Other OLED CMD tweaks?;
* Disable any unnecessary RP2040 peripherals/ features (audio amp, ADC, timers, etc.)


---

## Thumby Dormant Mode with Screen Off

This example was creating using the <a href="https://github.com/tomjorquera/pico-micropython-lowpower-workaround" alt="GitHub library for lower power pico processor usage" target="_blank">**low power workaround for Raspberry Pi Pico**</a>:

```py
from machine import Pin
from thumby import display
import lowpower

display.display.poweroff()

DORMANT_PIN = 27 # Right-most Thumby button, button A

print("before dormant")
lowpower.dormant_until_pin(DORMANT_PIN, False, False)
```

After putting a Thumby in dormant mode, it remained powered for 18+ hours.

---

## Deep Sleep Known Issues

Using the native `deepsleep` function available from the <a href="https://github.com/raspberrypi/pico-sdk" alt="GitHub library for pico processor" target="_blank">**Raspberry Pi Pico SDK**</a>, the OLED display stops responding - this is due to peripherals being disabled in order to save power. Use the native lower power tools at your own discretion.
