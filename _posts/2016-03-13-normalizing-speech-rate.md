---
id: 751
title: Normalizing Speech Rate
date: 2016-03-13T12:29:31+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=751
permalink: /2016/03/13/normalizing-speech-rate/
publicize_twitter_user:
  - eeejay
categories:
  - Accessibility
  - Software
  - Technology
  - Uncategorized
---
While working on the speech synthesis API in Firefox, I have been trying to figure out how to provide the most consistent experience across different desktop platforms. This is tricky, because each platform has its own speech API. Each API has slightly differing feature sets and idiosyncrasies.  
A good way to foresee the difficulties others will encounter when writing a cross-platform speech app, is to actually write one. So when we started work on the Narrate feature, I needed to account for the fact that the Linux speech API is not capable of pausing speech mid-utterance. We managed to design the interface in a way that wouldn&#8217;t require pausing speech, but still give the user an intuitive way of stopping and starting the narration mid-way through the article.  
When we landed Narrate, [Ehsan](https://ehsanakhgari.org/blog) noticed that the speech rate slider in the interface was [useless at either extremes](https://bugzilla.mozilla.org/show_bug.cgi?id=1254234). Either silly fast, or glacially slow. Since I was developing this feature on Linux, I didn&#8217;t encounter the fast rates OSX users experienced. I first thought this was a bug in our OSX speech synthesis support, but later realized Mac was the exception, and this was an issue with the rate conversion in Linux and Windows.  
Speech rate is subjective, in so many ways. What is a &#8220;normal&#8221; speech rate? I have found many numbers, ranging from 150 to 200 words per minute for US English speakers. Luckily, when it comes to the web API we don&#8217;t care what the &#8220;normal&#8221; rate is, we care about relative rate. But that doesn&#8217;t completely solve our conundrum.  
The Web Speech API (and SSML) defines the rate as a multiplier of the normal speech rate for a given voice. Meaning, 1 is normal, 2 is twice the speed and 0.5 is half. The speech rate goes through a few conversions:

  1. Web page provides a rate to the browser
  2. The browser converts the rate to the platform-specific speech API.
  3. The speech API converts the rate to the speech engine API.
  4. In some cases, the voice converts the rate value the engine provides it.

In OSX, life of course is easiest. The rate is defined as words per minute, their docs say &#8220;normal&#8221; is between 180 to 220. All we need to do is multiply that, and we get a predictable rate. Things get a little hairier on Linux and Windows. In Linux, the Speech Dispatcher API docs says that rate should be an integer between -100 and 100 with 0 being default. In Windows, the situation is not much better: from a cursory glance at the docs for [ISpVoice::SetRate](https://msdn.microsoft.com/en-us/library/ms719798(v=vs.85).aspx), it just specifies that accepted rates are between -10 and 10.  
Further digging brought up more information on Linux and Windows that made the rate parameter a bit more understandable:

  * In Linux, Speech Dispatcher&#8217;s eSpeak output module configuration file shows that the default rate is 160 wpm, the minimum is 80, and the max is 320. That&#8217;s pretty conservative, but at least it gives us an idea of what is going on.
  * [Deeply buried in the Windows docs](https://msdn.microsoft.com/en-us/library/ee431826(v=vs.85).aspx), I found a mention that the max is 3x normal, and the minimum is a third normal rate.

Now we have something to work with! Did I bore you? I am boring myself..  
Next post, a speech rate benchmark tool, pretty graphs, and my attempt at &#8220;math&#8221;!  
&nbsp;