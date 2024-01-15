---
title: "Godot SDF Gen"
summary: "A tool for generating simple SDF textures made with Godot."
lastmod: 2023-02-23

# header:
#     overlay_image: /images/godot-sdf-gen/tool_preview_1.png
#     overlay_filter: 0.3

#     caption: ""
#     actions:
#         -   label: "Source Code"
#             url: "https://github.com/QueenOfSquiggles/godot-sdf-gen" 
#         -   label: "Game Page"
#             url: "https://queenofsquiggles.itch.io/godot-sdf-gen" 


categories:
  - Tools

tags:
  - tool

images:
    - /images/godot-sdf-gen/tool_preview_1.png
    - /images/godot-sdf-gen/tool_preview_2.png
    - /images/godot-sdf-gen/tool_preview_3.png
---

# Tool Overview

Godot SDF Gen is a small tool I made for myself and others to easily generate "Signed Distance Field" textures, which can be used to create a [variety of fun effects](https://shaderfun.com/2018/07/01/signed-distance-fields-part-7-some-simple-effects/). 

# Purposes

I wanted to create a small, useful tool with the [Godot Game Engine](https://godotengine.org/). Although largely marketed as a *game* engine, Godot does actually provide a plethera of features beneficial to desktop and mobile tool applications. And that very distinction that the software application can be made in Godot and exported to desktop and mobile with minimal extra effort was very attractive. Given this project, a mobile version didn't really make sense. 

# UI

Godot had recently revamped their Theme designing system, which allowed for the user interface to be customized in many ways. I would say that I over did it on this project. I have a much stronger sense for code and narrative than I do for art. Colour blindness may have affected this.

# Systems

Originally, I created it as a [Minimal Viable Product (MVP)](https://en.wikipedia.org/wiki/Minimum_viable_product). I used the built-in Godot UI systems and the scripting language, GDScript to manually read the pixels of an image in and process the kernel to determine the SDF value. After getting it to work, I ported the logic to a shader so it could utilize the GPU's processing power. Unfortunately, setting the kernel size too high actually crashed my computer for reasons I'm still unsure. I believe it had something to do with my desktop environment, but as I said, I'm not sure. I added in a "safety lock" for keeping the kernel within a certain range. I also added a feature where you could have the program play a small notification sound once processing was completed. This was helpful for processing larger files since I was working mainly with a slower laptop at the time. 

# Reception

The tool went largely unnoticed by the public. It is available freely, but due to the niche feature, it is mostly just helpful for me and my purposes. Which is still a valuable way to spend my time. 

# Screenshots

![img](/images/godot-sdf-gen/tool_preview_1.png)

![img](/images/godot-sdf-gen/tool_preview_2.png)

![img](/images/godot-sdf-gen/tool_preview_3.png)

# Widget

<iframe src="https://itch.io/embed/1538319?dark=true" width="552" height="167" frameborder="0"><a href="https://queenofsquiggles.itch.io/godot-sdf-gen">Godot SDF Gen by QueenOfSquiggles</a></iframe>