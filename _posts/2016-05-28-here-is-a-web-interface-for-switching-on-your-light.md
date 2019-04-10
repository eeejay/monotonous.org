---
id: 1130
title: Here is a web interface for switching on your light
date: 2016-05-28T00:09:04+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=1130
permalink: /2016/05/28/here-is-a-web-interface-for-switching-on-your-light/
publicize_twitter_user:
  - eeejay
categories:
  - Personal
  - Software
  - Technology
---
Like I mentioned in a [previous post](http://blog.monotonous.org/2016/05/25/autonomous-plant-watering/), I wanted to try out a more hackable wifi plug. I got a Kankun &#8220;smart&#8221; plug. Like the other one I have the software is horrible. The good news is that they left SSH enabled on it.  
Once I get SSH access I got to work on a web app for it. I spent an hour styling a pretty button, look:  
<img class="alignnone size-full wp-image-1141" src="{{ "/assets/uploads/2016/05/screen-shot-2016-05-28-at-00-01-06.png" | relative_url }}" alt="Screen shot of button in off state" width="2048" height="1536" srcset="{{ "/assets/uploads/2016/05/screen-shot-2016-05-28-at-00-01-06.png" | relative_url }} 2048w, {{ "/assets/uploads/2016/05/screen-shot-2016-05-28-at-00-01-06-300x225.png" | relative_url }} 300w, {{ "/assets/uploads/2016/05/screen-shot-2016-05-28-at-00-01-06-768x576.png" | relative_url }} 768w, {{ "/assets/uploads/2016/05/screen-shot-2016-05-28-at-00-01-06-1024x768.png" | relative_url }} 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" />  
And when you turn it on it looks like this:  
<img class="alignnone size-full wp-image-1143" src="{{ "/assets/uploads/2016/05/screen-shot-2016-05-28-at-00-01-12.png" | relative_url }}" alt="Screen shot of button in on state" width="2048" height="1536" srcset="{{ "/assets/uploads/2016/05/screen-shot-2016-05-28-at-00-01-12.png" | relative_url }} 2048w, {{ "/assets/uploads/2016/05/screen-shot-2016-05-28-at-00-01-12-300x225.png" | relative_url }} 300w, {{ "/assets/uploads/2016/05/screen-shot-2016-05-28-at-00-01-12-768x576.png" | relative_url }} 768w, {{ "/assets/uploads/2016/05/screen-shot-2016-05-28-at-00-01-12-1024x768.png" | relative_url }} 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" />  
Anyway, if you want to have a pretty webby button for controlling you wifi socket you can grab it [here](https://github.com/eeejay/kankun-switch).