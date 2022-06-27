---
layout: post
title:  "Manipulation"
date:   2022-06-19 03:01:22
author: "CoalNova"
categories: CoalStar
tags:	CoalStar Explanation Introduction
cover:  "/assets/instacode.png"
---

The next step in the process is terrain manipulation. This is a difficult one, not in theory, but in execution. It is not difficult to conceptualize iterating a kernel over a height grid. The issues that present themselves are that of performance. Currently, terrain normals are calculated at mesh generation, which means that for height adjustment, new terrain mesh must be generated for each adjustment to show. The data generated for the mesh is not saved in RAM, but is carted off to the GPU once completed. Thus, the data cannot be directly accessed to be adjusted. Several methods are possible to save processing time, with tradeoffs. 

One solution is saving the VBO (vertex) data in each chunk and persisting it. This would be the fastest option, as adjustments could be immediately calculated and the update would be much faster. The downside is that more RAM would be used, and since mid-gameplay adjustments may be utilized, it increases the memory cost of the program by (1025 \* 1025 \* 3 \* 4) 12MB per loaded chunk. At (3 \* 3) 9 chunks meshed during play, that's ~113MB additional overhead. Ounces makes pounds makes pain, and although the target architecture for the application is 64bits, the ideal is keeping the total utlized memory below 4GB for application and system.

The Second solution is pulling in memory from the GPU, altering it, then pumping it back. The operation would be more costly than holding on to the data in RAM, but less so than reconstructing it every time. This may also be difficult as I cannot guarantee the functionality of this across all GPU chipsets. Modern nomenclature adopts the term "wild west" in regards to catagories of processes having seemingly no cohesive ruleset or guidelines. This is absolutely applicable to historical GPU functionality, all the way to the conception of hardware accelerated graphics. Though it's possibly more standardized now, not too long it certainly was not the case. Traipsing over the minefield of possible GPU limitations is suicide, and assumptions only serve to deepen the grave you unknowingly dig for yourself. 

The first choice will most likely be the immediate solution. In the future a check may be present at startup checking the GPU for various capabilities, with these brute-force methods as backups should elegant functionality not be possible. There are also opprtuinties for faster methods to generate the Vertex Buffer Object data that can be played around with.

As far as options for terrain manipulation, various shaping tools are planned for use. They will be catagorized apart from each other, by function. The big one worth going over is a clay-molding type smoothing algorithm I found by accident in a project many years ago. It emulates a thumb firmly pressing across clay. Other options are the standard raise/lower/smooth/flatten, along with special erosion techniques, sloping, and more to come. These options should help form a more organic looking worldspace, but will eventually need to be supplimented with rock outcroppings and other natural effects.

I do fear that at some point production will stall, as I stop working on the world, and just trek across it for hours in awe of it all, terrible.


