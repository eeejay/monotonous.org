---
id: 1152
title: I Built A Smart Clock
date: 2016-09-12T09:00:52+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=1152
permalink: /2016/09/12/i-built-a-smart-clock/
geo_public:
  - "0"
publicize_twitter_user:
  - eeejay
categories:
  - Personal
  - Software
  - Technology
---
Problem Statement:
:   In today&#8217;s fast-paced world, while juggling work and personal life, sometimes we need to know what time it is.

Solution:
:   A chronometer you can hang on the wall.

Wake up people. Clocks are the future. Embrace progress.  
Hello, my name is Eitan. I am a clock maker.  
Over the past year I have spent nights and weekends designing gear trains, circuit boards, soldering and writing software. The result is a clock. Not just any clock, it is a smart clock that could tell you what time it is **on demand**. It is internet-connected so you can remotely monitor what time it is in your home.  
It is powered by three stepper motors, 3 hall effect sensors, and a miniature computer. It also ticks.  
<figure id="attachment_1155" style="width: 300px" class="wp-caption aligncenter"><img class="wp-image-1155 size-medium" src="{{ "/assets/uploads/2016/09/p1070936jpg_29262204520_o.jpg?w=300" | relative_url }}" alt="Final clock. Translucent body showing all components including gears and Raspberry Pi." width="300" height="225" srcset="{{ "/assets/uploads/2016/09/p1070936jpg_29262204520_o.jpg" | relative_url }} 4592w, {{ "/assets/uploads/2016/09/p1070936jpg_29262204520_o-300x225.jpg" | relative_url }} 300w, {{ "/assets/uploads/2016/09/p1070936jpg_29262204520_o-768x577.jpg" | relative_url }} 768w, {{ "/assets/uploads/2016/09/p1070936jpg_29262204520_o-1024x769.jpg" | relative_url }} 1024w" sizes="(max-width: 300px) 100vw, 300px" /><figcaption class="wp-caption-text">The future of time telling.</figcaption></figure>  
Why? Because in my hubris I thought it would be an easy weekend project, and then things got out of hand.  
<img class="aligncenter" src="https://media.giphy.com/media/ukH2KaVFiwwSI/giphy.gif" alt="An early attempt at flight. The propeller falls off." width="300" height="224" /> 

## Gears

My first gear boxes were pretty elaborate, with different gear ratios for each motor/hand. I probably spent the most time in the design/print cycle trying to come up with a reliable solution that would transfer the torque from 3 separate motors to a single axis. I ended up with something much simpler, a 2:1 gear ratio for all hands.

<div style="clear:both;">
  <figure id="attachment_1156" style="width: 300px" class="wp-caption alignleft"><img class="size-medium wp-image-1156" src="{{ "/assets/uploads/2016/09/p1060972.jpg?w=300" | relative_url }}" alt="An example of an early super elaborate and huge gearbox." width="300" height="225" srcset="{{ "/assets/uploads/2016/09/p1060972.jpg" | relative_url }} 4592w, {{ "/assets/uploads/2016/09/p1060972-300x225.jpg" | relative_url }} 300w, {{ "/assets/uploads/2016/09/p1060972-768x577.jpg" | relative_url }} 768w, {{ "/assets/uploads/2016/09/p1060972-1024x769.jpg" | relative_url }} 1024w" sizes="(max-width: 300px) 100vw, 300px" /><figcaption class="wp-caption-text">An example of an early super elaborate and huge gear box.</figcaption></figure><br /> <figure id="attachment_1157" style="width: 300px" class="wp-caption alignright"><img class="size-medium wp-image-1157" src="{{ "/assets/uploads/2016/09/p1070903jpg_29379879016_o.jpg?w=300" | relative_url }}" alt="My final design." width="300" height="225" srcset="{{ "/assets/uploads/2016/09/p1070903jpg_29379879016_o.jpg" | relative_url }} 4592w, {{ "/assets/uploads/2016/09/p1070903jpg_29379879016_o-300x225.jpg" | relative_url }} 300w, {{ "/assets/uploads/2016/09/p1070903jpg_29379879016_o-768x577.jpg" | relative_url }} 768w, {{ "/assets/uploads/2016/09/p1070903jpg_29379879016_o-1024x769.jpg" | relative_url }} 1024w" sizes="(max-width: 300px) 100vw, 300px" /><figcaption class="wp-caption-text">My final design.</figcaption></figure>
