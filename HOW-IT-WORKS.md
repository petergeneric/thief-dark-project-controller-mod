How The Controller Mod Works
============================

The Dark Engine had old single-stick Joystick support via DirectX's old DirectInput interface.
This mod ships with a custom `dinput.dll` that is actually a shim between modern native controller APIs and the Dark Engine.

At startup, it claims to be an DirectInput joystick, behaving like a joystick that's plugged-in
but not used until the player connects a gamepad to their machine. At that point
it forwards the button/stick inputs to the Dark Engine.

To talk to controllers natively, I use SDL3. For the Dualsense controller, I also have custom
logic that talks directly to the controller via Bluetooth to send advanced haptic information,
which is ordinarily not supported wirelessly in Windows games.


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

It's best to configure the Dark Engine to use high-dpi mouse mode, otherwise small stick
deflections can have 'judder' because we can only move a tiny number of screen pixels
(and since we must move the mouse by whole number of pixels, if we want to move 0.5
pixels then we have to do this via a series of 0 and 1 pixel movements to average out to 0.5).


## Radial Menu

The radial menus allow the player to view and choose from their inventory with the joysticks.

The mod detects when RB is pressed, signals a SimTime scale change to the engine and then
switches to internal control mode, where it stops sending gamepad inputs to the engine, handling them itself.


# In Menus

The Dark Engine has no way to signal to cooperating processes whether the player is in a menu,
and if so which menu they are in. But its internal state knows this. On startup the mod
scans through the Dark Engine's RAM and identifies the locations of key menus, and when it
detects Menu Mode it checks these different locations to see which is active.

When the mod detects the engine is in menu mode, it scans through in-memory structures to find
the active menu, and that menu's clickable regions. DPad buttons move the mouse between those
clickable rectangles.

For the Save/Load menu, we go further and look for the individual slots (which are not
reported as clickable menu rectangles), and then move between them.

# Haptics/Rumble

If haptics support is enabled, at startup the game attempts to find pre-defined Sound functions
that I have located (supported in 1.27 and both 1.28 versions) and installs hooks into them
so that when the engine starts playback of a sound, the sound file name can be inspected
and translated into a haptic event.

The engine also communicates to the sound system the world position of the sound, as well as
the world position of Garrett's "ears", which I use to detect whether the sound was produced
by/on the player.

Haptic events are filtered by user preference (e.g. we detect each footstep and sheath/unsheath,
but having a controller vibrate for all of those would be overwhelming for the player.

When the haptic system decides to play a haptic event for the player, it passes it off to one
of two haptic drivers:

1. Traditional Rumble
2. Dualsense Advanced Haptics

## Rumble

Traditional rumble uses Eccentric Rotating Motors: a motors with an off-centre weight. One motor
has a light weight, the other has a heavy weight (for lower frequency rumble).
The mod loads `.rumble` files, which identify which motor to spin, by how much, and for how long.

## Advanced Haptics

The dualsense uses Voice Coil Motors, which vibrate a weight back and forth like a speaker for
low frequencies. This allows for incredibly subtle nuanced vibration patterns that change at
a high rate. The mod embeds the Meta Haptics SDK, reading `.haptic` files and then at runtime
rendering them into waveforms to be sent to the Dualsense controller. This approach means that
in the future new profiles can be added for new controller types. Haptic patterns can be
authored/customised in Meta's Open Source Haptics Studio. The default patterns that ship with
the mod are based on the audio files.

### Footsteps

Unlike ERMs, the Dualsense Voice Coil Motors are essentially identical between left/right.
When player footstep haptics are enabled, the mod pans footsteps to the left and right
of the controller, matching which foot Garrett is setting down in-game.

## FM Haptics and Controller Sounds

I would be really excited if a FM author wanted to add custom haptics/rumble into their mission.
The mod as-is can intercept any triggered sounds, so for example a squeaky floorboard could
trigger a different haptic.

Another possibility is playing custom sounds through the Dualsense speaker - imagine ghost
whispers or chains playing through the controller's speaker independently of the game's normal
audio.

Reach out to me if you're interested in doing this!
