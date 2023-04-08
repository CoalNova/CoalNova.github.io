---
layout: post
title:  "Polygonal Sands"
date:   2023-04-08 17:39:44
author: "CoalNova"
categories: CoalStar
tags:	CoalStar
cover:  "../assets/img/2023_03_10.png"
---

&emsp; Perhaps it is purely my cultural upbringing, but I percieve the fundamental building blocks of the universe as like sand. Countless, coarse, rough, but still oh so foundational. It is easy to see an endless expanse of sand as lifeless and inhospitable. To us, as living creatures it may as well be. Put it can be given shape and form.

&emsp; Great progress has been made over the past week. Many previous hurdles have been overcome and I feel I have time to work more completely on things:

 - Heightmap application has been introduced. This asslows bitmaps to be directly applied to chunk data, and saved. 
 - Relatedly, chunk saving and loading is functioning correctly. 
 - Basic movement and camera rotations are implemented for debugging. 
 - Basic Terrain shaders have been implemented.
 - A simple rendering flowpath has been implemented.

&emsp; Currently work is being done on updating terrain mesh resolution to track the focal point. More progress needs to be made, regardless. To match the 0.0.2 Engine Demo, it will still need: 

 - low level-of-detail distant terrain mesh
 - texture loading
 - noisemap application and smoothing on fresh terrain generation
 - setpiece mesh loading
 - instance batching
 - sunlight direction
 - sun sprite
 - sky box/plane

<iframe width="640" height="360" frameborder="0" src="https://mega.nz/embed/LpcQFYIK#xdfLG90TvJK43IOYzDFWJjxfBQhBDq0OZ_T-9vmV8Zk!1m" allowfullscreen ></iframe> 

 &emsp; More writing has been performed on the associated game project. Once the reimplementation is complete it should be a good opportunity to release some information.