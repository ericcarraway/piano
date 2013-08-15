piano
=====

Creates an SVG piano keyboard for inclusion in a web-page,
where key widths are accurately in position.

This keyboard has following properties:
- Octave width = 161 pixels = x.
- All white keys have equal width in front (W = x/7).
- All black keys have equal width (B = x/12).
- The narrow part of white keys C, D and E is W - B*2/3
- The narrow part of white keys F, G, A, and B is W - B*3/4

See [this page](http://www.mathpages.com/home/kmath043.htm) for the math.

usage
-----

1.  Create a container element for the piano in your HTML.

        <div id="piano-container"></div>


2.  Call the function that creates the piano.

        var firstNote = 60; //60 is the  4th octave C (the so-called 'middle C').
        var lastNote = 84;
        var pianoContainer = document.getElementById('piano-container');
        piano.drawSVGpiano(firstNote, lastNote, pianoContainer);

3.  The optional "callback" argument is a function that will be
    called when an event happens on any piano key. This function can
    be defined like this:

        var callback = function(event) {
          var note = event.target.note; //the note on whick the event happened can be accessed like this
          var element = event.target; //the element that called the event can be accessed like this
          alert('You clicked on note: ' + note); //do something
        }
        piano.drawSVGpiano(firstNote, lastNote, pianoContainer,callback);

4.  If you need a diferent event than "click" (e.g. a mouseover),
    define it like this:

        callback.eventType = 'mouseover'; //ommiting this, assumes the calling event is a click.

5.  If you want the piano smaller or bigger you can scale by setting a fifth argument.
    Example:

        piano.drawSVGpiano( 60,
                            72,
                            document.getElementById('piano-container'),
                            function(e){alert('You clicked on note: ' + e.target.note)},
                            1.5
        );
