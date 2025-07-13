---
layout: post
title: A new body control module (part 2)
date: 2025-07-10 00:00:00 +0200
tags: bcm, test-bench, odis-s, ambient-lighting
---
In the [previous][1] part I connected a new body control module (BCM) to my
test bench. I was able to power it, access it and flash different firmwares. In
the mean time, I also received a proper connector for T73a (the A-side
connector of the BCM) with part number `5Q0 937 700 B`, so I could properly
wire the BCM to the test bench.

Now that I have installed dynamic tail lights and performed software coding
using ODIS-S, I know that the adaptions and parameter set have changed compared
to the e-Golf I used to restore the settings and adaptions for firmware
 `5Q0 937 084 DD` with.

I wanted to test one more thing: what if I would downgrade from firmware
`5Q0 937 084 DD` to `5Q0 937 084 CQ` and then try to restore it using ODIS-S?
Index `CQ` is a firmware that is compatible with my car according to ETKA, and
since the hardware of the new BCM is based on is `H38` with part number
`5Q0 937 084 CG`, I should be able to flash it back to `CQ`. I could also have
chosen to flash `5Q0 937 084 CG`, but the software with index `CP` was already
in the BCM in the car and I could not find a `CP` firmware file.

Using the firmware file `FL_5Q0937084CQ_0253_S.frf` (which was actually listed
under the AUDI firmware files), I downgraded the BCM to `CQ`. This took about
four minutes, and the parameter set and adaptions were still the same. I then
connected with ODIS-S and restored the parameter set and adaptions. This time
it worked, and the BCM was restored to the factory defaults but with the
adaptions and parameter set of my e-Golf with dynamic tail lights.

The next step was to flash the BCM to `EC` again, but I took a intermediate
step and flash it to `DD` first. I did that so I could see if this would affect
the parameter set and adaptions (I created an adaption channel mapping after
each attempt). This procedure was not so different from the [previous][1] part.

I know have the BCM with software index `EC` and the parameter set as intended.
an even better result than before.

## Autoscan
I kept track of all the adaption channels when performing the upgrades. For
the ones interested, I have made the adaption channel maps available [here][3].
There are additional channels availble: from CQ to DD added 43 channels, and
from DD to EC added 35 channels.

[part 1][p1] - part 2 - [part 3][p3]

[1]: {% post_url 2025-05-21-a-new-body-control-module-part-1 %}
[2]: {% post_url 2025-07-04-installing-dynamic-tail-lights-part-3 %}
[3]: https://github.com/basilfx/project-egolf/tree/master/assets/posts/2025-07-10/vcds

[p1]: {% post_url 2025-05-21-a-new-body-control-module-part-1 %}
[p2]: {% post_url 2025-07-10-a-new-body-control-module-part-2 %}
[p3]: {% post_url 2025-07-14-a-new-body-control-module-part-3 %}
