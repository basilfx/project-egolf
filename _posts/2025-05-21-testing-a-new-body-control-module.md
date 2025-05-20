---
layout: post
title: Testing a new body control module
date: 2025-05-21 00:00:00 +0200
tags: bcm, test-bench, odis-s, ambient-lighting
---
The body control module (BCM) connects to many sensors, actuators, and lights
within the vehicle. They come in different tiers, such as low-line,
medium-line, and high-line. Depending on the vehicle and chosen options, a
specific BCM will be installed. The different versions have very similar
hardware but might differ on a few pins added or removed. Because 99% of the
hardware is identical, you can often flash firmwares of high-line versions on
lower-line versions. Obviously, this does not give you the new features that
require physical pins.

My vehicle is equipped with `5Q0 937 084 CF` based on `H36`. It runs software
`5Q0 937 084 CP`. This makes it a medium-line BCM. I know from ETKA that the
e-Golf was produced with `5Q0 937 084 DD` and `5Q0 937 084 DH` for newer model
years. I do not know which hardware version, but based on [this][1] source, it
is probably `H38` or `H40`.

My end goal is to upgrade the BCM to a high-line version for two reasons:

1. I need a high-line version for ambient lighting.
2. I want to run a newer software version.

I have done a BCM swap on a PQ35 vehicle, which was much easier than with MQB.
First of all, all of the long coding got moved to adaptions. My vehicle already
has more than 2500 adaptions, and newer software versions have even more.
Second, the BCM can be parameterized and requires a parameter set. I am not
really sure what this parameter actually does. I have found a parameter set
for a Volkswagen Tiguan and an AUDI A3 for the same BCM, and both files were
only a few kilobytes. That is not enough to cover defaults for all the
adaptions stored in the vehicle. And lastly: the BCM has component protection,
so you need access to ODIS-S with GeKo to remove component protection.

## The new BCM
I found a `5Q0 937 084 DD` with `H38`. This version supports ambient lighting
with 30 colors. Under the hood, this is just a `5Q0 937 084 CG` with a newer
firmware from the factory. This BCM is a high-line version and has the
pin necessary for ambient lighting (T73c/29). This second-hand BCM was
previously installed in a Skoda Superb MY2019.

{% responsive_image path: "assets/posts/2025-05-21/bcm.jpeg" alt: "The new BCM (ignore the masking tape)." %}

I asked the shop that sold me the BCM for a cut-off set of connectors. Some of
the listings I found online had BCMs with the connectors still attached, so I
figured that they would either be trash. However, that shop asked a fortune for
something that would otherwise be thrown away, so I end up not buying them.

That left me with a small challenge to connect the BCM to my test bench. I did
not want to install this BCM in the vehicle yet, because I wanted to prepare it
first. I ended up with using DuPont female pins with a bit of shrink wrap on
smaller pins, and some female Junior Power Terminals with shrink wrap on the
larger pins.

{% responsive_image path: "assets/posts/2025-05-21/wiring.jpeg" alt: "Wiring of the BCM on the test bench." %}

As you can see, most of the wires are connected to the A-side connector. That
is sufficient to get it up and running.

* T73a/1 -> Terminal 30 (12 V)
* T73a/12 -> Terminal 31 (ground)
* T73a/14 -> T20/14 (Gateway)
* T73a/16 -> Comfort CAN bus high
* T73a/17 -> Comfort CAN bus low
* T73a/44 -> Terminal 15 (12 V)
* T73a/47 -> Terminal 15 (12 V)
* T73a/63 -> Terminal 31 (ground)
* T73a/66 -> Terminal 30 (12 V)
* T73a/73 -> Terminal 30 (12 V)

For the C-side:

* T73c/1 -> Terminal 30 (12 V)
* T73c/63 -> Terminal 31 (Ground)
* T73c/73 -> Terminal 30 (12 V)

