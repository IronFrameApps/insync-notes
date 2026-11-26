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

## Blender check results (2026-11-26, read-only)
- Facing: both boss rigs and all Mixamo animation files share the same layout (armature rot 90, scale 0.01, toes toward -Y in Blender, hands 0.69 m out in T-pose). Rig and animations MATCH, so the wrong facing in UEFN comes from UEFN's import axis. Fix by rotating the boss (test on one boss).
- Snap cause CONFIRMED, root motion (hips travel in metres): Shoulder Throw 4.7, Hurricane Kick 3.7, Flying Bicycle Kick 2.4, Flying Kick-3 2.4, Chapa-Giratoria 2.1, Punch To Elbow Combo-2 1.9, Hell Slammer A 1.7, Dodging 1.0, Fist Fight A 1.0. Re-download these from Mixamo with In Place ticked.
- Already in place (zero drift, safe): Warrior Idle, Taunt, Body Block, Boxing x4, Elbow Punch x2, Headbutt, Jumping, Knee Jab, Martelo 2, Pontera, Punching x2, Reaction-2, Receive Punch, Receive Uppercut, Standing Taunt Battlecry-2.
- Walking.fbx (with skin) is HALF SIZE (hips 0.51 m vs 1.05 m on the others). Do not use; re-download a walk and a run, In Place.
- Test plan: one boss, Warrior Idle only; report facing and snapping before importing the rest.
