# Windows programs annotations

## Adobe softwares

### Fixing popup unlicensed software Adobe Photoshop

Create an inbound and outbound rule that blocks any connection with `photoshop.exe`.

Location: Windows Defender Firewall.

`%ProgramFiles%\Adobe\Adobe Photoshop 2023\Photoshop.exe`

### Fixing INK pressure on Photoshop

1. Go to your ink settings and enable `Windows INK` option.

2. Navigate to `C:\Users\%userprofile$\AppData\Roaming\Adobe\Adobe Photoshop %version%\Adobe Photoshop %version% Settings\`.

3. Create a file named `PSUserConfig.txt`.

4. Now you must open the file you've created and type the following in the first line of the document: `UseSystemStylus 0`.

5. Save the document and open photoshop again.

### Changing the UI accent color on Photoshop

1. Navigate through the directory `C:\Program Files\Adobe\Adobe Photoshop 2023\Required`
2. Locate the file `UIColors.txt` and create a backup of this file `UIColors.bkp`
3. Open the file to change the parameters
4. Find the item you want to customize the color and change the RGB values manually

> Tip: there will be four rows in each item color. Each row corresponds to a predefined theme color into the interface tab inside photoshop preferences.

- Here are a few items that can be listed as the bests to make your interface have an accent color.

| Item                         | Description                                 |
| ---------------------------- | ------------------------------------------- |
| RulerText                    | Numbers on the Horizontal & Vertical Rulers |
| RulerMarkers                 | The lines on the Rulers                     |
| ScrollingListSelectedDefault | Selected layers in the Layers Panel         |
| WidgetButtonStroke           | Button outlines                             |
| WidgetButtonFillPressed      | Pressed buttons                             |
| WidgetPillStrokeFocused      | Buttons on hover outline                    |
| WidgetScrollbarArrows        | Scrollbar arrows                            |
| WidgetScrollbarElevatorFill  | Scrollbar Rectangle                         |

There is also another way to change this color using [this script](content/341-Ui-Color-Picker-by-jazz-y.zip).

It's really simple.

1. Download and extract the script
2. Open with Adobe Photoshop
3. Click "Yes" on the pop-up that will appear
4. Search for the item and change the color
5. Save the file `UIColors.txt` and override it inside the folder shown in the steps above
6. Restart Photoshop

### Better response on Illustrator

1. Press <kbd>ctrl</kbd>+<kbd>K</kbd> and go to the performance tab
2. Enable the option **_Real-time Drawing and Editing_**

## uTorrent

### Hide ADS

Just simply disable these options below:

- `gui.show_plus_upsell`
- `offers.sponsored_torrent_offer_enabled`
- `offers.left_rail_offer_enabled`

### Improve download speed

1. Go into the tab **Bandwidth**
2. Set the option **Global maximum number of connections** to `400`

| Navigation                 |
| -------------------------- |
| [🠝 go top](#adobe) |
| [🠜 go back](../readme.md) |
