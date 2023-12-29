---
title: "Ascension Of The Lamb"
excerpt: "A small horror game made for Go Godot Jam 3"
layout: single
last_modified_at: 2023-12-29

header:
    overlay_image: /assets/images/ascension-of-the-lamb/ascension_header.png
    overlay_filter: 0.3

    caption: "Screenshot from the Game"
    actions:
        -   label: "Source Code"
            url: "https://github.com/QueenOfSquiggles/gogodot3-horror-game" 
        -   label: "Game Page"
            url: "https://queenofsquiggles.itch.io/the-ascension-of-the-lamb" 


categories:
  - Games
tags:
  - game
  - horror
  - game jam

gallery:
    -   url: /assets/images/ascension-of-the-lamb/ascension_gallery_1.png
        image_path: /assets/images/ascension-of-the-lamb/ascension_gallery_1.png
        alt: "A dirty hole in the ground"
    -   url: /assets/images/ascension-of-the-lamb/ascension_gallery_2.png
        image_path: /assets/images/ascension-of-the-lamb/ascension_gallery_2.png
        alt: "A hallway with a rusted grate in the middle"
    -   url: /assets/images/ascension-of-the-lamb/ascension_gallery_3.png
        image_path: /assets/images/ascension-of-the-lamb/ascension_gallery_3.png
        alt: "A dimly lit hallway"
    -   url: /assets/images/ascension-of-the-lamb/ascension_gallery_4.png
        image_path: /assets/images/ascension-of-the-lamb/ascension_gallery_4.png
        alt: "A simple bedroom with a spotlight illuminating it"
    -   url: /assets/images/ascension-of-the-lamb/ascension_gallery_5.png
        image_path: /assets/images/ascension-of-the-lamb/ascension_gallery_5.png
        alt: "A kitchen with rotting food and scattered cans"
    -   url: /assets/images/ascension-of-the-lamb/ascension_gallery_6.png
        image_path: /assets/images/ascension-of-the-lamb/ascension_gallery_6.png
        alt: "A stairwell lit from above by a small light"
    -   url: /assets/images/ascension-of-the-lamb/ascension_gallery_7.png
        image_path: /assets/images/ascension-of-the-lamb/ascension_gallery_7.png
        alt: "A small play room"
    -   url: /assets/images/ascension-of-the-lamb/ascension_gallery_8.png
        image_path: /assets/images/ascension-of-the-lamb/ascension_gallery_8.png
        alt: "A room with a radio lit from behind and couches in the background"
        # title: ""
---

# Game Overview
*Ascension Of The Lamb* is a "Retro PBR" game about exploring a mysterious cult bunker. 

![](/assets/images/ascension-of-the-lamb/ascension_gallery_1.png)

# Story of the Creation
I participated in the [Go Godot Jam 3](https://gogodotjam.com/the-jam/), which to save you a click is a game jam coordinated by the Godot community, specifically 'Redefine Gamedev', who is a fairly active member of the community. The jam was very exciting, with online social events planned for participants and hosted by various well known community members. 

I participated in the "Classic" experience, which was the easier of the two. We had roughly 9 days to make the game and were allowed to work on a team. I did end up working alone. But I was still determined to finish this game. I was excited to get working on making horror games. And for this one, I wanted to focus on setting up a proper atmosphere. Which if the feedback I got was honest, I think I succeeded there. 

The Theme for the jam was "Evolution" and I wanted to take that into an artistic interpretation of the cultists believing they would "evolve" or rather ascend into a higher form of life. The cult itself was inspired by some of the famous American cults from the 80s and 90s. 

![](/assets/images/ascension-of-the-lamb/ascension_gallery_2.png)

# Gameplay
The game is essentially a walking simulator. There is a simple physics simulation system that I used to make some simple puzzles and encourage exploration. There are two main ["lock and key"](https://tvtropes.org/pmwiki/pmwiki.php/Main/LockAndKeyPuzzle) puzzles which serve to stop the player and encourage them to explore the area more.

![](/assets/images/ascension-of-the-lamb/ascension_gallery_3.png)

# Visual Style - Retro PBR
For this game, I wanted to create a Playstation-similar style. I personally don't have any nostalgia for the Playstation, but I've seen a lot of other small indie horror games using the Playstation style to evoke a nostalgic feeling in the players. I wanted to add my own twist to it so I tweaked the parameters a bit. I kept the texture size of 128x128 and the dithering. But I swapped the standard blocky [bayer-matrix dithering](https://en.wikipedia.org/wiki/Bayer_filter) for [blue noise dithering](https://momentsingraphics.de/BlueNoise.html). I used two noise textures scrolling in different directions across the screen to affect the dithering which gave every surface a almost pulsating effect. Additionally, while I was going for a Retro look, I opted to use [PBR textures](https://en.wikipedia.org/wiki/Physically_based_rendering), specifically albedo, metallic, normal, and roughness.

I got some praise for this visual effect and I've taken to calling it "Retro PBR" as a general way to describe Retro-similar visuals that utlize a PBR rendering pipeline. 

I did struggle a lot with ["shadow acne"](https://www.opengl-tutorial.org/intermediate-tutorials/tutorial-16-shadow-mapping/). It was quite difficult because this version of Godot had some issues with the 3D rendering. It was generally considered unfit for making 3D games, but I tried anyway.

![](/assets/images/ascension-of-the-lamb/ascension_gallery_4.png)

# Overall Reception
The game did fairly well considering how it was made. Feedback ranged but there were a few common notes:
- [X] Writing is very good
- [X] Atmosphere is well set up
- [ ] The game lacks action, which makes it less fun to play
- [ ] Some players suggested adding jumpscares to make more of a haunted house experience

![](/assets/images/ascension-of-the-lamb/ascension_gallery_5.png)


![](/assets/images/ascension-of-the-lamb/ascension_gallery_6.png)

# My comments on the game
I feel that this game was a success for where I was at my experience level for the time. I had some specific goals and I accomplished them. Because I went for an artistic interpretation of the jam theme, it did not do very well. Likewise, I encountered several issues with my workflow such as a lack of experience in Blender, which I used for creating the level geometry, as well as struggling with the 3D capabilities of Godot 3, which uses a fairly outdated [OpenGL ES 3](https://www.khronos.org/opengles/) based rendering engine.

I think like many of my projects, this game served as an opportunity for me to learn. The feedback I got for this game really helped me hone my craft and I am incredibly grateful to everyone involved in the jam for helping me grow.

![](/assets/images/ascension-of-the-lamb/ascension_gallery_7.png)

# Widget
<iframe src="https://itch.io/embed/1562397?dark=true" width="552" height="167" frameborder="0"><a href="https://queenofsquiggles.itch.io/the-ascension-of-the-lamb">The Ascension Of The Lamb by QueenOfSquiggles</a></iframe>
<br/>

![](/assets/images/ascension-of-the-lamb/ascension_gallery_8.png)

# Gallery
*click on images for full resolution*

{% include gallery layout="half" caption="Screenshots from the game" %}
