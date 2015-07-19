# *Programming in HTML5 with JavaScript & CSS3*
## Study Guide


This repository is a markdown version of notes for Programming in HTML5 with JavaScript and CSS3 (which is a Microsoft certification exam). It is completely platform-agnostic and focused on the use of newer HTML5/CSS3/Javascript features. This study guide was originally created by <a href="https://github.com/Mellbourn?tab=repositories">@Mellbourn</a>. I have merely taken the notes and converted them to Markdown for easier reading. You can visit the <a href="https://docs.google.com/document/d/1RmVrbbMBZ4-mg8P4BHRuXZrTtpKv5eOieA5UHXgWw5M/edit#">original Google Document here</a>. While this guide was originally written for exam prep, it can always be used to introduce some of the newer features of the web to developers.

## Objectives

1. Implement and Manipulate Document Structures and Objects
2. Implement Program Flow
3. Access and Secure Data
4. Use CSS3 in Applications

## 1. Implement and Manipulate Document Structures and Objects

### Create the document structure

This objective may include but is not limited to: structure the UI by using semantic markup, including for search engines and screen readers (Section, Article, Nav, Header, Footer, and Aside).

**Create a layout container in HTML**
The `#container` defines how wide the Web page contents will be, as well as any margins around the outside and padding on the inside

```css
#container {
 width: 870px;
 margin: 0 0 0 20px; /* top right bottom left */
 padding: 0;
}
 ```
 
**Search Engine Optimization (SEO)**
- Have a unique `<title>` for each page
- Add a description for search engines: `<meta name=”description” content=”Some website">`
- Your Urls should use words and use a single url for a page (`301` to the correct one)
- Easy to navigate (flat hierarchy, with breadcrumb)
- Have a Sitemap file (xml description of navigation)
- `rel=nofollow` on links in comments

**Semantic HTML5 Markup**
```html
<article></article>
<aside></aside>
<section></section>
<figure><figcaption>
<nav></nav
<fieldset><legend></legend></fieldset> <!-- (groupbox) -->
<label for=”inputfieldid”></label>
```
**Semantic markup: ARIA - Disability Compliance**

- Start here: https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA
- *Roles*: dialog, directory, grid, heading, main, menu, tree
- *States & Properties*: aria-autocomplete, aria-checked, aria-haspopup
- Landmark roles: `role=application`, banner, form, main, navigation, search
- Live regions: alert, log, marquee
- Mark regions with `aria-live=’polite’` // assertive
- Type of update: `relevant=”additions`”
- `aria-busy=true` during updates
- `alt=””` when purely decorative
- `aria-labelledby` & `aira-describedby`

### Write code that interacts with UI controls

This objective may include but is not limited to: programmatically add and modify HTML elements; implement media controls; implement HTML5 canvas and SVG graphics.

Vanilla Javascript DOM Manipultaiton methods
- `add` and `modify`
- `appendChild`
- `removeChild`

**Media controls**

```html
<video>
   <source src="video.mp4" type='video/mp4' />
   <source src="video.webm" type='video/webm' />
   <object type="application/x-silverlight-2">
       <param name="source" value="http://url/player.xap">
       <param name="initParams" value="m=http://url/video.mp4">
   </object>
   No native support, download the video <a href="video.mp4">here</a>.
</video>
```

Video tag attributes: 
- `autoplay` 
- `controls`
- `muted`
- `poster`
- `loop`
- Methods `play()` & `pause()`

**HTML5 canvas**
```javascript
<script type="text/javascript">
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.fillStyle="#FF0000";
ctx.fillRect(0,0,150,75);
ctx.moveTo(0,0);
ctx.lineTo(300,150);
ctx.stroke();
ctx.beginPath();
ctx.arc(95,50,40,0,2*Math.PI);
ctx.stroke();
var grd=ctx.createLinearGradient(0,0,200,0);
grd.addColorStop(0,"red")
</script>
```
**SVG**

```html
<svg xmlns="http://www.w3.org/2000/svg" version="1.1">
   <circle cx="100" cy="50" r="40" stroke="black" stroke-width="2" fill="red" />

  <g fill="none">
    <path stroke="red" d="M5 20 l215 0" />

  <defs>
    <filter id="f1" x="0" y="0">
      <feGaussianBlur in="SourceGraphic" stdDeviation="15" />
    </filter>
  </defs>
  <rect width="90" height="90" stroke="green" stroke-width="3" fill="yellow" filter="url(#f1)" />
</svg>
```

### Apply styling to HTML elements programmatically**

This objective may include but is not limited to: change the location of an element; apply a transform; show and hide elements.

**css position
static, absolute, fixed, relative // fixed is relative browser window, absolute relative parent
location
document.getElementById("movetext").style.left = 100px;
apply a transform
    -webkit-transform: rotate(30deg);
translate(), scale(), skew(), matrix()
show and hide
display: block; display: none; (and take up no space) display: inline-block; display: list-item;
visibility: visible; visibility: hidden; (but still take up space)
Implement HTML5 APIs.
This objective may include but is not limited to: implement storage APIs, AppCache API, and Geolocation API
storage
typeof(Storage)!=="undefined"
localStorage.foo = “bar” permanent!
sessionStorage for the session
AppCache - cached until manifest changes!
<html manifest=”demo.appcache”>
CACHE MANIFEST
# 2012-02-21 v1.0.0
/theme.css
/logo.gif
/main.js

NETWORK:
login.asp

FALLBACK:
/html/ /offline.html
var appCache = window.applicationCache;

switch (appCache.status) {
  case appCache.UNCACHED: // UNCACHED == 0
    return 'UNCACHED';
    break;
  case appCache.IDLE: // IDLE == 1
    return 'IDLE';
    break;
  case appCache.CHECKING: // CHECKING == 2
    return 'CHECKING';
    break;
  case appCache.DOWNLOADING: // DOWNLOADING == 3
    return 'DOWNLOADING';
    break;
  case appCache.UPDATEREADY:  // UPDATEREADY == 4
    return 'UPDATEREADY';
appCache.swapCache(); // swaps 
appCache.update():  // update cache but does not reload window 
Geolocation
navigator.geolocation.getCurrentPosition(showPosition);
function showPosition(position)
  {
  x.innerHTML="Latitude: " + position.coords.latitude + 
setInterval(), clearInterval(), setTimeout() and clearTimeout
$(window).load(function(){   // executes after images have been loaded too
Establish the scope of objects and variables.
This objective may include but is not limited to: define the lifetime of variables; keep objects out of the global namespace; use the “this” keyword to reference an object that fired an event; scope variables locally and globally
delete to undefine variables (but not globals defined without var)
Create and implement objects and methods.
This objective may include but is not limited to: implement native objects; create custom objects and custom properties for native objects using prototypes and functions; inherit from an object; implement native methods and create custom methods
http://phrogz.net/JS/classes/OOPinJS.html
http://phrogz.net/JS/classes/OOPinJS2.html
Cat.prototype = new Mammal();
SuperCar.prototype = Object.create(Car.prototype);
object literal
personObj={firstname:"John",lastname:"Doe"};
shorthand for
personObj=new Object();
personObj.firstname="John";
personObj.lastname="Doe";
using a constructor:
function person(firstname,lastname,age,eyecolor)
{
  this.firstname=firstname;
  this.lastname=lastname;
  this.changeName=changeName;
  function changeName(name)
  {
    this.lastname=name;
  }
