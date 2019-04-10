---
id: 1275
title: 'Phoropter: A Vision Simulator'
date: 2017-11-06T07:38:53+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=1275
permalink: /2017/11/06/phoropter-a-vision-simulator/
geo_public:
  - "0"
publicize_twitter_user:
  - eeejay
categories:
  - Accessibility
  - Software
  - Technology
---
After porting [Aaron&#8217;s NoCoffee extension](http://blog.monotonous.org/2017/10/13/nocoffee-visual-impairment-simulator/) to Firefox, I thought it would be neat to make a camera version of that. Something you can carry around with you, and take snapshots of websites, signs, or print material. You can then easily share the issues you see around you.  
I&#8217;m calling it Phoropter, and you can [see it here](https://eeejay.github.io/phoropter) (best viewed with Chrome or Firefox on Android).  
I could imagine this is what Pokémon Go is like if instead of creatures you collected mediocre designs.  
Say you are looking at a London Underground map, and you notice the legend is completely color reliant. Looking through Phoropter you will see what the legend would look like to someone with [protanopia](http://www.color-blindness.com/protanopia-red-green-color-blindness/), red-green color blindness.  
<img class="wp-image-1283 aligncenter" src="{{ "/assets/uploads/2017/11/screenshot-nov-2-2017-2_10_50-pm1.png" | relative_url }}" alt="Screenshot (Nov 2, 2017 2_10_50 PM)(1)" width="334" height="593" srcset="{{ "/assets/uploads/2017/11/screenshot-nov-2-2017-2_10_50-pm1.png" | relative_url }} 1080w, {{ "/assets/uploads/2017/11/screenshot-nov-2-2017-2_10_50-pm1-169x300.png" | relative_url }} 169w, {{ "/assets/uploads/2017/11/screenshot-nov-2-2017-2_10_50-pm1-768x1365.png" | relative_url }} 768w, {{ "/assets/uploads/2017/11/screenshot-nov-2-2017-2_10_50-pm1-576x1024.png" | relative_url }} 576w" sizes="(max-width: 334px) 100vw, 334px" />  
You can then grab a snapshot with the camera icon and get a side-by-side photo that shows the difference in perception. You can now alert the transit authorities, or at least shame them on Twitter.  
<img class="alignnone size-full wp-image-1312" src="{{ "/assets/uploads/2017/11/image3.jpg" | relative_url }}" alt="A side-by-side snapshot of the London Tube's legend with typical vision on the left and protonopia on the right" width="960" height="690" srcset="{{ "/assets/uploads/2017/11/image3.jpg" | relative_url }} 960w, {{ "/assets/uploads/2017/11/image3-300x216.jpg" | relative_url }} 300w, {{ "/assets/uploads/2017/11/image3-768x552.jpg" | relative_url }} 768w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" />  
Once you get into it, it&#8217;s quite addicting. No design is above scrutiny.  
<img class="alignnone wp-image-1315 size-full" src="{{ "/assets/uploads/2017/11/image2.jpg" | relative_url }}" alt="A page from a workbook displayed side-by-side with typical and green-red blindness." width="960" height="690" srcset="{{ "/assets/uploads/2017/11/image2.jpg" | relative_url }} 960w, {{ "/assets/uploads/2017/11/image2-300x216.jpg" | relative_url }} 300w, {{ "/assets/uploads/2017/11/image2-768x552.jpg" | relative_url }} 768w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" />  
I started this project thinking I can pull it off with CSS filters on a video element, but it turns out that is way to slow. So I ended up using WebGL via [glfx.js](http://evanw.github.io/glfx.js/). Tried to make is as progressive as possible, you can add it to your home screen. I won&#8217;t bore you with the details, check out the [source](https://github.com/eeejay/phoropter) when you have a chance.  
There are still many more filters I can add later. In the meantime, open this in your mobile browser and,  
[<img class="size-full wp-image-1322 aligncenter" src="{{ "/assets/uploads/2017/11/cooltext264671948409237.png" | relative_url }}" alt="Collect Them All!" width="633" height="115" srcset="{{ "/assets/uploads/2017/11/cooltext264671948409237.png" | relative_url }} 633w, {{ "/assets/uploads/2017/11/cooltext264671948409237-300x55.png" | relative_url }} 300w" sizes="(max-width: 633px) 100vw, 633px" />](https://eeejay.github.io/phoropter)