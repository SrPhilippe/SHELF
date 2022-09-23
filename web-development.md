# Javascript

## Mozilla Developer Network links

---

## select by query

```js
    document.querySelector('selector')
    document.querySelectorAll('seletor')

    // verify if an element matches, similar to css has(selector)
    document.querySelector('seletor').matches('foo')

    // tests if the element has a class
    element.classList.contains('class')
```

## count object keys

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

## Logic to beauty animation contact form on keyup

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

---

## My default `.htacess` file

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

---

## Removing 000webhost wattermark

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

## Ternary operator

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

[◀◀ Return](readme.md)
