# J1, base joint

J1 is the base. It rotates about a vertical axis and carries the whole arm above it.

Because the axis is vertical, gravity produces no torque about J1. The motor only has to
beat inertia and friction. What the base does have to survive is the overturning moment of
the arm hanging out to one side, but that is a load on the output bearing and on the housing,
not on the motor. Mixing up those two is how prototype 1 ended up geared at 80:1, which is
about ten times what the joint needs.

## Current state

Prototype 1 is built and rejected. A GT2 belt stage at 4:1 sat upstream of a 20:1 cycloidal
stage, with the motor beside the axis instead of under it. The full reasoning is in
[design log 0001](../docs/design-log/0001-j1-belt-driven-base.md).

What survives from it: the housing doubling as the cycloidal ring gear, the 6812 output
bearing, the Ø115 housing and the Ø60 output flange.

The coaxial revision is not designed yet, and the ratio for it is still open. See the open
questions at the end of entry 0001.

## Files

| Path | What it is |
|---|---|
| [`cad/rejected/j1-belt-base-v1/PrototipoBase1.step`](cad/rejected/j1-belt-base-v1/PrototipoBase1.step) | prototype 1, as built |
