---
id: 104
title: Happy New Year
date: 2008-09-29T20:34:34+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=104
permalink: /2008/09/29/happy-new-year/
openid_comments:
  - 'a:1:{i:0;s:4:"8921";}'
  - 'a:1:{i:0;s:4:"8921";}'
original_post_id:
  - "104"
categories:
  - Accessibility
  - Personal
  - Technology
tags:
  - specular
---
&#8230; to Heebs and all.  
I am spending the Holiday with my grandparents in New York. It&#8217;s really nice to be able to do that.  
I have been taking time over the weekend to revisit my accessible tree comparison code from a month ago. I then managed to waste two days trying to get Selenium to work with trunk build of Firefox. I took David Bolter&#8217;s suggestion and relooked at Windmill. I would hate to switch automation schemes mid-project, but I could tell that eventually it will be beneficial. Windmill has it&#8217;s shortcomings too. It is amazing how non-trivial it is to launch Firefox. Both Selenium and Windmill have issues with that.  
Anyway, I decided to stop putting time into that for a while, and instead improve the whole tree comparison deal. There are a few issues that still need to be dealt with:

  1. Accessibility. Ironically the comparison display is not too accessible, it relies on colors for example. It should also have an optional column with info as to how that node changed (inserted, deleted, updated, moved). The &#8220;moved&#8221; string should be an anchor that by pressing it will put the focus on the other tree&#8217;s &#8220;moved&#8221; anchor and show where it moved to. Of course I could also add ARIA markup to this.
  2. Horizontal alignment. Equivalent nodes should be on the same row, this will also make it much more usable for screen reader users.
  3. More accurate matching. The heuristics I am using now are good for generic XML, but they could be made more relevant to accessibility APIs. A lot of the &#8220;moves&#8221; don&#8217;t make too much sense, and don&#8217;t make it any easier on the eyes. I am thinking that if I can&#8217;t improve this, I will just change &#8220;moved&#8221; markup to delete/insert.
  4. Prettyness. The output now is uglier than a monkey&#8217;s armpit. If I could get it together visually, I am sure it will be more usable and accessible too.

So here are two examples, they both use the [dijit form demo](http://archive.dojotoolkit.org/nightly/checkout/demos/form/demo.html "online dijit form demo"):

  1. [This is a comparison between Firefox 3.0.2 and Firefox nightly (9/29).]({{ "/specular/ff3_vs_ff31.xml" | relative_url }})
  2. [This is a comparison between Firefox nightly and IE 8 beta 2.]({{ "/specular/ff31_vs_ie8beta2.xml" | relative_url }})