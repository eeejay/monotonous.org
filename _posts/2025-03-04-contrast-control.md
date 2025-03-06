---
title: 'New Contrast Control Settings'
author: Eitan
layout: post
permalink: /2025/03/06/New-Contrast-Control-Settings/
geo_public:
  - "0"
publicize_twitter_user:
  - eeejay
categories:
  - Software
  - Technology
---

## What We Did

In today's nightly build of Firefox we introduced a simple three-state toggle for color contrast.

<img src="/assets/uploads/2025/03/new-tristate.png" alt="Screenshot of radio group in Firefox settings">

It allows you to choose between these options:

Automatic (use system settings)
: Honor the system's high contrast preferences in web content. If this is enabled, and say you are using a Windows High Contrast theme, the web content's style will be overridden wherever needed to display text and links with the system's colors.

Off
: Regardless of the system's settings the web content should be rendered as the content author intended. Colors will not be forced.

Custom
: Always force user specified colors in web content. Colors for text and links foreground and background can be specified in the preferences UI.

## Who Would Use This and How Would They Benefit?

There are many users with varying degrees of vision impairment that benefit from having control over the colors and intensity of the contrast between text and its background. We pride ourselves in Firefox for offering fine grained control to those who need it. We also try to do a good job anticipating the edge cases where forced high contrast might interfere with a user's experience, for example we put a solid background backplate under text that is superimposed on top of an image.

But, the web is big and complex and there will always be cases where forced colors will not work. For example, take this Wordle puzzle:
<img src="/assets/uploads/2025/03/wordle-1.png" alt="Wordle with default colors" style="margin: auto; display: block; max-width: 50%;">

The gold tiles indicate letters that are in the hidden word, and gold tiles represent letters that are in the word and in the right place in the word.

When a user is in forced colors mode, the background of the tiles disappears and the puzzle becomes unsolvable:
<img src="/assets/uploads/2025/03/wordle-2.png" alt="Wordle with default colors" style="margin: auto; display: block; max-width: 50%;">

## What More Can We Expect?

The work we did to add contrast control to the settings is a first step in allowing a user to quickly configure their web browser experience in order to adapt to their current uses. Just like text zoom, there is no one-size-fits-all. We will be working to allow users to easily adjust their color contrast settings as they are browsing and using the web.