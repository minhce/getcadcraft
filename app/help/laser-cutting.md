---
title: Send a drawing to a laser
summary: Open the Laser panel, choose what each layer does (cut, score, engrave, fill, picture), preview the head's moves, save GRBL laser-mode G-code, or send it from the browser after framing the job.
section: tasks
order: 137
keywords: laser, laser cutter, laser engraver, GRBL, G-code, gcode, engrave, fill, dither, picture engraving, score, cut, Web Serial, frame the job, power, speed, passes, LASER, LASERCUT, CNC
---

The {{ui:Laser}} panel turns the layers of a drawing into a program for a laser that runs GRBL (most hobby and small-shop diode and CO2 controllers). Type `LASER` (or `LASERCUT`) and press {{key:Enter}}, or choose {{ui:Laser…}} in the {{ui:More}} menu of the {{ui:View}} group. In the ribbon styles it is in the {{ui:File}} menu and beside {{ui:Plot}}. The panel opens over the drawing and stays open while you draw: the preview follows every change.

:::warning
Test every setting on scrap first, wear eye protection that fits your laser, keep the lid closed where there is one, and never leave a running laser alone. The numbers a layer starts with are placeholders, not recommendations for any material.
:::

## What is sent

The panel reads the model (not the sheets), on layers that are on and thawed:

- Lines, arcs, circles, polylines (arc segments stay arcs), ellipses and splines. A shape that ends where it starts counts as closed.
- Blocks are taken apart: an object on layer 0 inside a block goes with the layer of the block reference.
- A hatch sends its boundary, so a hatched logo on a **Fill** layer is filled.
- A picture (`IMAGEATTACH`) is engraved on a layer set to **Engrave picture**, when it lies square (not turned or slanted) and its file is open in CadCraft.
- Text, dimensions, leaders, points and construction lines are not sent; the panel says how many it left out. To burn text, draw the letters as shapes or hatch them.

Sizes go out in millimetres from the drawing's units (`UNITS`): a drawing in inches is multiplied by 25.4. A drawing with no units set is sent one unit to one millimetre. Tick {{ui:Only the selected objects}} to send part of the drawing.

## Choose what each layer does

Every layer with something on it is a row. {{ui:Does}} sets it to **Cut**, **Score**, **Engrave lines**, **Fill shapes**, **Engrave picture** or **Not sent**, with a {{ui:Power %}}, a {{ui:Speed mm/min}} and a number of {{ui:Passes}}. Each change is one undo step and is saved in the drawing: DWG (every version CadCraft saves) and DXF keep the settings, so the drawing opens with them next time. Other programs open the file as before; they see one unused block named CADCRAFT_LASER (purging it there removes the settings).

- **Fill** burns the inside of closed shapes in lines, {{ui:Line spacing}} apart, at an {{ui:Angle}}, both directions or one, with an overscan so the head is at speed when the laser comes on; cross-hatch adds a second pass at 90°. A shape with a hole stays open at the hole.
- **Engrave picture** turns a picture into dots (Floyd–Steinberg, Atkinson, ordered, or plain black and white at a threshold) or, with *Grey levels*, into variable power.
- Order: pictures and fills first, then line engraving, then scores, then cuts, so a cut-out part does not move while it is engraved. Within one layer the paths run **inside-first** (a hole before the plate it is in), nearest next.

## Preview, then save

The preview draws what the head does: burning lines in colour, fast moves in grey, and a green box round everything that burns. Below it are the size, the length of burn and a time estimate (without acceleration; a real machine takes longer). {{ui:Save G-code…}} writes GRBL laser-mode G-code: `$32=1`, `M4` (or `M3`) with S values, `G0` and `G1` moves, `M5` at the end. X0 Y0 is the job's lower left corner unless you choose the drawing's origin: set your machine's work zero there.

## Send from the browser

In Chrome and Edge, {{ui:Connect…}} asks you to choose the laser's USB port. Nothing connects or sends until you press a button. Press {{ui:Frame the job}} first: the head traces the box of the job with the laser **off** (or at the low power you set for a pointer) so you can see where it will burn. Only then does {{ui:Send job}} come on, and it goes off again if you change anything. {{ui:Pause}} holds the head, {{ui:Stop}} holds it, resets the controller (the laser goes off) and sends `M5`. Where Web Serial is missing (Firefox, Safari, and CadCraft Studio, which has no Web Serial yet) the panel offers saving only: save the G-code and send it with your laser's own program.

## Not built yet

Not built yet: other controllers' formats (Ruida, Marlin lasers, vendor files), tabs and lead-ins, kerf offset, material libraries, rotary and Z axes, camera alignment, text as outlines.
