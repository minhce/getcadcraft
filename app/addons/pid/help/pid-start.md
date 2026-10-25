---
title: P&ID: getting started
summary: What the P&ID add-on does in CadCraft, how to switch it on, and how a diagram is kept in an ordinary DWG or DXF file.
section: start
order: 1
keywords: p&id, pid, process, instrumentation, diagram, piping and instrumentation, tag, line number, instrument, equipment, line list, add-on
---

## What it is

P&ID is an add-on for CadCraft that comes with it and is free. It draws process and instrumentation diagrams: equipment, valves, instruments and the lines between them, with a tag on each item and a number on each line. From the finished drawing it makes the lists a diagram is read for (line list, equipment list, instrument index, valve list) and checks the drawing for the mistakes that are easy to miss.

It is off until you switch it on: {{ui:Settings}} › {{ui:General}} › {{ui:Add-ons}} › {{ui:P&ID}}. Its tools are in the {{ui:P&ID}} section of the right panel, as commands (below), and, when you ask for it in {{ui:Settings}} › {{ui:CadCraft}} › {{ui:P&ID}}, as a group at the end of the toolbar.

**A drafting aid, not an engineering approval.** The symbols are drawn by CadCraft after the common ideas of the standards named in "P&ID: symbols, tags and equipment"; the line numbers, tags and checks follow the usual habits of these diagrams, not any company's or standard's rules. A person who is responsible for the plant still decides what the diagram has to say.

## Your first diagram

1. Type {{cmd:PIDSYMBOL}}, type {{ui:S}} to choose a symbol (first its kind, then the symbol), and click where it goes. Equipment asks for its tag; the next free one is offered (`P-101`, `T-101`).
2. Type {{cmd:PIDLINE}}, type {{ui:V}}, {{ui:Z}} and {{ui:P}} for the service, size and spec (`PW`, `2"`, `A1A`), and click the corners of a process line. Start and finish on a nozzle: the click lands on it.
3. Put a valve on the line: {{cmd:PIDSYMBOL}}, a valve, and click on the line. The line is cut either side of the valve.
4. Place an instrument, type its letters (`FIC`) and it takes the next loop number (`FIC-101`). Draw a signal line to it: {{cmd:PIDLINE}}, {{ui:Y}} for a signal style.
5. Type {{cmd:PIDCHECK}} and go to each finding. Type {{cmd:PIDLIST}} and click where a list goes on the sheet.

## Files open anywhere

A symbol, a line and a list on the sheet are each saved as a block reference with its drawing inside, and its data kept with it under the application name `CC_PID`. A diagram saved as DWG or DXF opens in any CAD program as drawn, and in CadCraft without the add-on with nothing lost.

Connections are never stored: CadCraft works them out from where things touch, so moving a pump with {{cmd:MOVE}} keeps the diagram true.

## Units

Symbols are 4 in (100 mm in a metric drawing) by default; change it in {{ui:Settings}} › {{ui:CadCraft}} › {{ui:P&ID}}. Sizes in line numbers are text: type what your drawings say (`2"`, `DN50`).
