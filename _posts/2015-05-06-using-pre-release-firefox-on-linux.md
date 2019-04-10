---
id: 673
title: Using Pre-release Firefox on Linux
date: 2015-05-06T12:27:01+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=673
permalink: /2015/05/06/using-pre-release-firefox-on-linux/
geo_public:
  - "0"
publicize_twitter_url:
  - http://t.co/hMk1h6F01K
publicize_twitter_user:
  - eeejay
categories:
  - General
  - Software
  - Technology
---
Every committed Mozillian and many enthusiastic end-users will use a pre-release version of Firefox.  
In Mac and Windows this is pretty straightforward, you simply download the Firefox Nightly/Aurora/Beta dmg or setup tool, and get going. When it is installed it is a proper desktop application, you could make it your default browser, and life goes on.  
In Linux, we rely much more on packagers to prepare an application for the distribution before we could use it. This usually works really well, but sometimes you really just want to use an upstream app without any gatekeepers.  
The pre-release versions of Firefox for Linux comes in tarballs. You unpack them, and could run them out of the unpacked directory. But it doesn&#8217;t run well. You can&#8217;t set them as your default browser, the icon is a generic square, and opening links from other apps is a headache. In short, it&#8217;s a less than polished experience.  
So here is a small script I wrote, it does a few things:

  1. It downloads the latest Firefox from the channel of your choosing.
  2. It unpacks it into a hidden directory in your $HOME
  3. It adds a symbolic link to the main executable in `~/.local/bin` .
  4. It adds symbolic links for the icon&#8217;s various sizes into your icon theme in `~/.local/share/icons`.
  5. It adds a desktop file to `~/.local/share/applications`.

It doesn&#8217;t require root privileges, and is contained to your home directory so it won&#8217;t conflict with the system Firefox installation or touch the system `libxul`. Typically, you only need to run the script once per channel. After a channel is installed, they will get automatic updates through the actual app.  
<figure id="attachment_674" style="width: 660px" class="wp-caption aligncenter">[<img class="size-large wp-image-674" src="{{ "/assets/uploads/2015/05/screenshot-from-2015-05-06-12-08-51.png?w=660" | relative_url }}" alt="Nightly running in Fedora 22" width="660" height="371" srcset="{{ "/assets/uploads/2015/05/screenshot-from-2015-05-06-12-08-51.png" | relative_url }} 3200w, {{ "/assets/uploads/2015/05/screenshot-from-2015-05-06-12-08-51-300x169.png" | relative_url }} 300w, {{ "/assets/uploads/2015/05/screenshot-from-2015-05-06-12-08-51-768x432.png" | relative_url }} 768w, {{ "/assets/uploads/2015/05/screenshot-from-2015-05-06-12-08-51-1024x576.png" | relative_url }} 1024w" sizes="(max-width: 660px) 100vw, 660px" />](/assets/uploads/2015/05/screenshot-from-2015-05-06-12-08-51.png)<figcaption class="wp-caption-text">See the nice icon?</figcaption></figure>  
So, here are some commands you could copy to your terminal and have pre-release Firefox installed:

##### Nightly

`curl https://raw.githubusercontent.com/eeejay/foxlocal/master/foxlocal.py  | python - nightly`

##### Aurora

`curl https://raw.githubusercontent.com/eeejay/foxlocal/master/foxlocal.py  | python - aurora`

##### Beta

`curl https://raw.githubusercontent.com/eeejay/foxlocal/master/foxlocal.py  | python - beta`

##### Release

`curl https://raw.githubusercontent.com/eeejay/foxlocal/master/foxlocal.py  | python - release`