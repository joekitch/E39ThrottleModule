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



---


## Hardware

- Arduino Nano
- DAC
- ADC
- Canbus module
- canbus splitter


---

## Diagram



---

