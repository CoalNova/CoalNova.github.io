---
layout: post
title:  "Chunk, Part I"
date:   2023-04-30 14:27:40
author: "CoalNova"
categories: CoalStar
tags:	CoalStar
cover:  "../assets/img/2023_03_10.png"
---

&emsp; Unfortunately work and other things has slowed project gains, so instead lets cover implementation and design. This is the first of multiple to cover chunk implementation. A chunk, in the context of the Coalstar Engine, is the storage associated with a single dimensional slice. See? Simple.

&emsp; Okay, not so simple. The manner by which the engine can produce an infinitely large land mass is through dimensional projections. The terrain and all items in the engine only exist (for the purposes of rendering, memory, and animation/model fidelity) between -512.0f to 512.0f in the lateral axes. The different dimensions are projected outwards from the 'current' dimension of the viewer.

&emsp; The chunk is a struct associated with and to that dimension. It holds the terrain hight data as individually addressed points, for every other unit. As well, it will house data for all setpieces within the dimensional space. The specific layout of the data structure used for the setpiece collection has yet to be determined.

&emsp; In most open world engines, at that I'm familiar with functionally, the pieces that make up the world are much smaller than what I have in CoalStar. The reasons come down to memory/processing restrictions. With each part of the world comes scripts, collision, occlusion, rendering, animation, textures, models, just a bunch of stuff that is pure bloat if the player or viewer is not engaging with them. The obvious and first solution is to bind all of these expensive things to small bits of the world, small enough that the cost of loading/unloading and overhead on disk doesn't offset the gains of reduced assets and processing. 

&emsp; So a question comes back to the size of 'chunk' in Coalstar. The chunk is not to be itself a determinant in what assets are loaded, scripts run, and actors processed. That simple. The generation and processing of those elements (setpieces, actors, ecripts, actovators, etc) is based around a "Focus". As the "Focus" moves, it will update at a delta'd position change, and select generation and loading from a designated range around itself.

&emsp; This approach allows for granular asset generation for the player, not only in terms of rendering, but also for physics ops and possible CPU-intensive tasks. That is why the data structures which house the setpiece data need to be tuned for easy access. Instead of relying on a naive implementation of housing data in seperate and smaller unified world-parts, it will instead load everything from disk in a single go and generate as needed. Approximate heading and predictive generation might make this a faster process overall.