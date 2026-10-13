# Microphone Echo in a Live-Event Audio Chain

**Role:** Sound and lights technician's assistant (volunteer)
**Equipment:** Behringer X32 mixer, Scarlett Solo USB interface, Mac mini running ProPresenter
**Status:** Resolved

## Symptom

With ProPresenter active, the room had scratching noise and a delayed copy of every microphone. Muting the X32 channel that receives ProPresenter audio stopped it immediately, which showed the delayed audio was returning through that channel.

## Root cause

An unintended routing loop:

```
Microphones -> X32 -> Scarlett Solo -> ProPresenter channels 3 and 4 -> External Headphones output -> X32
```

ProPresenter channels 3 and 4 carried the house mix in for the livestream, but they were also routed to the Main output going back to the X32, so the room heard a slightly delayed copy of itself. The loop also risked loud feedback.

## Fix

- Confirmed the loop by muting the return channel.
- Checked the ProPresenter audio settings, input routing, and the Main routing grid.
- Removed the two Main output routes for channels 3 and 4.
- Left channels 1 and 2 routed so videos and music still play in the room.
- Raised the return fader slowly while testing the microphones. The echo was gone.

## Why it worked

Playback audio (channels 1 and 2) and livestream input audio (channels 3 and 4) are now separate paths. Channels 3 and 4 still receive the house mix for streaming, but no longer send it back to the room.

## Recovery checklist

1. If echo returns, mute the ProPresenter return channel on the X32.
2. Check ProPresenter Settings, Audio, Main routing.
3. Only channel 1 to device 1 and channel 2 to device 2 should be selected.
4. Channels 3 and 4 must not be routed to External Headphones.
5. Test at low volume before raising the fader.
