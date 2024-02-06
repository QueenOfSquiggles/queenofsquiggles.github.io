---
tvitle: "Blog Update Feb. 2024 - C++ Development"
summary: "Another update on the blog and my development goals"
date: 2024-02-06

images:
  - /images/watery-wails/watery_wails_pbr_demo.png

categories:
  - Blog Meta
tags:
  - blog meta
---


> ***Caution***
>
> Hot Takes Inside!

## General Update!

Hey y'all! I haven't been making much "Content:tm:" but I've been doing a lot of stuff otherwise! I've been talking with more professional game developers trying to figure out how I can break into the game development industry and actuall start a career. It'll be one year since my graduation soon and I'd like to find some kind of employment in my field :sweat_smile:

## Blog Technical

As a technical detail, I switched the system used to create the blog. I was using Jekyll to create a static website and I switched to Hugo for doing the same. There's a lot of benefits to switched to hugo. Writing is easier because it automatically refreshes my browser when detecting a change, manages images a lot nicer, and generally supports a much more robust website. I'm using a custom framework "HB (Hugo Bootstrap) Framework" (see the footer for links & details). 

## Resume updates

I imagine unless you're a tech recruiter (which if you are, why are you reading this? Hire me already!) you're probably not watching my resume. But now after taking with several more professional developers I was able to garner some critiques on my resume. I've even had a recruiter say they remembered me based off of the pictures in my resume. (Go put pictures in your resume right now!)

I added some posts for some recent games that I had forgotten to do write-ups for. But they are currently really bare-bones at best. Mostly just showing off screenshots more than anything. I'm nervous I won't be able to write a proper write-up for these games since its been so long since I made them, and I'd have to re-learn my own code-base to remember what I was doing and why.

## C++???
Yes! It has been a long while since I've done any development in C++. Mainly because I have had no reason to. I started programming with Java and made games with a pixel-raster system written in pure Java. And eventually worked up to LWJGL (which gave access to OpenGL draw calls). But for the most part, I have been doing scripting with game engines since I wanted to make games, and was less concerned with having fine-grain control over the intricacies of the runtime.

Some people have told me that any moment I spend brushing up on my C++ is not a moment wasted, with respect towards employment in the game industry. So I wanted to make sure I am not just capable but highly proficient in C++ game development. 

I had two main project goals. One of which is complete with patches added from time to time. The other is a bit larger and I am still working through it as it is a full game written in C++.

### A new standard! 

