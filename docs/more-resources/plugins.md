---
layout: page
title: Plugins
parent: More Resources
nav_order: 7
---

# Plugins

Plugins are extensions of the classic seekers game. It is possible to add new maps, game modes or languages to seekers. Plugins are currently only supported for the seekers server.

## Adding plugins

Download the latest uber jar artifact from the release page of the plugin. A uber jar file is a java archive that wraps all dependencies. This is required to load a plugin properly.

Drop the file in the plugin folder. If you have started your server for the first time, it will create a plugin folder. The folder is created in the same folder as the server.

Edit the config. Every plugin can have a own section in the `config.ini` file. Not all plugins need this section, however, if they need it, then a missing section can lead to errors. On the readme page of the plugin, you will find further instructions for the config.

That's it! If you start the server the next time, you will see that it loads the plugin.

## Creating a plugin

Generate a new repository from the seekers plugin template.

Edit all todos. You will see that in the gradle build files you should edit the plugin name, group and version. You may want to add more dependecies.