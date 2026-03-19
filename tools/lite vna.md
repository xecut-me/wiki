# Lite VNA

Actually LiteVNA 64-0.3.2  
Measurement frequency: 50kHz - 6.3GHz  
This is a tool to analyze antennas, it works by checking reflected signal.  

It's recommended to calibrate closest to the presumed frequency of your DUT (device under test). Having ±100MHz seems like a good place to start. You can try using a wide measurement range, but the results may be very inaccurate and at times useless. 

Prior to calibration consider whether you will need a cable for your antenna or you're able to connect your DUT directly to port S11. 
If a cable is required, do the calibration with the cable attached. Anything you connect to the VNA affects the measurements. You will need three calibration SMAs from inside the LiteVNA box.  

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


### Here's how to
#### Check antenna TX quickly: 
SWR / return loss is good when you need to check TX. 
You can use it to guesstimate the quality RX as well, but when receiving signal strength and signal-to-noise are more important. Any way to test those other than a real world test? 
- If your SWR is over 3 you probably don't want to use this antenna at this frequency to transmit >25% of power is returned back to transmitter
- If your SWR is under 2 your antenna is ok, about ~10% is returned back to the transmitter
- If your SWR is <1.5 your antenna is good, and the closer it gets to 1 the more amazing it is

#### Check antenna TX slowly:
Smith Chart:
The central horizontal line is from short on the left, to open on the right, with 50 Ohms in the center.  
50 Ohms is teh standard, standards are good  
Top part of the chart is inductance  
Bottom part is capacitance  

- You want the point you got at the selected frequency to be as close to the fucking center as possible

Also, if you know a lot you can tell us how to tune antennas 

// todo: add example pictures
