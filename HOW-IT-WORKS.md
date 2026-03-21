How The Controller Mod Works
============================

The Dark Engine had old single-stick Joystick support via DirectX's old DirectInput interface.
Modern pads use XInput. This mod ships with a custom `dinput.dll` that is actually
a shim between the OS-native DirectX and the Dark Engine.

At startup, it claims to be an DirectInput joystick, behaving like a joystick that's plugged-in
but not used until the player connects a XInput device to their machine. At that point
it forwards the button/stick inputs to the Dark Engine.



# In Game

## Left Stick - Passthrough

The Dark Engine's joystick support allows for fully analog movement. This actually allows
for movement slower than the keyboard can support. Sound emission when moving is directly
proportional to movement speed, so creeping with the joystick barely pushed can be
very quiet.

The mod includes two motion curves: a "slow" curve that allows for precise control of
the slowest creeping speed, and "fast" that prefers walking / running. If you keep your
stick barely pushed then it will switch automatically to the "slow" curve. As soon as you
go full deflection, it will always switch to the "fast" curve. You can currently manually
switch by pressing the left stick.

Getting the exact stick feel right is a work in progress. Advice from devs with experience
would be very welcome.

## Right Stick - Mouse Mapping

The Dark Engine doesn't have native stick support for freelook, so the right stick emulates
the mouse.


## Radial Menu

The radial menu allows the player to view and choose from their inventory with the joysticks.

The mod detects when RB is pressed, signals a SimTime scale change to the engine and then
stops sending gamepad inputs to the engine, handling them internally.


# In Menus

The mod detects whether the game is in a menu by checking how it's managing the mouse.
When in-game, the engine resets the mouse to the centre of the screen every frame.
When the engine stops doing this, the mod enables Menu Mode. It achieves this by
hooking into the function the engine calls.

Menu Mode operates in three different ways:
1. **Generic**: map left+right stick to the mouse (with different sensitivity curve to gameplay),
and A/B to Left Click and Escape key respectively. This is always active.
2. **Dark Menu Navigation**: where there are 3 or more Engine-level buttons on-screen, the mod 
detects this and the D-Pad navigates between them. Unfortunately not all clickable items are
actually top-level Dark Engine buttons ("rects"), so e.g. the start-of-level shop UI cannot
be fully automated with the D-Pad (same with the options menu)
3. **Fallback Arrow Keys mode**: NewDark 1.28 has, quite excitingly, added arrow key navigation
on the Load and Save menus. It works very well on the Load menu, and less well on the Save
menu. When in this mode (which is enabled if Dark Menu Navigation isn't possible on the screen)
then the mod maps D-Pad inputs to arrow keys.

## Detection

The Dark Engine has no way to signal to cooperating processes whether the player is in a menu,
and if so which menu they are in. But its internal state knows this. On startup the mod
scans through the Dark Engine's RAM and identifies the locations of key menus, and when it
detects Menu Mode it checks these different locations to see which is active.

# Extra Features

In order to make the game play in a more modern way, the mod *optionally* adds a Keyring mod.
I'm in two minds about whether this is the right thing to do, because it does change the
actual gameplay (to a more modern style, I think, but undeniably it's a change), and this
might be against the wishes of FM authors. I'd love feedback on this design decision from
FM authors!

This functionality can be disabled in gamepad.ini, and automatically disables itself if
it detects the J4F Keyring mod is also installed.

## Rationale

One rationale for including support for a Keyring mod natively in my mod is that I can do
things that a squirrel script cannot: the mod detects an attempt to frob a locked door and,
if we have a matching key, it kicks off a FSM that automates the following interaction:
1. Equip key
2. Trigger Use action (to bring the key into the centre of the screen)
3. Trigger Use action (to unlock+open the door)
4. Unequip the key (to avoid accidentally re-locking the door)

This last stage in particular requires access to an engine-internal Inventory Service.

# NewDark Engine Hacking

The NewDark engine is amazing, but it doesn't expose everything we need, so I've had to do
some disassembly and reverse engineering work on it to get to the structures I need.

Ideally I'd love to actually have first-class engine support for this, because it'd make
it really clean for other developers to do similar things without worrying about new
engine releases breaking functionality.

If only NewDark was open to PRs!

Here are the following areas that I have to peek inside / modify the engine:
1. Accessing internal COM services (InventoryService) - I trick the OSM script module into
giving me access to COM services that weren't intended to be supplied to script modules,
because otherwise there is no way I can see to unequip an Item, InvSelect rejects immediately
if passed ObjectId 0.
2. Menu Detection: hooking into pointer reset calls
3. Menu Detection: scanning memory locations to find Main Menu, etc. structures
4. Sim Time: the engine appears to suppport changing sim_time with a debug command (symbol
exists in THIEF.EXE but running it does nothing), however the engine does store an internal
sim time step value. I scan for this structure at startup (looking for initial values) and
allow changing it while the game is running. I use this to slow down time while the
radial menu is open. This is another area where an engine mod to enable sim_time command
would be really helpful, and it could potentially be opened up to other mods (although not
without its issues, since setting it too low can cause problems that the OSM can't repair)
5. EndFrame: to render the radial menu, I hook into EndFrame and then inject arbitrary
draw commands after the engine has done its work for the frame. The goal by doing this
is to allow a more complex set of overlays than is possible with the DarkOverlay service.
Currently the radial menu probably could be handled with Dark overlays and transparency, but
eventually I want to render item models directly rather than image icons (so that FM items
can appear cleanly)
6. Direct3D Device Capture: in order to do my EndFrame trick, I need to intercept the
Direct3D Device the game creates.
