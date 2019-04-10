---
id: 75
title: 'I *heart* Translators'
date: 2008-06-12T18:15:03+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=75
permalink: /2008/06/12/i-heart-translators/
openid_comments:
  - 'a:2:{i:0;s:4:"5931";i:1;s:4:"5928";}'
  - 'a:2:{i:0;s:4:"5931";i:1;s:4:"5928";}'
original_post_id:
  - "75"
categories:
  - Software
  - Technology
---
I know that I am supposed to be all gratuitous and all when it comes to translators who do a thankless job, and improve software by orders of magnitude to make them accessible to many locales. I usually am very thankful.  
In the past month I have briefly turned my back Accerciser trunk, and in that time some cuddly translator managed to bugger it not once, but twice.  
Once when someone uncommented a comment in the LINGUAS file, which resulted in an unconfigurable tree. Another time when someone changed a *.po file to have executable permissions. This was more annoying, since there is some script there in s.g.o&#8217;s guts that rejects any commit if the repo has an executable. Now you know me, I never look at the output message after I commit to SVN, especially now since I am doing it through git. Result: all my commits to Accerciser in the last month have been rejected, and I never realized it.  
I know what you all are thinking:

  1. Why don&#8217;t you just look into the Subversion history, and see who is messing with you? Well, I prefer to remain ignorant, and make sweeping accusations &#8211; I am bored.
  2. How in hell did an executable po file get into the repo in the first place? I don&#8217;t know, and searching for the answer might lead me to the answer of the first question, so I won&#8217;t bother.