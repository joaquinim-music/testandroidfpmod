# Android build notes — experimental Auto Windows fork

This ZIP is **source code**, not an installable `.geode` file.

The mod manifest already declares Geometry Dash Android 2.2081 support, and
 the repository's GitHub Actions workflow has Android32 and Android64 build
targets. That makes an Android build a reasonable target, but it still must
compile successfully against the correct Geode SDK and be tested in the Android
game before it can be called working.

## What changed in this revision

The experimental Auto Windows analyzer now pairs each jump press with its own
next matching release and shifts only that paired release while testing a click
offset. The previous logic could shift every later release of the same button,
which could corrupt replay timing.

## Important limitations

- The analyzer is experimental and has not been compiled or tested here.
- It needs an imported `.gdr` or `.gdr2` replay and the same level.
- It tests player-1 jump presses only.
- It replays the level from the beginning for each offset, so long replays can
take a very long time.
- Android support in `mod.json` is not proof that this modified code builds or
runs correctly on Android.

## Build path

Use the included `.github/workflows/build.yml` in a GitHub repository and run
the workflow. It is configured for Android32 and Android64 builds. Install only
the resulting Android-compatible `.geode` artifact that matches the architecture
and game setup supported by the device and Geode installation.
