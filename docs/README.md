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