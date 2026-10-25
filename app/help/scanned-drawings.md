---
title: Scanned drawings and the trace
summary: Bring in a scanned sheet, scale and square it, clean it up, erase parts of it, snap to its lines and trace it into lines and arcs.
section: tasks
order: 136
keywords: scan, scanned drawing, raster, tiff, jpeg, png, scale, align, deskew, despeckle, threshold, black and white, crop, erase, trace, vectorize, snap, arcs, hatching, paper drawings, old drawings, scanattach, scantrace
---

## From a paper sheet to drawing objects

A scanned drawing is a picture. CadCraft keeps the picture you gave it and never changes it: each clean-up step makes a new picture, one undo step each, and {{cmd:SCANINFO}} lists the original file and the steps taken since. Nothing is sent anywhere and nothing is guessed by a trained model: the clean-up and the trace are ordinary image processing, and they run on your computer.

1. **Insert it.** {{cmd:SCANATTACH}} reads a PNG, a JPEG, a TIFF (one page, or all the pages of a multi-page file) or a PDF page that is a picture. It asks for the page, the lower-left corner and the width. For a PDF page it also asks how many pixels per inch to draw the page at.
2. **Scale it.** {{cmd:SCANSCALE}}: pick two points on the scan, then type the true distance between them. The sheet is scaled about the first point.
3. **Align it.** {{cmd:SCANALIGN}}: pick two points on the scan and the two places they belong; the sheet moves and turns to fit, and scales too unless you answer No.
4. **Square it.** {{cmd:SCANDESKEW}} measures the angle the sheet's long lines lie at and shows it, with how sure it is. Accept it, or type your own, and the sheet is turned. A sheet with few long lines gets a warning: check the angle before you accept it.
5. **Clean it.** {{cmd:SCANCLEAN}} makes the sheet black and white (Auto evens out the paper first; Adaptive follows the paper's changes more closely; Level is one number for the whole sheet) and removes specks up to the size you set.
6. **Crop and erase.** {{cmd:SCANCROP}} keeps a window. {{cmd:SCANERASE}} erases a rectangle, a polygon or a lasso (press and drag): stamps, notes, a coffee ring.

The cleaned picture is what a saved DWG holds (an IMAGE and its IMAGEDEF, with the picture's file beside the drawing, as for any picture).

## Snap to the scan's lines

With {{cmd:RASTERSNAP}} on (the default), object snaps also find the lines of a black-and-white scan: the ends of lines, their middles, corners and crossings, shown with the usual snap marks. The part of the sheet under the pointer is traced as you move; zoom in enough that a pixel is a few screen pixels. A line longer than the part being traced is followed to its ends.

## The trace

{{cmd:SCANTRACE}} turns the lines of the sheet into lines and arcs on a new layer (SCAN-TRACE), as one undo step, with the scan still under them. You set:

- **Tolerance:** how far a traced line or arc may lie from the lines on the scan, in drawing units (the report also gives pixels). A tight tolerance follows every wobble; a loose one makes fewer, straighter pieces.
- **Window:** a corner of the sheet, or the whole sheet.
- **Arcs:** off makes lines only.
- **Leftovers:** what the trace left alone is drawn as boxes on a layer you can switch off, or not drawn.

The trace finds the centre of each stroke, follows it, fits straight lines and circular arcs to it, joins runs that were cut where another line crossed, makes nearly level and nearly plumb lines exactly level and plumb, and closes corners. **Text and hatching stay as raster:** pieces the size of lettering are set aside, and bundles of short parallel lines are taken for hatching and set aside.

When it finishes it says how many lines and arcs it made, the tolerance, and how many pieces it left as raster. **That is what the pixels gave, to that tolerance, and it is not a claim that the result is right.** Compare it with the sheet: a trace can miss a faint line, join two lines that lie very close, or draw a line where there is only a stain. Clean the scan first (squared, black and white, specks gone) and the result is much better.

## What it does not read

TIFF files stored in tiles, BigTIFF, TIFF with JPEG or deflate compression, Group 3 fax coding and colours kept in separate planes are refused with a message; save them again as strips with LZW, PackBits, Group 4 or no compression. Interlaced PNG files are refused too. Files over 128 MB or 100 million pixels are refused, and a trace window can hold at most 64 million pixels.
