---
layout: post
title: Tire pressure monitoring system (part 1)
date: 2025-05-18 00:00:00 +0200
tags: tpms, retrofit, odis-e
---
The tire pressure monitoring system (TPMS) are something I frequently monitor
on my primary vehicle. I have the impression that tire pressure is even more
important on an electric vehicle. There are two types of TPMS: direct and
indirect. The e-Golf uses the indirect variant, which cannot be monitored
until it is too late.

The indirect system uses the ABS wheel speed sensors to measure the wheels.
When the pressure drops, the wheel rolling radius decreases (it becomes
flatter). When it exceeds a certain threshold, the driver is notified.
This system can only detect underinflation. It also needs to learn what the
normal condition is, so you need to press the TPMS SET button each time you
inflate your tires.

The direct system uses sensors in each wheel (attached to the valve stem) and
measures the pressure directly. This information is then transmitted to a
sensor and displayed on the instrument cluster and infotainment system. This
system is often called TPMS-high.

I bought a kit from eBay, which included the TPMS sensor, four wheel sensors,
and the necessary wiring. The TPMS sensor has part number `5Q0 907 273 B` with
hardware version `H04`. The wheel sensors have part number `5Q0 907 275 F`.

{% responsive_image path: "assets/posts/2025-05-18/tpms.jpeg" alt: "The counterfeit TPMS sensor." %}

{% responsive_image path: "assets/posts/2025-05-18/sensor.jpeg" alt: "One of the four wheel sensors." %}

Using the test bench, I connected the TPMS sensor to the extended CAN bus using
the pinout below. I then added it to the gateway installation list so I could
access it.

Four-pin TPMS sensor connector (T4fh):

* T4fh/1 -> Extended CAN bus low
* T4fh/2 -> Terminal 30 (12 V)
* T4fh/3 -> Extended CAN bus high
* T4fh/4 -> Terminal 31 (ground)

This is where I became suspicious: communication with the sensor was
intermittent. VCDS constantly reconnected with the TPMS, which made the
interface unusable. However, it was able to identify the device, and the listed
hardware and software versions were different from those I expected: `H05` with
software `S051`.

{% responsive_image path: "assets/posts/2025-05-18/vcds.jpeg" alt: "Identification of the sensor in VCDS." %}

The TPMS sensor needs to be parameterized, which programs the nominal
pressures for one or more tire sets. The parameter file can be generated
using online tools. I created one for the e-Golf, which recommends 2.8 bar of
pressure for normal driving conditions. I attempted to upload the parameter
set using ODIS-E, but this failed as well. As a final attempt, I decided to
flash the sensor to a later firmware version. The sensor with part number
`5Q0 907 273 B` and software `0009` can be flashed to `5Q0 907 273 F` with
software `0011`. I tried this with the flash file `FL_5Q0907273___0011.frf`
and ODIS-E, but unfortunately this also failed.

After some research, I found [this][1] page which states that the sensor is
a fake, based on a GD32 microcontroller housed in a counterfeit enclosure.
There is nothing wrong with this microcontroller and the other parts used. It
is just not of the grade typically used for automotive applications. I will
contact the seller to resolve this issue and will likely look for an original
sensor.

{% responsive_image path: "assets/posts/2025-05-18/fake.jpeg" alt: "Internals of a fake TPMS sensor (sourced from [1])." %}

{% responsive_image path: "assets/posts/2025-05-18/real.jpeg" alt: "Internals of a real TPMS sensor (sourced from [2])." %}

## Designing a bracket
The Golf 7 never had the TPMS sensor as an option. Therefore, an official
mounting bracket does not exist. I have seen people mount it
[on the bottom bumper bar][3], [behind the bumper][4], or
[next to the gateway][5] (albeit a counterfeit version). For the Passat and
the Tiguan, the installation location is on the rear side of the vehicle.
Using signal strength, it can then detect where each tire sensor is located.

Since no official mounting bracket exists, I decided to design a simple one
using a 3D printer. Inspired by [this one][3], I kept the design simple and
used the two mounting holes on the TPMS sensor itself to bolt it to my bracket.
I did not feel comfortable designing a bracket that would hold the sensor by
itself, given that 3D printing using fused deposition modeling (FDM) prints
layer by layer and I expect the part to be exposed to harsh conditions.
The design is strong in the direction in which it mounts to the bumper bar
and the TPMS sensor. The taller parts are only for alignment and have no
functional purpose.

The bracket can be bolted onto the bottom bumper bar. This bar is also used
to mount a tow bar, but the bolts are higher up. To avoid damaging the PU
coating on the steel, I also designed a 'washer' that centers the bolt, so
there is no metal-on-metal contact. The cable can enter the vehicle through
a nearby rubber grommet.

{% responsive_image path: "assets/posts/2025-05-18/bracket-1.jpeg" alt: "First prototype printed using PLA material." %}

{% responsive_image path: "assets/posts/2025-05-18/bracket-2.jpeg" alt: "Test fit on the bumper bar." %}

{% responsive_image path: "assets/posts/2025-05-18/bracket-3.jpeg" alt: "M12-to-M8 centering ring to protect coating." %}

I made several prototypes to fine-tune the fit. Because I wanted to test how
the bracket would hold up, I already mounted it under the car. I printed a
dummy because I did not want to damage the counterfeit sensor since I do not
know if I can return it.

{% responsive_image path: "assets/posts/2025-05-18/bracket-4.jpeg" alt: "Second prototype with dummy sensor to test durability." %}

The bracket can be found on [Printables][6].

part 1 - [part 2][p2] - [part 3][p3]

[1]: https://www.drive2.ru/l/652143162373965600
[2]: https://www.drive2.ru/l/616081105128261542/
[3]: https://forums.ross-tech.com/index.php?threads/5328/
[4]: https://uk-polos.net/viewtopic.php?p=552256#p552256
[5]: https://www.golfmk7.com/forums/index.php?threads/direct-tpms-kit-retrofit-anyone.377976/page-3#post-7775959
[6]: https://www.printables.com/model/1335455-tpms-bracket-for-golf-mk75

[p1]: {% post_url 2025-05-18-tire-pressure-monitoring-system-part-1 %}
[p2]: {% post_url 2025-05-26-tire-pressure-monitoring-system-part-2 %}
[p3]: {% post_url 2025-06-15-tire-pressure-monitoring-system-part-3 %}
