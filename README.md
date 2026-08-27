# 6-DOF-Robot-Arm
A six axis robot arm built around 3D printed cycloidal reducers on NEMA 17 steppers.
Designed in Fusion 360, printed on a Bambu Lab A1.

I study mechanical engineering at Sapienza and this is my own project, outside of coursework.
What I want out of it is a modular arm, meaning every joint is the same kind of assembly:
one stepper, one cycloidal stage, one output flange. Scaling a joint should then be a matter
of changing dimensions, not of redesigning it.

Prototypes that got dropped are kept here together with the reason they were dropped. So far
I have learned more from those than from the ones that worked.

## Status

| | State |
|---|---|
| Cycloidal drive V1 | Printed, assembled, tested. It turns, but it is heavier than it needs to be and the printed ring pins rub. |
| Cycloidal drive V2 | In CAD. The ring pins become M3 screws with a bearing on top, which should turn the sliding contact into a rolling one. |
| J1, base joint | Prototype 1 built with a belt stage, then dropped. See [design log 0001](docs/design-log/0001-j1-belt-driven-base.md). |
| J2 to J6 | Not started. |

## How a joint is built

The same recipe everywhere:

- NEMA 17 stepper, 42 x 42 x 40 mm
- single stage cycloidal reducer, with the ring gear cut directly into the joint housing so
  it is not a separate part
- deep groove ball bearing on the output, 6812 (60 x 78 x 10) on the large joints
- Ø8 shafting and a Ø60 output flange as the interface between one joint and the next
- PLA on a Bambu Lab A1, 20% gyroid infill, speed reduced from the standard profile for
  dimensional accuracy

The parts that take real load are off the shelf: bearings, M3 screws, threaded inserts. The
printed parts mostly hold those in the right place.

## Why cycloidal

I looked at planetary reducers, harmonic drives and off the shelf smart servos first.
Harmonic drives are out of budget. Smart servos would work, but they hide the part of the
problem I actually wanted to work on. A cycloidal stage gives 20:1 or more in a single stage,
takes shock loads better than a printed planetary, and I can print it.

The price is that it is sensitive to print accuracy. Getting V1 to turn smoothly took several
calibration prints for hole and contour compensation before any real part came out usable.

## Repository layout

```
docs/design-log/     one entry per design decision, rejected ones included
cycloidal-drive/     the reducer module, shared by every joint
J1/                  base joint, yaw
```

Each module folder has its own README and a `cad/` folder with STEP files. Anything under
`cad/rejected/` was built or fully modelled and then abandoned.

## Design log

| # | Entry | Joint | Status |
|---|---|---|---|
| [0001](docs/design-log/0001-j1-belt-driven-base.md) | Belt driven J1 base, prototype 1 | J1 | Rejected |

## Licence

CERN-OHL-S v2, see [LICENSE](LICENSE). It is a hardware licence and it is strongly
reciprocal: you can use and modify these designs, but modified versions have to be released
under the same terms.
