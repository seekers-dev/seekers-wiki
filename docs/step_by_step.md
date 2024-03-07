# Step by step introduction

This tutorial will take you, step by step, from installing the necessary files for Seekers to creating your first simple AI.
It then also gives a small overview on what you could do afterwards to refine and optimize your bot.

## Installation

### Installing Python

First, you'll need to install [Python](https://www.python.org/downloads/). We recommend downloading the latest stable version, however, anything that is Python 3.9 or above
should work. The installing wizard as shown in the next picture usually does all the work then.

**IMPORTANT:** Notice the check field that is marked red in this image. Activate it so Python will be added to the PATH variable of your system - not doing so might result
in your system not recognizing your installation properly.

![win_installer](https://github.com/seekers-dev/wiki/assets/46622920/7595679a-6325-4a65-8bc3-e663c030df95)

After doing this, open a command line (under Windows, press the Windows key and enter "cmd") and try the command `python`, sending it with Enter. If you see something
like this:

```shell
Python 3.9.6 (tags/v3.9.6:db3ff76, Jun 28 2021, 15:26:21) [MSC v.1929 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
```

your installation was successful; exit the Python command line mode again by entering `exit()`.
If the `python` command threw an error, try the commands `py` or `python3`. (If any of these worked, keep in mind which one did.)
If all these actions fail, try troubleshooting using the official [Python Documentation](https://wiki.python.org/moin/BeginnersGuide/Download).


### Installing an IDE

Technically, all you'd need to start programming with Python is a command line (as discussed earlier) and a text editor.
This minimalistic setting would work but has proven to be impractical in most cases, which is why we recommend using an "IDE", an "integrated development environment".

Installing Python already gives you access to Python's very own IDE "IDLE". However, IDLE has some weaknesses which makes using other editors better for learning
and developing with Python. Here's a (non-comprehensive) list of IDEs we think are useful for getting started:

* **[Visual Studio Code](https://code.visualstudio.com/Download)** ("VS Code" for short). A relatively lightweight IDE which is usable also for a lot of other programming languages.
* **[PyCharm](https://www.jetbrains.com/pycharm/download/)**. An IDE optimized for Python development. Be careful, the version presented at the top of this page is the professional version which will cost money after a 30-day trial. Make sure you scroll down and download the "PyCharm Community Edition".
* **[Geany](https://www.geany.org/download/releases/)**. Not the most common editor for Python, but still easy to use and therefore recommendable.

### Installing Seekers

Now we get into installing Seekers itself. Get the newest Seekers release [here](https://github.com/seekers-dev/seekers-py/releases) (download the "seekers-py.zip", the others won't be needed for now).

What you just downloaded is a "zip" file, which has to be unpacked to get its contents (right-clicking and "Extract all..." or similar options should do the trick). This creates a folder called "seekers-py" in your Downloads. Copy it to a place where you'll find it again later (e.g. your Desktop or into your Documents folder). Write down or memorize the directory path of your "seekers-py" folder, this is important in order to use the command line later on. From now on, we will refer to the "seekers-py" folder as your directory.

Open a command line again. Move to your directory by entering the command
```shell
cd [directory path]
```
("cd" for "change directory"), where you replace `[directory path]` with whatever path your directory has (the one you've written down). We recommend using a virtual environment for the requirements installation. If you don't want to do this, simply skip the following paragraph.

#### Virtual Environment

Sometimes it's useful to install requirements and dependencies only for the applications that will need them. For this purpose, a virtual environment ("venv" for short) comes in handy. It can be created by using the command 
```shell
python -m venv venv
```
in your directory. Note that you have to activate the virtual environment afterwards and everytime you open a new command line using `venv\Scripts\activate` (Windows) or `source venv/bin/activate` (Linux).

#### Installing requirements

Now we continue installing the needed files for Seekers, regardless of whether you use a virtual environment or not.
This is done by simply running the command 
```shell
python -m pip install -r requirements.txt
```
You might need to replace "python" by "py" or "python3", depending on which of these worked when testing your Python installation. Alternatively, `pip install -r requirements.txt` should also work.

### Testing Seekers installation

Now it's time to give Seekers a test! Take your command line in your directory and enter 
```shell
python run_seekers.py ./examples/ai-decide.py ./examples/ai-simple.py
```
A new window should open, running the game, which might look similar to the following picture:

![ingame](https://github.com/seekers-dev/wiki/assets/46622920/9729c3aa-b6f3-4132-a6d5-b3cd654b6962)

If this works, congratulations! Seekers is ready for use now and we can dive into the fun part.

## The Game

One might think of Seekers as a "zero player game": Once the game starts, players cannot interfere with their team of Seekers anymore and therefore have to rely that it makes the right decisions on its own.

The way to "play" Seekers is to program a bot function (in a sense some kind of AI) that will control your team of Seekers. Players gain points by having their Seekers transport small dots, the so-called "goals", into their own Camp, which is marked by a square with the same color as the team. To accomplish this goal, Seekers can be given a "target" to move to, but they also have a magnet which can be turned attractive or repulsive to goals, depending on the use case.

The game has a lot more to discover, but this sums it up for the first part. To go more into detail, look at [Concept](concept), which explains all mechanics you need to know. If you want to know more about the game's parameters, see [Config](config).

## Creating an AI program

Now, let's dive into programming and designing your bot program. Open a new file in your chosen IDE and save it by the name "ai[name].py" either directly in your directory, the "examples" folder or create your own folder inside of your directory. You can replace "[name]" with anything you want; it can describe the strategy or team name of your bot for instance. Just remember that the filename always has to start with "ai" and ends with ".py" (marking it is a Python file).

Let's set up the basics first.

### Basic AI programming

At the top of your program, put the line `from seekers import *`. This will allow you to access the Seekers API so you can get information about the current game state but also issue commands to your seekers team.

Not too important, but a nice to have feature, is setting the color of your team with `__color__ = ([R], [G], [B])`. If you put in whole numbers ranging from 0 to 255 for each of "[R]", "[G]" and "[B]", you can set your team's color to an RGB value (e.g. putting in (255, 0, 0) would result in a red color).

The next part will be the heart piece of your program: the "decide" function. At each time unit (so called "ticks") of the game, it will be executed and calculate the next actions for your seekers depending on the current state of game. The simplest decide function, doing exactly nothing, would look as follows:
```
def decide(own_seekers: list[Seeker], other_seekers: list[Seeker], all_seekers: list[Seeker], goals: list[Goal],
           other_players: list[Player], own_camp: Camp, camps: list[Camp], world: World, passed_time: float):
    return own_seekers
```
Note that the "arguments" of this function, i.e. the data it will make its decisions on, are on the top line after the `def` keyword, initiating a function definition.
After this top line, you could do all sorts of calculations, loops or alternatives (as explained later) that modify the target or magnet state of your seekers. To conclude your decide function, it "returns" your seekers, i.e. it tells the game what you want to do in this tick. Everything that is contained in your function _has to_ be indented, usually by 4 space characters.

This is everything your AI definitely _needs_. It won't win you games though since we trained it to do, well, nothing (yet). To test our AI, don't forget to save the file and let's have a look at a command we have used earlier:
```shell
python run_seekers.py ./[AI1 path] ./[AI2 path]
```
`run_seekers` will always start a new game, but we will have to tell it which AIs shall play against. To do this, we include the file paths to our programs into the command. Beginning a path with `./` means that we look at the path _relative_ from our directory; so if your AI is called "ai-einstein.py" and lies directly in your directory, you can give its path as "./ai-einstein.py", whereas an AI called "ai-schroedinger.py" that was located in the "examples" folder has to be referenced as "./examples/ai-schroedinger.py". Running your program this way will give you the possibility to see potential errors or bugs, see whether its behaviour is intended and analyze how to optimize it.

In case you don't have an opposing program to test against yet (later on, you can try fighting against earlier versions), we recommend using the two AIs that are premade in the "examples" folder, "ai-simple.py" (which does nothing) or "ai-decide.py" (which has a really simple algorithm implemented which we'll build again in this tutorial). Also note that anything you write after a `#` sign in a Python file is not executed and can be used as a comment.

### Simple goal hunting

For our first step, we only want a seeker to hunt down a specific goal, mindlessly moving towards it. This strategy usually won't bring you a lot of success, but at least you may _accidentally_ gain some points and, quite importantly, you learn how to set seeker targets in general.

Move into your decide function and begin typing below the top line of the function definition, but above the `return` statement. (Don't forget the indentation!)
We start by selecting one specific seeker:
```
s0 = own_seekers[0]
```
Now we have saved our own seeker with the index 0, indicated by the brackets behind the `own_seekers` list, into a variable we simply called `s0`. Note that index counting in Python and many other programming languages starts at 0; so if your list contains 5 seekers, `own_seekers[0]` will actually return you the first seeker in the list, `own_seekers[2]` the one at the third position and so on. This is also why `own_seekers[5]` will most likely give you an error, since the list element with index 5 corresponds to the sixth element in the list - which doesn't exist in this case.

We can now use this variable to make the seeker do as we please. Type into the next line:
```
s0.target = goals[0].position
```
We simply tell the seeker with index 0 to set its target to the position of the goal with index 0, which means that it will just move to this one specific goal, all the time, no matter what. It's especially important to remember that when we set a target, that target has to be _a position_, not _an object_; just putting `goals[0]` on the right side will throw an error! Don't forget to hit "Save" or press Ctrl+S, then try out your AI.

Not convinced yet? Of course, we still have some work ahead of us. We're only using one of our five seekers which is wasted potential, and that one doesn't even try to bring goals into your camp but just pushes one goal around the map. Let's optimize a bit.

Full code of this subsection:
```
from seekers import *

__color__ = (255, 0, 0)

def decide(own_seekers: list[Seeker], other_seekers: list[Seeker], all_seekers: list[Seeker], goals: list[Goal],
           other_players: list[Player], own_camp: Camp, camps: list[Camp], world: World, passed_time: float):
    s0 = own_seekers[0]
    s0.target = goals[0].position
    return own_seekers
```

### Using the magnet

We have seen that our little seeker still has some potential to use, i.e. its magnet. Take out the `s0.target = ...` line for a moment and put in
```
g0 = goals[0]
```
so we can access the goal we want to catch more easily.

Let's make a plan first: Now our strategy will be to have the seeker move, with its magnet turned off, towards the goal; when it is close enough, the seeker turns its magnet attractive and moves towards your camp. To calculate the distance, we'll need the following line:
```
dist = world.torus_distance(s0.position, g0.position)
```
We save the result in a variable called `dist` for later use. Note that `world.torus_distance()` takes, exactly as the right side of a "target setting" did, _positions_, not _objects_ as arguments. Also note that this calculation is harder than simply subtracting x- and y-values of the positions since the game is played on a torus, where distance calculation is not as trivial. For more information, see the [Concept page about Physicals](concept#physicals).

Now we have to do different things depending on how big `dist` is. Let's start with the case where the seeker is really close to the goal it's trying to gather. To make sure the following code is executed if (and only if) the condition is fulfilled, we use Python's `if` statement (notice the indentation of everything that should be executed if the condition is met):
```
if dist < 40:
    s0.set_magnet_attractive()
    s0.target = own_camp.position
```
The number 40 is arbitrary and was found out by testing a bit, but has proven to be practical in this case. If the seeker is near enough, it activates its magnet, making it attractive to goals, and the seeker heads on to your own camp whose position was got with `own_camp.position`. Let's move on to the case where the seeker is too far away, the condition therefore _not_ met. We use the `else` statement, which should be on the same indentation level as the `if` and everything else that should only be executed if the condition is not met is indented once again:
```
else:
    s0.disable_magnet()
    s0.target = g0.position
```
The code here should be straightforward in that it is similar to the snippets before. However, one might ask: "Why turn the magnet off at all?" Well, moving whilst having your magnet on has consequences:
* Seekers with an activated magnet have lowered thrust which makes them accelerate less and therefore move at a lower speed.
* Seekers that collide with other (friendly or opposing) seekers may get disabled for a short time, depending on each other's magnet state. (see [this](concept#disabled-seekers))

So, if you don't _need_ your magnet right now, it is usually a good idea to turn it off. Save again and test the bot. See? This strategy is already a bit effective - speaking for the single seeker that is doing anything. Let's get the others out of their sleep!

Full code of this subsection:
```
from seekers import *

__color__ = (255, 0, 0)

def decide(own_seekers: list[Seeker], other_seekers: list[Seeker], all_seekers: list[Seeker], goals: list[Goal],
           other_players: list[Player], own_camp: Camp, camps: list[Camp], world: World, passed_time: float):
    s0 = own_seekers[0]
    g0 = goals[0]
    dist = world.torus_distance(s0.position, g0.position)
    if dist < 40:
        s0.set_magnet_attractive()
        s0.target = own_camp.position
    else:
        s0.disable_magnet()
        s0.target = g0.position
    return own_seekers
```

### Controlling all seekers

One simple and doable approach to controlling all seekers is copying the code we've created so far for all five seekers, just replacing the numbers. This _technically_ works, but would be bad coding style. Why? Well, for the first part, you'd have to copy the code and replace the numbers without forgetting anything or making any typos or even _accidentally_ also replacing the number 40 which should stay independent from what seeker you look at. Secondly, what if you wanted to change a code snippet for all seekers? You'd have to change the code everywhere - tedious work with a lot of potential for typos or forgetting a part!

Let's make it a bit easier. First, take out the line `s0 = ...` and replace it with:
```
for i, s0 in enumerate(own_seekers):
```
whilst indenting everything behind it, except for the `return` statement. The `for` loop in Python takes a list (or any so-called "iterable") and does whatever code you put inside it; _once_ for every element in that list. In this case, we took the enumerated version of our `own_seekers` list and will then execute the code we just did for the seeker with index 0 simply for _all_ your seekers. While in the `for` loop, we can even access the variables `s0` (which now contains the specific seeker we're applying our code on in this iteration) as well as `i`, which gives us the corresponding index.

Now the only thing that is left to change is that we don't always set `g0` to the goal with index 0 (otherwise, all seekers would try to gather one single goal), but dynamically to the goal with index `i`:
```
g0 = goals[i]
```

That's it! Try out your new AI again and see the simple strategy we've developed. Great!

Full code (this is essentially the same algorithm as the example AI "ai-decide.py"):
```
from seekers import *

__color__ = (255, 0, 0)

def decide(own_seekers: list[Seeker], other_seekers: list[Seeker], all_seekers: list[Seeker], goals: list[Goal],
           other_players: list[Player], own_camp: Camp, camps: list[Camp], world: World, passed_time: float):
    for i, s0 in enumerate(own_seekers):
        g0 = goals[i]
        dist = world.torus_distance(s0.position, g0.position)
        if dist < 40:
            s0.set_magnet_attractive()
            s0.target = own_camp.position
        else:
            s0.disable_magnet()
            s0.target = g0.position
    return own_seekers
```

### And now?

It might seem like this is everything there is to discover about Seekers, but this is only the beginning! Your possibilities are only limited by your imagination: We haven't touched the repelling magnet yet, we didn't optimize goal selection, all our seekers are doing the same thing... These are just some thought provokers of common ideas, but feel free to also try crazy things! And don't forget to join [our official Discord server](https://discord.gg/gRaTCgDS9b) for news, support and a welcoming community!

Remember that the wiki sites [Concept](concept) and [Config](config) are reliable sources for what mechanics and possibilities exist in Seekers. If you can't get enough and are confident enough to read bigger pieces of code, also feel free to have a look through the ["seekers_types.py" file](https://github.com/seekers-dev/seekers-py/blob/master/seekers/seekers_types.py). If you have questions about Python itself, the [Python Documentation](https://www.python.org/doc/) might be worth a look. And if you decide to learn even more Python outside of Seekers, we recommend you Al Sweigart's (free if read as e-books!) [Books to learn Python](https://inventwithpython.com/).
