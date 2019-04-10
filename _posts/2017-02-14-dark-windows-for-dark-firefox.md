---
id: 1216
title: Dark Windows for Dark Firefox
date: 2017-02-14T16:23:03+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=1216
permalink: /2017/02/14/dark-windows-for-dark-firefox/
publicize_twitter_user:
  - eeejay
categories:
  - Software
  - Technology
---
I recently set the Compact Dark theme as my default in Firefox. Since we don&#8217;t yet have Linux client-side window decorations yet (when is that happening??), it looks kind of bad in GNOME. The window decorator shows up as a light band in a sea of darkness:  
<img class="alignnone size-full wp-image-1222" src="{{ "/assets/uploads/2017/02/before_addon.png" | relative_url }}" alt="Firefox with light window decorator" width="3200" height="602" srcset="{{ "/assets/uploads/2017/02/before_addon.png" | relative_url }} 3200w, {{ "/assets/uploads/2017/02/before_addon-300x56.png" | relative_url }} 300w, {{ "/assets/uploads/2017/02/before_addon-768x144.png" | relative_url }} 768w, {{ "/assets/uploads/2017/02/before_addon-1024x193.png" | relative_url }} 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" />  
It just looks bad. You know? I looked for an addon that would change the decorator to the dark-themed one, but I couldn&#8217;t find any. I ended up adapting the [gtk-dark-theme](https://github.com/sagebind/atom-gtk-dark-theme) Atom addon to a Firefox one. It was pretty easy. I did it over a remarkable infant sleep session on a Saturday morning. Here is the result:  
<img class="alignnone size-full wp-image-1231" src="{{ "/assets/uploads/2017/02/after_addon.png" | relative_url }}" alt="Firefox with dark window decorator" width="3200" height="602" srcset="{{ "/assets/uploads/2017/02/after_addon.png" | relative_url }} 3200w, {{ "/assets/uploads/2017/02/after_addon-300x56.png" | relative_url }} 300w, {{ "/assets/uploads/2017/02/after_addon-768x144.png" | relative_url }} 768w, {{ "/assets/uploads/2017/02/after_addon-1024x193.png" | relative_url }} 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" />  
You can grab the yet-to-be-reviewed addon [here](https://addons.mozilla.org/en-US/firefox/addon/firefox-gtk-dark-theme/).