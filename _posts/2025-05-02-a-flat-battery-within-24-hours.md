---
layout: post
title: A flat battery within 24 hours
date: 2025-05-02 00:00:00 +0200
---
Within 24 hours, the car had a flat battery, and that while charing. Around
07:00 in the morning, the alarm sounded. I quickly grapped the remote, an shut
it off. The doors were unlocked. I cannot recall if I did that using the
remote, but I could not get them locked anymore.

It was still early in the morning, so I planned to grab some more sleep. I
figured that I would take a look later this morning.

Later that morning, I tried to close it again. This time I found it strange
that the dash gave an error message. I already figured it was probably a flat
battery. At least the e-Golf was [known][1] for this problem in 2018 with some
charge points, and given that this car was from around that time, it could be
related.

Using a multimeter, I quickly verified that the battery was empty. It only read
six volts. With the new car, I also got road services, so I called them.
Although they promised to be here within 90 minutes, it took over three hours.
Next time I will jumpstart it myself.

When I bought the car, I already noticed that the battery was still original.
The date code was week 35 of 2017. A 12 V battery usually has a lifetime of
between three to eight years, so the current battery was close to that. It
could therefore also be a bad battery. Then again, it was tested to be OK
before delivery.

Later that day, I googled some more, and I found a [reference][2] to a TPI
(Technical Product Information) with the number 2055573/4. I was able to find a
copy of the TPI, which outlined the same symptoms. As a solution, it mentioned
an optimized software update for the Battery Control Unit (J966, or block BD).

The software version in the control unit in my car is `5QE 915 022 AG` with
`SW 1097`. An update to `5QE 915 022 BM` with `SW 1100` (or later) was
suggested. Based on [vag-flashinfo.de][3], I know `SW 1104` was available
already.

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

7 Faults Found:
1048928 - Function Restricted due to Insufficient Voltage
          U1400 00 [00001000] - -
          [restriction_due_to_undervoltage]
          Intermittent - Confirmed - Tested Since Memory Clear
             Freeze Frame:
                    Fault Priority: 6
                    Fault Frequency: 131
                    Reset counter: 215
                    Mileage: 76146 km
                    Date: 2025.05.02
                    Time: 07:18:04

(and a lot more faults)
```

I will have to contact the dealership to see what is possible.

[1]: https://www.ad.nl/rotterdam/laadpaal-slurpt-stroom-uit-volkswagen-accu~a27a6995
[2]: https://evw-forum.de/index.php?thread/6040-12v-batterie-nach-t%C3%BCv-leer/&postID=124744#post124744
[3]: https://vag-flashinfo.de/site/index?partno=5QE+915+022
