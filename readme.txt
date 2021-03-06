this repository contains the eagle & gerber/svg files for avr-spi;
a simple SPI interface/programming board for flashing Atmega328 chips (PDIP)

------------------------------------------------------------------
------------------------------------------------------------------

the design allows for a single PDIP size Atmega328 to be flashed via SPI.
the choice of programmer is flexible, so long as it hosts an SPI interface
supported boards include the Atmel ICE, Sparkfun AVR Pocket Programmer, & Arduino

why use this method vs something like an Arduino?
  • eliminates the need for a bootloader to be flashed to the chip, freeing up about
    512-2k bytes flash memory space for additional program storage
  • allows programming using other languages, including C++ & AVR Assembly
  • permits extensive debugging & development process improvements (Microchip Studio)
  • speeds up program flash times considerably
  • doing it yourself is always more fun ^w^

------------------------------------------------------------------
------------------------------------------------------------------

the circuit is comprised of the following segments:
  > 6 pin SPI header
    • GND   -> Pins 8 (GND) & 22 (GND)
    • VCC   -> Pins 7 (VCC) & 20 (AVCC) | Pin 1 (!RESET) through 10kΩ pullup resistor
    • CIPO  -> Pin 18 (CIPO)
    • COPI  -> Pin 17 (COPI)
    • SCK   -> Pin 19 (SCK)
    • RST   -> Pin 1 (!RESET)
  > .1µF capacitor between VCC & GND
  > 200Ω resistor & blue LED -> Pin 14 (PB0)

the header allows connection to an external programming board
the capacitor stabilizes the supply voltage to the chip
the resistor & LED provide a built in method of testing the board & chip (PB0)
the pullup resistor holds the !RESET pin HIGH (logic low) until needed

------------------------------------------------------------------
------------------------------------------------------------------

the included files are:
  > EAGLE project files (schematic & board design)
  > original Gerber files (all layers)
  > modified Gerber files (removed excess plating, top & bottom layers)
  > SVG files of gerbers (inverted)
  > PNGs for laser engraving

for physically engraving the circuit i used the Snapmaker original
with top & bottom layer dimensions of 42.8mm x 75.5mm
  • necessary for proper scaling to match component dimensions
using Snapmaker Luban with the included PNG files in vector processing mode
  • B&W to 225, Impurity size 2
  • not sure why, but PNG files in vector mode seem to give the best results
from this i generated the gcode & ran 3 full passes at .2mm z variance
with laser power set to 96% (1600mW module)

------------------------------------------------------------------
------------------------------------------------------------------

these files & dimensions should work for all engravers,
but certain settings may have to be tweaked to achieve ideal results.

the included vector & PNG files have been inverted & edge traced so that the laser
will cut around the traces/holes/vias;
this works well with masking tape & simplifies the etching process.
peeling away the remaining tape after engraving leaves the circuit fully covered,
while exposing the remainder of the copper for etching (i used FeCl3).

this particular implementation uses a double sided PCB, but is designed
so that all component terminals begin on the bottom layer.
the remainder of the circuit is routed on the top layer, using a total of 8 vias.
this makes hand assembly much easier, allowing all components to be soldered from below.
it also widens the permissible error margin in matching the sides of the board together;
in this way, when drilling holes, the only parts that really need to line up are the vias.
if they are slightly out of alignment, a small bit of wire can be used to bridge the gap,
ultimately making it easier to get everything connected together properly by hand.

------------------------------------------------------------------
------------------------------------------------------------------

<3
