---
id: 429
title: GNOME Accessibility Via JHBuild
date: 2011-01-17T02:23:20+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=429
permalink: /2011/01/17/gnome-accessibility-via-jhbuild/
original_post_id:
  - "429"
categories:
  - Accessibility
  - Software
---
So a couple of weeks ago I ported Caribou to GTK+ 3 and PyGI. I also stopped testing it (and implicitly stopped supporting it) with CORBA AT-SPI. This means that if you want to download and test Caribou, or any GNOME 3.0 accessibility module for that matter, you need to jump through hoops to get all the prerequisites. There are two sane options:

  1. Install a pre-release distro like Ubuntu 11.04 or Fedora Rawhide. While the Caribou package is not necessarily up to date on these platforms, the prerequisites generally are, so you just need to clone Caribou from git.
  2. Use JHBuild. This is what all serious GNOME testers and developers use. Unfortunately Caribou is not in the current moduleset, and neither are some dependencies. Fortunately, I wrote a small [moduleset](http://people.gnome.org/~eitani/a11y/gnome-a11y-3.0.modules) file that takes the shortest path to having a working version of Caribou for your testing needs. It also has Orca, and other modules will be added in the future. This should probably go into upstream jhbuild eventually.

Once you have [installed JHBuild](http://library.gnome.org/devel/jhbuild/stable/getting-started.html.en), use the configuration below in your .jhbuildrc, or create .jhbuildrc.a11y, and use jhbuild -f if you have a working jhbuild environment you don&#8217;t want to mess with.  
`build_policy = 'updated'<br />
moduleset = 'http://people.gnome.org/~eitani/a11y/gnome-a11y-3.0.modules'<br />
modules = ['meta-gnome-a11y']<br />
checkoutroot = os.path.expanduser('~/gnome-a11y/source')<br />
prefix = os.path.expanduser('~/gnome-a11y/install')<br />
skip = ['gudev']`  
Next, run `jhbuild bootstrap` to install build tools, and install some other development libraries that are worth skipping in jhbuild (for now it&#8217;s just gudev).  
In Fedora:  
`yum install libgudev1-devel`  
In Debian/Ubuntu:  
`apt-get install libgudev-1.0-dev`  
Run `jhbuild build`, and watch things compile successfully.  
Now, the hairy part about GNOME accessibility is the fact that there is an AT-SPI registry that needs to start with the session. Optimally the registry runs on a dedicated accessibility D-Bus bus. First you need to make sure you installed and enabled at-spi2 through your distro. On Ubuntu you might want to install it via [PPA](https://launchpad.net/~accessibility-dev/+archive/ppa), on Fedora 14 it already is in the repositories, search for ﻿at-spi2. Next you need to enable desktop accessibility and D-Bus support:  
`gconftool-2 --set /desktop/gnome/interface/at-spi-corba --type bool false<br />
gconftool-2 --set /desktop/gnome/interface/at-spi-dbus --type bool true<br />
gconftool-2 --set /desktop/gnome/interface/accessibility --type bool true`  
There are a lot of tricks to get the newly built registry to run in your session, but the easiest way is also the most hackish, simply edit `/usr/share/dbus-1/services/org.a11y.atspi.Registry.service` and substitute `/usr` with the prefix to your newly installed registry, for example `/home/eitan/gnome-a11y/install`. Log out and back in again, and you should be using the latest AT-SPI2 registry.  
If everything worked, running `jhbuild run caribou` should bring you the latest version of Caribou.  
Good luck!