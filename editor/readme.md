## Menu
- [VS code](#vs-code)
- [Atom](#Atom)
- [Sublime]()

----------

## Atom
<kbd>alt + ctrl + .</kbd> *Close the current XML/HTML tag*

<kbd>ctrl + shift + U</kbd> *Toggle menu to change file encoding*

- ##### Brackets
    - <kbd>ctrl + M</kbd> *Jump to the bracket matching the one adjacent to the cursor. It jumps to the nearest enclosing bracket when there's no adjacent bracket.*

    - <kbd>alt + ctrl + ,</kbd> *Select all the text inside the current brackets*


- ##### Bookmark
    - <kbd>ctrl + F2</kbd> *List of bookmark to the current file*

    - <kbd>alt + ctrl + F2</kbd> *Toggle the current line to a bookmark*

    - <kbd>F2</kbd> *Jump to the next bookmark*

- #### Package
    - ##### Emmet
    <kbd>shift + E</kbd> *Expand abbreviation*

- #### snippets.cson

```cson
'.text.html.basic':
    'Jquery library 3.3.1':
        'prefix': 'script-jquery'
        'body': '<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>'
    'Materialize CSS':
        'prefix': 'css-materialize'
        'body': '<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0-beta/css/materialize.min.css">'
    'Default script':
        'prefix': 'script-main'
        'body': '<script src="js/main.js"></script>'
    'ViewPort':
        'prefix': 'meta-viewport'
        'body': '<meta name="viewport" content="width=device-width, initial-scale=1.0">'
    'My default page':
        'prefix': 'my-page'
        'body': 'div#header>(nav#menu>.container>ul>li*5>a>{item $}.container)'

'.source.css, .source.sass':
    'Open Sans font':
        'prefix': 'font-open-sans'
        'body': '@import url("https://fonts.googleapis.com/css?family=Open+Sans:400,400i,600,700");'
    'Fira Sans font':
        'prefix': 'font-fira-sans'
        'body': '@import url("https://fonts.googleapis.com/css?family=Fira+Sans:400,400i,600,700");'
```

- #### Keymap.cson
```cson
'atom-workspace':
    'ctrl-alt-s': 'atom-live-server:stopServer',
    'alt-shift-a': 'editor:toggle-soft-wrap'
```

----------

## VS code

```typescript
{
    "window.menuBarVisibility": "toggle",
    "editor.fontLigatures": true,
    "editor.fontSize": 15,
    "editor.fontFamily": "'Fira Code', Consolas, 'Courier New', monospace",
    "workbench.iconTheme": "eq-material-theme-icons-light",
    "workbench.colorCustomizations": {
        "statusBar.background": "#17191b"
    },
    "materialTheme.accentPrevious": "Teal",
    "explorer.confirmDelete": false,
    "liveServer.settings.donotShowInfoMsg": true,
    "workbench.startupEditor": "newUntitledFile",
    "editor.minimap.enabled": false,
    "explorer.confirmDragAndDrop": false,
    "liveServer.settings.donotVerifyTags": true,
    "materialTheme.fixIconsRunning": false,
    "explorer.openEditors.visible": 0,
    "window.zoomLevel": 0,
    "terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe",
    "git.confirmSync": false,
    "[css]": {},
    "beautify.config": {
        "html": {
            "unformatted": [
                "a",
                "abbr",
                "area",
                "audio",
                "b",
                "bdi",
                "bdo",
                "br",
                "button",
                "canvas",
                "cite",
                "code",
                "data",
                "datalist",
                "del",
                "dfn",
                "em",
                "embed",
                "i",
                "iframe",
                "img",
                "input",
                "ins",
                "kbd",
                "keygen",
                "label",
                "map",
                "mark",
                "math",
                "meter",
                "noscript",
                "object",
                "output",
                "progress",
                "q",
                "ruby",
                "s",
                "samp",
                "select",
                "small",
                "span",
                "strong",
                "sub",
                "sup",
                "svg",
                "template",
                "textarea",
                "time",
                "u",
                "var",
                "video",
                "wbr",
                "text",
                "acronym",
                "address",
                "big",
                "dt",
                "ins",
                "strike",
                "tt"
            ]
        }
    },
    "editor.smoothScrolling": true,
    "editor.mouseWheelZoom": true,
    "workbench.colorTheme": "City Lights",
    "editor.formatOnPaste": true,
    "[javascript]": {}
}
```
