---
id: 257
title: 'Banshee Accessibility: Where Am I?'
date: 2009-10-02T12:37:14+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=257
permalink: /2009/10/02/banshee-accessibility-where-am-i/
enclosure:
  - |
    {{ "/files/banshee_kb_nav.ogv" | relative_url }}
    5020854
    video/ogg
    
original_post_id:
  - "257"
categories:
  - Accessibility
  - Software
  - Technology
tags:
  - banshee-a11y
---
When I [started working on Banshee accessibility]({{ "/2009/09/15/banshee-accessibility/" | relative_url }} "Banshee Accessibility: Intro Post"), I pointed out various keyboard navigation issues in the ListView. For one, the column headers were not keyboard Navigable, so you couldn&#8217;t sort by column. Also, there was no indication the ListView had keyboard focus, this made keyboard navigation confusing.  
With my limited theming skills, I solved the latter, if anyone has a better idea for keyboard focus indication &#8211; please [submit patches](https://bugzilla.gnome.org/show_bug.cgi?id=595296 " Bug 595296 -  No visible focus indication for ListView")! My solution was slightly changing the ListView selection&#8217;s color, and making the frame&#8217;s border bolder.  
As for header navigation, the behavior I implemented mimics GtkTreeView: When tabbing into a ListView, focus first lands on the column headers, a second tab puts focus in the actual list. When focus is on the column headers, left and right change the active header, and return toggles sorting. There is a hidden advantage of horizontal control in the ListView that we will see in a later post regarding screen reader support.  
Enjoy this short screencast of keyboard navigation in Banshee&#8217;s ListViews.  
[<img class="alignnone size-full wp-image-261" title="Banshee ListView Focus Video" src="{{ "/assets/uploads/2009/10/banshee_video1.png" | relative_url }}" alt="Banshee ListView Focus Video" width="500" height="224" />]({{ "/files/banshee_kb_nav.ogv" | relative_url }} "Banshee ListView Focus Video")