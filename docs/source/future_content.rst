Future Content
--------------

Troubleshooting
~~~~~~~~~~~~~~~

**Eyelink 1000:**

If everything seems set up correctly and you see nothing on the Eyelink windows:

1. Make sure the lens cap is off.
2. Make sure your task computer is connected to the Eyelink computer. This is typically done with the ethernet cable, so check that it is firmly connected and your network settings are configured to use it.
3. If you still see nothing, restart the program. Quit Eyelink, check the cable connections on the tracker in the bore, then click the square button at the top left of the desktop screen to launch Eyelink again.

If everything seems set up correctly, but you notice a green "D" and green crosshairs (instead of white) during calibration:

1. The eyetracker thinks it is detecting the left eye. We usually track the right eye because that is where the camera is typically and stably positioned--over where the right eye is visible through the coil.
2. To switch eyes, return to the main menu where you have the thresholding controls for pupil and CR. Look near the bottom of the screen--there are buttons for left and right eye in the "Eye Tracked" window. Click the "Right" button.
3. Now click the pupil to direct Eyelink to the area you know it should focus on. The participant view window may flash light blue and refuse to keep the yellow box centered around the pupil. If this happens, it means the CR thresholding is way off (likely due to the left/right confusion). Increase or decrease it until it starts to look sensible again and allows you to focus the yellow box around the pupil. Now adjust the pupil thresholding as usual and try calibration again.

If the Eyelink computer is alerting you to a filename error, check the ID you are using to identify your participant on your task laptop (or whichever computer you have connected to the Eyelink system). Make sure it is at most 8 characters long.
  -Eyelink runs on an old DOS system, which limits filenames to 8 characters or less. You can still register the participant on the console using whatever naming convention you'd like, but any string that will end up being used by Eyelink to save files will need to adhere to the character limit.

**Optoacoustics Headphones**

Issues With Audio:

Unit Won't Turn On
  This may happen if a group forgets to turn the system off at the end of their session and it stays on for a long time before finally being switched off. Turn the unit off and leave it off for some time, perhaps while you are setting up and registering your participant. Try pressing the switch again and repeat until it turns on. It may take a few cycles of switch flipping, but the unit has always come back on before long.

No Task/Computer Audio Through Headphones:

1. If your participant reports no audio from the computer you are playing it from, but can hear your voice as you speak to them, check the cable connections at the back of the Optoacoustics box. The skinny black cable (labelled "Optoacoustics", connects the box to your computer) should be plugged into the "Line 1 In" port.
2. Turn off the Optoacoustics box. Replug the skinny black cable (labelled "Optoacoustics") and the other, slightly thicker black cable to its left (the power cable).
3. Check that the two round, silver buttons on the main face of the box are both pushed in.
4. Check that your computer volume is turned up.
5. Check that the volume knob on the box is turned up and the balance knob is in the middle.

Audio Through One Side of Headphones Only:

1. Check that the balance knob is not turned all the way to one side. Turn off the box and leave it off for a few minutes. While waiting, replug the Line 1 In cable. This is the skinny black cable labelled Optoacostics that connects the box to your computer.
2. Replace the Line 1 In cable. Find a new aux cable in the control room cabinets (likely in the box labelled "AV Cables") and try using it.

Users in Control Room Cannot Hear Task Audio:

1. If your participant can hear the audio playing from your computer, but you cannot, first check the speaker knob at the top-right side of the box. Turn it up if it is low.
2. Press the circular button right below it. It should be lit green.
3. Replace the Line 1 In cable. See the section directly previous, as these problems sometimes occur together and can both be resolved with a new cable.

Issues With ANC:

Noise Cancellation Stops:
The most common reason that noise cancellation stops completely is because the stimulus presented is too loud and overshoots the safety threshold (111dB).

1. This can be avoided by making sure the volume on your stimulus machine is at max and you can control/adjust the volume of the headphones using the 'Line 1' dial on the top of the unit.
2. Doing a volume test before your scan starts can help.
3. Start with the 'Line 1' volume dial in the middle (facing the top), and adjust as needed.
Note: There is no need to adjust the 'Line 2' volume dial, it doesn't do anything to affect the sound unless you have two volume sources!

