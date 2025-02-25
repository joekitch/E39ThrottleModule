# E39ThrottleModule
---

drive by wire throttle control for bmw e39, which sits in between the throttle pedal and DME, and can recieve throttle commands over canbus

The target vehicle is a 2003 bmw e39 540iT, to be able to brake using the semi-autonomous driving software OPENPILOT.

---

### Disclaimer

This has only been tested on one car, and not extensively

Do not expect this to save your life, it's a convenience feature at best

---

## Backround

This is specific to the drive-by-wire throttle pedal of a bmw e39 540i. Part number 35426786282

Picture of e39 throttle pedal
<p align="left">
  <img src="Pics/e39 540i throttle pedal.jpg?raw=true">
</p>

I'm not sure what other cars, if any, use this same throttle pedal

NOTE: this is the LATER version of this part, with the internal positon sensor. The earlier versions connect to the position sensor via an external linkage 

---

## Working principle

The throttle pedal is mostly a glorified potentiometer, it recieves a 5v refernce signal from the car, and the output voltage indicates to the DME how depressed the throttle pedal is.

0v corresponds to 0% throttle, and the pedal at its top position. 5v corresponds to 100% throttle, with the pedal completely depressed

On the bmw e39, the bus topology is an eclectic mix of canbus and LIN, but luckily the one true canbus connects to all the important pieces openpilot needs to talk to, including the DME (engine compute module)

This isn't accessible through the obd2 connector (which uses a separate "diagnostic bus" with limitations) as far as i can tell, and requires tapping into the true canbus further upstream.

---

## Tapping into the main bus

There's an available branch of the main canbus accessible via (???) , which the throttle control module will split off of. The brake module will also split off this bus in a different location but that's a different repo.

E39 canbus topology map, specifically the HIGH cluster which is more integrated
<p align="left">
  <img src="Pics/Bus Topology I -K-M-P-Can-Diagnostic.webp?raw=true">
</p>

If you have a KOMBI or LOW cluster, the topology is a little different, the same bus tapping approach will work, but it's worth knowing the differences
E39 canbus topology map, specifically the HIGH cluster which is more integrated
<p align="left">
  <img src="Pics/KOMBI K Bus Topology Chart for e39 e53 with Low Cluster.jpg?raw=true">
</p>

---

## Hardware

- Arduino Nano
- DAC
- ADC
- Canbus module
- canbus splitter


---

## Diagram

A general diagram of the whole system is below

<p align="left">
  <img src="Pics/BMW_Openpilot_throttle.drawio.png?raw=true">
</p>


---

