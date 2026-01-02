---
layout: post
title: e-Sound system (part 1)
date: 2025-07-21 00:00:00 +0200
tags: e-sound, retrofit, pedestrian-warning, pws
---
The name of the e-Sound system makes it sound like it is a sound upgrade for
the car. But is actually a pedestrian warning system (PWS, or AVAS). It is a
system that emits a sound when the car is driving at low speeds, to warn
pedestrians and cyclists. The sound is emitted by a speaker that is installed
in the front of the car, close to the right wheel arch. It must not be confused
with a similar system, that emits a sound by vibrating the front windows to
emit an 'engine sound' to the interior of the car.

This pedestrian warning system is required by law in many countries, including
the EU, and it is a requirement for all electric vehicles with a type approval
after July 2019. My e-Golf has MY2018, so it does not have to have this system
installed, but it has been an option back then. I want to retrofit it, because
my primary car has the system as well, and it is inevitable that all cars will
have this system at some point. Yes, the downside is that it will make the car
sound like a spaceship, but I can live with that. I am driving electric since
2017, so I had my share of people that did not hear me coming, including
children. The e-Golf does have an option to turn it off using a button in the
center console.

I have not found any information about a retrofit of this system, since it does
not have the appeal of a performance or comfort upgrade. But based on the
wiring diagram and parts list, it seems to be a simple retrofit. The system
consists of two electrical parts: a speaker (part number `5GE 035 362 A`) and a
control unit (part number `5QE 035 335 M`). The speaker is installed close to
the front right wheel arch, and the control unit is installed behind the
head-unit display. I also needed a connector for the speaker (`4D0 971 992 A`)
and a connector for the control unit (part number `8E0 972 112`).

It was pretty easy to find the parts second hand, especially since the system
is installed in several other brand of the Volkswagen Group. I did buy the
control unit from an old e-Golf with hardware version `H11` and software
version `0225`. There are newer unit, but I am unsure if they produce the same
sound. This is something that could definitely be part of the data set, but not
one that I could find. I did order the wrong version of the connector for the
control unit: it was keyed differently. Luckily, the second-hand speaker came
with the correct connector, but damaged. So I swapped the casing of the
connector and I had a working connector.

{% responsive_image path: "assets/posts/2025-07-21/parts.jpeg" alt: "The speaker and the control unit." %}

{% responsive_image path: "assets/posts/2025-07-21/connector.jpeg" alt: "The 12-pin connector for the control unit." %}

My next goal was to find out if it would work at all. I did not expect any
issues with coding: this system simply listens for a speed signal and emits a
sound accordingly so I did not expect any cross-coding. I created a wiring loom
to quickly connect it to the car. The pinout is listed below.

T12ab is the 12-pin connector for the control unit. T2hw is the 2-pin connector
for the speaker. T10ks is the 10-pin connector for the center console buttons
(EX23).

* T12ab/1 -> Terminal 15 (fuse SC48)
* T12ab/2 -> GND
* T12ab/3 -> Speaker T2hw/2 (via TIUL T17o/1)
* T12ab/4 -> Speaker T2hw/1 (via TIUL T17o/2)
* T12ab/7 -> Terminal 15 (fuse SC48)
* T12ab/8 -> GND
* T12ab/9 -> T10ks/7 (EX23)
* T12ab/10 -> T10ks/4 (EX23)
* T12ab/11 -> Powertrain CAN bus low
* T12ab/12 -> Powertrain CAN bus high

Of course, I did not connect it properly, only the bare minimum to get it
working. That means I took 12 V from somewhere else, and did not connect the
buttons. After plugging it in, without any coding, the car already notified me
that the system was connected.

{% responsive_image path: "assets/posts/2025-07-21/fault.jpeg" alt: "The instrument cluster showed this fault after starting the car without any coding." %}

I then connected the car to VCDS, added module `C0` to the list of installed
modules in the gateway and inspected the faults. The module reported an issue
with the buttons, which I temporary disabled using coding. After that, I made a
test drive, and was greeted with a sound while driving.

The next step is to source the parts for the mounts, find out where everything
needs to be bolted and route the wires.

part 1 - [part 2][p2] - [part 3][p3] - [part 4][p4] - [part 5][p5]

[p1]: {% post_url 2025-07-21-e-sound-system-part-1 %}
[p2]: {% post_url 2025-07-22-e-sound-system-part-2 %}
[p3]: {% post_url 2025-08-04-e-sound-system-part-3 %}
[p4]: {% post_url 2025-08-23-e-sound-system-part-4 %}
[p5]: {% post_url 2025-10-18-e-sound-system-part-5 %}
