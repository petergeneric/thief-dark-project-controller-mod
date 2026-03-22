This mod aims to add full controller support to Thief 1 and Thief 2.

It is a work in progress

[![Watch the video](https://img.youtube.com/vi/HQQ11GK6pfg/maxresdefault.jpg)](https://www.youtube.com/watch?v=HQQ11GK6pfg)
[Demo Video](https://www.youtube.com/watch?v=HQQ11GK6pfg)

Features
--------
- Friendly radial menu for your inventory
- Time slows when the menu is open
- D-Pad navigation of key menus
- Automatic key management (where the Mission makes it possible), based on [Sarcoth's excellent J4F Keychain](https://github.com/saracoth/newdark-mods/releases/latest)


Installation
------------

1. Take a backup of your thief `user.bnd` file
2. Make sure TFix 1.27 is installed (or NewDark 1.28 20250515)
3. Download gamepad.zip and install using [DMM](https://github.com/pshjt/dmm)
4. Copy `dinput.dll` and `user.bnd` from `MODS/gamepad/` into your game folder

For more details, and troubleshooting, see [INSTALLING.md](INSTALLING.md)

Controls
--------

```
Left Stick          Move (analogue)
Right Stick         Look / camera

A                   Jump / mantle
B                   Crouch
X                   Use item
                    Throw Junk (if holding)

Y (tap)             Holster weapon / item
Y (hold)            Drop item

LT                  Block
RT                  Attack / use weapon

LB + Left Stick     Lean left / right / forward
RB (hold)           Radial inventory menu (select with left stick)

LS click            Toggle slow/fast movement mode
RS click            Toggle creep

D-pad Up            Cycle Weapons (next)
D-pad Down          Cycle Weapons (previous)
D-pad Left          Cycle Items (previous)
D-pad Right         Cycle Items (next)

Back                Map
Start               Game menu

Movement has two speed modes (toggle with LS click):
  Slow mode: gentle stick = walk, full deflection = run
  Fast mode: small range for walk, rest is run
Full stick deflection auto-exits slow mode. Keeping the stick below 30% for 1 second auto-returns to slow mode.
```

Configuration
-------------

Edit MODS/gamepad/gamepad.ini to adjust deadzone, sensitivity, and other settings and features.


Feedback
--------

Feedback welcome!

 - Create an issue on this repository
 - [TTLG](https://www.ttlg.com/forums/showthread.php?t=153292&p=2536935#post2536935)
 - [Bluesky](https://bsky.app/profile/levitime.com)
 - Dromed Discord
