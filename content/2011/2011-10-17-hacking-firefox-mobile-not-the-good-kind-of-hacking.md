---
id: 496
title: Hacking Firefox Mobile, Not The Good Kind Of Hacking
date: 2011-10-17T07:57:59+00:00
author: Eitan
layout: post
guid: http://www.monotonous.org/?p=496
permalink: /2011/10/17/hacking-firefox-mobile-not-the-good-kind-of-hacking/
original_post_id:
  - "496"
categories:
  - Accessibility
  - Software
---
Hi again. Remember my first post to Planet Mozilla? I hope not. Sorry for the [male enhancement pills spam](http://yfrog.com/jyeitanplanetfeedp). Please stop contacting me for orders.  
I am in Toronto right now, spending a week with Mobile folks. It has been about 6 weeks since I started working on a mobile extension, and the list of dirty tricks we employing to get things done is growing. Some of these hacks are there because there is no alternative, and some are there because I just didn&#8217;t figure out the right way to do it.  
Here is a short list:

Gestures
:   I reinvented them, poorly. Our extension relies heavily on the ability to support a rich set of multi touch gestures. We have a hack, similar to how it was done in [Touching is Good](https://addons.mozilla.org/en-US/mobile/addon/touching-is-good/?src=search "Touching Is Good! Addon page") (I know!), where we swap out the callbacks in MouseModule and GestureModule for our own. This doesn&#8217;t seem right, for a few reasons. The main one being that this doesn&#8217;t seem like a real public API, and it will be broken sooner or later. The second thing is the fact that we are relying on [shaky JS](https://github.com/eeejay/Talk-To-Me/blob/master/content/gesture_mangler.js "Are weird gesture mangler") to re-interpret the platform-interpreted events. So maybe there is a better way to do things. The [`nsIDOMSimpleGestureEvent`](https://developer.mozilla.org/En/NsIDOMSimpleGestureEvent) only serves us to a limited degree, I  think there is room for a more low-level multi touch event API that is similar to the Android one. Or maybe a comprehensive high level API with more event types.

Speech
:   This should probably be [implemented natively](https://bugzilla.mozilla.org/show_bug.cgi?id=687879 "Bug 687879 - Expose platform's text to speech functionality as XPCOM component") and have multi-platform support. Right now, in Android, we are doing Javascript <-> js-types <-> jni <-> Java. What could go wrong?! But seriously, [it is kind of ugly](https://github.com/eeejay/Talk-To-Me/blob/master/content/android_api.js) right now, but I would like to make our JS solution prettier and useful to other extension writers who want to tap in to Android&#8217;s API and services.

Security
:   The Mozilla profile directory in Android is not world-readable, presumably for good reasons. Our extension&#8217;s media files need to be world-readable so that Android&#8217;s TextToSpeech service could pick them up and use them as earcons. This requires an [install](https://github.com/eeejay/Talk-To-Me/blob/master/bootstrap.js#L51) and uninstall hook that uses Android&#8217;s Context.getDir to get/create a subdirectory in Firefox&#8217;s top-level app directory where we could copy over those media files for system consumption. Maybe this is the best way to do it&#8230; But I can&#8217;t imagine anyone being happy about an extension writing to that directory. Sorry!

&#8211;enable-accessibility
:   Our extension depends on accessibility being enabled at build time. Since I am getting some face time with folks this week, it seems like a good thing to bring up.
:   

I am sure there are other horrible horrible hacks in there. But the list above is really what I needed to confess to. Thanks for empathetic attention.