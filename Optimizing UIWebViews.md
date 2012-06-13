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

*Does your page flicker?  Does your app run out of memory showing web content?  Blindly adding a 3D transform style?*

**HTML Rendering 101**

What is it? ***Taking textual HTML/CSS and converting it to painting and drawing commands to produce an image that we can display on screen.***

WebKit creates a ```RenderTree``` from the initial DOM Tree to enhance rendering and painting of elements on the page.  You can ask each individual piece of the page to render themselves (styles, positions, etc).  Don't want to paint the entire page all the time.  What if you are running a video?  WebKit cuts out a portion of the screen and hands it to the video renderer, so the page is not responsible for "refreshing" or updating the page/video.

**Compositing** is flattening layered assets into one, to enhance performance of page loading.

*Why are layers created?* 

* Always one tiled layer for main page
* Painting intensive elements (```video```, ```canvas```)
* 3D Transofmrations (```translate3d```, ```rotate3d```, ```translateZ```)
* Content enhancements (filters, masks, reflections, opacity, transitions, animations)
* Special cases (```position:fixed```, touch scrolling)
* Any content that overlaps an existing layer

**Tools**

* Web inspector
* Instruments
* WebKit debug tools
    * ```WebKitShowDebugBorders``` can be set in ```NSUserDefaults``` to see the borders around particular layers
    * ```WebKitDeveloperExtras``` ?
    


Rendering in Your App
-----

Asynchronous rendering, incremental rendering in WebKit

Create a rendering thread to free the main thread and allow user touch events/not block the application.

**Incremental Rendering**

* Loading *chunks* of the page, to show the user portions of the application as content is being loaded
* ```supressesIncrementalRendering```

**The Smart App Banner**

When user visits website, a new banner slides in with icon, link to app store, rating, cost, etc.  If the app is already installed on users device, the ```view``` button turns into an ```open``` button to jump the user to the app, potentially passing along info to the app.

*How?  Just add a **meta tag.***

```<meta name="apple-itunes-app" content-app-id=123, app-argument=x-sfp:///visit/real-rock />```