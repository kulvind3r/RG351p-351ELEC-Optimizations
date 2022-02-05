# RG351p-351ELEC-Optimizations
Some minor improvements for 351 ELEC firmware on RG351p devices

The instructions and files in this repository are provided without any warranty from author, use them at your own risk. I personally use them but i can't help you fix something that you break because of doing something wrong. So kindly do not expect support, i really don't have the time to provide it.


## Better Clock Management

In it's Pineapple Forest release 351 Elec's clock management code is being overridden by Retroarch's cpu power management. This causes the cpu clock to not go down even after the emulator's have been closed. 

In addition, many of the simpler emulators like GB, GBC etc can be run perfectly well for majority of the games on much lower clocks than what Retroarch forces them on.

Files provided here can be used to achieve this improved clock states.

351 ELEC devs are now aware of this problem and will most likely fix this in their next release. ( I hope so, it may not be priority for them)

So these fixes are only important for Pineapple Forest release of 351 ELEC.