# Preliminary notes for low frequency resonator  

I am looking into low frequency (100 ~ 200 kHz) resonators to:   
* Extend range of Low frequency NFC chips, 125kHz  
* Extend range and increase efficiency [1] of [Qi charging](https://en.wikipedia.org/wiki/Qi_(standard)), starting at 140KHz but might need wider operating range to support different devices.  

## Theory for wireless charging  
In poor coupling scenarios (e.g. far away or misaligned), an intermediate coil can improve both power transfer and efficiency, but if coupling is already good an intermediate coil can hurt both [2].  

The position of the intermediate coil is important. The transfer power seems to be best halfway between TX (primary) and RX (secondary) if TX and RX are symmetric, but if TX and RX are assymetrical it is best to have the intermediate coil closer to the smaller of TX and RX [3].  

[1] https://ieeexplore.ieee.org/document/6717985  
[2] https://www.researchgate.net/publication/320824277_Effects_of_intermediate_coil_on_power_transfer_capability_and_efficiency_in_three-coil_wireless_power_transfer_system  
[3] https://arxiv.org/pdf/2012.00244  

**More studies**  
Four coil system found the coils should be symmetrically spaced if all coils are the same geometry: https://www.mdpi.com/1996-1073/12/20/3991  
Exploration of geometry of intermediate coil when close to primary: https://ieeexplore.ieee.org/document/8702173  

## Existing products  
13.56Mhz Resonant Repeater for extending range of NFC chips:  
https://github.com/Hamspiced/NFC-Resonant-Frequency-Amplifier/  

Dual frequency field detector: https://github.com/exploitagency/RFID-Field-Detector  
This has an antenna to detect the low frequency. An easy starting point would be to copy that antenna on a thin pcb, and put in a capacitor instead of the LEDs. The optimal size might be different (see equivalent circuit in [1]) but it might work well enough to base a testing board off of it.  

## Product Vision for Qi extender  
My phone gets hot while wirelessly charging, and I think it would be cool to have something in my case to increase the efficiency of wireless charging. Ideally this would fit as a sticker small enough to go on the back of a phone case. Something like the V3 of Hamspiced Repeater.
Potential challenges:  
* Larger inductance and capacitance values are required, but there is also more space to work with.  
* Qi charging starts at 140 kHz, but changes frequency between 105-205 kHz to find the best match. This means there might not be a one-size-fits-all solution as different phone recievers might have different resonant frequencies. A deeper look at the specification is required here.  
* <a href="https://en.wikipedia.org/wiki/Qi_(standard)#Transmitters">maximum resonant circuit voltages as high as 200 volts.</a>
