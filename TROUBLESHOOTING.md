TROUBLESHOOTING
---------------

1. The joypad sticks don't work in the main menu (or right stick works, left doesn't, A/B doesn't work)
 - This probably means you don't have dinput.dll installed in your Thief/Thief2 game folder (alongside your thief exe file)
 - Alternatively, it could be your controller isn't supported - I've only got an Xbox One controller (but it should work with any XInput controller), please get in touch with me and I'll see what I can do

2. The dpad navigation doesn't work in the main menu screen
 - This is likely caused by the game engine not being the expected version (NewDark 1.27 or 1.28)

3. I can't move in-game using the left joystick
 - Check your user.bnd settings, see .bnd files in mod package

4. I can move but I can't look around
 - This can also be an issue in user.bnd, or if you don't have dinput.dll in your game folder

5. The right stick is too sensitive!
 - Adjust the sensitivity with MODS/gamepad/GamepadConfig.exe - you may also wish to set up high-dpi mouse settings in `cam_ext.cfg`, see INSTALLING.md for more information.

6. The game crashes at launch!
 - Check your game engine version, check any other game overlays or aggressive antivirus software; I'm aiming to make the mod co-exist nicely with other software, so raise a github issue if you can figure out what the cause was and I will try to reproduce and build a fix.

7. The game crashes when I load a save / start a new game
 - This suggests a compatibility issue between the OSM and `dinput.dll`
 
8. Everything works but I can't press RB to get the radial menu!
 - This usually means dinput.dll isn't loaded properly, or is not up-to-date. Reinstall it from the latest github release.

9. Dpad Item Cycling doesn't work like the keyboard `[` and `]` keys
 - That's correct, and by design (albeit I wish it was possible to have identical behaviour). The Dark Engine has a concept of a 'defocused' inventory item, but provides the mod no way to figure out whether an item is focused/defocused, so I have to work around this by ignoring the focused state.

10. I'm trying to customise the joystick binds and it's not working
 - Change force_joystick_binds in gamepad.ini to false

11. The game is juddery at higher framerates
 - This appears to be mostly an engine limitation; enabling high dpi mouse input (see INSTALLING.md) can help with this somewhat.  

12. The overlay isn't working, or is behaving strangely and I have RivaTuner installed
 - RivaTuner appears to be a bad citizen, and aggressively removes any hooks but its own. Its 'detour' mode appears to work collaboratively with other mods. Despite this, RivaTuner may interfere in other ways, I'd recommend disabling/removing it entirely.
