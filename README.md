# Meteor + mcopt Metal compatibility patch

> **Experimental vibe code — use at your own risk.** This project was produced as a quick compatibility patch, and I do not guarantee its correctness, safety, stability, performance, or future compatibility. Back up your Prism instance and worlds before using it.

A test patch for **Meteor Client 26.3-15** with **mcopt Metal 0.3.0-alpha.2** on Minecraft 26.3 Fabric / Apple Silicon.

It addresses the GUI crash caused by `mcopt.metal.MetalDevice` not implementing Meteor's internal `IGpuDevice` interface. The patch preserves mcopt's Metal renderer and forwards Meteor's active GUI scissor state to each Metal render pass.

## Contents

- `meteor-client-26.3-15-mcopt-compat.1.jar` — experimental replacement for Meteor 26.3-15.
- `meteor-mcopt-compat.patch` — source patch against Meteor commit `e3a2e77967629d216e127b5ceecf71fb15f9d2e5`.
- `README-mcopt-meteor-compat.md` — installation and test checklist.

## Install

1. Back up the instance (and your worlds).
2. Remove the stock `meteor-client-26.3-15.jar` from the instance's `mods` directory — do not keep both Meteor JARs.
3. Add the compatibility JAR.
4. Keep mcopt 0.3.0-alpha.2 installed and remove the `-Dmcopt.metal=false` workaround if you used it.
5. Launch and confirm that F3 shows `Metal 3 (mcopt)`.

## Verification status

The JAR was compiled successfully with Java 25 and the source patch was checked against a clean Meteor 26.3-15 source snapshot. It was reported to work in one real Apple-Silicon Prism installation, but that is **not** a broad compatibility guarantee.

SHA-256 for the included JAR:

`858ec7262c7f9e1f2a1e54ac5aef7e94cfd69a199f21e9cb882003d588a9014d`

## License

Meteor Client is GPL-3.0; this derivative patch/build is published under GPL-3.0 as well. mcopt itself is Apache-2.0.
