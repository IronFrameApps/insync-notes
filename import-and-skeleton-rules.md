# Importing rigs and animations into UEFN (skeleton, root, facing)

Pasted by JP 2026-11-25 (source: an AI answer, not copied from Epic; unverified details are marked). Ties to the boss fight: a wrong root or facing makes bosses snap and face the wrong way in Sequencer.

## Before exporting (Blender, Maya, etc.)
- Apply all transforms on mesh and armature: rotation 0, scale 1, position at origin. Unapplied transforms = rigs arrive rotated, tiny or huge.
- Root bone on the ground between the feet, at world origin. UEFN positions the whole character from the root.
- Every character faces the same direction in the 3D program. (Claimed: since 36.00 UEFN turns imported skeletal meshes to face its forward axis; this only works if sources are consistent. Unverified.)
- Same unit scale for every export (both bosses and all animations).
- Blender FBX exporter: turn OFF Add Leaf Bones; turn ON Only Deform Bones if the rig has control/helper bones; use Bake Animation for animations.

## Importing into UEFN
1. Import the MESH first. It creates the Skeletal Mesh and Skeleton assets.
2. Import animations against that EXISTING Skeleton (pick it in the import options; never let UEFN create a new one). A mismatched or duplicate skeleton gives twisted or offset animations.
3. One folder per boss so each rig's skeleton and animations stay together.
4. Check before using in a sequence: open the Skeletal Mesh and click through the Skeleton Tree (bones move the right parts?); open each Animation Sequence and confirm it plays right on the right character.

## Root motion (why bosses "teleport")
Some animations move the root bone through space. If one attack moves the root forward and the next clip starts at the origin, the character snaps back. Either animate attacks IN PLACE (root stays) and move the boss with Transform keys in Sequencer, or make each clip end where the next begins. (Mixamo downloads have an "In Place" option for many animations.)

## Fixing a rig that already imported badly
A few bones out of place: Skeletal Mesh Editor, Skeleton > Edit Skeleton, move bones back, test with Preview Animation. Rotation, scale or root problems: fix the source file and reimport (usually faster).

## Epic docs to check
Import and Play Mesh Animations; Convert a Static Mesh into a Skeletal Mesh (root bones, root motion, fixing bones); Left-Up-Forward Coordinate System.
