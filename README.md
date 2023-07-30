# Code+
> A quality of life plugin for the Lite XL text editor. Offering improvements such as highlighted comments and autocomplete for brackets, quotes and more.

## Basic usage

 Highlight comments with special properties using the **@Todo(...)** and **@Fixme(...)** keywords for an enhanced coding experience. 
 Streamline coding by auto-completing brackets, parentheses, quotation marks reducing manual effort and improving the writing code experience.

## Demonstration

![Code+ demo](https://s12.gifyu.com/images/Sckre.gif)

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

