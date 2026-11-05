# Meteor + mcopt Metal compatibility

> **Experimental vibe code — use at your own risk.** No guarantee of correctness, stability, performance or future compatibility. Back up your Prism instance and worlds.

A compatibility bridge for **Meteor Client 26.3-15** and **mcopt Metal 0.3.0-alpha.2** on Minecraft 26.3 Fabric / Apple Silicon. It fixes the GUI `MetalDevice -> IGpuDevice` crash while retaining mcopt Metal.

## Recommended: separate Meteor addon

Use `meteor-mcopt-compat-0.1.0.jar` with the **original** `meteor-client-26.3-15.jar` and mcopt 0.3.0-alpha.2. Do not use it alongside `meteor-client-26.3-15-mcopt-compat.1.jar`.

1. Remove the earlier patched Meteor JAR and restore the original Meteor 26.3-15 JAR.
2. Put the original Meteor JAR, mcopt and the addon JAR together in the Prism instance's `mods` folder.
3. Remove `-Dmcopt.metal=false` if present.
4. Launch, confirm F3 says `Metal 3 (mcopt)`, then test Meteor GUI/text fields.

Addon JAR SHA-256: `e687ab5ddeb42278cc6fd199bcacf8bd842b67c70bf9388bb768c80b5245ee4c`.

`meteor-mcopt-compat-addon-0.1.0-source.zip` contains the buildable GPL-3.0 addon source.

## Earlier patched-Meteor build

`meteor-client-26.3-15-mcopt-compat.1.jar` and `meteor-mcopt-compat.patch` are retained as the earlier standalone workaround. Prefer the addon above.

## Verification

Both the patched-Meteor build and the addon compiled successfully with Java 25. The original patched build was reported to work in one Apple-Silicon Prism installation. This is not broad runtime compatibility testing.

## License

GPL-3.0 for the Meteor-derived compatibility work; mcopt is Apache-2.0.
