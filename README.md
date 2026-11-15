# Warzone Aimbot

Download: soon

Aimbot module for Call of Duty Warzone that runs from an external overlay.

## Behaviour

- targets by crosshair distance, lowest HP or nearest
- configurable FOV circle and smoothing curve
- visibility check so it ignores walls
- hold or toggle mode, keybind free to change
- enemy / knocked / teammate filters

## Needs

Windows 10/11, Battle.net, administrator for the loader.

Install: extract, loader as admin, start the game, INSERT, bind the key. Ricochet is strict, test on a spare account.


## Compatibility

## Compatibility

- Windows 10 21H2 and newer, Windows 11 all builds
- borderless, windowed fullscreen, and windowed work
- 16:9 and 21:9 supported, other ratios render correct after a restart
- DPI scaling above 125% is handled by the loader

## Troubleshooting

## Troubleshooting

**Overlay does not show.** Switch the game to borderless or windowed fullscreen, exclusive fullscreen hides every overlay.

**Menu does not open.** Run the loader as administrator, INSERT is ignored without elevation.

**Nothing attaches.** Start the loader before the game. If the process is already running, restart it.

**Wrong values after a patch.** Wait for the next build, offsets are version specific.

**Overlay flickers in OBS.** Enable streamproof and capture the game with game capture, not display capture.

## Notes

## Notes

- keep the loader and config.json in the same folder
- profiles are plain text, edit them while the game is closed
- close other overlays (Discord, GeForce, RTSS) before attaching
- the first launch after a patch can take a few seconds longer while offsets load

## Aim tuning

| Parameter | Default | Range | Meaning |
| --- | --- | --- | --- |
| fov | 7 | 1-30 | radius in degrees where the aim reacts |
| smooth | 4.0 | 1.0-12.0 | higher is slower and more human |
| bone | head | head/chest/nearest | priority joint |
| visible_only | on | on/off | ignore targets behind geometry |
| hold_mode | on | on/off | aim only while the key is held |
| key | MOUSE5 | any | activation button |

## Architecture

## Architecture

The loader stays outside the game process and reads state through a handle, then paints an overlay window on top. Because nothing is injected, a game crash never takes the tool with it and the anti-cheat sees a normal desktop overlay.

The reader refreshes offsets on start, so a build works across restarts without a relaunch of Windows.

## FAQ

## FAQ

**Is it external or internal?** Read the first line of this page, the mode is written there.

**Does it need a key?** No.

**Can I move the config to another PC?** Yes, copy config.json next to the loader.

**Will a patch break it today?** Possibly, offsets are refreshed with each release.

**Is the overlay visible in clips?** Only if streamproof is off.