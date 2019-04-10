---
id: 60
title: X Marks The Spot
date: 2008-02-21T01:54:46+00:00
author: Eitan
layout: post
guid: http://monotonous.org/2008/02/21/x-marks-the-spot/
permalink: /2008/02/21/x-marks-the-spot/
categories:
  - Software
---
This weekend I spent some extra time in front of the computer. I was itching to get some kind of geotagging support into F-Spot. It was a fun ride, I got to relearn C# and use Monodevelop. Both of which are swell, it is a real plush experience. And Stetic is neat.  
[![Screenshot of geotag extension]({{ "/assets/uploads/2008/02/geotag2.png" | relative_url }})]({{ "/assets/uploads/2008/02/geotag.png" | relative_url }} "Screenshot of extension")  
Anyway, this extension allows you to take a GPS track file, and correlate it with photos using the EXIF timestamp. The result is a collection of automatically geotagged photos. You could see my start of a geotag collection [here](http://www.flickr.com/photos/mostlypictures/map "Flickr map page").  
You could get this work in progress with SVN:

<pre>svn co {{ "/geotag/geotag</pre>" | relative_url }}

To do:  
&#8211; Tag multiple versions, now only the default version gets tagged (maybe  
that is enough?).  
&#8211; Deal with RAW. I didn&#8217;t even test this, or for that matter anything  
non-jpeg.  
&#8211; Allow timestamp adjustments in the dialog. My Canon digital rebel does  
not provide a way to synchronize the clock very well, so the timestamp  
will never be very accurate (I heard you could do that in Nikon, but  
don&#8217;t get me started!).  
Far future:  
&#8211; Include a map widget. Unless you are a dork like me walking around  
with a GPS logger, this extension is useless. A map widget will allow  
people to review the coordinate info, and easily adjust it. I could  
personally live without the map now, because I upload pics to flickr,  
and it does the pretty map bit for me.