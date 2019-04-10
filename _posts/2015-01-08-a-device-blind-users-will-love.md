---
id: 627
title: A Device Blind Users Will Love
date: 2015-01-08T07:00:00+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=627
permalink: /2015/01/08/a-device-blind-users-will-love/
geo_public:
  - "0"
publicize_twitter_user:
  - eeejay
publicize_twitter_url:
  - http://t.co/nI03RA04Co
categories:
  - Accessibility
  - Firefox OS
  - Software
---
<blockquote style="margin-bottom:1.5em;">
  <p style="margin-bottom:.5em;">
    The Internet is a global public resource that must remain open and <strong>accessible</strong>.
  </p><footer style="text-align:right;">— Mozilla manifesto</footer>
</blockquote>

Mozilla invests in accessibility, because it&#8217;s the right thing to do.  
We have staff, a team of engineers, who exclusively focus on accessibility in our products and play a positive influence in the general accessibility of the web. This has paid off well, Firefox is well regarded as a leader in screen reader support on the desktop and on Android. We have the best HTML5 accessibility support in our browser, and we are **close** to having a fully functional screen reader in Firefox OS.  
<img class="aligncenter wp-image-630 size-medium" src="{{ "/assets/uploads/2015/01/mozilla-accessibility_logo-only_rgb.png?w=300" | relative_url }}" alt="Mozilla accessibility logo" width="300" height="300" srcset="{{ "/assets/uploads/2015/01/mozilla-accessibility_logo-only_rgb.png" | relative_url }} 443w, {{ "/assets/uploads/2015/01/mozilla-accessibility_logo-only_rgb-150x150.png" | relative_url }} 150w, {{ "/assets/uploads/2015/01/mozilla-accessibility_logo-only_rgb-300x300.png" | relative_url }} 300w, {{ "/assets/uploads/2015/01/mozilla-accessibility_logo-only_rgb-100x100.png" | relative_url }} 100w" sizes="(max-width: 300px) 100vw, 300px" />  
I say &#8220;close&#8221;, because we are not yet there. Most websites are fairly accessible with little to no effort from the site developers. The document model of the web is relatively simple and is malleable enough that blind users are able to access them through screen readers. Advanced web applications are a whole other story, developers are required to be much more mindful about how they are authored and account for users with disabilities when designing them. The most recognized standard for making accessible rich internet application is called ARIA (accessible rich internet applications), and it allows augmenting markup with attributes that will help assistive technologies (such as screen readers) have a good understanding of the state of the app, and relay it to the user.  
In Firefox OS we have a suite of core apps called Gaia that is the foundation for Firefox OS&#8217;s user interface. It is really one giant web app, perhaps one of the biggest out there. Since our mission dictates that we make our products accessible, we have embarked on that journey, we created a [screen reader for Firefox OS](https://wiki.mozilla.org/Accessibility/Mobile/ScreenReader "Firefox OS Screen Reader demo and tutorial"), and we got to work in making Gaia screen-reader friendly. It has been a long and [sisyphean](http://en.wikipedia.org/wiki/Sisyphus "Sisyphus in Wikipedia") process, where we would arrive at one module in gaia, learn the code, fix some issues, and move on to the next module. It feels something like this:  
<figure id="attachment_634" style="width: 460px" class="wp-caption aligncenter"><img class="wp-image-634 size-large" src="{{ "/assets/uploads/2015/01/benicia_grass_fire_1-1024x684.jpg?w=460" | relative_url }}" alt="helicopter dumps water on a grass fire" width="460" height="307" srcset="{{ "/assets/uploads/2015/01/benicia_grass_fire_1-1024x684.jpg" | relative_url }} 1024w, {{ "/assets/uploads/2015/01/benicia_grass_fire_1-1024x684-300x200.jpg" | relative_url }} 300w, {{ "/assets/uploads/2015/01/benicia_grass_fire_1-1024x684-768x513.jpg" | relative_url }} 768w" sizes="(max-width: 460px) 100vw, 460px" /><figcaption class="wp-caption-text">A California Department of Forestry helicopter dumps water on a grass fire in Benicia. (Robinson Kuntz/Daily Republic)</figcaption></figure>  
Firefox OS has grown tremendously in a couple of years. Things never slowed down, and we were always revamping one app or another, trying out something new, and evolving rapidly. This means that accessibility was always one step behind. If we got an app accessible in version n, n+1 was around the corner with a whole new everything. Besides working on Gaia, we have always been looping back to our screen reader, making it more robust and adding features. We have consistently been straddling the gap:  
<img class="aligncenter wp-image-636 size-large" src="{{ "/assets/uploads/2015/01/thegap.jpg?w=460" | relative_url }}" alt="The gap between Firefox OS and the screen reader" width="460" height="563" srcset="{{ "/assets/uploads/2015/01/thegap.jpg" | relative_url }} 2204w, {{ "/assets/uploads/2015/01/thegap-245x300.jpg" | relative_url }} 245w, {{ "/assets/uploads/2015/01/thegap-768x939.jpg" | relative_url }} 768w, {{ "/assets/uploads/2015/01/thegap-837x1024.jpg" | relative_url }} 837w" sizes="(max-width: 460px) 100vw, 460px" />  
Firefox OS has achieved some amazing milestones in its short life. Early in the project, there was still a hushed uncertainty. Did we over promise? Could we turn a proof of concept into a mass-market device? There were so many moving parts for a version one release. Accessibility was not a product priority.

### The return on investment

<blockquote style="margin-bottom:1.5em;">
  <p style="margin-bottom:.5em;">
    When I think about making our products accessible for the people that can’t see or to help a kid with autism, I don’t think about a bloody ROI.
  </p><footer style="text-align:right;">— An angry Tim Cook</footer>
