# Meteor + mcopt Metal compatibility

> **Experimental vibe code — use at your own risk.** No guarantee of correctness, stability, performance or future compatibility. Back up your Prism instance and worlds.

A compatibility bridge for **Meteor Client 26.3-15** and **mcopt Metal 0.3.0-alpha.2** on Minecraft 26.3 Fabric / Apple Silicon. It fixes the GUI `MetalDevice -> IGpuDevice` crash while retaining mcopt Metal.

## Recommended: separate Meteor addon

Use `meteor-mcopt-compat-0.1.1.jar` with the **original** `meteor-client-26.3-15.jar` and mcopt 0.3.0-alpha.2. Do not use it alongside `meteor-client-26.3-15-mcopt-compat.1.jar`. Remove the old 0.1.0 addon JAR first.

1. Remove the earlier patched Meteor JAR and restore the original Meteor 26.3-15 JAR.
2. Put the original Meteor JAR, mcopt and the addon JAR together in the Prism instance's `mods` folder.
3. Remove `-Dmcopt.metal=false` if present.
4. Launch, confirm F3 says `Metal 3 (mcopt)`, then test Meteor GUI/text fields.

Version 0.1.1 detects the Metal backend and skips only Meteor's **Blur** module, which otherwise triggers a confirmed native Apple Metal crash. It shows one Meteor warning in chat instead of letting the game process crash. Blur remains unchanged on non-Metal renderers.

Addon JAR SHA-256: `e34f4f458a58a6e6cca0a25c5988ed3b6596108970da7a8aac41d19b565e1103`.

`meteor-mcopt-compat-addon-0.1.1-source.zip` contains the buildable GPL-3.0 addon source.

## Earlier patched-Meteor build

`meteor-client-26.3-15-mcopt-compat.1.jar` and `meteor-mcopt-compat.patch` are retained as the earlier standalone workaround. Prefer the addon above.

## Verification

The 0.1.1 addon compiles successfully with Java 25. The prior GUI-scissor fix was reported to work in one Apple-Silicon Prism installation; the Blur guard is based on a crash trace that disappears when Meteor Blur is disabled. This is not broad runtime compatibility testing.

## License

GPL-3.0 for the Meteor-derived compatibility work; mcopt is Apache-2.0.
