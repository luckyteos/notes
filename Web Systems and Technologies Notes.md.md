---
title: Web Systems and Technologies Notes
created: '2020-02-01T01:06:57.950Z'
modified: '2020-02-01T02:57:35.853Z'
---

# Web Systems and Technologies

## Internet

### History

Started with ARPAnet [1960s] which was created at the height of the cold war

### Design Goals

* Survivable

* Simple

* Scalable

* Selectable - Able to find resource that you want (URIs etc)

### Benefits
* Accessibility
* De-Centralized
* Cheap
* Services Available

<br>

## WWW

Created by **Tim Berners Lee** in **1989**

Not the same thing as the internet

<br>

## Web Browser History

Mosaic -> Netscape Navigator -> Internet Explorer -> Mozilla Firefox -> Chrome

#### Mosaic (NCSA Uni of Illinois) [1993]

* Supported various protocols (FTP, NNTP) in addition to HTTP
* Supported the display of text and images on the same page

#### Netscape Navigator 1.0 (Released 15 Dec 1994)

* Displayed data while the data was still being loaded by the browser
* Had all the functionality of Mosaic that people liked

<hr>

### 1st Browser War (1995 - 2002)
Between Netscape and Internet Explorer

<hr>

#### Key Events

Release of Internet Explorer 1.0

Release of Netscape Navigator 3.0 - comes with Javascript

Release of Internet Explorer 3.0 - comes with CSS

Release of Internet Explorer 4.0 - comes bundled with windows

Netscape gets acquired by AOL

Development of Netscape ceases

<br>

## HTML

### HTML5

#### Goals

* Improve the native web [Make rich interactive web pages with plugins]

* Do more with less code [Some client side validation built in]

  ```html
  <input type = "password" minlength="8" required>
  ```

* Realize the semantic web [Machine understanding what each part of website means]

#### Semantic Tags

> Makes a page more understandable by the browser and accessible to users

```html
<header></header>
<nav></nav>
<main></main>
<figure></figure>
<figcaption></figcaption>
<footer></footer>
```

#### Declaration

`!DOCTYPE html`

<br>

## CSS

### Basic Syntax
```css
selector {
	property: value
}
```

### Box Model

![Box Model](https://i.imgur.com/yMFSm9n.png)

### How styles are placed matters

```html
<style>
    h2 {
        color: red;
    }
</style>
<link rel = "stylesheet" href= "css/style.css">
```

```css
h2 {
    color: blue;
}
```
###### What will the color of H2 be?

------

**blue** 

------

This is as the order in which the inline style and the external stylesheet are defined matters. In this case, style.css is placed after the style tag, and as they contain different styling for the same h2 element, style.css, defined last takes precedence

<br>

## Bootstrap
### Different ways to implement bootstrap code

| Method | Pros                                                         | Cons                                                         |
| ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| CDN    | **Faster loading** due to caching. <br /> Easy to select **desired** versions. <br />Up to date with latest **bug fixes**. <br /> **Saves** local space and bandwidth. | Requires more **vigilance** due to **security risks**, e.g. hackers taking over the CDN and injecting malicious script.<br /> Must always be **connected** to the internet (no off-line development). <br /> IDEs such as NetBeans may not be able to provide **syntax checking** on non-local files. |
| Local  | Can be read and parsed at build time by IDEs, allowing **syntax highlighting and hints**. <br />Can be used **offline**<br />**Easily viewed** by developers for educational or debugging purposes <br />Eliminates **external dependencies** (website will still work even if CDN goes down) | **Additional overhead** to download and maintain files locally<br />Takes up **disk space** on server<br />**Load times** can be **slower**, especially as web traffic scales up |

<br>

## JavaScript

>  Language created to respond to user events

>  Created by Brendan Eich at Netscape Communications in 1995 during the "1st Browser Wars"

>Has nothing to do with Java. The Java name is from a partnership between Sun microsystems and Netscape

### Basic Syntax

```js
var n = 12;
var s = "Hello World";
var o = true;
```

### On Efficient Loading of JS

[Javascript-async-defer](https://flaviocopes.com/javascript-async-defer/)

### Note on Cross-Origin

```html
<script src = "https://odirony.com/hello.php" crossorigin="anonymous"></script>
```

This will result in User Credentials not being sent, unless the request comes from the same origin as the web server

### Document Object Model

> Standard object model and programming interface for html

> Standard to get, change, add or delete HTML elements

![DOM](https://www.w3schools.com/js/pic_htmltree.gif)

Document Object: Represents the web page

#### Event Handling

##### Using Event Listeners

```js
var big_img = document.getElementById("big1");
big_img.addEventListener("click", myfunction);
```

* Event Listeners can be added to any DOM object, including the window
* Separates JavaScript from HTML Markup
* Multiple Event Listeners can be added to a single element

###### Event Bubbling

```js
document.getElementById("myP").addEventListener("click", myFunction, true);
document.getElementById("myDiv").addEventListener("click", myFunction, true);
```

The myDiv element's click event will be handled before the myP click event

###### Event Capturing

```js
document.getElementById("myP").addEventListener("click", myFunction, false);
document.getElementById("myDiv").addEventListener("click", myFunction, false);
```

The myP element's click event will be handled before the myDiv click event

### JSON

```js
var fruits = {"Pears": 1, "Apples", ["China apples", "NZ Apples"]};
var fruitsJSON = JSON.stringify(fruits);
var fruits2 = JSON.parse(fruitsJSON);
```



<br>

## WCAG (Web Content Accessibility Guidelines) 2.1

### Perceivable
> Perceive: to notice something or someone by using sight, sound, touch, taste, or smell

> Information and user interface components must be presented such that all users can take notice of them


* Provide **text alternatives** to non-text content
* Provide **captions and other alternatives** for multimedia
* Create content that can be presented in **different ways** without losing meaning
* Make it **easier** for users to see and hear content

### Operable
> User interface components and navigation must be operable


* Make all functionality available from a **keyboard**
*  Give users **enough time** to read and use content
* **Avoid content** that causes seizures or physical reactions
* Help users **navigate and find** content
* Make it easier to use **inputs** other than keyboard

### Understandable
> Information and the operation of the user interface must be understandable


* Make **text readable** and understandable
* Make content appear and operate in **predictable** ways
* Help users **avoid** and **correct** mistakes

### Robust
> Content must be robust enough that it can be interpreted by a wide variety of user agents, including assistive technologies


* Maximize compatibility with current and future user tools
<br>


















 











<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzNjYwMTU5OTEsLTk1NTk2MDQ4NV19
-->