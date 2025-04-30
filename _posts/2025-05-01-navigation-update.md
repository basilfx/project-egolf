---
layout: post
title: Navigation update
date: 2025-05-01 01:00:00 +0200
tags: navigation, firmware-update
---
The first change I made to the car was updating the navigation system—both the
firmware and the maps, and while I was at it, I also updated the speed cameras
as points of interest.

I live in a street that did not exist when the car was manufactured. The
previous owner did not care to update the maps. So for aesthetic reasons, the
first thing I did was update the maps. I did not want the vehicle to think I
parked it in a grassland every time I came home. Version 24.10 was the latest
version available at the time of writing. It can be downloaded for free from
the Volkswagen website. Once downloaded, it must be extracted onto a USB stick
or SD card. After inserting it into the car, the update can be started from the
advanced section in the navigation view.

The next thing I did was to update the firmware of the head unit. Volkswagen
does not provide these updates for free, but using the website
[mib-helper.com][1], I was able to determine whether an update was available
for my head unit.

{% responsive_image path: "assets/posts/2025-05-01/before.jpeg" alt: "Software version before the software update." %}

According to the software menu (hold the menu button for a few seconds), the
version I had was `MHI2_ER_VWG13_P4521` with `MU: 1161`. According to the above
website, `MHI2_ER_VWG13_K4525` with `MU: 1367` was the latest version
available. I got a hold of this update, installed it on a USB stick and started
the update from the software version menu.

{% responsive_image path: "assets/posts/2025-05-01/after.jpeg" alt: "Software version after the software update." %}

After some googling, I found out that TPI 2053827/3 [applies][2] to this
update. Here is the translated changelog:

```
Navigation/route:
* The destination entry in the display control unit of the radio navigation
  system cannot be confirmed. The "OK" button is grayed out.
* In navigation mode, the arrival time is not calculated correctly/implausibly.

Radio/settings/functions:
* After switching on the ignition, a pop-up for software update appears in the
  display control unit of the radio navigation system.
* Not all buttons are displayed/displayed in the menu for personalization.
* DAB+ stations are not stored / are sometimes deleted.
* A pop-up for license update appears in the display control unit of the radio
  navigation system.

Driver assistance systems:
* If the system language in the radio navigation system is set to "Arabic", the
  camera image "Area View" is not displayed correctly.

Car-Net:
* Non-existent or incorrectly displayed/displayed confirmation pop-up for
  remote update.
```

The final step I performed was installing a speed camera database. I downloaded
the latest set from [MIB Speedcam][3] and followed their instructions. The map
now displays small icons for speed cameras, which is a very nice enhancement.

[1]: https://www.mib-helper.com/
[2]: https://www.motor-talk.de/forum/discover-pro-firmware-update-1367-tpi-t6800106.html
[3]: https://t.me/mibspeedcam
