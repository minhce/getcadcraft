---
title: PDF underlays and PDF import
summary: Put a PDF page under your drawing to trace and plot it, or turn the page's lines and text into drawing objects.
section: tasks
order: 135
keywords: pdf, pdfattach, pdfimport, pdfclip, pdfadjust, pdflayers, underlay, trace, import pdf, scan, floor plan, fade, clip, layers, snap, open pdf
---

## Two ways to bring in a PDF page

- **Attach** ({{cmd:PDFATTACH}}) keeps the PDF as a picture under your drawing. You trace it, snap to its lines, fade it, clip it, and it prints with the sheet. The drawing keeps only the file's name.
- **Import** ({{cmd:PDFIMPORT}}) turns the page's lines, curves, fills and text into ordinary drawing objects, on layers named after the PDF. They are yours to edit, and the PDF is not needed afterwards.

Opening a PDF with {{ui:Open}} asks which of the two you want.

## Attach a page

1. Type `PDFATTACH` (or `PDFATT`) and choose the PDF. If it has several pages, type the page number.
2. Click the insertion point (the page's lower-left corner).
3. Press {{key:Enter}} for the page's true size, or type the scale: drawing units per PDF point (a point is 1/72 inch, so 0.3528 in a millimetre drawing).
4. Press {{key:Enter}} for no turn, or type an angle.

The page is an object like a block reference: move, rotate, scale, copy, erase and put it on a layer. Switch its layer off and it disappears. Zoom in and the page is drawn again sharply.

## Trace it

With {{ui:Snap}} on, the cursor snaps to the PDF's own lines: end points, midpoints and crossings (and {{ui:Nearest}} when that snap is on). Text drawn as letters on the page is not snapped to.

## Adjust it

- `PDFADJUST`: **Fade** (0 to 80 percent), **Contrast** (0 to 100), **Monochrome**, and **Onoff** to hide it without erasing it.
- `PDFCLIP`: show only a rectangle or polygon of the page; **Delete** removes the clip.
- `PDFLAYERS`: a PDF can have its own layers. The command lists them; type a number to switch that layer on or off for this underlay. The layers the file has off start off.

## Plot and save

PLOT prints the page as its lines, fills and text (so it stays sharp and searchable). Pictures inside the PDF are shown on screen but are not printed yet.

A DWG or DXF 2000 keeps the underlay as a link: the file's name, the page, where it lies, its scale, turn, clip, fade and contrast. The PDF itself is not in the drawing. Reopen the drawing, type `PDF` and pick the file again; the pages are shown as frames until you do, and take their true size when you do. Older DXF (R12) has no underlays: it keeps the frame and the name. How other programs read the saved clip and scale has not been checked in them yet.

## Import a page

1. Type `PDFIMPORT` (or `PDFIM`) and choose the PDF and page.
2. Click where the page's lower-left corner goes.
3. Press {{key:Enter}} for true size, type a scale, or choose **Two points**: the page is drawn at true size, then you click two points of a distance you know and type the real distance; everything is scaled to match.

Lines become lines and polylines, circles and arcs are recognised, filled shapes become solid hatches, and text becomes text on a layer ending in `-TEXT`. It is one undo step. Pictures in the PDF are not imported: attach the page instead. A scan (a page that is only a picture) has no lines to import.

PDFs are read as untrusted files: no scripts run, and a very large page is cut short and said so.
