## About

This project describes the process of creating a Fuzz Face guitar pedal from scratch. 

It uses Silicon NPN transistors, as opposed to the original's Germanium PNP. The circuit is also slightly modified from the original, aiming to eliminate high-frequency oscillations and boost the volume a little.

All files, except for the potentiometer library, were created by me.

Fuzz Face is a very simple circuit, so I soldered it on a Stripboard - for future, more complicated pedals I also aim to make PCBs.

### Schematic
Simplified schematic of the circuit, without off-board wiring:

<img width="552" height="500" alt="Fuzz Face Schematic" src="https://github.com/user-attachments/assets/7786a8fd-e977-4e55-a13a-dab57540a2cf" />

Note the swapped 1 and 3 on the potentiometers. That's done so on the finished pedal the knob values will increase when turning clockwise, instead of decrease.

### SPICE Simulation
As can be seen, the gain is so high that even at a low input signal value like 10mV pp, 
the output signal goes into clipping:

<img width="584" height="250" alt="SPICE Simulation at 10mV pp" src="https://github.com/user-attachments/assets/563702b1-4397-4387-a2b4-889b66b1c9c1" />


As input signal's voltage increases (100mV pp), the duty cycle changes:

<img width="584" height="250" alt="SPICE Simulation at 100mV pp" src="https://github.com/user-attachments/assets/abf628bd-c078-4488-ada8-2bd5b300b530" />

Pedal's frequency response:

<img width="584" height="250" alt="SPICE Simulation of frequency response" src="https://github.com/user-attachments/assets/da1ffb39-840a-4b80-b36b-6b3b96ba7c09" />

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
| C2         | 10uF              | Electrolytic, changed from 22uF|
| C3         | 0.01uF            | Ceramic/Film                   |
| C4,C5      | 100p              | Optional                       |
| R1         | 470               | changed from 330               |
| R2         | 47K               | changed from 33K               |
| R3         | 47K               | changed from 100K              |
| R4         | 6.8K              | changed from 8.2K              |
| Q1,Q2      | BC548C            | High gain of ~500              |
| R5         | 20K               | Optional                       |
| D1         | LED               | Optional                       |

Most of the component swaps (C1, C2 electrolytic instead of film; R2, R3, R4) are simply because that's what I had, and the differences weren't very noticeable. 

The changed C2 value and additional C4 & C5 capacitors aim to eliminate high-frequency oscillations. 
Swapping R1 from 470 to 330 was done to boost the output volume.

### Breadboard

Before soldering on a protoboard, firstly I've done the circuit on a breadboard.

I won't bother describing it here, as some great instructions already exist. A very good step-by-step write-up can be found here: [Breadboarding A Silicon Fuzz Face](https://diy.smallbearelec.com/HowTos/BreadboardSiFF/BreadboardSiFF.htm).

### Off-board wiring

Off-board wiring schematic was done in DIY Layout Creator:

<img width="510" height="455" alt="Offboard wiring" src="https://github.com/user-attachments/assets/ffadef98-8e36-4904-814c-5d624b9ee861" />

The wiring with a 3PDT allows for True Bypass, meaning the pedal won't influence the signal when the pedal is off.

The finished pedal's insides:

<img width="345" height="615" alt="Inside of pedal" src="https://github.com/user-attachments/assets/d88f0083-484e-40cb-82bd-5a4317c0a045" />

I'll admit the soldering is not the prettiest job. Something to improve on!

When purchasing the enclosure, for simplicity, I ordered a pre-drilled enclosure. 

The pre-drilled layout however doesn't allow for a 9V battery to fit inside the pedal.

In order to avoid something like this it'd be best to drill the enclosure yourself - or ditch the 9V battery altogether, using only a 9V adapter. 

Important to note that as most pedals, this one uses a center negative barrel jack, and there's no reverse voltage protection, so be mindful of that.

### Comparison

SPICE Simulation vs Oscilloscope:

<img width="565" height="583" alt="oscilloscope_comparison" src="https://github.com/user-attachments/assets/61d5d425-97b1-41bd-83c8-dfcfa86f5e5f" />

I think it's fair to say the signals are quite similar. The differences will mostly boil down to component tolerances (For example, the 500K pot used here
actually measures ~440K Ohms).

<!-- <img width="934" height="398" alt="oscilloscope_100mV_spice" src="https://github.com/user-attachments/assets/86cf3e87-e138-4306-b351-362d094b9348" /> -->
<!-- <img width="800" height="480" alt="oscilloscope_100mV" src="https://github.com/user-attachments/assets/b58d2b29-ffc2-409b-9fd0-1be0adca6092" /> -->

### Pedal Demo

to be done

### Acknowledgments

Some very useful links:

* [Geofex's The Technology of the Fuzz Face](http://geofex.com/article_folders/fuzzface/fftech.htm)
* [Barbarach's Pots for SPICE](https://barbarach.com/pots-for-spice/)
* [Madbeanpedal's off-board wiring write-up](https://madbeanpedals.com/tutorials/downloads/MBP_FootswitchWiring.pdf)
