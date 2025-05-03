---
layout: post
title: 22 degrees is too hot
date: 2025-05-04 00:00:00 +0200
tags: hvac, vcds, coding
---
A small one. For reasons I do not understand, the e-Golf always resets the
climate control temperature to 22 degrees Celsius. Is this more efficient?
I do not know. It is something that I — and former colleagues who drove an
e-Golf — never understood.

The fix is quite easy using VCDS (or similar).

1. Go to module 08-Auto HVAC.
2. Use the security access login code `S12345`.
3. Go to adaptions.
4. Change the value of `MAS07251-Cut-in behavior` to `activated`.

Next time you start the car, the last value will be remembered.
