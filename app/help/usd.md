---
title: Export the 3D model as USD
summary: Write the 3D tab's solids as USD for rendering programs and other 3D software.
section: tasks
order: 140
keywords: usd, usda, usdc, usdz, openusd, export, 3d, solids, usdout, export3d
---

The 3D tab's solids can be written as USD.

- Type {{cmd:USDOUT}} and choose `.usda` (text), `.usdc` (binary) or `.usdz` (one package file), or
- type {{cmd:EXPORT3D}} and choose {{ui:USD}} for a `.usdz` package.

Each solid becomes one object with its faces as a mesh and its colour as a material, in metres with Z up. A solid used several times is written once and placed where each copy is.
