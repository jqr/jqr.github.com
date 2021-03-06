---
layout: post
title: Automatically Generated Maps with Microformats
summary: Javascript-free google maps integration
javascript:
  - https://maps.google.com/maps/api/js?sensor=false
  - http://ideafoundry.info/javascripts/sumo/microformat.js
  - http://ideafoundry.info/javascripts/sumo/hcard.js
  - http://ideafoundry.info/javascripts/simple-maps/map.js
---

<p>
  Got a few addresses and want to show them on a map without writing any javascript?
  It turns out, there's an incredibly easy way: mark up your addresses as
  <a href="http://microformats.org/wiki/hcard">hCards</a> and use the
  <a href="https://github.com/collectiveidea/simple-maps">simple-maps</a> javascript library.
</p>

<h3>Microformats to the Rescue!</h3>
<p>
  Microformats are a simple way to attach meaning to standard HTML tags by
  using classes. Here is an example I made with the
  <a href="http://microformats.org/code/hcard/creator">hCard Creator</a>.
</p>

```html
<div id="hcard-starbucks" class="vcard">
  <a class="url fn" href="http://starbucks.com">Starbucks</a>
  <div class="adr">
    <span class="street-address">854 Broad Ripple Ave</span><br/>
    <span class="locality">Indianapolis</span>,
    <span class="region">IN</span>,
    <span class="postal-code">46220</span>
    <span class="country-name">USA</span>
  </div>
</div>
```

<p>
  Rendered as HTML using default styling, this looks like:
</p>

<p>
  <div id="hcard-starbucks" class="vcard">
    <a class="url fn" href="https://starbucks.com">Starbucks</a>
    <div class="adr">
      <span class="street-address">854 Broad Ripple Ave</span><br/>
      <span class="locality">Indianapolis</span>,
      <span class="region">IN</span>,
      <span class="postal-code">46220</span>
      <span class="country-name">USA</span>
    </div>
  </div>
</p>

<p>
  Pretty simple, it usually means adding some classes to data that's
  already on the page. We can style this however we like, including
  completely hiding elements with <code>display: none</code> for things
  that may be obvious (country name?).
</p>

<p>
  To display the map we just use an element with id="map"
</p>


```html
<div id="map" style="width: 100%; height: 400px"></div>
```

<div id="map" style="width: 100%; height: 400px">Map would be here if you had javascript enabled.</div>

<p>
  There are two pins because it also picks up my hCard from the site layout.
</p>

<h3>Automatic Geocoding</h3>
<p>
  You may have noticed I didn't specify longitude or latitude anywhere
  in the hCard. simple-maps detects and computes geocodes when they're not given.
</p>
