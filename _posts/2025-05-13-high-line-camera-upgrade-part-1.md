---
layout: post
title: High-line camera upgrade (part 1)
date: 2025-05-13 01:00:00 +0200
tags: rear-view-camera, retrofit, upgrade
---
Like other Volkswagen vehicles, the e-Golf has a retractable camera mounted
inside the rear logo. Whenever you put it in reverse, the logo collapses and
the camera appears. Volkswagen offers two types of cameras: a low-line
version (PR Code KA1) and a high-line version (PR Code KA2). From what I
understood, you will only receive a high-line camera in combination with a
towbar and trailer assist. This was never an option for the e-Golf.

Our primary car has a much better rear view camera, something I immediately
noticed during the test drive of the e-Golf. According to [this][1] page,
the low-line camera has a resolution of 640 x 492 pixels, roughly 0.3
Megapixels. The high-line camera has a resolution of 1312 x 1041 pixels,
roughly 1.3 Megapixels. The e-Golf I have is equipped with a Discover Pro 9.2"
(also known as MIB 2.5), which has a resolution of 1280 x 640 pixels, so it
can definately show more pixels. In addition, the high-line camera also shows
the driving trajectory lines.

I had two options to upgrade the camera. I could either replace the whole
logo assembly, including the camera, or replace the camera in the existing
assembly. The latter is much cheaper, and replacement cameras were easy to
find.

Or so I thought. I already ordered a replacement camera, but it is actually
one that does not have a parameter set for the Golf 7, only for Passat B8.
However, this does not seem to matter much once calibrated. The camera I
ordered has part number `5Q0 980 556 B`. The one that does have a parameter
set for the Golf 7 has part number `5Q0 980 568 B`. I also bought a wiring
set, because the new camera requires a CAN bus connection.

The new camera will not fit directly in the existing assembly. The mounting
holes for the camera are slightly different, and you need to drill holes in
the mounting bracket, or replace it with a 3D printed alternative. There is
one that I found [here][2], created by ataylor.

{% responsive_image path: "assets/posts/2025-05-13/bracket-1.jpeg" alt: "3D printed bracket for the camera." %}

{% responsive_image path: "assets/posts/2025-05-13/bracket-2.jpeg" alt: "3D printed bracket for the camera." %}

{% responsive_image path: "assets/posts/2025-05-13/bracket-3.jpeg" alt: "3D printed bracket for the camera." %}

I will see how this will work out, once I find the time to install the new
wires.

part 1 - [part 2][p2] - [part 3][p3] - [part 4][p4]

[1]: https://www.drive2.ru/l/666275185325777225/
[2]: https://www.printables.com/model/270860-vw-golf-mk7-rear-view-camera-adapter

[p1]: {% post_url 2025-05-13-high-line-camera-upgrade-part-1 %}
[p2]: {% post_url 2025-05-19-high-line-camera-upgrade-part-2 %}
[p3]: {% post_url 2025-05-25-high-line-camera-upgrade-part-3 %}
[p4]: {% post_url 2025-05-26-high-line-camera-upgrade-part-4 %}
