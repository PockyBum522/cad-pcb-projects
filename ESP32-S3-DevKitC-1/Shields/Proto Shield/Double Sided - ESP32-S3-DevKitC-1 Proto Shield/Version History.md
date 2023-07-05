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

To consider:
    * Making 3 columns of A, B, C etc indicators, as that would potentially make it more obvious which pads are *not* connected to MCU pins. This may not be needed once headers are soldered in, it might be obvious