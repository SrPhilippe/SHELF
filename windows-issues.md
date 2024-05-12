# Windows

## Issues with apps when using router WIFI

1. Testing packets
   - Open command prompt (cmd)
   - send a ping to any server using the flags `-f` and `-l <size>`

      ```batch
      ping google.com.br -f -l 1480
      :: where 1480 is the value in bytes

      :: RESPONSE
      Pinging google.com.br [142.250.79.3] with 1480 bytes of data:
      Packet needs to be fragmented but DF set.
      Packet needs to be fragmented but DF set.
      Packet needs to be fragmented but DF set.
      Packet needs to be fragmented but DF set.

      ::Verify interfaces MTU values
      netsh interface ipv4 show subinterfaces
      ::Change the MTU from the interfaces
      netsh interface ipv4 set subinterface <interface_index> mtu=<new_MTU_size> store=persistent
      ```

   - make this test decreasing the bytes size until the replies return TTL.
   - Take the value found and add + `28 bytes` to it (8 from ICMP packets and 20 used by the IP).
2. Change the MTU value (maximum transmission unit)
   - Access your router admin panel.
   - Find the location of MTU configuration - in my case was inside port config.
   - Change the value in bytes accordingdly to the result obtained in the test.



## Windows shortcuts

1. Run **<kbd>WIN</kbd> + <kbd>R</kbd>**

- `shell:system`: Windows sytem32 folder
- `shell:common startup`: Startup programs
- `shell:common programs`: Programs shortcuts
- `shell:control panel folder`: Control Panel
- `shell:fonts`: Windows font manager
- `shell:local appdata`: Local app data
- `shell:screenshots`: Screenshots folder
- `powercfg.cpl`: Power config plan

---

## Windows 10/11 Blurred apps fix

### Method 1: Change Nvidia settings (may solve for all apps)

   1. In **Nvidia Control Panel** set `Antialising - FXAA` to **Off** and hit apply.
   2. If the option above didn't work, you can also try to change the scalling mode to `No Scaling` inside **Adjust desktop size and position** and `perform scaling on` **GPU**. (make sure to mark the checkbox _Override the scalling mode set by games and programs_).

