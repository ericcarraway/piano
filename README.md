piano
=====

Creates an SVG piano keyboard for inclusion in a web-page,
where key widths are accurately in position.

See http://www.mathpages.com/home/kmath043.htm for the math.

This keyboard has following properties (x = octave width):
1. All white keys have equal width in front (W = x/7).
2. All black keys have equal width (B = x/12).
3. The narrow part of white keys C, D and E is W - B*2/3
4. The narrow part of white keys F, G, A, and B is W - B*3/4

usage
=====

1. Create a container element for the piano in your HTML.

<div id="piano-container"></div>


2. Call the function that creates the piano.

var firstNote = 60;
var lastNote = 84;
var pianoContainer = document.getElementById('piano-container');
piano.drawSVGpiano(firstNote, lastNote, pianoContainer, callback); //callback is optional


3. The optional "callback" argument is a function that will be
called when an event happens on any piano key. This function can
be defined like this:

var callback = function(event) {
  var note = event.target.note; //the note on whick the event happened can be accessed like this
  var element = event.target; //the element that called the event can be accessed like this
  alert('You clicked on note: ' + note); //do something
}


4. If you need a diferent event than "click" (e.g. a mouseover),
define it like this:

callback.eventType = 'mouseover'; //ommiting this, assumes the calling event is a click.

