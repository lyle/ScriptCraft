# Let's begin...
[![Gitter](https://badges.gitter.im/Join Chat.svg)](https://gitter.im/walterhiggins/ScriptCraft?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

I created ScriptCraft to make it easier for younger programmers to
create their own Minecraft Mods. Mods are written using the
Javascript programming language. Once the ScriptCraft mod is
installed, you can add your own new Mods by adding Javascript (.js)
files in a directory.

 * If you're new to programming and want to start modding Minecraft, then [Start Here][ypgpm].
 * If you've already used [Scratch][scr], have attended a few
   [CoderDojo][cd] sessions, or have already dabbled with Javascript,
   then [Start Here][cda].
 * Watch some [demos][ytpl] of what you can do with ScriptCraft.

This is a simple mod in a file called greet.js in the scriptcraft/plugins directory...

```javascript
exports.greet = function( player ) {
   echo( player, 'Hello ' + player.name );
};
```

At the in-game prompt, type...

    /js greet(self)

... to see the greeting. Anything you can do using CanaryMod or CraftBukkit's API in Java, you can do using ScriptCraft in Javascript.

# Description

ScriptCraft is a plugin for Minecraft Servers which lets operators,
administrators and plug-in authors customize the game using
Javascript.  ScriptCraft makes it easier to create your own mods. Mods
can be written in Javscript and can use the full [CanaryMod API][cm]
or [Bukkit API][bukkit]. I recommend using CanaryMod because
CraftBukkit is no longer being actively developed due to a legal
dispute. The ScriptCraft mod also lets you enter javascript commands
at the in-game prompt.  To bring up the in-game prompt press the `/`
key then type `js ` followed by any javascript statement. 
For example:  `/js 1 + 1` will print 2.

ScriptCraft also includes many objects and functions to make building
and modding easier using Javascript. The Javascript `Drone` object
bundled with ScriptCraft provides an easy way to build at-scale in
Minecraft. See the attached [temple.js][temple] file for an example
of how you can use the sample Drone plugin to create new buildings in
Minecraft.

[drone]: https://github.com/walterhiggins/ScriptCraft/tree/master/src/main/javascript/drone/drone.js
[cottage]: https://github.com/walterhiggins/ScriptCraft/tree/master/src/main/js/plugins/drone/contrib/cottage.js
[temple]: https://github.com/walterhiggins/ScriptCraft/blob/master/src/main/js/plugins/drone/contrib/temple.js
[bukkit]: http://dl.bukkit.org/
[cm]: http://canarymod.net/

# Prerequisites

You will need to have Java version 6 or later installed on your
machine. Check the version by typing `java -version` at a command
prompt.  You will need to [install CanaryMod][ic] or [install Bukkit][ib] 
on your machine (I recommend using CanaryMod as Bukkit is
no longer being actively developed). CanaryMod and Bukkit are both
versions of Minecraft (server) that make it easy to install plugins
and customize Minecraft.  You can [download the CanaryMod server
here.][ic]

# Installation

If you don't want to compile from source, you can [download the
compiled plugin here][dl] and copy it the craftbukkit's plugins
directory.

# Post Install

Once installed, a new scriptcraft/plugins directory is automatically created.  All files in the scriptcraft/plugins
directory will be automatically loaded when the server starts.  *Only
players who are ops can use this plugin.* You can grant a player `op`
privileges by typing 'op <username>' at the server console prompt or
by adding the player's username to the ops.txt file in your
server directory.

Launch the server, then launch the Minecraft client and create a new
server connection. The IP address will be `localhost` . Once you've
connected to your server and have entered the game, look at a
ground-level block and type ...

    /js up().box( blocks.wool.black, 4, 9, 1 )

... This will create a black monolith structure 4 blocks wide by 9
blocks high by 1 block long.  Take a look at the
src/main/javascript/drone/drone.js file to see what ScriptCraft's
drone can do.  If you're interested in customizing minecraft beyond
just creating new buildings, take a look at [./homes/homes.js][homes] for examples of how to create a
javascript plugin for Minecraft.

[ho]: blob/master/src/main/javascript/plugins/homes/homes.js
[ar]: blob/master/src/main/javascript/plugins/arrows/arrows.js
[si]: blob/master/src/main/javascript/modules/signs/menu.js

A Javascript mod for minecraft is just a javascript source file (.js)
located in the craftbukkit/plugins/scriptcraft/plugins directory. All .js files in this
directory will be automatically loaded when the craftbukkit server
starts. To get started writing your own mod, first take a look at some
of the existing mods in the [homes][ho], [arrows][ar] and
[signs][si] directories. 

# Additional information

Because the CanaryMod API is open, all of the CanaryMod API is accessible
via javascript once the ScriptCraft plugin is loaded. There are a
couple of useful Java objects exposed via javascript in the
ScriptCraft plugin...

 * `__plugin` - the ScriptCraft Plugin itself. This is a useful
   starting point for accessing other CanaryMod objects. The `__plugin`
   object is of type [net.canarymod.plugin.Plugin][api] and all
   of its properties and methods are accessible. For example... `js
   __plugin.name` returns the plugin's name
   (javascript is more concise than the equivalent java code:
   __plugin.getName() ).

 * `server` - The top-level net.canarymod.Server object. See the [CanaryMod API docs][cmapi] for reference.

 * `self` - The player/command-block or server console operator who
   invoked the `/js` command. Again, this is a good jumping off point for
   diving into the CanaryMod API.

[dl]: http://scriptcraftjs.org/download
[api]: https://ci.visualillusionsent.net/job/CanaryLib/javadoc/
[ib]: http://wiki.bukkit.org/Setting_up_a_server
[ic]: http://canarymod.net/releases
[cbdl]: http://dl.bukkit.org/downloads/craftbukkit/
[cmapi]: https://ci.visualillusionsent.net/job/CanaryLib/javadoc/

# Contributing

If you would like to contribute source code and/or documentation changes please [read contributing.md][contrib]

## Status

[![Travis Build Status](https://api.travis-ci.org/walterhiggins/ScriptCraft.png)](http://travis-ci.org/walterhiggins/ScriptCraft)

# Bukkit Configuration 
## (You can ignore this if usng CanaryMod)

ScriptCraft also works with Bukkit Plugin and uses the Bukkit Configuration
API. On first loading, ScriptCraft will create a config.yml file in
the plugins/scriptcraft/ directory. This file looks like this...

    extract-js:
      plugins: true
      modules: true
      lib: true

This file allows scriptcraft admins to turn on or off re-unzipping of the `modules`,
`plugins` and `lib` folders when deploying a new version of
scriptcraft. It's strongly recommended that the `lib` directory always
be set to true to get the latest core scriptcraft code . The modules
and plugins directories are optional and not part of scriptcraft core.

# Further Reading

ScriptCraft has [its own website][website] with further information.

 * To get started using ScriptCraft to Learn Javascript, read [The Young Person's Guide to Programming in Minecraft][yp].
 * The ScriptCraft [API documentation][api].
 * To delve deeper into creating your own minecraft mod for use by others, read [Creating a complete Minecraft Mod in  Javascript][mm].
 * Take a look at some [examples][ex]

You can find more information about [ScriptCraft on my blog][blog].

[blog]: http://walterhiggins.net/blog/cat-index-scriptcraft.html
[buk]: https://github.com/walterhiggins/ScriptCraft/blob/master/bukkit.md
[yp]: docs/YoungPersonsGuideToProgrammingMinecraft.md
[mm]: docs/Anatomy-of-a-Plugin.md
[api]: https://github.com/walterhiggins/ScriptCraft/blob/master/docs/API-Reference.md
[website]: http://scriptcraftjs.org/
[ypgpm]: docs/YoungPersonsGuideToProgrammingMinecraft.md
[cd]: http://coderdojo.com/
[scr]: http://scratch.mit.edu/
[cda]: http://cdathenry.wordpress.com/category/modderdojo/
[ytpl]: http://www.youtube.com/watch?v=DDp20SKm43Y&list=PL4Tw0AgXQZH5BiFHqD2hXyXQi0-qFbGp_
[ex]: ../../tree/master/src/main/javascript/plugins/examples
[contrib]: contributing.md
