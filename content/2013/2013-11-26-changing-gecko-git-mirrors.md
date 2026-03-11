---
id: 599
title: Changing Gecko Git Mirrors
date: 2013-11-26T18:29:44+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=599
permalink: /2013/11/26/changing-gecko-git-mirrors/
publicize_twitter_user:
  - eeejay
publicize_twitter_url:
  - http://t.co/3RoUVhO7q4
categories:
  - Software
  - Technology
---
You may have read the news that [Ehsan will be end of lifing his github gecko mirror](https://groups.google.com/forum/#!topic/mozilla.dev.planning/rkyKnCMQmYg).  
Having a current mozilla-central mirror on git has contributed to my mental health, and has generally allowed me to be a better human being and not drown in self pity and misery. So thank you Ehsan.  
Luckily, the RelEng team has picked up the baton, and have a git mirror of their own running. So go [clone it](https://github.com/mozilla/gecko-dev). Unfortunately the commits do not share the same SHA1 as Ehsan&#8217;s repo. So you can&#8217;t just switch the remote URI. Also, after you clone, you will need to migrate your branches over. There might be ways to do this in a bulk-ish way, but I only have one branch that I really care about, and I will keep the old clone around for a while if I need to pick something up from an obscure branch. So I did this off the top of my head:  
`
[eitan@mozbox Mozilla]$ cd mozilla-central-old/
[eitan@mozbox mozilla-central-old]$ git checkout a11y
[eitan@mozbox mozilla-central-old]$ git format-patch master..a11
0001-Bug-942991-Updated-virtual-cursor-navigation-sounds.patch
0002-Bug-942994-Introduce-clicked-sound.patch
0003-supress-error-when-trying-to-activate-invalid-access.patch
0004-hide-visual-cursor-when-vc-is-null.patch
0005-some-cursor-control-tweaks.patch
0006-start-of-new-dialog-focus.patch
0007-Only-blur-focus-if-new-pivot-position-is-not-focused.patch
[eitan@mozbox mozilla-central-old]$ cd ../gecko-dev
[eitan@mozbox gecko-dev]$ git checkout -b a11y
[eitan@mozbox gecko-dev]$ git am ../mozilla-central-old/000*.patch
Applying: Bug 942991 - Updated virtual cursor navigation sounds.
Applying: Bug 942994 - Introduce clicked sound
Applying: supress error when trying to activate invalid accessibles.
Applying: hide visual cursor when vc is null
Applying: some cursor control tweaks
Applying: start of new dialog focus
Applying: Only blur focus if new pivot position is not focused.
[eitan@mozbox gecko-dev]$
`  
Tada!