GAMEPAD AND RADIAL MENU SUPPORT FOR THIEF 1 AND 2
=================================================

Copyight (c) Peter Wright 2026
https://www.ttlg.com/forums/showthread.php?t=153292

NOTE: INSTALL THIS MOD WITH DMM, Dark Engine Mod Manager
NOTE: THIS MOD INSTALLATION REQUIRES EXTRA STEPS AFTER DMM INSTALL!

To fully install this mod, install and enable with DMM, then go into MODS/gamepad/ and copy dinput.dll
into the root of your thief game folder (alongside THIEF.EXE or THIEF2.EXE)

Without this extra step, the mod cannot work.



ENGINE VERSION
--------------

This mod requires either:
 - The latest TFix 1.27
 - NewDark 1.28 20250515 (preferably; works best with TFix installed first)

 
 GAMES
 -----

 - Thief 1 (I have tested with Thief Gold)
 - Thief 2 (Only Mission 1 tested so far)

I have not tested it with Fan Missions, but it should work. Please report issues to me

OPERATING SYSTEM VERSIONS
-------------------------

I've tested with:
 - Crossover Office 26 (Wine, under macOS Apple Silicon - my primary target)
 - Windows 11


TROUBLESHOOTING
---------------

I'm poking around a bit at the internals of the NewDark engine for this mod, so more bugs are possible

1. The joypad sticks don't work in the main menu (or right stick works, left doesn't, A/B doesn't work)
 - This probably means you don't have dinput.dll installed in your Thief/Thief2 game folder (alongside your thief exe file)
 - Alternatively, it could be your controller isn't supported - I've only got an Xbox One controller (but it should work with any XInput controller), please get in touch with me and I'll see what I can do

2. The dpad navigation doesn't work in the main menu screen
 - This is likely caused by the game engine not being the expected version (the latest TFix 1.27, or ideally NewDark 1.28 20250515)
 - N.B. dpad navigation won't work in the Load/Save screen until NewDark 1.28 (and the save screen is fiddly for keyboard navigation in 1.28)

3. I can't move in-game using the left joystick
 - Check your user.bnd settings, see .bnd files in mod package

4. I can move but I can't look around
 - This can also be an issue in user.bnd, or if you don't hav edinput.dll in your game folder

5. The right stick is too sensitive!
 - Adjust the sensitivity in MODS/gamepad/gamepad.ini (optionally place your settings in game folder/gamepad.ini to save across mod version upgrades)

6. The game crashes at launch!
 - Check your game engine version. If in doubt get NewDark 1.28 referenced on TTLG
 - If you're still having issues, look at MOD/gamepad/gamepad.ini and change "enable_menu_navigation" to from "true" to "false"

7. The game crashes when I load a save / start a new game
 - This suggests a compatibility issue between the OSM
 
8. Everything works but I can't press RB to get the radial menu!
 - This usually means dinput.dll isn't loaded properly

9. You have changed how keys work / keys are behaving weirdly!
 - By default I try to auto-select the Key that will work for the Lock you're using (not all locks in all missions work), and unlock+open+unequip the key in one go.
 - You can disable this with MOD/gamepad/gamepad.ini, set "enable_automatic_key_selection" to "false"
 - This change is a slightly more streamlined version of J4FKeyring
 - If you have J4FKeyring installed, this mod will disable its own keyring handling and leave your J4FKeyring settings alone

10. I'm trying to customise the joystick binds and it's not working
 - Change force_joystick_binds in gamepad.ini to false


CREDITS
-------

 - Pixel Art by Plutonia - https://www.youtube.com/@Plutonia001
 - NewDark
 - osm-rs Dark Engine Scripting in Rust by Jarrod Doyle - https://github.com/JarrodDoyle/osm-rs