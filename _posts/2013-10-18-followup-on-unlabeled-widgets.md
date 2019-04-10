---
id: 585
title: Followup On Unlabeled Widgets
date: 2013-10-18T03:39:29+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=585
permalink: /2013/10/18/followup-on-unlabeled-widgets/
publicize_twitter_user:
  - eeejay
publicize_twitter_url:
  - http://t.co/jXVn8pWdw4
categories:
  - Accessibility
  - Firefox OS
  - Software
  - Technology
tags:
  - fxosa11yworkshop
---
After my [previous post](http://blog.monotonous.org/2013/10/17/firefox-os-app-accessibility-workshop-part-1-labels/ "Firefox OS App Accessibility Workshop Part 1: Labels"), about labels, [@ted_drake](http://twitter.com/ted_drake "@ted_drake on Twitter") [commented](http://blog.monotonous.org/2013/10/17/firefox-os-app-accessibility-workshop-part-1-labels/#comment-1250 "Comment from last post") &#8220;_Is there a reason why you didn’t simply add text to the button?_&#8221; which is a good question! The short answer is, we don&#8217;t want to render the text in the button. Instead we want to keep it a graphical icon.  
But this question demands an emphasis:  
**WAI-ARIA is a last resort, it is designed to be a stopgap that augments conventional HTML markup.** As HTML evolved, many of the problems ARIA solves have been eliminated. Often, if you are using ARIA you are making a mistake. As Ted continues to say: &#8220;_&#8230;the first rule of ARIA is to not use it when there is a standard alternative._&#8221;  
So back to the issue of labeling controls and elements; aria-label is a last resort. The best option is rendered text, so the visual display is consistent with the accessible naming, for example `<button>Press me</button>`. After that there are two attributes that can be used, `title` and `alt`.  
An image may have an alternative textual description, that is what the `alt` attribute is for. Almost any element may have a `title` attribute, which will provide a human readable name for the given object.  
In fact, **I was wrong in the earlier post**. Instead of using `aria-label`, `title` would have sufficed. The only times `aria-label` should be used is when you don&#8217;t want a tooltip with the text to be visible on desktop, and for naming more complex composite widgets.  
I just learned something new, I hope you did too!