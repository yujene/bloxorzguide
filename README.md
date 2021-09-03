# Bloxorz - Speedrunning Guide and Knowledge Base
_by yujene_

## Table of Contents
- [Introduction](#introduction)
- [Basics](#basics)
- [Advanced Movement](#advanced-movement)
- [Glitches](#glitches)
- [Glitchless Guide](https://github.com/yujene/bloxorzguide/blob/master/glitchless.md)
- [Any% Guide](https://github.com/yujene/bloxorzguide/blob/master/anypercent.md)
- [Closing Words and Credits](#closing-words-and-credits)

----

## Introduction
This document serves as a guide and knowledge base of the mechanics and strats for speedrunning Bloxorz. It will assume that you have a basic understanding of how the game works, but some basics will be included as relevant prerequisite information.

The contents of this document is based on information I've accumulated from running the game and doing experiments. If there's any missing, inaccurate, or unclear information in this document, contact me through discord dm yujene#6345 or the Bloxorz discord linked below.

**Bloxorz New Discord:** https://discord.gg/4yw8MPPJmQ  
**Bloxorz Old Discord:** https://discord.gg/zQQvZ3JmJM  
**Bloxorz Leaderboard:** https://www.speedrun.com/bloxorz

----
## Basics
### Game
Use https://www.coolmathgames.com/0-bloxorz/play so you only have the game in the browser.

### Controls
The block is moved using WASD or the arrow keys. They can be used interchangeably or at the same time.

The space bar toggles between cubes when the block is split. It has no cooldown so you can swap on every frame as long as you have control of the cubes.

### Switches
#### Soft Switch
The soft button can be pressed by any orientation of a block or cube.  
When pressed, the tiles it links to are either enabled, disabled, or toggled.

#### Heavy Switch
The heavy switch can only be pressed by a block in the standing orientation.  
When pressed, the tiles it links to are either enabled, disabled, or toggled.

#### Split Switch
The split switch can only be pressed by a block in the standing orientation.  
When pressed, the block splits into two cubes that are placed into their respective locations.

----
## Advanced Movement
### Movement Timing
The possible movements are **L**eft, **R**ight, **U**p, and **D**own for rolling in the configurations of **W**ide, **L**ong, and **C**ube. The figures below show the roll directions corresponding with the notation for the block. The cube configuration refers to when the block is split into two cubes.

![directions](images/movement/directions.png)

Below is a table of how long it takes for each movement direction-configuration combination. The time is shown in frames rounded to 3 decimals, where 1 frame = 1/30 seconds.

|     | L   | R   | U   | D   |
|-----|----:|----:|----:|----:|
|**W**|6.605|6.555|6.605|7.414|
|**L**|6.587|6.593|6.563|6.596|
|**C**|6.545|6.550|6.557|6.561|

### Input Buffering
Inputs can be pressed as a block or cube is moving to get the next movement out as soon as possible. The most recent direction input is used, so the previous direction input can continue to be held. For this reason, you can overlap your inputs to ensure direction changes on the next possible frame.

<img src="images/movement/buffer.gif" width="544" height="425"/>

\
As the block, you can buffer space to stop while holding a direction. I don't know of any practical use of this.

<img src="images/movement/buffer_space.gif" width="544" height="425"/>

### Fast Toggling
Fast toggling is when you input a direction to a cube, swap to second cube, then input a direction to the second cube before the first cube finishes its movement animation. This allows moving both cubes at the same time. The time difference between initial direction input and toggling can range from 0ms to 217ms. 0ms is the fastest possible fast toggle, and anything after 217ms would be a regular toggle since the block has finished its moving animation.

The comparison below shows the difference between regular toggling and fast toggling respectively. Regular toggling sends an input to the second cube after the first cube's movement animation ends. Fast toggling swaps and sends an input to the second cube before the first cube's movement animation ends.

<img src="images/movement/toggle.gif" width="544" height="425"/>
<img src="images/movement/fast_toggle.gif" width="544" height="425"/>

\
The image below shows the timing difference between regular and fast toggling. The time row labels the time in frames assuming 30fps, or indicates a variable. Inputs are coloured blue. Red and green indicate the start and end of the corresponding cube movement animations. Orange shading indicates the region where the swap input can be done.

<img src="images/movement/fast_toggle.png" width="850" height="600"/>

The top timeline shows the timing of a regular toggle. Time begins when Right is sent to cube 1. The movement animation takes 6.5f. The variable x represents how long you wait after the first cube's animation before sending Right to the second cube. The range of x is `x >= 0`, so `x = 0` is the fastest regular toggle. The swap input can occur anywhere between time 0 and x.  
The bottom timeline shows the timing of a fast toggle. The variable y represents how long you wait between Right inputs for each cube. The swap input can occur anywhere between time 0 and y.

### Chained Fast Toggling
<img src="images/movement/chained_fast_toggle.gif" width="544" height="425"/>

----
## Glitches
### Instance Duplication and Stacking
#### How it works
I'm still not sure exactly how this works in the code, but this is the best explanation I have for what's going on. After splitting the block into two cubes, making them fall off the edge at the same time causes the game to call the respawning code once per instance per cube. On the first time executing instance duplication, you end up with 2 instances because each cube calls the respawn code. On the nth time duplicating, you have two cubes of 2^(n-1) instances calling the respawn code resulting in 2^n instances. I'll be referring to how many times you do instance duplication by "n stacks" or "stacking n times".

The left side of the image below shows why the instances duplicate in powers of two. The right side shows how you would only see one instance after stacking. This means that there's 2^n-1 instances you're also controlling but can't see.

<img src="images/glitches/stacking.png" width="766" height="363"/>

The table below shows the relation between stack number and number of instances.

|Stack Number|Number of Instances|
|-----|----:|
|0|1|
|1|2|
|2|4|
|3|8|
|4|16|
|5|32|

#### Why is this useful
The significance of instance duplication is that it allows for you to skip levels. When you complete a level with instance duplication, the levelNumber variable gets incremented per instance. This means you can complete a level with n stacks to skip 2^n-1 levels. For [example](https://youtu.be/Yj86HAkrAbU?t=78), completing stage 8 with 1 stack will skip the stage title animation and spawn you straight into stage 10.

#### How to do it
The basic idea is to make both cubes fall off the edge at the same time. This requires doing a non-fast toggle off the edge. This means sending movement input to the first cube, swap, then send movement input to the second cube after the first cube's movement animation has finished. For instance duplication, move the second cube once the first cube is in the falling animation. If you try sending a movement input to the second cube before the first cube's movement animation is finished, you'll see it snap back onto the tile.

The video below sends a movement input to the top cube after 4 frames, so it snaps back on the tile.

<img src="images/glitches/early_stack.gif" width="544" height="425"/>

The video below sends a movement input to the top cube after 7 frames. I think this is the earliest possible frame for 30fps and 1 frame off optimal in 60fps.

<img src="images/glitches/fast_stack.gif" width="544" height="425"/>

#### Important note for moving after respawn
Depending on how much you delayed the second cube's movement input, your duplicated set of instances will be desynchronized with your visible set upon respawning. You should be able to hear when both sets have landed. The block is not controllable for about 11 frames after the landing sound, so don't hold any direction until 11 frames after you hear all instances have landed to avoid desynchronizing.

### Menuing
The menuing glitch allows you to warp to stage 1 from any stage. This is accomplished by quitting to menu while dying. Pressing Quit to Menu sets the levelNumber to 1 and attempts to load into the main menu. Dying triggers the code that tries to load the level using the levelNumber variable and this overrides the attempt to get to the main menu. When the menuing glitch is done correctly, you load into stage 1 after dying with no stage title cutscene. The video below shows the menuing glitch being used in stage 2.

<img src="images/glitches/menuing.gif" width="768" height="432"/>

### Desync Stacking
#### What is this
Desync stacking is executing instance duplication on some of the instances instead of all instances. Normally, all instances are synchronized, so instance duplication doubles the total number of instances. Currently, I only have a setup and practical use for doing desync stacking with half of the instances to multiply the number of instances by 1.5 instead of 2 for normal stacking.

The way to make this work is to desynchronize the position of half of the instances with the other half. Then, you have to do instance duplication on half of the instances while the other half stays on the platform. For the last move of instance duplication on the first half of instances, it shouldn't matter if the other half dies since all of them will respawn together into the same spot.

The image below shows how desync stacking is able to multiply the number of instances by 1.5 instead of 2. The first step is regular instance duplication, so the number of instances double. The next step is desync stacking to multiply the number of instances by 1.5.

<img src="images/glitches/desync_stacking.png" width="766" height="363"/>

#### How to do it
Desync stacking is only possible if you have at least 2 instances because you need two sets of instances to work with. I'll be showing how to desync stack on stage 8.

This is what it looks like to successfully desync stack if you do it with 1 stack. You get warped to stage 11 since 1 stack + 1 desync stack is 3 instances as shown in the image above. Note: the way I complete the stage at the end of the gif is not optimal.

<img src="images/glitches/desync_stacking.gif" width="768" height="432"/>

\
Now I'll show each step of what's happening in the video above with an explanation of the inputs and visual of what each instance looks like. The left side will be the visible half of instances, and right side will be the invisible half of instances.

When you do your last stack before doing desync stack, your original instances will spawn at a different time than the duplicated instances. This time difference should be how long you waited before killing the second cube during stacking. As you're respawning, hold right until the visible block has started its movement animation. You should also be able to hear the invisible instance hitting the split tile. If you let go of right at the correct time, the visible block should be lying flat and invisible instances should have the cubes in the default splitting destinations.

<img src="images/glitches/step1.gif" width="768" height="432"/>

\
Before the next step, you have to wait until the invisible cubes are controllable after the split. I have no clue how long you have to wait.

Fast method: After waiting, press left, fast toggle right. The top invisible cube moves left, and the bottom moves right. Since you fast toggled, the visible block only moves left once.

Easier alternative: Press left, space, right without fast toggling. The invisible cubes should do the exact same thing. Only difference is that the visible block will move left, then right. Note: the video below shows how it should look for fast method.

<img src="images/glitches/step2.gif" width="768" height="432"/>

\
Fast method: Press right, space, left not fast toggled. This kills both invisible cubes while the visible block moves and returns to spawn position.

Easier alternative: Press space, left, space, right, left. The first space swaps to control top invisible cube. Left, space, right kills both invisible cubes and leaves the visible block lying flat. The final left input brings the visible block back to spawn position. Note: the fast and easy strats converge after this step, so the image is the same now

It's important that the visible block returns to spawn position so all instances are synchronized once the new duplicated instances spawn.

<img src="images/glitches/step3.gif" width="768" height="432"/>

\
Wait until you hear all instances landing, then solve stage 8 with any strat.

----
## Glitchless Guide
The [Glitchless Guide](https://github.com/yujene/bloxorzguide/blob/master/glitchless.md) is on another page but I put a link here if you didn't use the table of contents.

----
## Any% Guide
The [Any% Guide](https://github.com/yujene/bloxorzguide/blob/master/anypercent.md) is on another page but I put a link here if you didn't use the table of contents.

----
## Closing Words and Credits
Thanks for reading this document. Hopefully it was useful for understanding the tech and/or the strats used in current runs.

Thanks to buhbai's arbguide for the format inspiration.

Thanks to mini weets#3103 for finding a large portion of the glitches.

Thanks to plezbb for getting me too into this game.
