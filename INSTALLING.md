Installation Guide
==================

Copyright (c) Peter Wright 2026

After install, if something isn't working properly, see the [Troubleshooting Guide](TROUBLESHOOTING.md).


Quick Start
-----------

1. Make sure you have **NewDark 1.27 or 1.28** (see *Engine Version* below).
2. Take a backup of your Thief `user.bnd` file.
3. Install `gamepad.zip` with [DMM](https://github.com/pshjt/dmm) and enable the mod.
4. Run `MODS/gamepad/GamepadConfig.exe`. This copies `dinput.dll` into your game folder
   for you and lets you customise the mod. (If you prefer, you can skip the config tool
   and manually copy `dinput.dll` from `MODS/gamepad/` into the root of your game folder,
   alongside `THIEF.EXE` / `THIEF2.EXE`.)
5. See *Steam Deck, Proton and Wine* below for additional steps for Steam Deck

N.B. Without step 4 the mod cannot work — `dinput.dll` is what converts the engine's old DirectInput API to modern XInput and hooks into the core engine features the mod relies on.


Engine Version
--------------

The mod requires NewDark and supports *v1.27** and **1.28** (tested up to NewDark 1.28 20250515). I find 1.28 works best

If you're unfamiliar with Thief, the easiest way to get a recent, patched engine is to use one of these:

 - [RoguePatcher](https://www.ttlg.com/forums/showthread.php?t=152977)
 - [TFix](https://www.ttlg.com/forums/showthread.php?t=134733)
 - [NewDark 1.28](https://www.ttlg.com/forums/showthread.php?t=152974) — manual engine update ([download](http://ariane4ever.free.fr/ariane4ever/viewtopic.php?f=2&t=7502))


Backing Up Your Bindings
------------------------

By default, the mod enables joystick input and writes joybutton bindings to your `user.bnd` on launch. If it changes anything, it first backs up your previous settings to `user.bnd.bak`.

You should still take your own backup of `user.bnd` before installing, just in case. The values the mod applies are listed in the bundled `auto.user.bnd`.

If you'd rather manage your own bindings, set `force_joystick_binds = false` in `gamepad.ini`.


Recommended: High-DPI Mouse Settings
------------------------------------

For the smoothest look/camera control, tell the engine to treat the controller's right stick as a high-DPI mouse. Add the following two lines to `cam_ext.cfg` in your game folder:

```
use_raw_mouse_input 1
raw_mouse_sens_scale 0.5
```

Alternatively, keep the game's in-game Mouse Sensitivity slider reasonably low and raise the mod's own sensitivity in `GamepadConfig.exe`. A low in-game sensitivity lets the mod supply more precise inputs which reduces juddering.


Configuration
-------------

Run `MODS/gamepad/GamepadConfig.exe` to adjust deadzones, look sensitivity, rumble, button bindings, and more — and to update the mod when a new release is available. Settings are saved to a `gamepad.ini` in your game folder so they survive mod upgrades. You can also create or edit that `gamepad.ini` by hand; see the bundled file for the available options and their defaults.


Steam Deck, Proton and Wine
---------------------------

Under Proton or Wine, mark `dinput.dll` as **"native then built-in"** so the engine loads the
mod's DLL. In Steam, set the game's Launch Options to:

```
WINEDLLOVERRIDES="dinput=n,b" %command%
```

On Steam Deck, also remember to set Thief to use **Joystick mode** in the controller
settings.


Fan Missions
------------

If the mod doesn't work (for example in the default version of *The Black Parade*), edit the FM's `fm.cfg` and remove the `apply_dbmods 0` line. That line tells the engine not to load any `.dml`/`.osm` mods (normally to stop mods interfering with the FM, but this also blocks this mod from working).


Gamepads
--------

Any XInput device should work. The mod has been tested with:

 - The Xbox Wireless Controller (the primary target)
 - Playstation controllers (e.g. DualSense) via DS4Windows
 - Steam Deck

Updating
--------

The bundled `GamepadConfig.exe` includes an update feature (in the About tab)
