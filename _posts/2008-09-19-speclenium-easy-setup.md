---
id: 97
title: 'Speclenium &#8211; Easy Setup'
date: 2008-09-19T15:17:42+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=97
permalink: /2008/09/19/speclenium-easy-setup/
openid_comments:
  - 'a:1:{i:0;s:4:"8594";}'
  - 'a:1:{i:0;s:4:"8594";}'
original_post_id:
  - "97"
categories:
  - Accessibility
  - Technology
tags:
  - specular
---
I created a couple of packages that will make it easier to start using Speclenium.

### Setting up the server

First, copy the Speclenium server to every test machine, if it is a Windows box, use [this]({{ "/files/Speclenium-standalone-win32-0.0.1.zip" | relative_url }} "Windows Speclenium Package") package, double click on speclenium.exe, everything needed for it to run is in that archive. If you are using Linux, use [this]({{ "/files/Speclenium-standalone-0.0.1.tar.gz" | relative_url }} "Linux Speclenium Package") package. You will need Python and Twisted installed for the Linux version.

### Setting up the test suite

The test suite could be run on the same machine, or a different one. You will need Python 2.5 for this. Down load [this]({{ "/files/Specular-testsuite-0.0.1.tar.gz" | relative_url }} "Speclenium test suite") package, adjust _settings.ini_ for your environment, and run _run_tests &#8211;help_.  
I need to set up a project page with all the latest packages and source code. Maybe on codetalks.org?