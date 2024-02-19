# gfmpw-breakout
This repo contains all the files, including production-ready gerber files, for this PCB:

![](Screenshot_2024-01-27_17-30-15.png)

It contains all components on-board to keep the caravel management controller happy and breaks out the user IO lines into the same footprint as a DIP-40 IC. The board is meant for both prototyping, i.e. on a breadboard, or use as a module on another PCB.

Specifically, it has:

 - Space for any GFMPW IC
 - Socket for spiflash IC containing mangement controller firmware, plus required level shifters and 3.3V voltage regulator
 - Power-on reset circuitry
 - LED on ``gpio``
 - Breakouts for pins ``mprj_io[37:5]`` as well as ``mprj_io[0]``, ``mprj_io[1]`` and ``mprj_io[4]``
