---
id: 227
title: Banshee Accessibility
date: 2009-09-15T12:31:35+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=227
permalink: /2009/09/15/banshee-accessibility/
openid_comments:
  - 'a:1:{i:0;s:5:"21298";}'
original_post_id:
  - "227"
categories:
  - Accessibility
  - Software
  - Technology
tags:
  - banshee-a11y
---
Over the next week or two I plan to document some work I am doing on Banshee to increase it&#8217;s accessibility. It has been a while since I was able to concentrate on a pet project without feeling guilty about my other responsibilities, recently I was able to put some time into Banshee accessibility, and have fun at the same time!  
**Disclaimer:** I currently only working on bare-bones Banshee with UI no extensions like Last.fm. Extensions need to be worked on too, in due time.  
Finding access blockers in software is an easy process, you could achieve a good measure of coverage just by using common sense. There will always be issues that you have overlooked, luckily in the Open Source world, there will always be vocal users who will be happy to point out why your application sucks just a bit. Of course you could always opt for an official audit, or refer to such documents as Section 508 for further access requirement guidelines.  
In my non-methodological review, I found several issues that need addressing, I am sure there are more, in such a rich application like Banshee, it is hard to reach all the corners, if you see any glaring omissions, or even something more nuanced, please let me know, and I will add it to this master list.

### Input Access

