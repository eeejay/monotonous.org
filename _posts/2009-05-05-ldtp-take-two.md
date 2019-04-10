---
id: 190
title: 'LDTP &#8211; Take Two'
date: 2009-05-05T01:04:10+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=190
permalink: /2009/05/05/ldtp-take-two/
openid_comments:
  - 'a:1:{i:0;s:5:"15703";}'
original_post_id:
  - "190"
categories:
  - Software
  - Technology
---
Recently some brave individuals started working on an upstream automated testing project for GNOME. This is exciting.  
I say brave because we had a discussion regarding this a couple of years back, and if I recall correctly we stalled when it came to choosing an automation library. Anyway, it was decided that we will be going ahead with LDTP, big step.  
LDTP is a mature library, and being such it had accrued sets of requirements from the different utilizers. The core is threaded, and written in cspi, which is unmaintained today, and uses a raw socket to communicate to the client end.  
With [Nagappan](http://nagappanal.blogspot.com/)&#8216;s blessing, I started work on a Python rewrite of the core. The main goal being to simplify the code-base and prepare LDTP for the eventual migration of AT-SPI to D-Bus. We also chose to use higher level protocols for communication: XML-RPC. Also, this new version does away with threading in favor of an event loop that plays nicely with AT-SPI events.  
After a week of work, I became fairly pleased with the shape it has taken. I used introspection wherever possible as not to duplicate the API both on the client and on the server. The introspection also helps in generating ooldtp&#8217;s API, the object oriented interface to LDTP.  
The code could be checked out from my [github tree](http://github.com/eeejay/ldtp2/tree/master "Github repository").