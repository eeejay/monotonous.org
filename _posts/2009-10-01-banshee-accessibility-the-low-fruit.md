---
id: 255
title: 'Banshee Accessibility: The Low Fruit'
date: 2009-10-01T11:18:15+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=255
permalink: /2009/10/01/banshee-accessibility-the-low-fruit/
openid_comments:
  - 'a:3:{i:0;s:5:"21145";i:1;s:5:"21153";i:2;s:5:"21181";}'
original_post_id:
  - "255"
categories:
  - Accessibility
  - Software
  - Technology
tags:
  - banshee-a11y
---
In [my quest to make Banshee more accessible]({{ "/2009/09/15/banshee-accessibility/" | relative_url }} "Banshee Accessibility: Intro Post"), I listed several issues that came up in a few minutes of testing. In this post I will review the solutions to some of the more straight-forward issues.

#### Fix top toolbar keyboard navigation

The top toolbar, where the play controls live had inconsistent keyboard behavior. Typically, you arrow left and right to reach different items on the bar, but the toolbar had two widgets which grabbed the arrow keys, and did not allow further navigation.  
The volume button is a highly customized Gtk.Button, the OnKeyPressEvent method is overridden, and all sorts of key pairs are assigned to do essentially the same thing, you guess what: +/-, Add/Subtract, Up/Down, Left/Right. Since there are plenty of alternatives for adjusting the volume, I simply removed the Left/Right keys so the widget does not consume them, and the parent toolbar will receive them.  
The seek slider essentially a Gtk.HScale, I haven&#8217;t figured out why but pressing left/right when the slider is in focus does not change it&#8217;s value. It&#8217;s probably some widget property I missed. In any case, since left/right doesn&#8217;t do anything in the widget, I figure nobody will miss it. I overrode OnKeyPressEvent, and made sure to return false when left or right is pressed.  
You could see the actual patches in the [bug report](https://bugzilla.gnome.org/show_bug.cgi?id=595300 " Bug 595300 -  Focus gets stuck in top toolbar keyboard navigation").

#### Text alternatives to icon buttons

This took me longer to figure out then I want to admit, the problem seems to be that the playback toolbar button accessible objects do not have a textual representation. It also seems that the current Banshee code does everything right: Gtk.UIManager is used, and text labels are provided. The short answer to my long inquiry is simply that GAIL is not exposing toolbar button names. I wish I filed a GAIL bug once I discovered that, because now &#8211; two weeks later &#8211; I don&#8217;t completely remember what the issue is. In any case a quick workaround in Banshee was to use the Gtk.Stock enumerators and not the stock string ids. I know, silly. I promise to file a GAIL bug on this soon. For now, you could look at the [bug report](https://bugzilla.gnome.org/show_bug.cgi?id=595294 " Bug 595294 -  No alternative text exposed in AT-SPI for playback buttons") for the workaround.