Initially I had an issue with the BCM going into sleep mode, even though I had
built the [emulator][2] to broadcast the `Klemmen_Status_01` message on the CAN
bus. After inspecting the status of Terminal 15 according to the CAN bus, I
noticed that it was not stable. When I disconnected the BCM, the issue
disappeared.

After some testing, I [found][3] out I had to connect T73a/44 and T73a/47. Then
the status became stable and the BCM did not fall asleep.

I have ordered a dedicated connector with partnumber `5Q0 937 700 B` (for the
A-side), so I can connect the pins more safely.

## Ambient lighting
Since my final goal is to add ambient lighting to the vehicle, I wanted to test
this out. Ambient lighting uses a single-wire LIN bus. Every light is connected
to the same wire and has its own group address. Pin T73c/29 on the BCM is
where this wire starts.

At first, I connected a wire to this pin. I measured its voltage, but it was
close to zero. Because there were still many faults in the BCM related to
missing supply voltages, I first ensured that the C-side of the BCM got some
power connected. After that, the errors disappeared, and the pin showed a
higher voltage.

Using VCDS or ODIS-E, there are ways to test specific functionality. There is a
so-called 'output test' for ambient lighting. Unfortunately, I was not able to
get the light to work, most likely because I had not properly coded it. I have
to assign the correct group address to the desired light group, such that the
vehicle knows which lights to adapt when you change a certain light group
(e.g., the footwell lights). I confirmed that this pin was actually sending out
data using an oscilloscope.

## Up and down
From the community, I knew that I could flash this BCM to version
`5Q0 937 084 EC`. There are no known advantages for the e-Golf, but it feels
good to run a newer firmware version. `DD` is probably released in 2018, `EC`
is available since 2013. Using the flash file `FL_5Q0937084EC_1513_S.frf`, I
was able to flash it using ODIS-E. This operation took about four minutes.

{% responsive_image path: "assets/posts/2025-05-21/odis-e.png" alt: "Summary of the ODIS-E flashing operation." %}

The EEPROM and parameter set were not affected. As can be seen in the above
screenshot, this remained `V03935283PX`.

The next step I had to perform was to compare the adaptions of my vehicle's
BCM and the new one. Using VCDS, it is quite easy to make an export of the
adaption maps, and then compare it using a text compare tool. This resulted in
many differences, especially in the configuration of all the lighting
adaptions. This was expected, of course.

I had two options to resolve these differences:

1. Restore adaptions (using VCDS).
2. Get access to ODIS-S and restore configuration.

Option one would work, but since the `EC` (but also `DD`) has more adaptions
than the original `CG`, there will be options that I cannot match. Also, it
will still have the parameter set name `V03935283PX`, which is for a Skoda
Superb MY2019.

The second option requires access to ODIS-S with an online account. I was able
to get access (SVM is sufficient), which gave me the possibility to restore the
module with the configuration from the factory. But here is the catch: the
BCM with software `EC` never existed for the e-Golf, let alone my specific
model year. ODIS-S will therefore fail when trying to restore the
configuration. But the e-Golf was produced with a `DD` BCM, so I figured that
if I could find a VIN of an e-Golf with BCM `DD`, then I could try that.

I got one step further in the process, but eventually it failed with a similar
error that `EC` was too new. I figured that I could downgrade back to `DD`
first using the flash file `FL_5Q0937084DD_0273_S.frf`, and then try it again.
And this worked!

{% responsive_image path: "assets/posts/2025-05-21/identification.jpeg" alt: "Advanced module identification using VCDS." %}

The parameter set is now `V03935289SL`. I also compared the adaptions, and this
was a better match with my own BCM. Still a lot of adaptions that I will need
to adjust, but this is the closest I can get to a BCM for an e-Golf.

[1]: https://www.drive2.ru/b/689173339607946503/
[2]: {% post_url 2025-05-15-a-gateway-on-a-test-bench %}
[3]: https://www.golfmk7.com/forums/index.php?threads/mqb-platform-test-bench-attempt.448109/page-2
