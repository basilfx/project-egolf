---
layout: post
title: A list of small changes
date: 2025-05-14 00:00:00 +0200
tags: vcds, coding, adaptions
---
This is a list of minor coding and adaption changes I applied since I own the
car. I used VCDS to make these changes.

## Disable day-time running lights
When performing codings and adaptions, I prefer to disable lights and HVAC to
reduce power consumption. The day-time running lights cannot be disabled by
default, but the option below will add an option in the lights configuration
menu to disable them.

1. Go to module 09-Central Electronics.
2. Use the security access login code 31347.
3. Go to adaptions.
3. Change the value of
  `ENG141647-ENG116594-Außenlicht_Front-Tagfahrlicht Aktivierung durch BAP oder Bedienfolge moeglich`
  to `active`.

## Enable needle sweep and lap timer in instrument cluster
This makes the instrument cluster more fun. The analog instrument cluster of
the e-Golf is boring, in my honest opinion.

1. Go to module 17-Instruments.
2. Go to coding.
3. Change byte 1, bit 0 to `Gauge Test/Needle Sweep active`.
4. Change byte 1, bit 3 to `Lap Timer active`.

The final long coding is `07AD28186F8C00080188690B5601082080000000`.

## Acoustic locking confirmation
I do not use this feature a lot, but I can easily toggle it from the locks
and windows configuration menu.

1. Go to module 09-Central Electronics.
2. Use the security access login code 31347.
3. Go to adaptions.
4. Change the value of
   `IDE02269-ENG116666-Acknowledgement signals-Akustische Rueckmeldung entriegeln`
   to `active`.
5. Change the value of
   `IDE02269-ENG116667-Acknowledgement signals-Akustische Rueckmeldung verriegeln`
   to `active`.
6. Change the value of
   `IDE02269-ENG116669-Acknowledgement signals-Akustische Rueckmeldung global`
   to `active`.
7. Change the value of
   `IDE02269-ENG122188-Acknowledgement signals-Menuesteuerung akustische Rueckmeldung`
   to `active`.

## Enable off-road menu in infotainment display
This will add an off-road menu to the infotainment display, where you can see
show meters with the current altitude, steering angle and so forth.

1. Go to module 5F-Information Electronics.
2. Go to adaptions
3. Change the value of
   `ENG122227-ENG117566-Car_Function_Adaptations_Gen2-menu_display_compass`
   to `activated`.
4. Change the value of
   `ENG122227-ENG117568-Car_Function_Adaptations_Gen2-menu_display_compass_over_threshold_high`
   to `activated`.
5. Change the value of
   `ENG122229-ENG117732-Car_Function_List_BAP_Gen2-compass_0x15`
   to `activated`.

## Colors in infotainment display and instrument cluster
With this change, you can change the border and background colors in your
instrument cluster and navigation display.

1. Go to module 09-Central Electronics.
2. Use the security access login code 31347.
3. Go to adaptions.
4. Change the value of
   `IDE09731-ENG125015-Int. light: 2nd generation-weicher Farbwechsel`
   to `active`.
5. Change the value of
   `IDE09731-ENG125017-Int. light: 2nd generation-Instrumententafelbeleuchtung mehrfarbig`
   to `active`.
6. Change the value of
   `IDE09731-ENG154513-Int. light: 2nd generation-Ambiente_Farbwahl_FPA_waehlbare_Kopplung`
   to `active`.
7. Change the value of
   `IDE09731-ENG154514-Int. light: 2nd generation-Ambiente_Farbwahl_FPA_waehlbare_Kopplung_Status_hmi_default`
   to `coupled`.
8. Change the value of
   `IDE09732-ENG115870-Interior light: light configuration-Ambiente_Applikationsleisten_in_Instrumententafel`
   to `installed`.
9. Change the value of
   `IDE09732-ENG126835-Interior light: light configuration-Ambientemenue mit globalem aus`
   to `active`.
10. Change the value of
    `IDE09732-ENG126836-Interior light: light configuration-Ambientemenue mit alle Zonen`
    to `active`.
11. Change the value of
    `IDE09732-ENG133384-Interior light: light configuration-Ambient_Farbliste_HMI`
    to `active`.

I decided to use OBDEleven and spend some credits to code all 30 colors for me,
otherwise I had to adapt 30 colors times three channels. If you feel like it,
you would need to adapt the channels such as the ones below.

* `IDE11714-ENG126825-Ambient light color list-Rotwert Farbe 1`
* `IDE11714-ENG126826-Ambient light color list-Gruenwert Farbe 1`
* `IDE11714-ENG126827-Ambient light color list-Blauwert Farbe 1`
* ...

Because I have the personalization feature, I also adapted the gateway to
remember the chosen color per driver profile.

1. Go to module 19-Gateway.
2. Go to coding.
3. Change byte 11, bit 7 and enable `FPA_Funktion_AMB`.

The final long coding for the gateway is `0201001704F81000FB001290081D00000001070100070000000300000000`.

After all the changes, I can now change the colors. This will become even more
prominent when the active info display is retrofitted.

{% responsive_image path: "assets/posts/2025-05-14/colors-1.jpeg" alt: "The list of 30 colors to choose from." %}

{% responsive_image path: "assets/posts/2025-05-14/colors-2.jpeg" alt: "The chosen color becomes visible in the instrument cluster." %}
