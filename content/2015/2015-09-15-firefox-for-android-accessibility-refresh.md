---
id: 660
title: Firefox for Android Accessibility Refresh
date: 2015-09-15T10:14:55+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=3
permalink: /2015/09/15/firefox-for-android-accessibility-refresh/
geo_public:
  - "0"
publicize_twitter_user:
  - eeejay
categories:
  - Accessibility
  - Software
  - Technology
---
When we first made Firefox accessible for Android, the majority of our users were using Gingerbread. Accessibility in Android was in its infancy, and certain things we take for granted in mobile screen readers were not possible.  
For example, swiping and explore by touch were not available in TalkBack, the Android screen reader. The primary mode of interaction was with the directional keys of the phone, and the only accessibility event was &#8220;focus&#8221;.  
The bundled Android apps were hardly accessible, so it was a challenge to make a mainstream, full featured, web browser accessible to blind users. Firefox for Android at the time was undergoing a major overhaul, so it was a good time to put some work into our own screen reader support.  
We were governed by two principals when we designed our Android accessibility solution:

  1. Integrate with the platform, even if it is imperfect. Don&#8217;t require the user to learn anything new. The screen reader was less than intuitive. If the user jumped through the hoops to learn how to use the directional pad, they endured enough. Don&#8217;t force them through additional steps. Don&#8217;t make them install addons or change additional settings.
  2. Introduce new interaction modes through progressive enhancements. As long as the user could use the d-pad, we could introduce other features that may make users even happier. There are a number of examples of where we did this: 
      * As early as our gingerbread support, we had keyboard quick navigation support. Did your phone have a keyboard? If so, you could press &#8220;h&#8221; to jump to the next heading instead of arrowing all the way down.
      * When Ice Cream Sandwich introduced explore by touch, we added swipe left/right to get to previous or next items.
      * We also added 3 finger swipe gestures to do quick navigation between element types. This feature got mixed feedback: It is hard to swipe with 3 fingers horizontally on a 3.5&#8243; phone.

It was a real source of pride to have the most accessible and blind-friendly browser on Android. Since our initial Android support our focus has gone elsewhere while we continued to maintain our offering. In the meantime, Google has upped its game. Android has gotten a lot more sophisticated on the accessibility front, and Chrome integrated much better with TalkBack (I would like to believe we inspired them).  
Now that Android has good web accessibility support, it is time that we integrate with those features to offer our users the seamless experience they expect. In tomorrows Nightly, you will see a few improvements:

  1. TalkBack users could pinch-zoom the web content with three fingers, just like they could on Chrome ([bug 1019432](https://bugzilla.mozilla.org/show_bug.cgi?id=1019432)).
  2. The TalkBack local context menu has more options that users expect with web content, like section, list, and control navigation modes ([bug 1182222](https://bugzilla.mozilla.org/show_bug.cgi?id=1182222)). I am proud of our section quick nav mode, I think it will prove to be pretty useful.
  3. We integrate much better with the system cursor highlight rectangle ([bug 1182214](http://bugzilla.mozilla.org/show_bug.cgi?id=1182214)).
  4. The TalkBack scroll gesture works as expected. Also, range widgets can be adjusted with the same gesture ([bug 1182208](https://bugzilla.mozilla.org/show_bug.cgi?id=1182208)).
  5. Improved BrailleBack support ([bug 1203697](https://bugzilla.mozilla.org/show_bug.cgi?id=1203697)).

That&#8217;s it, for now! We hope to prove our [commitment to accessibility](https://www.mozilla.org/en-US/about/manifesto/#principle-02) as Firefox [branches out to other platforms](https://www.marcozehe.de/2015/09/10/accessibility-features-in-firefox-for-ios/). Expect more to come.