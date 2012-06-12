Optimizing Web Content and UIWebViews
=========

**Image Decoding**

* Decoding images requires width * height * 4 bytes
* Avoid using images that are larger than needed
* Compact sprites with only the most used assets.  No sense in loading the % of unused images within the sprites.

**Javascript Loading**

* New web inspector for iOS to attach to an iOS device or the simulator
* Use web inspector timeline to profile loading
* Use "Instrument Navigator" to see the network request timeline of all resources loaded 
* ```async``` attribute to javascript file; executed as soon as page loads
* ```defer``` attribute executed in order of ```<script>``` tags, just before DOMContentLoaded
* Put your script tags @ the bottom of the doc, so that the full html doc can load before loading the javascript
* Don't **chain** resources, but rather list all the resources you need directly in the HTML so they can begin downloading immediately! (also true with CSS)

**Leverage the DOM**

* Only use the Javascript framework when its the right tool for the job; heavy on the load!
* Adding & removing classes
* Finding elements with a CSS selector ```querySelectorAll('.class')```
* ```DOMContentReady``` is the standard for when the DOM content has been loaded and is ready to work with

**Layout Calculation**

Keep in mind when trying to determine (say the height) of the current layout on the page, and then updating that layout, it has to re-calculate the total height of the page each time (say in a foor loop).  Try to determine all the heights in a loop, and then resize all of the desired heights in another loop.

* Avoid forcing unnecessary layout (clientHeight, Width, Top, let, right, bottom, etc.)
* Use web inspector timeline to profile layouts and rendering

Layers in WebKit Rendering
-----