Noise Cancellation Fading:
Studies that run numerous functional tasks, or have sequences in between functional runs that don't use the ANC function, will notice that over time the algorithm used to produce the noise cancellation may fade and the quality of the noise cancellation will diminish.

1. The most effective way to avoid this is adding another short learning sequence into your protocol.
2. Stopping the algorithm just before the end of your sequence and starting the algorithm again just after your next sequence starts up again has proven somewhat effective in keeping the ANC feature intact.

Audio Output is Unbalanced:

1. Check the knob in the upper left corner of the back of the unit. Turn it until the dot at the top of the dial is lined up in the middle. The knob should always stay in this position, as it ensures that the audio will not be played in one ear more than the other.

**BOLD Screen**

Make sure the power to the AV hub is on and the HDMI/DisplayPort cables are plugged into the correct places (see labels)!

BOLDscreen Not Displaying:

First-pass Checks and Resets

1. Make sure that the AV hub box is turned on. There should be a light on at the leftmost side of the box and a red/green light flashing from the back.
2. Make sure that the correct input is selected. An orange light should be illuminated on the front of the AV box, to the right of the input you are using. Press the corresponding button if not.
3. Do not plug in multiple inputs. There is no need to plug both the HDMI and DisplayPort cables into your laptop, for example, because the input selection button will determine which one is being used anyway.
4. Check that all the cables are plugged into the correct ports. See the picture and description above for reference.
5. Disconnect and reconnect the cables between the AV hub and your laptop.
6. If you usually use HDMI, try DisplayPort instead (or vice versa). You may need to use an adapter to try the new connection method.
7. Do not use adapters unnecessarily. For example, the DisplayPort cable can connect directly to the iMac through a USB-C port. There is no need to introduce an adapter into this connection.
8. Only add "redundant" adapters if you test and see that they are necessary to get your display working.
9. Disconnect the clone. Unplug the cable labelled "MONITOR" from the "CLONE" port. This means you will not be able to see what the participant is seeing on the BOLDscreen, but if disconnecting the clone helps, it may mean that the external monitor was drawing too much power and causing issues with your display.
10. Restart your laptop. Sometimes, even closing and reopening the lid will recover the connection.
11. Restart the AV hub. Press the power button at the leftmost side of the front of the box. Wait a few seconds, then press it again.

CCN iMac Test:

