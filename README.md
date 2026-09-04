## About

This project describes the process of creating a Fuzz Face guitar pedal from scratch. It uses Silicon NPN transistors, as opposed to the original's Germanium PNP. The circuit is also slightly modified from the original, aiming to eliminate high-frequency oscillations and boost the volume a little.
My aim was to Do-It-Myself, so all files were created by me, except for the potentiometer library,
which is linked below. Circuit was soldered on a Stripboard. For future pedals I also aim to make PCBs.

### Schematic
pic
### SPICE Simulation
pic
### Components needed
| Designator | Component         | Notes                          |
|------------|-------------------|--------------------------------|
|            | Stripboard        |                                |
|            | Jumpers and wires |                                |
|            | DC Barrel Jack    |                                |
|            | 3PDT              |                                |
|            | Battery clip      |                                |
| +9V        | 9V Battery        |                                |
| IN         | Stereo Jack       |                                |
| OUT        | Mono Jack         |                                |
| RV1        | Alpha B1K         |                                |
| RV2        | Alpha A500K       |                                |
| C1         | 2.2uF             | Electrolytic                   |
| C2         | 10uF              | Electrolytic changed from 22uF |
| C3         | 0.01uF            | Ceramic/Film                   |
| C4,C5      | 100p              | Optional                       |
| R1         | 470               | changed from 330               |
| R2         | 47K               | changed from 33K               |
| R3         | 47K               | changed from 100K              |
| R4         | 6.8K              | changed from 8.2K              |
| Q1,Q2      | BC548C            |                                |
| R5         | 20K               | Optional                       |
| D1         | LED               | Optional                       |
### Breadboard
not sure
### Off-board wiring
schematic & pedal
### Comparison
Simulation vs Oscilloscope
### Demo
YT

## Acknowledgments

Some very useful links:

* [Geofex's The Technology of the Fuzz Face](http://geofex.com/article_folders/fuzzface/fftech.htm)
* [Barbarach's Pots for SPICE](https://barbarach.com/pots-for-spice/)
* [Madbeanpedal's off-board wiring write-up](https://madbeanpedals.com/tutorials/downloads/MBP_FootswitchWiring.pdf)