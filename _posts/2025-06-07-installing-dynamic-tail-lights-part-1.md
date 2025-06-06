---
layout: post
title: Installing dynamic tail lights (part 1)
date: 2025-06-07 00:00:00 +0200
tags: tail-lights, dynamic, retrofit
---
The dynamic tail lights are one of the features that really stand out. I really
like how they add depth to the car. My e-Golf does not have these lights, but
many people have retrofitted them—even on the pre-facelift model. I do not know
if I will do this now or later, but since I still have all the panels removed
from the trunk lid, it might be wise to prepare this for future installation.

{% responsive_image path: "assets/posts/2025-06-07/lights.jpeg" alt: "Different segments of the dynamic tail lights." %}

The tail lights consist of four pieces. I need the following parts (left-hand
drive, rest-of-the-world):

* `5G0 945 207 G` - Left outside
* `5G0 945 307 P` - Left inside
* `5G0 945 308 P` - Right inside
* `5G0 945 208 G` - Right outside

The tricky part seems to be the wiring. The existing connectors will not fit on
the new tail lights. Also, the inner tail lights are part of the turn signals,
so additional wiring must be installed to connect the outer and inner tail
lights. Almost all of the first page search results describe the retrofit for
the pre-facelift model or for American vehicles. The same applies to the
pre-fabricated adapter cables on AliExpress.

It turns out that Volkswagen offers an official retrofit option for the Golf.
This kit has part number `5G1 052 200 C` and contains the four tail lights,
wiring loom, and (coding) instructions. The existing connectors will be
replaced by `1K8 972 928 B`, which are not included.

{% responsive_image path: "assets/posts/2025-06-07/wiring.png" alt: "Retrofit wiring overview." %}

The thing that confuses me is that the official kit will add an additional wire
to the body control module (BCM). All the pre-fabricated adapter cables do not
do this. According to the [instructions][1], this is what should be adapted on
the BCM side:

* Connector T73c:
  * remove pin 9.
  * remove pin 3, move it to pin 9.
  * move pin 9 to pin 3.
  * add the additional wire to pin 6.

It is not terribly difficult to do. I could imagine that swapping pin T73c/3
and T73c/9 could also be solved at the other side of the cable. Using this kit
has one advantage: it comes with a Software Version Management (SVM) code. This
means that I can use ODIS-S to perform the coding for me, and that the retrofit
is 'officially' registered with Volkswagen. I might postpone swapping the BCM
for ambient lighting; otherwise, ODIS-S might not recognize my BCM properly.

part 1 - [part 2][p2]

[1]: https://www.kunzmann.de/produkt/exterieur-led-rear-light-set-vw-golf-7-r-facelift-genuine-volkswagen-upgrade-kit,15200,Anleitung-Golf-7-R-Facelift.pdf

[p1]: {% post_url 2025-06-07-installing-dynamic-tail-lights-part-1 %}
[p2]: {% post_url 2025-06-14-installing-dynamic-tail-lights-part-2 %}
