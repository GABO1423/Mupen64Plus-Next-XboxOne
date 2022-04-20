# Mupen64Plus-Next-XboxOne
This is a modified version of the [Mupen64Plus-Next](https://github.com/libretro/mupen64plus-libretro-nx) libretro core that is primarily intended for use with Xbox One and Series consoles. All credit goes to [m4xw](https://github.com/m4xw) for the core, as well as the [ANGLE](https://github.com/google/angle) implementation.

The main changes made to the core are the following:

- [GlideN64](https://github.com/gonetz/GLideN64) has been downgraded to the version used in this [commit](https://github.com/libretro/mupen64plus-libretro-nx/commit/143e608e3ce715f62c71d589d7129ccd80ab0819). This is due to newer versions of GlideN64 used in the core after this point not working on Xbox One systems. Greeting you with a black screen with audio. While AngryLion works, it's too slow for the Jaguar CPUs on the Xbox One systems. So GlideN64 is the next best thing.
- [ParaLLEl-RSP](https://github.com/Themaister/parallel-rsp) has been enabled for this core, it is meant to be used alongside the AngryLion RDP plugin. 
- The core options have been modified to reflect the GlideN64 downgrade, meaning options added after the commit linked above have been removed.
- The mupen64plus.ini file in the mupen64plus-core/data folder has been modified to be more in line with the standalone [mupen64plus-core](https://github.com/mupen64plus/mupen64plus-core) repositiory.
- The radius used the in the emulate_game_controller_via_libretro.c file is set to a value of 80, which limits the emulated analog stick range. This can have some negative impact on games, such as making it impossible to jump out of water in Super Mario 64. I changed this to a value of 100, which allows the analog stick to reach the full range of an N64 stick while still allowing for more subtle and slow movements.
- A new ANGLE directory has been added, making it simple to build this core without needing to provide any additional files.

Besides the changes listed above, nothing else was changed from the Mupen64Plus-Next source code.
Since ANGLE can be kind of a performance bottleneck, I do not recommend using this core outside of the intended use case of Xbox systems with RetroArch installed.
