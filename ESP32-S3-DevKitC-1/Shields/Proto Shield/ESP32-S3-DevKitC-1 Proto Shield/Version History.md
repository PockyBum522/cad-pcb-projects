VER: 00.00.01
    * First order from JLCPCB on 2023-06-29 

VER: 00.00.02
    * Updated version screenprint
    * Centered letters in middle, indicating rows. They were not quite aligned vertically with each other or the center
    * Moved R3v3 to be at the end of rail to be consistent with others

VER: 00.00.03
    * Added trace screenprinting to top layer since traces themselves aren't super obvious
    * Widened space between headers as I mismeasured the ESP32 dev board
    * Due to the above line, added a middle column of pads with no traces to anywhere
    * Updated rev screenprint number
    * Added header H16 since board was widened
    * Added second column of A, B, C, D, etc... row identifiers
    * Added 09 column identifier to both sides
    * Moved GPIO id text to other side of the "set of two" connected pads
    * Moved Header text away from header pads so more visible when headers soldered on
    * Added regions encircling the GPIO labels and what coupled pads are associated with them to better define which are which

VER: 01.00.00
    * Switched to KiCad
    * Moved rails back one space so labels for GPIO pins have more room to be printed
    * Added RESET and BOOT switches
    * Added switch orientation silkscreening