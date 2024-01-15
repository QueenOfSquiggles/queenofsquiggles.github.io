---
title: "Where The Dead Lie"
summary: "A short horror game made to test out Godot 4's capabilities"
date: 2024-01-15

categories:
  - Games
tags:
  - game
  - horror

images:
    - /images/where-the-dead-lie/wtdl-img-2.png
    - /images/where-the-dead-lie/wtdl-img-1.png
    - /images/where-the-dead-lie/wtdl-img-3.png
    - /images/where-the-dead-lie/wtdl-img-4.png
    - /images/where-the-dead-lie/wtdl-img-5.png
---
{{< project_links
	game="https://queenofsquiggles.itch.io/where-the-dead-lie"
	source="https://github.com/QueenOfSquiggles/DumbJumpscareGame"
>}}

# Game Overview
Where The Dead Lie is a short horror experience made in roughly a week to test my skills of game development and the features of Godot 4's beta release 16.

# Goals and Lessons

For this game I wanted to try out the features of Godot 4. Mainly the new Vulkan based rendering engine and the various refactors made for the C# scripting system. Additionally, I wanted to stretch my skills a bit by trying a genre of games that I had never made before, jumpscare horror games. While I had a general idea of how jumpscare horror games (JHG) work, I had never properly made one of these games myself and wanted to see if I could. 

Additionally, I wanted to work on balancing priorities between my games and my school work. So I also wanted to make sure that the game never got more important to me than my school work.

