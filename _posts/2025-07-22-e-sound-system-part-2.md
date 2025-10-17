---
layout: post
title: e-Sound system (part 2)
date: 2025-07-22 00:00:00 +0200
tags: e-sound, retrofit, pedestrian-warning, pws
---
Now that I verified that the e-Sound system would work [yesterday][1], and that
the ESC/ASR button would work as well [two weeks ago][2], I could start with
the final wiring loom in the engine bay. I needed to route three wires from the
coupling point (TIUL) on the driver side to the right side of the front bumper
(two wires for the speaker, 0.75 mm²) and the ABS pump (ESC/ASR button,
0.35 mm²). These three wires need to go through the so-called firewall.

There are two options to route the wires through the firewall. The first one
is to use the secondary hole that probably exists for service or repair
purposes. The other option is to try to feed the wires throug the existing
hole. However, this the cable rubber grommet is taped very well to the wiring
loom. The first option would require me to properly seal the hole, so even
though option two is the hardest, it was the easiest to seal and the best
looking.

{% responsive_image path: "assets/posts/2025-07-22/firewall.jpeg" alt: "Removed all the tape around the rubber grommet, and used a pen tube to push the new wires through." %}

I carefully removed the tape around the rubber grommet, and then used a pen
tube to push the three new wires through. It definately took some time, and was
not easy on the hands, but it worked. Once the wires were through, I determined
the final lenght of the wires in the engine bay. I then taped the inside part
with cloth tape, and the outside part with heat-resistant cloth tape. I then
sealed the rubber grommet with the same tape, such that it looked as original
as possible.

{% responsive_image path: "assets/posts/2025-07-22/going-up-1.jpeg" alt: "With a bit of fiddling, I got through." %}

{% responsive_image path: "assets/posts/2025-07-22/going-up-2.jpeg" alt: "Can you spot the new wire?" %}

The next step was to route the wires behind the cable tray below the
windshield. I'm not sure how this tray/area is called, but it is where the
wiper motor is installed. Again, this plastic entry point was taped very well,
so I removed this too and fed the new wires through. I did not want to remove
the left side wiper arm, so it was a bit of fiddling to get it throught.

{% responsive_image path: "assets/posts/2025-07-22/inside-tray.jpeg" alt: "The new wires in the tray." %}

Finally, it had to go through the exit point on the right side of the car. This
part was even more taped, so I removed enought to pierce through it. After
installing the wires, I sealed it again with the heat-resistant cloth tape.

{% responsive_image path: "assets/posts/2025-07-22/exit-side.jpeg" alt: "The exit point of the new wiring loom." %}

At the exit point, one wire goes to the ABS pump. The other two wires go to the
bottom at the right side of the front bumper (left side on the photo). I rolled
the wires up, and taped them for now. I will finalize this at a later time.

On the inside, I also mounted the wiring loom to the existing wiring loom, and
routed them to the coupling point. The ABS wire goes to pin 5 of the black TIUL
connector (T17d). The two speaker wires go to pins 1 and 2 of the blue TIUL
connector (T17o). Note that the part that is fixed to the mount, is the part
of the connector that goes to the main wiring loom and thus to the engine bay.

{% responsive_image path: "assets/posts/2025-07-22/coupling-point.jpeg" alt: "The coupling point on the left side of the vehicle." %}

Crimping the 0.35 mm² pin terminal was not too hard, but for the 0.75 mm² I
definitely had a hard time. I don't own all crimping tools, so I did my best
with the ones I have. It took me a few tries to make it work, because initially
the crimp was still too thick to fit inside the connector.

For completeness, you will need the following conector pins:

* Female, up to 0.5 mm²: `000 979 034 E`
* Female, up to 1 mm²: `000 979 159 E`
* Male, up to 0.5 mm²: `000 979 035 E`
* Male, up to 1 mm²: `000 979 160 E`

Be aware that there are compatible versions of these pins that will fit, but
must not be mixed. I'm not sure which ones they are, but I compared them.
The proper ones have a copper side/color on the pins.

[part 1][p1] - part 2 - [part 3][p3] - [part 4][p4] - [part 5][p5]

[1]: {% post_url 2025-05-29-esc-button-part-1 %}
[2]: {% post_url 2025-07-09-esc-button-part-2 %}

[p1]: {% post_url 2025-07-21-e-sound-system-part-1 %}
[p2]: {% post_url 2025-07-22-e-sound-system-part-2 %}
[p3]: {% post_url 2025-08-04-e-sound-system-part-3 %}
[p4]: {% post_url 2025-08-23-e-sound-system-part-4 %}
[p5]: {% post_url 2025-10-18-e-sound-system-part-5 %}
