---
layout: post
title: Tire pressure monitoring system (part 4)
date: 2025-07-17 00:00:00 +0200
tags: tpms, retrofit
---
I verified that the tire pressure monitoring system (TPMS) was capable of
receiving updates of the new wheel sensors I bought from AliExpress. The only
thing left to do was to mount the sensors inside the tires. Today I went to a
tire shop, and they had a spot available to immediately mount the sensors
inside the tires. Before I did that, I asked them to verify the sensors using
their own testing tool, and they were able to confirm the identifiers with the
identifiers I read using VCDS. They also stated that the battery was still
good for at least 24 months, which I guess is the maximum time the device can
report.

After mounting the sensors, I drove back home, and the sensors were
automatically detected after a few kilometers of driving. The tires were
inflated to 2.5 bar, which is the recommended pressure for 'comfort' driving. I
inflated them to 2.8 bar, which is the recommended pressure for 'normal'
driving.

{% responsive_image path: "assets/posts/2025-07-17/tpms.jpeg" alt: "Tire pressures as reported by the TPMS." %}

The tire pressures flucuate a bit, depending on the temperature of the tires.
When one side of the car is parked in the sun, the tire pressure tends to be a
bit higher at that side. Based on this, it seems that the car correctly
identified left and right, and probably also front and rear. The TPMS is now
fully operational.

I still need to finalize the fuse box wiring, which I will do when I finalize
the ambient lighting retrofit.

[part 1][p1] - [part 2][p2] - [part 3][p3] - part 4

[p1]: {% post_url 2025-05-18-tire-pressure-monitoring-system-part-1 %}
[p2]: {% post_url 2025-05-26-tire-pressure-monitoring-system-part-2 %}
[p3]: {% post_url 2025-06-15-tire-pressure-monitoring-system-part-3 %}
[p4]: {% post_url 2025-07-17-tire-pressure-monitoring-system-part-4 %}
