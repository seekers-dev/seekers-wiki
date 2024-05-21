---
layout: page
title: Config
parent: More Resources
nav_order: 6
---

# Config

Games are hosted with a configuration. You can change the configuration by editing the config file. In the description below you can see which properties change what aspect.

## Global

```ini
[global]
# wait until every AI has submitted its orders before performing the next game tick [bool]
wait-for-players=true
# time until the game ends [int]
playtime=5000
# frames per second [int]
fps=60
# number of updates every frame [int]
speed=2
# number of players (see auto-play) [int]
players=2
# number of seekers per player [int]
seekers=5
# number of goals [int]
goals=5
# color threshold for avoidance of similar colors [float]
color-threshold=0.1
```

## Map

```ini
[map]
# map dimensions [int]
width=768
height=768
```

## Camp

```ini
[camp]
# camp dimensions [int]
width=55
height=55
```

## Physical

```ini
[physical]
# friction of any physical [float]
friction=.02
```

## Seeker

```ini
[seeker]
# length of the acceleration vector of a seeker [float]
thrust=0.1
# ratio of the thrust of a seeker when its magnet is active [float]
magnet-slowdown=.2
# time until a seeker becomes active again [int]
disabled-time=250
# radius of a seeker [float]
radius=10
# mass of a seeker [float]
mass=1
```

## Goal

```ini
[goal]
# time until a goal gets scored [int]
scoring-time=100
# radius of a goal [float]
radius=6
# mass of a goal [float]
mass=.5
```

## Flags

```ini
[flags]
# enable experimental friction, as implemented by joendter [bool]
experimental-friction=false
# enable student's t-test, this requires scipy [bool]
t-test=false
# draw the game relative to [str]
# center - the center of the map
# player/<player_index>/<seeker_index> - the specified seeker of the specified player
# goal/<goal_index> - the specified goal
relative-drawing-to=center
```