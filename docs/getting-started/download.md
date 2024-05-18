---
layout: page
title: Download
parent: Getting Started
nav_order: 1
---

# Download

Download the latest release [here](https://github.com/seekers-dev/seekers-py/releases/tag/v0.1.0).

## Installing Python

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


## Installing an IDE

Technically, all you'd need to start programming with Python is a command line (as discussed earlier) and a text editor.
This minimalistic setting would work but has proven to be impractical in most cases, which is why we recommend using an "IDE", an "integrated development environment".

Installing Python already gives you access to Python's very own IDE "IDLE". However, IDLE has some weaknesses which makes using other editors better for learning
and developing with Python. Here's a (non-comprehensive) list of IDEs we think are useful for getting started:

* **[Visual Studio Code](https://code.visualstudio.com/Download)** ("VS Code" for short). A relatively lightweight IDE which is usable also for a lot of other programming languages.
* **[PyCharm](https://www.jetbrains.com/pycharm/download/)**. An IDE optimized for Python development. Be careful, the version presented at the top of this page is the professional version which will cost money after a 30-day trial. Make sure you scroll down and download the "PyCharm Community Edition".
* **[Geany](https://www.geany.org/download/releases/)**. Not the most common editor for Python, but still easy to use and therefore recommendable.

## Installing Seekers

Now we get into installing Seekers itself. Get the newest Seekers release [here](https://github.com/seekers-dev/seekers-py/releases) (download the "seekers-py.zip", the others won't be needed for now).

What you just downloaded is a "zip" file, which has to be unpacked to get its contents (right-clicking and "Extract all..." or similar options should do the trick). This creates a folder called "seekers-py" in your Downloads. Copy it to a place where you'll find it again later (e.g. your Desktop or into your Documents folder). Write down or memorize the directory path of your "seekers-py" folder, this is important in order to use the command line later on. From now on, we will refer to the "seekers-py" folder as your directory.

Open a command line again. Move to your directory by entering the command
```shell
cd [directory path]
```
("cd" for "change directory"), where you replace `[directory path]` with whatever path your directory has (the one you've written down). We recommend using a virtual environment for the requirements installation. If you don't want to do this, simply skip the following paragraph.

### Virtual Environment

Sometimes it's useful to install requirements and dependencies only for the applications that will need them. For this purpose, a virtual environment ("venv" for short) comes in handy. It can be created by using the command
```shell
python -m venv venv
```
in your directory. Note that you have to activate the virtual environment afterwards and everytime you open a new command line using `venv\Scripts\activate` (Windows) or `source venv/bin/activate` (Linux).

### Installing Requirements

Now we continue installing the needed files for Seekers, regardless of whether you use a virtual environment or not.
This is done by simply running the command 
```shell
python -m pip install -r requirements.txt
```
You might need to replace "python" by "py" or "python3", depending on which of these worked when testing your Python installation. Alternatively, `pip install -r requirements.txt` should also work.

## Testing Installation

Now it's time to give Seekers a test! Take your command line in your directory and enter 
```shell
python run_seekers.py ./examples/ai-decide.py ./examples/ai-simple.py
```
A new window should open, running the game, which might look similar to the following picture:

![ingame](https://github.com/seekers-dev/wiki/assets/46622920/9729c3aa-b6f3-4132-a6d5-b3cd654b6962)

If this works, congratulations! Seekers is ready for use now and we can dive into the fun part.
