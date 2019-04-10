---
id: 324
title: Telepathy Debugging
date: 2010-02-17T10:46:24+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=324
permalink: /2010/02/17/telepathy-debugging-3/
original_post_id:
  - "324"
categories:
  - Software
  - Technology
---
I have been working on different Telepathy pieces for the last month or two. And have been thinking a lot about how I run and test the different components. One of the first things I did was put together a script based on one in telepathy-glib to start a new session bus dedicated for testing with an alternative service directory. This allows me to use Empathy for communication uninterrupted by testing.  
When I was working on Gabble. I had a python test client I would run against it, this meant I had to have two terminal windows open, one for the client, and one for the CM. Last week I started working on Mission Control too, and found myself quickly drowning in open terminal windows and debug output. What I needed badly was a debug log viewer.  
There already is a log viewer in Empathy, but I found it tedious to restart it between Empathy runs, and it was missing some basic things like copy/paste, search, and category filtering. So over the weekend I hacked up a quick and dirty UI that does all of the above. Hopefully we could add these features back into the Empathy viewer, and make it possible to run outside of Empathy.  
[<img class="alignnone size-medium wp-image-325" title="Screenshot: Telepathy Debug Output Viewer" src="{{ "/assets/uploads/2010/02/Screenshot-Telepathy-Debug-Output-Viewer-300x120.png" | relative_url }}" alt="" width="300" height="120" />]({{ "/assets/uploads/2010/02/Screenshot-Telepathy-Debug-Output-Viewer.png" | relative_url }})  
You could grab it from my [git repo](http://git.collabora.co.uk/?p=user/eitan/telepathy-debug-view.git;a=summary).