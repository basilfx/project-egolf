---
layout: post
title: Battery control unit software update
date: 2025-05-12 00:00:00 +0200
tags: software-update, charger, troubleshooting
---
Today the car got repaired under warranty. They applied the software update
for the battery control unit (J966, or block BD), replaced a relay that could
potentially get stuck and tested the 12 V battery.

Before:

```
Address BD: Hi Volt. Batt. Charg. (J966)       Labels:| 5QE-915-022-V2.clb
   Part No SW: 5QE 915 022 AG    HW: 12E 915 022 F
   Component: LMSG          H20 1097
   Serial number: 01147073170309 Dataset Number: V03935260B0001
   Coding: CA0914040400
   Shop #: WSC 00029 028 00029
   ASAM Dataset: EV_HVChargManagVWMQB 003004
   ROD: EV_HVChargManagVWMQB.rod
   VCID: 0655960518A4D3EAB56-8052

No fault code found.
```

After:

```
Address BD: Hi Volt. Batt. Charg. (J966)       Labels:| 5QE-915-022-V2.clb
   Part No SW: 5QE 915 022 BM    HW: 12E 915 022 F
   Component: LMSG          H20 1100
   Serial number: 01147073170309 Dataset Number: V03935268XK 0001
   Coding: CA0914040400
   Shop #: WSC 00029 028 00029
   ASAM Dataset: EV_HVChargManagVWMQB 003004
   ROD: EV_HVChargManagVWMQB.rod
   VCID: 0D47A9297DD2A0B2F4C-8058

No fault code found.
```

You can see that the software got updated to `5QE 915 022 BM` with `SW 1100`.
No change was made to the coding, but the dataset did change.

From the repair bill I could see that the relay that got replaced has part
number `4H09 512 53A`. It is located in the interior fuse box. I am not quite
sure what is switched by this relay though.

The 12 V battery was tested to be OK. I still have my doubts. It might have
enough capacity left for the test to pass, but it may already have degraded
enough. I already have plans to replace it nonetheless.

## Charger at fault?
When I arrived back home, I immediately tried to charge the car. That worked,
but when I paused charging from the app, the problem persisted. That was a
disappointment, especially after having driven quite a distance to reach the
dealership. As mentioned in a previous post, I did not suspect the charger to
be at fault, because our primary car charges without issues.

I was already on the [latest][1] charger firmware (7.1.6 as of writing). I
decided to ask a contact about potential issues with this firmware version. He
was not aware of any problems with version 7 or later, but did mention there
were big problems with certain cars and charger firmware version 6.4.0 and
6.5.0. He suggested that I try firmware version 6.6.2, which means I had to
downgrade.

After the downgrade, the problem disappeared. To summarize the charger
firmwares:

* 6.4.0 -> broken
* 6.5.0 -> broken
* 6.6.2 -> works
* 7.1.3 -> broken
* 7.1.6 -> broken

The downside is that I have an issue with the display failing from time to
time. The charger firmware 7.1.6 would fix that. Although the battery control
module update did not resolve the issue, at least it is now running the latest
version.

[1]: https://knowledge.alfen.com/space/IN/243466257/Release+notes+-+Firmware+updates+NG-Platform+(NG-910+%2F+NG-920)
