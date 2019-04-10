---
id: 329
title: Morality Plays in Accessibility
date: 2010-02-23T13:51:14+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=329
permalink: /2010/02/23/morality-plays-in-accessibility/
original_post_id:
  - "329"
categories:
  - Accessibility
  - Personal
  - Software
  - Technology
---
Besides being a great designer, [Seth Nickel](http://blogs.gnome.org/seth/ "Seth's blog") is a really good writer. Maybe that&#8217;s what it takes if you want to pass on your vision and ideas to stubborn developers. He [wrote](http://blogs.gnome.org/seth/2010/02/23/morality-plays/) one paragraph yesterday that resonated with me:

> &#8230;﻿﻿we’ve been framing the hacker<->designer conversation around low level usability. Maybe we could get more done if the default conversation was different? If it happened earlier? If it was about deep design rather than surface bodangles?

This is _exactly_ how I feel about the designer<->accessibility-advocate conversation. Accessibility is too often an afterthought that is divorced from the design process.  
In the past I did some contract work as an &#8220;accessibility engineer&#8221; on a certain project. It went something like this (at the risk of encouraging an annoying meme):

<h3 style="color:#ff0000;">
  NO
</h3>

<span style="color:#ff0000;">projectmanager: </span> It is soooo important for us that this application be really really accessible, and support ATK really really well. And that people with disabilities have really really good access to this. Also, if you could make sure your ATK support is good enough for automated testing, that would be greeaaaat.  
<span style="color:#ff0000;">accessibilityperson: </span> I would love to help. I noticed that the color theme is hard-coded, this is problematic since users with visual impairments have different needs regarding color and contrast.  
<span style="color:#ff0000;">artsyfartspants: </span> The color scheme is deliberate and has been very carefully thought out. And besides, it is white on black, which is technically high-contrast, so anybody could read it.  
<span style="color:#ff0000;">accessibilityperson: </span> I also noticed that animations in this application are hard-coded and cannot be disabled. This is an issue since people may be very sensitive to animations and get motion sickness. The application should respect a system-wide animation-disable toggle.  
<span style="color:#ff0000;">artsyfartspants: </span> Please see my answer above. The animation&#8217;s effect and timing have been very carefully thought out. This is old news, I wrote the design spec 6 months ago, you are wasting my time.  
<span style="color:#ff0000;">accessibilityperson: </span> The user notification is transient, and disappears after a few, hard-coded, seconds. Users with cognitive disabilities, slow readers or users who are not native speakers of the interface&#8217;s language will have a hard time understanding the notification before it disappears.  
<span style="color:#ff0000;">artsyfartspants: </span> By design, see above.  
<span style="color:#ff0000;">accessibilityperson: </span> The user notification appears, hard-coded, in the upper right corner of the screen. Users with bad peripheral vision will miss these notification if their gaze is not set on the screen&#8217;s corner.  
<span style="color:#ff0000;">artsyfartspants: </span> By design, go away.  
<span style="color:#ff0000;">accessibilityperson: </span> But..  
<span style="color:#ff0000;">artsyfartspants: </span> Bye!  
_A week later_  
<span style="color:#ff0000;">accessibilityperson: </span> I completed adding ATK support to the application, you could grab my branch and try it out. I have other concerns regarding accessibility issues in this application that need to be addressed.  
<span style="color:#ff0000;">projectmanager: </span> Great! Could we now do automated testing on our POS and increase it&#8217;s quality a lot?  
<span style="color:#ff0000;">accessibilityperson: </span> Sure. I also wrote an Orca script for the app so that screen reader users have a pleasant experience using it.  
<span style="color:#ff0000;">projectmanager: </span> k. Write automated tests.  
Do I have a good solution to all the accessibility issues I brought up? Not necessarily, that is why we have good designers.

<h3 style="color:#00ff00;">
  YES
</h3>

<span style="color:#00ff00;">designguru: </span>Here is a writeup and a few mockups for the app. I did my best at **universal design** and included a diverse array of users in the use cases I designed for.  
<span style="color:#00ff00;">hackmaster2000 :</span> This looks good! I will implement this while making sure that **mechanism and policy are separate** so that edge-case users can be accommodated for without intrusive patches and hacks.  
<span style="color:#00ff00;">projectmanager: </span>Great work guys! The universality of the design, and the modular implementation will allow us to make some extra cash as we deploy this app for mobile devices and e-readers with little modification.  
<span style="color:#00ff00;">accessibilityguy: </span>Lookin&#8217; good. I have a branch with ATK support, I am currently testing this app with different assistive technologies. Could I suggest just tweaking this and that?  
<span style="color:#00ff00;">projectmanager, hackmaster2000, designguru: </span>Absolutely, making sure our software is accessible is very important for our project. We support all our users, **not just the first 80%**.  
<span style="color:#00ff00;">projectmanager: </span>I can haz magic testing now plz?

### Postscript

[Máirín&#8217;s writeup](http://mairin.wordpress.com/2010/02/23/painless-accessibility-tips-for-gnome-designers-and-developers) about the accessibility discussions at the UX hackfest really made me happy. So glad Willie Walker made it there, I thought of going, but Willie really knows how to drive a point home.  
My friend just came by and asked if I am blogging about Open Sores. I guess so!