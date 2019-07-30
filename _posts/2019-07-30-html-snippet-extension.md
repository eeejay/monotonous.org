---
title: 'HTML Text Snippet Extension'
author: Eitan
layout: post
permalink: /2019/07/30/html-snippet-extension/
geo_public:
  - "0"
publicize_twitter_user:
  - eeejay
categories:
  - Software
  - Technology
---
I often need to quickly test a snippet of HTML, mostly to see how it interacts with our accessibility APIs.

Instead of creating some throwaway HTML file each time, I find it easier to paste in the HTML in devtools, or even make a data URI.

Last week I spent an hour creating an extension that allows you to just paste some HTML into the address bar and have it rendered immediately.

You just need to prefix it with the `html` keyword, and you're good to go. Like this `html <h1>Hello, World!</h1>`.

You can [download it from github](https://github.com/eeejay/quicksnippet/releases).

There might be other extensions or ways of doing this, but it was a quick little project.