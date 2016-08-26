% Habits
% John Doe
% March 22, 2005
 

# What do we do?
 
## What is it?

__Creating modules to facilitate ultrasound hacking__ : the principles of the echOmods is to enable a full chain of ultrasound image processing and hardware control.

We have chosen to use a module approach to make sure that each key component inside ultrasound image processing can easily be replaced and compared with another module, while providing logical _logic blocks_ and corresponding interfaces for these modules to communicate. There's a module for [high-voltage pulsing](/tobo/), one for the [transducer](/retroATL3/), one for the [analog processing](/goblin/), one for [data acquisiton](/toadkiller/), ... and many more!

These modules can have a form factor close to classical breadboard electronic modules, with a row of 19 pins on the side.

Key interfaces, signals and alims will be available on each of the 19 tracks on the motherboard, and will enable communication between modules. However, some tracks can be unused by the modules. 


## What does it look like?

The modules sit on a breadboard, and communicate through the tracks laying below. The configuration represented below show the Basic dev kit.

![](/include/20160814/IMG_3430.png)

## What does it cost?

Even with the most expensive options, the basic kit, we're still below 500$.

Some stuff, unexpensive to buy, to build a ultrasound testing kit, totals _500$_, as detailed below:

* A power supply giving 3.3V and 5V ([mogaba](/mogaba/)) -- _5$_
* An analog processing ([goblin](/goblin/)) -- _130$_
* A high voltage pulser ([tobo](/tobo/)) -- _110$_
* A motherboard ([doj](/doj/)) made out of stripboard  -- _10$_
* A pulser ([oneeye](/oneeye/)) from a trinket pro  -- _20$_
* An old ATL probe ([retroATL3](/retroATL3/)) -- _75$_
* A beaglebone and PRUDAQ ([toadkiller](/toadkiller/)) -- _150$_

Need one of the custom boards? Message me at kelu124@gmail.com !


 
# Graphing the modules
 

# The modules organization 

![Graph](/include/sets/basic.png) 

 
# Table Docs
# A recap of our modules 


