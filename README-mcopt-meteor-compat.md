# Meteor 26.3-15 + mcopt 0.3.0-alpha.2 test build

This is an experimental compatibility build for Minecraft 26.3 Fabric on Apple Silicon. It keeps mcopt's Metal renderer enabled and patches Meteor's GUI scissor handling.

Built from Meteor commit `e3a2e77967629d216e127b5ceecf71fb15f9d2e5` (the source state corresponding to the 26.3-15 build) with mcopt 0.3.0-alpha.2 source/API checked.

## Install

1. Back up the Prism instance or at least `minecraft/mods` and `minecraft/config`.
2. Remove `meteor-client-26.3-15.jar` from that instance's `mods` folder. Do not leave both Meteor JARs installed.
3. Add `meteor-client-26.3-15-mcopt-compat.1.jar` to the same folder.
4. Keep `mcopt` 0.3.0-alpha.2 installed, and remove `-Dmcopt.metal=false` if it was added as a workaround.
5. Launch once and check F3: its renderer line must say `Metal 3 (mcopt)`.

## Test checklist

1. Open Meteor's GUI and a text field; this is the path that previously crashed.
2. Open nested/scrolling Meteor windows, click settings and type into search/text fields.
3. Enter a single-player world, then a representative server if applicable; open and close the Meteor GUI repeatedly.
4. If it crashes, save `latest.log` and the new crash report before changing any mods.

## Scope and verification

The JAR includes two optional Mixin additions:

* `MetalDeviceMixin` makes mcopt's `mcopt.metal.MetalDevice` implement Meteor's `IGpuDevice` scissor-state interface.
* `MetalEncoderMixin` applies that state when mcopt's `MetalEncoder.createRenderPass` creates a render pass.

`./gradlew clean build -Pbuild_number=15-mcopt-compat.1` completed successfully with Java 25, and the packaged JAR was checked for both new mixin classes. This was not run in a live Apple-Silicon Minecraft session, so it is a test patch rather than a compatibility guarantee.

SHA-256:

`858ec7262c7f9e1f2a1e54ac5aef7e94cfd69a199f21e9cb882003d588a9014d`
