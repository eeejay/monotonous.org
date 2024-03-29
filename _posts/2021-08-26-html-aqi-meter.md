---
title: 'HTML AQI Gauge'
author: Eitan
layout: post
permalink: /2021/08/26/html-aqi-meter/
geo_public:
  - "0"
publicize_twitter_user:
  - eeejay
categories:
  - Software
  - Technology
---

I needed a meter to tell me what the air quality is like outside. Now I know!

If you need one as well, or if you are looking for an accessible gauge for anything else, here you go.

You can also <a href="https://codepen.io/eeejay/pen/GREJWga">mess with it on Codepen</a>.

<script>
  function setDial(aqi) {
    let angle = getAQIDialAngle(aqi);
    let [bg, white] = getAQIColor(aqi);

    let meter = document.querySelector(".gauge > div[role=meter]");
    let dial = meter.querySelector(".dial");
    meter.setAttribute("aria-valuenow", aqi);
    meter.setAttribute("aria-valuetext", aqi);
    dial.querySelector(".aqi-num").textContent = aqi;
    dial.querySelector(".arrow").style.transform = `rotate(${angle - 90}deg)`;
    dial.style.backgroundColor = bg;
    dial.classList.toggle("white", white);
  }


function getAQIDialAngle(aqi) {
  if (aqi >= 301) {
    return Math.min((aqi - 301) / 200 * 30 + 150, 180);
  } else if (aqi >= 201) {
    return (aqi - 201) / 100 * 30 + 120;
  } else if (aqi >= 151) {
    return (aqi - 151) / 50 * 30 + 90;
  } else if (aqi >= 101) {
    return (aqi - 101) / 50 * 30 + 60;
  } else if (aqi >= 51) {
    return (aqi - 51) / 50 * 30 + 30;
  } else if (aqi >= 0) {
    return aqi / 50 * 30;
  } else {
    return 0;
  }
}

function getAQIColor(aqi) {
  function combineColors(c1, c2, bias) {
    return c1.map((c, i) => ((c * (1 - bias)) + (c2[i] * bias)));
  }

  function stringifyColor(c) {
    return `rgb(${c})`;
  }

  function calculateColors(c1, c2, bias) {
    let bg = combineColors(c1, c2, bias);
    let white = ((bg[0] * 299) + (bg[1] * 587) + (bg[2] * 114)) / 1000 < 128;
    return [stringifyColor(bg), white];
  }

  const aqiColorMap = [
    [0, [0, 255, 0]],
    [50, [255, 255, 0]],
    [100, [255, 126, 0]],
    [150, [255, 0, 0]],
    [200, [143, 63, 151]],
    [300, [126, 0, 35]]
  ];

  for (let i in aqiColorMap) {
    let [target, color] = aqiColorMap[i];
    if (target > aqi) {
      if (i == 0) {
        return calculateColors(color, color, 1);
      }

      let [prevTarget, prevColor] = aqiColorMap[i - 1];
      return calculateColors(prevColor, color, (aqi - prevTarget) / (target - prevTarget));
    }
  }

  let [, color] = aqiColorMap[aqiColorMap.length - 1];
  return calculateColors(color, color, 1);
}
</script>
<style>
  .gauge {
    display: inline-block;
  }

  .gauge > div[role=meter] {
    border-radius: 8rem 8rem 0 0;
    border: 1px solid black;
    width: 16rem;
    height: 8rem;
    background-color: black;
    position: relative;
    overflow: hidden;
    background: conic-gradient(from 0deg at 50% 100%,
                                red 30deg, #8f3f97 30deg 60deg,
                                #7e0023 60deg 91deg, transparent 91deg 269deg,
                                #00e400 269deg 300deg, #ffff00 300deg 330deg,
                                #ff7e00 330deg 360deg);
  }

  .gauge > label {
    font-size: 14px;
    text-align: center;
    background-color: black;
    padding: .2rem 0;
    display: block;
  }

  .dial {
    background-color: #00ff00;
    transition: background-color 1s, color .25s;
    border-radius: 10rem 10rem 0 0;
    width: 70%;
    height: 70%;
    display: flex;
    flex-direction: column;
    align-content: center;
    justify-content: center;
    position: absolute;
    bottom: 0;
    left: 15%;
    z-index: 2;
    overflow: hidden;
    box-shadow: 0px 0px 0px 1rem #000;
    border-bottom: none;
    box-sizing: border-box;
    color: #000;
  }

  .dial.white {
    color: #fff;
  }

  .dial > span {
    text-align: center;
    font-family: sans-serif;
  }

  .dial > .arrow {
    position: absolute;
    left: calc(50% - .25rem);
    bottom: 0;
    width: .5rem;
    height: calc(100% + 1px);
    background-color: transparent;
    transform-origin: bottom center;
    transform: rotate(-90deg);
    transition: transform 1s;
  }

  .dial > .arrow:after {
    content: "";
    border-left: .5rem solid transparent;
    border-right: .5rem solid transparent;
    border-top: .5rem solid #000;
    position: absolute;
    left: calc(50% - .5rem);
    top: 0;
    width: 0;
    height: 0;
    transition: border-color .25s;
  }

  .dial.white > .arrow:after {
    border-top-color: #fff;
  }

  .aqi-num {
    font-weight: bold;
    font-size: 120%;
    margin-top: 1.25rem;
  }

  @media (forced-colors: active) {
  .dial {
    border: 2px solid black;
    border-bottom: none;
  }
  
  .gauge > div[role=meter] {
    border-width: 2px;
    border-bottom: none;
  }
  
  .gauge > label {
    border: 2px solid black;
  }
}

</style>

<div>
  <label for="set-aqi">Set AQI:</label><input type="range" id="set-aqi" min="0" max="500" value="10">
</div>
<div class="gauge">
  <div role="meter" aria-valuemin="0" aria-valuemax="500" aria-labelledby="meter-label">
    <div class="dial"><span class="aqi-num"></span><span>AQI</span><div class="arrow"></div></div>
  </div>
  <label class="label" id="meter-label">10 Minute Average US EPA PM2.5 AQI</label>
</div>

<script>
  let range = document.getElementById("set-aqi");
  setDial(range.value);

  range.addEventListener("change", evt => {
    setDial(evt.target.value);
  });
</script>
