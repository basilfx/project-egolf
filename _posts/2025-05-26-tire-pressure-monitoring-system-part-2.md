---
layout: post
title: Tire pressure monitoring system (part 2)
date: 2025-05-26 01:00:00 +0200
tags: tpms, retrofit
---
After having received a [fake][1] TPMS sensor, I ordered a second-hand version
from a Tiguan. This time, I knew it would be a genuine one. The seller of the
fake one refunded me the money. At least the wiring loom was usable.

There are two hardware versions of the TPMS sensor, `H04` and `H06`. Both
versions can be flashed to software version `5Q0 907 273 F`, but `H06` offers
better protection against moisture, according to [this][2] website. It
probably has a better conformal coating applied to the internal hardware. I
therefore went with the `H06` version, which was a bit harder to find and a
bit more expensive.

I printed another version of my TPMS bracket, and mounted this onto the bumper
bar on the left rear side. I will probably make one more revision to include a
hole to tie the corrugated pipe to.

{% responsive_image path: "assets/posts/2025-05-26/tpms-bracket-1.jpeg" alt: "TPMS bracket 1" %}

{% responsive_image path: "assets/posts/2025-05-26/tpms-bracket-2.jpeg" alt: "TPMS bracket 2" %}

After coding, the sensor appeared in the head unit and in the instrument
cluster. The displayed pressures are historical, and I know the donor vehicle
had sustained damage on the front left side.

{% responsive_image path: "assets/posts/2025-05-26/tpms.jpeg" alt: "TPMS coded" %}

I still have to find a set of sensors and mount them inside the tires.

[part 1][p1] - part 2 - [part 3][p3]

[1]: {% post_url 2025-05-18-tire-pressure-monitoring-system-part-1 %}
[2]: https://www.drive2.ru/l/616081105128261542/

[p1]: {% post_url 2025-05-18-tire-pressure-monitoring-system-part-1 %}
[p2]: {% post_url 2025-05-26-tire-pressure-monitoring-system-part-2 %}
[p3]: {% post_url 2025-06-15-tire-pressure-monitoring-system-part-3 %}
