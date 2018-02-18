
[](@description Using a Raspberry Pi to image)

## Introduction

This project has a specific target of providing a __low-cost, open source technological kit to allow scientists, academics, hackers, makers or OSHW fans to hack their way to ultrasound imaging__ - below 500$ - at home, with no specific equipment required. 

### Objective

The aim of this project is to build a small ultrasound imaging hardware and software development kit, with the specific goal of:

- building an _analog "debugging tool"_ to explore ultrasound imaging systems. 
- consolidating [existing hardware research](http://openhardware.metajnl.com/articles/10.5334/joh.2/);
- simplifing / lowering the cost of the kit;
- providing a benchmark of ultrasound systems;
- introducing a simple API to control hardware;
- having a server which provides raw ultrasound data, and for ultrasound imaging, can deliver standard DICOM files;
- having a kit that can be used for pedagogical and academic purposes - not to mention people who want to understand ultrasound!

Previous project has shown the feasibility of the hardware, but was not simple enough. Let's keep the momentum, and use this dev kit in other projects as well - such as dopplers or non-destructive testing, different projects using piezos as sensors.

## Architecture

Ultrasound imaging has evolved since the first ultrasound machine appeared. The first devices were using single-sensor (transducers) techniques, coupled with mechanical scanning - hence allowing a single signal processing channel. The architecture of such systems, as shown below, is well-known and formed the basis of ultrasound imaging.


![](http://openhardware.metajnl.com/articles/10.5334/joh.2/joh-1-2-g1.png/?action=download)


This kit consists of several modules mainly built from easily available components - after a short benchmark of [existing ICs](https://kelu124.gitbooks.io/echomods/content/Chapter6/bench.html). Two electronic modules were specifically designed to provide the basic development kit. 

* the __Transducer Pulser Module (TPM)__: designed to provide a precise high-voltage pulse, necessary to excite the sensor, while remaining robust enough to be controlled by an Arduino;
* the __Analog Processing Module (APM)__: designed to correctly process the raw ultrasound electric signal, while easily exposing all intermediary signals, and exposing a digital output to the user
* the __RPi high-speed ADC__ uses two interleaved AD9200, clocked with the RPi, which reads at 11Msps, leading to an effective 22Msps acquisition speed (bottleneck being the RPi copying the ADC values through the GPIOs register to RAM). The signals can be read as is (eg in case of analog enveloppe detection) or offset by Vref/2 (to acquire the raw signal). Due to the GPIO necessary to run the modules, we are left with 2x9 GPIO left, resulting in a 22Msps, 9 bit ADC. One or two logic signals can additionaly be sampled - for an external motor hall sensor for example.

A modular approach was chosen to ensure that each key component inside the ultrasound image processing can easily be replaced and compared with another module. Each electronic module takes the place of a function in the signal processing chain or allows tapping into the different signals circulating between the blocks. 

Previous experiments have been done, to get images using different digital acquisition systems, such as a bitscope, a STM32, or a high-speed ADC for beaglebone. The Raspberry Pi was retained in the end for its ease of use, its price, and community working on it - increasing the potential reach of the project. 

## Assembly guide 

### Required materials

* A [pulser board](/tobo/) - to generate the high voltage pulse to use the transducer
* An [analog front end](/goblin/) - to amplify the weak signals generated by the echoes
* an [ADC cape](/elmo/) - a custom made 11Msps to 22Msps ADC pHAT for Raspberries.
* a [Raspberry Pi, 0 or W](/tomtom/) to manage everything
* the [motherboard, v2](/doj/) - to connect the different modules together
* and some extras such as headers, jumpers, and a smallish OLED screen

For the transducer, one can use either a [ATL mechanical probe](/retroATL3/) for example, or a [piezo + servo setup](/cletus), to mechanically scan the medium to be imaged 








