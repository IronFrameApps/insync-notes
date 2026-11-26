# Our boss rigs: what is known (2026-11-26)

- Bosses: samurai-rigged.fbx (black) and whiteboss-rigged.fbx (white), Mixamo skeleton (65 bones, mixamorig:), 1.8 m. 29 Mixamo animation FBX (no mesh) on the same skeleton. Extras with skin: Walking, Standing Death Left 01 (no run yet).
- Mixamo auto-rigging put the ARMS BACKWARDS on the bosses, so the bone positions were fixed by hand in Blender. The rigs we have are the fixed ones.
- In UEFN right now (JP, 2026-11-26): the bosses FACE THE WRONG WAY and SNAP (teleport) between animations.

## Likely causes (to check, not yet confirmed)
1. Facing: the Blender-fixed rigs may face a different axis than the Mixamo animations (Mixamo faces +Z in its own space; Blender faces -Y; UEFN forward is +X, Left-Up-Forward). Check Blender export axes (Forward -Z? Up Y?) and that transforms are applied (rotation 0, scale 1).
2. Snap: Mixamo animations carry root motion (Hips moves). Download animations with "In Place" ticked, or key the boss's position in Sequencer / Verse and keep clips in place.
3. Hand-fixed bones: if bone rest pose or bone roll in the rigged FBX differs from the animation FBX skeleton, animations play twisted. The mesh and animations must share the same rest pose.

## Rule
Test ONE boss with ONE animation (Warrior Idle) first: check facing, arms and snapping, before importing all 29.
