title: Advanced Theming with HTML5
output: index.html
theme: theme
controls: false
logo: theme/logo.png

--

# Advanced Theming with HTML5

## And some JavaScript

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

# HTML 5 `<video>`

<video id="video" style="margin: 0 auto; display: block;"></video>

--

# The codes

Initialize the camera on a `<video id="video"></video>` element:

```javascript
var video = document.getElementById('video');

var connect = function (stream) {
  video.src = window.URL ? window.URL.createObjectURL(stream) : stream;
  video.play();
};
var error = function (e) { alert(e.message); };

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
ctx.drawImage(video, 0, 0, canvas.width, canvas.height);

var base64Image = canvas.toDataURL();
```