| ThumbnailImage | Name | In | Out |
|------|-------|----|------|
|<img src='https://github.com/kelu124/echomods/blob/master/sleepy/viewme.png' align='center' width='150'>|**[sleepy](/sleepy/Readme.md)**: The aim of this echOmod is to encase the whole modules object in a neat case, making it transportable.|||
|<img src='https://github.com/kelu124/echomods/blob/master/tobo/viewme.png' align='center' width='150'>|**[tobo](/tobo/Readme.md)**: The aim of this echOmod is to get the HV Pulse done.|<ul><li>ITF-A_gnd</li><li>ITF-B_5v</li><li>ITF-I_pulse_on</li><li>ITF-J_pulse_off</li><li>ITF-S_3_3v</li><li>ITF-mET_Transducer</li></ul>|<ul><li>ITF-R_reserved</li><li>ITF-mET_SMA</li><li>ITF-mET_Transducer</li></ul>|
|<img src='https://github.com/kelu124/echomods/blob/master/cletus/viewme.png' align='center' width='150'>|**[cletus](/cletus/Readme.md)**: The aim of this module is to interface the transducer and the servo, aka the physical parts, to the analog part of the modules chain.|<ul><li>ITF-A_gnd</li><li>ITF-B_5v</li><li>ITF-N_cc_motor_pwm</li><li>ITF-S_3_3v</li><li>ITF-mET_Transducer</li><li>ITF-mET_Piezo</li></ul>|<ul><li>ITF-mET_Piezo</li><li>ITF-mET_Transducer</li></ul>|
|<img src='https://github.com/kelu124/echomods/blob/master/doj/viewme.png' align='center' width='150'>|**[doj](/doj/Readme.md)**: Getting a motherboard: that's fitting all the modules in an easy way, with an easy access to all tracks.|||
|<img src='https://github.com/kelu124/echomods/blob/master/oneeye/viewme.png' align='center' width='150'>|**[oneeye](/oneeye/Readme.md)**: The module aims at making a microcontroler, for the moment the <code>ArduinoTrinketPro</code>, usable with the motherboard and the set of modules.|<ul><li>ITF-A_gnd</li><li>ITF-B_5v</li><li>ITF-S_3_3v</li></ul>|<ul><li>ITF-G_gain_control</li><li>ITF-I_pulse_on</li><li>ITF-J_pulse_off</li><li>ITF-N_cc_motor_pwm</li></ul>|
|<img src='https://github.com/kelu124/echomods/blob/master/croaker/viewme.png' align='center' width='150'>|**[croaker](/croaker/Readme.md)**: The aim of this echOmod is to receive the signal and process it.|<ul><li>ITF-A_gnd</li><li>ITF-B_5v</li><li>ITF-mEG_SPI</li></ul>|<ul><li>ITF-mED-TFT-Screen</li><li>ITF-mEC-WiFi-UDP-Stream</li><li>ITF-I_pulse_on</li><li>ITF-J_pulse_off</li></ul>|
|<img src='https://github.com/kelu124/echomods/blob/master/retroATL3/viewme.png' align='center' width='150'>|**[retroATL3](/retroATL3/Readme.md)**: The aim of this echOmod is to get the mechanical movement of the piezos. Salvaged from a former ATL3.|<ul><li>ITF-A_gnd</li><li>ITF-F_12V</li><li>ITF-N_cc_motor_pwm</li><li>ITF-mET_Transducer</li><li>Motor</li><li>Tri-Piezo Head</li></ul>|<ul><li>Motor</li><li>ITF-mET_Transducer</li><li>Tri-Piezo Head</li></ul>|
|<img src='https://github.com/kelu124/echomods/blob/master/toadkiller/viewme.png' align='center' width='150'>|**[toadkiller](/toadkiller/Readme.md)**: The aim of this echOmod is to simulate the enveloppe (or maybe soon the raw signal) that would come from the piezo and analog chain.|<ul><li>ITF-A_gnd</li><li>ITF-B_5v</li><li>ITF-S_3_3v</li><li>ITF-E_signal_envelope</li></ul>|<ul><li>WiFi UDP Stream</li><li>ITF-mED-TFT-Screen</li><li>ITF-I_pulse_on</li><li>ITF-J_pulse_off</li><li>ITF-N_cc_motor_pwm</li></ul>|
|<img src='https://github.com/kelu124/echomods/blob/master/kina/viewme.png' align='center' width='150'>|**[kina](/kina/Readme.md)**: The aim of this echOmod is to acquire the enveloppe of the signal and stream it. Designed for slow (~64 lines / s) acquisitions.|<ul><li>ITF-A_gnd</li><li>ITF-B_5v</li><li>ITF-S_3_3v</li><li>ITF-E_signal_envelope</li><li>ITF-I_pulse_on</li></ul>|<ul><li>ITF-mEC-WiFi-UDP-Stream</li><li>ITF-mED-TFT-Screen</li><li>ITF-I_pulse_on</li><li>ITF-J_pulse_off</li><li>ITF-N_cc_motor_pwm</li></ul>|
|<img src='https://github.com/kelu124/echomods/blob/master/goblin/viewme.png' align='center' width='150'>|**[goblin](/goblin/Readme.md)**: The aim of this echOmod is to get the signal coming back from a transducer, and to deliver the signal, analogically processed, with all steps accessible to hackers. |<ul><li>ITF-A_gnd</li><li>ITF-B_5v</li><li>ITF-S_3_3v</li><li>ITF-G_gain_control</li><li>ITF-C_amplified_raw_signal</li><li>ITF-E_signal_envelope</li><li>ITF-R_reserved</li><li>ITF-mET_SMA</li></ul>|<ul><li>ITF-C_amplified_raw_signal</li><li>ITF-E_signal_envelope</li><li>ITF-mEG_SPI</li></ul>|
|<img src='https://github.com/kelu124/echomods/blob/master/silent/viewme.png' align='center' width='150'>|**[silent](/silent/Readme.md)**: The aim of this echOmod is to simulate a raw signal that would come from the piezo and analog chain.|<ul><li>ITF-A_gnd</li><li>ITF-B_5v</li><li>ITF-J_pulse_off</li></ul>|<ul><li>ITF-R_reserved</li></ul>|
|<img src='https://github.com/kelu124/echomods/blob/master/mogaba/viewme.png' align='center' width='150'>|**[mogaba](/mogaba/Readme.md)**: The aim of this echOmod is to get 3.3V and 5V done.|<ul><li>ITF-mEM_Alimentation</li><li>ITF-F_12V</li></ul>|<ul><li>ITF-A_gnd</li><li>ITF-B_5v</li><li>ITF-F_12V</li><li>ITF-S_3_3v</li></ul>|



