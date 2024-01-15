---
title: "This Metal Heart Still Beats"
summary: "A small puzzle game made for Ludum Dare 51"
lastmod: 2024-01-14



categories:
  - Games
tags:
  - game
  - game jam

images:
    - /images/this-metal-heart-still-beats/screenshots_1.png
    - /images/this-metal-heart-still-beats/screenshots_2.png
    - /images/this-metal-heart-still-beats/screenshots_4.png
    - /images/this-metal-heart-still-beats/screenshots_3.png
---
{{< project_links 
	game="https://queenofsquiggles.itch.io/this-metal-heart-still-beats" 
	source="https://github.com/QueenOfSquiggles/this-metal-heart-still-beats" 
>}}

## Game Overview

This game was made for Ludum Dare 51, which had the theme "Every 10 seconds".

## Story

I made the game a story of a person and their robotic partner, Ava, who has short circuited. You as the player have to try to fix their wiring while they are in a 'sleep mode' that ticks their circuits every ten seconds. The game is mostly a puzzle game of having Ava clean up some trash. The circuits are intentionally similar to [Unreal's Blueprints](https://docs.unrealengine.com/5.1/en-US/blueprints-visual-scripting-in-unreal-engine/). 

## Technical Information

At the time of development, the Godot Engine Development Team had announced they would be sunsetting the "Visual Script" language for Godot. It was a visual scripting language option similar to Blueprints, but lacking in many ways, which led to the sunsetting. There were many flaws with it, one of the key flaws was that it was slower to make functionality in Visual Script than it was to write it in GDScript. And the logical flow of Visual Script was nearly identical to GDScript.

Thinking of these problems, and often referencing Unreal Engine's documentation on Blueprints, I decided to try to make a small programming puzzle game. I made sure to focus on "macro level" functions. So instead of smaller components I worked on specific actions and sequencing.

I used an [Event Bus](https://dzone.com/articles/design-patterns-event-bus) to decouple the different interlocked systems. Mainly I used the Event Bus to push events for each of the node actions.

> Note: in this case "node" is referring to the nodes in the visual scripting system within the game. However it is worth noting that Godot's basic elements of structure are also called "node" because the structure of a program in Godot is in a [Tree of Nodes](https://docs.godotengine.org/en/stable/tutorials/scripting/scene_tree.html).

There were several subscribers to these events. The logging system would print out information about what actions are being taken, or if a sensor event is going unhandled. Ava would listen to the action events and perform them in sequence with a small time delay and some smooting to make the actions more appealing. However, because they used an Event Bus and neither depended on each other, I was able to insert events manually and debug each component on its own, which saved valuable time in the game jam.

Surprisingly enough, Godot's UI system has the structure for a basic node and sockets GUI. I customized them with a custom theme and worked to make sure they were usable for the game.

### Technical Failings

#### Missing Failure State

I originally wanted the tension of the game to come from making a mistake. I planned on having the fail state be when Ava's circuits tick while the circuits are being manipulated, or are in an invalid configuration. However, I didn't finish this system, and I put too much effort to prevent the players from creating an invalid configuration.

#### Event System

Events were scripted in GDScript, which largely relies on [Duck Typing](https://en.wikipedia.org/wiki/Duck_typing) over [nominative typing](https://en.wikipedia.org/wiki/Nominal_type_system). As such using specific Event classes to differentiate and encapsulate the event data didn't make a lot of sense. Or at least would have been too cumbersome in that paradigm. So I opted for a string serialization, which can be seen in the log. Ava's actions are printing the unedited event string. This event string had to be constructed and subsequently parsed by each subscriber. In this case there were only two subscribers and a very short list of possible events. So handling this was relatively simple. But since working on this game, I've opted to use C# over GDScript in order to make more coherent Event Bus structures using delegates and C# events. C# is available as an optional scripting language for Godot, and there has been talk of making it included in the "standard build" of Godot 4, but as of writing this is not the case.

#### Free Movement

Despite forcing an integer based movement system, and a 2D tile based world, the motion is actually in pixels and not in tiles. So if someone tells Ava to move 3 units to the left, they will slide 3 pixels to the left instead of 3 tiles, which was generally expected of a puzzle game of this nature. 

## Reception

The game was made for the "Compo" version of the jam, which is 48 hours long instead of 72 hours. It ranked 142nd out of 2421 submitted projects (623 of which were in the Compo). This places it in the top 6% of games submitted in the competition. If you are interested in more information about Ludum Dare 51, the host has created an interesting [Statistics Page](https://ldjam.com/events/ludum-dare/51/stats).


## Widget

<iframe src="https://itch.io/embed/1726321?dark=true" width="552" height="167" frameborder="0"><a href="https://queenofsquiggles.itch.io/this-metal-heart-still-beats">This Metal Heart Still Beats by QueenOfSquiggles</a></iframe>

## Gallery

![img](/images/this-metal-heart-still-beats/screenshots_2.png)

![img](/images/this-metal-heart-still-beats/screenshots_4.png)

![img](/images/this-metal-heart-still-beats/screenshots_3.png)