</div>

## Limit Switches

Another challenge I struggled with was how would the software know where each hand is at any given time? A stepper motor is nice because it has some predictability. Each one of its steps is equal, so if you know that a step size is 6 degrees, it will take 60 steps to complete a rotation. In our case, this isn&#8217;t good enough, because:

  1. The motor is not 100% guaranteed to complete each step. If there is too much resistance on it, it will fail. I struggled to design a perfect gear box that won&#8217;t ever make things hard for the motors, but there will be a bad tooth every once in a while that will jam the motor for a step or two.
  2. The motor I chose for this project is the 28BYJ-48, mainly because it is cheap and you can get a pack of 5 from amazon with drivers for only $12. Its big drawback is that there is no consensus on what the precise step size is. Internally the motor has 32 steps per revolution (11.25 degrees per step). But it has a set of reduction gears embedded in it that make the steps per revolution something like 2037.886. Not a nice number and, more importantly, not good for clocks that risk drifting out of precision.
  3. When the clock is first turned on, it has no way to know the initial position of each hand.

I decided to solve all this with limit switches. If the clock hands somehow closed a circuit at the top of each rotation, we would at least know where &#8220;12 o&#8217;clock&#8221; is and we will have something to work with. I thought about using buttons, metal contacts and the likes. But I didn&#8217;t like the idea of introducing more wear on a delicate mechanical system: how many times will the second hand brush past a contact before screwing it up?  
So, I went with latching hall effect sensors. The basic concept is magnets. The sensor will open or close a circuit depending on what pole of a magnet is nearby. I glued tiny magnets at opposite ends of the gears, and by checking the state of the a sensor circuit after every motor step you can tell if we just got to 6 o&#8217;clock or 12 o&#8217;clock.  
<figure id="attachment_1158" style="width: 300px" class="wp-caption aligncenter"><img class="size-medium wp-image-1158" src="{{ "/assets/uploads/2016/09/p1070908jpg_29334676491_o.jpg?w=300" | relative_url }}" alt="Two magnets on opposite sides of the gear, and the hall effect sensor is clamped just above the gear to detect them." width="300" height="225" srcset="{{ "/assets/uploads/2016/09/p1070908jpg_29334676491_o.jpg" | relative_url }} 4592w, {{ "/assets/uploads/2016/09/p1070908jpg_29334676491_o-300x225.jpg" | relative_url }} 300w, {{ "/assets/uploads/2016/09/p1070908jpg_29334676491_o-768x577.jpg" | relative_url }} 768w, {{ "/assets/uploads/2016/09/p1070908jpg_29334676491_o-1024x769.jpg" | relative_url }} 1024w" sizes="(max-width: 300px) 100vw, 300px" /><figcaption class="wp-caption-text">Two magnets on opposite sides of the gear, and the hall effect sensor clamped just above the gear to detect polarity changes.</figcaption></figure>

## Circuits

