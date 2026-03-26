This mod aims to add full controller support to Thief 1 and Thief 2.

It is a work in progress

[![Watch the video](https://img.youtube.com/vi/Vp-ogAktpUI/maxresdefault.jpg)](https://www.youtube.com/watch?v=Vp-ogAktpUI)
[Demo Video](https://www.youtube.com/watch?v=Vp-ogAktpUI)
Features
--------
- Friendly radial menus for weapons and inventory
- Time slows when the menu is open
- D-Pad navigation of key menus
- Automatic key management (where the mission makes it possible), based off [Sarcoth's excellent J4F Keychain](https://github.com/saracoth/newdark-mods/releases/latest). Optional.


Installation
------------

1. Take a backup of your thief `user.bnd` file
2. Install TFix 1.27, (optionally and preferably add NewDark 1.28 20250515)
3. Download gamepad.zip and install using [DMM](https://github.com/pshjt/dmm)
4. Copy `dinput.dll` from `MODS/gamepad/` into your game folder

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

Y (tap)             Equip/Holster weapon
Y (hold)            Drop item

LT                  Block
RT                  Attack / use weapon

LB + Left Stick     Lean left / right / forward
RB (hold)           Radial inventory menu (select with left/right sticks
RB (hold) + Y		Unequip Weapon+Item

RS click            Force sneak speed

D-pad Up            Cycle Weapons (next)
D-pad Down          Cycle Weapons (previous)
D-pad Left          Cycle Items (previous)
D-pad Right         Cycle Items (next)

Back                Map
Back (hold)			Equip/Unequip item
Start               Game menu

L3+Y				Quicksave
L3+B				Quickload

Movement has two speed modes (toggle with LS click):
  Slow mode: gentle stick = walk, full deflection = run
  Fast mode: small range for walk, rest is run
Full stick deflection auto-exits slow mode. Keeping the stick below 30% for 1 second auto-returns to slow mode.
```

Configuration
-------------

Edit *MODS/gamepad/gamepad.ini* to adjust deadzone, sensitivity, customise button bindings, and more.


Feedback
--------

Feedback welcome!

 - Create an issue on this repository
 - [TTLG](https://www.ttlg.com/forums/showthread.php?t=153292&p=2536935#post2536935)
 - [Bluesky](https://bsky.app/profile/levitime.com)
 - Dromed Discord
