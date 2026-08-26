# Modular 6-DOF Robotic Arm

An open, fully modular 6-DOF robotic arm for pick-and-place and general domestic use, built
around **3D-printed cycloidal drives on NEMA 17 steppers**. Designed in Fusion 360.

This is a personal engineering project: I am a mechanical engineering undergraduate at
Sapienza, and the goal is as much to document the reasoning as to build the hardware.
Prototypes that get rejected are kept here, with the reasoning that killed them — that part
is usually more useful than the part that worked.

## Design goals

| | |
|---|---|
| Purpose | Pick and place, domestic use |
| Degrees of freedom | 6 |
| Joints | Cycloidal drives, one NEMA 17 per joint |
| Architecture | Fully modular — every joint is the same kind of thing |
| Manufacturing | 3D printing + off-the-shelf bearings and fasteners |

## Repository layout

```
cad/                     STEP files
  rejected/              prototypes that were not carried forward
docs/
  design-log/            why each design decision was made — and unmade
```

## Design log

The design log records each significant decision, including the rejected ones, with the
numbers behind it.

| # | Entry | Status |
|---|---|---|
| [0001](docs/design-log/0001-j1-belt-driven-base.md) | Belt-driven J1 base (prototype 1) | **Rejected** — belt tension loads the cycloidal input shaft, the height saving does not pay for the footprint, and 23:1 in one stage removes the need for the belt |

## Current state

- **J1** — belt-driven base prototype built and rejected (see entry 0001). Next revision:
  coaxial NEMA 17 with a 24-pin / 23-lobe cycloidal stage at 23:1, Ø115 housing, 6812 output
  bearing.
- **J2–J6** — not started.

## Licence

Not yet chosen. Until one is added here, treat the contents as "all rights reserved" and get
in touch if you want to reuse them.
