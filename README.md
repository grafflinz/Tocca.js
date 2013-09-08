Tocca.js (Beta 0.0.2)
========

Super lightweight script ( ~1kB ) to detect via Javascript events like 'tap' 'dbltap' 'swipeup'  'swipedown'  'swipeleft'  'swiperight' on any kind of device.

<a href="http://gianlucaguarini.github.io/Tocca.js/demo.html" target="_blank">Demo</a>

## Usage

Include the script into your page:
<pre lang="html">
&lt;script src="path/to/Tocca.js"&gt;&lt;/script&gt;
</pre>

Once you have included Tocca.js you will be able to catch all the new events:

<pre lang="javascript">
elm.addeventListener('tap',function(e){});
elm.addeventListener('dbltap',function(e){});
elm.addeventListener('swipeleft',function(e){});
elm.addeventListener('swiperight',function(e){});
elm.addeventListener('swipeup',function(e){});
elm.addeventListener('swipedown',function(e){});
</pre>

It works with jQuery as well:
<pre lang="javascript">
$(elm).on('tap',function(e,data){});
$(elm).on('dbltap',function(e,data){});
$(elm).on('swipeleft',function(e,data){});
$(elm).on('swiperight',function(e,data){});
$(elm).on('swipeup',function(e,data){});
$(elm).on('swipedown',function(e,data){});
</pre>

## API and Examples

Anytime you will use a Tocca.js event the callback function will receive a special event object containing the following properties

 - <code>x</code> { Int }: latest x position of pointer at the end of the event
 - <code>y</code> { Int }: latest y position of pointer at the end of the event
 - <code>originalEvent</code> { Object }: the original javascript native event that has been triggered
 - <code>distance</code>: this property is available only for the swipe events
 	- <code>x</code> { Int }: the x absolute difference between the beginning and the end of the swipe gesture 
 	- <code>y</code> { Int }: the y absolute difference between the beginning and the end of the swipe gesture

Examples:

<pre lang="javascript">
elm.addEventListener('dpltap',function (e){
	console.log(e.x);
	console.log(e.y);
});
elm.addEventListener('swipeup',function (e){
	console.log(e.x);
	console.log(e.y);
	console.log(e.distance.x);
	console.log(e.distance.y);
});

// with jQuery

$(elm).on('dpltap',function (e,data){
	console.log(data.x);
	console.log(data.y);
});
$(elm).on('swipeup',function (e,data){
	console.log(data.x);
	console.log(data.y);
	console.log(data.distance.x);
	console.log(data.distance.y);
});
</pre>


Anyway you can combine Tocca.js with the default javascript touch events:

	- <code>touchmove</code>
	- <code>touchstart</code>
	- <code>touchend</code>
	- <code>touchcancel</code>

To disable the default touch behaviours (zoom on double tap, scroll on swipe...) on a certain element via javascript you can always use the following snippet:

<pre lang="javascript">
elm.addEventListener('touchmove',function(e){e.preventDefault()});
elm.addEventListener('touchstart',function(e){e.preventDefault()});
elm.addEventListener('touchend',function(e){e.preventDefault()});
</pre>


## Configuration

Whenever you want to configure the plugin events settings you can do that simply specifying two constants before including Tocca.js into the page

<pre lang="html">
&lt;script&gt;
var SWIPE_TRESHOLD = 80, // default value
	TAP_TRESHOLD = 200; // default value
&lt;/script&gt;
&lt;script src="path/to/Tocca.js"&gt;&lt;/script&gt;
</pre>

## Browser Support

Actually the script has been tested on all the modern browsers but it need a better testing phase over several platforms: Chrome 29+ Firefox 23+ Opera 12+ Safari 5+

It works on mobile/tablet browsers and on desktop browsers as well.

On the old browsers all the Tocca.js events cannot be triggered.

## Changelog

### 0.0.2
	Android Bug fix

## What does Tocca mean?!

'Tocca' is the second person singular of the imperative Italian verb 'Toccare' that means to touch.
