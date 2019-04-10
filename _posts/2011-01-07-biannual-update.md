---
id: 417
title: Biannual Update
date: 2011-01-07T17:18:56+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=417
permalink: /2011/01/07/biannual-update/
original_post_id:
  - "417"
twitter_cards_summary_img_size:
  - 'a:6:{i:0;i:154;i:1;i:136;i:2;i:3;i:3;s:24:"width="154" height="136"";s:4:"bits";i:8;s:4:"mime";s:9:"image/png";}'
categories:
  - Accessibility
  - Personal
  - Software
---
It&#8217;s been almost six months since my last post. So why not just recount all the major things that happened last year. I have been extremely busy, I have been working full time for Collabora, and at the same time managed to always have some project or other deadline I was racing towards. This is probably the first time I paused to think about the wild goose chase that was 2010. Here goes:

### Collabora

<img class="alignleft" title="Collabora Logo" src="http://planet.collabora.co.uk/images/collabora.png" alt="" width="154" height="136" /> I have been drafting [Telepathy](http://telepathy.freedesktop.org/wiki) specs, improving Gabble, drafting more specs, and generally learning a lot. Some (potential) user-visible features include bomb-proof XMPP invisibility, interactive authentication, power saving, communication policy (contact blocking), improved codec-conflict user messages in VoIP and video sessions. And more that I can&#8217;t remember right now. Of course this is on top of the client work that is not public yet. It&#8217;s been a great experience, working with energized smart people like Simon, Will and Sjoerd is fantastic. I would love to head to [FOSDEM](http://fosdem.org) this year and see everyone, but I will be turning 30, so probably not.

### GNOME Accessibility Team

[<img class="alignleft size-full wp-image-421" title="gnome_a11y" src="{{ "/assets/uploads/2011/01/gnome_a11y.png" | relative_url }}" alt="" width="131" height="161" />]({{ "/assets/uploads/2011/01/gnome_a11y.png" | relative_url }})Early last year Willie Walker&#8217;s Orca team in Oracle was finally liquidated and we were not sure where things were headed. I was working on putting a [hackfest](http://live.gnome.org/Accessibility/Hackfest2010) together, giving a [talk](http://people.gnome.org/~eitani/csun2010/), organizing a booth, and generally having a presence in CSUN. This was the first a11y meetup, and I spent time preparing a presentation, dealing with sponsorship and travel, getting resources for the hackfest and booth. Besides saying goodbye to Will at CSUN, it was also a disengagement for me, as my job and other projects were keeping me elsewhere.  
Since that hackfest there has been [another one](http://live.gnome.org/Accessibility/HackfestAEGIS2010) in Seville, ﻿﻿Alejandro and Joanie have been leading the GNOME a11y team like nobody&#8217;s business. There is even a weekly meeting that I never attend on a regular basis. Things are looking good, it is really humbling. Joanie started doing this work pretty much at the same time I got involved in a11y, and she is still plugging away. Somebody please hire her so she could do this full time.  
I also gave a [talk]({{ "/guadec2010" | relative_url }}) at GUADEC about Universal Design. I learned a lot preparing it, and I hope to continue polishing it.

### Getting Closer

[<img class="alignleft size-full wp-image-422" title="Getting Closer" src="{{ "/assets/uploads/2011/01/weblogo.png" | relative_url }}" alt="" width="143" height="150" />]({{ "/assets/uploads/2011/01/weblogo.png" | relative_url }})At some point this year, I found the time to develop an iPhone application, a GIS Django backend and a web-based map authoring tool! The idea of the app is basically aural augmented reality. For example you could walk around in a city neighborhood and listen to past events and stories of different places. The main difference from an audio tour is that you are being led by sound as it gets louder when you approach as opposed to visible landmarks. Of course the technology is the trivial part, the real magic is in the well-produced audio. [Jenny Asarnow](http://23rdandunion.org/) has been doing that, and created fantastic soundscapes with stories and music. Full discloser, she is also my sweetheart. [Getting Closer](http://getting-closer.org/) was showcased in two events: [Megapolis](http://megapolisfestival.org/blogalogadingdong/) in Baltimore and [Third Coast](http://www.thirdcoastfestival.org/) in Chicago. We hope to collaborate with more audio producers and find new and exciting uses for this. As for my end, it was fun to step out of my niche Desktop programming and do some mainstream stuff, like iOS, Django and HTML/JS, just to know I could.

### Causing A Nuisance

[<img class="alignleft size-full wp-image-424" title="ga" src="{{ "/assets/uploads/2011/01/ga1.jpg" | relative_url }}" alt="" width="160" height="120" />]({{ "/assets/uploads/2011/01/ga1.jpg" | relative_url }})I joined other [young Jewish activists](http://youngjewishproud.org) in New Orleans this fall where we successfully agitated the Jewish American community into conversation by interrupting the Jewish General Assembly, the largest annual event surrounding Jewish philanthropy. Disrupting the Israeli prime minister&#8217;s keynote was really just an added bonus. This is one of the most important things I have been part of this year, and I am completely flattened by the amount of positive responses we have gotten for this. I wrote an essay about the experience that I hope it will be published soon. I am looking forward to continuing to be part of this conversation.

### Caribou

[<img class="alignleft size-full wp-image-426" title="IMG_0161" src="{{ "/assets/uploads/2011/01/IMG_0161.jpg" | relative_url }}" alt="" width="150" height="225" />]({{ "/assets/uploads/2011/01/IMG_0161.jpg" | relative_url }})After things settled down, and I caught back up on work, I started giving Caribou some desperately needed attention. I asked that it be pulled from the GNOME 2.32 module set in the last cycle because I just never had time to really get it ready for release. No excuses! I spent the holiday slowness porting Caribou to GTK3 and GObject introspection. Let me tell you, it was not trivial! I ended up rewriting whole chunks of Caribou, which was not all that bad. Since taking over maintainership I have done little in doing major changes, and accepted some large patches that I never should have, so it was cleanup time. This whole ordeal did not introduce any user-visible changes besides a new prefs window and stability. Um, I guess that is something. Anyway, I will be merging it to master today. That bad news (and this is what sucks about GNOME 3.0), is that other contributors and testers will need to do a jhbuild dance before being able to run any of this. I have a moduleset I will share with the world that does the minimum required stuff for a development a11y stack, with the new AT-SPI2, Orca, Accerciser and Caribou. There are some amazing artists in the GNOME community, anyone fancy on [designing an icon](https://bugzilla.gnome.org/show_bug.cgi?id=618293) for Caribou?

### That&#8217;s Not It!

I am sure I forgot stuff.