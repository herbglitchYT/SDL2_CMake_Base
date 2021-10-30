# SDL CMake Base
## Description
sdl cmake basic setup

## Setup
* mingw-w64
    * [MinGW-w64 website](https://www.mingw-w64.org/). MingW-W64-builds under downloads is what is used.
    * direct link to the installer [MinGW-w64 installer](https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win32/Personal%20Builds/mingw-builds/installer/mingw-w64-install.exe/download)
    * These are the options that are used
    * ![MinGW-w64 Settings](https://i.imgur.com/i9bkmbu.png)
    * **Make sure to add to path** [How to add to path](https://helpdeskgeek.com/windows-10/add-windows-path-environment-variable/)

* Install CMake
    * [CMake Download Page](https://cmake.org/download/)

* In vscode install CMake Tools
    * ![CMake Tools](https://i.imgur.com/QFazixd.png)

* in vscode terminal, run ```git submodule update --init --recursive```
* in vscode, Run ```CMake: CMake Scan for Kits```
* in vscode, Run ```CMake: Select a Kit```
    * select ```GCC [version] i686-w64-mingw32```
* in vscode, Run ```CMake: Delete Cache and Reconfigure```
    * This may take a bit, but you shouldn't have to run it again
* press [f7]
* in the vscode terminal you can now run the project by Running ```build\sdl_cmake.exe```
    *you can also run as debu by pressing [ctrl] + [f5]