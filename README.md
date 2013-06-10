# Dragster
HTML5 `dragenter` and `dragleave` events [are crap](http://www.quirksmode.org/blog/archives/2009/09/the_html5_drag.html). Detecting drag hover events on dropzone elements with children is a PITA that involves placeholder overlay elements, doing stuff every 350ms on `dragover`, or [this](http://stackoverflow.com/a/10906204/91934).

Dragster gives you sane new `dragster:enter` and `dragster:leave` events that behave just like `mouseenter` and `mouseleave`. 

## Setup

Include Dragster in your app.

```html
<script src="/lib/dragster.js"></script>
```

Make Dragster do its thing on the elements you would like to emit saner events.

```javascript
var dropzone = document.getElementById( "my-dropzone" )
new Dragster( dropzone );
```

Add some event listeners without pulling your hair out.

```javascript
document.addEventListener( "dragster:enter", function (e) {
  e.target.classList.add( "dragged-over" )
}, false );

document.addEventListener( "dragster:leave", function (e) {
  e.target.classList.remove( "dragged-over" )
}, false );
```

Call the `removeListeners` method to teardown a Dragster instance.

```javascript
dragster = new Dragster( dropzone );
// Dragster events are emitted.
dragster.removeListeners();
// Dragster events no longer emitted.
```

## Todo
- Cross browser testing. So far only tested in Chrome.
- Make it a Bower component.

## License
Dragster is released under the [MIT License](http://ben.mit-license.org/)
