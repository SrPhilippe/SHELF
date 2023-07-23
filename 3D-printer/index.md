# 3D Printer

## Things to know before the purchase

- Glass bed: Durable, easy to use, clean, and sleek
- The top of the z-axis (threaded rod) is meant to be free-floating, so don't make any upgrades to make it steady
- Good to use silicon spacers for the bed
- Buy good Bed clips
- Fusion 360
- Reducing the outer shell wall speed in low-cost printers
- Replace the nozzle when it gets worn out
- Add a belt tensioner if it doesn't come stock with them

## Scott Yu-Jan  printer settings

| Name                                   | Value               |
| -------------------------------------- | :-----------------: |
| Generate Support                       | TRUE                |
| Support Structure                      | Tree                |
| Tree Support Branch Angle              | 40                  |
| Tree Support Branch Distance           | 0.6mm               |
| Tree Supoort Branch Diameter           | 2mm                 |
| Tree Supoort Branch Diameter Angle     | 5                   |
| Tree Collision Resolution              | 0.2mm               |
| Support Placement                      | Touching buildplate |
| Support Overhang Angle                 | 50                  |
| Support Pattern                        | Zig Zag             |
| Support Wall Line Count                | 1                   |
| Connect Support ZigZags                | TRUE                |
| Support Density                        | 0%                  |
| Suport Line Distance                   | 0mm                 |
| Intial Layer Support Line Distance     | 0mm                 |
| Enable Support Brim                    | TRUE                |
| Support Brim Width                     | 4mm                 |
| Support Brim Line Count                | 10                  |
| Support Z Distance                     | 0mm                 |
| Support Top Distance                   | 0mm                 |
| Support X/Y Distance                   | 0.5mm               |
| Support Distance Priority              | Z overrides X/Y     |
| Minimum Support X/Y Distance           | 0.3mm               |
| Support Stair Step Height              | 0.3mm               |
| Support Stair Step Maximum Width       | 5.0mm               |
| Support Stair Step Minimum Slope Angle | 10.0                |
| Enable Support Interface               | TRUE                |
| Enable Support  Roof                   | TRUE                |
| Enable Support Floor                   | TRUE                |
| Support Interface Thickness            | 1.6mm               |
| Support Roof Thickness                 | 1.6mm               |
| Support Floor Thickness                | 1.6mm               |
| Support Interface Resolution           | 0.2mm               |
| Support Interface Density              | 33.333%             |
| Support Roof Density                   | 50%                 |
| Support Roof Line Distance             | 1.6mm               |
| Support Floor Density                  | 33.333%             |
| Support Floor Line Distance            | 2.4mm               |
| Support Interface Pattern              | Grid                |

## Fusion 360

### Main material with a dark theme

1. Press <kbd>A</kbd> to open the appearance tab
2. Go to `plastic > ABS White material`
3. Change the color to `RGB - 160, 160, 160`
4. Change these other parameters: `Roughness - 0.4` `Reflection - 0.060`
5. Favorite this custom material
6. Now overwrite the default material to the one inside the favorites library inside `Preferences > Material > Apply a different appearance > Favorites library > Plastic > ABS (White)`

### Configs

| Tab                        | Name                           | vALUE                      |
| :------------------------: | ------------------------------ | :------------------------: |
| General                    | Reverse Zoom Direction         | TRUE                       |
| Material                   | Material Theme                 | Stainless steel - Polished |
| Graphics > Display         | High-resolution Canvas Graphic | TRUE                       |
| Unit and Value Display     | Material Unit Display          | Metric mmNs                |
| Default Units > Design     | Default Units For New Design   | mm                         |
| Default Units > Simulation | Default Units                  | Metric (SI)                |

### Inner offset to use with bolts

| Offset  | Result                                                               |
| :-----: | -------------------------------------------------------------------- |
| \-0.15  | It fits well but with some wiggle                                    |
| \-0.10  | Recommended                                                          |
| \-0.05  | Usable but it fits a little tight                                    |
| default | it fits tight and will damage the inner thread, should never be used |
