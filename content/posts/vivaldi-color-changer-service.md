---
title: "Vivaldi Color Changer Service"
date: 2018-10-26T00:00:00-07:00
draft: false
---

<!-- Copyright (c) 2018 Jeffrey Tucker //-->
<!-- SPDX-License-Identifier: CC-BY-SA-4.0 //-->

![RGB Keyboard](/posts/vivaldi-color-changer-service/keyboard.jpg)

Photo by
[Nhu Nguyen](https://unsplash.com/photos/kr-jmsASg8M?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)
on
[Unsplash](https://unsplash.com/?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

Soon after installing and using Vivaldi exclusively, the
[1.5 update](https://vivaldi.com/blog/how-vivaldi-got-its-lights/) came out. I
saw how cool it was to have a RGB setup that syncs with your web browser. I
investigated obtaining a Phillips Hue Bridge for my own setup when an amazing
idea came; Vivaldi might be able to be modified to bring this functionality to
any RGB setup. I was already planning on building my first computer (but earning
money for that took a few years). Once I had settled on a motherboard company,
Gigabyte, I set out to plan how I would combine Vivaldi's customizability with
[Gigabyte's RGB Fusion API](https://www.gigabyte.com/mb/rgb/sdk).

## General Plan

![Animated diagram of the program](/posts/vivaldi-color-changer-service/diagram.gif)

The general idea is that a Vivaldi JavaScript mod would grab the color in
hexadecimal and push it to a service called [PubNub](https://www.pubnub.com/).
PubNub is a network that near instantaneously transfers data from one program to
the next. The data is then sent back to the computer through a Windows Service
which is identified by having the same subscribe key as the mod. The service
uses a C# version of the
[RGB Fusion API written by Tyler Szabo](https://github.com/tylerszabo/RGB-Fusion-Tool).
The API tells the motherboard to change the colors to the hex value sent. This
idea seemed feasible, but it would take some time and work.

## Executing the Plan

Around April, when the computer was freshly built, I began work on this project.
You will learn more about what I learned from each part of this project in later
blog posts. I asked the amazing
[Vivaldi Community](https://forum.vivaldi.net/topic/26553/is-there-a-way-to-get-the-accent-color-in-custom-js)
for help with the Vivaldi mod since I had never written one. With their help, I
was able to grab the color from the active tab. I then used a
[PubNub JavaScript file](https://github.com/pubnub/javascript/releases) that
allowed me to send it off to their network. Afterwards, I began writing the C#
Windows Service. I decided to use [Topshelf](http://topshelf-project.com/)
because it allows you to easily debug a Windows Service by running it as a
Console App. After I finished that, I began work on the installer.

## Why did it take so long?

If you have ever worked on a coding project you know that the answer is never
simple. I thought I could handle writing an
[MSI installer](https://github.com/oleg-shilo/wixsharp). The problem is, they
are a pain to write. I got part of the way through writing it but getting the
publish and subscribe keys from user input to install was frustrating. I put the
project on hiatus for the summer and took a break from the coding life.

## What can this program do?

This program allows you to have the motherboard on your computer change based on
the main color of the content of the webpage you are on. My favorite part
however is the resuability of the code. I want to make this code work for any
motherboard brand as well as have a Linux version if possible. If you know
anything about coding and want to help with the project, look on the [Github
page](https://github.com/sirfredrick/VivaldiColorChanger) for planned features
and start working on one. Pull requests are warmly welcomed.

## I want to use it right now!

The easiest way to install the project is to go to the Github page and download
the binaries. You can then follow the instructions in the README file. Please
note this project only works for [Gigabyte RGB Fusion compatible motherboards](https://www.gigabyte.com/mb/rgb/Product)
running on a Windows Operating System.

I hope you enjoyed the time and effort that went into this project. If you want
to hellp improve this project look on Github for a list of planned features and
make a pull request; they are always welcome! Also, see the next blog post for
more information about the individual parts of this project!

-- Sir Fredrick

