# Games configs and more
[Go to games](../games/)
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

In my case I'm using voicemeeter to control my audio interface, so I'm using Voicemeeter Virtual ASIO

**Important:** you should copy the text related to your asio driver in this block of text.

6 - Open `RS_ASIO.ini` file inside the game directory and paste your asio driver name right after `Driver=` line.

**Important:** You have to assign the input and output driver in this text file.

In my case I used `[Asio.output]` assigned to `Voicemeeter Virtual ASIO` and `[Asio.input.0]` assigned to `Voicemeeter Virtual ASIO`

Now you're most done.

It's important to remember that when we talk about stuff related to a external instrument connected to your computer, the sound will always have some delay.The most bufferSize you have setted to your device the longest time it will take the sound to come out of the speakers.

In order to reduce the delay we should find the lowest bufferSize value until the sound start to strike.

my buffersize inside voicemeter ASIO Driver: 224

___

## Cyber hunter config

This is a part of code from the `config` file inside folder's directory.
Better graphics and high FPS.

```ini
[graphic_setting]
graphic_quality = 4
display_mode_pc = 1
fps_level_pc = 4
graphic_quality_show = 4
graphic_hdr = -1
```
