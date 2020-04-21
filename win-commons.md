# Windows solutions

### Autorun file
The name must be `autorun.inf`
```batch
[AutoRun]
icon=exemplo.exe
```

---

### Disable windows defender

1. Run `gpedit.msc` command in **_run window_**
2. Go to **_administrative templates > Windows Components > Windows Defender Antivirus_**
3. Go to folder **_Real-time Protection_** and enable **_Turn off real-time protection_**
---

### Get full ownership on windows
```batch
takeown /F C: /R
```

---

### Activating memory cache L2 and L3

1. Open CPU-Z and check in the cache tab if you have these 2 sort of memory available

2. open the **regedit** <kbd>windows</kbd>**+**<kbd>R</kbd> and type `regedit`

3. locate `Computador\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management`

4. There is a file `SecondLevelDataCache` which by default is disabled. You Can enable it putting your **memory cache L2** value of bytes on it.

5. To activate the **memory cache L3** it needs to create a **DWORD 32** with the name `ThirdLevelDataCache`

[◀◀ Return](readme.md#menu)

---

### issue with hard disk windows in 100%
#### Option 1

1. Open up the command line as administrator

2. Execute the following command
```batch
Dism /Online /Cleanup-Image /ScanHealth
```

*(wait as long as it takes)*

3. then execute the command below
```batch
Dism /Online /Cleanup-Image /RestoreHealth
```

4. When it's done, restart your computer

#### Option 2
> Disabling the superfetch

1. Press <kbd>windows</kbd>**+**<kbd>R</kbd> and type `services.msc`

2. Locates the `Superfetch` service

3. **right click** and stop it

4. **right click** then **properties**

5. In **startup type** select the **disabled** option

---

### Delete temporary files
1. Locate the folders below by pressing <kbd>windows</kbd>**+**<kbd>R</kbd>

*Do with each one*
- `%temp%`
- `temp`
- `prefetch`
- `recent`

then hit <kbd>ENTER</kbd>

---

### ShutDown windows

```batch
shutdown -s -t (time)
```
> Obs.: Use `-r` instead of `-s` to restart

*time in seconds*

---

### How to turn off windows defender in windows 10

1. Disable **real time protection** on windows update > windows defender firewall.

2. press <kbd>window</kbd>**+**<kbd>R</kbd> and type `gpedit.msc`, then hit enter or OK.

3. Go to `Computer configuration\Administrative Templates\Windows Components\Windows Defender Antivirus`

4. Double click on **Turn off Windows Defender Antivirus** and hit OK.

[◀◀ Return](readme.md)