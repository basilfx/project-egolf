---
layout: post
title: Upgrading the PLA module
date: 2025-05-27 00:00:00 +0200
tags: pla, parking-assist, upgrade
---
My e-Golf has a PLA 3.0 module (German for Parklenkassistent) with 12 sensors
to cover the full circumference of the vehicle It can park itself, which is a
nice party trick, but I will probably never use it in practice. According to
VCDS, the following module is installed:

```
Address 10: Park/Steer Assist (J791)       Labels:| 5Q0-919-298.clb
   Part No SW: 5QA 919 298 E    HW: 5QA 919 298 A
   Component: PLA 3.0 12KH07 0452
   Serial number: 000308417617207 Dataset Number: V03935264ZA 0001
   Coding: 2271167811
   Shop #: WSC 00029 028 00029
   ASAM Dataset: EV_EPHVA2CAU3700000 009038
   ROD: EV_EPHVA2CAU3700000_009_VW37.rod
   VCID: 52FD7A55A46CBF4A69E-8006

No fault code found.
```

What surprised me was that it had index `E` with software version `0452`. This
could be a 'special' version for the e-Golf (like the [gateway][1] was
'special' for electric vehicles). However, newer e-Golfs are produced with
index `D` and software version `0050` (yes, one letter back) or `H` with
software `0061`. I can also not think of a reason why this module would be
different for an electric vehicle. But all of them are based on hardware
`5QA 919 298 A`.

Nonetheless, the latest available version seems to be index `K` with software
`0073`, and I have the urge to update as much as I can. I found a second-hand
version with index `K` from a Tiguan for cheap. As with the gateway swap, I
had no intention of potentially damaging the original module, especially since
I could not find a flash file with index `E`.

The PLA module is located under the steering wheel parallel to the BCM.
Swapping it is easy: remove the two connectors, gently pulled the module out of
its bracket and install the new one.

It is necessary to parameterize the PLA module. The parameter data probably
contains information about the sensor placement, vehicle dimensions and other
data. Since the e-Golf was not produced with index `K`, I could not perform
the same trick as with the [BCM][2], where I would use ODIS-S to reconfigure
the module. But after some googling, I found a parameter set for a Golf 7
Facelift (MY2020). The dataset also mentioned 'two speakers', which is likely
similar to that of any other Golf. The name of the parameter set is
`V03935336AG`. I flashed it using ODIS-E, restored the long coding and then
compared all adaptions with a backup of the original module. There were no big
differences, and everything seems to work as before.

{% responsive_image path: "assets/posts/2025-05-27/pla.jpeg" alt: "The PLA 3.0 modules." %}

[1]: {% post_url 2025-05-15-a-gateway-on-a-test-bench %}
[2]: {% post_url 2025-05-21-testing-a-new-body-control-module %}
