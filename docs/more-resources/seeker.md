---
layout: page
title: Seeker
parent: More Resources
nav_order: 1
---

# Seeker

Seekers are physicals.

Seekers have two attributes:
1. **target** (Vector (position))
2. **magnet strength** (float (number))

Seekers always accelerate towards their target.

Their magnet can attract (positive magnet strength) or repel (negative magnet strength) goals. This is useful when transporting goals to the camps.
The magnet is considered "on" if its strength is unequal to zero.

## Magnet Slowdown

As long as the magnet of as seeker is turned on, its [`seeker.thrust`](config#seeker) gets multiplied by [`seeker.magnet-slowdown`](config#seeker). If the seeker turns its magnet back off, its `thrust` resets.

## Disabled Seekers

If two seekers collide, they are at risk of getting disabled.
* Seekers with their magnet turned on will always get disabled.
* If both have the magnet turned off, both will get disabled.

Disabled seekers don't accelerate and their magnet turns off. Seekers are disabled for [`seeker.disabled-time`](config#seeker) ticks.
