# 0001 — Belt driven J1 base, prototype 1

**Status:** rejected
**Date:** 2026-08-26
**Joint:** J1, base yaw
**CAD:** [`J1/cad/rejected/j1-belt-base-v1/PrototipoBase1.step`](../../J1/cad/rejected/j1-belt-base-v1/PrototipoBase1.step)

## Summary

The first base prototype drove J1 with a GT2 belt stage (20T to 80T, 4:1) upstream of a
21 pin cycloidal stage (20:1), so 80:1 overall. The motor sat 81.93 mm to the side of the
axis so that its 40 mm body did not stack under the reducer.

I dropped it because the belt can lose position with nothing watching, because its tension
permanently loads the one shaft that carries the cycloidal eccentric, and because the height
it saves costs more in footprint than it is worth. 80:1 also turned out to be far more
reduction than J1 needs.

![Annotated view of the rejected prototype](images/j1-belt-base-annotated.png)

## What was built

Measured from the CAD assembly:

| Item | Value |
|---|---|
| Motor | NEMA 17, 42 x 42 x 40 mm |
| Belt stage | GT2, 20T to 80T, 11 mm tooth face |
| Pitch diameters | 12.73 mm / 50.93 mm |
| Centre distance | 81.93 mm, fixed, no tensioner modelled |
| Belt length needed | 268.3 mm, 134 teeth |
| Cycloidal stage | 21 ring pins Ø8 on a Ø80 pitch circle, 20 lobe disc, 20:1 |
| Main bearing | 6812, 60 x 78 x 10 mm |
| Output | Ø60 flange, 8 mm shaft interface |
| Overall ratio | 4 x 20 = 80:1 |
| Envelope | 161.9 x 115.0 x 67.0 mm, motor included |

The motor hangs shaft down at X = -81.93 mm with its 20T pulley at the bottom of the base.
The 80T pulley sits on the cycloidal input shaft, on the J1 axis. The cycloidal ring is cut
into the base housing itself and the 6812 carries the output flange at the top.

![Power path, rejected vs coaxial](images/j1-power-path.svg)

## Why it was rejected

**The belt can lose position and nothing would see it.** Pulley clearance itself is not the
issue: it sits upstream of the reducer, so 0.05 to 0.1 mm of belt travel is only 0.02 to
0.05° at the output. The issue is that both pulleys are printed, and a printed 80T GT2 pulley
has real pitch error and runout that repeats once per input revolution and goes straight
through the cycloidal stage. It also drifts, since tension falls as the printed bracket creeps
and moves with temperature. And with the step count taken at the motor, everything downstream
is open loop, so a skipped tooth is a permanent 0.9° error at J1 that never comes back.

**Belt tension loads the shaft that must not deflect.** A NEMA 17 at 0.40 N·m with a 20T
pulley (pitch radius 6.37 mm) gives about 63 N of tangential force. Belts are tensioned at
roughly 1.0 to 1.5 times that and the two spans add on the shaft, so both pulley shafts carry
95 to 125 N of standing radial load whether the joint moves or not. On the driven side that
shaft carries the cycloidal eccentric, and the mesh is defined by the eccentricity, so any
deflection there adds to it directly and changes which lobes touch. The steel shaft barely
moves, about 0.01 mm for Ø8 over a 20 mm overhang, but it sits in printed bearing seats and
PLA creeps under a load that never goes away. That is the worst load case for printed plastic,
and here it exists only to keep a belt tight.

**The height saving costs more than it saves.**

| | Belt version, built | Coaxial NEMA 17, estimate |
|---|---|---|
| Height, base plate to output face | 67 mm | about 88 mm |
| Footprint | 162 x 115 mm | Ø115 mm |
| Extra parts | 2 pulleys, belt, input shaft, 2 bearings | none |

