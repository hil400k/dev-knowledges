# Let's go...

> Please, select the allowed pragma directives (http-equip attributes on a meta-element).

content-language, refresh, set-cookie

> Which of the following video formats is NOT supported by the video tag?

Mov - not supported; Supported: mp4, ogg, WebM

> Which attribute triggers an abort event?

abort

> What was the previous version of HTML, prior to HTML5?

HTML 4.01

> Which of the following methods returns a geolocation object in HTML5?

navigator.geolocation

> Which method is used to finish a launched worker?

terminate

> Which of the following attributes triggers an event when an element gets user input?

oninput

> The ImageData object represents the underlying pixel data of an area of a canvas object
including which of the following read-only attributes?

data, height, width

> Which of the following HTML elements is used to create vector graphics?

svg

> What is the main difference between HTML and XHTML?

A syntax error in XHTML stops the rendering of the document, whereas a syntax error in HTML would be ignored and the document fully rendered.

> Which method is used to check if the browser can play specified audio/video type?

canPlayType

> Which of the following is NOT a valid attribute for the audio element in HTML5?

stopped

> Select all the valid attributes of an audio element.

autoplay, controls, src

> Which of the following methods can be used to estimate page load times?

Using the Navigation Timing JavaScript API.

> Which of the following are the valid values of the <a> element’s target attribute in HTML5?

_blank, _self, _parent, _top

> Assuming that some text needs to be written on an HTML5 canvas, select a replacement for the commented line below:
```js <canvas id=»e» width=»200″ height=»200″></canvas>
<script>
var canvas = document.getElementById(«e»);
//insert code here
context.fillStyle = «blue»;
context.font = «bold 16px Arial»;
context.fillText(«Zibri», 100, 100);
</script>
```
var context = canvas.getContext(«2d»);

> What is the role of the <dfn> element in HTML5?

It is used to define a definition term.

> Which of the following is a possible way to get fullscreen video played from the browser using HTML5?
```html
<video height=»100%» width=»100%»>
```
> Which method of HTMLCanvasElement is used to represent image of Canvas Element?

toDataURL()

> Which of the following will detect when an HTML5 video has finished playing?

```js var video = document.getElementsByTagName(‘video’)[0]; video.onended = function(e) { } ```

> Which method of the HTMLCanvasElement is used to represent an image of a canvas element?

toDataURL

> Which of the following will restrict an input element to accept only numerical values in a text field?

``` <input type=»number» /> ```

> Which of the following is the correct way to display a PDF file in the browser?

``` <object type=»application/pdf» data=»filename.pdf» width=»100%» height=»100%»/> ```

> Which of the following is the best method to detect HTML5 Canvas support in web browsers?

!!window.HTMLCanvasElement

> Which media event is triggered when there is an error in fetching media data in HTML5?

onstalled

> Which of the following is the correct way to check browser support for WebSocket?

```js console.log(window[‘WebSocket’] ? ‘supported’ : ‘not supported’); ```

> Which of the following is not a valid attribute for the <video> element in HTML5?

disabled (correct: autoplay, controls, height, loop, muted, poster, preload, src, width)

> Which of the following are sample use cases for HTML5 web workers?

Polling URLs in background, Syntax highlighting without blocking code editing capabilities in online IDEs


