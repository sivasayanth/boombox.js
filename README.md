Boombox.js Overview
===================

HTML5 introduces the <code>*lt;audio&gt;</code> element which offers a way to play audio natively
in the browser. However the native controls are a little lacking in style.
Thankfully HTML5 also brings a full api to interact with which allows us to skin
an Audio object however we want.

Goals
-----

The primary goal of this project is to create a high quality HTML5 audio boombox
that can be easily skinned and extended.

Get a modern browser
--------------------

First things first—make sure you’re running a modern browser. My favorite is
[Chrome](http://www.google.com/chrome) but [Safari](http://www.apple.com/safari/download/), [Opera](http://www.opera.com/mobile/download/versions/), [Firefox](http://www.mozilla.com/en-US/firefox/new/), or even [IE9](http://windows.microsoft.com/en-US/internet-explorer/downloads/ie-9/worldwide-languages) will also do. 

Including jQuery & boombox.js
-----------------------------

Next grab the latest copy of jQuery and boombox.js and include a link to both of
them in your HTML <code>&lt;head&gt;</code> section.

<code><pre>
&lt;head&gt;
     &lt;script src="js/jquery.js" type="text/javascript"&gt;&lt;/script&gt;
     &lt;script src="js/boombox.js" type="text/javascript"&gt;&lt;/script&gt;
&lt;/head&gt;
</pre></code>

Include the buttons
-------------------

You’ll need buttons in order to control the boombox. Add these buttons that are
nested within a <code>&lt;div id="boombox"&lt;</code>.

<code><pre>
&lt;div id="boombox"&gt; 
      &lt;div&gt;&lt;span id="counter"&gt;1&lt;/span&gt; &lt;span id="trackName"&gt;&lt;/span&gt;&lt;/div&gt; 
      &lt;button id="playbutton" class="slick-black boombox"&gt;Play&lt;/button&gt; 
      &lt;button id="pausebutton" class="slick-black boombox"&gt;Pause&lt;/button&gt; 
      &lt;button id="prev" class="slick-black boombox"&gt;Previous&lt;/button&gt; 
      &lt;button id="next" class="slick-black boombox"&gt;Next&lt;/button&gt; 
      &lt;button id="volumedownbutton" class="slick-black boombox"&gt;Volume Down&lt;/button&gt; 
      &lt;button id="volumeupbutton" class="slick-black boombox"&gt;Volume Up&lt;/button&gt; 
&lt;/div&gt;&lt;
</pre></code>

Create a boombox
----------------

Use jQuery to grab <code>&lt;div id="boombox"&gt;</code> and call the boombox method on it. Pass in
  an object literal of songs to play. The keys should be the title you would
  like to appear on the screen and the value should be a path to the audiofiles.

&lt;script&gt; 
  $(document).ready(function() {
    $("#boombox").boombox({
      'All is Illusion' : '../music/allisillusion',  
      'Grace' : '../music/grace'  
    });
  });
&lt;/script&gt; 

You’ll notice above that the song paths don’t have a file extension. That is
because boombox detects what codec the browser supports and serves up the
correct file. As a developer you need to encode your audiofiles once as .mp3 and
once as .ogg and put the path to those files in the object literal that is
passed into the boombox function.

Remember to not use the file extensions because those will be added by boombox()
to work on a per browser basis. 

Mime Type
---------

To get Firefox to recognize the .ogg file type correctly you will need to add
this one line to the .htaccess file on the server that is serving up the
audiofiles.

<code><pre>
  AddType audio/ogg .ogg
</pre></code>
