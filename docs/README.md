# Important Notes in PCB Design

## Download LCSC Components

To do this, we need the following lib in python:

```bash
pip install easyeda2kicad
```

With this, to download a component, use:

```bash
easyeda2kicad --full --lcsc_id=C2040 --output ./temp/temp_lib
```
The --full option will download the symbol, footprint and the 3d model. If we
need juts one part we can use --symbol, --footprint or --3d.

## Designators Size

0,8 × 0,8 mm and 0,15 of thickness.

## Copper Zones

- Use **B** to fill or refill all zones.
- Use **Ctrl+B** to remove filled areas in All zones.

## Rules

Define in PCB editor: File -> Board Setup -> Design Rules -> Constraints

### Copper

| **Rule** | **Value** |
|---|---|
| Minimum clearance         | 0.15 mm |
| Minimum track width       | 0.15 mm |
| Minimum connection width  | 0 mm    |
| Minimum annular width     | 0.13 mm |
| Minimum via diameter      | 0.45 mm |
| Copper to hole clearance  | 0.3 mm  |
| Copper to edge clearance  | 0.5 mm  |

### Holes

| **Rule** | **Value** |
|---|---|
| Minimum through hole    | 0.3 mm |
| Hole to hole clearance  | 0.5 mm |

### uVias

| **Rule** | **Value** |
|---|---|
| Minimum uVia diameter | 0.2 mm |
| Minimum uVia hole     | 0.1 mm |

### Silkscreen

| **Rule** | **Value** |
|---|---------|
| Minimum item clearance  | 0.15 mm |
| Minimum text height     | 0.8 mm  |
| Minimum text thickness  | 0.15 mm |

### Others

| **Rule** | **Value** |
|---|---|
| Arc/Circle maximum allowed deviation               | 0.005 mm |
| Allow fillets/chamfers outside zone outline        | Off      |
| Minimum thermal relief spoke count                 | 2        |
| Include stackup height in track length calculations| On       |

## Stackup (4 layers)

Define in PCB editor: File -> Board Setup -> Board Stackup -> Physical Stackup

Based on JLCPCB JLC04161H-7628 (1.6 mm).

| **Layer** | **Type** | **Material** | **Thickness** | **Epsilon R** | **Loss Tan** |
|---|---|---|---|---|---|
| F.Mask       | Mask    | -        | 0.01 mm    | 3.3       | 0        |
| F.Cu         | Copper  | -        | 0.035 mm   | -         | -        |
| Dielectric 1 | PrePreg | FR4      | 0.2104 mm  | 4.5       | 0.02     |
| In1.Cu       | Copper  | -        | 0.0152 mm  | -         | -        |
| Dielectric 2 | Core    | FR4      | 1.065 mm   | 4.5       | 0.02     |
| In2.Cu       | Copper  | -        | 0.0152 mm  | -         | -        |
| Dielectric 3 | PrePreg | FR4      | 0.2104 mm  | 4.5       | 0.02     |
| B.Cu         | Copper  | -        | 0.035 mm   | -         | -        |
| B.Mask       | Mask    | -        | 0.01 mm    | 3.3       | 0        |

Board thickness: 1.6062 mm

## Custom Rules

Define in PCB editor: File -> Board Setup -> Design Rules -> Custom Rules

Allows silk and courtyard overlap between connectors (J*) placed side by side.

```
(rule "Allow silk overlap between J connectors"
    (severity exclusion)
    (constraint silk_clearance)
    (condition "A.memberOfFootprint('J*') && B.memberOfFootprint('J*')"))

(rule "Allow courtyard overlap between J connectors"
    (severity exclusion)
    (constraint courtyard_clearance)
    (condition "A.Reference == 'J*' && B.Reference == 'J*'"))
```
