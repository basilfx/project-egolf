---
layout: post
title: ESC button (part 1)
date: 2025-05-29 00:00:00 +0200
tags: esc, asr, button, retrofit
---
Another retrofit where I probably have more joy in doing all the research then
actually using it. But I also like to have more buttons in the center console.

{% responsive_image path: "assets/posts/2025-05-29/button-1.jpeg" alt: "ESC button in the center console in a GTI." %}

The e-Golf has the same ABS pump as all the other models, even the more
sportier onces. Some of these models have a dedicated button in the center
console to toggle between different electronic stability control (ESC) and
traction control (ASR) programs. The following options are generally availble:

* ESC & ASR enabled
* ESC Sport
* ESC Off
* ASR Off

ESC and ASC enhance stability. But sometimes you want to disable it. It can
be disabled via the infotainment menu, or via a dedicated button. This button
is not standard on most variants of the Golf. But it can be [retrofitted][1].

The part number I need is `5G1 927 137 AA`, because I also have the driving
mode switch.

{% responsive_image path: "assets/posts/2025-05-29/button-2.jpeg" alt: "Center console buttons part." %}

## Coding the ABS module
The available programs are controlled by the ABS module (J104, or block 03). I
first decided if the e-Golf would accept the additional programs to make it
worth the effort. I did the same adaption on my Volkswagen Polo MY2016, so I
knew what to expect.

1. Go to module 03-ABS Brakes.
2. Go to coding (there are no labels).
3. Change byte 29 to end with a `9`. In my case, I changed `E2` to `E9`.

This will enable the ESC Sport option. Other options are [available][1].

The final coding is `01FA40A12C20216E4778060841C92980023484E26082943338915078C2E903`.

In the menu, I now have more options to choose from. They seem to work just
fine.

{% responsive_image path: "assets/posts/2025-05-29/esc.jpeg" alt: "ESC sport is now an option." %}

## Checking the wiring
The ABS module has a 46-pin connector on the e-Golf. Pin 39 of this connector
is connected to the button in the center console. I checked the wiring diagrams
of my e-Golf, and compared this to a Golf GTI. The e-Golf wiring diagrams show
that this pin is not populated, but the Golf GTI does.

{% responsive_image path: "assets/posts/2025-05-29/wiring-1.png" alt: "Partial pinout of the 46-pin ABS pump connector for an e-Golf." %}

{% responsive_image path: "assets/posts/2025-05-29/wiring-2.png" alt: "Partial pinout of the 46-pin ABS pump connector for a Golf GTI." %}

On some Golf variants, this pin is pre-wired to the so-called TIUL coupling
point, next to the footrest, even if the button is not installed. I removed
this connector, and verified that pin 5 was not populated, which was to be
expected. This means that I will have to run a wire through the firewall of
the car, then from the coupling point to the center console.

{% responsive_image path: "assets/posts/2025-05-29/tiul.jpeg" alt: "The TIUL coupling point, pin 5 is the third pin from the left on the bottom row." %}

I will probably test this first, by connecting a wire to the 46-pin connector
on the ABS pump first, then 'toggle' it by momentarily connecting it to 12 V.
According to the schematic, the switch will connect that pin to a 12 V source
once pressed. This way, I know if it is worth the effort to run the wire
through the firewall.

{% responsive_image path: "assets/posts/2025-05-29/schema.png" alt: "E256 is the button in the center console (I believe the symbols are reversed)." %}

## The hardware

[1]: https://www.golfmk7.com/forums/index.php?threads/how-to-retro-fit-the-traction-control-esc-button-to-a-mk7-golf.320066/
