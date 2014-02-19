Ice-Tube-Clock
==============

Ice Tube Clock - PhilD13

This is my working directory fork of the icetube clock from Adafruit that will incorporate various board changes and component updates as 
I learn more about Eagle Cad.


The working directory is where the latest working files are located. 

Transistor version of main board is a modified version of the Adafruit main board. Some components and traces have been moved around to 
accommodate the use of a 2N2907 transistor for Q3 and the R6 1K resistor that is required for the transistor. Of course, the transistor version can be used 
with a FET by replacing R6 with a jumper

Schematic and Part Changes
1.) Change the ATmega168V-10PU to a ATMEGA328P-PU-ND to provide memory space for the use of the  xmas-icetube firmware by John Archie.
		See: https://github.com/johngarchie/xmas-icetube/

2.) Change value of R3 from 22 ohm to 11 ohm. The 11 ohm resistor can also be changed to a jumper wire if desired to help correct dim digits.
		See: http://forums.adafruit.com/viewtopic.php?f=41&t=39298&p=203372&hilit=11+ohm#p203372
	and
		http://forums.adafruit.com/viewtopic.php?p=179107#p179107

3.) Change values of C8 and C9 from 20pf to 10pf for better timekeeping. 
		See: http://forums.adafruit.com/viewtopic.php?p=189366#p189366

4.) Change Q3/Q4 from ZVP3306A FET to a ZVP2110A (still P-channel) so mount matching board silk screen 
		See: http://forums.adafruit.com/viewtopic.php?f=41&t=39298&p=203372&hilit=ZVP2110#p203372

5.) Changed Q3 to a 2N2907 transistor/ 1K resistor combo in transistor version of board. Can use a jumper and FET if desired. Board will 
accommodate either one. 

Tips:
The Ice Cube Clock will blink the display after a power loss. This is normal and acts like most other commercial clocks to warn of a potential 
time loss due to a power loss. Toggle through the Menu options to stop the blinking.
- This how it's supposed to work anytime the clock senses a loss of power and is not an indication of the FET being installed backwards 
or some other problem. 

The FET Q3 is designed into the clock as a high side switch to disconnect the voltage from the tube filament (bias) and the voltage (VCC) 
from the MAX6921 VFD drive chip in the event of a loss of normal input voltage. This leaves only the ATMEGA328P-PU-ND processor powered by 
the battery and a good battery can power the processor for at least a couple weeks.

The Q3 FET will still work if it is installed backwards. The clock will still work and display time just fine. Due to how a FET is 
constructed, the FET will not fully turn off if it is reversed in the circuit and will still pass current which will cause the battery to quickly die

So, if the clock does not keep time while only on battery power then the FET Q3 is probably installed backwards causing it to not turn 
off properly when power is removed.

I have found that the current ZVP3306A (from Diodes Inc.) p-channel enhancement mode FET supplied for Q3 has the correct orientation when 
installed with the rounded side with writing on it facing the rounded side of the silkscreen outline on the board as in the photo below. 
This orientation also matches the schematic for the clock. 
This is contrary to the assembly instructions. http://learn.adafruit.com/ice-tube-clock-kit/board-assembly
See this thread for more information: http://www.adafruit.com/forums/viewtopic.php?f=41&t=43209

The clock when first built and powered on has the brightness defaulted (is set) to the dimmest setting making it very hard to see
to set in normal room brightness. Turn the room lights out.

On the Adafruit firmware, the Brightness setting is the 4th menu in. Press the Menu button 4 times, then press the + button 2 or 3 times to set brightness higher
before trying to set other options. This makes it much easier to read the clock while initially setting and getting used to the menus 
and can be adjusted later as desired.

When installing the buttons on the board, make sure to get all of the buttons flat to the circuit board and keep them flat while soldering 
them in place. If the buttons are not flat to the circuit board, their black stems won't fit properly through the case holes and may stick 
in when pressed, so pay close attention to that detail. If they do get soldered in not quite flat then you may need to make the button 
holes in the case back slightly larger. Use care, the proper size drill bit (one size larger than the hole is good) in a battery drill, 
go slow and drill from both sides of the hole or the plastic may break.

