<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

 Set a code for your precious safe!
    **Controls**
    * Switch 2 is used to reset the safe. 
    * Switch 8 is used to set your code (ON = set, OFF = locked)
    * Switches 3 to 5 are used to set the code.
    * The push button is used to enter your code.

## How to test

Press the green button in the top left of the pane to begin the simulation.
    Set your desired code using Switches 3 to 5. Once you've done so, toggle Switch 8 to ON then back OFF--the safe is now set!
    Turn ON Switch 2, and press the push button. The red LED labeled "Locked" should turn on and the seven segment display should show "L" (for locked).
    Next turn OFF Switch 2 to begin entering codes.  

    # Customizable padlock test run 
Inputs are in the left-side column, expected outputs on the right, specified 
as MSB.  Any bits specified as 'x' or '-' are treated as "don't change" for 
inputs and "don't care" for outputs.  "c" bits are treated a clocks, such that
changing a bit, say, to 1 on some line with a clock will:
  * apply any changes to inputs;
  * then toggle the clock bit(s); and finally 
  * toggle the clock bit(s) again, returning them to their original state.


The header is ignored, as are whitespaces, so you may format as appropriate.

Here we have PRG bit to enable programing, 3 bits in "COMBO" 
and finally reset and clock bits.  

The output is the 7-segment "L" or "U" display.

We start by setting combination to 1 1 0 (MSB), try that out, then re-program
to 0 0 1, and confirm that works.


|RC| PRG  xx  COMBO  Rx  |    7-segment    |       comment           |
|--|---------------------|-----------------|-------------------------|
|00|  0   00   000   00  |   -- ----- -    | start with hard reset   |
|1c|  x   xx   xxx   xx  |   -- ----- -    | enable system           |
|xc|  x   xx   xxx   1x  |   -- ----- -    | lock it                 |
|xc|  1   xx   110   0x  |   -- ----- -    | program w/110 combo     |
|xc|  0   xx   xxx   1x  |   -- ----- -    | lock it                 |
|xc|  x   xx   111   0x  |   -- 11100 -    | try a bad combo         |
|xc|  x   xx   001   xx  |   -- 11100 -    | another bad combo       |
|xc|  x   xx   110   xx  |   -- 11111 -    | the right combo         |
|xc|  x   xx   000   xx  |   -- 11111 -    | bad but still unlocked  |
|xc|  x   xx   xxx   1x  |   -- ----- -    | lock it                 |
|xc|  x   xx   xxx   0x  |   -- 11100 -    | now locked again        |
|xc|  1   xx   001   xx  |   -- ----- -    | program w/001 combo     |
|xc|  0   xx   xxx   1x  |   -- ----- -    | lock it                 |
|xc|  x   xx   100   0x  |   -- 11100 -    | try a bad combo         |
|xc|  x   xx   001   xx  |   -- 11111 -    | the new combo, unlocks  |




## External hardware

LEDs, pushbuttons, 7seg display i think.

