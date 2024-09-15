# Code+
> A quality of life plugin for the Lite XL text editor. Offering improvements such as highlighted comments and autocomplete for brackets, quotes and more.

## Basic usage

 Highlight comments with special properties using the **@Todo(...)** and **@Fixme(...)** keywords for an enhanced coding experience. 
 Streamline coding by auto-completing brackets, parentheses, quotation marks reducing manual effort and improving the writing code experience.

## Demonstration

![Code+ demo](https://dcs99ww84zr4t.cloudfront.net/e8zdm7%2Fpreview%2F60821783%2Fmain_large.gif?response-content-disposition=inline%3Bfilename%3D%22main_large.gif%22%3B&response-content-type=image%2Fgif&Expires=1726412344&Signature=FcH-xLXO7ra51NxhbjKW-bc0g4kLsPX3LhcBvBwLJwRZ73mqtq5XvaL3KoUQPylhGtFwRbnMb6Tg91r5ky-B-iw2UNJkIRq641P8EEsWMktfHRDfjNEOGhbl9TsTlb5ZSZZW4oXA8TtY3e4-u93CLc1nHOJ6shD5VEWUFfSfPFLAVybrj~Q110i7Y-g~oBOw0vGyaBJrQ76XOcIfSraRPoS~OE3wyMgGOvjU2c2gZL-CbhG177tJBh2dVSjFXlyt3VUfKy7fxIlCqq~f3M-fw1MMH2EqsiSZWfO4YnncPMNs0jLHQN4-17Belq0rS4-TXe~7XKMBAEREugaRITetWQ__&Key-Pair-Id=APKAJT5WQLLEOADKLHBQ)

## Instalation
Navigate to the `data/plugins` folder and run the following command:
```bash 
git clone https://github.com/chqs-git/code-plus.git
```

Alternatively you can download and rename the `init.lua ` file to `code+.lua` and drop it into the `data/plugins` folder.

## Configuration

Using the settings plugin for Lite Xl you can easily configure your experience by changing the highlight colors for the *@todo* and *@fixme* operators.

If you wish to add more highlights you can simply update the following code:
```lua
function DocView:draw_line_text(line, x, y)
    local lh = draw_line_text(self, line, x, y)

    if config.plugins.code_plus.enabled then
      highlight_comment(self, line, x, y, "@todo", config.plugins.code_plus.todo)
      highlight_comment(self, line, x, y, "@fixme", config.plugins.code_plus.fixme)
      -- add a new highlight! the color is just an example
      highlight_comment(self, line, x, y, "@new_tag", {common.color "#ffffff"})
    end
    return lh
end
```

To extend the already auto-completing utilities to other keywords, you can simply use the `complete` function. Create a new command for the new auto-complete utility (required) and map a *key* to the command.