## Goals
- Make a Jumpscare Horror Game
- Utilize the new Vulkan Renderer and "Signed Distance Field Global Illumination" (SDFGI)
- Use lessons from [Ascension Of The Lamb](/games/ascension-of-the-lamb/) to create a creepy atmosphere
- Get some practice with [Blender](https://www.blender.org/) to make semi-realistic models
- Don't let the game get a higher priority than school work

## Lessons

I learned a lot from making this game. Firstly I learned that making a JHG can be quite fun, even if I don't personally enjoy the genre as much. Additionally, I did a lot of work improving my asset workflow. 

### Asset Workflow
For 3D models, I found that it was worth it to look for 3rd party assets under permissive licenses in some cases. Not necessarily because I couldn't model them myself, but because allowing myself to use someone else's asset saved me time which could be focused more and the tricky parts of the game. 

Additionally, I was comfortable enough in Blender to make changes to existing models as needed. And I did this often to tweak embedded materials and sometimes the geometry as well. 

Some changes I made include:
- Changing the Godot Robot to a blue metal instead of a rough blue
- Changing the DSLR Camera to a simple metal
- Simplifying the geometry of the DLSR Camera

## Lessons Review

Overall, I feel that I learned a lot. I got much better with using Blender for procedural material baking as well as texture painting. I learned techniques to cut the bake time down to several seconds per texture instead of several minutes per texture. 

I also learned about the Godot 4 Vulkan Forwar+ Rendering pipeline. I was able to utilize more robust materials and larger textures to create very realistic scenes, while still including an air of fantasy to it through the monster and the general setting.

I also learned how to properly animate a character in Blender, utilizing Inverse Kinematics to make the animation process much easier.

## Goals Review
- [X] Make a Jumpscare Horror Game
- [X] Utilize the new Vulkan Renderer and "Signed Distance Field Global Illumination" (SDFGI)
- [X] Use lessons from [Ascension Of The Lamb](/games/ascension-of-the-lamb/) to create a creepy atmosphere
- [X] Get some practice with [Blender](https://www.blender.org/) to make semi-realistic models
- [ ] Don't let the game get a higher priority than school work

Overall, I met my goals. The only one I failed with it letting it get in the way of school work. I'm incredibly passionate about game development. But when I allow myself to indulge in this passion, some other parts of my life tend to fade into the background. Now I was able to get everything done. Both the game and my school work. And I only had one late assignment during development. And that assignment was only late by about six hours. 

So in summary, I've been growing in my ability to synthesize lessons from provious projects. I've also been gaining momentum with learning softwares.

# Software Used
- [Godot 4 Beta 16]()
    - Beta versions available on the download repo
- [Krita]()
  - General 2D texturing and UI Elements
- [GIMP]()
  - Technical texture processing
- [Blender]()
  - 3D Modelling
  - Texture Painting
  - Procedural Material Design
- [Rodzilla's Material Maker]()
  - Procedural Material Generation
  - ORM Texture Generation
    - Ambient Occlusion
    - Roughness
    - Metalness
- [Audacity]()
  - Audio Processing

# The Windows Debacle

For whatever reason, the game would freeze on windows upon release. I use a Linux desktop for all of my daily purposes so I wasn't able to properly test on Windows myself. I'm incredibly grateful to the various people who were able to provide system information and logs to help with the solving of the issue. We finally found a solution when I submitted an issue to the Godot Engine Repository. There I learned that there was a bug in the version of Godot where certain Resource failures could result in infinite recursion. Specifically the segment in my game that was triggering it was the font. I chose to try out the System Font feature and chose a few system fonts that I was familiar with "Noto Sans" and "Fira Sans". Unfortunately, most Windows PCs didn't have these fonts installed, which resulted in the bug.

Switching to a resource that used a Noto Sans TTF file fixed the problem, and I pushed it out to my players to enjoy.

# Marketing and Sales Review

For this game I did fairly minimal marketing. The game was released with fairly minimal fanfare. Despite this there was a surge in downloads upon release. In part due to the sale I made where for the first week of release the game could be claimed for free. After which the game costs $1 minimum, with a recommended $5. This sale was listed on a reddit thread and the game held a position in the "New and Popular" section for Horror games on [Itch IO](https://itch.io/). As of writing, the game has 1350 views, 109 downloads, and 3 purchases. Considering the effort put into this game, I feel this is a pretty good outcome. The genre is fairly saturated, so asking for money will tend to hurt downloads overall.

I think in th future, I might make the release sale much shorter. Most of the downloads occured during the sale, and only a few people chose to purchase. As much as I like to think myself a philanthropist, I really need that money to sustain my life. In the future, I think I'll be removing options for free downloads. And for the demos, I'll actually restrict the content of the game as opposed to allowing the full version of the game. I thought the "Pirate Version" was a fun way to describe it, and I set it to prompt the players to donate to me or purchase the game to remove the prompt. It opens pages in their browser and is generally annoying, but still a free way to play the entirety of the game.

Since the end of the sale, the Pirate Versions have been outpacing the paid versions in terms of releases.

In the future, I'll change a lot in terms of marketing and sale style. I'm hoping that my next game will do much better. I'll be utilizing Godot's ["Release Feature"](https://docs.godotengine.org/en/stable/tutorials/export/feature_tags.html#custom-features) system to manage building demos that are restricted versions of the main game.

# Butler, and Incremental Patches

In the past, I've used GitHub and GitHub actions to push incremental builds to my projects. One issue I did have was with the autoamtic versioning and with the fact that I had limited processing minutes available on my free account. 

I learned about a tool make by the Itch IO team called "Butler", which was a command line tool for uploading the game with automatic incremental patches and consistent download channels on the project page. Despite being fairly comfortable in the terminal, I was hesitant to use Butler on my computer. But after trying it with this game I think it will be my default approach to uploading game builds going forwards.

I especially appreciate the "channel" approach which means that each named "channel" results in one downloadable file. And each channel can be updated independantly. Additonally, the versioning can be overridden or the default incrementer can be used.  

For my next project, I'm planning on making a shell script to run through pushing all of the versions to their respective channels. Or possibly a python script to make it platform independant.

# Screenshots

![img](/images/where-the-dead-lie/wtdl-img-1.png)
![img](/images/where-the-dead-lie/wtdl-img-3.png)
![img](/images/where-the-dead-lie/wtdl-img-4.png)
![img](/images/where-the-dead-lie/wtdl-img-5.png)



# Widget

<iframe src="https://itch.io/embed/1900264?dark=true" width="552" height="167" frameborder="0"><a href="https://queenofsquiggles.itch.io/where-the-dead-lie">Where The Dead Lie by QueenOfSquiggles</a></iframe>