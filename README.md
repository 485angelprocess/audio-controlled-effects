# audio-controlled-effects
Audio controlled music effects controller for Pure Data

# Use

Run in Pure Data with moocow library.

Audio trigger input controls and selects menu options to create separate channeled loops. Use headphones to prevent control feedback. The top menu is a pitch-controlled menu. Midi pitches 60-70 (C4-Bb4) scroll through 5 menu options. The pitch range and start point is adjustable as arguments to the [PitchMenu] abstraction. To select a menu option do a loud audio "bonk", or sharp noise. I find that plosives ("Tuh" or "Puh") give the most reliable bonk.

1. Start/stop: Exit the top menu (stop speech synthesizer pitch menu). On another bonk return the top menu, and clear and stop all loops.
2. Pause: Exit the top menu. On another bonk return to the top menu, but continue all all loops.
3. Line1-3: Edit Line 1-3. Each loop line has 4 positions. The lowest position (lowest ping) clears the loop, the next position starts recording, the third ends recording and the fourth returns to the top menu. The first loop recorded defines the length of the loop. Subsequent loops are recorded in overdub mode, where recording will flip back to the beginning when the end of the master loop is reached.

The thresholds for the loops may need adjustment. The input levels should be such that you can sing comfortably and trigger one menu option reliably, this may take some patience. By default the trigger and loop line share the same input, this can be useful for recording voice loops, but can be difficult to manage triggering bonks and singing melodies simulataneously. Another option is to use two audio inputs, such as USB audio device to separate the trigger and loop line. Use your audio settings and pure datas audio settings to select the correct device and channel settings. Outputs can also be set to separate channels, this can help send the loop lines through external effects and the menu notifications clean.

# Effects

Each loop line has effects applied after recording. The effect options are pass, ring modulation and distortion. They are selected through messaging [effect linenumber effectnumber] where linenumber is the line number 1-3, and effect number is 0 1 or 2. All effects share a control value sent by message [effect linenumber control1 controlnumber] where control number is a positive integer.

# Test bench

The test bench allows testing of voice control menus with the substition of voice input for in software oscillators. Useful for debugging without worrying about feedback or microphone levels.
