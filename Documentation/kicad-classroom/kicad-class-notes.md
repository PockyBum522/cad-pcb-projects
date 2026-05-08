# Download/Install KiCad 10

    - Start with no libraries

    - If you install a flatpak version, make sure to use Flatseal to enable read/write permissions for where you want to store projects/libraries
        

# Get Libraries:

    https://gitlab.com/kicad/libraries

    Good to redownload these libraries periodically as they're updated frequently. Old versions will still work, but you'll get new components.

    Download just symbols and footprints for now
    
    [Find out how to actually import symbol libraries and update]
    

# Schematic Editor Dark Theme:

    Startup screen > Plugin and content manager > Color themes tab > Install "Skyline" theme (Make sure to hit apply pending changes)

    You then have to set it in Preferences > Preferences > Schematic Editor > Colors 


# Overall Process:

    1. Start by making a schematic in the schematic editor, get that at least 95% done and ONLY THEN start working in the PCB editor
    
    2. No matter how simple your board is, if it has more than literally one single component, always make a schematic. YOU WILL HATE YOURSELF LATER IF YOU DO NOT. THIS IS THE VOICE OF EXPERIENCE SPEAKING.
    
    3. Symbol Editor = Schematic
       
       Footprint editor = PCB Editing
       
       You'll bounce around to these only as you can't find symbols or footprints you want to use. 
       
       You'll use them to make that symbol or footprint, and then go back to the schematic editor once you've finished making the symbol you needed, or the PCB editor once you finished making the footprint you needed. 

    4. Finally, you'll export gerber files and zip them and that's the file you'll give to your manufacturer. 
    
    [ 5. Note on being aware that drill files may need to be generated separately and added to the zip beyond what KiCad gives for gerber files.     ]


# The Project:

    https://docs.arduino.cc/retired/hacking/hardware/building-an-arduino-on-a-breadboard/


# Start by Making the Schematic:

    General Notes for Making Schematic:
    
        Package Size (giggity):
        
            I make it a habit of using 1206 components for everything I can possibly get in that size. Resistors, Capacitors, LEDs all come in this size. I do this for a few reasons:
            
                1. When I order components, I get extras, that way I know what I have on hand and have saved myself from having to make extra orders for components frequently.
                
                2. 1206 is a fairly large SMD package size, they're really easy to solder.
                
                3. If I screw up a component or trace, the pads are large enough to solder bodge wires to/I can swap out components with the same footprint
                
                4. I can just put down 1206 footprints for everything common, saving time having to look up the size of components I have. 
            
        Keep a list of the components you use frequently. It's nice to have part numbers handy when you need to order more or look up a datasheet. Just a text file is fine. 
        
        If you're going to make a lot of boards, order several hundred 10k resistors, 1k, 100k, etc. Same for filtering caps and I would suggest a few LEDs as well. I like green for power and blue for diagnostic, but use whatever you like. Green or red for power is fairly standard, though. Order a bunch of whatever resistors you need to use the LEDs you get on 3.3v, 5v, etc...
        
        
# Schematic by Component Order:

    Preferences > Manage Symbol Libraries 
        
        - Drop down arrow next to folder icon
        
        - "Folder with ".kicad_sym files"
        
        - Hit ok
        
        - If you have a personal symbol library or libraries (now or in the future) they'll need to be added here in the same way
        
    
    Place > Place Symbols to place a component. This does not cement the footprint as well, but sometimes picks a default one. You can change footprint later, just worry about symbol for now. 
    
    1. 7805 Voltage regulator
    
        1a. Look up what digi-key has for options

            - If you don't know what component category you're looking for, exactly, try searching and seeing what categories pop up at the top of the search. If you just want to filter by specifications, going into the category and then selecting filters is a good way to find components.

            - Type 7805 in search bar
            
            - Use Surface Mount filter options under mounting type
            
            - Find one with a bunch of stock at a good price
            
            - Place symbol
            
            - Double click on symbol to edit
            
            - Pick footprint, type in TO-363-3 to filter
            
            - Reference datasheet for pinout
            
            - Confirm symbol choice
            
            [ Getting the symbol correct is very important because it's what's going to be checking our PCB layout when we go to do that. Make absolutely sure pinout and footprint are right. ]
            
    2. Repeat the steps in 1a for *every other component*
    
    3. Note that you may have to create footprints for anything you can't find premde footprints for. This may also happen with symbols. More on that later.
    

