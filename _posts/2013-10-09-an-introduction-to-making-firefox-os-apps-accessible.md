---
id: 531
title: An Introduction To Making Firefox OS Apps Accessible
date: 2013-10-09T18:15:40+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=531
permalink: /2013/10/09/an-introduction-to-making-firefox-os-apps-accessible/
enclosure:
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
  - |
    http://people.mozilla.org/~eisaacson/screenreaderextension.webm
    1247415
    video/webm
    
publicize_twitter_user:
  - eeejay
publicize_twitter_url:
  - http://t.co/JGMzlbdAq4
categories:
  - Accessibility
  - Firefox OS
  - Software
tags:
  - fxosa11yworkshop
---
Hello! This is a first post in a series that will outline the challenges and remedies for making an accessible app in Firefox OS.  
**First** you may ask, accessible to whom? Good question. Accessibility is a very broad term. There are many reasons why Firefox OS would not be available to an individual. In this series we will focus on making apps that are accessible to blind users.  
**Secondly** you may ask, how does a blind person use a Firefox OS device? They can&#8217;t. At least not yet. The accessibility team at Mozilla is focusing on bringing together the right tools and integrating them into Firefox OS to make that happen. Namely, we are working on a screen reader.  
**Thirdly** you may ask, how does a blind user use a touch screen smartphone? Very efficiently. When the iPhone 3GS was introduced, it came with a screen reader. Today, iOS devices are very popular among blind users. With a few simple gestures, the entire feature-set of a smartphone becomes available to visually impaired people. This video highlights how that is done with the iPhone:  
[youtube=http://www.youtube.com/watch?v=tVruB7I2G14&w=560&h=315]  
In Firefox OS we are working on a screen reader with a very similar interaction model to both iOS and Android&#8217;s solutions. The main design principal is to allow the user to explore the display with their touch without directly affecting the state of the underlying apps. To interact with an application, for example to activate a control, the user first finds the control by “feeling around” on the screen and then double-taps to activate it. In addition to exploring by touch, the user could flick left or right to advance through the UI in a linear fashion. That is the basic idea, there are many more features and gestures that a user could learn. But if they got the basics, they are good to go.  
**Fourthly** you may ask, if there is no screen reader available on Firefox OS, how do I test my app to assure it works for blind users? There are two answers here.

## Screen Reader Simulator Extension

If you work on Gaia with desktop Firefox, there is an extension that is automatically downloaded when you make with DEBUG=1. You can also use the extension, outside of Gaia, in a standalone fashion with Nightly. It is available here. This extension adds a devtools panel simply called “Screen Reader”. It has an “Enable” button. Once that button is toggled, the content view will have our screen reader applied to it. If you hold your mouse button and drag it along the screen, you will notice an orange rectangle highlighting different items. You will also notice that the main area of the devtools panel starts to populate with text. This is a log of what a blind user would hear as synthesized text. The extension has additional toolbar buttons, the “Navigation” buttons are there for you to easily navigate through the content, if you press the center button the highlighted item will be activated, for example a link would be clicked. The “Scroll” section allows you to scroll the currently active view. This is useful since the touchscreen gesture for scrolling is a two finger swipe, which is hard to do on most desktops. Here is a [silent screencast](http://people.mozilla.org/~eisaacson/screenreaderextension.webm "Screencast of screen reader simulator") of the extension in action.

## Enabling The Screen Reader On The Device

You should only do this if you understand how the screen reader works. It could be hard to undo if you don&#8217;t, and you may end up needing to clobber your Gaia profile to get your device back. But if you are OK with all that, it is easy. You just need a build off of master (version 1.3), go to the Settings app, and drill down to the developer settings (Device Information->More information->Developer), under the Accessibility header is a checkbox for the screen reader. Enable that. That is it, you should have a talking device!