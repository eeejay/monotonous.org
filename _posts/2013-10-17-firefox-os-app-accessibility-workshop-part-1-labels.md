---
id: 541
title: 'Firefox OS App Accessibility Workshop Part 1: Labels'
date: 2013-10-17T18:35:39+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=541
permalink: /2013/10/17/firefox-os-app-accessibility-workshop-part-1-labels/
twitter_cards_summary_img_size:
  - 'a:6:{i:0;i:320;i:1;i:480;i:2;i:3;i:3;s:24:"width="320" height="480"";s:4:"bits";i:8;s:4:"mime";s:9:"image/png";}'
publicize_twitter_user:
  - eeejay
publicize_twitter_url:
  - http://t.co/1fHAoi41Lj
categories:
  - Accessibility
  - Software
  - Technology
tags:
  - fxosa11yworkshop
---
This is the first post in a multi-part series where I will walk you through all the steps I took to make the Gaia Clock app accessible. Now, as of this posting, these changes have not been merged into Gaia, not even reviewed. You could follow the entire effort to make the app accessible in [bug 921201](https://bugzilla.mozilla.org/show_bug.cgi?id=921201 "Bug 921201 - Make clock app accessible")  
In this post, we will cover the most cliché web accessibility topic, and that is properly labeling controls and elements.  
<img class="alignnone" alt="Screenshot of Clock app" src="{{ "/assets/uploads/2013/09/screen-shot-2013-09-03-at-19-07-05.png" | relative_url }}" width="320" height="480" />  
When I started testing the clock app with a screen reader, I quickly stumbled upon a control that the screen reader describes as “button”. Sighted users have a good clue as to what this button does. It has an image of a bell, and a plus sign. The active tab below says &#8220;Alarm&#8221;, so a sighted user would likely assume this button will allow them to add an alarm setting. And they would be right. A blind user will hear &#8220;button&#8221;, and won&#8217;t have the vaguest idea as to what this button does.  
The solution is straightforward. We need to add a label. The aria spec gives us the `aria-label` attribute just for that purpose:

<pre>...
 &lt;!--  create new alarm icon --&gt;
<span class="patch-removed">-&lt;button id="alarm-new"&gt;&lt;/button&gt;</span>
<span class="patch-added">+&lt;button id="alarm-new" aria-label="New alarm" data-l10n-id="newAlarmButton"&gt;&lt;/button&gt;</span>
...</pre>

Of course, when you add human readable strings, you need to make it localizable, the l10n.js script should do the trick along with the `data-l10n-id` attribute above. We will add the string to the locale properties files:

<pre>...
 editAlarm             = Edit alarm
<span class="patch-added">+newAlarmButton.ariaLabel = New alarm</span>
...</pre>

It&#8217;s that simple. We just took the first step to screen reader friendliness.  
Next post we will dig deeper into other accessibility challenges and solutions, stay tuned!