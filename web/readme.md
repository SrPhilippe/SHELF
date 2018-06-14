# Menu
- [MDN Useful]()
- [Javascript]()
- [Mysql]()
- [.htacess]()

___

## Javascript useful
- ##### select by query
```javascript
    let element = document.querySelector("selector")
```

- ##### scroll animation to the anchor
```javascript
let $doc = $("html, body")
$(".scroll").click(function(e) {
  $doc.animate({
    scrollTop: $( $.attr(this, "href") ).offset().top
  }, 500)
  e.preventDefault()
})
```

- ##### Shorhand if else
```javascript
(condition) ? true : false;
```

- ##### Easy way to reset timer js
```javascript
let second = 5
let timer = () => {
    interval = setInterval(nextSlider, seconds * 5)

    timer() // starts the timer
    clearInterval(interval)
}
```

- ##### Logic to beauty animation contact form on keyup
```javascript
$("#contato form input").each((i, el) => {
  $(el).on("keyup", () => {
    let keyL = $(el).val().length
    if (keyL > 0) {
      $(el).addClass("active")
      $(el).prev("p.info-input").addClass("active")
    } else {
      $(el).removeClass("active")
      $(el).prev("p.info-input").removeClass("active")
    }
  })
})
```

- ##### Script to remove watermark from 000webhost
```javascript
// Script para ocultar marca d'agua 000webhost
$("div[style='text-align: right;position: fixed;z-index:9999999;bottom: 0; width: 100%;cursor: pointer;line-height: 0;display:block !important;']").css("display", "none");
```

___

## Mozilla Developer Network links
- [HTTP Headers status](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Status)
- [Event interface](https://developer.mozilla.org/en-US/docs/Web/API/Event)
- [Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest)
- [FileReader](https://developer.mozilla.org/en-US/docs/Web/API/FileReader)

[◀◀ Return](readme.md#menu)

___

## My default `.htacess` file
