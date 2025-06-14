---
layout: post
title: Tire pressure monitoring system (part 3)
date: 2025-06-15 00:00:00 +0200
tags: tpms, retrofit
---
I received new tire pressure monitoring sensors from AliExpress. I was a bit
hesitant to buy new ones from AliExpress or eBay given my previous experience
with the [fakes ones][1]. It were the reviews by other buyers and a price of
30 euros that made me buy it once more. This time I received the orange
sensors, with the same part number: `5Q0 907 275 F`. It does not contain a
Volkswagen logo, and the text on the sensor is hard to read (it seems to be
laser etched). This is not uncommon: parts produced by the same OEM are often
sold via other channels, but without the vehicle manufacturers' logo. A least
the good thing is, is that it was produced this year (if this can be trusted).

{% responsive_image path: "assets/posts/2025-06-15/sensor.jpeg" alt: "The texts are hard to read on the TPMS sensor." %}

When I compared the sensor to the 'definitely fake ones', they look quite
similar, except for the valve stem, which looked more sturdy. I also compared
this sensor to sensors found on Google, ones I presume are original: their
texts are much easier to read and they do have a Volkswagen logo.

How do I know that the 'definitely fake ones' were fake? There is a measuring
block on the TPMS (J502, or block 65) that shows the identifier of the last
sensor that transmitted data. Sensors typically transmit when they are
rotating, or when the pressure suddenly drops. Since I did not mount the sensor
inside the tires yet, I put the sensors in a pressure sprayer, raised the
pressure and then suddenly released it. I was unable to get this to work for
the 'definitely fake ones', but this did work for the replacement ones.

{% responsive_image path: "assets/posts/2025-06-15/testing-1.jpeg" alt: "Testing the new TPMS sensors in a pressure spayer." %}

{% responsive_image path: "assets/posts/2025-06-15/testing-2.jpeg" alt: "Receiving the identifier of the sensor under test." %}

I did not pump the pressure spayer up to 5.4 bar. I believe this is just a
default value. When I dropped the pressure, I did receive truthworthy values.
This means that the new sensor are working at least.

Were the 'definitely fake ones' really fake? Not really. There is this project
called [rtl_433][2] that can use a cheap DVB-T receiver to receive radio
signals on arbitrary frequencies within its range, and visualize them on a
waterfall graph. I had this DVB-T receiver lying around, and tuned to 433.92
MHz, which is the frequency used by the sensors.

{# TODO waterfall graph visualizing TPMS signal #}

When I repeated the test with the pressure sprayer, I could see that something
was transmitting at that frequency when I dropped the pressure. I therefore
believe that they are working, they are just not compatible with a real
`5Q0 907 273 F`.

## Bracket update
I made a small change to the design. A 5 mm hole was added to the side, which
allows one to attach these small nylon push pin tie wraps to the side. This
can be used to guide the wire to the sensor, for added rigidety.

{% responsive_image path: "assets/posts/2025-06-15/tie-wrap.jpeg" alt: "Nylon push pin tie wrap." %}

You can find the updated bracket on [Printables][3].

[part 1][p1] - [part 2][p2] - part 3

[1]: {% post_url 2025-05-18-tire-pressure-monitoring-system-part-1 %}
[2]: https://github.com/merbanan/rtl_433
[3]: https://www.printables.com/model/1335455-tpms-bracket-for-golf-mk75

[p1]: {% post_url 2025-05-18-tire-pressure-monitoring-system-part-1 %}
[p2]: {% post_url 2025-05-26-tire-pressure-monitoring-system-part-2 %}
[p3]: {% post_url 2025-06-15-tire-pressure-monitoring-system-part-3 %}
