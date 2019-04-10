---
id: 73
title: Orca Doings
date: 2008-05-16T12:14:45+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=73
permalink: /2008/05/16/orca-doings/
categories:
  - Accessibility
---
This last couple of months has been characterized by random bursts of productivity. After I reached all of the deliverables from my last Mozilla Foundation grant, I decided to give it another liberal reinterpretation, and have just been picking up different bits and pieces of Orca, and found stuff that interested me to work on.

#### Contracted Braille

This work has mostly been completed in early march. Since we are depending on an external library, liblouis, one of the most important tasks was to get liblouis into a shape that could allow it to be shipped in major distros. All sorts of distros arose, from packaging to licensing. Luckily, John Boyer has been extremely helpful, and thanks to the ViewPlus folks, we were able to get liblouis re-licensed as LGPL 3. I am maintaining liblouis and liblouisxml &#8220;forks&#8221; that are autotooled and easy to install and package for distributions. Hopefully the main development and releases will be on these autotooled versions, making users lives easier, and getting distributions to package it.

#### Firefox Braille Support

When I was working on the contracted braille bit, I noticed that cursor routing was not yet implemented in our Firefox support. I got basic braille display cursor routing support to work in Firefox, and also link following support. A braille display user does not have to take her fingers off the braille display to surf the web. This is neat.

#### Mouse Review

When I was playing with a friend&#8217;s Wii, I noticed how cool and easy it is to point and click with the controller to type in your name on an on-screen keyboard from across the room. It was easy because of the &#8220;resistance&#8221; the controller&#8217;s motor emitted. This made me think of how we could apply that in Orca: with one of those vibrating gaming mice, and with speaking the current component we could allow low-vision (maybe even blind?) users get a better picture of the graphical interface, and allow folks to use the mouse for those tasks that have no keyboard access. I thought I deserved a Nobel prize.  
When I got to CSUN, I discovered that this is actually not a new idea at all. Some products already do that. Even NVDA does it by default. Mike said it would be a useful feature, so I hacked away during CSUN, and had something to show in the final days. Mouse review mode is available in development versions of Orca today, and will be in our 2.24 release.

#### Script Support Refactor

One of the stuff that I have been thinking about since I got involved in Orca is how do we add support for non-application customizations. For example, today it is possible for core or third party developers to extend Orca and override the default behavior and allow better access for specific applications like Evolution. We needed a way to support similar scripts, but for web applications like GMail too. When I took a look at how the source tree looked, I realized that there is an opportunity for a refactor. Last July just before GUADEC I got so excited about refactoring Orca&#8217;s codebase, that I even drew up pretty UML diagrams and attached them to a bug report. I met Willie Walker for the first time in GUADEC. He apologized for dousing my enthusiasm, but there were bigger tasks at the time than large-scale cleanups. Before CSUN we re-targeted web application scripting as a certain priority, and my refactor ideas were finally heard! The entire team stayed supportive and kept an open mind while I spliced files and created a lot of new directories. The diagram below is the UML I made last year.  
[<img class="alignnone size-full wp-image-74" title="July 2007 Refactor Proposal" src="{{ "/assets/uploads/2008/05/scripts_proposal.png" | relative_url }}" alt="This is a UML diagram that I sketched up last year." width="450" height="624" />]({{ "/assets/uploads/2008/05/scripts_proposal.png" | relative_url }})