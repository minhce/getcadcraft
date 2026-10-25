---
title: P&ID: symbols, tags and equipment
summary: The symbol library and the standards it follows, placing symbols, valves with actuators, in-line items that cut a line, and tags.
section: tasks
order: 10
keywords: symbol, valve, gate, globe, ball, check, butterfly, actuator, pump, vessel, tank, exchanger, instrument, balloon, tag, ISA, ISO, nozzle, connection
---

## The library

{{cmd:PIDSYMBOL}} places any of 52 symbols in five kinds, and a valve can carry any of five actuators.

| Kind | Symbols | Standard idea it follows |
|---|---|---|
| Valves | gate, globe, ball, check, butterfly, plug, needle, diaphragm, angle, three-way, pressure relief, rupture disc | ISO 10628 (symbols for chemical and process engineering diagrams) |
| Actuators | diaphragm, motor, solenoid, piston, hand operated | ISO 10628 |
| Equipment | vertical and horizontal vessel, storage tank, sphere, column, reactor, shell and tube and plate exchanger, air cooler, fired heater, centrifugal and positive displacement pump, compressor, fan, filter, agitator | ISO 10628 |
| Instruments | balloons: field, main panel, local panel, shared display, computer function, programmable logic controller | ISA-5.1 (instrument identification: the balloon and where it is mounted) |
| In-line items | reducer, cap, flange, blind flange, spectacle blind, union, orifice plate, strainer, sight glass, expansion joint, flame arrestor, specification break | ISO 10628; orifice plate ISA-5.1; specification break ISO 14617 |
| Connectors and line ends | off-page connector (to, from), flow arrow, vent, drain, tie-in point | ISO 14617 (symbols for diagrams), ISO 10628 |

Every shape is drawn by CadCraft and dedicated to the public domain (CC0 1.0): use them anywhere. The standards give the idea of a shape (a bow tie for a valve, a circle for a pump, a circle for an instrument); no vendor's symbol library and no standard's own artwork was copied or traced. The tables of letters and shapes in a standard are the standard's: for a drawing that has to follow one, check it against the standard itself.

## Placing symbols

Type {{cmd:PIDSYMBOL}}. {{ui:S}} chooses the symbol (its kind first), {{ui:A}} turns the next symbols, and for a valve {{ui:T}} chooses its actuator. Click to place; Enter ends.

- **Nozzles.** Equipment, valves and instruments have connection points (a pump's suction and discharge, a vessel's top, bottom and sides). A click near a line end or another symbol's connection puts the new symbol's nearest connection exactly there.
- **In-line items cut the line.** A valve, reducer, strainer or other in-line symbol clicked on a process line is turned along the line and cuts it: two pieces, each ending on the symbol. They keep the line number; one piece writes it. {{cmd:UNDO}} puts the line back whole.
- **Valves with actuators** have one more connection, on top of the actuator, where a signal line ends. A check valve, relief valve and rupture disc take no actuator.

## Tags

Equipment, instruments and pressure relief devices need a tag; the checks say so when one is missing.

- **Equipment** is offered the next free tag with a prefix by kind (`P-101` pumps, `T-101` tanks and spheres, `V-101` vessels, `E-101` exchangers, `C-101` columns, `K-101` compressors). Type another to use it.
- **Instruments** ask for letters (`FIC`) and take the next loop number (`FIC-101`), or you type the whole tag. The first letter says what is measured, the letters after it what the instrument does with it: {{cmd:PIDLIST}} reads them out in words (`Flow: indicate, control`). A transmitter and its controller share a loop number.
- **Hand valves and in-line items** are not asked; give them a tag afterwards with {{cmd:PIDTAG}}: click the symbol, type its tag and a description. {{ui:A}} in {{cmd:PIDTAG}} tags every untagged piece of equipment at once, numbered from left to right.

Other facts about an item (service, design pressure and temperature, capacity, material, notes) go in {{ui:Properties}}, and come out in the equipment list.
