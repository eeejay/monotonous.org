---
id: 488
title: 'Caribou Week Who Is Paying Attention Anyway &#8211; We Need a New Maintainer'
date: 2011-08-07T06:41:29+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=488
permalink: /2011/08/07/caribou-week-who-is-paying-attention-anyway-we-need-a-new-maintainer/
original_post_id:
  - "488"
categories:
  - Accessibility
  - Software
tags:
  - caribou
---
<img class="alignnone" title="I'm Going To The Desktop Summit" src="https://www.desktopsummit.org/sites/www.desktopsummit.org/files/DS2011banner.png" alt="" width="333" height="110" />  
After making a non-binding resolution to report my Caribou progress on a weekly basis, I flaked. Of course. But luckily [Nohemi](http://justabovethetagclouds.blogspot.com/ "Nohemi's Blog") has picked up the slack and have kept you all up to date about the libcaribou powered GNOME Shell keyboard in her more binding GSoC reports. So no more architecture diagrams are needed, you all get the idea. But if you didn&#8217;t, let me make it clear: The goal of Caribou is to make it easy to implement new on screen keyboards where you would only need to provide the view, and libcaribou will be your model and controller.  
It is better to admit now than later: I will not have the bandwidth to continue to work on Caribou as my time is slowly running out. So&#8230;

<p style="text-align:left;">
  <a href="{{ "/assets/uploads/2011/08/caribou_recruit.jpg" | relative_url }}"><img class="size-full wp-image-489 aligncenter" title="We need you in Caribou" src="{{ "/assets/uploads/2011/08/caribou_recruit.jpg" | relative_url }}" alt="" width="450" height="599" /></a><br /> What we need:
</p>

  * A maintainer.
  * A GTK module, Nohemi is working on this, but we will need similar solutions for other toolkits and fallbacks (XIM?).
  * Unit tests for the library &#8211; libcaribou is gaining features and getting complex. We need some tests here.
  * More keyboard layouts/languages.
  * More function keys for the switch scanning keyboard.
  * Finer interaction modes:
  * Modifiers, use latching and traditional key gestures with multitouch.
  * Respect AccessX settings for sticky/slow/bounce keys.
  * A more hardware-like interaction where keys will auto-repeat when held down.
  * etc.
  * &#8230; and automatically choose the right mode for the keyboard without comfusing the user.

  * Revisit the &#8220;X adapter&#8221; and maybe use something more high level.

<p style="text-align:left;">
  Anyway, plenty of exciting work. Are you at the summit, please find me if any of this interests you.
</p>