---
id: 670
title: eSpeak Web Speech API Addon
date: 2015-04-29T10:26:36+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=670
permalink: /2015/04/29/espeak-web-speech-api-addon/
publicize_twitter_user:
  - eeejay
publicize_twitter_url:
  - http://t.co/IjmE0MCDV1
categories:
  - Uncategorized
---
Now that [eSpeak runs pretty well in JS](http://blog.monotonous.org/2015/04/14/reintroducing-espeak-js/ "(re)Introducing eSpeak.js"), it is time for a Web Speech API extension!  
What is the Web Speech API? It gives any website access to speech synthesis (and recognition) functionality, Chrome and Safari already have this built-in. This extension adds speech synthesis support in Firefox, and adds eSpeak voices.  
For the record, we had speech synthesis support in Gecko for about 2 years. It was introduced for accessibility needs in Firefox OS, now it is time to make sure it is supported on desktop as well.  
Why an extension instead of built-in support? A few reasons:

  1. An addon will provide speech synthesis to Firefox **now** as we implement built-in platform-specific solutions for future releases.
  2. An addon will allow us to surface current bugs both in our Speech API implementation, and in the spec.
  3. We designed our speech synthesis implementation to be extensible with addons, this is a good proof of concept.
  4. People are passionate about eSpeak. Some people love it, some people don&#8217;t.

So now I will shut up, and let eSpeak do the talking:

  * [Download the latest version](https://addons.mozilla.org/en-US/firefox/addon/espeak-web-speech-api/).
  * [Check out the source.](https://github.com/eeejay/espeak-webspeech-api)
  * [Visit this speech synthesis demo page](http://eeejay.github.io/webspeechdemos/).