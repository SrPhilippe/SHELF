# Commands

## CMD commands

### Close and open explorer

```batch
:: Opening
 start explorer.exe

:: Closing (kill)
 taskkill /f /im explorer.exe
```

---

## Bash commands

### Open file

```batch
explorer index.html
```

### Move directory

```batch
mv ./other-images/ ./images

:: You don't necessarily need to specify the relative folder
mv other-images images

:: Moving 'hello.txt' to the folder '/awesome/'
mv /example/hello.txt /awesome/
```

### Rename

To rename you can use the same command to [move a directory](#move-directory). You need to supply the same path to the directory but with a different name.

```batch
:: Renaming file
mv main.js index.js

:: Renaming folder
mv awesome superawersome
```

### Copy

```batch
:: Copying file or folder into another folder
cp -r awesome superawesome

:: Copying file content into another file
cp hello.txt hi.txt
```

### Create file

```batch
touch to-do-list.txt
```

### Delete file

```batch
rm to-do-list.txt
```

> Use <kbd>-f</kbd> argument to forcefully delete a file.
> Use <kbd>-r</kbd> argument to recursively delete along with its content.

### Create folder/s

```batch
mkdir foldername
```

> Use <kbd>-p</kbd> argument to create nested directories.

### clear console

```batch
cls
```

[◀◀ Return](readme.md#menu)
