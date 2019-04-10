---
id: 468
title: Caribou Week Whatever
date: 2011-06-07T13:33:31+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=468
permalink: /2011/06/07/caribou-week-whatever/
original_post_id:
  - "468"
categories:
  - Accessibility
  - Software
  - Technology
tags:
  - caribou
---
Hi again.  
Since the last time I wrote to you, dear bloggy, I have been working a lot on Caribou, made a trip to welcome Jenny back from Haiti, and crossed the continent by rail.  
[<img class="alignnone" title="Glacier National Park, view from the train" src="http://farm4.static.flickr.com/3330/5737930551_da1ee8bba1.jpg" alt="" width="500" height="375" />](http://www.flickr.com/photos/66518776@N00/sets/72157626635726069/with/5737930551/)  
Let&#8217;s talk about Caribou, so much has changed!

### Antler

Antler is the Keyboard UI that is bundled with Caribou. It does not have the pretension of being ready for users any time soon, it is more a sample implementation of a libcaribou keyboard,and a place for me to try stuff out and see if it would work in our platform. You could follow [Nohemi](http://justabovethetagclouds.blogspot.com/ "Nohemi's Blog")&#8216;s progress to catch up on how libcaribou is being used to power the new GNOME Shell keyboard UI. With all that said, Antler is still kinda cool. Here is a crappy video of Antler&#8217;s touch keyboard in action:  
[youtube http://www.youtube.com/watch?v=y2dJRC-YoIs&w=560&h=349]

### Scanning Support

I redesigned Caribou&#8217;s switch support from the ground up with the goal of simple configuration. There is still plenty of more work to do, but after looking at commercial alternatives I feel like we could do a pretty good job. Here is me typing text solely with the right shift key:  
<figure id="attachment_474" style="width: 500px" class="wp-caption alignnone">[<img src="{{ "/assets/uploads/2011/06/caribou_scanning.gif" | relative_url }}" alt="" title="Caribou Scanning" width="500" height="302" class="size-full wp-image-474" />]({{ "/assets/uploads/2011/06/caribou_scanning.gif" | relative_url }})<figcaption class="wp-caption-text">Please excuse the green/red combo</figcaption></figure>

### Input Method Support (bye AT-SPI!)

This is an experimental tangent, that might or might not be worth the time I spend on it. Recently Caribou master received GTK2/GTK3 input modules that perform DBus calls to the Caribou keyboard, and have it show up when and where it is needed. This has proven to be pretty tricky. I will hopefully follow up with a post about this, and some interesting <del datetime="2011-06-07T19:22:36+00:00">hacks</del> innovations surrounding these methods. Future work includes writing similar modules for QT3 and QT4. And having the keyboard emit key activation signals that the modules could use for inserting text instead of using XTest which feels so hackish and wrong.