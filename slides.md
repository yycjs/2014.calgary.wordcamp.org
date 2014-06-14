title: Advanced Theming with HTML5
output: index.html
theme: theme
controls: false
logo: theme/logo.png

--

# Advanced Theming with HTML5

## And some JavaScript

#### [yycjs.com/2014.calgary.wordcamp.org](http://yycjs.com/2014.calgary.wordcamp.org)

-- presenter

![David Luecke](http://gravatar.com/avatar/a14850281f19396480bdba4aab2d52ef?s=200)

## David Luecke

* [<i class="fa fa-github"></i> daffl](https://github.com/daffl)
* [<i class="fa fa-twitter"></i> @daffl](http://twitter.com/daffl)

--

# What's HTML 5 anyway

Much like HTML 4 but with new elements, for example:

<img src="img/html5.png" style="float: right; width: 300px; margin-right: 100px;" alt="HTML5 logo" />

- `<footer>`, `<header>`, `<nav>`
- `<main>`, `<article>`, `<section>`
- `<input type="number|search|email|url|...">`
- `<audio>`, `<video>`
- `<canvas>`, `<progress>`
- And [lots more](https://developer.mozilla.org/en/docs/Web/Guide/HTML/HTML5/HTML5_element_list)

--

# Like...

`<input type="date">`

<input type="date" style="font-size: 1.5em; margin: 40px 0;">

`<progress>`

<progress max="100" value="20" style="zoom: 2; margin-top: 30px;"></progress>

--

# And JavaScript APIs

<img src="img/js.png" style="float: right; width: 300px; margin-right: 100px;" alt="JS unofficial logo" />

* Drawing on `<canvas>`
* Drag & Drop
* Offline web applications
* Geolocation
* File upload
* Web audio and video

--

# And custom elements

HTML 5 allows to register your own custom tags. This will become especially interesting
in combination with [Web Components](http://webcomponents.org/):

```javascript
<sript type="text/javascript" src="//daffl.github.io/slider/slider.js"></script>

<davids-slider auto-rotate="true" time="2000">
  <img src="image1.png" alt="Sets up">
  <img src="image2.png" alt="an image">
  <img src="image3.png" alt="slider">
</davids-slider>
```

-- hide-logo

# HTML 5 `<video>`

<video id="video" style="margin: 0 auto; display: block; height: 70%;"></video>

--

# The codes

Initialize the camera on a `<video id="video"></video>` element:

```javascript
var video = document.getElementById('video-snapshot');

function connect(stream) {
  video.src = window.URL ? window.URL.createObjectURL(stream) : stream;
  video.play();
};
function error(e) { alert(e.message); };

navigator.getMedia = (navigator.getUserMedia ||
  navigator.webkitGetUserMedia ||
  navigator.mozGetUserMedia ||
  navigator.msGetUserMedia);
navigator.getMedia({ video: true }, connect, error);
```

--

# Taking a snapshot

Gets a Base64 encoded image of the current `<video>` element picture:

```javascript
var canvas = document.createElement('canvas');
var context = canvas.getContext('2d');

canvas.width = video.videoWidth;
canvas.height = video.videoHeight;
context.drawImage(video, 0, 0, canvas.width, canvas.height);

var base64Image = canvas.toDataURL();
```
