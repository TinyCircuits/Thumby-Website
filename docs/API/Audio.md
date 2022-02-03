## Audio
* Note: audio not implemented on web IDE emulator but is unlikely to cause exceptions
* ### Functions
    * `thumby.audio.play(freq, duration, duty)` | plays audio at sound frequency `freq` and duty cycle `duty` for `duration` in milliseconds without blocking code execution. For now, try searching 'music notes to frequency chart' to relate these parameters to musical notes. `freq` can technically range from 7Hz ~ 125MHz, but human hearing is in the 20 ~ 20000Hz range. Returns None
        * `freq`
            * type: int
            * values: 20 ~ 20000 (Hz)
        * `duration`
            * type: int
            * values: 0 ~ 2147483647 (ms)
        * `duty`
            * type: uint_16
            * values: 0 (0%) ~ 65535 (100%) (default: 32768 or 50%)
    * `thumby.audio.playBlocking(freq, duration, duty)` | plays audio at sound frequency `freq` and duty cycle `duty` for `duration` in milliseconds while blocking code execution. For now, try searching 'music notes to frequency chart' to relate these parameters to musical notes. `freq` can technically range from 7Hz ~ 125MHz, but human hearing is in the 20 ~ 20000Hz range. Returns None
        * `freq`
            * type: int
            * values: 20 ~ 20000 (Hz)
        * `duration`
            * type: int
            * values: 0 ~ 2147483647 (ms)
        * `duty`
            * type: uint_16
            * values: 0 (0%) ~ 65535 (100%) (default: 32768 or 50%)
    * `thumby.audio.stop()` | stops playing any running audio started by `thumby.audio.play(...)`. Returns None
    * `thumby.audio.set_enabled(setting)` | stops buzzer from outputting sound when `thumby.audio.play()` or `thumby.audio.playBlocking()` are called using `setting` flag. `thumby.audio.playBlocking(...)` will still block subsequent code execution for the duration provided to it. Returns None
        * `setting`
            * type: bool
            * values: 1/True (audio enabled) or 0/False (audio disabled)
