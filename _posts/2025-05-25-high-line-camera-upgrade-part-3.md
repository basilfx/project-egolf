---
layout: post
title: High-line camera upgrade (part 3)
date: 2025-05-25 00:00:00 +0200
tags: rear-view-camera, retrofit
---
[Yesterday][1] I finished installing two CAN bus wires for the new rear view
camera. Today I continued the installation and was able to test it. It is not
yet finished, because I did not have all the necessary pins and connectors to
install it properly.

I do not want to splice into existing wiring, and prefer to install an adapter
instead, for two reasons:

1. Existing wiring is often tighly taped and too short to properly work with,
   making proper splices hard to install.
3. I want to be able to revert my changes if really necessary, for whatever
   reason.

The camera needs to be connected to the Infotainment CAN bus network. As
mentioned in [yesterdays][1] post, I decided to route it together with the TPMS
wiring on the left side of the car. On AliExpress, I found a gateway splitter
cable at the gateway side. ~~It exposes the necessary CAN bus lines.~~ Future
me, read [part 4][2].

{% responsive_image path: "assets/posts/2025-05-25/splitter.jpeg" alt: "Gateway splitter" %}

In [part 1][3] and [part 2][4] I already prepared the camera for installation.
I could now remove the actuator part from the logo assembly by disconnecting
all the connectors connected to the assembly, then removing the four T20
screws. Be sure to support it, otherwise it might drop down.

{% responsive_image path: "assets/posts/2025-05-25/assembly.jpeg" alt: "Logo assembly" %}

With the actuator part removed, I could disassemble it and install the new
camera. I followed [this][5] guide.

{% responsive_image path: "assets/posts/2025-05-25/camera-installation-1.jpeg" alt: "Actuator part removed." %}

{% responsive_image path: "assets/posts/2025-05-25/camera-installation-2.jpeg" alt: "Low-line and High-line cameras compared." %}

{% responsive_image path: "assets/posts/2025-05-25/camera-installation-3.jpeg" alt: "Disassembly of the camera housing of the actuator." %}

The existing wiring can be reused, but does not directly plug into the new
camera (the video signal does). With the low-line camera, the camera is
activated when the backup light is activated. This also actuates the servo
motor to present the camera. The high-line camera now activates via the CAN
bus. This has the bonus that you can also show the camera using the park assist
button even if you are not in reverse. Once activated, it is the camera that
now actuates the servo motor.

Eight-pin connector from the camera (T8aj):

* T8aj/1 -> Terminal 30 (12 V, take from T4d/4)
* T8aj/5 -> Terminal 31 (ground, take from T4d/2)
* T8aj/6 -> Servo motor (connect to T4/3, remove existing wire)
* T8aj/4 -> Infotainment CAN bus high
* T8aj/8 -> Infotainment CAN bus low

T4d is the four-pin connector from the servo motor. T4bt is the four-pin
connector used to power the low-line camera.

I did not have the correct pins and connectors, so I temporarily used power
from T4bt/1 and the video signal ground. I did not have the right pin for
T4d/3, so I used this makeshift solution to at least test everything out. I
have ordered the male and female version of that connector (part numbers
`4B0 973 812` and `4B0 973 712`), so I can assemble a proper adapter that
provides power, ground and the actuator pin via the one connector (T4d),
instead of two.

{% responsive_image path: "assets/posts/2025-05-25/connector.jpeg" alt: "Make-shift wire as pin terminal in connector T4d." %}

[part 1][p1] - [part 2][p2] - part 3 - [part 4][p4]

[1]: {% post_url 2025-05-24-tpms-and-camera-preparation %}
[2]: {% post_url 2025-05-26-high-line-camera-upgrade-part-4 %}
[3]: {% post_url 2025-05-13-high-line-camera-upgrade-part-1 %}
[4]: {% post_url 2025-05-19-high-line-camera-upgrade-part-2 %}
[5]: https://www.drive2.ru/l/666275185325777225/

[p1]: {% post_url 2025-05-13-high-line-camera-upgrade-part-1 %}
[p2]: {% post_url 2025-05-19-high-line-camera-upgrade-part-2 %}
[p3]: {% post_url 2025-05-25-high-line-camera-upgrade-part-3 %}
[p4]: {% post_url 2025-05-26-high-line-camera-upgrade-part-4 %}
