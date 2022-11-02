# My web development memory book

Important patterns, codes, exemples I find useful or important to use in my projects.

| Menu                      |
| ------------------------- |
| [Javascript](#javascript) |
| [CSS](#css)               |
| [HTML](#html)             |
| [Apache](#apache)         |
| [Vs Code](#vs-code)       |

| Navigation                 |
| -------------------------- |
| [🠜 go back](../readme.md) |

## Javascript

### select by query

```js
    document.querySelector('selector')
    document.querySelectorAll('selector')

    // Tests wheather the current element matches the 'foo' selector or not
    document.querySelector('element').matches('selector')

    // Tests wheather the element has a class or not
    element.classList.contains('class')
```

### count object keys

```js
    let obj = {
      name: "João",
      age: 25,
      sons: 1
    }

    Object.keys(obj).length // this will return 3
```

### Easy way to reset timer js

```js
let secs = 5,
    timer = function() {
        interval = setInterval(nextSlider, secs * 5)

    timer() // starts the timer
    clearInterval(interval)
}
```

### Logic to beauty animation contact form on keyup

```html
<form class="contact-form">
    <div class="item">
        <p>Nome</p>
        <input type="text">
    </div>
    <div class="item">
        <p>Sobrenome</p>
        <input type="text">
    </div>
    <div class="item">
        <p>E-mail</p>
        <input type="mail">
    </div>
    <div class="item">
        <p>Mensagem</p>
        <textarea cols="30" rows="5"></textarea>
    </div>
    <input type="submit" value="Enviar">
</form>
```

```js

// Selecting textareas and inputs that don't match [hidden] and [submit] types
const inputs = document.querySelector('textarea, input:not([type="hidden"], [type="submit"])')

inputs.forEach(el => {
  el.addEventListener('input', () => {
    const target = el.currentTarget
    (target.value > 0)
      ? target.previousSibling.classList.add('active')
      : target.previousSibling.classList.remove('active')
  })
})
```

### Removing 000webhost wattermark

```js
// Select all Div childs inside body element
const $bodyDivs = document.querySelectorAll('body > div')

 $bodyDivs.forEach((el) => { // Finding webhost div
  let unknownEl = el.firstChild
  if (
   unknownEl.nodeName === 'A' &&
   unknownEl.querySelector('img').getAttribute('alt') ===
    'www.000webhost.com'
  ) {
   el.remove() // Removes the webhost element from the DOM
  }
 })
```

### Ternary operator

```js
let a = 1
let b = 2
let c,d = null

a === b ? c = true : c = false

// You can separate the true/false lines

(a === b)
? c = true
: c = false

// Allowing more than one task

a === b
? (c = true, d = false)
: (c = false, d = true)

// The elseif

a !== b
? d = false
  : (a === b) // elseif
  ? c = true
: console.log('do nothing') // false value for a !== b

```

## Regular expression to match an email pattern

```regexp
/^[^ ]+@[^ ]+\.[a-z]{2,3}$/
```

### Better **one**

```regexp
/^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$/
```

## Util functions

### Global Event Listener

```js
export function addGlobalEventListener(
  type,
  selector,
  callback,
  options,
  parent = document
) {
  parent.addEventListener(type, e => {
    if (e.target.matches(selector)) callback(e)
  },
    options
  )
}
```

### Handling css classes

```js
export const addClass = (element, classes = 'active') => {
  element.classList.add(classes)
}

export const rmClass = (element, classes = 'active') => {
  element.classList.remove(classes)
}

export const toggClass = (element, classes = 'active') => {
  element.classList.toggle(classes)
}
```

### Query Selector

```js
export function qs(selector, parent = document) {
  return parent.querySelector(selector)
}
```

## Fixed menu anchor correction

When we use a fixed menu in our website. We end up messing with the anchor offset, in a way that makes the menu always hidding the initial part of the section.

Nowadays, there's a very simple solution using the css property `scroll-margin-top`.

I personally prefer to set the property through javascript.

```js
//
const sections = document.querySelector('.sections')
const menu = document.querySelector('.menu') // Menu with 75px height
const  menuHeight  = menu.offsetHeight // Gets the height from the menu

sections.forEach(section => {
  section.style.scrollMarginTop =
    `${menuHeight}px` // output => scroll-margin-top: 75px
})

```

### Associate value in more than one variable

```js
let token = false
let lastTimestamp = false

token = localStorage.token = 3
lastTimestamp = localStorage.lastTimestamp = currentSec()
```

| Navigation                                   |
| -------------------------------------------- |
| [🠝 go top](#my-web-development-memory-book) |
| [🠜 go back](../readme.md)                   |

---

## CSS

## My custom css reset file

I usually name it `varnreset.css` because it's also where I set the **_:root_** variables inside the project.

```css
:root {
    --font-family: sans-serif;
    --tran-fade-normal: opacity .4s ease;

    --margin-icon-link: 0.3rem; // Margin used between text links and the icon in it
}

::-webkit-scrollbar {
    background-color: initial;
    width: initial;
}

::-webkit-scrollbar-thumb {
    background-color: initial;
    border-radius: initial;
}

::selection {
    background-color: initial;
    color: initial;
}

html {
  scroll-behavior: smooth;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

img {
  vertical-align: middle;
  max-width: 100%;
}

ul, ol {
  list-style: none;
}

a {
  display: inline-block;
}

textarea {
    font-family: var(--font-family);
    resize: none;
}

.container {
  max-width: 1124px;
  margin-block: auto;
  width: 100%;
}
```

### Commented sections

```css
/* -------------------------------------------------- */

/* =HEADER  |---------------------------------------- */

/* =MENU    |---------------------------------------- */

/* =SUB     |---------------------------------------- */

/* =MAIN    |---------------------------------------- */

/* =FOOTER  |---------------------------------------- */

/* =QUERIES |---------------------------------------- */
```

### About variables

Set the variables in the **_:root_** using the usual method `--name-of-the-var`. But when it comes to variables that are avaiable only in specific scopes, it's better to differentiate using **underline** <kbd>_</kbd>.

- E.g. `--_name-of-the-var`

```css
:root {
  /* Variable in the root scope */
  --z-index-tooltip: 10;
}

.wrapper {
  /* This variable is avaiable only inside the .wrapper scope */
  --_size: 3rem;
}
```

| Navigation                                   |
| -------------------------------------------- |
| [🠝 go top](#my-web-development-memory-book) |
| [🠜 go back](../readme.md)                   |

---

## HTML

| Navigation                                   |
| -------------------------------------------- |
| [🠝 go top](#my-web-development-memory-book) |
| [🠜 go back](../readme.md)                   |

---

## Apache

### My default `.htacess` file

```apache
# This function bellow redirect the user to the following link if the user try to access a directory or file that doesn't exist.
ErrorDocument 404 https://(link here)/

# This whole block of code removes the .html to the link
RewriteEngine on
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME}\.html -f
RewriteRule ^(.*)$ $1.html [NC,L]

# sets the max_filesize and post_max_size
php_value upload_max_filesize 500M
php_value post_max_size 500M
```

| Navigation                                   |
| -------------------------------------------- |
| [🠝 go top](#my-web-development-memory-book) |
| [🠜 go back](../readme.md)                   |

## Vs code

Vs code configs not in use

```jsonc
  // Power mode !DISABLED
  "powermode.enabled": false,
  "powermode.presets": "flames",
  "powermode.explosions.size": 8,
  "powermode.shake.enabled": false,
  "powermode.explosions.duration": 150,
  "powermode.combo.timerEnabled": "hide",
  "powermode.combo.location": "statusbar",
  "powermode.combo.counterEnabled": "hide",

  "editor.fontLigatures": "'ss01', 'ss03', 'ss05', 'cv01', 'cv02', 'cv06', 'cv27', 'cv29', 'cv30'", // Ligatures for 'Fira Code'
  "editor.fontLigatures": "'calt', 'ss01'", // Ligatures for 'Cascadia Code'

  // Ruler code wrap
  "editor.rulers": [90],
  "workbench.colorCustomizations": {
    "editorRuler.foreground": "#2185ba"
  }
```

| Navigation                                   |
| -------------------------------------------- |
| [🠝 go top](#my-web-development-memory-book) |
| [🠜 go back](../readme.md)                   |
