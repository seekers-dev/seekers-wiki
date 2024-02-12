# Write an AI

## Create your file

Create a file that starts with `ai` and ends with `.py`. Everything between is up to you and should represent the name of your team.

At the very top of your file, import the default definitions.

```py
from seekers import *
```

Then, create a function with the following signature:

```py
def decide(own_seekers: list[Seeker], other_seekers: list[Seeker], all_seekers: list[Seeker], goals: list[Goal],
           other_players: list[Player], own_camp: Camp, camps: list[Camp], world: World, passed_time: float):
    ...
    return own_seekers
```

The function must be called `decide`, takes 9 arguments and returns a list of the modified seekers.

Inside the function, you can write your code.

## Set color

You can specify the color of your ai by adding the following code at the top of your file.

```py
__color__ = (255, 0, 0)
```

This will result in a red color. The color property uses rgb values.

## Full code and other examples

This is the full code of this tutorial:

```py
from seekers import *


__color__ = (255, 0, 0)

def decide(own_seekers: list[Seeker], other_seekers: list[Seeker], all_seekers: list[Seeker], goals: list[Goal],
           other_players: list[Player], own_camp: Camp, camps: list[Camp], world: World, passed_time: float):
    ...
    return own_seekers
```

You can check out all examples [here](https://github.com/seekers-dev/seekers-py/tree/master/examples).