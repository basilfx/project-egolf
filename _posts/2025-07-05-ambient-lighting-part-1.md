---
layout: post
title: Ambient lighting (part 1)
date: 2025-07-05 00:00:00 +0200
tags: retrofit, ambient-lighting
---
This part technically already started, because I did some experiments when I
[tested][1] the new LED footwell lights. But actual work on the car started
today. My plans with this retrofit will first focus on the footwell lights in
the front and the rear of the car. But ambient lighting can also be installed
in the door panels, the glove box and even the sunroof (Passat). Nonetheless,
it is a retrofit that originally was not available on the Golf.

The Golf has an option for footwell lights, and even an option for fixed-color
light strips in the door panels. Therefore, the dashboard and the seats have
the cut-outs to mount footwell lights. The size of these lights happen to match
the size of the ambient lights used in the Audi A4. Newer Volkswagens use
smaller lights. I therefore ordered the A4 lights with the following part
numbers:

* `8W0 947 415 A` (front left)
* `8W0 947 415 B` (front right)
* `8W0 947 415 C` (rear left)
* `8W0 947 415 D` (rear right)

All the lights look the same, but the connector for the left and right side
are keyed differently. The parts numbers for the four-pin connectors are
`8K0 973 754` (black) and `8K0 973 754 A` (brown).

I started with mounting the lights under the front seats. By removing four
bolts on the seat slide rails, I could lift the seats up its back and access
underneath. Be sure to protect your interior carpet, because the seats are
heavy and the slide rails can scratch the carpet.

The cut out for the lights is already present, but there is a lot of foam
behind it. By pushing it away, I was able to install the light, and even though
the foam pushes the light back out a bit, it is installed securely. I ran the
wire through as much as possible under the foam, such that you cannot see or
hit it with your feet. Then I combined the wire with the existing loom and ran
it via the braided sleeve.

{% responsive_image path: "assets/posts/2025-07-05/seat.jpeg" alt: "The footwell light is mounted below, the wire runs to the top. " %}

Under the seat, there is a coupling point for all the wires that run to the
seat. I initially had the plan to install the additional wires in the red
connector, because there are empty slots available. I even crimped the pins
until I realized that I can also add an additional connector on the bracket,
next to the yellow airbag connector. The connector that fits is `8K0 972 994`,
which is the male version of the `8K0 973 754`.

{% responsive_image path: "assets/posts/2025-07-05/connector.jpeg" alt: "The connector attaches to the on bracket at the front seat coupling point." %}

{% responsive_image path: "assets/posts/2025-07-05/connector-installed.jpeg" alt: "The wire from the footwell light attached to the connector." %}

The wires from the coupling point then run under the carpet to the door sills.
I left them there for now. In the next parts I will install the front ambient
lights in the dashboard, and combine all the wires and connect them to the
body control module (BCM), power and ground.

[1]: {% post_url 2025-05-21-a-new-body-control-module-part-1 %}