Electricity is magic to me, I really don&#8217;t understand it. I learned just enough to get this project going. I started by reading Adafruit tutorials and breadboarding. After assembling a forest of wires, I finally got a &#8220;working&#8221; clock. I wanted the final clock to be more elegant than this:  
<img class="aligncenter size-medium wp-image-1160" src="{{ "/assets/uploads/2016/09/img_20160701_212504_28030141675_o.jpg?w=300" | relative_url }}" alt="Breadboard, raspberry pi, motor drivers and gearbox all taped to a peice of cardboard." width="300" height="225" srcset="{{ "/assets/uploads/2016/09/img_20160701_212504_28030141675_o.jpg" | relative_url }} 5248w, {{ "/assets/uploads/2016/09/img_20160701_212504_28030141675_o-300x225.jpg" | relative_url }} 300w, {{ "/assets/uploads/2016/09/img_20160701_212504_28030141675_o-768x576.jpg" | relative_url }} 768w, {{ "/assets/uploads/2016/09/img_20160701_212504_28030141675_o-1024x768.jpg" | relative_url }} 1024w" sizes="(max-width: 300px) 100vw, 300px" />  
With some graph paper, I sketched out how I can arrange all of the circuits on a perf board and went to work soldering, after inhaling a lot of toxic fumes and leaving some of my skin on the iron I got this:  
<img class="aligncenter size-medium wp-image-1161" src="{{ "/assets/uploads/2016/09/img_20160708_234832_27572238683_o.jpg?w=225" | relative_url }}" alt="BOttom of perfboard showing a lot of bare wires and soldering." width="225" height="300" srcset="{{ "/assets/uploads/2016/09/img_20160708_234832_27572238683_o.jpg" | relative_url }} 3936w, {{ "/assets/uploads/2016/09/img_20160708_234832_27572238683_o-225x300.jpg" | relative_url }} 225w, {{ "/assets/uploads/2016/09/img_20160708_234832_27572238683_o-768x1024.jpg" | relative_url }} 768w" sizes="(max-width: 225px) 100vw, 225px" />  
I was happy with the result, but it could be prettier. Plus, I would never put myself through that again. I wanted to make this process as easy as possible. So I decided to splurge a bit, I redesigned the board using Fritzing:  
<img class="aligncenter wp-image-1162 size-medium" src="{{ "/assets/uploads/2016/09/screenshot-from-2016-09-09-13-03-34.png?w=300" | relative_url }}" alt="Screenshot of Fritzing design app." width="300" height="169" srcset="{{ "/assets/uploads/2016/09/screenshot-from-2016-09-09-13-03-34.png" | relative_url }} 3200w, {{ "/assets/uploads/2016/09/screenshot-from-2016-09-09-13-03-34-300x169.png" | relative_url }} 300w, {{ "/assets/uploads/2016/09/screenshot-from-2016-09-09-13-03-34-768x432.png" | relative_url }} 768w, {{ "/assets/uploads/2016/09/screenshot-from-2016-09-09-13-03-34-1024x576.png" | relative_url }} 1024w" sizes="(max-width: 300px) 100vw, 300px" />  
&#8230;and ordered PCB prints from their online service. After a month or so I got these in the mail:  
<figure id="attachment_1163" style="width: 300px" class="wp-caption aligncenter"><img class="size-medium wp-image-1163" src="{{ "/assets/uploads/2016/09/p1070880jpg_28792531333_o.jpg?w=300" | relative_url }}" alt="Custom PCBs printed in Berlin!" width="300" height="225" srcset="{{ "/assets/uploads/2016/09/p1070880jpg_28792531333_o.jpg" | relative_url }} 4592w, {{ "/assets/uploads/2016/09/p1070880jpg_28792531333_o-300x225.jpg" | relative_url }} 300w, {{ "/assets/uploads/2016/09/p1070880jpg_28792531333_o-768x577.jpg" | relative_url }} 768w, {{ "/assets/uploads/2016/09/p1070880jpg_28792531333_o-1024x769.jpg" | relative_url }} 1024w" sizes="(max-width: 300px) 100vw, 300px" /><figcaption class="wp-caption-text">Custom PCBs printed in Berlin!</figcaption></figure>  
Soldering on components was a breeze&#8230;  
<figure id="attachment_1164" style="width: 300px" class="wp-caption aligncenter"><img class="size-medium wp-image-1164" src="{{ "/assets/uploads/2016/09/p1070887jpg_29305709512_o.jpg?w=300" | relative_url }}" alt="PCB with jumper headers and resistors." width="300" height="225" srcset="{{ "/assets/uploads/2016/09/p1070887jpg_29305709512_o.jpg" | relative_url }} 4592w, {{ "/assets/uploads/2016/09/p1070887jpg_29305709512_o-300x225.jpg" | relative_url }} 300w, {{ "/assets/uploads/2016/09/p1070887jpg_29305709512_o-768x577.jpg" | relative_url }} 768w, {{ "/assets/uploads/2016/09/p1070887jpg_29305709512_o-1024x769.jpg" | relative_url }} 1024w" sizes="(max-width: 300px) 100vw, 300px" /><figcaption class="wp-caption-text">PCB with jumper headers and resistors.</figcaption></figure>

