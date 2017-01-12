# Morse Mech

A single-key mechanical keyboard. (Typed, of course, in [International Morse
code](1).) The software for this board can be found in [its own separate repo](2).
The following instructions may change over time, and should be taken as a guide
only. Use common sense, and feel free to submit a pull request--or even just
email me--to update this file if it gets outdated.

[1]: https://en.wikipedia.org/wiki/Morse_code
[2]: https://github.com/Ernest314/Morse-Mech-PCB


## Features

- True single-key operation
- Conforms to International Morse Code
- High-quality mechanical switch
- Adaptive signaling timing
- 16.8 million-color backlighting
- RGB indicator light
- Onboard EEPROM settings storage
- Full-speed USB operation
- USB HID-compatible device


## Version tracking

Both this repo and the [corresponding code repo](2) are pushed with the latest
updates. This means that the latest commit for this repo corresponds to the
latest commit for the code repo. If you have a legacy revision of the board,
you will either have to modify the source code (feel free to ask me for help),
or use the code repo with the closest corresponding dates.


## Assembly

The KiCAD schematic contains footprint and datasheet values for each component.
In addition to selecting components with matching values/footprints, you may
also directly use the components in the datasheets provided. When this board was
first designed, all components were available from Mouser. (The components are
very common; they will probably all be available from [Mouser](3) or [Digikey](4).
Another good resource for finding components is [Octopart](5).)

Switches and keycaps were purchased from [MAX Keyboard](6), although you can get
them from anywhere you prefer. The only limitation is that the footprint on the
PCB is that of a Cherry MX switch. (This means Gateron, Kailh, and Razer
switches should all work.)

The PCB for this board was initially manufactured by [OSH Park](7). OSH Park
accepts directly uploading `.kicad_pcb` files, and the current PCB is laid out
to the tolerances of OSHPark. Another convenient manufacturer is [DirtyPCBs](8),
although the tolerances of the board have not been tested with them. (Some
adjustments may be needed.) The PCB fits inside the 5cm x 5cm smaller limit for
PCB sizes, and is pretty close to that size.

A stencil for the board was ordered from [OSH Stencils](9). This was because I
needed additional stencils, and it was cheap enough that I decided it was worth
it to combine them and get them shipped. However, it is completely feasible to
laser-cut the stencils.

The initial run of this board did not have a case, but one can easily be created
for it. There are no mounting holes (other than the extra stabilization pins for
PCB-mounted switches). An easy way would be to 3D-print a case, or to create a
sandwiched laser-cut case. The board can be secured with hot glue, double-sided
tape, or just by sandwiching the corners of the PCB.

[3]: http://www.mouser.com/
[4]: http://www.digikey.com/
[5]: https://octopart.com/
[6]: http://www.maxkeyboard.com/
[7]: https://oshpark.com/
[8]: http://dirtypcbs.com/store/pcbs
[9]: https://www.oshstencils.com/#


## Programming

The AVR can be programmed with any AVR programmer (compatible with ATmegas). The
initial run of the boards were programmed with an Atmel-ICE programmer. (The
specific AVR that the programmer should be compatible with is the `ATmega16u2`.)
The AVR is interfaced with a standard 6-pin ICSP header, with the square pad
denoting "pad 1". The pads provided on the board are not meant to have a
shrouded header soldered on; instead, a Pogo pin <-> ICSP adapter was used to
program the AVR.

Again, the code for the board can be found in [its own repo](2). (See above
discussion of repo compatibility.) [Atmel Studio 7](10) was used to program the
board--see that repo for more details.

[10]: http://www.atmel.com/microsite/atmel-studio/


## Operating instructions

*Finally! What you were waiting for!*

As a *true* Morse code keyboard (there is **a single switch**, not two like
with many other keyboards), there is some additional setup that is needed to run
the board. For additional details (e.g. the different indicator light meanings),
reference [the code repo](2) for this board.

In order to start sending data to the computer, the keyboard needs to first be
placed into "active" mode. This consists of entering the [prosign](11) `<CT>`
(mneumonic "copy this"). Behind the scenes, this allows the microcontroller to
figure out the lengths of the operator's particular timings for dots and dashes.
Correspondingly, to suspend the keyboard, enter the prosign `<SK>` (mneumonic
"silence key").

As for entering actual characters, the keyboard accepts standard [International
Morse Code](1). This includes letters, numbers, and punctuation. There is no way
to enter lower-case letters; all letters are entered in upper-case (in genuine
telegraph style). **This is a feature, not a bug.**

[11]: https://en.wikipedia.org/wiki/Prosigns_for_Morse_code
