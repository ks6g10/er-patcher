# Elden Ring Proton Patcher


A tool aimed at enhancing the experience when playing the game on linux through proton.

## Warning

**This tool is based on patching the game executable though hex-edits. However it is done in a safe and non-destructive way, that ensures the patched executable is never run with EAC. Use at your own risk!** 

## Features

- set custom frame time limits (e.g. 30, 90, 165, ...)
- disable black borders when using resolutions with an aspect ratio other than 16:9 (e.g. ultrawide).
- vigniette removal

## Usage

1. Copy the file `er-patcher` to the game directory.
2. In steam, set the game launch options to `./er-patcher ARGS -- %command%` where ARGS is replaced with a combination of
  - `-r RATE` or `--rate RATE` for setting a custom framerate cap (default: 60)
  - `-u` or `--ultrawide` for removing black bars
  - `-v` or `--vigniette` for removing the vigniette overlay
  - Example: `./er-patcher --rate 30 -uv -- %command%`
  - Example with mangohud and wine fullscreen fsr: `./er-patcher --rate 144 -uv -- env WINE_FULLSCREEN_FSR=1 MANGOHUD=1 MANGOHUD_CONFIG=histogram %command%`
3. Launch the game through steam. `er-patcher` automatically launches a patched version of `eldenring.exe` with EAC disabled.

### Windows

It should work on windows, just as well. The only difference is, that you need to run the script via your python 3 installation. Depending on the version of python 3 you have installed you would need a slightly different path than shown in the following example.

Example: `C:\Program Files\Python36\python.exe er-patcher --rate 165 -uv -- %command%`

## How it works

When the game is launched through steam, the tool creates a patched version of `eldenring.exe` called `eldenring.patched.exe` while leaving the original intact. The tool then modifies the steam launch command by replacing the string `start_protected_game.exe` with `eldenring.patched.exe` so that the patched exe is always run without EAC. After the game is closed, `eldenring.patched.exe` is deleted.