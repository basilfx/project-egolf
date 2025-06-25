---
layout: post
title: A short to ground
date: 2025-05-31 00:00:00 +0200
tags: fault-finding, short-to-ground
---
Whenever I modify the car, I am always concerned about making things worse.
This was one such situation, but it turned out I was not at fault.

Last week, I [upgraded][1] the camera from a KA1 to a KA2 model. I needed to
[add][2] several CAN bus and supply wires from the front of the car to the
trunk lid, which required removing a few panels and taping the new wires to the
existing loom. Everything worked perfectly for a week with no faults. However,
today the head unit displayed a fault with the left-hand side back-up light
bulb.

I knew something was wrong: this e-Golf uses only LEDs, and the likelihood of
an LED failure is very low. I connected OBDEleven, which revealed the
following fault.

{% responsive_image path: "assets/posts/2025-05-31/fault.png" alt: "OBDEleven fault." %}

A short to ground — never a good sign. The first step I took was to unplug the
connector from the inner tail light to see if the error would change.
Although this resulted in two additional errors (open circuit and short
circuit to B+), the short to ground persisted. This ruled out any issues with
the tail light itself.

Next, I used a multimeter to measure between the back-up light bulb pin and
ground. This showed a dead short. During [last week's][1] camera installation,
I had modified some wiring connected to the back-up light bulb. However, after
measuring between these pins and the pin of the light bulb at fault, I found
they were not connected. This indicated that the reverse light signal
originates from the other back-up light bulb on the right-hand side.

To rule out a wiring issue, I disconnected the two connectors at the trunk lid
coupling point (THK). The short measured at the tail light connector
disappeared, indicating that the loom in the trunk lid was not damaged.
However, there remained a large loom running from the back to the front that
could potentially be the source of the problem.

Since all the wires in the loom were properly taped, I did not initially
suspect a short to ground via the ground wire. Most of the ground wiring runs
through the chassis, so a cut wire seemed more plausible. I began by removing
some easily accessible trim pieces: the door sill trim and the side trim next
to the back seats. With the multimeter still connected, I wiggled the wire
loom and was able to roughly identify where the wire was damaged.

My suspicion was correct — it was a short to the chassis. After some
inspection, I discovered the following:

{% responsive_image path: "assets/posts/2025-05-31/problem1.jpeg" alt: "Problem 1" %}

Can you spot it? Let's move the wire loom aside by removing the plastic clip
that secures it to the chassis.

{% responsive_image path: "assets/posts/2025-05-31/problem2.jpeg" alt: "Problem 2" %}

{% responsive_image path: "assets/posts/2025-05-31/problem3.jpeg" alt: "Problem 3" %}

A splinter of metal had cut into the wire loom. It was likely a remnant of
the chassis welding process, resembling a small blowout. Two wires had minor
damage to their protective insulation, but I did not see any exposed or
damaged wire strands, so I was fortunate. I removed the splinter, covered the
spot with tape, and wrapped the damaged wires with PVC tape.

{% responsive_image path: "assets/posts/2025-05-31/solution.jpeg" alt: "Problem 3" %}

I tested the lights before reinstalling all the trim pieces, and the problem
was resolved. It still puzzles me why this was not an issue for the previous
owner, especially since the car is already seven years old.

{% responsive_image path: "assets/posts/2025-05-31/trim.jpeg" alt: "Trim installed back" %}

[1]: {% post_url 2025-05-26-high-line-camera-upgrade-part-4 %}
[2]: {% post_url 2025-05-24-tpms-and-camera-preparation %}
