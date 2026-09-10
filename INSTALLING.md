Installation Guide
==================

Copyright (c) Peter Wright 2026

After install, if something isn't working properly, see the [Troubleshooting Guide](TROUBLESHOOTING.md).


Quick Start
-----------

If you're using the GOG version of Thief Gold, the mod is pre-installed. Otherwise:

1. Make sure you have **NewDark 1.27 or 1.28** (see *Engine Version* below on how to install it with TFix/T2Fix or RoguePatcher).
3. Download `gamepad.zip` and then run `GamepadConfig.exe` inside the .zip. Point it at your Thief or Thief 2 game folder, and it will install itself. If you're on Steam Deck, run it from the `steam-deck.zip` file instead.
4. See *Steam Deck, Proton and Wine* below for additional steps for Steam Deck

N.B. You can also install using [DMM](https://github.com/pshjt/dmm). If you do this, you'll need to run `MODS/gamepad/GamepadConfig.exe` to finish the installation.


Engine Version
--------------

A recent NewDark version is required (v1.27 or v1.28).

If you're unfamiliar with Thief, the easiest way is to use one of these updaters:

### Thief 1
 - [TFix Lite](https://drive.google.com/drive/folders/1CfuL9y-gzyZNb5n5b0098AxNclt2lZPs), or [TFix](https://www.ttlg.com/forums/showthread.php?t=134733)
 - [RoguePatcher](https://www.ttlg.com/forums/showthread.php?t=152977)
 - [NewDark 1.28](https://www.ttlg.com/forums/showthread.php?t=152974) — manual engine update ([download](http://ariane4ever.free.fr/ariane4ever/viewtopic.php?f=2&t=7502))

### Thief 2
 - [T2Fix Lite (Direct Download Link)](https://github.com/Xanfre/T2Fix/releases/download/1.27-2025-08-10/T2Fix_Lite_1.27-2025-08-10.exe)
 - [T2Fix](https://www.ttlg.com/forums/showthread.php?t=149669)


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

The Steam Deck Native Gamepad Config tool (called `GamepadConfig`, rather than `GamepadConfig.exe`) can be installed as a Non-Steam Game so you can configure the mod without having to return to Desktop mode.


Gamepads
--------

Any modern controller should work. The mod has been tested with:

 - PS5 and PS4 controllers
 - The Xbox Wireless Controller
 - Steam Deck

Updating
--------

The bundled `GamepadConfig.exe` includes an update feature (in the About tab)


Backing Up Your Bindings
------------------------

By default, the mod enables joystick input and writes joybutton bindings to your `user.bnd` at first launch. If it changes anything, it first backs up your previous settings to `user.bnd.bak`.
