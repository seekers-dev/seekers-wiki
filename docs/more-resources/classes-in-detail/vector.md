---
layout: page
title: Vector
parent: Classes in detail
nav_order: 1
---

# Vector

Vector objects in Seekers are used to represent positions or velocities. All angles are given in radians.

## Properties

```x``` (float)

x component of the vector.

```y``` (float)

y component of the vector.

## Methods

``copy()`` $\rightarrow$ Vector

Returns a copy of the vector.

``dot(other: Vector)`` $\rightarrow$ float

Returns the scalar product with another vector.

``static from_polar(angle: float, radius: float)`` $\rightarrow$ Vector

Initializes a new vector from polar coordinates.