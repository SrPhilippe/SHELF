# 3D Printer

Add Anti-backlash Nut - This is meant for the lead screw z axis

## Power supply / Sizes

- Input supply: 115-230 V 50-60 Hz (bivolt)
- Output supply: 24 V 15 A (360 W)
- Dimensions: 475x445x515mm
- Weight: 8,3 Kg
- Machine power: 360 W
- SN: NEP 4 23710.A0197
- 1.2A current version

## Calibration

### Flow Rate formula

`( flowRatio_old * (100 + modifier) / 100)`

Default `0.98`

### Max Volumetric Speed

`start + (height-measured * step)`

## Fusion 360

### Main material with a dark theme

1. Press <kbd>A</kbd> to open the appearance tab
2. Go to `plastic > ABS White material`
3. Change the color to `RGB - 160, 160, 160`
4. Change these other parameters: `Roughness - 0.4` `Reflection - 0.060`
5. Favorite this custom material
6. Now overwrite the default material to the one inside the favorites library inside `Preferences > Material > Apply a different appearance > Favorites library > Plastic > ABS (White)`

### Configs

| Tab                        | Name                           | Value       |
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

## Materials settings

| Material     | Brand   | Temperature | Color        | Flow Ratio | PA    | Max VA |
| ------------ | ------- | :---------: | ------------ | :--------: | :---: | :----: |
| Basic PLA    | 3D Fila | 220         | Branco Gesso | 0,957      | 0,033 | 17     |
| PLA EasyFill | 3D Fila | 205         | Blue         | 0.995      | 0.028 | -      |

## Slicer settings

### Orca

#### G-code start/end

##### START G-CODE

```gcode
RESPOND TYPE=command MSG="ORCA START G-CODE"

; -- Turn the lights on
FLASHLIGHT_ON
MODLELIGHT_ON

G90 ; use absolute coordinates
RESPOND MSG="ABSOLUTE CORDINATES"
M83 ; extruder relative mode
RESPOND MSG="EXTRUDE RELATIVE MODE"

; -- Origin position
G1 X2 Y10 Z50 F3000
RESPOND MSG="ORIGIN POSITION"

M104 S120 ; set temporary nozzle temp to prevent oozing during homing and auto bed leveling
M140 S[bed_temperature_initial_layer] ; set final bed temp
G4 S10 ; allow partial nozzle warmup
RESPOND MSG="WARM-UP THINGS"

BED_MESH_CLEAR
BED_MESH_PROFILE LOAD=6
RESPOND TYPE=command MSG="BED_MESH LOADED"

M190 S[bed_temperature_initial_layer_single] ; wait for bed temp to stabilize

G28 ; home axis
RESPOND MSG="HOMING"

M104 S[nozzle_temperature_initial_layer] ; set final nozzle temp

; -- Origin position
G1 Z5 F300
G1 X2 Y10 F3000
G1 Z50 F300

RESPOND MSG="Origin Pos"

M109 S[nozzle_temperature_initial_layer] ; wait for nozzle temp to stabilize

; -- Prime filament
RESPOND TYPE=command MSG="Priming the Nozzle"
G1 Z0.28 F240
G92 E0
G1 Y140 E10 F1500 ; prime the nozzle
G1 X2.3 F5000
G92 E0
G1 Y10 E10 F1200 ; prime the nozzle
G92 E0

RESPOND TYPE=command MSG="Printing"
```

##### END G-CODE

```gcode
{if max_layer_z < printable_height}G1 Z{z_offset+min(max_layer_z+2, printable_height)} F600 ; Move print head up{endif}
G1 X5 Y{print_bed_max[1]*0.8} F{travel_speed*60} ; present print
{if max_layer_z < printable_height-10}G1 Z{z_offset+min(max_layer_z+70, printable_height-10)} F600 ; Move print head further up{endif}
{if max_layer_z < printable_height*0.6}G1 Z{printable_height*0.6} F600 ; Move print head further up{endif}
M140 S0 ; turn off heatbed
M104 S0 ; turn off temperature
M107 ; turn off fan
M84 X Y E ; disable motors
```

#### Global Processes

##### Elegoo default speed

| Parameter             | Value    |
| --------------------- | :------: |
| First layer           | 60 mm/s  |
| First layer infill    | 80 mm/s  |
| Outer wall            | 130 mm/s |
| Inner wall            | 150 mm/s |
| Sparse infill         | 200 mm/s |
| Internal solid infill | 150 mm/s |
| Gap infill            | 80 mm/s  |
| Support               | 60 mm/s  |

#### Bridging with ABS my configs

| Parameter             | Value   |
| --------------------- | :-----: |
| External Bridge speed | 15 mm/s |
| Internal Bridge speed | 15 mm/s |
| Bridge flow           | 0.78    |
| Thick bridges         | Enabled |

