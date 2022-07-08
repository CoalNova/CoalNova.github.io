---
layout: post
title:  "Midsummer"
date:   2022-06-27 03:46:15
author: "CoalNova"
categories: CoalStar
tags:	CoalStar
cover:  "/assets/instacode.png"
---

This is an exceptionally busy time, it seems. Been attempting to find some amount of time to work on development. Unfortunately a trip has been planned that will most likely consume the next two weeks. A small amount of progress has been made in having the chunk keep the VBO data. When an alteration occurs it should now update the VBO data directly, modify what has been altered, and pump the update to the GPU. "Should" is the key word here, as it currently does not appear to function as it should. It is likely an issue with the -512,+512 worldspace coordinates being confused with the 0-1024(5) coordinates needed for calculating position in a data array.

Will need to experiment more with these values and processes to fix it to update, even if the options are not yet fully implemented. Further moving forward, the data will need to be saved. After this step would have been ogd placement and saving. However, the code base is in desperate need of cleaning, straitening, and commenting. A few elements will need tweeking beyond just basic line cleanup. Systems, such as mesh/material/shader management will need some attendance as well. My justification for this now is that I am considering moving the project over and opening up the source. 

I feel confident enough with my knowledge of C++ to where I can at least defend the insanity of some of the design choices made. And the possible feedback recieved should make for a cleaner, stouter, more elegant solution all around.

Recently, I played a game. It is a small, old, and simple game. But it stuck in my mind like a tick for what has been several weeks. It made me start to wonder about the functionality of this engine, and the possibility of experimenting with a 'lite' version for proof-of-concepting the headier ideas I'd like seen in CoalStar. It will absolutely take time and effort, but advancement in one is advancement in the other. An issue I am painfully aware of is that I am not familiar, or at least overly familiar, with the concepts needed in the engine. As I experiment and play around with ideas, it gives me a better understanding of what I am doing. Implementing an understood concept is far quicker than that experimentation. It, _should_ only be a slight impact on development time, but with the added benifits of robustness.


I really should start having a standard format for these entries.