</blockquote>

Take 5 seconds, and let that sink in. Apple is not a charity, they are one of the most profitable companies on the planet. Still, they understand the social value of making their products accessible.  
Yet, I will argue that **there is a bloody return on investment in accessibility**.  
Mobile is changing our social perception on disability and blurring the line between permanent and temporary barriers. The prevailing assumption used to be that your user will sit in front of a 14&#8243; monitor with a keyboard, mouse and an undivided attention. But today there can be no assumptions, an app needs to be usable in many situations that impair the user in comparison to a desktop setup:

  * A user will browse the web on a small, 3.5&#8243; device with no keyboard, and only their inaccurate fat fingers as a pointing device for activating links.
  * A driver will need to keep their eyes on the road and cannot interact with complex interfaces.
  * A cyclist on a cold winter day will have gloves and will want to look up where they are going on a map.
  * A pedestrian will look up a nearby restaurant on a sunny day with plenty of glare making it hard to read their phone&#8217;s screen.

<figure id="attachment_655" style="width: 460px" class="wp-caption aligncenter"><img class="wp-image-655 size-large" src="{{ "/assets/uploads/2015/01/texting-while-driving.jpg?w=460" | relative_url }}" alt="A driver texting in traffic" width="460" height="325" srcset="{{ "/assets/uploads/2015/01/texting-while-driving.jpg" | relative_url }} 640w, {{ "/assets/uploads/2015/01/texting-while-driving-300x212.jpg" | relative_url }} 300w" sizes="(max-width: 460px) 100vw, 460px" /><figcaption class="wp-caption-text">This shouldn&#8217;t happen.</figcaption></figure>  
The edge case of <q>permanently impaired</q> users is eclipsed by the common mobile use case which needs to appeal to users with all sorts of temporal impairments: motor, visual and cognitive. Apple understands that with Siri, and Google does too with Google Now. In Firefox OS, sooner or later we will need a good voice input/output story.  
I made a case for accessibility, and I could probably stop here. But I won&#8217;t. Because **the real benefit of an accessible device is priceless**.  
<figure id="attachment_659" style="width: 460px" class="wp-caption aligncenter"><img class="wp-image-659 size-large" src="{{ "/assets/uploads/2015/01/impact_graph.jpg?w=460" | relative_url }}" alt="Graph showing impact on blind users in contrast to other users" width="460" height="589" srcset="{{ "/assets/uploads/2015/01/impact_graph.jpg" | relative_url }} 1832w, {{ "/assets/uploads/2015/01/impact_graph-234x300.jpg" | relative_url }} 234w, {{ "/assets/uploads/2015/01/impact_graph-768x983.jpg" | relative_url }} 768w, {{ "/assets/uploads/2015/01/impact_graph-800x1024.jpg" | relative_url }} 800w" sizes="(max-width: 460px) 100vw, 460px" /><figcaption class="wp-caption-text">While blind smart phone users are a small fraction of the general population, the impact on their lives is so much greater.</figcaption></figure>  
We all benefit from that smart phone in our pocket. The first iPhone was a real revolution. It allows us to check mail on the go, share our lives on social networks, ignore our family, and pretend like we we are doing something important in awkward parties. But for blind users, smart phones have increased their quality of life in profound and amazing ways. Blind smart phone owners are more independent, less isolated. and they can participate in online life like never before. Prior to smart phones, blind folks depended on very expensive gadgets for mobile computing. Today, a smart phone with a few handy apps could easily replace a $10,000 specialty device.  
Smart phones in the hands of blind users is **a very big deal**.  
[<img class="aligncenter size-large wp-image-658" src="{{ "/assets/uploads/2015/01/5953945.jpg?w=460" | relative_url }}" alt="Three blind iphone owners" width="460" height="268" srcset="{{ "/assets/uploads/2015/01/5953945.jpg" | relative_url }} 618w, {{ "/assets/uploads/2015/01/5953945-300x175.jpg" | relative_url }} 300w" sizes="(max-width: 460px) 100vw, 460px" />](http://www.stuff.co.nz/technology/gadgets/5953951/iPhone-4S-Life-changing-phone-for-blind)

### What we need to do

To make this happen, every decision by our product team, every design from UX, and every line of code from developers needs to account for the blind user experience. This isn&#8217;t as big a deal as it sounds, screen readers support is just another thing to account for, like localization. We know today that designing and developing UI for right-to-left languages take some consideration. Especially if you live in a left-to-right world.  
What we need is **project-wide consciousness around accessibility**. It is great that we have an <q>accessibility team</q>, and I think Mozilla benefits from it. But this does not let anyone else off the hook from understanding accessibility, embedding it in our products, and embracing it as a value.  
I fear that this post will disappoint because I won&#8217;t get into **how** blind users use smart phones, and **how** should developers account for the screen reader. I have written in the past about this, and [Yura](http://yzen.github.io/ "Yura's blog") has some good posts on that as well. And yes, we need to step up our game, document and communicate more.  
But for now, here are two things you could do to get a better picture:

  1. If you own an Android device or iPhone, turn on the screen reader, close your eyes and learn to use it. Challenge yourself to complete all sorts of tasks with your screen reader on. Test the screen readers limits.
  2. With your Firefox OS device, [turn on the screen reader](https://wiki.mozilla.org/Accessibility/Mobile/ScreenReader "Firefox OS Screen Reader demo and tutorial"). It works in the same fashion as the iOS or Android one does. Check your latest creation, and see what is broken and missing.

2015 is going to be a great year for Firefox OS. I have already heard all sorts of product ideas that have the potential of greatness. We are destined to ship something **amazing**. But for bind users, it could be **life changing**.