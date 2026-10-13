# ATtiny85 Sensor Node

A small through-hole PCB built around an ATtiny85 that reads a potentiometer with the on-chip ADC and drives an LED output. I designed it in KiCad as the capstone of a self-directed electronics curriculum covering circuit fundamentals, digital logic, and PCB design workflow.


## Status

- [x] Schematic complete, ERC clean
- [x] PCB layout complete, DRC clean
- [x] Gerbers exported and ready for fabrication (JLCPCB)

<!-- Update this list as the project moves forward. Leave unchecked anything that is not done yet. -->

## Overview

The board has four main parts:

- **Sensor input:** a potentiometer wiper connected to PB3 (ADC3) for analog input
- **Output:** an LED driven by the microcontroller
- **Programming:** a 6-pin ISP header for flashing with a USBasp programmer
- **Power:** a decoupling capacitor, a RESET pull-up resistor, and a power indicator LED

I used through-hole components throughout so the board can be hand-soldered.

## Design Decisions

**Pin conflict between the potentiometer and SCK.** My first layout put the potentiometer wiper on a pin that also serves as SCK for in-system programming, which would have interfered with flashing the chip. I moved the wiper to PB3 so the ADC input and the ISP header no longer share a pin.

**Decoupling capacitor wiring.** While checking the schematic I found wiring errors in my decoupling capacitor connections and corrected them so the capacitor sits across the supply pins as intended.

**RESET pull-up.** I added a pull-up resistor on RESET so the chip does not reset from noise during normal operation.

**Power indicator LED.** I added an LED on the supply rail so I can confirm power with a quick glance before probing.

**Net labels for ISP routing.** I used net labels instead of long wires for the programming header connections to keep the schematic readable.

**Ground pour.** The board has a GND copper pour to give a low-impedance return path and simplify routing.

**Through-hole parts.** Every component is through-hole for easy hand-soldering.

## Bill of Materials

| Part | Notes |
|------|-------|
| ATtiny85-20PU | DIP-8 microcontroller |
| DIP-8 machined-pin socket | Lets the chip be removed and reprogrammed |
| Alpha RD901F-40 potentiometer | Analog input |
| 10 µF electrolytic capacitor | 
| Pin headers | ISP programming header |
| LEDs and resistors | 330, 1k, & 10k Ω |
| USBasp programmer | For flashing (not part of the board) |




## Tools

- KiCad (schematic capture, PCB layout, DRC/ERC, Gerber export)
- JLCPCB (fabrication)
- USBasp (in-system programming)
- Multimeter (board testing)

## Author

Samil Sharma, Mechanical Engineering at UIUC (pursuing ECE) | https://www.linkedin.com/in/samil-sharma-a38b2a301/
