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

`Python 3.9.6 (tags/v3.9.6:db3ff76, Jun 28 2021, 15:26:21) [MSC v.1929 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.`,

your installation was successful; exit the Python command line mode again by entering `exit()`.
If the `python` command threw an error, try the commands `py` or `python3`.
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

Now we get into installing Seekers itself.
