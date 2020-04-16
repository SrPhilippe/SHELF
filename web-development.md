# Javascript

## Menu
-   [MDN Useful](#mozilla-developer-network-links)
-   [.htacess](#my-default-htacess-file)

---

-   ##### select by query

```javascript
    let element = document.querySelector("selector")
```

---

- ##### count object keys
```javascript
    let obj = {
      name: "João",
      age: 25,
      sons: 1
    }

    Object.keys(obj).length // this will return 3
```

-   ##### scroll animation to the anchor

```javascript
let $doc = $("html, body")
$(".scroll").click(function(e) {
  $doc.animate({
      scrollTop: $( $.attr(this, "href") ).offset().top
  }, 500)
  // e.preventDefault() // Just prevent the default action if you want to hide the anchor URL
})
```

-   ##### Shorhand if else

```javascript
(condition) ? true : false;
```

-   ##### Easy way to reset timer js

```javascript
let secs = 5,
    timer = function() {
        interval = setInterval(nextSlider, secs * 5)

    timer() // starts the timer
    clearInterval(interval)
}
```

-   ##### Logic to beauty animation contact form on keyup
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
        <input type=F"mail">
    </div>
    <div class="item">
        <p>Mensagem</p>
        <textarea cols="30" rows="5"></textarea>
    </div>
    <input type="submit" value="Enviar">
</form>
```
```javascript
$('.contact-form .item input, .contact-form .item textarea').each((index, el) => {
  $(el).keyup(e => {
    let letters = $(e.currentTarget).val().length
    if (letters > 0) {
      $(el).prevAll('p').addClass('active')
    } else {
      $(el).prevAll('p').removeClass('active')
    }
  })
})
```

-   ##### Script to remove watermark from 000webhost

```javascript
// Script para ocultar marca d'agua 000webhost
$("div[style='text-align: right;position: fixed;z-index:9999999;bottom: 0; width: 100%;cursor: pointer;line-height: 0;display:block !important;']").css("display", "none")
```

[◀◀ Return](readme.md#menu)

---

## Mozilla Developer Network links

 -   [HTTP Headers status](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status)
-   [Event interface](https://developer.mozilla.org/en-US/docs/Web/API/Event)
-   [Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
-   [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
-   [XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest)
-   [FileReader](https://developer.mozilla.org/en-US/docs/Web/API/FileReader)
-   [Location API](https://developer.mozilla.org/en-US/docs/Web/API/Location)
-   [Streams API](https://developer.mozilla.org/en-US/docs/Web/API/Streams_API)
-   [MIME types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types)
-   [Classes](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Classes)
-   [calc()](https://developer.mozilla.org/en-US/docs/Web/CSS/calc)
-   [Manifest](https://developer.mozilla.org/pt-BR/docs/Web/Manifest)

[↑ TOP](#Menu)

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
[↑ TOP](#Menu)
[◀◀ Return](readme.md)
