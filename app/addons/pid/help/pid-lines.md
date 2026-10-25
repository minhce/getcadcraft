---
title: P&ID: lines and line numbers
summary: Process lines and the four kinds of signal line, how a line number is built, and keeping one number across valves and branches.
section: tasks
order: 20
keywords: line, process line, line number, signal, pneumatic, electric, software, capillary, service, spec, size, sequence, arrow, branch
---

## Drawing a line

Type {{cmd:PIDLINE}} and click the corners; Enter ends. Before the first point, {{ui:Y}} chooses the kind of line, {{ui:V}}, {{ui:Z}} and {{ui:P}} the service, size and spec of a process line, {{ui:A}} the flow arrow, and {{ui:M}} copies the fields of a line you click. A line always starts as a process line; the service, size, spec and arrow are remembered for the next one.

A click near a nozzle, a line end or another line lands on it exactly, so what you draw is connected. A line started on the end of another process line carries on with its number.

| Kind | Looks like | Means |
|---|---|---|
| Process line | heavy continuous line | pipe: carries a line number |
| Pneumatic signal | thin line with slashes across it | air signal |
| Electric signal | dashed | electric signal |
| Software or data link | dotted | link between control functions |
| Capillary tube | dash and dot | filled sensing line |

The signal kinds follow the ideas of ISA-5.1; the drawing is CadCraft's own.

## The line number

A process line's number is built from its fields by a scheme: size, service, sequence and spec joined by dashes (`2"-PW-101-A1A`). A line given a service gets the next free sequence number in that service, from 101. Change the scheme in {{ui:Settings}} › {{ui:CadCraft}} › {{ui:P&ID}}: put the parts in braces, in any order (`{svc}{seq}/{size}` makes `PW101/2"`). Or type the number yourself in {{ui:Properties}}, in {{ui:Line number (typed)}}: it is used as typed.

{{cmd:PIDLN}} sets the service, size and spec of the lines you click; {{ui:N}} gives each a new number.

## Valves, pieces and branches

A line cut by valves is several pieces with one number. The longest piece writes it ({{ui:Write the number on this piece}} in {{ui:Properties}} moves it). The line list counts the pieces as one line, from the first end to the last.

A line that ends on the middle of another line is a branch: the main's row in the line list names it. A line whose number changes where nothing sits between the two is flagged by {{cmd:PIDCHECK}}: put a reducer or a specification break there. A number may change at a valve.
