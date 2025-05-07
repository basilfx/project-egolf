---
layout: post
title: Charger investigation
date: 2025-05-08 00:00:00 +0200
tags: charging, troubleshooting
---
Since I had a flat battery, I did not dare to charge the car overnight. But
during this weekend, I noticed odd behavior with the car and/or charger. This
behavior is something I never noticed with our primary car.

I have an Alfen Eve Mini charger (which got rebranded to Alfen Single Pro
Line). I bought this charger from my former employer when I left. It is a nice
charger, as long as you do not require support. In short, I encountered two
incidents where I required technical support from Alfen, but Alfen does not
deal with customers directly. My former employer was the registered
administrator of my charge point in Alfen's system, but they sold it to me
under the condition that I had to manage it myself. I ended up in limbo. With
the help of a few people on the internet, I was able to solve this.

Returning to the unusual behavior I observed: When charger was completed (or
paused), I noticed that the charger kept making a clicking sound (the
high-voltage switch). On the display I noticed that it went to a charging
state, only drawing a few watts. After a minute or so, it went into a sleep
state. This kept on repeating, and is probably the reason why the car battery
drained: it never got a chance to go into a proper deep sleep power state.

I took a look at the log file of the charger. Here is a part of the day the
battery died:

```
2025-05-02T06:56:53.742Z:INFO:taskMaster.c:4887:Socket #1: state led   : WAIT_FOR_EVCONNECT
2025-05-02T06:56:53.734Z:INFO:taskMaster.c:4880:Socket #1: state Mode-3: STATE_B2
2025-05-02T06:56:53.722Z:INFO:taskMaster.c:4873:Socket #1: state power : POWER_MAIN_OFF_BYPASS_OFF
2025-05-02T06:56:53.714Z:INFO:taskMaster.c:4865:Socket #1: state main  : CHARGING_POWER_OFF
2025-05-02T06:56:54.789Z:INFO:taskMain.c:1415:Socket #1: main state: CHARGING_POWER_OFF, CP: 8.4/-11.0, tag: 19902004
2025-05-02T06:56:54.078Z:INFO:taskMain.c:6693:Socket #1: CPhigh 8.4 V
2025-05-02T06:56:53.839Z:COM:ocpp_rpc.c:1292:<- [3,"658",{}]

2025-05-02T06:56:53.753Z:COM:ocpp_rpc.c:715::"SuspendedEV"}]

2025-05-02T06:57:03.898Z:INFO:taskMain.c:6761:Socket #1: reset HF switch count 3
2025-05-02T06:57:06.777Z:USER:taskMaster.c:6673:Socket #1: I1=0.0A I2=0.0A I3=0.0A P=0.0kW Idc=0.0mA
2025-05-02T06:57:06.761Z:USER:taskMaster.c:6637:Socket #1: L1N=238.9V L2N=238.5V L3N=237.6V L1L2=413.0V L2L3=412.7V L3L1=412.9V
2025-05-02T06:57:24.753Z:INFO:taskMain.c:1415:Socket #1: main state: CHARGING_WAKEUP, CP: 0.0/0.0, tag: 19902004
2025-05-02T06:57:24.082Z:INFO:taskMain.c:6698:Socket #1: CPlow 0.0 V
2025-05-02T06:57:24.074Z:INFO:taskMain.c:6693:Socket #1: CPhigh 0.0 V
2025-05-02T06:57:23.792Z:INFO:taskMaster.c:4880:Socket #1: state Mode-3: STATE_E
2025-05-02T06:57:23.757Z:INFO:taskMaster.c:4865:Socket #1: state main  : CHARGING_WAKEUP
2025-05-02T06:57:29.507Z:INFO:taskMaster.c:4865:Socket #1: state main  : CHARGING_POWER_ON
2025-05-02T06:57:29.324Z:INFO:taskMain.c:1415:Socket #1: main state: CHARGING_POWER_OFF, CP: 8.4/-11.0, tag: 19902004
2025-05-02T06:57:28.812Z:INFO:taskMain.c:6698:Socket #1: CPlow -11.0 V
2025-05-02T06:57:28.269Z:INFO:taskMaster.c:4880:Socket #1: state Mode-3: STATE_B2
2025-05-02T06:57:28.261Z:INFO:taskMaster.c:4865:Socket #1: state main  : CHARGING_POWER_OFF
2025-05-02T06:57:27.792Z:INFO:taskMain.c:6698:Socket #1: CPlow 8.3 V
2025-05-02T06:57:27.785Z:INFO:taskMain.c:6693:Socket #1: CPhigh 8.3 V
2025-05-02T06:57:27.757Z:INFO:taskMaster.c:4880:Socket #1: state Mode-3: STATE_B1
2025-05-02T06:57:30.523Z:INFO:taskMain.c:1415:Socket #1: main state: CHARGING_POWER_ON, CP: 5.7/-11.0, tag: 19902004
2025-05-02T06:57:30.332Z:INFO:taskMain.c:6693:Socket #1: CPhigh 5.6 V
2025-05-02T06:57:29.675Z:COM:ocpp_rpc.c:1292:<- [3,"659",{}]

2025-05-02T06:57:29.585Z:COM:ocpp_rpc.c:715::"Charging"}]

2025-05-02T06:57:29.585Z:COM:ocpp_rpc.c:715:-> [2,"659","StatusNotification",{"connectorId":1,"errorCode":"NoError","status"
2025-05-02T06:57:29.570Z:INFO:taskMaster.c:4887:Socket #1: state led   : CHARGING_POWER_ON
2025-05-02T06:57:29.562Z:INFO:taskMaster.c:4880:Socket #1: state Mode-3: STATE_C2
2025-05-02T06:57:29.550Z:INFO:taskMaster.c:4873:Socket #1: state power : POWER_MAIN_ON_BYPASS_ON
2025-05-02T06:57:29.542Z:USER:taskMaster.c:6673:Socket #1: I1=0.0A I2=0.0A I3=0.0A P=0.0kW Idc=0.0mA
2025-05-02T06:57:29.527Z:USER:taskMaster.c:6637:Socket #1: L1N=238.7V L2N=238.2V L3N=238.3V L1L2=412.5V L2L3=413.0V L3L1=413.0V
2025-05-02T06:57:29.519Z:INFO:taskMaster.c:6591:Start logging meter values @30s.
2025-05-02T06:57:59.566Z:USER:taskMaster.c:6673:Socket #1: I1=0.4A I2=0.4A I3=0.0A P=0.0kW Idc=0.0mA
2025-05-02T06:57:59.554Z:USER:taskMaster.c:6637:Socket #1: L1N=239.0V L2N=238.4V L3N=237.3V L1L2=412.8V L2L3=412.3V L3L1=412.7V
2025-05-02T06:58:17.695Z:INFO:taskMain.c:1415:Socket #1: main state: CHARGING_POWER_OFF, CP: 8.4/-11.0, tag: 19902004
2025-05-02T06:58:16.980Z:INFO:taskMain.c:6693:Socket #1: CPhigh 8.4 V
2025-05-02T06:58:16.914Z:COM:ocpp_rpc.c:1292:<- [3,"660",{}]

2025-05-02T06:58:16.691Z:COM:ocpp_rpc.c:715::"SuspendedEV"}]

2025-05-02T06:58:16.691Z:COM:ocpp_rpc.c:715:-> [2,"660","StatusNotification",{"connectorId":1,"errorCode":"NoError","status"
2025-05-02T06:58:16.683Z:INFO:taskMaster.c:4887:Socket #1: state led   : WAIT_FOR_EVCONNECT
2025-05-02T06:58:16.671Z:INFO:taskMaster.c:4880:Socket #1: state Mode-3: STATE_B2
2025-05-02T06:58:16.660Z:INFO:taskMaster.c:4873:Socket #1: state power : POWER_MAIN_OFF_BYPASS_OFF
2025-05-02T06:58:16.652Z:INFO:taskMaster.c:4865:Socket #1: state main  : CHARGING_POWER_OFF
2025-05-02T06:58:20.445Z:INFO:taskMain.c:1415:Socket #1: main state: CHARGING_POWER_ON, CP: 5.6/-11.0, tag: 19902004

2025-05-02T06:58:19.917Z:COM:ocpp_rpc.c:1292:<- [3,"661",{}]

2025-05-02T06:58:19.742Z:COM:ocpp_rpc.c:715::"Charging"}]
2025-05-02T06:58:19.742Z:COM:ocpp_rpc.c:715:-> [2,"661","StatusNotification",{"connectorId":1,"errorCode":"NoError","status"
```

Notice how it switches between 'charging' state and 'suspended EV'? The latter
is a state when vehicle suspends charging. This makes me believe it is a
vehicle problem. It could still be a software issue, or the 12 V battery is at
the end of its lifespan, and the vehicle keeps trickle charging it, waking up
the whole vehicle in the process. On the other hand, I am not the first owner
of this vehicle, which may put the fault at the charger (or the combination of
both).

To further visualize this, I decided to plot the number of charger state
changes over time, and here is what I got. Remember, our primary car has no
issues, and we charged that one during the rest of the month.

{% responsive_image path: "assets/posts/2025-05-08/updates.png" alt: "Problem 2" %}
