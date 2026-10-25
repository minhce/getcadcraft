---
title: History: versions and what changed
summary: See the versions of a drawing (copies Studio keeps when you save, and the cloud's), open or restore one, and compare two with what changed shown in colour.
section: tasks
order: 135
keywords: history, versions, version history, restore, previous version, undo a save, compare, compare drawings, dwgcompare, changes, added, removed, changed, snapshot, backup, cloud versions
---

## What you will make

A look at an earlier version of a drawing, and a list of what is different from now: what was added, what was removed and what changed, marked in colour on the drawing.

## Open History

Type `HISTORY` (or `HIST`) and press {{key:Enter}}, or choose {{ui:History…}} in the {{ui:More}} menu of the {{ui:View}} group. The panel opens beside the drawing and stays open while you work, so you can pan and zoom the drawing with the colours on it.

History works in CadCraft Studio. In a browser, the panel only says so.

## Where the versions come from

- **On this computer.** Each time you open a drawing from a file in Studio, and each time you save it, Studio keeps a copy of the file in its own storage on this computer. The first copy is {{ui:As opened}}: the file as it was before your first save over it. Studio keeps the newest 25 copies of each drawing, and the oldest go first when all the copies together pass 400 MB. A save that changes nothing keeps nothing. Nothing is uploaded.
- **In the cloud.** When you open a drawing from your cloud files in Studio, the panel also lists {{ui:In the cloud}}: every version the cloud holds, with its number, who saved it and the note. The panel only reads them. CadCraft does not send its own saves to the cloud yet, so these are the versions saved from other devices and the web. Sign in again in Studio if it says the sign-in ran out.

A drawing you have not saved yet has no copies: save it first.

## Open or restore a version

- {{ui:Open}} puts that version in a tab of its own. Your drawing is not touched.
- {{ui:Restore}} replaces this drawing with that version. It asks first. Studio keeps a copy of the drawing as it is now in History (marked {{ui:Before a restore}}) before it does, and nothing is written to the file until you save. A restore cannot be undone with {{key:Mod+Z}}; use that copy.

## Compare

1. Click {{ui:Compare}} on a version. It is compared with {{ui:The drawing as it is now}}; to compare it with another version instead, choose that one in {{ui:Compare with}} first.
2. Read the result under the list: how many objects were added, removed and changed, and a list of them. Click an item in the list to move the view to it.
3. On the drawing:
   - **green** objects were added,
   - **red** objects were removed (they are in the older version only),
   - **orange** objects changed: the new shape is solid and the old one dashed.
4. {{ui:Show on the drawing}} turns the colours off and on; {{ui:Clear the colours}} takes the result away. Closing the panel clears them too.

The list says what changed in a changed object: its text, that it moved, its shape, its layer, colour, linetype or lineweight. Each sheet is compared on its own; the colours show on the sheet that is open.

:::note
A drawing has no lasting number for each object, so CadCraft matches objects by what they are: the same object on both sides is unchanged; an object of the same type and layer that lies within its own size of an old one is the same object, changed; whatever is left is added or removed. An object moved far from where it was shows as removed in one place and added in the other. A block reference counts the content of its block.
:::

## Common mistakes

- **"No copies yet."** Studio keeps a copy at each open and save of a drawing that has a file on this computer. A drawing opened from a browser tab, or never saved, has none.
- **The cloud list is missing.** It appears for a drawing opened from the cloud in Studio; a file opened from the disk is not a cloud drawing.
- **Everything looks changed.** Two versions saved by different programs write the same drawing in different ways (names of anonymous blocks, rounding). Compare versions saved by CadCraft.
