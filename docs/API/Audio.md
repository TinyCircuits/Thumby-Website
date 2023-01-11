# Audio

### Functions

`thumby.audio.play(freq, duration)` | plays audio at sound frequency `freq` for `duration` in milliseconds without blocking code execution. For now, try searching 'music notes to frequency chart' to relate these parameters to musical notes. `freq` can technically range from 7Hz-125MHz, but human hearing is in the 20-20000Hz range. Returns None

--- 

* `freq`
    * type: int
    * values: 20 ~ 20000 (Hz)
* `duration`
    * type: int
    * values: 0 ~ 2147483647 (ms)

--- 

`thumby.audio.playBlocking(freq, duration)` | plays audio at sound frequency `freq` for `duration` in milliseconds while blocking code execution. For now, try searching 'music notes to frequency chart' to relate these parameters to musical notes. `freq` can technically range from 7Hz-125MHz, but human hearing is in the 20-20000Hz range. Returns None

* `freq`
    * type: int
    * values: 20 ~ 20000 (Hz)
* `duration`
    * type: int
    * values: 0 ~ 2147483647 (ms)

---

`thumby.audio.stop()` | stops playing any running audio started by `thumby.audio.play(...)`. Returns None

---

`thumby.audio.set_enabled(setting)` | stops buzzer from outputting sound when `thumby.audio.play()` or `thumby.audio.playBlocking()` are called using `setting` flag. `thumby.audio.playBlocking(...)` will still block subsequent code execution for the duration provided to it. Returns None

* `setting`
    * type: bool
    * values: 1/True (audio enabled) or 0/False (audio disabled)


--- 

## Advanced Community-fueled Usage

It's possible to make more complicated sound effects and music with Thumby using software. Check out the <a href="https://arcade.thumby.us/" target="_blank" alt="Thumby arcade game Melody Maker"><b>arcade game Melody Maker</b></a> made by <a href="https://github.com/FestyWalrus" target="_blank" alt="GitHub account https://github.com/FestyWalrus"><b>SuperRiley64 (@FestyWalrus on GitHub)</b></a> to make your own tunes that save to Thumby, or use an audio library to take your Thumby music to the next level. 

<center><iframe width="560" height="315" src="https://www.youtube.com/embed/vbBQ11BZWoU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe></center>
<center>*Bad Apple on Thumby using PWM at 80 kHz - showcasing what's possible with the tiny piezo!*</center>

Background: Thumby Rev 6 utilizes a piezo disc connected through a buffer to a GPIO pin to create audio effects. Anything other than a square wave on one channel requires more software.

An impressive community developed audio library, Thumby Polysynth, made by <a href="https://github.com/transistortester" target="_blank" alt="GitHub account transistortester"><b>@transistortester</b></a> allows for more complicated audio configurations, please take a look at their <a href="https://github.com/transistortester/thumby-polysynth" target="_blank" alt="README on GitHub Repository transistortester thumby-polysynth"><b>README on their GitHub Repository</b></a> for more information.

> *Disclaimer: This library is not maintained nor guaranteed by the TinyCircuits team, use it as an external resource at your own discretion.*






