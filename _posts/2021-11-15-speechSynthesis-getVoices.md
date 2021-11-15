---
title: 'speechSynthesis.getVoices()'
author: Eitan
layout: post
permalink: /2021/11/15/speechSynthesis-getVoices/
geo_public:
  - "0"
publicize_twitter_user:
  - eeejay
categories:
  - Software
  - Technology
---

Half of the DOM [Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API) deals with speech synthesis. There is a method called `speechSynthesis.getVoices` that returns a list of all the supported voices in the given browser. Your website can use it to choose a nice voice to use, or present a menu to the user for them to choose.

The one tricky thing about the `getVoices()` method is that the underlying implementation will usually not have a list of voices ready when first called. Since speech synthesis is not a commonly used API, most browsers will initialize their speech synthesis lazily in the background when a `speechSynthesis` method is first called. If that method is `getVoices()` the first time it is called it will return an empty list. So what will conventional wisdom have you do? Something like this:

```js
function getVoices() {
  let voices = speechSynthesis.getVoices();
  while (!voices.length) {
    voices = speechSynthesis.getVoices()
  }

  return voices;
}
```

If synthesis is indeed not initialized and first returns an empty list, the page will hang in an infinite CPU-bound loop. This is because the loop is monopolizing the main thread and not allowing synthesis to initialize. Also, an empty voice list is a valid value! For example, Chrome does not have speech synthesis enabled on Linux and will always return an empty list.

So, to get this working we need to not block the main thread by making asynchronous calls to `getVoices`, we should also have a limit on how many times we attempt to call `getVoices()` before giving up, in the case where there are indeed no voices:

```js
async function getVoices() {
  let voices = speechSynthesis.getVoices();
  for (let attempts = 0; attempts < 100; attempts++) {
    if (voices.length) {
      break;
    }

    await new Promise(r => requestAnimationFrame(r));
    voices = speechSynthesis.getVoices();
  }

  return voices;
}
```

But that method still polls, which isn't great and is needlessly wasteful. There is another way to do it. You could rely on the `voiceschanged` DOM event that will be fired once synthesis voices become available. We will also add a timeout to that so our async method returns even if the browser never fires that event.

```js
  async function getVoicesAsync() {
    const GET_VOICES_TIMEOUT = 2000; // two second timeout

    let voices = window.speechSynthesis.getVoices();
    if (voices.length) {
      return voices;
    }

    let voiceschanged = new Promise(
      r => speechSynthesis.addEventListener(
        "voiceschanged", r, { once: true }));

    let timeout = new Promise(r => setTimeout(r, GET_VOICES_TIMEOUT));

    // whatever happens first, a voiceschanged event or a timeout.
    await Promise.race([voiceschanged, timeout]);

    return window.speechSynthesis.getVoices();
  }
```

You're welcome, Internet!