Keyboard access, or more specifically non-pointer access, is important for accessibility. Pointer access requires a minimal amount of dexterity and vision. Keyboard access, while not always as efficient or as discoverable, allows keyboard users, or users of alternative input methods to use all features of an application in an unassisted manner. Of course, by adding mnemonics and keyboard shortcuts in a smart fashion that complements the workflow in the application, you provide power users and keyboard users alike with a snappy and efficient experience when using your software.  
Of course, there is the other extreme too. Your application should not require elaborate keyboard gestures as the only means of access. This too, requires an amount of dexterity that could be strenuous on keyboard users, especially on-screen keyboard users. Just like general usability, functionality should be easily learnable, users should not have to memorize keyboard commands. This limits usability for users with cognitive disabilities.  
Bottom line, provide more than one way of achieving the same thing: Pointer access that will be discoverable to users, and keyboard access that is easily learnable (ctrl+n opens a new document), not too elaborate (not more than two modifiers, no timed strokes, like &#8220;double click&#8221;), conforms with expected behavior (tab moves focus, ctrl+z does undo).  
Before considering shortcuts and mnemonics, a GUI should cycle focus from one component to another when pressing tab. Tab focuses on the next item in logical order, and shift+tab focuses on the previous item. If the focus widget consumes the tab key, for example a text entry widget, ctrl+tab should be used to cycle through it.  
A typically sensitive area is drag and drop. Drag and drop requires simultanious pointer motion: click on an item or selection, move pointer while holding down left mouse button, let go of mouse button when pointer is over destination. Besides being a bit complex, often drag and drop operations perform non-trivial tasks that are hard to undo, like file operations. Ever drop a bunch of files over a folder icon in Nautilus, only to discover that they ended up in the parent folder because you weren&#8217;t precise enough?

#### Banshee Input

The first thing I tested was focus cycling. Pressing tab six or seven times returns you to the toolbar, this is good news, it means nothing is grabbing tab in a fashion that won&#8217;t let us cycle. When a toolbar item is focused, the left/right arrow keys are used for changing focus between the different toolbar items in the toolbar, this is where problems occurred. When Banshee first starts the seek bar is set to zero, and is disabled, after arrowing right a few times, focus lands on the volume item, pressing any arrow key when the volume item is in focus will invoke the volume control, the only way of returning to other toolbar items is to focus out and back into the toolbar. When a song is paused or playing, and the seek bar holds a value, it will grab focus, and won&#8217;t let you right arrow to the volume item. Unlike the volume control, when focus is stuck on the seek bar, the arrow keys don&#8217;t do anything useful like seeking, neither does page up/down help.  
Knowing that the list views used in Banshee are custom widgets, I was pleasantly surprised to see that there is proper cursor control when arrowing down or up with the control key pressed. This allows selecting multiple items using the keyboard, and exploring the list without changing the selection.  
When clicking on the column headers in the track list view, I was able to change the sorting order of the tracks. This doesn&#8217;t seem to be possible with the keyboard. The vanilla GtkListView focuses on the column headers before focusing on the list cells. This allows keyboard interaction with the column headers. The Banshee ListView does not implement this.  
There seems to be no way to search in a track with the keyboard, I found an open bug that says it used to be possible with ctrl+left/right, this should be reintroduced.  
There seems to be alternative methods for drag and drop tasks. I was able to queue and add songs to playlists with the keyboard alone. I may have missed some drag and drop features, if I did let me know.

### Theming

While application developers and designers often have a good idea of the look and feel an application should have, it is still necessary to allow users to tweak the user interface&#8217;s appearance to achieve higher contrast and comfortable colors. As the computer-literate population ages, the sleek, fine print, interfaces that used to be sexy and awesome will become more of a liability, and something more easy on the eyes will be required.  
Specific colors should not be relied on to convey status or information, if they do, there should be a textual alternative.  
The text size limit that a GUI could handle should ultimately be the physical display used. For example, I should be able to set the application font to 36 points, and still have the application usable and mildly aesthetic on a 40 inch display.

#### Banshee Theming

Before trying any special themes with Banshee, I noticed when testing the focus cycle that the Banshee ListView widgets don&#8217;t have a clear focus indicator. Anyone who could tell me where keyboard focus is in the screenshot below will receive a free gmail account.  
[<img class="alignnone size-medium wp-image-232" title="Banshee screenshot: Where is the current focus?" src="{{ "/assets/uploads/2009/09/focus_where-300x164.png" | relative_url }}" alt="Banshee screenshot: Where is the current focus?" width="300" height="164" />]({{ "/assets/uploads/2009/09/focus_where.png" | relative_url }})  
Next I tried all the different contrast themes.  
[<img class="alignnone size-thumbnail wp-image-239" style="margin-right:5px;" title="Banshee screenshot: Low contrast theme" src="{{ "/assets/uploads/2009/09/low_contrast-150x150.png" | relative_url }}" alt="Banshee screenshot: Low contrast theme" width="100" height="100" />]({{ "/assets/uploads/2009/09/low_contrast.png" | relative_url }})[<img class="alignnone size-thumbnail wp-image-233" style="margin-right:5px;" title="Banshee screenshot: High contrast theme" src="{{ "/assets/uploads/2009/09/high_contrast-150x150.png" | relative_url }}" alt="Banshee screenshot: High contrast theme" width="100" height="100" />]({{ "/assets/uploads/2009/09/high_contrast.png" | relative_url }})[<img class="alignnone size-thumbnail wp-image-234" title="Banshee screenshot: High contrast inverse theme" src="{{ "/assets/uploads/2009/09/high_contrast_inverse-150x150.png" | relative_url }}" alt="Banshee screenshot: High contrast inverse theme" width="100" height="100" />]({{ "/assets/uploads/2009/09/high_contrast_inverse.png" | relative_url }})  
You will notice that it is not possible to read the selection on the left treeview, this is a transient issue that rears it&#8217;s head only in certain focus states. The icons in the high-contrast theme are not all high contrast, and their size is not consistent. This is a long-standing, system-wide, issue with accessibility theming, it isn&#8217;t Banshee specific, but it needs to be fixed too. The other noticeable issue in the inversed contrast theme is the invisibility of the column header borders in the mail track ListView. Overall, I am pretty pleased with Banshee&#8217;s behavior in contrast themes.  
As ugly as Banshee looks with large fonts, it renders fairly well, without any serious issues.  
[<img class="alignnone size-medium wp-image-236" title="Banshee screenshot: Custom large fonts" src="{{ "/assets/uploads/2009/09/large_fonts-300x164.png" | relative_url }}" alt="Banshee screenshot: Custom large fonts" width="300" height="164" />]({{ "/assets/uploads/2009/09/large_fonts.png" | relative_url }})  
<span>One cute UI elements I was not able to personally explore is the capacity bar displayed when a portable music player is plugged in.</span>  
<span><a href="{{ "/assets/uploads/2009/09/home-shot-3.png" | relative_url }}"><img class="alignnone size-full wp-image-235" title="Banshee screenshot: Portable player capacity bar widget" src="{{ "/assets/uploads/2009/09/home-shot-3.png" | relative_url }}" alt="Banshee screenshot: Portable player capacity bar widget" width="228" height="174" /></a><br /> </span>  
The text alternative here seems to do the job, if we were left to colors alone, it would have been an issue. I couldn&#8217;t directly test this for ATK support, as I stole this screenshot from the Banshee website.

### AT-SPI Support

A recent requirement for applications with GUIs is that they provide out-of-process programmatic access to their interface. This allows assistive technologies to provide alternative output and input for the application. In GNOME we are very fortunate to have AT-SPI, which is a relatively clean accessibility API.

#### AT-SPI Support in Banshee

A quick way to test AT-SPI support is to use Orca when keyboarding through the application. When tabbing through Banshee, I hardly heard anything. When navigating the top toolbar, I mostly just heard &#8220;button&#8221;. Browsing artists, albums or tracks brought up no speech at all. We can now use Accerciser to get a better idea why Orca was not providing useful speech for Banshee. Browsing Banshee with Accerciser quickly shows us the reasons for Orca&#8217;s muteness.

  * The play button does not have a text alternative in the accessible object to complement the play icon.

[<img class="alignnone size-full wp-image-244" title="Highlighted play button" src="{{ "/assets/uploads/2009/09/play_button.png" | relative_url }}" alt="Highlighted play button" width="276" height="49" />]({{ "/assets/uploads/2009/09/play_button.png" | relative_url }})  
[<img class="alignnone size-full wp-image-245" title="Play button in Accerciser's tree view" src="{{ "/assets/uploads/2009/09/play_button_in_accerciser.png" | relative_url }}" alt="Play button in Accerciser's tree view" width="275" height="352" />]({{ "/assets/uploads/2009/09/play_button_in_accerciser.png" | relative_url }})

  * The biggest omission in Banshee&#8217;s AT-SPI tree is the custom ListView widget. As seen in the Accerciser screenshot below, a childless accessible object with the role on &#8216;unknown&#8217; is in place of where we would expect a &#8216;table&#8217; accessible. This is probably the biggest single access blocker in Banshee, since the ListView widget is the principal component in Banshee, and is part of what makes it such a great media manager.

[<img class="alignnone size-full wp-image-242" title="Highlighted artists ListView widget" src="{{ "/assets/uploads/2009/09/listview_highlighted.png" | relative_url }}" alt="Highlighted artists ListView widget" width="283" height="194" />]({{ "/assets/uploads/2009/09/listview_highlighted.png" | relative_url }})  
[<img class="alignnone size-full wp-image-243" title="Artists ListView in Accerciser's tree view" src="{{ "/assets/uploads/2009/09/listview_in_accerciser.png" | relative_url }}" alt="Artists ListView in Accerciser's tree view" width="278" height="443" />]({{ "/assets/uploads/2009/09/listview_in_accerciser.png" | relative_url }})

### Summary

Here is a final task list I hope to check off. Might not get to all of this, but I hope to follow up with posts soon when I do.

  * Banshee&#8217;s ListView AT-SPI support ([bug #533030](https://bugzilla.gnome.org/show_bug.cgi?id=533030)).
  * Text alternatives to icon buttons ([bug #595294](https://bugzilla.gnome.org/show_bug.cgi?id=595294)).
  * Visible focus indicator for Banshee&#8217;s ListView ([bug #595296](https://bugzilla.gnome.org/show_bug.cgi?id=595296)).
  * ListView column headers&#8217; borders visible in high-contrast inverse ([bug #595297](https://bugzilla.gnome.org/show_bug.cgi?id=595297)).
  * Keyboard control of ListView column headers ([bug #595299](https://bugzilla.gnome.org/show_bug.cgi?id=595299)).
  * Add keyboard support for in-track seeking ([bug #535924](https://bugzilla.gnome.org/show_bug.cgi?id=535924)).
  * Fix top toolbar keyboard navigation ([bug #595300](https://bugzilla.gnome.org/show_bug.cgi?id=595300)).