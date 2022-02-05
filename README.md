# RG351p-351ELEC-Optimizations
Some minor improvements for 351 ELEC firmware on RG351p devices

The instructions and files in this repository are provided without any warranty from author, use them at your own risk. I personally use them but i can't help you fix something that you break because of doing something wrong. So kindly do not expect support, i really don't have the time to provide it.

_**Also, i don't think 351Elec devs want the avg person to do these mods, as you can screw your system. So don't go and harass them for these. They are good folks over there.**_
_**If you screw up something just see below instruction**_

## I SCREWED UP MY DEVICE, HOW DO I FIX IT?
Just delete the files you copied to your device, from this mod, Reboot your device.


----------------------------------------------------------------------------------------------------------------
## Mod 1: Optimum Retroarch Clock Optimization

Retroarch configuration for optimized clocks for various emulators. Many of the simpler emulators like GB, GBC etc can be run perfectly well for majority of the games on much lower clocks than what Retroarch forces them on.

### Install Instructions

### Default Retroarch configuration

Set the below values in `/storage/roms/gamedata/retroarch/retroarch.cfg` file on your device. If any value is not present in the file you can just add it.

```
cpu_main_gov = "conservative"
cpu_max_freq = "1296000"
cpu_menu_gov = "powersave"
cpu_min_freq = "1008000"
cpu_scaling_mode = "1"
```

### Other Emulators / Games Configuration

Copy all the directories from `retroarch-optimizations` to `/storage/roms/gamedata/retroarch/config` directory on your device.

### Effects

- Sets retroarch to run at minimum clock during menus.

- Sets retroarch to scale in a more optimum way from base clock to max clock for CPU, instead of always running at max clock.

- Sets each emulator and game individually to run at the clock speed required for it. The files are fore cores that i use for various systems, if you use a different core, you can create a similar config for that core or game by trying and testing.

### CAUTION:

For the mod to work, you need to do changes in both the default Retroarch configuration and Other Emulators. If you just do one of the two , the mod will not work.

----------------------------------------------------------------------------------------------------------------
## Mod 2: Better Overall Clock Management

In it's Pineapple Forest release 351 Elec's clock management code is being overridden by Retroarch's cpu power management. This causes the cpu clock to not go down even after the emulator's have been closed. 

Files provided here can be used to achieve these improved clock states.

351 ELEC devs are now aware of this problem and will most likely fix this in their next release. ( I hope so, it may not be priority for them. )

So these fixes are only important for Pineapple Forest release of 351 ELEC.

### Install Instructions

#### Maximum Clock & Base Clock

- Create a directory `overrides` in `/storage/roms/bios` on your RG351p device.
- Copy the file `runemu.sh` from `clock-optimization/maximum-base` to `/storage/roms/bios/overrides/` directory on your RG351p.
- Copy the file `es_systems_custom.cfg` to `/storage/.config/emulationstation` directory on your RG351p.
- Restart Emulation Station. On Systems screen press _select_ and the _Restart EmulationStation_

#### Optimum Clock & Base Clock

- Create a directory `overrides` in `/storage/roms/bios` on your RG351p device.
- Copy the file `runemu.sh` from `clock-optimization/optimum-base` to `/storage/roms/bios/overrides/` directory on your RG351p.
- Copy the file `es_systems_custom.cfg` to `/storage/.config/emulationstation` directory on your RG351p.
- Restart Emulation Station. On Systems screen press _select_ and the _Restart EmulationStation_

### Effects

- Device will by default always run at 1 GHz outside of emulators. ( Only exception to this rule is the short time between first booting your device and launching your first game. )

- Device will return to Base clock of 1 GHz on quitting any emulator.

- Depending on which Option you applied in above instructions, following will happen.
	- **Maximum Clock & Base Clock**: On setting _"enable max performance"_ to Yes/On in ES Menu. Device will permanently run at Max Clock for CPU (1.3GHz) & GPU in that emulator/game.
	- **Optimum Clock & Base Clock**: On setting _"enable max performance"_ in Yes/On in ES Menu. Device will scale from min (1 GHz) to Max Clock (1.3 GHz) for CPU & GPU as per the load, in that emulator/game.

In my personal testing for PPSSPP, on game Hot Shot Tennis, Optimum Clock option works fine, you don't need to force CPU & GPU to always run at max clocks. Battery will thank you.

All of This is good for battery and tempratures. There is no need for running system at a higher clock if it is not required. It is just a waste of resources.

### CAUTION:

Since you are now optimizing clocks, for any emulator where you do not see good performance, you will have to go and set _"enable max performance"_ to Yes/On either in the _advance game options_ for that game / in the _advance system options_ for that system as a whole. 

So don't come complaining here that some X system that was working amazing earlier, is not working great now. You need to use the mod correctly. Just delete the mod if you can't fix it.
