---
id: 450
title: Caribou Week 1
date: 2011-04-22T18:48:44+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=450
permalink: /2011/04/22/caribou-week-1/
original_post_id:
  - "450"
categories:
  - Accessibility
  - Technology
tags:
  - caribou
---
Dear blog,  
I have been spending the last while working exclusively on Caribou, trying to get it out of the miserable shape it is in and make sure that it not only remains relevant, but really shines. I have been doing this for two weeks. But the first week was mostly spent on chasing down this [bug](https://bugzilla.gnome.org/show_bug.cgi?id=647729) in GDK. So I really only got down to business this last week.  
Here is a photo:

<p style="text-align:center;">
  <img class="aligncenter" title="Weather over Port Townsend" src="http://farm6.static.flickr.com/5142/5644079081_a7473371b6.jpg" alt="" width="500" height="333" />
</p>

What I have done:

  * Created an introspectable C library, initially to do the keyboard emulation and XKB stuff, but I have grand plans for it. What already landed in master is just simple key synth methods to replace Caribou&#8217;s reliance on python-virtkey which was never approved as GNOME external dependency.
  * Created an experimental git branch with a revamp of how we do layout in Caribou. Users will no longer choose between layouts, this is inferred from the current keyboard group the X server is set to. If the user will have any choice it will be between geometries, either a more natural geometry similar to what you have on tablets, or a fuller keyboard emulation.
  * Made &#8220;sub keys&#8221;, all the latest screen keyboards seem to do this, so now Latin accents and Semitic vowels could be easily entered.

Ok blog, I have to go. I&#8217;ll need to write a brief roadmap of where I think we should take this, and how Caribou could play a role in GNOME Shell, etc.  
Here is a screencast of what Caribou looks like today.  
[youtube http://www.youtube.com/watch?v=TLNQNwM-fjE&w=480&h=390]