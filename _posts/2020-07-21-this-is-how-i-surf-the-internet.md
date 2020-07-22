---
title: 'This is how I surf the Internet'
author: Eitan
layout: post
permalink: /2020/07/21/this-is-how-i-surf-the-internet/
geo_public:
  - "0"
publicize_twitter_user:
  - eeejay
categories:
  - Software
  - Technology
---

<img src="/assets/uploads/2020/07/newtabs.png" alt="tab bar with a bunch of new tabs">

Aside from a handful of pinned tabs, I open a new tab for anything I need to do: search the web, file a bug, look up documentation, check on the news, the weather, you get the idea. I am also addicted to Firefox’s new tab page, so I'll often open a new tab out of boredom to let Pocket suggest an article for me. I hardly ever look at the same tab twice. If I need to get to something, it is never worth digging through all those tabs, I’ll just type what I am looking for in a new tab, and hope for a good suggestion from the awesomebar. After a couple of days I’ll have hundreds of tabs open. I declare “tab bankruptcy”, I purge them all, and start over.

A while ago I made an addon for myself. It was essentially a tab FIFO. It would only allow 10 tabs to be open at a time. If an 11th tab was created, the least recently activated tab would be closed.

<img src="/assets/uploads/2020/07/throttle-tabs-popup.png" alt="Throttle Tabs popup" style="max-width: 250px; float: right; margin-left: 1rem;">

I came to think what if I am not the only person who abuses tabs in this way? What if there are other poor souls out there with hundreds or even thousands of open tabs. Are they waiting for Marie Kondo to hold their hand while they deliberate each tab before they discard it?

So I decided to polish my addon a bit, give it a UI, and put it up on AMO. Since users might not trust an addon that automatically closes tabs, I decided to add an “overflow” feature which is essentially tab purgatory. Instead of having the addon auto-close the tab, it hides it. The tab is still accessible via the addon’s popup, Firefox’s “Hidden Tabs” submenu, or through tab search in the awesomebar. The overflow can be capped too so it can permanently discard old tabs after a given limit.


It's called Throttle Tabs, it has a cute logo (which I now realize looks like a tab with a poop emoji on it), and [you can get it on addons.mozilla.org](https://addons.mozilla.org/en-US/firefox/addon/throttle-tabs/).