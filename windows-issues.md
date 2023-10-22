# Windows solutions

## Windows shortcuts

### Run <kbd>Windows</kbd> **+** <kbd>R</kbd>

- `shell:system`: Windows sytem32 folder
- `shell:common startup`: Startup programs
- `shell:common programs`: Programs shortcuts
- `shell:control panel folder`: Control Panel
- `shell:fonts`: Windows font manager
- `shell:local appadta`: Local app data
- `shell:screenshots`: Screenshots folder
- `powercfg.cpl`: Power config plan

---

## Autorun file

The name must be `autorun.inf`

```batch
[AutoRun]
icon=exemplo.exe
```

---

## (OEM) Original Equipment Manufacturer check

### Checking

```batch
wmic path softwarelicensingservice get OA3xOriginalProductKey
```

### Activation

```batch
SLUI 3
```

## Check and uninstall Windows Product key

### Checking Product key

```batch
slmgr /dlv
```

### Uninstalling Product key

```batch
slmgr /upk
```

---

## Get full ownership on windows

```batch
takeown /F C: /R
```

---

### ~~Activating memory cache L2 and L3~~

1. Open CPU-Z and check in the cache tab if you have these 2 sort of memory available

2. open the **regedit** <kbd>windows</kbd>**+**<kbd>R</kbd> and type `regedit`

3. locate `Computador\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management`

4. There is a file `SecondLevelDataCache` which by default is disabled. You Can enable it putting your **memory cache L2** value of bytes on it.

5. To activate the **memory cache L3** it needs to create a **DWORD 32** with the name `ThirdLevelDataCache`

[◀◀ Return](readme.md#menu)

---

## issue with hard disk windows in 100%

### Option 1

1. Open up the command line as administrator
2. Execute the following command `Dism /Online /Cleanup-Image /ScanHealth`
3. (wait as long as it takes)
4. then execute the following command `Dism /Online /Cleanup-Image /RestoreHealth`
5. When it's done, restart your computer

### Option 2

#### Disabling the superfetch

1. Press <kbd>windows</kbd>**+**<kbd>R</kbd> and type `services.msc`
2. Locates the `Superfetch` service
3. **right click** and stop it
4. **right click** then **properties**
5. In **startup type** select the **disabled** option

---

### Delete temporary files

1. Locate the folders below by pressing <kbd>windows</kbd>**+**<kbd>R</kbd>

Do with each one

- `%temp%`
- `temp`
- `prefetch`
- `recent`

then hit <kbd>ENTER</kbd>

---

## ShutDown windows

```batch
shutdown -s -t (time)
```

> Obs.: Use `-r` instead of `-s` to restart

time in seconds

---

### How to turn off windows defender in windows 10/11

1. Disable **real time protection** on windows update > windows defender firewall.

2. press <kbd>window</kbd>**+**<kbd>R</kbd> and type `gpedit.msc`, then hit enter or OK.

3. Go to `Administrative Templates\Windows Components\Microsoft Defender  Antivirus`

4. Double click on **Turn off Microsoft Defender Antivirus** and hit OK.

5. Now inside the current folder, open the folder **real time protection** and repeat the step 4 but instead, disable **turn  off real-time protection**.

`HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`

create a DWORD 32 bits `DisableAntiSpyware` value `1` or `0`

---

### Enabling Ultimate performance in power mode

Just run this command on CMD

```bash
powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61
```

---

## Missing open/close laptop lid in power options

### Add lid close action

```bash
powercfg -attributes SUB_BUTTONS 5ca83367-6e45-459f-a27b-476b1d01c936 -ATTRIB_HIDE
```

### Add lid open action

```bash
powercfg -attributes SUB_BUTTONS 99ff10e7-23b1-4c07-a9d1-5c3206d741b4 -ATTRIB_HIDE
```

Otherwise, if you want to remove it you can change the parameter at the end of the code to `+ ATTRIB_HIDE`

## Deactivate hibernate file

Only for those who owns an ssd

```bash
powercfg.exe /hibernate off
```

It will delete the user file

## MSI AFTERBURNER CONFIG

Colors Library | R | G | B
---------------|:-:|:-:|:-:
Color 0        |185|231|0
Color 1        |224|0  |49
Color 2        |17 |175|242
Color 3        |255|255|255
System Color   |255|255|255

Separatos | Value
----------|:-----
Prolog    |`<C3><B=0,0>\b`
Text      |`\n`
Group name|`\t`
Group data|Separator that you want - In my case **space**
Epilog    |`\n<S=100><C4>%Time%     <S=200><FR>FPS`

Group Separator | Value
----------------|:-----
Framerate       |`\n`
CPU usage       |`\n`

---

### Solve issue with discord overlay

There is an issue where MSI Afterburner don't let the discord overlay show up in the game. To solve this, you'll need to put the code bellow under the line `InjectionDelay=15000` inside `GLOBAL` file at `C:\Program Files (x86)\RivaTuner Statistics Server\ProfileTemplates`

```bash

InjectionDelayTriggers=IGO64.dll,IGO32.dll,d3dcompiler_47.dll,DiscordHook.dll,DiscordHook64.dll,GameOverlayRenderer.dll,GameOverlayRenderer64.dll,steam_api64.dll,steam_api.dll,d3d9.dll,dxgi.dll,d3d9_smaa.dll,d3d11.dll,DiscordOverlay.dll,DiscordOverlay64.dll

```

## Changing Windows boot logo

1. Download this [HackerBGRT](https://github.com/Metabolix/HackBGRT)
2. Create an image with 250x250 resolution and BMP format with a full black background color
   - The image must be 24-bit format named `boot_image.bpm`
3. Execute the `setup` file and press `I` to install
4. A txt file will pop-up, let it open
5. Execute paint with administrator priviledges
6. Open the `.bmp` image you created
7. Click `File > Save as > Select A:/EFI/HackBGRT/`
8. Overwrite the `splash.bmp` image in this folder
9.  Close paint and then the cmd terminal

| Navigation                 |
| -------------------------- |
| [🠝 go top](#windows-solutions) |
| [🠜 go back](../readme.md) |