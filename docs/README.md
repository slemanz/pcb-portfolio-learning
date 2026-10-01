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