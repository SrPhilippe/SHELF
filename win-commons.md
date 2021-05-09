# Windows solutions

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

## Disable windows defender

1. Run `gpedit.msc` command in **_run window_**
2. Go to **_administrative templates > Windows Components > Windows Defender Antivirus_**
3. Go to folder **_Real-time Protection_** and enable **_Turn off real-time protection_**

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

### How to turn off windows defender in windows 10

1. Disable **real time protection** on windows update > windows defender firewall.

2. press <kbd>window</kbd>**+**<kbd>R</kbd> and type `gpedit.msc`, then hit enter or OK.

3. Go to `Computer configuration\Administrative Templates\Windows Components\Windows Defender Antivirus`

4. Double click on **Turn off Windows Defender Antivirus** and hit OK.

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

[◀◀ Return](readme.md)
