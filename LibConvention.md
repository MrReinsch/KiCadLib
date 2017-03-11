# Kicad Library Convention

Copy from: https://github.com/KiCad/kicad-library.wiki.git

Revision 1.1, October 1st 2016  
Devised by Carl Poirier  
With help from members of:
kicad-lib-committers 
kicad-developers

1. General Rules

Writing uses C-style naming with the first letter of each word being capitalized. Ex: "Socket_Strip_Straight_2x06"
Every acronym has all of its letters capitalized.
Manufacturer name is capitalized as usual. Ex: NEC, Microchip.
When dimensions are used in part name, they are in millimeters, decimal places separated by a dot, and unit is not mentioned. Ex:  "C_Rect_L13_W4_P10"
Filename is the same as the part name.
The order of elements in names must be the same as the enumerations presented in this document.
Reference fields are prefilled with the reference designator of the part (IEEE 315-1975).
Symbol Libraries

2. Symbol Library Names (.lib files)

Manufacturer.
Category or family of parts. ex: "Capacitors", "Spartan6", etc.
3. General Rules for Symbols

Using a 100mil grid, pin ends and origin must lie on grid nodes (IEC-60617).
For black-box symbols, pins have a length of 100mils. Large pin numbers can be accomodated by incrementing the length in steps of 50mils.
Origin is placed in the middle of symbol.
Black-box components group pins logically, for example by function set, and ports in counter-clockwise position.
Whenever possible, inputs are on the left and outputs are on the right.
Field text uses a common size of 50mils.
The Value field is prefilled with the object name.
Description and keywords properties contain the relevant information.
For components with a single default footprint, footprint field is filled with valid entry of the format "Footprint_Library:Footprint_Name" and is set to invisible.
4. Symbol Names

Name of symbol, may be shortened for common components or use reference designator of the symbol (IEEE 315-1975). ex: "Conn_4x2", "C", etc.
Manufacturer.
Part number, including extension for specific footprint (JEDEC for common devices, ex: 1N4001).
Any modification to the original symbol, indicated by appending the reason. Ex: different pin ordering: "Transistor_PNP_Pinswap1".
Indication of quantity if symbol is an array. Ex: resistor array: "Resistor_x8".
Footprint Libraries

5. Footprint Library Names (.pretty repositories)

Part type (resistor, cap, etc), must be in plural form.
Package type (SOIC, SMD, etc).
Manufacturer.
Part number.
6. General Rules for Footprints

Follows datasheet recommendation unless intentional variation, for example longer pads for hand soldering.
Pad 1 is on the left first, then at the top, except at the top for PLCC (IPC-7351).
For through-hole components, footprint anchor is set on pad 1.
For surface-mount devices, footprint anchor is placed in the middle with respect to device lead ends (IPC-7351).
Silkscreen is not superposed to pads, its outline is completely visible after board assembly, uses 0.12mm line width and provides a reference mark for pin 1 (IPC-7351C).
Courtyard line has a width 0.05mm. This line is placed so that its clearance is measured from its center to the edges of pads and body, and its position is rounded on a grid of 0.01mm.
Courtyard clearance is 0.25mm except for components smaller than 0603 at 0.15mm, connectors, SMD canned capacitors and crystals at 0.5mm and BGA at 1.0mm. (IPC-7251, IPC-7351B)
Cannot be duplicated to match a different pin ordering. This is to be handled in the symbol libraries.
Fabrication layer contains an outline of the part using a 0.10mm line width.  
7. Names for footprints of Surface-Mount Devices (SMD)

Specific package feature first, not separated by anything. Ex: "TSSOP".
Package name, numbers separated from letters using hyphen. Ex: "SOT-89".
Variation of package, separated by another hyphen. Ex: SOT-23 with 5 pins: "SOT-23-5", Exposed pad under package: "QFP-48-1EP".
If it's a manufacturer-specific package, name can be appended, separated by an underscore.
Any modification to the original footprint, indicated by appending the reason. Ex: longer pads used to facilitate hand soldering of a QFN component: "QFN-52_HandSoldering".
8. Names for footprints of common devices, such as resistors, capacitors, etc

Name of part, may be shortened for common components. ex: "Cap", "Socket_Strip", etc.
Dimension, which may include at its end the positioning. Ex: "5x7mm_Horiz", "1x02_Angled".
Pad distance, in the form of an RM rating.
Any modification to the original footprint, indicated by appending the reason.
9. Names for footprints of specific devices

Name of part.
Part number. Ex: "Oscillator_SI570"
Any modification to the original footprint, indicated by appending the reason.
10. Footprint properties

Footprint name must match its filename. (.kicad_mod files)
Doc property contains a full description of footprint.
Keywords are separated by spaces.
Value has a height of 1.0mm, is filled with footprint name and is placed on the fabrication layer.
Reference designator has a height of 2.0mm or smaller if needed and is placed on the fabrication layer.
Attributes is set to the appropriate value, see tooltip for more information.
All other properties are left to default values. (Move and Place: Free; Auto Place: 0 and 0, Local Clearance Values: 0)
3D Shape ".wrl" files are named the same as their footprint and are placed in a folder named the same as the footprint library replacing the ".pretty" with ".3dshapes". Variations of the same footprint can refer to the same 3D model and thus violate this rule.
e.g. No requirement to have a separate 3D model for a _HandSoldering version of the same footprint
