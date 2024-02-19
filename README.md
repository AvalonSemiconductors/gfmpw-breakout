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

Note: the board does not have the capability to program the 25Q32 spiflash in-place. You will need to solder it to a breakout board such as [this](https://protosupplies.com/product/pcb-smd-soic-8-msop-8-tssop-8-to-dip-adapter5-pack/) and socket it using female headers on the GFMPW breakout. To program it, any number of portable ROM programmers can be used, such as the [CH341A](https://www.amazon.com/Programmer-Module-CH341A-Burner-5V-3-3V/dp/B07PFCJ8G9).

The pinout of the board is as such (a KiCad symbol is [also available](board_symbol.kicad_sym)):

![](Screenshot_from_2024-02-19_14-44-46.png)

Note that 3V3 is a output from the on-board voltage regulator. The only power input is 5V.

To edit the KiCad files, you will need to add the ``Caravel_Board.pretty`` footprint files from the efabless/caravel_board repo, which can be obtained [here](https://github.com/efabless/caravel_board/tree/main/hardware/footprints/Caravel_Board.pretty).

# BOM

| Designator(s) | Value       | TME # | Mouser # |
|---------------|-------------|-------|----------|
| U1         | AMS1117-3.3 | AZ1117H-3.3TRE1 | 595-REG1117-3.3 |
| U2         | 25Q32 or compatible       | MX25L1006EMI-10G | 454-W25Q32JVSSIMTR |
| U3         | MCP1319MT | MCP1319MT-29LT | 579-MCP1319MT29LE/OT |
| U4         | GFMPW IC | N/A | N/A |
| U5, U6, U7, U8 | SN74LV1T34 | SN74LV1T34DBVRG4 | 595-SN74LV1T34DBVRG4 |
| D1, D2 | LED 1206 (metric 3216) | 24-21SURC/S530-A2 | 630-HSMH-H150 |
| R1, R3, R3 | 1K 1206 (metric 3216) | 1206S4F1001T5E | 71-RCA12061K00JNEA |
| R2 | 10K 1206 (metric 3216) | 1206S4F1002T5E | 667-ERA-8VEB1002V |
| C1, C2, C3 | 100nF 1206 (metric 3216) | 1206B104J500CT | 581-KAM31BR71H104KT |
