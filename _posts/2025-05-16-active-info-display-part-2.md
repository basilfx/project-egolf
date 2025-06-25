---
layout: post
title: Active Info Display (part 2)
date: 2025-05-16 00:00:00 +0200
tags: active-info-display, retrofit, gateway
---
Today I visited the shop that would perform the installation of the Active Info
Display for me. There were simply too many hurdles I would have to overcome to
successfully complete it myself.

There is not much to show other than a before and after picture.

{% responsive_image path: "assets/posts/2025-05-16/before.jpeg" alt: "Before cluster replacement." %}

{% responsive_image path: "assets/posts/2025-05-16/after.jpeg" alt: "After cluster replacement." %}

They did a great job. The cluster looks as good as new. I really like it,
especially that I can always see the exact digital vehicle speed without
having to navigate to the vehicle info view.

While I was there, I also asked them to remove component protection from the
new gateway I prepared. They even installed it, and it worked without any
issues. I still need to adjust a few settings that did not match the old
gateway. The gateway is easily accessible under the steering wheel, so the
installation was not too difficult.

{% responsive_image path: "assets/posts/2025-05-16/gateway.jpeg" alt: "Location of the gateway module." %}

## Autoscan
I created another autoscan and adaption channel maps using VCDS. You can find
these [here][1]. It includes all the coding changes up to this point.

[part 1][p1] - part 2

[1]: https://github.com/basilfx/project-egolf/tree/master/assets/posts/2025-05-16/vcds

[p1]: {% post_url 2025-05-06-active-info-display-part-1 %}
[p2]: {% post_url 2025-05-16-active-info-display-part-2 %}
