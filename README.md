# Creamlinux
A CreamAPI clone for Linux.

Since 20PercentRendered has archived the repo, I have decided to fork and support it as far as I can.

## Support
This *should* work for any linux native steam title that doesn't block LD_PRELOAD. The following games have been tested and confirmed to work:

 - Stellaris
 - Hearts Of Iron IV
 - Europa Universalis IV
 - Crusader Kings II
 - PAYDAY 2
 
## Usage 
0. You will need the actual, **up-to-date** DLC files in the game. Creamlinux does **not** auto-download anything
1. Download the [latest](https://github.com/anticitizn/creamlinux/releases/latest/download/creamlinux.zip) release of Creamlinux
2. Unzip it and copy the files to the game's directory
3. Set the game's steam launch params to `sh ./cream.sh %command%`
4. Launch the game and have fun!

The list of "supported" DLCs is stored in `cream_api.ini`. If you want to test creamlinux on a new game or a new DLC has just come out, you can add more entries here manually.

If that doesn't work, please check the Troubleshooting section below.

## Building from source
0. Ensure you have all build dependencies installed:
- On Ubuntu: `build-essential` `gcc-multilib` `g++-multilib` `cmake` `git`
- On Arch: `base-devel` `multilib-devel` `cmake` `git`

1. Clone the project:
```
git clone https://github.com/anticitizn/creamlinux
```
2. Build the project:
```
sh ./build.sh
```

3. Copy `output` folder contents to the game folder
4. Set the game's steam launch params to `sh ./cream.sh %command%`

Alternatively, if you have Docker installed, you can just run `docker compose up`

# Troubleshooting
## Red triangles next to DLCs
This is normal. The DLCs should still work.

![Red triangles next to DLCs are normal](https://cdn.discordapp.com/attachments/663174968791662594/1093109044295766106/image.png)

## DLCs don't work
Have you made sure to download the latest version of the DLC files? Sometimes unrelated patches or updates to the game will modify some DLC files, and creamlinux is currently somewhat sensitive to outdated files.

## Game not starting after enabling creamlinux
Have you made sure that you actually put the creamlinux files in the game's directory? (I sometimes forget to move them out of the `creamlinux` folder into the game directory proper)

## Nothing helped!
Please collect a log using the instructions below, then post an issue describing your situation [here](https://github.com/anticitizn/creamlinux/issues/new).

## Gathering logs
Install `konsole` and set your game launch options to this:
```
konsole --hold -e sh ./cream.sh %command%
```
Then launch the game (skip any launchers like the Paradox launcher if possible, they interfere with the logging). Wait for the game to load if applicable, close it, then copy and paste the contents of the terminal.

# Advanced 
If you want to load `cream_api.ini` from a specific path, specify the path with `CREAM_CONFIG_PATH` in the launch options.

## Credits
[pulzed](https://github.com/pulzed) for [mINI](https://github.com/pulzed/mINI)(ini.h)

[Valve](https://www.valvesoftware.com/) for [steamworks](https://partner.steamgames.com/)

[gabime](https://github.com/gabime) for [spdlog](https://github.com/gabime/spdlog)

[goddeysfreya](https://github.com/goddessfreya) for [hookey](https://github.com/goddessfreya/hookey)

[20PercentRendered](https://github.com/20PercentRendered) for [creamlinux](https://github.com/20PercentRendered/creamlinux)
