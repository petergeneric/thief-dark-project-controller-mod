This mod adds full controller support to Thief 1 and Thief 2.

[![Download Latest Version](https://img.shields.io/badge/Download-Latest%20gamepad.zip-brightgreen?style=for-the-badge&logo=github)](https://github.com/petergeneric/thief-dark-project-controller-mod/releases/download/v1.8.1/gamepad.zip)  
[![Get it on GOG](https://img.shields.io/badge/Get%20it%20on%20GOG-v1.8%20preinstalled-9e8ba8?style=for-the-badge&logo=gogdotcom&logoColor=white)](https://www.gog.com/game/thief_gold)
  
[![Watch the video](screenshot.jpeg)](https://www.youtube.com/watch?v=HY29B94PAuA)
[Demo Video](https://www.youtube.com/watch?v=HY29B94PAuA)


Features
--------
- Friendly radial menus for weapons and inventory
- Keyboard/mouse radial supprt
- Time slows when the menu is open
- D-Pad navigation of key menus
- Optional automatic key management (where the mission makes it possible), based off [Sarcoth's excellent J4F Keychain](https://github.com/saracoth/newdark-mods/releases/latest).


GOG Installation / Update
-------------------------
[The GOG version of Thief Gold](https://www.gog.com/en/game/thief_gold) comes with v1.8.1 of this mod pre-installed, this is the easiest way to get started with Thief.
Install the GOG version, then launch Gamepad Settings from GOG Galaxy, go to the About tab and Check For Updates to update to the latest version.

Future GOG updates could re-install earlier versions of the mod, so you may wish to copy your install out of the GOG Galaxy folder.

Manual Installation
-------------------

See [Install Guide](INSTALLING.md) for full information. Basic process is:

1. You'll need NewDark 1.27 or 1.28. If in doubt, [use RoguePatcher](https://www.ttlg.com/forums/showthread.php?t=152977) or [TFix](https://www.ttlg.com/forums/showthread.php?t=134733). You can also directly install [NewDark 1.28]([https://www.ttlg.com/forums/showthread.php?t=152974](http://ariane4ever.free.fr/ariane4ever/viewtopic.php?f=2&t=7502)) (per [this TTLG thread](https://www.ttlg.com/forums/showthread.php?t=152974)). I find NewDark 1.28 works best.
2. Take a backup of your thief `user.bnd` file
3. Install gamepad.zip using DMM, and enable the mod
4. Run `MODS/gamepad/GamepadConfig.exe` (or copy `dinput.dll` from `MODS/gamepad` into your thief install folder)
5. *Steam Deck users:* Add `WINEDLLOVERRIDES="dinput=n,b" %command%` to your Thief launch arguments in Steam, and enable Joystick Mode for Thief.

Controls
--------

<details open>
<summary><b>Xbox layout</b> (click to show/hide)</summary>

![Xbox binding diagram](bindings.svg)

</details>

<details>
<summary><b>DualSense layout</b> (via DS4Windows or v2-prerelease. Click to show/hide)</summary>

![DualSense binding diagram](bindings-ds5.svg)

</details>


<details open>
<summary><b>Default Bindings</b> (click to show/hide)</summary>

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

LB + Dpad Up/Down   Zoom in/out (Thief 2)
					N.B. does not work with arrows if Bow Zoom is enabled (game limitation)
LB + Dpad Left		Cycle Lockpick (Triangle/Square picks)

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

</details>

Configuration
-------------

Use *MODS/gamepad/GamepadConfig.exe* to adjust deadzone, sensitivity, customise button bindings, and more. You can also manually add your own gamepad.ini in the game's folder and customise it.

When adjusting look sensitivity, I find it best to keep the game's Mouse Sensitivity reasonably low and increase the mod's sensitivity - this will provide smoother motion at slow speeds (due to how passing mouse inputs to games works).
Alternatively, enable high dpi mouse settings for the game per the [Install Guide](INSTALLING.md#recommended-high-dpi-mouse-settings).

Feedback
--------

If you run into a problem, please check the [Troubleshooting Guide](TROUBLESHOOTING.md), and raise a github issue if that doesn't help.

Links
-----

 - [TTLG](https://www.ttlg.com/forums/showthread.php?t=153292&p=2536935#post2536935)
 - [ModDB](https://www.moddb.com/mods/thief-controller-mod)
 - Visit the Dromed Discord
