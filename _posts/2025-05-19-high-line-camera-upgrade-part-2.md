---
layout: post
title: High-line camera upgrade (part 2)
date: 2025-05-19 00:00:00 +0200
tags: rear-view-camera, retrofit, odis-e
---
I had less luck preparing the fake TPMS sensor [yesterday][1]. That did not
stop me from trying it today with the high-line camera. I hooked up the camera
to my test bench. ~~The CAN bus lines are connected to the infotainment CAN
bus, which I have exposed using a gateway splitter.~~ It turns out that it was
the wrong bus, even though it worked. See [this][2] post for how I found this
out.

Eight-pin connector from the camera (T8aj):

* T8aj/1 -> 12 V (Terminal 30)
* T8aj/5 -> GND (Terminal 31)
* T8aj/4 -> Infotainment high
* T8aj/8 -> Infotainment CAN bus low

The camera already runs the latest firmware, so there was no need to flash it
with a later firmware. The version I have is `5Q0 980 556 B` with `SW 0231`.
But it does require parameterization.

Like mentioned before, the Golf 7 never got this camera, so there are no
parameters available. I have used the [parameters][3] for a Passat B8 Variant
(V03935314JY) which matches somewhat in terms of camera position. I will have
to calibrate it afterwards, so I hope it will not cause any issues. I used
ODIS-E to upload the parameter set to the camera, which took just a few
seconds.

After uploading the parameters, the long coding was reset. I then used the
following coding as a starting point, also provided by [this][3] page:
`01730201E600201F000040`. I will dive into proper coding once the camera is
installed in the vehicle.

The camera is now ready for installation. I will complete that step later.

[part 1][p1] - part 2 - [part 3][p3] - [part 4][p4]

[1]: {% post_url 2025-05-18-tire-pressure-monitoring-system-part-1 %}
[2]: {% post_url 2025-05-26-high-line-camera-upgrade-part-4 %}
[3]: https://www.drive2.ru/l/652145911153035624/

[p1]: {% post_url 2025-05-13-high-line-camera-upgrade-part-1 %}
[p2]: {% post_url 2025-05-19-high-line-camera-upgrade-part-2 %}
[p3]: {% post_url 2025-05-25-high-line-camera-upgrade-part-3 %}
[p4]: {% post_url 2025-05-26-high-line-camera-upgrade-part-4 %}
