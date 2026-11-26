# UEFN rules we learned the hard way (read this first)

Written 2026-11-25 for the Claude Code on the Shadow PC (UEFN MCP) and for Forge chat. Add a line every time something goes wrong.

## Before you do anything
1. Say the plan in a few lines and wait for JP's yes before building or running scripts that write files.
2. Verify facts before stating them. Look it up in uefn-kb/sources (digests, wiki) or in the project. Never invent a class, function or device name.
3. Test ONE small piece first (one object, one animation, one Verse file), look at the result, then do the rest.
4. Back up the level before big changes. Never touch the level, spawn pads or island settings without being asked. Never touch the `circuitcity` folder; new work goes in `circuitcitynative`.
5. Work in stages. Save and read back after every stage. If something fails, stop and report. Do not retry blindly.
6. JP does: Shadow login, Epic login, firewall prompts, Publish. Never press Publish.

## Names and files
- UEFN rejects underscores. Use letters and numbers only in every asset, folder and material name.
- UEFN strips textures from FBX imports and flattens materials. Import PNGs with the texture tools and apply them through a material instance (base colour = the PNG).
- Big merged FBX imports look wrong (triangle limits, white glass, white floor). Build natively piece by piece; import only small low-poly hero models.
- Animations: import with the EXISTING skeleton (do not create a new one). Mixamo rigs use `mixamorig:` bones (65 bones). One skeleton plays all animation files made on it.
- Check a skeletal mesh really has Mixamo bones before importing (single-bone body = static model, cannot animate).
- Flying and hovering are done with Verse, not animations.

## Editor quirks
- Details boxes are Left, Up, Forward (not X, Y, Z).
- Ctrl+S fails while a field has focus: click the toolbar Save icon.
- Scale field: double-click it, Ctrl+A, type the value, Enter, then zoom in to verify.
- Never edit an object you have not confirmed is the selected one (wrong object edited once).

## Shadow PC stream quirks (when a human or Forge types into it)
- Shift is dropped: no capitals, colons, pipes or parentheses. Plain words only.
- First typed characters can be dropped. Click folders instead of typing paths.
- Drag-drop from tools does not work; JP drags files himself. Files get there via a catbox link.
- Opening a pc.shadow.tech tab from Forge's browser tool can kick JP's session. Only do it when JP says so.

## Verse
- Epic's Verse is checked by the compiler. Write small, compile, fix the errors, then continue. Never paste unchecked Verse.
- Real API names live in `sources/uefn/Modules/FortniteGame/**/*.digest.verse` (v44.00). Search there before using any class.
- Verse files are written/compiled through the MCP, or JP pastes them via VS Code.
