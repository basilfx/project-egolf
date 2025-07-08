---
layout: post
title: ESC button (part 2)
date: 2025-07-09 00:00:00 +0200
tags: esc, asr, button, retrofit
---
I stated in the previous part that I would probably test the wiring before
installing the button. Today I added a wire to the ABS pump connector, to see
if it would work. According to the wiring diagrams, T46a/39 of the 46-pin ABS
pump connector is connected to the ESC button in the center console. This
button only connects to 12 V when pressed.

Disconnecting the ABS pump connector is not that hard, but I never did it
before. You have to push the red locking tab down, and then turn the grey
lever down and the connector can be removed. Then, the lever part can be
removed carefully by cutting the tie wrap and pressing a tab on the rear side.
The pins themselves are secured, and can be unlocked by pushing the purple tab
on the front side of the connector.

{% responsive_image path: "assets/posts/2025-07-09/connector.jpeg" alt: "The 46-pin connector." %}

Pin 39 is one of the small wires of the connector. There was a brown dummy pin
installed, which you can easily pull out. Most other connectors on the car use
rubber seals to prevent water ingress, but it seems that when the terminals
are properly secured, they rest on a rubber membrane to prevent water ingress.
It took me some time to figure this out, but lookin at some AliExpress listings
showed me that they do not include rubber seals for the small pins.

I did not have the right pin terminal, so I used a different one that fits but
does not lock in place. I have not been able to find the right part number for
the pin terminal, but the equivalent repair wire is `000 979 046 E`.

{% responsive_image path: "assets/posts/2025-07-09/terminal.jpeg" alt: "The pin terminal has a different design than most other pin terminals used on the car." %}

{% responsive_image path: "assets/posts/2025-07-09/installed.jpeg" alt: "The green wire is here for testing only." %}

I ran the additionl wire inside the car via the window, just for testing. I
then simply connected the wire to the 12 V socket, and noticed in the
instrument cluster that it switched between the different ASR/ESC programs.
That means that it will work, and I can continue. For now I cut the wire inside
the hood, and will install this properly via the firewall and coupling point in
the next part.

{% responsive_image path: "assets/posts/2025-07-09/working.jpeg" alt: "The instrument cluster shows when the progam changes." %}

[part 1][p1] - part 2

[p1]: {% post_url 2025-05-29-esc-button-part-1 %}
[p2]: {% post_url 2025-07-09-esc-button-part-2 %}
