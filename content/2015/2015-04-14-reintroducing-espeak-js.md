---
id: 665
title: (re)Introducing eSpeak.js
date: 2015-04-14T14:31:52+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=665
permalink: /2015/04/14/reintroducing-espeak-js/
publicize_twitter_user:
  - eeejay
publicize_twitter_url:
  - http://t.co/lLfzsLqV9P
geo_public:
  - "0"
categories:
  - Accessibility
  - Software
  - Technology
---
## td;dr

Look! [A flashy demo with buttons](http://eeejay.github.io/espeak/emscripten/espeak.html)!

## Background

A long time ago, we were [investigating](https://bugzilla.mozilla.org/show_bug.cgi?id=525444) a way to expose text-to-speech functionality on the web. This was long before the [Web Speech API](https://dvcs.w3.org/hg/speech-api/raw-file/tip/speechapi.html) was drafted, and it wasn&#8217;t yet clear what this kind of feature would look like. Alon Zakai stepped up, and [proposed](https://bugzilla.mozilla.org/show_bug.cgi?id=525444#c22http://) porting eSpeak to Javascript with Emscripten. This was a provocative idea: was our platform powerful enough to support speech synthesis purely in JS? Alon got back a few days later with a working demo, the answer was &#8220;yes&#8221;.  
While the [speak.js](https://github.com/kripken/speak.js) port was very impressive, it didn&#8217;t answer many of our practical needs. For example, the latency was not good enough for making a responsive UI, you could wait more than a couple of seconds to hear a short phrase. In addition, the longer the text you wanted to synthesize, the longer you needed to wait.  
It proved a concept, but there were missing pieces we didn&#8217;t have four years ago. Today, we live in the future of 2011, and things that were theoretical then, are possible now (in the future).

### asm.js

Today, Emscripten will compile C/C++ code into a subset of Javascript called asm.js. This subset is optimized on all current browsers, and allows performance to be about 2x native. That is really good. eSpeak is a pretty lightweight library already, the extra performance boost of asm.js makes speech instantaneous.

### Transferable Objects

Passing data between a web worker and a parent process used to mean a lot of copying, since the worker doesn&#8217;t share memory with the parent process. But today, you can transfer ownership of ArrayBuffers with zero copying. When the web worker is ready to send audio data back to the calling process, it could do so while maintaining a single copy of the audio buffer.

### Web Audio API

We have a slick, full featured Audio API today on the web. When speak.js came out in 2011, it used a prefixed method on an `<audio>` element to write PCM data to. Today, we have a proper API that enables us to take the audio data and send it through an elaborate pipeline of filters and mixers, or even send it into the ether with WebRTC.

### Emscripten Got Fancy

This was my first time playing with it, so I am not sure what was available in 2011. But, if I have to guess, it was not as powerful and fun to work with. Emscripten&#8217;s new WebIDL support makes adding bindings extremely easy. You still get a chance to do some pointer arithmetic, but that&#8217;s supposed to be fun. Right?

## So here is eSpeak.js!

I wanted to do a real API port, as opposed to simply porting a command line program that takes input and writes a WAV file. Why? two main reasons:

  1. eSpeak can progressively synthesize speech. If you provide a callback to espeak\_Synth(), it will be called repeatedly with as many samples as you defined in the buffer size. It doesn&#8217;t matter how long the text is that you want synthesized, it will fill the buffer and return it to you immediately. This allows for a consistent low latency from the moment you call espeak\_Synth(), until you could start playing audio.
  2. eSpeak supports events. If you use a callback, you get access to a list of events that provide a timestamp in the audio, and the type of event that occurs there, such as word or sentence boundaries.

And, of course, with all the recent-ish platform improvements above, I was really time for a [fresh attempt](https://github.com/eeejay/espeak/tree/emscripten).

### Future Work

  * Break up the data files. Right now, eSpeak.js is over a 2MB download. That&#8217;s because I packaged all the eSpeak data files indiscriminately. There may be a few bits that are redundant. On the flip side you get all 99 voice/language combinations (that&#8217;s a good deal for 2MB, eh?). It would be cool to break it up to a few data files and allow the developer to choose which voices to bundle or, even better, just grab them on demand.
  * Make a demo of the speech events. It makes my head hurt to think about how to do something compelling. But it is a neat feature that should somehow be shown.
  * ScriptProcessorNode is apparently deprecated. This is going to need to be ported to an AudioWorker once that is widely implemented.

<span style="font-size:200%;">I&#8217;m done apologizing, <a href="http://eeejay.github.io/espeak/emscripten/espeak.html">here is the demo</a>.</span>