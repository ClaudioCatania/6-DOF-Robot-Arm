# Cycloidal drive

The reducer used at every joint of the arm. V1 is built and running, V2 is in CAD.

## V1 specifications

| Parameter | Value |
|---|---|
| Eccentricity | 1.37 mm |
| Reduction ratio | 1:20 |
| Ring gear pins | 21, 3D printed, integrated into the housing |
| Cycloidal disc thickness | 7 mm |
| Output pin holes | Ø8 mm |

## Bearings

| Quantity | Size | Function |
|---|---|---|
| 2 | 20x32x7 | Shaft to disc |
| 1 | 20x32x7 | Output to rear of the drive |
| 12 | 3x8x4 | Output pins |
| 1 | 60x78x10 | Output to ring gear |

## Fasteners

| Quantity | Item |
|---|---|
| 8 | M3 screws, 35 mm |
| 8 | M3 nuts |
| 6 | M3 screws, 25 mm |
| 12 | M3 threaded inserts |

## Print settings, Bambu Lab A1

- Infill: 20% gyroid. Good compromise between stiffness, weight and taking load from more
  than one direction.
- Speed: reduced from the standard profile, for dimensional accuracy.
- Material: PLA.

Hole and contour compensation on the XY plane were calibrated with test prints before any
real part was printed. Without that step the bearing seats came out too tight to use.

## Design problems I ran into

- **Sizing the main bearing.** The 60x78x10 had to have a bore larger than the circle the
  output pins sit on, otherwise it would run into them.
- **The smaller bearings.** The 20x32x7 and the 3x8x4 were picked after several iterations,
  to fit the disc dimensions I had settled on.
- **Interference fits.** Getting these to hold without splitting the part took several
  prototypes.

## V1 status

- [x] Geometry defined, eccentricity and ratio
- [x] Bearings sized
- [x] Print settings calibrated
- [x] Hole and contour compensation calibrated on test prints
- [x] Parts printed
- [x] Assembled and tested

It turns and it works. Three things are wrong with it:

1. It is heavier than it needs to be.
2. The two discs touch each other slightly.
3. The ring gear pins are printed and rub. This is the real problem: the disc slides against
   the pin instead of rolling on it, and no amount of lubricant fixes a sliding contact.

## V2, in CAD

The main change is the ring pins. Instead of printed posts, each pin becomes an M3 screw
passing right through the housing, with a heat set insert, a 3x8x4 bearing and a printed
spacer on it. The bearing outer race becomes the pin, so the contact turns from sliding to
rolling, and the screw is supported at both ends instead of cantilevered.

The spacers have to touch only the inner race of the bearing, so their outside diameter has to
stay at 5 mm or less. Standard M3 washers are 7 mm across and would press on the outer race
and lock the bearing.

I also changed the number of the theets of the ring gear from 21 to 24 so the reduction ratio in 1:23 and the ring gear can be sealed to the bearing housing with an even number of bolts

Still to do on V2: fillets of 1 to 2 mm on the inside corners of the lightening windows, and
screws with a plain unthreaded shank in the bearing area rather than thread all the way.

## Files

| Path | What it is |
|---|---|
| `cad/CycloidalDriveV1Assembly.f3z` | V1 assembly, Fusion 360 archive |
