---
title: "Emu-ception"
subtitle: "A 4 layer deep emulation experience, a. k. a. the best way to play PONG"
date: 2022-07-05T18:23:10-07:00
draft: false
---

<!-- Copyright (c) 2022 Jeffrey Tucker //-->
<!-- SPDX-License-Identifier: CC-BY-SA-4.0 //-->

**Siezure Warning**: This article contains video of the CHIP-8 version of PONG
that may cause siezures. The videos in this article will not autoplay and
sufficient information will be given in a caption under the video.

PONG, it's a game that you can play (I know right?!). But have you ever
considered what version is the best to play? I've wondered the same but today
I've got the answer for you.

I was researching CHIP-8 for my first emulation project when I stumbled across a
version of PONG that some would say is less than ideal. The two player controls
are wack, and the game continually loops with no end goal in sight. However,
this had potential.

For those of you who don't know CHIP-8 is an interpreted assembly language that
was used to create video games back in the 1970s. It allowed these games to work
across multiple different architectures. Since it is one of the older game
"consoles" it needed lower hardware requirements. So all that we need to make it
better is to port it to a newer console!

Luckily, that work has already been done for us by the
[NES-CHIP-8](https://github.com/NovaSquirrel/NES-CHIP-8) emulator graciously
made open source by [NovaSquirrel](https://github.com/NovaSquirrel). I'm running
a modified version of the NES-CHIP-8 project which can be found
[here](https://github.com/sirfredrick/NES-CHIP-8). She did such a great job
making this that I feel bad about what this is going to turn into... anyway, now
we have the CHIP-8 game running on the NES (I'm using an emulator since I don't
own an NES myself).

{{< video src="https://blog.sirfredrick.com/videos/emu-ception1.webm" alt="PONG gameplay everything is normal except the emulator adds 'by NovaSquirrel' at the top" width="640" >}}

Wait! That console came out in 1985! We have over 30 years of
untapped potential!

Luckily, a really old unmaintained emulator project has the answer. The
pocketnes project does just what its name tells you, allows you to run NES games
straight from your pocket! No, I'm not talking about a smart phone emulator, I'm
talking about a GameBoy Advance Emulator!!!

{{< video src="https://blog.sirfredrick.com/videos/emu-ception2.webm" alt="PONG gameplay the right paddle is missing and the text is replaced with −8" width="640" >}}

There are some graphical glitches and inaccuracies introduced here to fit into
the GameBoy's portable hardware but we've now got a console from... 2001? No,
that can't be right... that's a whole 11 years ago!

Luckily, we have a solution! From the code of the popular VisualBoy Advance
emulator comes [VBA GX](https://wiibrew.org/wiki/Visual_Boy_Advance_GX) a
GameBoy Advance emulator for the GameCube/Wii. Since, I don't have a Wii handy
I'll be using the Dolphin emulator!!!!

This particular emulator has a Wiimote controlled menu. Make sure to turn on the
DSP LLE Recompiler so you can hear the music!

{{< audio src="https://blog.sirfredrick.com/audio/vbagx-music.webm" caption="VBA GX audio" license="GPL License" license-link="https://github.com/dborth/vbagx#readme" width="300">}}

{{< video src="https://blog.sirfredrick.com/videos/emu-ception3.webm" alt="All of the above issues plus the game goes below 10 FPS when a point is earned" width="640" >}}

Wait...

Well... at least it's running on my gaming desktop I made in 2018... that's only
4 years ago!

Have you ever asked how, before you decided if you should? Well, that's what
happened here. I've created PONG running on a CHIP-8 emulator running on a NES
emulator running on a GameBoy Advance emulator running on a Gamecube/Wii
emulator running on a Gaming PC! Check out the project on
[GitHub](https://github.com/sirfredrick/emu-ception)

Welp, hope you like it! Bye!
