# Pocketbook Era Button Remap
Remapping both physical buttons on Pocketbook Era to turn the page forward in KOReader.

The following instructions will allow the user to change the default physical button configuration when using KOReader on Pocketbook Era. The configuration persists after an online update, but needs to be repeated if the update server is down and a manual update is performed by replacing old KOReader files with new ones.

1. Connect the ereader to a PC and choose `PC Link` in the prompt on the device.
2. On the PC, navigate to the following path: `applications\koreader\frontend\device\pocketbook\`.
3. Open the file `device.lua` in a text editor.
4. Find the following text block:
   ```self.input = require("device/input"):new{
        device = self,
        raw_input = raw_input,
        event_map = setmetatable({
            [C.KEY_HOME] = "Home",
            [C.KEY_MENU] = "Menu",
            [C.KEY_PREV] = "LPgBack",
            [C.KEY_NEXT] = "LPgFwd",
            [C.KEY_UP] = "Up",
            [C.KEY_DOWN] = "Down",
            [C.KEY_LEFT] = "Left",
            [C.KEY_RIGHT] = "Right",
            [C.KEY_OK] = "Press",
        }, {__index=raw_input and raw_input.keymap or {}}),
5. Change `[C.KEY_PREV] = "LPgBack"` to `[C.KEY_PREV] = "LPgFwd"`.
6. Scroll down and find the following text block:
   ```-- PocketBook InkPad 3 Pro (740_2)
    local PocketBook740_2 = PocketBook:extend{
    model = "PBInkPad3Pro",
    display_dpi = 300,
    isAlwaysPortrait = yes,
    usingForcedRotation = landscape_ccw,
    hasNaturalLight = yes,
    raw_input = {
        touch_rotation = -1,
        keymap = {
            [115] = "Menu",
            [109] = "LPgFwd",
            [104] = "LPgBack",         
7. Change `[104] = "LPgBack"` to `[104] = "LPgFwd"`.
8. Save the changes and close the file.
9. Safely eject the device from the PC and relaunch KOReader; the new configuration should not require a device reboot.
