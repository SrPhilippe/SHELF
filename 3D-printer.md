# 3D Printer

## Things to know before the purchase

- ~~Glass bed: Durable, easy to use, clean, and sleek~~
- Garolite (G10) bed sheet
- Calibrate E-steps/mm (Extruder steps) or rotation distance in klipper
- The top of the z-axis (threaded rod) is meant to be free-floating, so don't make any upgrades to make it steady
- Good to use silicon spacers for the bed
- Buy good Bed clips
- Reducing the outer shell wall speed in low-cost printers
- Replace the nozzle when it gets worn out
- Add a belt tensioner if it doesn't come stock with them

## Fusion 360

### Main material with a dark theme

1. Press <kbd>A</kbd> to open the appearance tab
2. Go to `plastic > ABS White material`
3. Change the color to `RGB - 160, 160, 160`
4. Change these other parameters: `Roughness - 0.4` `Reflection - 0.060`
5. Favorite this custom material
6. Now overwrite the default material to the one inside the favorites library inside `Preferences > Material > Apply a different appearance > Favorites library > Plastic > ABS (White)`

### Configs

| Tab                        | Name                           | vALUE       |
| :------------------------: | ------------------------------ | :---------: |
| General                    | Reverse Zoom Direction         | TRUE        |
| Material                   | Material Theme                 | Steel Satin |
| Graphics > Display         | High-resolution Canvas Graphic | TRUE        |
| Unit and Value Display     | Material Unit Display          | Metric mmNs |
| Default Units > Design     | Default Units For New Design   | mm          |
| Default Units > Simulation | Default Units                  | Metric (SI) |

### Inner offset to use with bolts

| Offset  | Result                                                               |
| :-----: | -------------------------------------------------------------------- |
| \-0.15  | It fits well but with some wiggle                                    |
| \-0.10  | Recommended                                                          |
| \-0.05  | Usable but it fits a little tight                                    |
| default | it fits tight and will damage the inner thread, should never be used |
