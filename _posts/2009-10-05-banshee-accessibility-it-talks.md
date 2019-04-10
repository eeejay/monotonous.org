---
id: 265
title: 'Banshee Accessibility: It Talks!'
date: 2009-10-05T10:30:09+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=265
permalink: /2009/10/05/banshee-accessibility-it-talks/
enclosure:
  - |
    {{ "/files/banshee_orca.ogv" | relative_url }}
    13645487
    video/ogg
    
openid_comments:
  - 'a:2:{i:0;s:5:"21305";i:1;s:5:"21309";}'
original_post_id:
  - "265"
categories:
  - Accessibility
  - Software
  - Technology
tags:
  - banshee-a11y
---
Instead of showing cryptic Accerciser screenshots, I went ahead and created a screencast of Banshee working with Orca.  
[<img class="alignnone size-full wp-image-266" title="Orca and Banshee screencast" src="{{ "/assets/uploads/2009/10/banshee_video2.png" | relative_url }}" alt="Orca and Banshee screencast" width="500" height="306" />]({{ "/files/banshee_orca.ogv" | relative_url }} "Orca and Banshee screencast")  
I forgot to demo a few things, but you get the idea, Banshee works with Orca. I started a Banshee Orca script that enables such prettiness as synchronized seek bar reports. You could get it from [the bug report](https://bugzilla.gnome.org/show_bug.cgi?id=597170 " Bug 597170 -  Add support for Banshee"), or an updated version from my [Orca git branch](http://github.com/eeejay/orca "My Orca Github Branch"). You could also keep track of all the Banshee a11y work through my [Banshee git branch](http://github.com/eeejay/banshee-a11y "My Banshee Accessibility Branch on Github").  
You will notice a few moments of awkward silence, there still is plenty of work to do, particularly with the SourceView on the left hand side: Both visible focus indication and some ATK instrumenting are missing.  
Anyway, real life is going to call me soon, so I hope y&#8217;all enjoyed this as much as I did. I also hope these things find their way into trunk in one way or another. If I see that this is under popular demand I will try to keep my ppa current.