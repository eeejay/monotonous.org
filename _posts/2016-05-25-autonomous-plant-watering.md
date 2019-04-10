---
id: 974
title: Autonomous Plant Watering
date: 2016-05-25T18:30:30+00:00
author: Eitan
layout: post
guid: http://blog.monotonous.org/?p=974
permalink: /2016/05/25/autonomous-plant-watering/
publicize_twitter_user:
  - eeejay
categories:
  - Personal
  - Software
  - Technology
  - Uncategorized
---
Here in our house we keep our plants on the threshold of death. They are in constant limbo as we remember to water them every few months. It is really quite disgraceful.  
<figure id="attachment_987" style="width: 4592px" class="wp-caption alignnone"><img class="alignnone size-full wp-image-987" src="{{ "/assets/uploads/2016/05/p1070571.jpg" | relative_url }}" alt="A pathetic house plant" width="4592" height="3448" srcset="{{ "/assets/uploads/2016/05/p1070571.jpg" | relative_url }} 4592w, {{ "/assets/uploads/2016/05/p1070571-300x225.jpg" | relative_url }} 300w, {{ "/assets/uploads/2016/05/p1070571-768x577.jpg" | relative_url }} 768w, {{ "/assets/uploads/2016/05/p1070571-1024x769.jpg" | relative_url }} 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /><figcaption class="wp-caption-text">Our sad sad plant.</figcaption></figure>  
One day I looked at our plants and thought we needed to do something. Go and water them? The plant doesn&#8217;t just need water. It is suffering from the systemic problem of us never remembering to water it. No. Watering the plant would be too easy, we need a technological solution that will hydrate the plant **and** not require us to change our comfortable habit of neglect.  
I googled &#8220;automated house plant watering&#8221; and the first link that comes up is an [instructable](http://www.instructables.com/id/Cheap-and-Easy-Automatic-House-Plant-Watering-Syst/). It promised to be a cheap and easy project. So I went ahead and got all the materials: an aquarium air pump, some tubing and valves. I then followed the instructions and assembled the parts as they describe. The result was underwhelming. I got some gurgling at the plant end of the tube, not a steady or measurable flow. I really don&#8217;t understand the physics that makes that system work, but it has a lot to do with water pressure: the deeper your reservoir the more efficient the water gets pumped. As the water gets consumed, the pump gives less output. So to get an optimal plant-watering we would need to make sure the tank is always full. Whats the point of automating it if you have to fill the tank after every watering?? This won&#8217;t do. I plan to put this on a timer. I need to know that if I have it on for 1 minute I will always pump a comparable amount of water to the plant.  
So I got to thinking, how can an air pump pump water? Specifically, how can it pump water with a constant pressure? I came up with this schematic:  
<figure id="attachment_1027" style="width: 4078px" class="wp-caption alignnone"><img class="alignnone size-full wp-image-1027" src="{{ "/assets/uploads/2016/05/p10705881.jpg" | relative_url }}" alt="Brilliant schematic" width="4078" height="3105" srcset="{{ "/assets/uploads/2016/05/p10705881.jpg" | relative_url }} 4078w, {{ "/assets/uploads/2016/05/p10705881-300x228.jpg" | relative_url }} 300w, {{ "/assets/uploads/2016/05/p10705881-768x585.jpg" | relative_url }} 768w, {{ "/assets/uploads/2016/05/p10705881-1024x780.jpg" | relative_url }} 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" /><figcaption class="wp-caption-text">Air is pumped into a sealed jar with an outlet tube that relieves the jar&#8217;s pressure by pushing water out through another tube!</figcaption></figure>  
I grabbed a mason jar and drilled two 3/16&#8243; holes in the lid. This allowed me to insert the two air tube which are slightly thicker (5mm). They fit snuggly and formed a seal.  
<img class="alignnone size-full wp-image-1087" src="{{ "/assets/uploads/2016/05/p1070577.jpg?w=9184" | relative_url }}" alt="Jar lid with two tubes running through" width="4592" height="3448" />  
Next I attached one of the tubes to the pump, and placed the second one&#8217;s end in a glass. Turned on the pump and! Yes! It works! Science! I was getting a steady flow of water. The jar was emptied in a constant rate. This setup will do. I&#8217;m so pleased with this!  
I splurged and got a slightly more expensive pump with 4 outputs so I can water 4  plants individually.  
<img class="alignnone size-full wp-image-1090" src="{{ "/assets/uploads/2016/05/p1070568.jpg" | relative_url }}" alt="Aquarium air pump with 4 outlets" width="4592" height="3448" srcset="{{ "/assets/uploads/2016/05/p1070568.jpg" | relative_url }} 4592w, {{ "/assets/uploads/2016/05/p1070568-300x225.jpg" | relative_url }} 300w, {{ "/assets/uploads/2016/05/p1070568-768x577.jpg" | relative_url }} 768w, {{ "/assets/uploads/2016/05/p1070568-1024x769.jpg" | relative_url }} 1024w" sizes="(max-width: 767px) 89vw, (max-width: 1000px) 54vw, (max-width: 1071px) 543px, 580px" />  
This setup has a few advantages over other pump setups:

  * It is cheap. So far the bill of parts is around $12.50.
  * It offers predictable water throughput.
  * You can connect any sealable container. Don&#8217;t want to refill the water after 32oz of watering? Get a gallon jug.
  * If the reservoir runs dry the motor won&#8217;t catch fire. That apparently is a thing water pumps.
  * Since the water is only going through a simple tube and not an expensive motor, you can pump a nutrient solution. If you want to pamper your plants, we don&#8217;t.

I made a stupid pump. Why is that cool? Because with a WiFi plug it becomes smart! It is now a Connected Device™. I plugged it into a Bayit WiFi socket, and set it to turn on for 20 seconds each Monday afternoon. That will feed our plants about a 1/2 a cup a week. If we like the results we may extend it to a full cup!  
<figure id="attachment_1098" style="width: 4592px" class="wp-caption alignnone"><img class="alignnone size-full wp-image-1098" src="{{ "/assets/uploads/2016/05/p1070590.jpg?w=9184" | relative_url }}" alt="Bayit WiFi Socket" width="4592" height="3448" /><figcaption class="wp-caption-text">The Internet is in control!</figcaption></figure>  
**A Word on WiFi Sockets**  
They suck. They take the simplest operation of closing a circuit and abstract it in a shitty smartphone app that only works half the time. Well, at least that has been my impression with this Bayit gadget. For my next project I am going to use a Kankun smart plug. Apparently it runs OpenWRT and is very hackable.

### Bill of Materials

<table border="0" cellspacing="0">
  <colgroup span="2" width="171"></colgroup> <tr>
    <td align="left" height="34">
      Air Pump
    </td>
    
    <td align="right">
      $6.99
    </td>
  </tr>
  
  <tr>
    <td align="left" height="34">
      Air tube
    </td>
    
    <td align="right">
      $3.42
    </td>
  </tr>
  
  <tr>
    <td align="left" height="34">
      Mason jar
    </td>
    
    <td align="right">
      $2.09
    </td>
  </tr>
  
  <tr>
    <td align="left" height="34">
      Wifi plug
    </td>
    
    <td align="right">
      $24.99
    </td>
  </tr>
</table>