# Place Every other component:
        
    1. 1206 LED
    
    2. Copy and paste 1206 LED. Note that it automatically increments the index. 

    3. Update value on both LEDs to indicate color.
    
    4. Place generic resistor
    
        4a. Add footprint
        
        4b. Add value
        
    5. Copy resistor after adding value and note it comes with the footprint and value when copied, but updates index.
    
    6. 10k Resistor - Just copy and only update value. See why the 1206 thing is nice?
    
    7. 10uf cap - Walk through filtering in digikey once more - check datasheet to see if polarized - or google
    
    8. Other 2 22pF caps, change value after adding footprint
    
    9. Crystal Oscillator - Filter by SMD, then frequency, then start looking at package options
    
        9a. Discuss hand-soldering and looking at datasheet for pin layouts
        
        9b. Can also just pick through-hole, just keep it to a minimum cause it's a pain when you go to assemble the board.
        
        9c. Spoiler - HC-49/US looks like the best balance of solderability and number of options. 
        
            9ca. Note you'll likely pay more for this. If you're making a ton of boards, consider reflow ovens/etc...
            
        9d. Look for hand solder options on footprints when doing so
        
    10. UART Header - Conn_01x06_Pin 
    
    11. Atmega328-P
    
    12. Momentary button
    
        12a. What happens when we have on-hand components that we don't know spec for? We...
        
    
# Make Symbols

    1. Open symbol editor
    
    2. New library
    
    3. I've just been making a library with all the custom components I use in one library, I'm sure it's better to organize them off into their own categories but it makes it really easy to re-use things in future projects.
    
    4. New symbol
    
    5. Name it
    
    6. https://en.wikipedia.org/wiki/Reference_designator
    
    7. Set reference letter and hit ok
    
    8. Add pins
    
    9. Draw graphic
    
    10. Position everything
    
    11. Save

    12. Go back to schematic editor

    13. Add to schematic
    
    14. Now how do we add the footprint for something we don't even know the model number of? We...
    

# Make Footprint

    1. Get out your calipers
    
    2. Open the footprint editor
    
    3. New library (Or add library if you've already made one) (May have to right click > New footprint on added library before it loads it properly.)
    
    4. New footprint
    
    5. Add pads
    
        5a. Measure legs, widest dimension, add some dimension for fit
        
        5b. Add pad dimension, 0.8 / 1.6 for this
        
    6. Measure leg spacing
    
    7. Place pads
    
    8. Check pad/pin numbers
    
    9. Think about what the graphic should be
    
    10. Does thing need polarization on graphic?
    
    11. Note that pins get the symbol labels assigned to the footprint automatically with pad numbers
                   

# Sometimes, you get lucky:

    - Manufacturers will sometimes give you footprints, symbols, 3D models, etc. 
    
    - Always Google the model/part number and "symbol" or "footprint" or "kicad" before making your own.     

    
# Get Wired:
    
    1. Move components around a bit to start
    
    2. Make necessary connections 
    
    3. Update footprint for UART board with new pins, retain numbers, just add labels
    
    4. When done, Inspect > Electrical Rules Checker
    
    
# Get Wired II, The Rewirening:

    In schematic editor Tool > Switch to PCB Editor
    
    Tools > Update PCB from Schematic
    
    [ Move everything around, discuss net lines and trying to get them somewhat organized ]
    


# Set up DRC/Board constraints:

    Get specifications from: https://jlcpcb.com/capabilities/pcb-capabilities (or whatever manufacturer you're using will have a similar page.)

    [ Make new screenshot ] 
    

# RUN DRC:    


# Export Gerbers:


# Walk through setting up JLCPCB Order


# BOM

    
# Closing Thoughts:

    Feel free to ask me if you are looking for something specific or starting a common project - I've done pi hats, ESP32 boards, etc. Happy to help. 
    
    Texting me is best way to contact me if you don't already have a standard method you talk to me with. 