![XKCD comic referenced](https://imgs.xkcd.com/comics/standards.png)

[XKCD reference](https://xkcd.com/927)

I am rather picky about build systems. And one of my biggest complaints when it comes to c++ build systems is how non-opinionated (wishy-washy) they are! What I really love about a build system like rust's `cargo build` or C#'s `dotnet build` is that they expect a particular project layout, with a specific configuration file that details exactly what the build system needs to know to prep the code into an executable state. 

When I searched for C++ build systems. The main ones that got recommended were "Make" and "CMake".

#### The problem with Make

Make is a super generic build system for linux. You define a serious of tasks and each task and list zero or more tasks that it depends on. And by chaining these with arcane combinations of symbols, you can craft a moderately usable build system. And in that sense I'd consider it only slightly more efficient than just writing a shell script for all the `g++` calls I want.

The trouble as well is there is little to be said about a standard. The only standard is the name of the script file (I dare not call it a configuration file!). From there you can actually use Make to do just about anything. You could have a make-file that downloads images from a website, formats them, and exports them to a particular directory. Which is impressive. But again, that's scripting, not necessarily a build system. 

#### The problem with CMake

CMake, or "the build system for creating make files". It is arguably a very robust system which enables cross platform development and coordination of large code bases with less effort than most major build systems. Additionally, it is truely not a scripting system but an actual build system. Using the incredibly odd language system you can define variables and perform processes and... I promise it's technically not a scripting system again. 

The main detail in CMake that makes it more promising is that it doesn't require you to write out your `g++` calls (since that would really break the cross platform capabilities). So all you have to do is define a project target and attach source files to that target. Simple right? Well every time you make, delete, or move a file, you need to change one **or more** `CMakeLists.txt` files.

#### My best effort

I wanted a stupid simple build system that expects a specific project layout but uses that to create a very dynamic build approach. I never really intended for it to be used by anyone but myself so I named it "SSBS", which is an acronym for "Squiggles Stupid Build System" but also sounds like a ship name, "S.S. Bullshit". Please clap I am very clever :cry:.

The build system itself is rather small and written in C++ for compiling C++ on linux specifically. I considered developing for cross platform. But the appeal of a simple Makefile to bootstrap the project was appealing.

Basically what it does is searches recursively in a `src/` directory for any `.c`, `.h`, `.cpp`, and `.hpp` files and adds them to a source list. It then generates `g++` commands for each source file and emits the objects into a similar tree structure as source in the `build/` directory. Additionally, the output of the `g++` call is emitted to a log file. Then once the calls are complete, it reads the log files to parse out errors, warnings, and notes. (For now, I couldn't manage to capture the actual output of the `g++` call and this is the best solution since linux has a piping system for commands).

Then it prints out all of the errors, warnings, and notes (with a little bit of style using a single-header library). It also ends with a breakdown of whether it succeeded or failed and how many errors, warnings, and notes were found.

I could probably write a lot more about SSBS. But unless literally anyone besides me finds interest in it, I might not? But I realize I might have to because it's pretty telling for my skills and drive to create solutions for problems and easing friction of development.

### A new game?

I'm still playing around with name ideas. So far I like, "Watery Wails" since it is an interesting title, gives some but not all details of the content, and is also relatively unique. (I had considered "Sunken Souls" briefly but I know people working on a game called "Sunken ..." that I don't wanna be terribly similar in name to. To avoid competition.)

#### Engine Development

The area of the games industry I am most excited about is engine & tool development. And so for that purpose, this game is mostly an excuse to make a super basic game engine. Though unlike popular game engines such as "Godot" and less important engines like "Unity" have robust scripting capabilities, a straightforward GUI, and decent scene structure systems, the engine I am making is much closer to a library or framework. Technically it is a framework but I really want to be able to say I  made a custom engine so I'm calling it an engine. 

The goal of this engine is to be highly specialized. The reason for that is the more specialized a system is, the easier it is to get it feature complete. I really like making 3D PBR horror games with as much style as I can muster. 

![A demo of the PBR capabilites of the engine as of writing](/images/watery-wails/watery_wails_pbr_demo.png)
> Important note: I got this model online, I didn't model it myself. 


Here you can see a few interesting details:
- The object with multiple different PBR materials attached
- Albedo, Normal, ORM mapping enabled
- ImGUI used to display basic debug information (for now!)

Some details you can't really see here:
- Resource management system (prevents loading the same file twice)
- Smart-pointer backed systems
- Render batching through single render passes for objects with a common shader program.
	- I'm toying with the idea of further sorting by material, but that would be a bit extra work and I'm not going to optimize much until I actually encounter performance issues.
- Robust input action system through a TOML file specification
	- Includes gamepad support
- Game Objects
- Transform objects (position, rotation, and scale packaged together and easily loaded into model *transform* matrix)
- A custom GLSL `#include` system (which allows for shared information across many shader files).

My goals for the engine, "Next Steps":
- Support static environment irradiance maps in the PBR rendering (to make reflections and such more realistic)
- Access mouse input from the input system (very little work, it's just a bit lower priority than others)
- OpenAL integration for sound effects and streamed music. (My current task as of writing)
- Some kind of GUI system
	- I'm tempted to opt for ImGUI as the GUI system for the game as a whole, but I think making my own GUI system would be significantly better because it would give me skills I could translate into a UI/UX position if that's what gets my "foot in the door" in the game industry.
- 


#### Game Development

The actual gameplay of this game is almost entirely theoretical at this moment. Since I really need a ton of engine systems in place before I'm comfortable actually building gameplay systems. 

The overall goal is to be similar to *Five Nights At Freddy's* (Specifically the first game) and *I'm On Observation Duty* (maybe I should give my game a longer title to fit in?? More syllables == better game right?)

The game will take place at a pool since I'm drawing on my experience when I worked as a lifeguard. I had my fair share of terrifying experiences there, and I want to try to translate the fear and axiety of literally having people's lives in your hands into the game. And a hefty amount of frustration for the parents that would literally abandon their kids to the pool because it was cheaper than daycare. (Basically take all of the corporatism parody of later FNAF games and translate that into parody of negligent parents and I think I'm there?)

One of my main struggles is finding ways to share what I'm making. Until I am ready to work on the game itself, any screenshots would just be "Hey look at this raw code that made such and such system more efficient!" (Imagine trying to write alt text for that!)

##### Release?

I have absolutely no clue when a release date would be. But I can say that it will be available for linux and *possibly* windows. I need to do a bit more research into how cross compilation for MacOS is on linux, but if I have to buy a developer's license the cost is too high for whatever meager profit I'll be making on this game. If I somehow break $50 I'm literally going to have a party or something.

## Why this blog post?

Well I wanted to give a lot of general updates. But also I wanted to talk about my C++ development a little bit since it's probably going to take a long while before it's actually done. 
