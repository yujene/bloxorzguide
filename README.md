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

**Bloxorz Old Discord:** https://discord.gg/zQQvZ3JmJM  
**Bloxorz Leaderboard:** https://www.speedrun.com/bloxorz

----
## Basics
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

### Fast Split
Previously thought swapping after splitting allowed block to move earlier, but I don't think this is true. I'll have to time this again.

### Fast Toggling
Fast toggling is when you input a direction to a cube, toggle during the movement animation, then input a direction to the other cube. Theoretically, this allows moving both cubes at the same time. The time difference between initial direction input and toggling can range from 0ms to 217ms. 0ms is the fastest possible fast toggle, and anything after 217ms would be a regular toggle since the block has finished its moving animation.

![toggle](images/movement/toggle.gif)
![fasttoggle](images/movement/fasttoggle.gif)

### Chained Fast Toggling

----
## Glitches
### Instance Duplication
### Stacking
### Menuing
### Desync Stacking

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