1. If resetting the hub/cable inputs did not help, try plugging the display HDMI into the CCN iMac. This is often a reliable test as to whether it is a BOLDscreen/display issue or a specific laptop/machine issue.
2. If the BOLDscreen works when the display cable is plugged into the CCN iMac, the issue might be with the display settings. Check the settings like resolution, refresh rate, display mirroring vs. extended etc. on your task computer.
3. Check your adapter, if you are using one to connect the HDMI cable to your laptop. Make sure it is clean and completely plugged in. If the screen works via the iMac and resetting the hub didn't help, your adapter may not be working. Look for a spare adapter in the box on the window ledge. There are also more adapters in the labelled cabinet.
4. If the BOLDscreen doesn't work when the display cable is plugged into the CCN iMac and further testing with the adapter isn't an option (the correct spare isn't available, you know the original adapter is not the problem, etc.), notify CCN staff. There may be an issue with the BOLDscreen itself.

Archived: BOLDscreen 24 Display Issue

The old BOLDscreen used to encounter display problems due to interactions with the HDMI splitter and/or processing chip of the task laptop. The issues are documented here for archival purposes.

BOLDscreen Coloration Issue

- There is a known bug with newer MacBooks where the image has a pink tint. This is actually not an issue with the BOLDscreen, but with how the color settings on the Macbook interact with the HDMI splitter.
- This is hopefully no longer a concern after the January 2024 upgrade (from the 24 to the 32 UHD BOLDscreen), but for documentation purposes, these were the two workarounds available:

  i. Intel Based Chips: If the Macbook has an Intel processing chip (i5, i7 etc.), there is a script available which will correct the color settings to allow use with the external monitor. Please make sure to have Ruby downloaded onto your Macbook and download the patch from this GitHub site. If the user would like to attempt with assistance, please follow instructions from this Github site. Reach out to CCN Staff to coordinate patch if assistance is desired.
  ii. Silicon Based Chips: If the Macbook has an Apple Silicon chip (M1/M2), then the current script doesn't work unfortunately. The workaround is to bypass the splitter altogether. This does mean forgoing the external monitor.
    - Unplug the BOLDscreen HDMI from the back of the HDMI splitter (labeled BOLDscreen)
    - Connect any adaptors necessary to the BOLDscreen HDMI and plug into Macbook
    - The Macbook should be mirrored onto the BOLDscreen without any discoloration or tint
    - Once the session is over, make sure to plug the BOLDscreen HDMI back into the splitter

**Response Devices**

Please make sure the USB Cable has been plugged into the correct device!

Button Box Not Working:

1. Check to make sure the bottom row of lights on the button box interface light up when the corresponding buttons are pressed. Left-most light corresponds to the left most button (2BB) or the top button (4BB)
2. If all the lights are flashing then the problem is most likely an issue with the connection to your computer:
  - Check that the USB indicator on the button box interface is static (not blinking). A blinking USB status means the button box interface isn't registering that it's connected to a laptop/computer.
  - If the USB status light is static (not blinking), open up a text document (word, pages, txt edit) and ask your participant to press the buttons; responses should be collected.
  - If it works for a txt file but not your stimulus presentation program, keep the USB plugged in and restart your program (Matlab, PsychoPy etc.). Often what happens is these programs are started before the USB is connected, which doesn't allow the program to register the external device.
  - If the button box itself appears not to be working (e.g., one button does not push through a response while the others do), there is one 2-button and one 4-button spare in the drawer by the sink, beneath where the thermometer and oxygenation clip are stored.
Remember, do NOT bring the demo button box from the testing room into the scanner suite. It is for practice purposes only and NOT MR safe.

**MR-Safe Glasses**

Cleaning the Glasses

- There are supplies (glass-cleaning solution, wipes) for cleaning the MR-safe glasses in the same cabinet where the glasses are stored. Please use them, not the Lysol wipes, to clean the glasses without damaging them.

Lensometer

*A tool for measuring the prescription on an eyeglass lens.* This is stored in a small, rectangular box in the cabinet with the MR glasses. It is a white box under the cleaning wipes.

1. Open the box and remove the components within (2).
2. Connect the largest piece to power using the black cable.
3. The tool can also run on battery power. However, it seems to behave unreliably when both power sources (batteries and cable) are used, so we have removed the batteries and recommend you do not place new ones in. The lensometer stays on by default, by the nature of its design, so the batteries will continue to drain even when it's not being used.
4. Stand the largest piece upright and slot it into the divot on the outer shell of the box (3). You may not be able to slide it all the way in because of the power cable. This is okay--just make sure the piece is upright and stable.
5. Slide the reflective rectangular piece horizontally into the small slats. This may take a bit of wiggling (4). If one end doesn't seem to want to slide in, turn it around and try inserting from the other end.
6. You can leave this piece aside unless you want to measure a pair of glasses. Its purpose is to provide a stand to stabilize the glasses on.
7. Once the stand piece is in, you can slide it up and down as needed to provide a stable resting place for your glasses.
8. Squeeze the silver trigger on the back and hold the lens in question in the resulting aperture space. Release the trigger and the lens will be held firmly in its position (5).
9. Look through the eyepiece and find the green, starry shape that will be defining the focus. If it's off-center or totally missing, adjust the position of the lens in its measurement position. Once you find it and it's centered, turn the black dial on the right until it becomes clear and focused.
10. Read the little window on the left of the tool to see what the corresponding prescription is (6). Red and black numbers correspond to positive and negative.
