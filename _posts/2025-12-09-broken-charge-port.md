---
layout: post
title: Broken charge port
date: 2025-12-09 00:00:00 +0100
tags: charge-port, repair
---
Yesterday, the charge port of the e-Golf broke. Last Friday, I was unable to
remove the plug from the car, but eventually I managed to get it out. Then on
Saturday, I wanted to charge the car again, but this time the plug would not
lock. Although charging would commence on the charge point, the car gave a red
LED indication on the charge port. I tried to swap the cable with another one,
and I finally managed to charge it again. Until yesterday, when I could not
get it to work, no matter how often I tried.

{% responsive_image path: "assets/posts/2025-12-09/failure.jpeg" alt: "The red light of doom." %}

With less than 50 kilometers of range, I was able to drive it to the local
dealer. Although this was not the dealer where I bought the car, I did not have
any choice. The car still has warranty, and I was allowed to get it repaired
at any authorized Volkswagen dealer.

At the dealer, they confirmed that the charge port was broken, and the root
cause is the locking motor. It is a common failure mode that also occurs on
other Volkswagen models that have the same charge port design. The locking
motor is directly connected to the wiring loom, so according to a repair
instruction ([TPI 2051071/6][1]), a replacement part can be connected by
cutting the wiring loom and splicing in a new connector.

{% responsive_image path: "assets/posts/2025-12-09/replacement-part.jpeg" alt: "The replacement part with the connector installed." %}

I was lucky that this was covered by warranty. It blew my mind when I heard
that the replacement part was over 300 euros (excluding labor costs). I know
that repair parts can be expensive, but for something that is just an RC motor
with a few plastic gears, it is quite a lot. For the newer models such as the
ID.3 and ID.4, this motor can be replaced separately and only costs about 50
euros. And besides that, I was able to find the same motor for a fraction of
the price for the e-Golf. OK, I do have to add a connector to it, but still.
Nonetheless, I am happy that the car is fixed, and fast. The dealer did a great
job in getting it quickly.

When I picked up the car, I asked if they still had the broken part. For such
a price, I want to know the failure mode. Opening it up was easy, and it
operates very simple: two wires are for power, and two wires are for signaling.
A small cam is turned by the motor, which presses a microswitch on the start
and end position. I believe that the controller will measure this, and expects
a change of signal when the motor is powered.

{% responsive_image path: "assets/posts/2025-12-09/inside-motor.jpeg" alt: "Inside the motor part. The small microswitch is located above the top gear." %}

Before opening it up, I already noticed that the motor would not spin. But
after opening it up and applying some grease, it started to work again. At
least it was not dirty on the inside, so it was not due to water ingress. The
gears were in good condition too, so I presume that something internally bound,
causing the motor to stall and the locking pin to not move. So even though I
have it fixed right now, next time it would fail, I would defintely replace
the motor with a new one, but then I would do it myself.

[1]: https://www.bolidenforum.de/forum/vag-tpi-2024/4690466-tpi-nr-2051071-6-elektrik-ladestecker-ladekabel-laesst-sich-nicht-verriegeln-entriegeln
