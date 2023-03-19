---
layout: post
title:  "Rocks and Twigs and Buggy Things"
date:   2023-03-19 18:49:07
author: "CoalNova"
categories: CoalStar
tags:	CoalStar
cover:  "../assets/img/2023_03_10.png"
---

&emsp; Currently, the development focus for engine is implementing the debug cube. It is meant as a safe fallback for any erronious setpiece generation. If there is a fault in generating mesh, loading asset data, shader generation or program compilation, it all should revert to the cube.

&emsp; One hurdle to this has been migration from the raw, exposed [GLEW](https://glew.sourceforge.net/) C bindings to [Zig-GameDev](https://github.com/michal-z/zig-gamedev)'s ZOpengl wrapper. GLEW was having difficulties with the [Zig Language Server](https://github.com/zigtools/zls) where, as far as I can tell, ZLS was timing out attempting to parse the bindings GLEW would make. GLEW, or the GL Extension Wrangler, performs a runtime process on initialization to bind alll of the hardware GL functions and extensions. What that _means_ is actually difficult to explain in a devblog.

&emsp; In an attempt to keep it brief as I understand it, different cards across generation, class, chipset, and chipset vendor all have different implementations of GL's functions. These may be vendor specific between, NVidia, AMD, and Intel. They may be the Architecture Review Board's (ARB) version of the implementation, or the standard version. NVidia and AMD have vendor specific functions which may offer faster/more effecient options for as AA, DSAO, or HBAO. I Am Not An Expert at opengl, so only offer my perspective thorugh piggybacking implementation.

&emsp; Regardless, the ZLS's attempt at resolving the runtime shenanigans for giving language features in VSCode/VSCodium caused a notable lag on the laptop used to develop. I do not recall the Desktop suffering issues, but this laptop would grind to a halt. Mouse input, audio, even keyboard status lights where halted between 15 and 40 seconds. So, yeah, ZOpengl. In the code ZOpengl is namespaced as "zgl". This is not to be confused the library with the same name. 

&emsp; The SDL portion of Zig-Gamedev is unused, as the bindings did not expose the SDL Renderer, which is utilized by the [0.0.2 Demo](https://coalnova.github.io/links/) of the engine. The software renderer will also be utilized in the engine moving forward. 