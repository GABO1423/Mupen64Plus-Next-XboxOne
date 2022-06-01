# Mupen64Plus-Next-XboxOne
This is a modified version of the [Mupen64Plus-Next](https://github.com/libretro/mupen64plus-libretro-nx) libretro core that is primarily intended for use with Xbox One and Series consoles. All credit goes to [m4xw](https://github.com/m4xw) for the core, as well as the [ANGLE](https://github.com/google/angle) implementation, and [tunip3](https://github.com/tunip3) for the custom [ANGLE](https://github.com/Xbox-Homebrew/angle) version used in this core.

The main changes made to the core are the following:

- [GLideN64](https://github.com/gonetz/GLideN64) has been downgraded to the version used in this [commit](https://github.com/libretro/mupen64plus-libretro-nx/commit/143e608e3ce715f62c71d589d7129ccd80ab0819). This is due to newer versions of GLideN64 used in the core after this point not working on Xbox One systems. Greeting you with a black screen with audio. While AngryLion works, it's too slow for the Jaguar CPUs on the Xbox One systems. So GLideN64 is the next best thing.
- [ParaLLEl-RSP](https://github.com/Themaister/parallel-rsp) has been enabled for this core, it is meant to be used alongside the AngryLion RDP plugin. 
- The [core options](https://github.com/GABO1423/Mupen64Plus-Next-XboxOne/blob/master/libretro/libretro_core_options.h) have been modified to reflect the GLideN64 downgrade, meaning options added after the commit linked above have been removed.
- Aside from the changes made to the core options for GLideN64, the [AngryLion](https://github.com/ata4/angrylion-rdp-plus) related settings have recieved some minor [aesthetical changes](https://github.com/GABO1423/Mupen64Plus-Next-XboxOne/commit/aea9273f1173d78b3bbdba92f9cde4c7087b1535).
- The [mupen64plus.ini](https://github.com/GABO1423/Mupen64Plus-Next-XboxOne/blob/master/mupen64plus-core/data/mupen64plus.ini), and [mupen64plus.ini.h](https://github.com/GABO1423/Mupen64Plus-Next-XboxOne/blob/master/custom/mupen64plus-core/main/mupen64plus.ini.h) files have been modified to be more in line with the standalone [mupen64plus-core](https://github.com/mupen64plus/mupen64plus-core) repository.
- The radius used in the [emulate_game_controller_via_libretro.c](https://github.com/GABO1423/Mupen64Plus-Next-XboxOne/blob/master/custom/mupen64plus-core/plugin/emulate_game_controller_via_libretro.c#L299) file is set to a value of 80, which limits the emulated analog stick range. This can have some negative impact on games, such as making it impossible to jump out of water in Super Mario 64. I changed this to a value of 100, which allows the analog stick to reach the full range of an N64 stick while still allowing for more subtle and slow movements.
- A new [ANGLE](https://github.com/GABO1423/Mupen64Plus-Next-XboxOne/tree/master/ANGLE) directory has been added, making it simple to build this core without needing to provide any additional files.

Besides the changes listed above, nothing else was changed from the Mupen64Plus-Next source code.
Since ANGLE can be kind of a performance bottleneck, I do not recommend using this core outside of the intended use case of Xbox systems with RetroArch installed.

**Click [here](https://github.com/GABO1423/Mupen64Plus-Next-XboxOne/blob/master/README-original.md) to read the original Mupen64Plus-Next README file.**

# Build Instructions

**Prequisites**:

- [MSYS2](https://www.msys2.org/) with the [mingw-w64-x86_64-toolchain](https://packages.msys2.org/group/mingw-w64-x86_64-toolchain) packages installed.
- **Optional**: Either [Git for Windows](https://gitforwindows.org/) or the [Git](https://packages.msys2.org/package/git) package for MSYS2.

**Step 1: Getting the source code**

You can either use the command `git clone https://github.com/GABO1423/Mupen64Plus-Next-XboxOne.git` with a command prompt, or download the source code as a zip file directly from GitHub:

![image](https://user-images.githubusercontent.com/35014183/164373033-25607e57-24c5-4987-91bc-3e43c7f02387.png)

**Step 2: Setting up the build**

Once the source code is downloaded, go into the ANGLE directory and unzip the ANGLE Library.7z file. You should end up with two folders: `lib` and `include`.
Next, open MSYS2 (make sure you open the MINGW 64-bit variant).

![image](https://user-images.githubusercontent.com/35014183/164373294-7e12f238-b013-40df-b686-1ef24c541d9d.png)

Then use the `cd` command to navigate to where the code is located.

**Step 3: Begin the build**

Simply type `make` on MSYS2, press Enter, and watch it build! You should end up with a file called "mupen64plus_next_libretro.dll" if everything goes correctly.
