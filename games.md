# Games configs and more

## Rocksmith 2014 Edition

I got problems when I launched the game. The sound was chopping and the game window was always minimized, even when I tried to maximize it.

### Solution

1 - Open the `.ini` file inside the game directory folder `\Steam\steamapps\common\Rocksmith2014`

2 - Set the screen resolution in the `ScreenWidth` and `ScreenHeight` parameter

3 - Set `Win32UltraLowLatencyMode` to **0** if you got audio problems.

> For more information visit [this article](https://www.ubisoft.com/en-us/help/rocksmith-2014-edition-remastered/connectivity-and-performance/article/having-sound-issues-in-rocksmith-2014/000063924)

___

## Rocksmith 2014 [ASIO support](https://github.com/mdias/rs_asio)

1 - Download [last release](https://github.com/mdias/rs_asio/releases/latest) of the RS Asio on github provided by [mdias](https://github.com/mdias)

2 - Make sure `Rocksmith.ini` file has both options `ExclusiveMode` and `Win32UltraLowLatencyMode` setted to **1**

3 - Place the files from **RS_ASIO** inside Rocksmith directory

4 - Run Rocksmith once _- This will create `RS_ASIO-log.txt` file inside the game directory

5 - Open `RS_ASIO-log.txt` and search for a line containing `AsioHelpers::FindDrivers` header. It will show you bellow the list of ASIO drivers you have

```txt
0.365 [INFO]  AsioHelpers::FindDrivers
0.366 [INFO]    Voicemeeter AUX Virtual ASIO
0.366 [INFO]    Voicemeeter Insert Virtual ASIO
0.366 [INFO]    Voicemeeter Virtual ASIO
```

In my case, I'm using Voicemeeter to control my audio interface, so I'm using Voicemeeter Virtual ASIO.

**Important:** you should copy the text related to your Asio driver in this block of text.

6 - Open `RS_ASIO.ini` file inside the game directory and paste your Asio driver name right after `Driver=` line.

**Important:** You have to assign the input and output drivers in this text file.

In my case, I used `[Asio.output]` assigned to `Voicemeeter Virtual ASIO` and `[Asio.input.0]` assigned to `Voicemeeter Virtual ASIO`

Now you're almost done.

It's important to remember that when we talk about stuff related to an external instrument connected to your computer, the sound will always have some delay. The most bufferSize you have settled to your device the longest time it will take the sound to come out of the speakers.

To reduce the delay we should find the lowest bufferSize value until the sound start to strike.

my buffer size inside Voicemeter ASIO Driver: 224

___

## Cyber hunter config

This is a piece of code from the `config` file inside the folder's directory.
It will give us better graphics and a higher FPS.

```ini
[graphic_setting]
graphic_quality = 4
display_mode_pc = 1
fps_level_pc = 4
graphic_quality_show = 4
graphic_hdr = -1
```

___

## Minecraft

- GD Launcher
- ATLauncher
- SKLauncher (Pirate Version)

Some of the config files are located inside [this folder](./minecraft/)

In order to have a better performance in this game, I recommend using Fabric Loader with a rendering API called SODIUM, which improves your FPS on a HUGE scale.

### Mods

All of the mods are available to download on [Modrinth](https://modrinth.com/).

- ~~Forge Library~~ *USE FABRIC LOADER INSTEAD*
- ~~Optifine~~ *USE IRIS SHADERS INSTEAD*
- Fabric Loader
- Iris Shaders
- Sodium
- Journey map
- Just Enough Items

### Resource pack

- [Faithfull](https://faithfulpack.net/downloads)
- Stay True
- [Legendary](https://legendaryrttextures.com/download/)
- [Redstone Utilities](https://faithfulpack.net/addons/redstone-utilities)

### Server

You may encounter issues when running a minecraft java server. If so, please consider to install [Java JDK Development Kit](https://www.oracle.com/java/technologies/downloads/).

___

## Best ASCII arts

```ascii
⣿⣿⣿⣿⣿⣿⣿⣿⣿⡿⠻⠋⠭⣭⠻⠟⠻⠿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⠇⠄⠄⠁⠨⢰⠤⡐⡘⡙⠻⠟⠛⠻⡿⣷⣜⡛⣻⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⡇⠈⠄⠄⠄⠈⣀⣨⣤⣥⣦⣦⣤⡂⠱⡞⢸⣿⣿⣟⣻⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⢻⣿⡇⠂⠄⡀⠄⣕⣵⢿⣿⢿⣿⣟⣿⣝⡆⠁⠨⣹⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣴⣿⣿⣿⠁⢁⠄⠤⠁⠉⢫⠮⡻⡿⠿⡓⠑⠩⠉⢹⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⢉⣶⣿⣿⢁⡢⠑⢅⠄⠐⠈⠄⣬⣾⣳⣄⢂⠠⡠⢹⣿⣿⡿⣻⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣻⣄⣦⣾⡿⢿⣿⣷⡌⠌⠢⡫⡪⡾⣽⢿⣺⣯⣻⣯⢯⣫⣿⣿⢞⢾⢜⣽⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣧⣮⣿⣖⢀⠄⠈⠎⠝⠹⡹⡳⡋⡓⠽⣑⢺⣻⡏⣽⣿⣷⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⠛⠄⠁⣿⡷⠆⡐⠐⡐⡀⣲⢳⠨⡚⢞⣹⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⡿⠄⡥⣼⢝⡠⣥⣦⣔⢆⡩⡼⣤⢵⣮⢸⡪⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⡗⡈⡁⠠⣿⣿⣿⣐⠈⠊⡊⠂⠯⠻⠁⠁⢼⣿⢰⢱⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⠌⠄⠠⣵⣿⣿⣿⣿⡿⠄⡆⡎⡔⡐⠄⠁⢈⠅⢢⠺⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣎⡪⣸⣿⣿⡿⠿⣋⠂⠄⡂⠨⡈⠏⡇⢀⠄⠘⠸⠿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣷⣼⣾⣻⣬⣮⠏⠈⠌⡂⢁⠄⠣⡣⡂⠠⠐⠄⢌⠉⡛⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⠟⡀⠄⠁⠄⠄⠄⠁⠪⡢⠐⠄⡁⠠⠑⠷⣶⣤⣽⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣋⣴⠂⡐⢰⡊⠠⢀⠡⠐⡭⡌⠄⠐⡀⠅⢐⠉⠿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡆⠠⠁⡐⡈⢴⣀⠁⠐⡈⢀⠡⠄⣳⣤⣂⣡⠈⢛⠻⠿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣔⠄⠄⡀⣿⣿⣮⡄⠨⠄⠠⠁⠄⣻⣿⣿⣿⣷⣶⣷⣾⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⠁⠄⢰⣤⣟⣻⣿⡀⢁⢡⣬⣐⣀⢛⢿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣵⣤⣦⣟⣻⡟⣿⣟⣧⣔⣸⣿⣿⣿⣿⣶⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿
```

| Navigation                           |
| ------------------------------------ |
| [🠝 go top](#games-configs-and-more) |
| [🠜 go back](./readme.md)            |
