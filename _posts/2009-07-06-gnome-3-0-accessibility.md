---
id: 204
title: GNOME 3.0 Accessibility
date: 2009-07-06T11:09:54+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=204
permalink: /2009/07/06/gnome-3-0-accessibility/
original_post_id:
  - "204"
categories:
  - Accessibility
  - Software
  - Technology
---
[<img class="alignnone" title="Alfredo Kraus Auditorium" src="http://farm3.static.flickr.com/2608/3694356343_39e7d2cbb5.jpg?v=0" alt="" width="500" height="333" />](http://www.flickr.com/photos/mostlypictures/3694356343/)  
[Mark Doffman](http://doffman.com/ "Mark's blog") gave a briefing of the state of GNOME accessibility towards 3.0. If I could recall the few slides from memory they included:

### AT-SPI

This is probably the largest body of work that has been done recently on the GNOME a11y front. AT-SPI currently is the biggest bonobo interface we have, and it&#8217;s migration to D-Bus, mostly by Mark and Mike Gorse has been a major undertaking. The first release is due shortly.

### gnome-mag

Gnome-mag did not have a maintainer until very recently. Now we do. It must be ported to D-Bus too.

### gnome-speech

Text to speech is a hot topic. Mark didn&#8217;t go into detail regarding this, but we are dealing with multiple issues. First, of course, is it&#8217;s use of CORBA. Second, the fact that it leaves the sound device output up to the synth engine makes results inconsistent with different synthesizers. This is especially noticeable when major sound subsystem changes are occuring, specifically around PulseAudio.  
Luke &#8220;[TheMuso](/TheMuso "TheMuso's blog")&#8221; Yelavich is currently [scrambling](http://www.themuso.id.au/speech/speech-dispatcher-orca-integration.txt "Luke's proposal") to get Speech Dispatcher [into shape](https://wiki.ubuntu.com/DesktopTeam/Specs/Karmic/GnomeSpeechReplacement "Karmic Speech Spec"). Speech Dispatcher uses raw sockets and it&#8217;s own protocol, it does not use D-Bus, as Mark suggested. It would be really nice if it did, and if it were D-Bus activated, but it isn&#8217;t. On a non-accessibility related note, I think we would all benefit from a desktop speech service.

### GNOME-Shell

GNOME-Shell and Mutter currently use Clutter for a lot of their graphics, this makes AT-SPI support tricky and non-trivial. This will obviously need to be resolved before GNOME 3.0 since as the name suggests, this will be GNOME&#8217;s shell!  
I am going to eat ice cream.  
Ok, I am back. I forgot what else I had to write, so I might get back to this in another post. Or not.  
<img class="aligncenter size-full wp-image-197" title="GNOME Sponsorship Badge" src="{{ "/assets/uploads/2009/06/sponsored-badge-simple.png" | relative_url }}" alt="GNOME Sponsorship Badge" width="213" height="213" />