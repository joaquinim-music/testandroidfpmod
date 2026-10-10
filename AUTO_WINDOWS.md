# Automatic Click Window Analyzer

This fork adds an experimental **Auto Windows** button to Frame Window Counter.

## What it does

- Keeps the original GDR/GDR2 input stream when a replay is imported.
- Uses the real Geometry Dash `PlayerObject::pushButton` / `releaseButton` calls to replay the macro.
- Tests a selected 1P Jump press at offsets around its original frame.
- Shifts the matching release by the same amount so the click duration stays intact.
- Detects success when the level reaches `PlayLayer::levelComplete()` and failure when the player dies.
- Stores measured windows in the existing `FrameAction.frameWindow` field.
- Writes a text report to the mod's `AutoWindows` save folder.

## Important

This is an experimental first implementation. It currently scans offsets from -12 to +12 frames and tests each click independently by replaying the level from the start. A long macro can therefore require a very large number of full level replays.

The analyzer currently measures **1P Jump press inputs**. It does not yet use GDR2 physics-extension data, random-seed restoration, or checkpoint-based acceleration.

## How to use

1. Build/install this modified mod.
2. Import the `.gdr`/`.gdr2` replay normally once. The raw input stream is retained in memory for the analyzer.
3. Load the same Geometry Dash level the replay was recorded on.
4. Turn off Practice Mode.
5. Open the Frame Window Editor and press **Auto Windows**.
6. Leave the game alone while the analyzer runs.
7. When it finishes, the measured values are written back into the Frame Window fields and a text report is saved under `AutoWindows`.
