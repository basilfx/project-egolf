---
layout: post
title: TPMS and camera preparation
date: 2025-05-24 00:00:00 +0200
tags: rear-view-camera, tpms, wiring
---
Both the TPMS sensor and high-line rear view camera require additional wiring.
The TPMS sensor requires four additional wires (CAN high, CAN low, 12V, and
GND). The rear view camera requires only two additional wires (CAN high and
CAN low) because the existing low-line camera already provides the power and
signal wires that can be reused.

The TPMS sensor will be installed under the vehicle, on the left rear side.
The wires will enter the boot via a rubber grommet. It therefore made sense
to run the two additional wires for the rear view camera on the same side, so
I did not have to remove trim panels on both sides of the vehicle: the
gateway has access to all the CAN bus lines.

I decided to first remove the front seat and the rear seats. This makes the
removal of the other trim panels much easier. I then removed the door sill
trim, the side trim up to the roof liner, and all the lid trim pieces. I
recommend [this video][1] to get an idea of how to remove the panels.

The CAN bus wires for the camera were added to the left side and routed via
the left rubber grommet between the roof and the trunk lid. Be careful when
removing them, as they can easily be damaged. I might need to replace one
some day, as it does not seal properly on the lid side. I recommend removing
only the lid side and using a cable fish tape.

{% responsive_image path: "assets/posts/2025-05-24/trunk-lid.jpeg" alt: "CAN bus wires for rear view camera" %}

The TPMS wires were fed through the chassis using a corrugated pipe. I drilled
a hole in the existing grommet, which I plan to replace with a better part
once I can find one.

{% responsive_image path: "assets/posts/2025-05-24/tpms.jpeg" alt: "TPMS cable" %}

Both cables were then taped to the existing wiring loom, all the way to the
front of the car. Unfortunately, I did not take more pictures that day. It was
a rainy day and I underestimated the amount of work.

[1]: https://www.youtube.com/watch?v=paJLp7HYb_A
