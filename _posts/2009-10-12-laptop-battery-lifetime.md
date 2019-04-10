---
id: 273
title: Laptop Battery Lifetime
date: 2009-10-12T12:36:20+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=273
permalink: /2009/10/12/laptop-battery-lifetime/
original_post_id:
  - "273"
categories:
  - Software
  - Technology
---
Hey,  
What&#8217;s up with my battery? I got this laptop, a Lenovo T400, about a year ago, and my 4 cell battery is reporting 37.4% capacity. This sucks. I&#8217;m going to need to get a new one.  
`eitan@sparky:~$ cat /proc/acpi/battery/BAT0/info<br />
present:                 yes<br />
design capacity:         37440 mWh<br />
last full capacity:      14010 mWh<br />
battery technology:      rechargeable<br />
design voltage:          14400 mV<br />
design capacity warning: 700 mWh<br />
design capacity low:     200 mWh<br />
capacity granularity 1:  1 mWh<br />
capacity granularity 2:  1 mWh<br />
model number:            42T4573<br />
serial number:            2242<br />
battery type:            LION<br />
OEM info:                SONY<br />
`  
What did I do to deserve this? Any fellow Internet users know? I have been running alpha versions of Ubuntu often, has there been some major power management bug that may have killed my battery? Have my usage habits been destructive? I can&#8217;t think of any awful abuse that I put my battery through.