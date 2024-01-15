---
title: "Godot Lighting Exploration"
summary: "Playing around with different lighting models available in Godot 4"
date: 2023-10-05

# header:
#     overlay_filter: 0.7

#     caption: "Main Example"
#     actions:
#         -   label: "Source Code"
#             url: "https://github.com/QueenOfSquiggles/Godot-Lighting-Capabilities-Test"
#         -   label: "Runnable Build"
#             url: "https://queenofsquiggles.itch.io/squiggles-godot-lighting-demo"

categories:
  - Tech
tags:
  - godot
  - tech discussion

images:
    - /images/squiggles-light-example/image1.png
    - /images/squiggles-light-example/image2.png
    - /images/squiggles-light-example/image4.png
---

{{< project_links 
	source="https://github.com/QueenOfSquiggles/Godot-Lighting-Capabilities-Test" 
	download="https://queenofsquiggles.itch.io/squiggles-godot-lighting-demo"
>}}

# The goal

I recently competed in Ludum Dare 54 (theme "Limited Space"). One of the problems players have mentioned is the poor performance. Mainly this is due to heavy leaning on `VoxelGI` and `SDFGI` which are Godot's premier techniques for rendering realtime global illumination. What I wanted out of this is to explore what is possible with Godot, and what options are available if I want to lean towards supporting end users on lower end hardware.

Let's look at the techniques we have available to us!

## SDFGI

SDFGI is a light model managed not by a particular node but as a part of the `WorldEnvironment`. The technical details of it go way over my head, but basically it uses the geometry of the scene to approximate(?) the global illumination while making heavy use of Signed Distance Fields

## VoxelGI

VoxelGI is a semi-realtime model that makes use some some baked data as well as real time calculations. This does limit how fully an environment is able to be lit realistically. However it makes up for that by being quite easy to set up and immediately adds details to the game. The main downside is runtime performance.

## LightmapGI

Lightmap Global Illumination uses exclusively pre-baked data. Meaning that while requiring a large file that caches the lighting data, the runtime performance cost is extremely low. (But not zero because nothing is ever easy!)

Because the lighting model is baked ahead of time, you can have highly realistic simulated light for a given space. And on top of that, the node automatically places lighting probes based on your settings. Though there is a lightmap probe node if you want to set some specific probe locations.

## ReflectionProbe

Reflection Probe might not be something you think of for lighting model. While extremely useful for creating *reflections*, it also provides some indirect lighting through the reflection contribution. Because of this, it can provide some added light while also making reflections appear more realistic.

However, there are two modes:
- Update Once
    - More performant
    - Does not detect changes
- Update Always
    - Slower
    - Reacts to changes in the scene

So when it comes to reflection probes, you may want to evaluate which mode is most effective for your scene in particular. Because I made a purely static scene for this experiment, I used "Update Once".

# The experiment

This experiment was to create a somewhat interesting scene. I recently saw the new Dune movie and liked the "mars" themes of this asset pack by Kay Lousberg. So I decided to make a desert planet themed scene.

The main reason I opted to use this asset pack (besides looking really cool) is that LightmapGI requires UV2 data from meshes. And Godot can only generate those for `MeshInstance3D` nodes that are using an `ArrayMesh` resource. At least as far as I could tell. With the GLTF models Kay produced, I was able to import them with static light baking enabled (which is **not** on by default)

The experiment was to see if individual light model nodes could all contribute to the same scene, and if disabling individual nodes would affect the illumination contributions negatively.

## Designing a level

With the assets I started to make a little story about a landing zone, some bases set up and trucks moving cargo around. The actual details of it were not super important, the goal was to show off the lighting anyway. But making little stories is one of my joys.

Something I discovered is all of the assets use a single material and texture, and it's their UV coordinates that affect the colour of the mesh. Which is incredibly efficient for space when making a game. However it did not allow me to override individual "materials" of different models. For example I wanted to make the trucks have reflective windshields and more metallic hulls. Instead I opted to duplicate one of the rock meshes and replace the entire material with a slightly rough metallic material. Just to make sure the reflection probes were working as expected.

## Initial bugs

As it would turn out, moving nodes arround, which I did to make the project easier to parse for people hoping to learn from it, actually breaks `LightmapGI` nodes. As it would turn out, `LightmapGI` nodes only search for meshes among their siblings and children (recursively). So if there are components of a specific branch of the scene tree that are inaccessible, the `LightmapGI` will be unable to discover them!

While frustrating at first, this is actually *incredibly* useful! What this means is that you can have individual "segments" of your level with different light maps baked. So you could have a segment that the player will see all the time, and a segment that is only seen in cutscenes and even putting those in the same scene file, you can separate the lightmap baking and even use different settings!

# Results

It appears that layering static and dynamic light model nodes works rather well! There are some artifacts produced when the settings are changed, but it would appear that overall the quality is extremently high!


If you want to try out the application for yourself, it's free on my itch. [Download here!](https://queenofsquiggles.itch.io/squiggles-godot-lighting-demo)
