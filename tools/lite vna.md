# Lite VNA

Actually LiteVNA 64-0.3.2
This is a tool to analyze antennas, it works by checking reflected signal. 

Measurement frequency: 50kHz - 6.3GHz
It's recommended to calibrate closest to the presumed frequency of your DUT (device under test). Having ±100MHz seems like a good place to start. You can also use a wide measurement range if you like to, but zooming in to a narrower view may be less accurate. 

Prior to calibration consider whether you will need a cable for your antenna or you're able to connect your DUT directly. 
If a cable is required, do the calibration with the cable attached. If you only need a protrusion to orifice converter you can and should calibrate without it. You will need three calibration SMAs from inside the LiteVNA box.  

Calibration for antenna measurement:
1. Turn on LiteVNA and connect the cable if necessary. 
2. Poke LiteVNA's screen to bring up the menu.
3. Poke Stimulus, and select either Start and Stop frequencies or Center frequency. 
4. Select Back ⇒ Calibrate ⇒ Reset ⇒ Calibrate
5. You should now be on the screen with OPEN, SHORT, LOAD, etc. 
6. Connect the Open SMA, the empty-hollow thingy, and press OPEN. 
7. Wait until a checkmark appears near OPEN.
8. Connect the Short SMA, the full-metal pin thingy, and press SHORT.
9. Wait until a checkmark appears near SHORT.
10. Connect the Load SMA, most closely resembling a normal antenna, and press LOAD. 
11. Wait until a checkmark appears near LOAD. 
12. You are done, pressing DONE will prompt you for a slot to save your calibration to. You can also save it to ram if you don't care much about your calibration. 

Calibration slots: 
Please do not save to the topmost slot 0. 

Slot0 10MHz - 3Ghz nowire
Slot1 91Mhz - 959Mhz yeswire

To Select one of these slots find the RECALL menu option. 


Heres how to measure stuff with it:
1. It is recommended 
2. b
3. ???
4. PROPHET


Heres how to read the lines and stuff:
example picture
lines meaning
