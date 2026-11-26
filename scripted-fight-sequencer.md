# Scripted boss fight (Level Sequence + Cinematic Sequence device)

Pasted by JP 2026-11-25 (source: an AI answer, not copied from Epic; the doc names at the bottom are Epic pages to read). Use for the white boss vs black boss fight.

## Symptom / likely cause / fix
| Symptom | Likely cause | Fix |
|---|---|---|
| Bosses out of sync | Each boss is in its own sequence or device, so they start at slightly different times | Put BOTH bosses in ONE Level Sequence played by ONE Cinematic Sequence device (shared timeline) |
| Boss snaps to a different spot at the start | No Transform key at frame 0, so it starts from where it was placed in the level | Playhead at 0000, set a Transform keyframe on each boss at its start position and rotation |
| Boss teleports between attacks | Some attack animations move the character; the next clip starts and the boss snaps back to its actor | Key the boss's Transform track so it moves with each clip; overlap clips slightly so Sequencer blends |
| Boss spins or faces wrong way | Rotation keys cross 0/360 (350 to 10), so it turns the long way | Keep rotation continuous (use 370 instead of 10); add more rotation keys between big turns |
| Boss pops back to start when the fight ends | Finish Completion State Override restores the original state | Set it to Force Keep State |
| Players see bosses appear or vanish at distance | Playback only sent to nearby players | Turn on Level Sequence Actor Always Relevant on the device |

Also: trigger the device ONLY ONCE. Triggering it again while it plays restarts the sequence, and the bosses look like they teleport.

## AI bosses (NPC or Guard spawners)
AI characters choose their own movement and targets, so two AI bosses will not stay in choreographed sync. Set fight = Level Sequence. Real fight = accept that positions vary.

## Epic docs to read for this
- Cinematic Sequence Device
- Sequencer and Control Rig
- Skeletal Animation
- Animation 101 Template
- Import and Play Mesh Animations
