---
layout: post
title: 12 V battery replacement
date: 2025-05-12 01:00:00 +0200
tags: battery, maintenance, replacement
---
As mentioned in the previous post, I already had plans to replace the 12 V
battery of my car. The current one was still the one from the factory, and was
stamped with date code week 35 of 2017. Given that the normal lifetime of a
12 V battery is somewhere between three to eight years, it is already on the
longer side.

Battery failure is not binary. They degrade in capacity until a point they are
not capable of being usable. Regular combustion vehicles draw a lot of current
when the start motor is engaged. Under unfavorable circumstances, a cold and
undercharged battery might drop below a usable charge level, which can lead to
troubles starting the vehicle.

Electric vehicles do not have a start engine. Instead, they have a high-voltage
contactor, which needs to be energized by the 12 V battery to be operable. Once
toggled, you can 'start' the car. When the 12 V battery voltage drops, it gets
charged by the high-voltage battery. But even if the high-voltage battery is
full, it cannot operate if the 12 V battery is empty.

## The replacement
My e-Golf was equipped from the factory with a 59 Ah EFB 12 V battery. EFB is
the type of battery, and stands for 'Enhanced Flooded Battery'. The car is also
equipped with battery monitoring equipment, to measure power draw and estimate
charge levels.

The factory battery is size H5, which is about 242 mm long. The mount itself
has room for a H6, which is about 278 mm long. I found a replacement battery
of 72 Ah in capacity of size H6, produced by Exide. The type of the battery was
AGM, which stands for 'Absorbent Glass Mat'.

AGM is a battery type, offering better lifetime, lower self-discharge rates and
better resistance to cold temperatures. I do not see any reasons not to upgrade
from EFB to AGM. The car is not used or charged daily, so it should be an even
better fit. There is some discussion if this is possible, but the e-Golf
produced for the american market uses a battery with [part number][1]
`000 915 105 CC`, which is an AGM type battery.

{% responsive_image path: "assets/posts/2025-05-12/old.jpeg" alt: "The old battery." %}

{% responsive_image path: "assets/posts/2025-05-12/removed.jpeg" alt: "The old battery removed." %}

{% responsive_image path: "assets/posts/2025-05-12/new.jpeg" alt: "New battery installed." %}

{% responsive_image path: "assets/posts/2025-05-12/done.jpeg" alt: "New battery installed." %}

The old battery weighed about 19 kilograms. The new one weighs about 21
kilograms and has approximately 22% more capacity. While at it, I also
installed a battery protection cover (part number `5Q0 915 411 H`) that I
bought second-hand from a Passat. This cover is not installed on the e-Golf,
but is installed on the combustion cars to protect it from engine heat. I see
it as a layer of protection, and it does not harm if it does not work.

## Coding the new battery
The new battery needs to be programmed. You need to tell the gateway module
(J533, or block 19) about its size and type, so it can properly estimate the
state of charge and apply the right charge characteristics.

You can code the new battery using VCDS.

1. Go to module 19-Gateway.
2. Go to adaptions.
3. Change `IDE03256-MAS06105-Battery adaptation-Rated battery capacity` to the
   new battery size.
4. Change `IDE03256-MAS06106-Battery adaptation-Battery technology` to the type
   of the battery. Apparently, 'fleece' is the option for AGM type batteries,
   not 'binary-AGM'. See [here][2] for more information.
5. There are two adaptions left for the manufacturer and serial number. They
   are not required, and did not even match with the original battery installed
   in my car. I did change the value of
   `IDE03256-MAS06107-Battery adaptation-Battery manufacturer` to `TU3`, which
   according to [this][3] equals Exide.

[1]: https://parts.vw.com/p/Volkswagen_2019_e-Golf-SEL-Premium-Hatchback/Battery/47985038/000915105CC.html
[2]: https://www.audizine.com/forum/showthread.php/898523-AGM-battery-coding-on-OBDeleven-quot-Fleece-quot-or-quot-Binary-AGM-quot
[3]: https://forums.ross-tech.com/index.php?threads/29706/#post-249801