## Software

Software is my comfort zone, you don&#8217;t get burnt, electrocuted, or spend a whole day 3D printing just to find out your design is shit. My plan was to compensate for all the hardware imperfection in software. Have it be self-tuning, smart and terrific.  
I chose to have NodeJS drive the clock. Mostly because I have recently got comfortable with it, but also because it is easy to give this project a slick web interface.  
<img class="aligncenter size-medium wp-image-1165" src="{{ "/assets/uploads/2016/09/screenshot_2016-09-09-12-45-38.png?w=169" | relative_url }}" alt="The web interface, with a form to set the time on the clock." width="169" height="300" srcset="{{ "/assets/uploads/2016/09/screenshot_2016-09-09-12-45-38.png" | relative_url }} 720w, {{ "/assets/uploads/2016/09/screenshot_2016-09-09-12-45-38-169x300.png" | relative_url }} 169w, {{ "/assets/uploads/2016/09/screenshot_2016-09-09-12-45-38-576x1024.png" | relative_url }} 576w" sizes="(max-width: 169px) 100vw, 169px" />  
Doing actual GPIO calls to move the motors didn&#8217;t work well in JS. Python wasn&#8217;t cutting it either. I needed to move 3 motors simultaneously at intervals below 20 milliseconds. The CPU halts to a stop. So I ended writing a small C program that actually does all the GPIO bits. You start it with an RPM as an argument, and it will do the rest. It doesn&#8217;t make sense to spawn a new process on each clock tick, so instead I have the JS code send a signal to the process each second.  
With the help of the Network Time Protocol and some fancy high school algebra I was able to make the clock precise to the second. Just choose a timezone, and it will do the rest. It should even switch back and fourth from daylight savings time (haven&#8217;t actually tested that, waiting for DST to naturally end).

## Mounting

I went to TAP Plastics, my go-to retailer for all things plastic. I bought a 12&#8243; diameter 3/8&#8243; thick acrylic disc. Drilled some holes, and got to mounting this whole caboodle. This project is starting to take shape! With the help of a few colorful wires for extra flourish:  
<figure id="attachment_1169" style="width: 300px" class="wp-caption aligncenter"><img class="size-medium wp-image-1169" src="{{ "/assets/uploads/2016/09/p1070911jpg_29379977416_o.jpg?w=300" | relative_url }}" alt="Call the components mounted on the acrylic disc." width="300" height="225" srcset="{{ "/assets/uploads/2016/09/p1070911jpg_29379977416_o.jpg" | relative_url }} 4592w, {{ "/assets/uploads/2016/09/p1070911jpg_29379977416_o-300x225.jpg" | relative_url }} 300w, {{ "/assets/uploads/2016/09/p1070911jpg_29379977416_o-768x577.jpg" | relative_url }} 768w, {{ "/assets/uploads/2016/09/p1070911jpg_29379977416_o-1024x769.jpg" | relative_url }} 1024w" sizes="(max-width: 300px) 100vw, 300px" /><figcaption class="wp-caption-text">All the components mounted on the acrylic disc.</figcaption></figure>

## In Conclusion

The slick marketing from Apple and Samsung will have you believe that your life isn&#8217;t complete without their latest smart watch. They are wrong.  
Your life isn&#8217;t complete because you haven&#8217;t built your own smart clock. Prime your soldering iron and [get to work](https://github.com/eeejay/clockers)!