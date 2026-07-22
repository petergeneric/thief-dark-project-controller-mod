# Haptics - Sound Trigger

The mod allows FM Authors to add custom haptics features to their FMs.

Please reach out if you have ideas for improvements, or want help - I'd be really excited to have a FM do this!
Currently haptics don't loop, they just play once when the engine sound starts.
If you wanted, e.g. a rainfall patter, you could add a repeating rain drone that triggers a subtle haptic for Dualsense.


The gamepad mod works based on sound triggers for key haptics. This means when you
play a particular sound, it can trigger a haptic playback to the player's controller.

Put a `haptics.ini` file in your FM root:

```
[CustomSoundTriggers]
rockfall = true
rockslid = true
```

Then place a .rumble and .haptic file into your mod's `haptics` folder:

```
haptics/rockfall.rumble
haptics/rockfall.haptic

haptics/rockslid.rumble
haptics/rockslid.haptic
```

## Haptic Authoring: Dualsense

The Dualsense controller uses a Voice Coil Motor. This allows for advanced haptics.
You can author these haptics in Meta's open source "Haptics Studio".

I have a fork of this that lets you author and play back haptics on a controller interactively.

You produce a .haptic file, which is a JSON description of the impulses, and at runtine the mod
will generate a waveform to send to the controller.

## Haptic Authoring: Rumble

Rumble uses weighted motors: one for high frequencies and one for low. The .rumble format for the
mod describes how to drive these motors. For example, use this .rumble file content for a heartbeat rumble:

```
{
"generic": [
  { "lo": 20, "hi": 0,  "dur": 25  },
  { "lo": 0,  "hi": 0,  "dur": 200 },
  { "lo": 0,  "hi": 20, "dur": 25  },
  { "lo": 0,  "hi": 2,  "dur": 10  },
  { "lo": 0,  "hi": 0,  "dur": 745 }
]
}
```

I have a tool that will turn a .haptic into a .rumble, but you'll get the cleanest and best results
by experimenting with values yourself. I have a fork of Meta Haptic Studio that will let you preview
the results with a Dualsense or Xbox controller.



## Caveats

Currently you can't define a custom sound that starts with "ft", because this is special-cased for the
footstep path internally by the mod.