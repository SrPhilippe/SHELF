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
