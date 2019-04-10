---
id: 1334
title: 'How To Tweak Firefox&#039;s User Interface'
date: 2017-11-15T16:07:50+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=1334
permalink: /2017/11/15/how-to-tweak-firefoxs-user-interface/
geo_public:
  - "0"
publicize_twitter_user:
  - eeejay
categories:
  - Accessibility
  - Software
  - Technology
---
(**Warning:** Modifying `userChrome.css` is not guaranteed to work between versions of Firefox and may lead to hard-to-diagnose bugs. Use at your own risk!)  
Firefox Quantum has made a clean break from Firefox&#8217;s legacy addons. Hooray!  
A casualty of this change is the ability to have addons that fundamentally alter Firefox&#8217;s user interface. This can be a problem if you depended on this for accessibility needs. Say, you had an addon that enlarged the fonts in Firefox&#8217;s chrome.  
Luckily, not all is lost. With some CSS knowledge, you can customize the Firefox user interface as much as you need. Simply drop some CSS rules into $PROFILE/chrome/userChrome.css.  
Here is an example rule that employs large yellow on black text:

<pre><span style="color:#af5f00;">*</span> <span style="color:#06989a;">{</span>
  <span style="color:#4e9a06;">font-size-adjust</span>: <span style="color:#cc0000;">0.75</span> <span style="color:#75507b;">!important</span>;
  <span style="color:#4e9a06;">background-color</span>: <span style="color:#cc0000;">#000</span> <span style="color:#75507b;">!important</span>;
  <span style="color:#4e9a06;">color</span>: <span style="color:#cc0000;">yellow</span> <span style="color:#75507b;">!important</span>;
<span style="color:#06989a;">}</span>
</pre>

The effect on Firefox will be dramatic:  
<figure id="attachment_1338" style="width: 660px" class="wp-caption aligncenter"><img class="size-large wp-image-1338" src="{{ "/assets/uploads/2017/11/screenshot-from-2017-11-15-16-01-53.png?w=660" | relative_url }}" alt="" width="660" height="469" srcset="{{ "/assets/uploads/2017/11/screenshot-from-2017-11-15-16-01-53.png" | relative_url }} 2560w, {{ "/assets/uploads/2017/11/screenshot-from-2017-11-15-16-01-53-300x213.png" | relative_url }} 300w, {{ "/assets/uploads/2017/11/screenshot-from-2017-11-15-16-01-53-768x546.png" | relative_url }} 768w, {{ "/assets/uploads/2017/11/screenshot-from-2017-11-15-16-01-53-1024x728.png" | relative_url }} 1024w" sizes="(max-width: 660px) 100vw, 660px" /><figcaption class="wp-caption-text">Restylized user interface with yellow on black text</figcaption></figure>  
Note, this **will** break things, and it will not be perfect. Before using this kind of solution check what accessibility features your platform provides.