##### Filename format

```json
{input_filename_base}-{print_time}-{layer_height}mm-{filament_type[0]}.gcode
// OR
{input_filename_base}-{print_time}-{total_weight}g-{layer_height}mm-{filament_type[0]}
```

---

## Printer config (printer.cfg)

### Screw Tilt Adjust

```gcode
#####################################################################
# Screw tilt adjust / Bed screws
#####################################################################

[screws_tilt_adjust]
# Gives the palpation values on the bed and indicates the changes to be made           
screw1: 54.00, 10.50
screw1_name: front left screw
screw2: 223.50, 10.50
screw2_name: front right screw
screw3: 223.50, 180.50
screw3_name: rear right screw
screw4: 54.00, 180.50
screw4_name: rear left screw
horizontal_move_z: 10.0
speed: 150.0
screw_thread: CW-M4

[bed_screws]
# Place the nozzle at the screws to make manual adjustments
screw1: 32.5, 32.5
screw1_name: front left screw
screw2: 202.5, 32.5
screw2_name: front right screw
screw3: 202.5, 202.5
screw3_name: rear right screw
screw4: 32.5, 202.5
screw4_name: rear left screw
horizontal_move_z: 10.0
speed: 150.0
```

## Others

### SSH Login

```batch
:: Default user
user: mks
password: makerbase

:: User with admin priviledges
user: root
password: makerbase
```

1. INTALL PSCP from Putty download files
2. Place the file in your user folder `%userprofile%`
3. Open CMD and get inside the user profile folder cd %userprofile%
4. execute this command `pscp -P 22 root@10.0.0.133:/home/mks/klipper_config/printer.cfg newfilename.cfg`

Another great software is WINSCP.

---

### Fixing moonraker paths

1. `cd ./moonraker`
2. `git pull`
3. `./scripts/data-path-fix.sh`

---

### SSH Through Vscode

1. Install *Remote - SSH* extension
2. <kbd>Ctrl</kbd> **+** <kbd>Shift</kbd> **+** <kbd>P</kbd> > *Add a new SSH HOST*
3. Type: `ssh mks@10.0.0.133`

`<username>@<host_or_printer_ip_address>`

It's going to popup a screen asking for password and the connection will be made.

---

### Klipper Flash MCU

- In this case, there's no `STM32F402` inside MCU, so use `STM32F401` instead.

```txt
####################################################################################
# This product (Neptune 4/4pro/4plus/4max) adopts Klipper firmware 
# and does not support users to update the official klipper/fluidd
# /moonraker by themselves, otherwise the machine will not work properly.
# If you want to DIY and are an expert or interested in this field, 
# we recommend that you prepare your own tools for burning images so 
# that you can restore them if problems arise. Please contact after-sales 
# support team for tutorials on burning images. Thank you for your cooperation!
####################################################################################
# This file contains common pin mappings for ZNP-K1-V1.0 
# boards. To use this config, the firmware should be compiled for the
# STM32F402. When running "make menuconfig", enable "extra low-level
# configuration setup", select the 32KiB bootloader, and serial (on
# USART1 PA10/PA9) communication.

# The "make flash" command does not work on the ZN-K1-V1.0. Instead,
# after running "make", copy the generated "out/klipper.bin" file to a
# file named "elegoo_k1.bin" on an SD card and then restart the ZNP-K1-V1.0
# with that SD card.
```

---

### (Fixing Error upload to print host)

If the gcode is too big and `object_processing` is enabled, the request can take more than 1 minute which is the default timeout for nginx. To change it, edit `/etc/nginx/nginx.conf` and add the following code inside http section but place it at the end:

```conf
http {
  ...
  ...
  ...

  proxy_send_timeout 500s;
  proxy_read_timeout 500s;
  fastcgi_send_timeout 500s;
  fastcgi_read_timeout 500s;
}
```

---

### Change timezone

Login into armbian using SCP and Mks user

```bash
sudo armbian-config
```

1. Go to `personal > Timezone`
2. Select your timezone
3. exit

---

### Elegoo compress files to install

`tar -cvf extra_update etc/ home/`

---

### Klipper Adaptive Meshing Purging

1. You will need `[exclude_object]` defined in *printer.cfg*.

2. You will also need to make sure the following is defined in *moonraker.conf*:

```json
[file_manager]
enable_object_processing: True
```

---

### Backup EMMC files

You can backup using an EMMC adapter connected to your computer and [Win32 Disk Imager](https://win32diskimager.org/).

1. > It won't launch if Google drive is opened

> This software has a launching issue when the computer has a mounted drive on the system like Google Drive. So in order to fix you can simply close GDrive application.
