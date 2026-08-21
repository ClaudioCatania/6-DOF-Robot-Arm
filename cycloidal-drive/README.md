# Cycloidal Drive V1

Cycloidal reducer designed for the 6DoF robotic arm.

## Specifications

| Parameter | Value |
|---|---|
| Eccentricity | 1.37 mm |
| Reduction ratio | 1:20 |
| Ring gear pins | 21 (3D printed, integrated into the housing) |
| Cycloidal disc thickness | 7 mm |
| Output pin holes | Ø8 mm |

## Bearings

| Quantity | Size | Function |
|---|---|---|
| 2 | 20x32x7 | Shaft–disc connection |
| 1 | 20x32x7 | Output–rear of cycloidal drive connection |
| 12 | 3x8x4 | Output pins |
| 1 | 60x78x10 | Output–ring gear connection |

## Fasteners

| Quantity | Item |
|---|---|
| 8 | M3 screws, 35mm |
| 8 | M3 nuts |

## Print settings (Bambu Lab A1)

- **Infill:** 20%, gyroid pattern — good compromise between stiffness/weight and multi-directional load resistance
- **Speed:** reduced from standard, for better dimensional accuracy
- **Material:** PLA

## Design challenges

- **Bearing sizing:** the 60x78x10 bearing needed a diameter larger than the circumference on which the output pins are placed, otherwise it would interfere with them. The 20x32x7 and 3x8x4 bearings were selected after multiple iterations to best match the chosen disc dimensions.
- **Interference-fit connections:** connecting these components with interference fits proved tricky and required building several prototypes to get right.

## Project status

- [x] Geometric parameters defined (eccentricity, reduction ratio)
- [x] Bearing sizing finalized
- [x] Print settings calibrated
- [x] XY Hole/Contour Compensation calibration via test prints
- [x] Functional parts printing
- [x] Assembly and testing

## Notes
Altough the current version still has some problems:
Excessive weight,
Slight contact between the two disks,
Power losses caused by friction at the 3D-printed pins.
I’m still satysfied with the result and will soon release a second version with with a lighter design and add some oil to the pins to reduce friction