### Method 2: Registry method (may solve for all apps)

   1. Inside Windows Registry Editor navigate to `Computer\HKEY_CURRENT_USER\Control Panel\Desktop`.
   2. Look for `Win8DpiScaling` and change it's value to **1**.
   3.Create a `DWORD32` named **LogPixels** (if it doesn't already exists) and set the `value` to `DECIMAL=120` DEFAULT `DECIMAL=125`.

### Method 3: Individual setting for apps

   1. Right click on the executable file from the application being blurred and go to **properties**.
   2. Navigate to tab **Compability**.
   3. In the Settings section, choose: Change high DPI settings.
   4. Check the box Override high DPI scalling behavior.
   5. Let the scalling be performed by the application.

---

## Autorun file

The name must be `autorun.inf`

```batch
[AutoRun]
icon=exemplo.exe
```

---

## Windows Activation

### (OEM) Original Equipment Manufacturer check

1. Checking

   ```bash
   wmic path softwarelicensingservice get OA3xOriginalProductKey
   ```

2. Activating

   ```bash
   SLUI 3
   ```

### Check and uninstall Windows Product key

1. Checking Product key

   ```batch
   slmgr /dlv
   ```

2. Uninstalling Product key

   ```batch
   slmgr /upk
   ```

---

## Get full ownership on windows

```bash
takeown /F C: /R
```

---

## issue with hard disk windows in 100%

1. Open the command line as administrator
2. Execute the following command `Dism /Online /Cleanup-Image /ScanHealth`
3. Wait as long as it takes, untill the process is finished
4. Execute the following command `Dism /Online /Cleanup-Image /RestoreHealth`
5. Wait until the process is completed and restart the computer

### Disable superfetch service

1. Press **<kbd>WIN</kbd> + <kbd>R</kbd>** and type `services.msc`
2. Locate the `Superfetch` service
3. **right click** and stop it
4. **right click** then **properties**
5. In the dropdown **startup type** select the option: **disabled**

---

## Temporary folders

- `%temp%`
- `temp`
- `prefetch`
- `recent`

---

## Shutdown windows

```bash
shutdown -s -t time
```

> Obs.: Use `-r` instead of `-s` to restart

**time** in seconds

---

## Run the System File Checker tool (SFC.exe)

To do this, follow these steps:

Open an elevated command prompt. To do this, do the following as your appropriate:

If you are running Windows 10, Windows 8.1 or Windows 8, first run the inbox Deployment Image Servicing and Management (DISM) tool prior to running the System File Checker.  (If you are running Windows 7 or Windows Vista, skip to Step 3).

Type the following command, and then press Enter.  It may take several minutes for the command operation to be completed.

```bash
DISM.exe /Online /Cleanup-image /Restorehealth
```

Important: When you run this command, DISM uses Windows Update to provide the files that are required to fix corruptions. However, if your Windows Update client is already broken, use a running Windows installation as the repair source, or use a Windows side-by-side folder from a network share or from a removable media, such as the Windows DVD, as the source of the files. To do this, run the following command instead:

```bash
DISM.exe /Online /Cleanup-Image /RestoreHealth /Source:C:\RepairSource\Windows /LimitAccess
```

Note: Replace the C:\RepairSource\Windows placeholder with the location of your repair source. For more information about using the DISM tool to repair Windows, reference Repair a Windows Image.

At the command prompt, type the following command, and then press ENTER:

```bash
sfc /scannow
```

---

## How to disable Windows Defender on Windows 10/11

1. Disable **real time protection** inside `windows update > windows defender firewall`

2. press **<kbd>WIN</kbd> + <kbd>R</kbd>** and type `gpedit.msc` then hit enter or OK

3. Go to `Administrative Templates\Windows Components\Microsoft Defender  Antivirus`

4. Double click on **Turn off Microsoft Defender Antivirus** and hit OK

5. Now inside the current folder, open the folder **real time protection** and repeat the step 4 but instead, disable **turn  off real-time protection**

`HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`

create a DWORD 32 bits `DisableAntiSpyware` value `1` or `0`

---

## Enabling Ultimate performance in power mode

Run the following command

```bash
powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61
```

---

## Missing open/close laptop lid in power options

1. Add lid close action

   ```bash
   powercfg -attributes SUB_BUTTONS 5ca83367-6e45-459f-a27b-476b1d01c936 -ATTRIB_HIDE
   ```

2. Add lid open action

   ```bash
   powercfg -attributes SUB_BUTTONS 99ff10e7-23b1-4c07-a9d1-5c3206d741b4 -ATTRIB_HIDE
   ```

Otherwise, if you want to remove it you can change the parameter at the end of the code to `+ ATTRIB_HIDE`

---

## MSI AFTERBURNER CONFIG

| Colors Library | R   | G   | B   |
| -------------- | :-: | :-: | :-: |
| Color 0        | 185 | 231 | 0   |
| Color 1        | 224 | 0   | 49  |
| Color 2        | 17  | 175 | 242 |
| Color 3        | 255 | 255 | 255 |
| System Color   | 255 | 255 | 255 |

| Separatos  | Value                                          |
| ---------- | ---------------------------------------------- |
| Prolog     | `<C3><B=0,0>\b`                                |
| Text       | `\n`                                           |
| Group name | `\t`                                           |
| Group data | Separator that you want - In my case **space** |
| Epilog     | `\n<S=100><C4>%Time%     <S=200><FR>FPS`       |

| Group Separator | Value |
| --------------- | ----- |
| Framerate       | `\n`  |
| CPU usage       | `\n`  |

---

## Solve issue with Discord overlay

There is an issue where MSI Afterburner don't let the discord overlay show up inside any game.

1. To solve this, navigate to `C:\Program Files (x86)\RivaTuner Statistics Server\ProfileTemplates`
2. Open the file `GLOBAL`
3. Add the following code under the line that contains `InjectionDelay=15000`

```js
InjectionDelayTriggers=IGO64.dll,IGO32.dll,d3dcompiler_47.dll,DiscordHook.dll,DiscordHook64.dll,GameOverlayRenderer.dll,GameOverlayRenderer64.dll,steam_api64.dll,steam_api.dll,d3d9.dll,dxgi.dll,d3d9_smaa.dll,d3d11.dll,DiscordOverlay.dll,DiscordOverlay64.dll
```

---

## How to  Change Windows boot logo

1. Download this [HackerBGRT](https://github.com/Metabolix/HackBGRT)
2. Create an image with 250x250 resolution and BMP format with a full black background color
   - The image must be 24-bit format named `boot_image.bpm`
3. Execute the `setup` file and press `I` to install
4. A txt file will pop-up, let it open
5. Execute paint with administrator priviledges
6. Open the `.bmp` image you created
7. Click `File > Save as > Select A:/EFI/HackBGRT/`
8. Overwrite the `splash.bmp` image in this folder
9. Close paint and then the cmd terminal

---

### ~~Activating memory cache L2 and L3~~

1. Open CPU-Z and check in the cache tab if you have these 2 sort of memory available

2. open the **regedit** with **<kbd>WIN</kbd> + <kbd>R</kbd>** and type `regedit`

3. locate `Computador\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management`

4. There is a file `SecondLevelDataCache` which by default is disabled. You Can enable it putting your **memory cache L2** value of bytes on it.

5. To activate the **memory cache L3** it needs to create a **DWORD 32** with the name `ThirdLevelDataCache`

[◀◀ Return](readme.md#menu)

---

## ~~Disable hibernate file~~

Not recommended - maybe only when using a good SSD

```bash
powercfg.exe /hibernate off
```

This is going to delete the user file

---

| Navigation                      |
| ------------------------------- |
| [🠝 go top](#windows) |
| [🠜 go back](./readme.md)       |