Identify the tube you have
	There are 22 holes in the Tubes PC board for tube wires.
	Count the wires on the tube. Some tubes have 19 wires and some tubes may have 22 wires (three are not connected inside of tube in that case). 
	
	If the tube has 19 wires, the wire spacing will be different and you'll see two wires that seem 'farther apart' than the others. 
	Begin by threading those two front wires into the PC board so that they straddle the 3 NC (not connected) pins. 
	
	If the tube has 22 wires, then the wire spacing will be even all around the tube and you will see three non-connected pins inside the glass tube.
		Thread the three non-connected wires, so they pass through the holes marked "Display NC" (not connected).
 
	For both tube types, pass the remaining wires through so they pass straight through and are not crossed or bent.
	Pass the wires into the holes only a little way and bend wire over. After all the wires are inserted in their proper holes, then begin working 
	the tube board down towards the base of the tube.
 
Allow plenty of time to fit the tube to the circuit board it mounts on and be patient. 
	Tweezers and a small pair of needle nose pliers can help straighten any wires and assist in getting them through the holes. 
	Don't try to force any wires through their holes. 
	Inserting each wire a little ways into its corresponding hole, then bending the wires end over so it will stay in the hole
	makes it easier to maneuver the tube and board while inserting wires.
	Once all the wires are in their proper holes, begin moving the PC board up the wires toward the tube end. Use fingers, tweezers, 
	and needle nose pliers as necessary to assist in sliding the PC board into proper position.

Check the fit of the tube in the case before soldering. 
	Do this by mounting the case base plate (with the setting instructions) to 
	the main PC board. Then assemble the back side and the left side case panels to the base plate and adjust the position as needed.
	A distance of about 4 - 6 mm between the glass tube end and the PC board front should be a good position. Check that the tubes 
	PC board sits flush in the female header when the tube is in the case.
	
Tack the tube in place
	Once the wiring of the tube to the PC board is verified to be correct, there are no crossed wires, no shorted wires, 
	and the tube distance is proper  Solder tack two upper and two lower wires to hold the tube in place on the PC board.
	Remove the tube from the case and header. Solder all the wires and trim very close to PC board so everything fits 
	properly when the case is assembled. 	
	
	
Data Sheet Links and ETC.
	ATMEGA328P-PU-ND DigiKey part: http://www.digikey.com/product-detail/en/ATMEGA328P-PU/ATMEGA328P-PU-ND/1914589
	ATMEGA328P-PU-ND Data sheet: http://www.atmel.com/Images/Atmel-8271-8-bit-AVR-Microcontroller-ATmega48A-48PA-88A-88PA-168A-168PA-328-328P_datasheet.pdf
	
	FET ZVP2110A DigiKey part: http://www.digikey.com/product-detail/en/ZVP2110A/ZVP2110A-ND/92620
	FET ZVP2110A Data Sheet: http://www.diodes.com/datasheets/ZVP2110A.pdf
	
	MAX6921AQI+-ND DigiKey part: http://www.digikey.com/product-detail/en/MAX6921AQI%2B/MAX6921AQI%2B-ND/1512036
	MAX6921AQI+-ND Data Sheet: http://datasheets.maximintegrated.com/en/ds/MAX6921-MAX6931.pdf
	
	IRFD110PBF-ND DigiKey part: http://www.digikey.com/product-detail/en/IRFD110PBF/IRFD110PBF-ND/812472
	IRFD110PBF-ND Data Sheet: http://www.vishay.com/doc?91127

Older parts for reference:	
	ATMEGA168V-10PU-ND DigiKey part: http://www.digikey.com/product-detail/en/ATMEGA168V-10PU/ATMEGA168V-10PU-ND/735447
	ATMEGA168V-10PU-ND http://www.atmel.com/Images/doc2545.pdf
	
	FET ZVP3306A DigiKey part: http://www.digikey.com/product-detail/en/ZVP3306A/ZVP3306A-ND/92625
	FET ZVP3306A Data Sheet: http://www.diodes.com/datasheets/ZVP3306A.pdf
	
	Original Ice Tube Clock board and schematic, firmware: https://github.com/adafruit/Ice-Tube-Clock

Firmware:	
	Really Good Firmware: https://github.com/johngarchie/xmas-icetube/