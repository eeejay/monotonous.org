---
id: 77
title: Introducing Pyia
date: 2008-07-01T10:14:59+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=77
permalink: /2008/07/01/introducing-pyia/
openid_comments:
  - 'a:5:{i:0;s:4:"6368";i:1;s:4:"7291";i:2;s:4:"7290";i:3;s:4:"6300";i:4;s:4:"6388";}'
  - 'a:5:{i:0;s:4:"6368";i:1;s:4:"7291";i:2;s:4:"7290";i:3;s:4:"6300";i:4;s:4:"6388";}'
original_post_id:
  - "77"
categories:
  - Accessibility
  - Software
  - Technology
---
Last week I was doing my best to dive into the wonderful world of Windows accessibility. So to flatten the curve, I decided to take shot at making a lightweight Python MSAA client library, Pyia.  
It is heavily inspired by [pyatspi](http://live.gnome.org/GAP/PythonATSPI "Pyatspi wiki page")&#8216;s class mixins. pyOrbit made it very easy to do this in pyatspi, making CORBA friendly and Pythonic. [Comtypes](http://sourceforge.net/projects/comtypes/ "Comtypes sourceforge page"), does the same in Windows, making COM cool as a cucumber.  
Accessible objects emulate containers for easy access to children nodes. Also notice a few convienient methods, like getDesktop which returns the desktop client. Also getStateName will return a human readable list of states rather than a bitmask.

<pre>&gt;&gt;&gt; import pyia
&gt;&gt;&gt; desktop = pyia.getDesktop()
&gt;&gt;&gt; for window in desktop:
        if not window.accState(0) &
          pyia.STATE_SYSTEM_INVISIBLE:
          print window
[window | ]
[window | Python Shell]
[window | Mozilla Firefox Start Page - Mozilla Firefox]
[window | Program Manager]
&gt;&gt;&gt; desktop[14].accStateName()
u'unavailable invisible'</pre>

This might be a bad idea, but I added some AT-SPI concepts, for example a registry, where you connect event callbacks. Also, events are wrapped in structures with a &#8220;source&#8221; field that is a reference to the accessible that is responsible for the event. There is no extra wire traffic because the reference is not retrieved until the source field is either explicitly called, or the event is printed (converted to a string).

<pre>&gt;&gt;&gt; import pyia
&gt;&gt;&gt; def event_cb(event):
        print event
&gt;&gt;&gt; pyia.Registry.registerEventListener(
        event_cb, pyia.EVENT_OBJECT_FOCUS)
&gt;&gt;&gt; pyia.Registry.start()
gainFocus
        source: [client | Mozilla Firefox Start Page - Mozilla Firefox]
        window: 524618
        thread: 568
        tstamp: 14692927
gainFocus
        source: [client | Python Shell]
        window: 1573178
        thread: 352
        tstamp: 14694599
&gt;&gt;&gt;
</pre>

You could try this stuff out by checking it out from [Github](http://github.com/eeejay/pyia/tree/master "Pyia tree on Github").  
If that is too much overhead, here is a [binary Windows installer](http://www.gnome.org/~eitani/win32/pyia-0.0.1.win32.exe "Pyia executable installer").  
You will need the comtypes Python module.