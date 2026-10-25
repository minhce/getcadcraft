---
title: Splines and polylines: SPLINE, SPLINEDIT, PEDIT
summary: Draw a smooth curve through points or from a control polygon, edit its fit and control points, and edit polylines (join, close, width, fit, spline, decurve) or turn a spline into a polyline.
section: tasks
order: 55
keywords: spline, splinedit, spl, spe, pedit, pe, fit points, control points, weights, nurbs, polyline edit, join, fit curve, decurve, convert to polyline, precision, tangent, curve, fit tolerance
---

## What you will make

A curve through five points, then the same curve edited three ways, and a polyline built from three lines.

## Draw a spline through points

1. Type `SPL` and press {{key:Enter}}.
2. Click or type the points the curve should pass through: `0,0`, `100,80`, `200,-30`, `350,50`, `500,0`. Press {{key:Enter}} after the last one.
3. {{ui:Start tangent}}: click a point the curve should leave towards, or press {{key:Enter}} to let it decide. Do the same for the end tangent.

The curve passes through every point. Type `C` instead of {{key:Enter}} to close it (the curve comes back to the first point). {{key:U}} (`Undo`) takes the last point back while you are drawing.

### Draw one from a control polygon

Type `M` at the first prompt, then `C` (Control vertices) and a degree from 1 to 5 (3 is the usual). Now the points you pick are the corners of a polygon that pulls the curve towards them; the curve starts on the first and ends on the last. A closed one wraps round, with no corner at the join.

### Turn a polyline into a spline

At the first prompt type `O` (Object) and select polylines or lines. They become splines through their vertices; the originals go.

## Edit a spline

Select it and type `SPE` (or type `SPE` and click it). Grips show the fit points (or the control points of a spline that has none): drag one to reshape the curve. At the prompt:

- **Fit data** (a spline drawn through points): `A` adds a fit point (click where), `D` deletes one (click near it), `M` moves one (click near it, then click its new place), `T` sets the end tangents, `P` purges the fit points, so the spline is edited by its control points from then on.
- **Edit vertex**: `A` adds a control point without changing the curve, `M` moves one, `W` gives one a **weight** (above 1 pulls the curve closer to it, below 1 lets it go).
- **Open** or **Close**, and **Reverse** (the curve runs the other way).
- **convert to Polyline** (`P`): the spline becomes a polyline; the precision is how many segments each span gets (10 is the usual).
- **Undo** takes the last change back; **eXit** ends.

{{ui:Properties}} shows a spline's degree, how many fit and control points it has, its length, and lets you open or close it.

## Edit a polyline

Select a polyline and type `PE`. A line, an arc or a spline you pick is first offered as a polyline to turn into (a spline asks for the precision).

- **Close** / **Open** joins or separates the ends.
- **Join** adds lines, arcs and polylines whose ends meet the polyline's end. `Fuzz distance` is how far apart ends may be and still join (0 means they must meet).
- **Width** gives the whole polyline one width (0 removes it).
- **Fit** replaces the polyline by a smooth curve that passes through its vertices; **Spline** by a cubic B-spline that follows them (it starts and ends at the first and last vertex and stays near the others). Both become a polyline of short segments, and the original corners are kept, so **Decurve** brings them back.
- **Ltype gen** says whether a dashed linetype runs on along the whole polyline or starts again at each vertex.
- **Reverse** changes the order of its vertices. **Multiple** (`M` at the first prompt) edits several polylines with the same options.

Editing the vertices of a polyline in {{ui:Properties}} or with grips stays as it was: PEDIT has no vertex editor.

## In files

DWG and DXF 2000 keep a spline as a spline: degree, control points, knots, weights, fit points and tangents. A spline you open and don't change is written back exactly as it came. DXF R12 has no spline: it is saved as a polyline along the curve, and the history says how many.

Offset, trim, extend, fillet, break and join do not work on splines. {{cmd:EXPLODE}} a spline, or {{cmd:PEDIT}} it, to get a polyline those commands take.

## Common mistakes

- **The curve overshoots between close points.** A curve through points bends where the points do. Use fewer points, or a control polygon.
- **"That is not a spline."** SPLINEDIT only takes splines; {{cmd:PEDIT}} edits polylines.
- **A closed fit spline has a slightly different shape in another program.** CadCraft closes it with one smooth join at the first point; another program may close it with a periodic curve. A closed control-point spline is the same in both.
