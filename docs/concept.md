# Game Concept

Players compete by controlling little circles called "seekers". Every player has an underlying program, its AI. The player with the most points after [`global.playtime`](https://github.com/seekers-dev/seekers/wiki/Configuration#global) wins.

Players recieve points by bringing balls, so called "goals", to their camp.

![Ingame picture](https://user-images.githubusercontent.com/37810842/207417325-30e82c8b-b53b-44e7-9d41-ca431dc579e2.png)

In this image you see two AIs competing. Each AI gets assigned a color. 
* The colored squares are the camps of their respective AI.
* The colored big circles are the seekers of their respective AI.
* The little purple circles are the goals.

## Physicals

Every physical (seekers and goals) has a **velocity** as well as a **position**. They glide on the game surface with friction. The world is shaped like a torus, that means seekers come out the other side if they "hit a wall". The world's dimensions are defined [here](config#map).

Physicals are always circles and thus have a radius as well as a mass. They always collide with each other elastically. These attributes are stored in the config as:
* [`seeker.radius` / `seeker.mass`](config#seeker)
* [`goal.radius` / `goal.mass`](config#goal)

### Movement

In "normal mode" (see [`flags.experimental-friction`](config#flags)), the following is performed every game step for every physical:
1. The physical's velocity is multiplied by [`physical.friction`](config#physical)
2. The physical's updated acceleration is added to its velocity. The length of the acceleration vector is [`seeker.thrust`](config#seeker) except when the magnet is turned on, see below. 
3. The physical's velocity is added to its position.
4. The physical's position is normalized to "wrap around the edges".

Every goal's acceleration is just `0`.
Every seeker's acceleration is `0` while it's disabled.
One game step has the time of `1`.

## Seekers

Seekers are physicals.

Seekers have two attributes:
1. **target** (Vector (position))
2. **magnet strength** (float (number))

Seekers always accelerate towards their target.

Their magnet can attract (positive magent strength) or repel (negative magnet strength) goals. This is useful when transporting goals to the camps.
The magnet is considered "on" if its strength is unequal to zero.

### Magnet Slowdown

As long as the magnet of as seeker is turned on, its [`seeker.thrust`](config#seeker) gets multiplied by [`seeker.magnet-slowdown`](config#seeker). If the seeker turns its magnet back off, its `thrust` resets.

### Disabled Seekers

If two seekers collide, they are at risk of getting disabled.
* If you have your magnet turned on, you will get disabled.
* If both have the magnet turned off, both will get disabled.

Disabled seekers don't accelerate and their magnet turns off. Seekers are disabled for [`seeker.disabled-time`](config#seeker) ticks.

## Camps

Every player has exacly one camp placed on the map. It doesn't interact with physicals whatsoever and can be considered an overlay for a section of the map. 
The size of a camp is defined [here](config#camp).

They are important for scoring points as explained below:

## Goals

Goals are physicals. 

A player recieves a point when a goal stays in their camp for [`goal.scoring-time`](config#goal) ticks.
* The time spent in a camp is accumulated, that means it can temporarily exit the camp.
* If the goal enters another player's camp, its timer resets.

When a goal is scored, it gets placed at a random location.

## Players

Every time the player's AI is called, it can change the
1. **target**
2. **magnet strength**

of each of its seekers. 

To make this decision, it is aware of the whole game. This includes and is limited to:
* your own seekers
* the seekers of your opponents
* all goals
* all camps
* the passed playtime

### Seeker Information

* position, acceleration, velocity
* player (owner)
* magnet strength
* target
* time until they get enabled again

### Goal Information

* position, acceleration, velocity
* owner of the camp they were in last
* time that they spent in that camp

### Camp Information

* position and dimensions
* owner 