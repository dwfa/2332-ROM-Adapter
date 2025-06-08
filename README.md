Various Adpaters for the MOS 2332 ROM

In the **2732-TH** Directory is the PET 2332 to 2732 ROM Adapter

Overview

This repository contains the KiCad design files for an adapter board that allows a standard 2732 EPROM (Erasable Programmable Read-Only Memory) to function as a direct replacement for a MOS 2332 Mask ROM in vintage computer systems, specifically targeting Commodore PET computers (e.g., PET 8032, SuperPET).

The MOS 2332 is a 4KB (4096 x 8-bit) mask-programmable ROM often found in older systems. Due to their mask-programmed nature, these ROMs cannot be easily reprogrammed or replaced if faulty or if custom firmware is desired. This adapter board provides a modern, flexible solution by mapping the 2332's pinout and specific control logic to a readily available and reprogrammable 2732 EPROM.
Features

    * 2332 Pinout Adaptation: Correctly maps the address (A0-A11), data (D0-D7), and control signals of the 2332 ROM to the corresponding pins of a 2732 EPROM.
    * NOROM Signal Handling: Incorporates necessary 74LS series logic gates (74LS04 Hex Inverter and 74LS32 Quad 2-input OR Gate) to correctly interpret the PET system's NOROM signal, ensuring proper
      ROM enabling/disabling for normal operation and diagnostic purposes.
    * 2-Layer PCB: Designed as a cost-effective 2-layer printed circuit board, suitable for fabrication by most hobbyist-friendly PCB manufacturers.
    * Physical Compatibility:
        * 2332 Side: Utilizes through-hole pads for soldering standard 2x12 pin headers, allowing the adapter to plug directly into the existing 2332 ROM socket on the mainboard.
        * 2732 Side: Features a 24-pin DIP socket for easy insertion and replacement of a 2732 EPROM.
    * Robust Design Rules: Implements conservative design rules for trace width, clearance, via size, and solder mask, ensuring high manufacturability and reliability.

Compatibility

This adapter is designed to replace 2332 ROMs in systems that utilize the pinout and NOROM logic of the MOS 2332, such as the Commodore PET 8032 and SuperPET.
Getting Started (Building Your Own)

To build this adapter, you will need to:

    * Obtain the PCB:
        * Download the latest Gerber files from the Releases section of this repository.
        * Order the PCB from your preferred manufacturer (e.g., PCBWay, JLCPCB) using these Gerber files.
    * Gather Components: Refer to the Bill of Materials (BOM) section for the required components.
    * Assemble the Board: Solder the components onto the PCB according to the silkscreen markings and
      component placement.
    * Program Your 2732 EPROM: Load your desired 4KB (2048 x 16-bit or 4096 x 8-bit) ROM image into a
      2732 EPROM using an appropriate EPROM programmer.
    * Install: Plug the assembled adapter into the 2332 ROM socket on your target system.

Design Details
KiCad Version

    * Designed using KiCad 8.0.x. While efforts are made to ensure compatibility, older or newer KiCad
      versions may display minor differences.

Key Components

    * 2332 (Header): Connection points for 2x12 pin headers, 0.1" pitch, 0.6" row spacing (custom footprint).
    * 2732 (Socket): 24-pin DIP socket (0.6" wide).
    * 74LS04: 74LS04 Hex Inverter (14-pin DIP).
    * 74LS32: 74LS32 Quad 2-input OR Gate (14-pin DIP).

Layout Strategy

    * 2332 Interface: Utilizes through-hole pads on the top layer for soldering pin headers, with pins facing downwards.
    * 2732 Socket: Located on the top layer, soldered from the bottom.
    * Logic Gates: Placed on the top layer.
    * Routing: Achieved on a 2-layer board using a combination of top and bottom traces, with vias strategically placed to connect layers, manage
      signal remapping, and avoid trace crossings.
    * NOROM Logic Implementation: The adapter routes the relevant 2332 control signals (CS1, CS2) through the 74LS04 and 74LS32 gates to correctly
      drive the 2732's Chip Enable (overlineCE) pin. Unused inputs on the 74LS chips are tied directly to GND for stability.
    * Unused 74LS inputs are tied to ground

Bill of Materials (BOM)

| Designator | Qty | Part                                    | Footprint (KiCad)        | Description                       |
| :--------- | :-: | :-------------------------------------- | :----------------------- | :-------------------------------- |
| 2332       |  1  | 24-pin Pin Header (male)                 | PinHeader_2x12_DIP24_W15.24mm (custom) | To plug into 2332 socket        |
| 2732       |  1  | 24-pin DIP Socket                        | DIP-24_W15.24mm        | For 2732 EPROM                    |
| 74LS04     |  1  | 74LS04 Hex Inverter (14-pin DIP)         | DIP-14_W7.62mm         | Logic for NOROM                   |
| 74LS32     |  1  | 74LS32 Quad 2-input OR Gate (14-pin DIP) | DIP-14_W7.62mm         | Logic for NOROM                   |

License
This project is released under the GPL v3.0 License.

Acknowledgments

    The KiCad EDA Suite for excellent open-source PCB design tools.
    The vintage computing community for inspiring such projects.