The belt buys about 21 mm, and it buys it below the J1 flange, which is pedestal height and
can be recessed into whatever the arm is bolted to. What it adds is 47 mm sideways, at the
level where J1's own link sweeps. Trading a round base for a lopsided one to save pedestal
height is the wrong way round. There is also no tensioner in the model: the centre distance is
fixed, which pins the belt at 268.3 mm, not a stock closed loop length in most GT2 ranges, and
leaves no way to re-tension it once the printed parts creep.

**It breaks the modularity rule.** Every other joint is meant to be a cycloidal drive on a
NEMA 17. A belt gives J1 its own power path, bracket, failure mode and spare part.

## The ratio was wrong too

J1 turns about a vertical axis, so gravity produces no torque about it and the ratio is not
set by a holding load. It is bounded below by the torque needed to accelerate the arm and
above by the output speed the motor can still deliver.

These are estimates, not measurements. Links 1 to 3 do not exist yet, so the load inertia is a
guess for a 2.0 kg arm with a 0.5 kg payload at 0.40 m. Usable motor torque 0.24 N·m (0.6 of
0.40 N·m holding), assumed stage efficiency 0.75, target 90 °/s reached in 0.30 s, useful
motor speed 600 rpm at 24 V.

```
T_acc = 0.125 kg·m² x 5.24 rad/s²   = 0.65 N·m
T_req = 0.65 + 0.50 friction        = 1.15 N·m
i_min = 1.15 / (0.24 x 0.75)        = 6.4
i_max = 600 rpm / 15 rpm            = 40
```

Anything between roughly 6.4 and 40 works. The 20:1 stage alone gives 3.60 N·m against
1.15 N·m needed, a safety factor of 3.1, and 180 °/s. The belt pushes it to 80:1, which is
14.4 N·m and 45 °/s. Nothing on this arm needs 14 N·m about a vertical axis, and halving the
slew speed to get it is a bad trade.

Where 80:1 does win is inertia matching. At 20:1 the reflected load inertia is about 58 times
the rotor, which is high, and the stepper will feel it during hard ramps. I am accepting that
on purpose: it can be handled with S curve ramps, by keeping the arm light, and by closing the
loop on J1 later if it turns out to matter. It is a tuning problem, and a belt is a mechanical
one.

## Decision

- Drop the belt stage, mount the NEMA 17 coaxially under the cycloidal drive.
- Keep the 6812 output bearing, the Ø60 output flange, the Ø115 housing and the
  housing-as-ring-gear idea. Those parts of prototype 1 were right.
- Ratio of the coaxial version not decided yet, see below.

## Open question: how many ring pins

A single disc cycloidal drive with N ring pins and an N-1 lobe disc gives a ratio of N-1, so
the ratio is chosen by picking the pin count, and the pin count is limited by how much
material is left between pins.

| Pins on Ø80 | Ratio | Pin spacing | Web between Ø8 pins |
|---|---|---|---|
| 21, built | 20:1 | 11.97 mm | 3.97 mm |
| 24 | 23:1 | 10.47 mm | 2.47 mm, too thin |

24 pins would only fit with the pins at Ø6 instead of Ø8. That looks free on the drawing but
it is not, because from V2 the pin is no longer printed: it is an M3 screw with a 3x8x4
bearing on it, and the outer race of that bearing is the pin. Ø6 means a 3x6x2.5 bearing, so
contact width drops from 4 mm to 2.5 mm and every pin carries less. Adding three pins while
weakening all of them, to gain 15% of a ratio that already has a safety factor of 3.1, is not
obviously worth it. Leaning towards 21 pins and 20:1, which also reuses the discs and the
3x8x4 bearings I already have. Not decided.

## Other open points

- [ ] Check the load inertia on the real arm once links 1 to 3 exist. The ratio rests on it.
- [ ] Measure the real efficiency of the printed cycloidal stage. 0.75 is a guess.
- [ ] Decide whether J1 gets an output side encoder before committing to open loop.
