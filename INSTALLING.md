GAMEPAD AND RADIAL MENU SUPPORT FOR THIEF 1 AND 2
=================================================

Copyight (c) Peter Wright 2026
https://www.ttlg.com/forums/showthread.php?t=153292

NOTE: INSTALL THIS MOD WITH DMM, Dark Engine Mod Manager
NOTE: THIS MOD INSTALLATION REQUIRES EXTRA STEPS AFTER DMM INSTALL!

To fully install this mod, you need to also copy the following files from this mod folder
into the root of your thief game folder (alongside THIEF.EXE or THIEF2.EXE)

1. dinput.dll
2. user.bnd (alternatively, see below for exact settings to use)

Without both of these steps (and installing the mod via DMM) it will not work.



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
 - Crossover Office 26 (Wine, macOS Apple Silicon - my primary target)
 - Windows 11


user.bnd
--------

```
;This mod requires the joystick to be enabled so we can support native analog left stick movement

joystick_enable 1
joystick_sensitivity 3.0
; No deadzone for Thief - the mod handles deadzone itself
joystick_deadzone 0.0
bind joy_axisx +joyxaxis
bind joy_axisy +joyforward
bind joy1 +jumpblock
bind joy10 +walkfast
bind joy11 +block
bind joy12 +use_weapon
bind joy13 drop_item
bind joy2 crouch
bind joy3 +use_item
bind joy4 clear_weapon
bind joy5 +leanleft
bind joy6 +leanright
bind joy7 automap
bind joy8 sim_menu
bind joy9 +creepon

; freelook is required, but you probably have this enabled already
freelook 1
```

TROUBLESHOOTING
---------------

I'm poking around a bit at the internals of the NewDark engine for this mod, so more bugs are possible

1. The joypad sticks don't work in the main menu (or right stick works, left doesn't, A/B doesn't work)
 - This probably means you don't have dinput.dll installed in your Thief/Thief2 game folder (alongside your thief exe file)
 - Alternatively, it could be your controller isn't supported - I've only got an Xbox One controller (but it should work with any DirectInput controller), please get in touch with me and I'll see what I can do

2. The dpad navigation doesn't work in the main menu screen
 - This is likely caused by the game engine not being the expected version (the latest TFix 1.27, or ideally NewDark 1.28 20250515)
 - N.B. dpad navigation won't work in the Load/Save screen until NewDark 1.28 (and the save screen is fiddly for keyboard navigation in 1.28)

3. I can't move in-game using the left joystick
 - Check your user.bnd settings, see above

4. I can move but I can't look around
 - This can also be an issue in user.bnd, or if you don't hav edinput.dll in your game folder

5. The right stick is too sensitive!
 - Adjust the sensitivity in MODS/gamepad/gamepad.ini

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

10. The icons are weird in the menu
 - Yes, I'm not able to use the game models for the menu, so it relies on manual artwork

11. I'm trying to customise the joystick binds and it's not working
 - Change force_joystick_binds in gamepad.ini to false
12. The Skybox is messed up
 - This might be me? I'm hooking in to NewDark's DirectX Device for the overlay, and I'm trying to figure out if it's me or just a coincidental NewDark glitch on my hardware


CREDITS
-------

 - Pixel Art by Plutonia - https://www.youtube.com/@Plutonia001
 - NewDark
 - osm-rs Dark Engine Scripting in Rust by Jarrod Doyle - https://github.com/JarrodDoyle/osm-rs