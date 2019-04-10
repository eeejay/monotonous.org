---
id: 347
title: Networking Question
date: 2010-03-03T16:23:53+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=347
permalink: /2010/03/03/networking-question/
openid_comments:
  - 'a:10:{i:0;s:5:"27717";i:1;s:5:"27718";i:2;s:5:"27719";i:3;s:5:"27722";i:4;s:5:"27723";i:5;s:5:"27726";i:6;s:5:"27746";i:7;s:5:"27760";i:8;s:5:"27785";i:9;s:5:"28419";}'
original_post_id:
  - "347"
categories:
  - Software
  - Technology
---
I work out of coffee shops. It just depresses me to sit at home and not see a living soul all day besides the occasional house-mate.  
There is one shop that really allows me to get into my zone. It might have something to do with the liquor license, the ping pong table and loud music. The problem is, they somehow blocked all non-web traffic on their wifi hotspot. Since my day primarily revolves around IRC, XMPP, SMTP and SSH, I really can&#8217;t sit there for too long before I need to find somewhere that will allow me to push my git changes.  
So I thought I was being all clever when I set up OpenVPN on my private server and configured it to listen on TCP port 443. Does anyone have tips for tunneling arbitrary protocols through port 80/443? I thought the OpenVPN setup was especially nifty because it only required one NetworkManager click.