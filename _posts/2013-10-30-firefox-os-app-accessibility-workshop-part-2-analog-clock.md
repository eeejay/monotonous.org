---
id: 561
title: 'Firefox OS App Accessibility Workshop Part 2: Analog Clock'
date: 2013-10-30T18:45:03+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=561
permalink: /2013/10/30/firefox-os-app-accessibility-workshop-part-2-analog-clock/
publicize_twitter_user:
  - eeejay
publicize_twitter_url:
  - http://t.co/4nNWypTJCe
twitter_cards_summary_img_size:
  - 'a:6:{i:0;i:320;i:1;i:480;i:2;i:3;i:3;s:24:"width="320" height="480"";s:4:"bits";i:8;s:4:"mime";s:9:"image/png";}'
categories:
  - Accessibility
  - Firefox OS
  - Software
tags:
  - fxosa11yworkshop
---
_This is a second post in a series about making Firefox OS apps accessible to blind users. You could read the intro [here](http://blog.monotonous.org/2013/10/09/an-introduction-to-making-firefox-os-apps-accessible/ "An Introduction To Making Firefox OS Apps Accessible"), and a post about labels [here](http://blog.monotonous.org/2013/10/17/firefox-os-app-accessibility-workshop-part-1-labels/ "Firefox OS App Accessibility Workshop Part 1: Labels")._  
The Gaia Clock App has a pretty analog view, with ticking hands. You can stare at it and wonder how generations past were able to divine the time of day from a few muted lines. The analog clock should serve the same purpose for blind users as it does to sighted users: It should tell time. In this post I&#8217;ll give an overview of the steps I needed to take to make the analog clock view useful.  
[<img class="aligncenter size-full wp-image-589" alt="Analog View in Clock App" src="{{ "/assets/uploads/2013/10/screen-shot-2013-10-04-at-11-20-02.png" | relative_url }}" width="320" height="480" srcset="{{ "/assets/uploads/2013/10/screen-shot-2013-10-04-at-11-20-02.png" | relative_url }} 320w, {{ "/assets/uploads/2013/10/screen-shot-2013-10-04-at-11-20-02-200x300.png" | relative_url }} 200w" sizes="(max-width: 320px) 100vw, 320px" />](/assets/uploads/2013/10/screen-shot-2013-10-04-at-11-20-02.png)  
If you are a blind user,the screen reader won&#8217;t even bother telling you about the analog view. The view is composed from a collection of empty `div` elements. Since they don&#8217;t contain anything besides some special styling, the screen reader skips them and does not bother the user with some arbitrary nested divs. For a good reason, **the entire Internet is a collection of redundant nested divs!**  
To make the screen reader display the view to the user, we need to give the view an appropriate role. This will tell the screen reader&#8217;s heuristics that the view is an item of interest. I chose to use the `img` role, since this is a graphic that describes time. There are other roles that would also be appropriate, such as `marquee`. But I chose `img`.  
I applied this role on the clock&#8217;s container:

<pre>...
         &lt;div role="tabpanel" id="alarm-panel" class="active panel"&gt;
           &lt;div id="clock-view"&gt;
             &lt;div id="analog-clock"&gt;
<span class="patch-removed">-              &lt;div id="analog-clock-container"&gt;</span>
<span class="patch-added">+              &lt;div id="analog-clock-container" role="img"&gt;</span>
                 &lt;div id="analog-clock-face"&gt;
                   &lt;div id="analog-clock-hands"&gt;
                     &lt;div class="analog-clock-hand" id="secondhand"&gt;&lt;/div&gt;
...</pre>

When I tried the screen reader with this change, I found that I was able to land on the analog view. The screen reader would say &#8220;graphic&#8221;, which is not very useful, but it is something. Now the user knows what is taking up all that space on the screen.  
The next step is to label the graphic with the current time. This was done in Javascript. Every time the clock hands are updated, we update the ARIA label as well:

<pre>...
   updateAnalogClock: function cv_updateAnalogClock(opts) {
     opts = opts || {};
     if (opts.needsResize) {
       this.resizeAnalogClock();
     }
     var now = new Date();
     var sec, min, hour;
     sec = now.getSeconds();
     min = now.getMinutes();
     // hours progress gradually
     hour = (now.getHours() % 12) + min / 60;
     this.setTransform('second', sec);
     this.setTransform('minute', min);
     this.setTransform('hour', hour);
<span class="patch-added">+</span>
<span class="patch-added">+    // Update aria label for analog view.</span>
<span class="patch-added">+    var time = Utils.getLocaleTime(now);</span>
<span class="patch-added">+    this.container.setAttribute('aria-label',</span>
<span class="patch-added">+                                time.t + (time.p ? ' ' : '') + time.p);</span>
<span class="patch-added">+</span>
     // update again in one second
     this.timeouts.analog = setTimeout(
       this.updateAnalogClock.bind(this), 1000 - now.getMilliseconds()
     );
   },
...</pre>

Another round with the screen reader, it now says &#8220;11:20 AM, graphic&#8221;. That is a lot better!  
[<img class="aligncenter size-large wp-image-591" alt="Screenshot of Screen Reader Emulator showing the analog view correctly." src="{{ "/assets/uploads/2013/10/screenshot-from-2013-10-30-112114.png?w=460" | relative_url }}" width="460" height="392" srcset="{{ "/assets/uploads/2013/10/screenshot-from-2013-10-30-112114.png" | relative_url }} 959w, {{ "/assets/uploads/2013/10/screenshot-from-2013-10-30-112114-300x256.png" | relative_url }} 300w, {{ "/assets/uploads/2013/10/screenshot-from-2013-10-30-112114-768x656.png" | relative_url }} 768w" sizes="(max-width: 460px) 100vw, 460px" />](/assets/uploads/2013/10/screenshot-from-2013-10-30-112114.png)