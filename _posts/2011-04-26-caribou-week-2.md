---
id: 456
title: Caribou Week 2
date: 2011-04-26T10:54:46+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=456
permalink: /2011/04/26/caribou-week-2/
original_post_id:
  - "456"
categories:
  - Accessibility
  - Technology
tags:
  - caribou
---
Hello again.  
I didn&#8217;t get a chance to talk about my plans for Caribou in this little private SOC I am having here. Well here <del>are two oil rigs</del> is a diagram to illustrate it:  
[<img class="alignnone size-full wp-image-458" title="Caribou Architecture Diagram" src="{{ "/assets/uploads/2011/04/caribou-arch.png" | relative_url }}" alt="" width="500" height="286" />]({{ "/assets/uploads/2011/04/caribou-arch.png" | relative_url }})

Caribou Daemon
:   The daemon, through AT-SPI and [any means necessary](http://www.democracynow.org/2010/2/22/malcolm_x_by_any_means_necessary) figures out when a typing task is needed and activates the keyboard through DBus. When it does this, it provides as much information as possible regarding the text entry task: The location and size of the text area, the location of the cursor and the type of text expected (plain, email, url, number, full name). The daemon is written in Python, at least for now as Python is equipped with the best AT-SPI client library. The daemon has a relatively small body of code, so porting it to C is a worthy mission for some time in the future.

libcaribou
:   This is a library for keyboard implementors. It is written in C/GObject. It handles all common Caribou keyboard tasks such as:</p> 
    
      * De-serializing Caribou keyboard definition files into KOMs (Keyboard Object Model, I just made that up. You are welcome), with respect to the user&#8217;s XKB configuration and keyboard type preferences.
      * Implementing defined keyboard behavior.
      * Exposing the keyboard over DBus with interfaces known to the Caribou Daemon.
      * Implement scanning.
      * Do all the ugly X tasks, XKB, XTest, you name it. This could be replaces/supplemented with a higher level input method in the future.

Keyboard UI
:   This is the view for libcaribou&#8217;s model. It can be written in any language and toolkit that supports GObject introspection. The packaged UI is called **Antler**, and currently it is less than 200 lines of Python/GTK+. The idea here is that GNOME Shell (or anyone) could easily implement their own keyboard that can take advantage of Caribou&#8217;s facilities. If we pull this off well, keyboards will be advertising capabilities and co-exist, so the appropriate keyboard UI is invoked for the given task. 

Thanks for reading! In a future post I will describe Antler and plans I have for it.