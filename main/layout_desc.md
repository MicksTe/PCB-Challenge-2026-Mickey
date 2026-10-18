Overall board size is 46.8mm x 62.4mm. Probably could have done better if i utilised the bottom side more and the empty spots but I ran out of time
### Stack-up
Top
GND shielding
Power + extra unimportant signals
Bottom

### High speed traces
- 32.768 kHz crystal for ESP32 is ground shielded and via fenced to avoid interference. Also ground on all layers below the crystal
- High speed clock (clk) on input side placed on bottom layer, no traces or components under it even with shield, would have liked to add a ground around it but ran out of space
- clk traces had continuous plane under it, and when changing layers, made sure there was GND via next to clk via
- USB routed as differential pair, Inner 1 has GND plane so thare is a continuous return path under it


### Note
- Did not consider the NPN transistors as an ICso there are vias and routing under it
- GND pads on ESP32 were not tied to the GND net so I changed it myself
- Pin 9 of both adders were both labelled COUT but served no purpose to be tied that way and may even be problematic(short when both COUTs are different) so decided to change it to no net. If this was intentional I wouldve routed this on Inner 2 and there would not be much difference on the overall layout
- NRST switch not connected to anything. I assumed this wouldve been connected to the MCU, so it is placed somewhat closely
- There was a DRC violation for a pad and non-plated through hole for the USB-C port, since this was to do with the footprint, I added an exception in DRC custom rules
- Removed name and value from silkscreen