# Progress
 
# Progress on building the modules 


Note that the 'BONUS!' represents something that _could_ be done, and does not count as a strict TODO.


| Name of module | ToDo | Done |  Progress |
|------|-------|----|-----|
|sleepy|<ul><li>Choose the design once the modules are done</li><li>Get to work with Arthur</li></ul>|<ul><li>Checking Arthur availability</li></ul>|33% |
|tobo|<ul><li>Publish the sources in KiCAD</li></ul>|<ul><li>Writing specs </li><li>Sending microcircuits to Edgeflex</li><li>Agreeing on the strips/tracks </li><li>Defining the ICs to use to pulse</li><li>Getting schematics</li><li>Publishing schematics</li><li>Receive the module</li><li>Test it with different transducers</li></ul>|88% |
|cletus|<ul><li>Choose the servo (&gt;100Hz)</li><li>Do the structure of the holder (3D design?)</li></ul>|<ul><li>Get a 3.5MHz piezo</li></ul>|33% |
|doj||<ul><li>Having the list of strips accessible</li><li>Design</li><li>Assemble it</li><li>Test it</li></ul>|100% |
|oneeye||<ul><li>First test with Arduino Trinket</li></ul>|100% |
|croaker|<ul><li>Getting some PRU code</li><li>Getting some images</li><li>Getting images onto a screen</li><li>Replace the work done by <a href="/oneeye/">OneEye</a> by <a href="/croaker/">Croaker</a>.</li></ul>|<ul><li>Choose the platform (BBB, RPi0, STM32, ... ?) : that'll be BBB</li></ul>|20% |
|retroATL3|<ul><li><em>BONUS!</em> Get RealTime acquisition</li><li>Acquire and build ultrasound pictures =)</li></ul>|<ul><li>Finding the pins mapping</li><li>Motor in action</li><li>Refill Oil</li><li>Test echoes</li><li><a href="https://hackaday.io/project/9281-murgen-open-source-ultrasound-imaging/log/42113-testing-murgen-with-a-market-probe">Make and insert a video: there</a></li></ul>|83% |
|toadkiller|<ul><li>Do the quick check up</li></ul>|<ul><li>Nothing</li></ul>|50% |
|kina|<ul><li>Get the code up and running</li><li>Try to get the pulser there as well (timers)</li><li>Get several samples per position to average then stream</li><li>Output data to a 128x64 OLED screen</li></ul>|<ul><li>TODO</li></ul>|20% |
|goblin|<ul><li><em>BONUS!</em> Plug it to a <a href="/croaker/">RPi0 or BBB or RPi</a> or else.</li><li><em>BONUS!</em> or test it with the <a href="/kina/">EMW3165</a>.</li><li>Publish the sources in KiCAD (@Sofian maybe?)</li></ul>|<ul><li>Check the power consumption</li><li>Specs to write</li><li>Agreeing on the strips </li><li>Check if 5V and 3.3V are stable</li><li>Defining the ICs to use</li><li>Getting schematics</li><li>Send microcircuits to Edgeflex</li><li>Receive the module</li></ul>|88% |
|silent||<ul><li>Feather: <a href="/silent/software/featherWICED/SignalGenerator.ino">work with an interrupt</a></li><li>Write code for feather WICED</li><li>Publish this code</li><li>Remove Signal Bias</li><li>Validated with a Feather WICED (<a href="/silent/software/featherWICED/SimpleSignalGenerator.ino">code</a>).</li><li>Feather: remove the average value before inputing in Goblin</li><li><a href="/silent/2016-08-09 SilentPlusTobo.md">Check output with Goblin</a></li></ul>|100% |
|mogaba|<ul><li><em>BONUS!</em> benchmark power supplies </li></ul>|<ul><li>Manage to feed it 12V</li><li>Bring power to it through the 12V <code>ITF-F_12V</code> track </li><li>Test if 12V OK</li><li>Find supplier</li></ul>|100% |