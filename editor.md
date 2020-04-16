# Visual Studio Code

### Basics

```typescript

{
    "terminal.integrated.shell.windows": "C:\\Windows\\System32\\bash.exe",
    "editor.fontFamily": "'Fira Code', Consolas, 'Courier New', monospace",
    "workbench.colorTheme": "City Lights",
    "workbench.iconTheme": "material-icon-theme",
    "extensions.ignoreRecommendations": false,
    "editor.mouseWheelZoom": true,
    "editor.fontLigatures": true,
    "explorer.openEditors.visible": 0,
    "window.menuBarVisibility": "toggle",
    "window.zoomLevel": 0,
    "explorer.confirmDelete": false,
    "editor.wordWrap": "on",
    "files.autoSave": "afterDelay",
    "files.autoSaveDelay": 300,
    "git.confirmSync": false
}

```

### Extensions
Configs for extensions
```typescript

{
    "liveServer.settings.donotShowInfoMsg": true,
    "prettier.semi": false,
    "prettier.tabWidth": 4,
    "[html]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[javascript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    }
}

```

### Beautify
Configure those elements that won't have the beautify applied to them
```typescript
{
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
    }
}
```
