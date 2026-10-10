## About

This project describes the process of creating a Fuzz Face guitar pedal from scratch. It uses Silicon NPN transistors, as opposed to the original's Germanium PNP. The circuit is also slightly modified from the original, aiming to eliminate high-frequency oscillations and boost the volume a little.
My aim was to Do-It-Myself, so all files were created by me, except for the potentiometer library,
which is linked below. Circuit was soldered on a Stripboard. For future pedals I also aim to make PCBs.

### Schematic
Simplified schematic of the circuit, without off-board wiring:

<img width="884" height="805" alt="Fuzz Face Schematic" src="https://github.com/user-attachments/assets/7786a8fd-e977-4e55-a13a-dab57540a2cf" />

### SPICE Simulation
As can be seen, the gain is so high that even at a low input signal value like 10mV pp, 
the output signal goes into clipping:

<img width="934" height="398" alt="SPICE Simulation at 10mV pp" src="https://github.com/user-attachments/assets/563702b1-4397-4387-a2b4-889b66b1c9c1" />


As input signal's voltage increases, the duty cycle changes:

<img width="934" height="398" alt="SPICE Simulation at 100mV pp" src="https://github.com/user-attachments/assets/abf628bd-c078-4488-ada8-2bd5b300b530" />

Pedal's frequency response:

<img width="934" height="398" alt="SPICE Simulation of frequency response" src="https://github.com/user-attachments/assets/da1ffb39-840a-4b80-b36b-6b3b96ba7c09" />

At maximum fuzz (fuzz=1.0) we get a resonant frequency around 220Hz, so it'd best
not to turn the fuzz knob all the way when playing.

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
| Q1,Q2      | BC548C            | High gain of ~500              |
| R5         | 20K               | Optional                       |
| D1         | LED               | Optional                       |

Most of the component swaps are simply because that's what I had.

### Breadboard

Before soldering on a protoboard, firstly I've done the circuit on a breadboard.
A very good step-by-step write-up can be found here: * [Breadboarding A Silicon Fuzz Face](https://diy.smallbearelec.com/HowTos/BreadboardSiFF/BreadboardSiFF.htm).

### Off-board wiring

Off-board wiring was done in DIY Layout Creator:

<img width="1019" height="910" alt="Offboard wiring" src="https://github.com/user-attachments/assets/ffadef98-8e36-4904-814c-5d624b9ee861" />

The wiring with a 3PDT allows for True Bypass, meaning the pedal won't influence the signal when the pedal is off.

The finished pedal:

<img width="1844" height="3276" alt="Inside of pedal" src="https://github.com/user-attachments/assets/d88f0083-484e-40cb-82bd-5a4317c0a045" />

I'll admit the soldering is not the prettiest job. Something to improve on!

### Comparison

SPICE Simulation vs Oscilloscope:

<img width="848" height="875" alt="oscilloscope_comparison" src="https://github.com/user-attachments/assets/61d5d425-97b1-41bd-83c8-dfcfa86f5e5f" />

I think it's fair to say the signals are quite similar. The differences will mostly boil down to component tolerances (For example, the 500K pot used here
actually measures ~440K Ohms).

<!-- <img width="934" height="398" alt="oscilloscope_100mV_spice" src="https://github.com/user-attachments/assets/86cf3e87-e138-4306-b351-362d094b9348" /> -->
<!-- <img width="800" height="480" alt="oscilloscope_100mV" src="https://github.com/user-attachments/assets/b58d2b29-ffc2-409b-9fd0-1be0adca6092" /> -->

### Demo
YT

## Acknowledgments

Some very useful links:

* [Geofex's The Technology of the Fuzz Face](http://geofex.com/article_folders/fuzzface/fftech.htm)
* [Barbarach's Pots for SPICE](https://barbarach.com/pots-for-spice/)
* [Madbeanpedal's off-board wiring write-up](https://madbeanpedals.com/tutorials/downloads/MBP_FootswitchWiring.pdf)
