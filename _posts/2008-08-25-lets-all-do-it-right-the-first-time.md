---
id: 83
title: 'Let&#039;s all do it right the first time'
date: 2008-08-25T12:49:48+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=83
permalink: /2008/08/25/lets-all-do-it-right-the-first-time/
openid_comments:
  - 'a:1:{i:0;s:4:"7876";}'
  - 'a:1:{i:0;s:4:"7876";}'
original_post_id:
  - "83"
categories:
  - Accessibility
  - Technology
tags:
  - specular
---
For the last month or so I have been plugging away and thinking of efficient and approachable ways for testing [WAI-ARIA](http://www.w3.org/WAI/intro/aria "WAI-ARIA overview on W3C") conformance across browsers. When Firefox first implemented ARIA there was plenty of hard work being done both by the Firefox developers and the assistive technology developers to assure that users will have a smooth experience when they encounter rich internet applications using Firefox. The accessible web experience is fortunately spreading with [Webkit](https://bugs.webkit.org/show_bug.cgi?id=12132 "Webkit ARIA Bugzilla bug"), [Opera](http://dev.opera.com/articles/view/introduction-to-wai-aria/ "Intro to ARIA on Opera Dev Site") and [IE](http://msdn.microsoft.com/en-us/library/cc304059(VS.85).aspx "MSDN article about ARIA in IE8") working on their own ARIA implementations. What we really needed was an accessibility &#8220;acid test&#8221; to assure that these discrete implementations share enough in common so that screen readers and the likes will support all browsers with minimal blood sweat and tears.  
I reached a couple of dead ends. Nonetheless I hope that most of that code has not been written in vain. For example, I have a Python library that does accessible tree comparisons using [an algorithm that produces a minimal delta](https://d2.dev.java.net/doc/pdf/DomDiff-research.pdf "Change Detection in Hierarchically Structured Information") description. This makes it easy to quickly spot differences in large and complex accessible node trees.  
Anyway, I happened upon an awesome project called [Selenium](http://selenium.openqa.org "Selenium Homepage") that provides automated cross-browser, cross-platform web testing. This was a good find. Besides being browser and platform agnostic, Selenium is also fairly language and test framework agnostic, allowing tests to be written comfortably and integrated into any kind of test framework and scripting language.  
Besides the Selenium &#8220;remote control&#8221; that runs on test target machines, I created another service called Specular, or Speclenium (the serializer and core is Specular, the specific service that works with Selenium is Speclenium). This server communicates with the remote control via XML-RPC and relays accessibility related assertions and verifications. This allows Speclenium to &#8220;do one thing well&#8221; and deal exclusively with accessibility related tests. Since Specular/Speclenium is written in Python, I was able to take advantage of both pyatspi and pyia to provide cross-platformness (Win32 and Unix). This allows writing tests that will work on both platforms.  
<figure id="attachment_86" style="width: 450px" class="wp-caption aligncenter">[<img class="size-full wp-image-86" title="Diagram of Selenium and Speclenium topology" src="{{ "/assets/uploads/2008/08/spec-dia-brief.png" | relative_url }}" alt="Diagram of Selenium and Speclenium topology" width="450" height="285" />]({{ "/assets/uploads/2008/08/spec-dia.png" | relative_url }})<figcaption class="wp-caption-text">Diagram of Selenium and Speclenium topology</figcaption></figure>  
This is what you need to get it up and running:

  * [Java](http://www.java.com/getjava/ "Java download site"), [Python](http://www.python.org/download/ "Python download page") and [Twisted](http://twistedmatrix.com/trac/wiki/Downloads "Twisted download page").
  * [Pyia](http://github.com/eeejay/pyia/tree/master "Pyia tree on Github"), or [pyatspi](http://live.gnome.org/GAP/PythonATSPI "Pyatspi wiki page"), depending on what your platforms are.
  * Modified Selenium RC and core, you could get a snapshot [here]({{ "/files/selenium-remote-control-1.0-SNAPSHOT-dist.zip" | relative_url }} "Modified Selenium RC Snapshot"). 
      * If you want to build it yourself, you will need both [selenium-core](http://github.com/eeejay/selenium-core/tree "Selenium core on my github account") and [selenium-remote-control](http://github.com/eeejay/selenium-remote-control/tree "Selenium RC on my github account") from my github repo. Read the [Selenium-RC Developer&#8217;s Guide](http://wiki.openqa.org/display/SRC/Developer%27s+Guide "Selenium RC Developr's Guide") for building it.
  * [Specular/Speclenium](http://github.com/eeejay/specular/tree/master "Specular repo on github").

Note to non-git users: You don&#8217;t need to download and learn git. Github provides download links with current snapshots of the files in the repo.  
Setup steps:

  1. Set up the target machine: 
      1. Run selenium-server on the machine with the test environment.
      2. On the same machine run &#8216;speclenium&#8217;, it&#8217;s a Python executable in the specular package.
  2. On another machine (or the same one), set up the speclenium test scripts. 
      1. Customize tests/settings.py in the specular package. It should point to your target machines and to the available browsers. It&#8217;s pretty self explanatory.
      2. I provided some sample tests that could be run with the run\_tests Python executable. Try &#8220;run\_tests -h&#8221; to get an idea of how to run them.

I&#8217;ll provide a screencast in the future for the lazy folks. In any case, I hope to polish up all the steps above and make setup a pleasant and simple experience. This is important especially in Windows where prerequisites could be a pain the the behind.  
Oh yeah, the other use case for this hairball is accessible web application development. If you are a l33t web developer, and you test your code with Selenium, you should use Speclenium too!  
That&#8217;s a long post. I hope to make all of that less complicated and streamlined in the near future.