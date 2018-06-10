## Common

#### Autorun file
The name must be `autorun.inf`
```batch
[AutoRun]
icon=exemplo.exe
```
[Go back](./../readme.md#menu)
___

#### Get full ownership on windows
```batch
takeown /F C: /R
```

___

#### Activating memory cache L2 and L3

1. Open CPU-Z and check in the cache tab if you have these 2 sort of memory available

2. open the **regedit** <kbd>windows</kbd>**+**<kbd>R</kbd> and type `regedit`

3. locate `Computador\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management`

4. There is a file `SecondLevelDataCache` which by default is disabled. You Can enable it putting your **memory cache L2** value of bytes on it.

5. To activate the **memory cache L3** it needs to create a **DWORD 32** with the name `ThirdLevelDataCache`

___

#### issue with hard disk windows in 100% ##
##### Option 1

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

##### Option 2
> Disabling the superfetch

1. Press <kbd>windows</kbd>**+**<kbd>R</kbd> and type `services.msc`

2. Locates the `Superfetch` service

3. **right click** and stop it

4. **right click** then **properties**

5. In **startup type** select the **disabled** option

___

#### Delete temporary files
1. Locate the folders below by pressing <kbd>windows</kbd>**+**<kbd>R</kbd>

*Do with each one*
- `%temp%`
- `temp`
- `prefetch`
- `recent`

then hit <kbd>ENTER</kbd>

___

#### ShutDown windows

```batch
shutdown -s -t (time)
```

*time in seconds*
