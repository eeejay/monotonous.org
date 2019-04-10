---
id: 833
title: Benchmarking Speech Rate
date: 2016-03-17T13:44:57+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=833
permalink: /2016/03/17/benchmarking-speech-rate/
publicize_twitter_user:
  - eeejay
categories:
  - Accessibility
  - Software
  - Technology
  - Uncategorized
---
In my last post, I covered the speech rate problem as I perceived it. Understanding the theory of what is going on is half the work. I decided to make a cross-platform speech rate benchmark that would allow me to identify how well each platform conforms to rate changes.  
So how do you measure speech rate? I guess you can count words per minute. But in reality, all we want is relative speech rate. The duration of each utterance at given rates should give us a good reference for the relative rate. Is it perfect? Probably not. Each speech engine may treat the time between words, and punctuation pauses differently at different rates, but it will give us a good picture.  
For example. If it takes a speech service _α_ seconds to speak an utterance, it should take it _α/2_ seconds to to say the same thing with a rate of 2.0, or _2α_ at a rate of 0.5. If we want to measure the engines rate compliance across a set of different rates, we first get the utterance time with a &#8220;normal&#8221; rate of 1.0, and then the rest is simple division.  
[I wrote a tool to do just this](http://eeejay.github.io/webspeechdemos/rates.html). Play around with it. It is fun.

### Speech Rates in OSX

As I mentioned in the previous post, it looks like our OSX speech support is the only platform where we actually got it right. Running the rates benchmark on the Alex voice gives us these results:

<table class="table table-condensed">
  <tr>
    <th>
      Voice
    </th>
    
    <th class="ratecell">
      1/2.5
    </th>
    
    <th class="ratecell">
      1/2.25
    </th>
    
    <th class="ratecell">
      1/2
    </th>
    
    <th class="ratecell">
      1/1.75
    </th>
    
    <th class="ratecell">
      1/1.5
    </th>
    
    <th class="ratecell">
      1/1.25
    </th>
    
    <th class="ratecell">
      1
    </th>
    
    <th class="ratecell">
      1.25
    </th>
    
    <th class="ratecell">
      1.5
    </th>
    
    <th class="ratecell">
      1.75
    </th>
    
    <th class="ratecell">
      2
    </th>
    
    <th class="ratecell">
      2.25
    </th>
    
    <th class="ratecell">
      2.5
    </th>
  </tr>
  
  <tr class="result">
    <td>
      Alex
    </td>
    
    <td class="ratecell">
      0.415
    </td>
    
    <td class="ratecell">
      0.459
    </td>
    
    <td class="ratecell">
      0.521
    </td>
    
    <td class="ratecell">
      0.593
    </td>
    
    <td class="ratecell">
      0.688
    </td>
    
    <td class="ratecell">
      0.826
    </td>
    
    <td class="ratecell">
      1.00
    </td>
    
    <td class="ratecell">
      1.27
    </td>
    
    <td class="ratecell">
      1.52
    </td>
    
    <td class="ratecell">
      1.75
    </td>
    
    <td class="ratecell">
      1.99
    </td>
    
    <td class="ratecell">
      2.23
    </td>
    
    <td class="ratecell">
      2.48
    </td>
  </tr>
</table>

You know what would be prettier than a table? A graph! So I made the benchmark generate a graph that gives a good visualization of the rate distribution. I normalized it with a log10 so that you can get a better idea of distances in the graph. Here is what it looks like for a rate-conforming voice like Alex:  
<figure id="attachment_875" style="width: 1527px" class="wp-caption alignnone"><img class="alignnone size-full wp-image-875" src="{{ "/assets/uploads/2016/03/rate_osx_alex.png" | relative_url }}" alt="Rate distribution of Alex voice on OSX" width="1527" height="816" srcset="{{ "/assets/uploads/2016/03/rate_osx_alex.png" | relative_url }} 1527w, {{ "/assets/uploads/2016/03/rate_osx_alex-300x160.png" | relative_url }} 300w, {{ "/assets/uploads/2016/03/rate_osx_alex-768x410.png" | relative_url }} 768w, {{ "/assets/uploads/2016/03/rate_osx_alex-1024x547.png" | relative_url }} 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /><figcaption class="wp-caption-text">Rate distribution of Alex voice on OSX</figcaption></figure>  
OSX voices aren&#8217;t perfect. For example, the Hebrew Carmit Voice does not support rates under 0.5 (or above 3, but that is not shown here). If a rate out of the supported range is given, the voice will just go back to its default. That&#8217;s not too good! There may be some workarounds to make sure we at least use the max/min rate, but I didn&#8217;t check it out yet.

<table class="table table-condensed">
  <tr>
    <th>
      Voice
    </th>
    
    <th class="ratecell">
      1/2.5
    </th>
    
    <th class="ratecell">
      1/2.25
    </th>
    
    <th class="ratecell">
      1/2
    </th>
    
    <th class="ratecell">
      1/1.75
    </th>
    
    <th class="ratecell">
      1/1.5
    </th>
    
    <th class="ratecell">
      1/1.25
    </th>
    
    <th class="ratecell">
      1
    </th>
    
    <th class="ratecell">
      1.25
    </th>
    
    <th class="ratecell">
      1.5
    </th>
    
    <th class="ratecell">
      1.75
    </th>
    
    <th class="ratecell">
      2
    </th>
    
    <th class="ratecell">
      2.25
    </th>
    
    <th class="ratecell">
      2.5
    </th>
  </tr>
  
  <tr class="result">
    <td>
      Carmit
    </td>
    
    <td class="ratecell">
      0.926
    </td>
    
    <td class="ratecell">
      0.927
    </td>
    
    <td class="ratecell">
      0.520
    </td>
    
    <td class="ratecell">
      0.584
    </td>
    
    <td class="ratecell">
      0.686
    </td>
    
    <td class="ratecell">
      0.818
    </td>
    
    <td class="ratecell">
      1.00
    </td>
    
    <td class="ratecell">
      1.27
    </td>
    
    <td class="ratecell">
      1.54
    </td>
    
    <td class="ratecell">
      1.75
    </td>
    
    <td class="ratecell">
      2.04
    </td>
    
    <td class="ratecell">
      2.30
    </td>
    
    <td class="ratecell">
      2.53
    </td>
  </tr>
</table>

<figure id="attachment_885" style="width: 1527px" class="wp-caption alignnone"><img class="alignnone size-full wp-image-885" src="{{ "/assets/uploads/2016/03/rate_osx_carmit.png" | relative_url }}" alt="Carmit rate distribution" width="1527" height="816" srcset="{{ "/assets/uploads/2016/03/rate_osx_carmit.png" | relative_url }} 1527w, {{ "/assets/uploads/2016/03/rate_osx_carmit-300x160.png" | relative_url }} 300w, {{ "/assets/uploads/2016/03/rate_osx_carmit-768x410.png" | relative_url }} 768w, {{ "/assets/uploads/2016/03/rate_osx_carmit-1024x547.png" | relative_url }} 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /><figcaption class="wp-caption-text">Carmit rate distribution</figcaption></figure>  
It could even be worse. OSX has a voice named &#8220;Bad News&#8221;. Apparently, there is only one rate in which to deliver bad news:

<table class="table table-condensed">
  <tr>
    <th>
      Voice
    </th>
    
    <th class="ratecell">
      1/2.5
    </th>
    
    <th class="ratecell">
      1/2.25
    </th>
    
    <th class="ratecell">
      1/2
    </th>
    
    <th class="ratecell">
      1/1.75
    </th>
    
    <th class="ratecell">
      1/1.5
    </th>
    
    <th class="ratecell">
      1/1.25
    </th>
    
    <th class="ratecell">
      1
    </th>
    
    <th class="ratecell">
      1.25
    </th>
    
    <th class="ratecell">
      1.5
    </th>
    
    <th class="ratecell">
      1.75
    </th>
    
    <th class="ratecell">
      2
    </th>
    
    <th class="ratecell">
      2.25
    </th>
    
    <th class="ratecell">
      2.5
    </th>
  </tr>
  
  <tr class="result">
    <td>
      Bad News
    </td>
    
    <td class="ratecell">
      0.882
    </td>
    
    <td class="ratecell">
      0.899
    </td>
    
    <td class="ratecell">
      0.917
    </td>
    
    <td class="ratecell">
      0.937
    </td>
    
    <td class="ratecell">
      0.956
    </td>
    
    <td class="ratecell">
      0.978
    </td>
    
    <td class="ratecell">
      1.00
    </td>
    
    <td class="ratecell">
      1.02
    </td>
    
    <td class="ratecell">
      1.03
    </td>
    
    <td class="ratecell">
      1.04
    </td>
    
    <td class="ratecell">
      1.05
    </td>
    
    <td class="ratecell">
      1.05
    </td>
    
    <td class="ratecell">
      1.06
    </td>
  </tr>
</table>

<figure id="attachment_893" style="width: 1527px" class="wp-caption alignnone"><img class="alignnone size-full wp-image-893" src="{{ "/assets/uploads/2016/03/rate_osx_bad_news.png" | relative_url }}" alt="Bad News rate distribution" width="1527" height="816" srcset="{{ "/assets/uploads/2016/03/rate_osx_bad_news.png" | relative_url }} 1527w, {{ "/assets/uploads/2016/03/rate_osx_bad_news-300x160.png" | relative_url }} 300w, {{ "/assets/uploads/2016/03/rate_osx_bad_news-768x410.png" | relative_url }} 768w, {{ "/assets/uploads/2016/03/rate_osx_bad_news-1024x547.png" | relative_url }} 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /><figcaption class="wp-caption-text">Bad News rate distribution</figcaption></figure>  
With a few exceptions, speech rate on OSX is pretty good. Their API and documentation is straightforward enough that we nailed this on the first shot.

### Speech Rates in Windows

As mentioned in the previous post, speech rate in SAPI is defined as an integer from -10 to 10. In our initial implementation, we naively assumed that we can take the Web Speech API rate multiplier, and convert it to an SAPI rate by using the 10th root of the value and multiplying it by ten. In effect, projecting the maximal distribution of SAPI speech rates across the allowed Web Speech API values: 0.1 would become -10, 10 would be 10.  
With my fancy new benchmark tool, we could get a good picture of where that leads us with the standard David voice:

<table class="table table-condensed">
  <tr>
    <th>
      Voice
    </th>
    
    <th class="ratecell">
      1/2.5
    </th>
    
    <th class="ratecell">
      1/2.25
    </th>
    
    <th class="ratecell">
      1/2
    </th>
    
    <th class="ratecell">
      1/1.75
    </th>
    
    <th class="ratecell">
      1/1.5
    </th>
    
    <th class="ratecell">
      1/1.25
    </th>
    
    <th class="ratecell">
      1
    </th>
    
    <th class="ratecell">
      1.25
    </th>
    
    <th class="ratecell">
      1.5
    </th>
    
    <th class="ratecell">
      1.75
    </th>
    
    <th class="ratecell">
      2
    </th>
    
    <th class="ratecell">
      2.25
    </th>
    
    <th class="ratecell">
      2.5
    </th>
  </tr>
  
  <tr class="result">
    <td>
      MS David
    </td>
    
    <td class="ratecell">
      0.712
    </td>
    
    <td class="ratecell">
      0.713
    </td>
    
    <td class="ratecell">
      0.712
    </td>
    
    <td class="ratecell">
      0.799
    </td>
    
    <td class="ratecell">
      0.892
    </td>
    
    <td class="ratecell">
      0.976
    </td>
    
    <td class="ratecell">
      1.00
    </td>
    
    <td class="ratecell">
      0.977
    </td>
    
    <td class="ratecell">
      1.13
    </td>
    
    <td class="ratecell">
      1.25
    </td>
    
    <td class="ratecell">
      1.41
    </td>
    
    <td class="ratecell">
      1.40
    </td>
    
    <td class="ratecell">
      1.40
    </td>
  </tr>
</table>

That&#8217;s not too good. For example, if you provide a rate of 2.0, you would expect double the normal rate, but you only get 1.41x. Here is a graph:  
<figure id="attachment_921" style="width: 1527px" class="wp-caption alignnone"><img class="alignnone size-full wp-image-921" src="{{ "/assets/uploads/2016/03/rate_windows_broken.png" | relative_url }}" alt="Broken rate distribution on Windows" width="1527" height="816" srcset="{{ "/assets/uploads/2016/03/rate_windows_broken.png" | relative_url }} 1527w, {{ "/assets/uploads/2016/03/rate_windows_broken-300x160.png" | relative_url }} 300w, {{ "/assets/uploads/2016/03/rate_windows_broken-768x410.png" | relative_url }} 768w, {{ "/assets/uploads/2016/03/rate_windows_broken-1024x547.png" | relative_url }} 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /><figcaption class="wp-caption-text">Broken rate distribution on Windows</figcaption></figure>  
I also mentioned in the previous post, that after digging in MSDN, I found a page that explains what the expected speech engine characteristics are. In essence, 10 in SAPI means three times the normal speed, and -10 is one third. That is something to work with! [I fixed the math we do for the rate conversion](https://bugzilla.mozilla.org/show_bug.cgi?id=1256521), and once we correctly projected our multiplier values into what SAPI accepts we got much better benchmark results:

<table class="table table-condensed">
  <tr>
    <th>
      Voice
    </th>
    
    <th class="ratecell">
      1/2.5
    </th>
    
    <th class="ratecell">
      1/2.25
    </th>
    
    <th class="ratecell">
      1/2
    </th>
    
    <th class="ratecell">
      1/1.75
    </th>
    
    <th class="ratecell">
      1/1.5
    </th>
    
    <th class="ratecell">
      1/1.25
    </th>
    
    <th class="ratecell">
      1
    </th>
    
    <th class="ratecell">
      1.25
    </th>
    
    <th class="ratecell">
      1.5
    </th>
    
    <th class="ratecell">
      1.75
    </th>
    
    <th class="ratecell">
      2
    </th>
    
    <th class="ratecell">
      2.25
    </th>
    
    <th class="ratecell">
      2.5
    </th>
  </tr>
  
  <tr class="result">
    <td>
      MS David
    </td>
    
    <td class="ratecell">
      0.413
    </td>
    
    <td class="ratecell">
      0.454
    </td>
    
    <td class="ratecell">
      0.509
    </td>
    
    <td class="ratecell">
      0.568
    </td>
    
    <td class="ratecell">
      0.713
    </td>
    
    <td class="ratecell">
      0.799
    </td>
    
    <td class="ratecell">
      1.00
    </td>
    
    <td class="ratecell">
      1.25
    </td>
    
    <td class="ratecell">
      1.40
    </td>
    
    <td class="ratecell">
      1.76
    </td>
    
    <td class="ratecell">
      1.97
    </td>
    
    <td class="ratecell">
      2.19
    </td>
    
    <td class="ratecell">
      2.41
    </td>
  </tr>
</table><figure id="attachment_934" style="width: 1527px" class="wp-caption alignnone">

<img class="alignnone size-full wp-image-934" src="{{ "/assets/uploads/2016/03/rate_windows_fixed.png" | relative_url }}" alt="Fixed Windows rate distribution" width="1527" height="816" srcset="{{ "/assets/uploads/2016/03/rate_windows_fixed.png" | relative_url }} 1527w, {{ "/assets/uploads/2016/03/rate_windows_fixed-300x160.png" | relative_url }} 300w, {{ "/assets/uploads/2016/03/rate_windows_fixed-768x410.png" | relative_url }} 768w, {{ "/assets/uploads/2016/03/rate_windows_fixed-1024x547.png" | relative_url }} 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /> <figcaption class="wp-caption-text">Fixed Windows rate distribution</figcaption></figure> 

### Speech Rates in Linux

In Linux, we originally had the same naive conversion that we had in Windows, with the only diff being that in Speech Dispatcher the rate is an integer from -100 to 100. The results were just as bad:

<table class="table table-condensed">
  <tr>
    <th>
      Voice
    </th>
    
    <th class="ratecell">
      1/2.5
    </th>
    
    <th class="ratecell">
      1/2.25
    </th>
    
    <th class="ratecell">
      1/2
    </th>
    
    <th class="ratecell">
      1/1.75
    </th>
    
    <th class="ratecell">
      1/1.5
    </th>
    
    <th class="ratecell">
      1/1.25
    </th>
    
    <th class="ratecell">
      1
    </th>
    
    <th class="ratecell">
      1.25
    </th>
    
    <th class="ratecell">
      1.5
    </th>
    
    <th class="ratecell">
      1.75
    </th>
    
    <th class="ratecell">
      2
    </th>
    
    <th class="ratecell">
      2.25
    </th>
    
    <th class="ratecell">
      2.5
    </th>
  </tr>
  
  <tr class="result">
    <td>
      default
    </td>
    
    <td class="ratecell">
      0.659
    </td>
    
    <td class="ratecell">
      0.684
    </td>
    
    <td class="ratecell">
      0.712
    </td>
    
    <td class="ratecell">
      0.757
    </td>
    
    <td class="ratecell">
      0.804
    </td>
    
    <td class="ratecell">
      0.887
    </td>
    
    <td class="ratecell">
      1.00
    </td>
    
    <td class="ratecell">
      1.01
    </td>
    
    <td class="ratecell">
      1.07
    </td>
    
    <td class="ratecell">
      1.07
    </td>
    
    <td class="ratecell">
      1.14
    </td>
    
    <td class="ratecell">
      1.15
    </td>
    
    <td class="ratecell">
      1.20
    </td>
  </tr>
</table>

<figure id="attachment_942" style="width: 1527px" class="wp-caption alignnone"><img class="alignnone size-full wp-image-942" src="{{ "/assets/uploads/2016/03/rate_linux_broken.png" | relative_url }}" alt="Broken rate distribution on Linux" width="1527" height="816" srcset="{{ "/assets/uploads/2016/03/rate_linux_broken.png" | relative_url }} 1527w, {{ "/assets/uploads/2016/03/rate_linux_broken-300x160.png" | relative_url }} 300w, {{ "/assets/uploads/2016/03/rate_linux_broken-768x410.png" | relative_url }} 768w, {{ "/assets/uploads/2016/03/rate_linux_broken-1024x547.png" | relative_url }} 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /><figcaption class="wp-caption-text">Broken rate distribution on Linux</figcaption></figure>  
Speech Dispatcher has limited documentation. But luckily, it is open source, so we just need to read the code, right? I guess. Theoretically. But in this case, it just made me go down a rabbit hole. Speech Dispatcher supports a few engines, but in reality most distributions make it hard to use anything that isn&#8217;t eSpeak. I looked at the eSpeak speechd configuration file, and it had some interesting numbers. The &#8220;normal&#8221; rate is 170 eSpeak words per minute. The max is 390, and the min is 80. In a proportional sense that would be a min rate of 0.47, and a max of 2.3.  
Adjusting the math in our Speech Dispatcher adapter to those theoretical values made things much better, but not perfect. Reading the code of speechd, and its eSpeak output module didn&#8217;t reveal anything else. Instead of relying on bad documentation and fallible &#8220;source code&#8221;, I decided to just go with the numbers I was seeing in the benchmark. Speech Dispatcher rates max out at 2.5x and won&#8217;t go below 1/2x. I put those numbers into our conversion formula, and.. [it worked well](https://bugzilla.mozilla.org/show_bug.cgi?id=1254738)!

<table class="table table-condensed">
  <tr>
    <th>
      Voice
    </th>
    
    <th class="ratecell">
      1/2.5
    </th>
    
    <th class="ratecell">
      1/2.25
    </th>
    
    <th class="ratecell">
      1/2
    </th>
    
    <th class="ratecell">
      1/1.75
    </th>
    
    <th class="ratecell">
      1/1.5
    </th>
    
    <th class="ratecell">
      1/1.25
    </th>
    
    <th class="ratecell">
      1
    </th>
    
    <th class="ratecell">
      1.25
    </th>
    
    <th class="ratecell">
      1.5
    </th>
    
    <th class="ratecell">
      1.75
    </th>
    
    <th class="ratecell">
      2
    </th>
    
    <th class="ratecell">
      2.25
    </th>
    
    <th class="ratecell">
      2.5
    </th>
  </tr>
  
  <tr class="result">
    <td>
      default
    </td>
    
    <td class="ratecell">
      0.488
    </td>
    
    <td class="ratecell">
      0.487
    </td>
    
    <td class="ratecell">
      0.487
    </td>
    
    <td class="ratecell">
      0.567
    </td>
    
    <td class="ratecell">
      0.678
    </td>
    
    <td class="ratecell">
      0.812
    </td>
    
    <td class="ratecell">
      1.00
    </td>
    
    <td class="ratecell">
      1.29
    </td>
    
    <td class="ratecell">
      1.47
    </td>
    
    <td class="ratecell">
      1.76
    </td>
    
    <td class="ratecell">
      1.96
    </td>
    
    <td class="ratecell">
      2.14
    </td>
    
    <td class="ratecell">
      2.39
    </td>
  </tr>
</table><figure id="attachment_955" style="width: 1527px" class="wp-caption alignnone">

<img class="alignnone size-full wp-image-955" src="{{ "/assets/uploads/2016/03/rate_linux_fixed.png" | relative_url }}" alt="Fixed rate distribution on Linux" width="1527" height="816" srcset="{{ "/assets/uploads/2016/03/rate_linux_fixed.png" | relative_url }} 1527w, {{ "/assets/uploads/2016/03/rate_linux_fixed-300x160.png" | relative_url }} 300w, {{ "/assets/uploads/2016/03/rate_linux_fixed-768x410.png" | relative_url }} 768w, {{ "/assets/uploads/2016/03/rate_linux_fixed-1024x547.png" | relative_url }} 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /> <figcaption class="wp-caption-text">Fixed rate distribution on Linux</figcaption></figure> 

### Conclusion

What&#8217;s the lesson to be learned? Not sure. Sometimes the docs are good, other times less so, and sometimes not at all? Benchmarks and real-world results are important?  
The one certain thing I know now is that graphs are cool. This is what the rate distribution was before I fixed these issues, check it out:  
<figure id="attachment_965" style="width: 1527px" class="wp-caption alignnone"><img class="alignnone size-full wp-image-965" src="{{ "/assets/uploads/2016/03/rate_all_broken.png" | relative_url }}" alt="Rate distribution on all three platforms before fix" width="1527" height="816" srcset="{{ "/assets/uploads/2016/03/rate_all_broken.png" | relative_url }} 1527w, {{ "/assets/uploads/2016/03/rate_all_broken-300x160.png" | relative_url }} 300w, {{ "/assets/uploads/2016/03/rate_all_broken-768x410.png" | relative_url }} 768w, {{ "/assets/uploads/2016/03/rate_all_broken-1024x547.png" | relative_url }} 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /><figcaption class="wp-caption-text">Rate distribution on all three platforms before fix</figcaption></figure>  
And look how clean and nice it is now:  
<figure id="attachment_968" style="width: 1527px" class="wp-caption alignnone"><img class="alignnone size-full wp-image-968" src="{{ "/assets/uploads/2016/03/rate_all_fixed.png" | relative_url }}" alt="Fixed rate distribution on all three platforms" width="1527" height="816" srcset="{{ "/assets/uploads/2016/03/rate_all_fixed.png" | relative_url }} 1527w, {{ "/assets/uploads/2016/03/rate_all_fixed-300x160.png" | relative_url }} 300w, {{ "/assets/uploads/2016/03/rate_all_fixed-768x410.png" | relative_url }} 768w, {{ "/assets/uploads/2016/03/rate_all_fixed-1024x547.png" | relative_url }} 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /><figcaption class="wp-caption-text">Fixed rate distribution on all three platforms</figcaption></figure>  
&nbsp;  
&nbsp;  
&nbsp;