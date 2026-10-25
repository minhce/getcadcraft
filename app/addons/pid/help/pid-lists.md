---
title: P&ID: lists on the sheet, CSV and XLSX
summary: The line list, equipment list, instrument index and valve list: on the sheet as tables that stay current, and out as one workbook or a CSV.
section: tasks
order: 30
keywords: list, line list, equipment list, instrument index, valve list, table, export, csv, xlsx, spreadsheet
---

## The four lists

| List | One row per | Columns |
|---|---|---|
| Line list | line number | size, service, spec, insulation, from, to, branches |
| Equipment list | piece of equipment | tag, type, description, service, design pressure, design temperature, capacity, material, nozzles used, connected lines, notes |
| Instrument index | instrument | tag, function in words, loop, mounting, service, description, what it is connected to |
| Valve list | valve and tagged in-line item | tag, type, actuator, line, service, description, notes |

From and To follow the line through valves and in-line items to the equipment, instrument or connector at each end (`T-101 (right)`, `P-101 (suction)`); an end that joins nothing says so.

## On the sheet

Type {{cmd:PIDLIST}}, choose a list and click the table's top-left corner. The table is an object: it follows the drawing, so tagging a pump, drawing a line or erasing a valve changes its rows in the same undo step. Text height is in {{ui:Settings}} › {{ui:CadCraft}} › {{ui:P&ID}}.

## Out as a file

Type {{cmd:EXPORT}} and choose **P&ID lists (XLSX workbook)**: one worksheet per list, a bold header row, text throughout. Or **P&ID lists (CSV)**: every list in one file, each under its name. A cell that starts with `=`, `+`, `-` or `@` is written as text, never as a formula.
